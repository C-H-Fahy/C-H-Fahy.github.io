---
title:  "Pipewire with Scarlett Solo"
date:   2022-11-14T13:19:30Z
permalink: ./2022-11-14-Pipewire-with-Scarlett-Solo
categories: Blog
---



When using a scarlett solo with pipewire, pipewire takes both channels on the Solo
and tries to treat it as a stereo source.

This is usually not ideal, as the left source on the Solo is an XLR input while the right source is a AUX port, and it is unlikely that you want your XLR input playing only on the left side when the audio is recorded with an application like OBS or Audacity. Some applications like Discord automatically map Stereo to Mono but this may come at reduced quality.

In order to fix this,  it is likely that you will want to create a loopback device that takes the left channel of the Solo and turns it into a single audio source.

The [pipewire docs](https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Virtual-Devices#virtual-mono-source) describe how to do this for some devices, however the device name of the connected Solo is determined by a string that is tied to that unique device.

In order to find the string you can do
```
$ pactl list sources
```
and then create a config file for pipewire by copying /usr/share/pipewire to /etc/pipewire/pipewire.conf

and add under context.modules = [
```
    {   name = libpipewire-module-loopback
            args = {
                capture.props = {
                    audio.position = [FL, FL]
                    node.target = alsa_input.usb-Focusrite_Scarlett_Solo_USB_XXXXXXXXXXXXXX-00.iec958-stereo
                }
                playback.props = {
                    media.class = Audio/Source
                    node.name = mono-microphone
                    node.description = "Scarlett Left"
                    audio.position = [mono]
                }
            }
    }
```
Replacing XXXXXXXXXXXXXX with the string listed listed beside device.serial = "Focusrite\_Scarlett\_Solo\_USB\_  after doing pactl list sources.

And then you should be able to select the "Scarlett Left" option and have mono audio be recorded by default. 


One thing remains consistent with audio with Linux and that is that it is always difficult to get working, and some applications will just decide not to work anyway, but I hope this guide manages to help someone.

Please feel free to contact me to tell me if you find a better way of doing this.
#### Corrections/Edits:

2022-11-14T18:41:55: spag
