---
layout: default
title:  "Zoom: open redirect Single Sign On"
date:   2021-10-18T16:13:00Z
permalink: ./2021-10-18-zoom-open-redirect
category: update
---

#Zoom: open redirect Single Sign On

When signing on to zoom via the single sign in option, it is possible to cause an open redirect by terminating a real domain with a /, This can be used to serve fairly convincing fake login pages as the user would expect to be asked for their login details for their organisation after pressing sign in

Normally, Zoom requires that you request a "Vanity URL" from them to put in this "domain" box,these domains are in a strange format, and require some type of verification, presumably to prevent such social engineering attacks. This open redirect partially subverts that control.

![Zoom SSO sign in page with "example.com/" in box](/assets/2021-10-18-zoom-open-redirect-image0.png)

![Example webpage post redirect](/assets/2021-10-18-zoom-open-redirect-image1.png)

Zoom(desktop) client version 5.8.1 (1435)


#### Corrections/Edits:

2021-10-18T16:13:00Z - social engineering != Phishing


#### Timeline:

2021-10-09T20:47:25Z - 

Vulnerability Reported via Email to security@zoom.us

2021-10-12T21:18:37Z -

Instructed by security@zoom.us to submit via HackerOne.com

2021-10-15T22:47:25Z -  

Vulnerability Reported via HackerOne.com

2021-10-18T01:15:08Z - 

Vendor closed report "Issues that require unlikely user interaction"
