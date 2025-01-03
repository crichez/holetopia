# holetopia.com

This repository contains configuration files for `holetopia.com` because I am
incapable of resisting a good bit.

## Overview

The site is hosted using Apache httpd on Ubuntu 24.04.1 LTS.
SSL certificates are managed by certbot and Let's Encrypt.
DNS servers are hosted by Gandi and use DNSSEC, the zone file is included.
We don't serve any content, only the following redirects:
* `holetopia.com` => `twitch.tv/ashleyroboto`
* `holetopia.com/ashleyroboto` => `twitch.tv/ashleyroboto`
* `holetopia.com/youtube` => `youtube.com/ashleyroboto`
* `holetopia.com/vods` => `youtube.com/@ashleyrobotovods`
* `holetopia.com/instagram` => `instagram.com/ashleyroboto`
* `holetopia.com/tiktok` => `tiktok.com/@ashleyroboto`
* `holetopia.com/discord` => `discord.gg/beanboat`
* `holetopia.com/bluesky` => `bsky.app/profile/ashleyroboto`

## Contributing

If you want to add/remove/modify any redirects, message me on discord
`@tofugarden#0246`. If you are on the receiving end of a redirect and would
like to be removed, you can message me and the removal will be processed, no
questions asked.

If you would like to change the apache configuration or improve the repo in
general, you can go ahead and create an issue or PR. Keep in mind:
* All redirects are served via TLS, and all targets must support TLS
* HTTP/2 is not supported due to host configuration limitations
* IPv6 is not supported due to host configuration limitations
* We will never serve any actual content on holetopia.com unless requested
  to do so by Ashley herself

## Installation

We depend on Debian-style `apache2`, so all you really need to do is:
1. Configure DNS records
2. Get a (www.)holetopia.com TLS certificate via certbot
3. Run the following:

```sh
git clone https://github.com/crichez/holetopia
cd holetopia
sudo cp holetopia.conf /etc/apache2/sites-available
sudo a2ensite holetopia
sudo systemctl reload apache2
```

I don't include testing instructions since this is a trivial site, these notes
are mostly for myself when I have to do a migration in a few years and forget
how everything works :)
