---
layout: default
---

# Other platforms
Github: [https://github.com/C-H-Fahy](https://github.com/C-H-Fahy)
Mastodon: [https://infosec.exchange/@chfahy](https://infosec.exchange/@chfahy)
Linkedin: [https://www.linkedin.com/in/chfahy](https://www.linkedin.com/in/chfahy)
Twitter: [https://twitter.com/C\_H\_FAHY](https://twitter.com/C_H_FAHY)

# Zoom: Open Redirect Single Sign On
When signing on to zoom via the single sign in option, it is possible to cause an open redirect by terminating a real domain with a /, This can be used to serve fairly convincing fake login pages as the user would expect to be asked for their login details for their organisation after pressing sign in

Normally, Zoom requires that you request a "Vanity URL" from them to put in this "domain" box,[these domains are in a strange format, and require some type of verification](https://support.zoom.us/hc/en-us/articles/215062646), presumably to prevent such social engineering attacks. This open redirect partially subverts that control.
[read more](./2021-10-18-zoom-open-redirect)

