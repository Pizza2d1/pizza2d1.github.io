---
parent: RSS feed
title: Fixing existing services
layout: home
nav_order: 2
---

# Fixing existing services

On this edition of server management, we get to learn about the important of RTFM (Read The Fucking Manual)

___

## Copyparty
One BIG issue that I was having everytime when restarting the server or updating my docker images was copyparty, it is one of the most useful services that I host for how easy it is to use, how easy it is to connect to other devices (whether on Windows or Linux), and it's really nice in terms of large uploads/downloads because the files remember their states similar to rsync.
___
The problem isn't that it scans the files to hash them all, that makes sense when you are wanting a consistent database and want to verify file integrity for when you try and upload an existing file. The problem was that it decided to scan and hash the ENTIRE server filesystem (which amounts to about 8.5 TiB) each time, which caused the copyparty instance to lock up until the hashing was done, making it so nobody could upload to their drives or to any copyparty volumes in general for ALMOST A FULL DAY. So yeah, a pretty big issue, which was previously solved by just never updating copyparty or restarting the server, but thats a pain.
___
### The fix 
After looking at the github page for probably the 50th time to find a fix, I realized that each volume has something called "flags", I didn't think of it before but those probably mean that I could make it so that instead of scanning the entire filesystem, it would only do that for selected drives, such as the personal file drives where someone might upload the same exact file and it can catch that, but when you have a static movie directory volume that isn't prone to that, it makes sense to not run the process of checking those. So I just turned off hashing the entire filesystem and used the "flags" per volume for important ones that people are likely to upload to.
___
This lead to copyparty startup going from almost a full day to only about a couple seconds.


___
___

## Nextcloud
Nextcloud is meant for big infastructures that actually need it, not just for people that do stupid homelabs, so typically when you first hear about Nextcloud and try to run it on a dinky laptop server or a simple NAS, you find that it is pretty darn slow, so you typically play around with it for a bit until you stop it so that your Jellyfin instance isn't as slow anymore.
___
For this one I don't EXACTLY know what I did to fix it, my idea is that just having a better server rack made it better, but one of the configuration things that I did seemed to help so that it was faster for loading things and initial startups
___
### The "fix"
I just gave nextcloud more RAM for it's PHP-FPM workers, so instead of giving it the default 1048 MiB (1 GB), I just gave it 16 GB. Yeah.

___
___

## Reverse Proxy
This is a bit of a older fix, but it's one that I think sort of fits into this storytime
___
A while back there I was using apache for serving my website and for doing reverse proxies since it was what I was taught in CTEC and I had gotten so familiar with it that I was making file-versioning scripts to modify my configuration so that I could update them quickly. But then a good (handsome) friend told me about Caddy, I had some idea of what Caddy was, because I had seen a lot of people posting their reverse proxy configs with Caddy and Nginx but not apache and was wondering how it worked, since it looked so strange.
___
### The fix 
After tinkering around a bit and testing it out, I figured out how Caddy works and it is SO MUCH BETTER THAN APACHE, oh my god, I don't think I could go back, it's so nice, it has all the security config options as apache, and it's secure by default.
