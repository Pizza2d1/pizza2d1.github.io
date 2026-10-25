---
title: Jellyfin updating to 12.0
layout: home
nav_order: 2
---

# Jellyfin server is updating to 12.0
The newest version of Jellyfin is out and with the appeal of better performace and sercurity patches, I really wanted to update to it asap, but the first time I did it, everything broke and I didn't have a proper backup of the jellyfin instance so a lot of data was lost and I had to go back to regular 10.11.11, which was fine since it still had compatibility with third-party apps like JellyMusicDiscovery + ytmusicserver.

## New movies and shows
Sadly I don't think I will be spending much more time adding content and will instead be working on trimming down the fat, so that people who might wanna mirror or people who worry about bandwidth don't have to worry as much. Notable shows and movies being The Big Bang Theory and most of the Spider-man films, which were uneccessarily big. With this trimming of most shows we should be able to save about 500 GB - 1 TTB of storage which would be really nice considering that I am running low on storage, the process of trimming down has already started and we have already saved over 300 GB

## Performance
Jellyfin also switched back to using a proper GPU on a laptop rather than using 90% of the server rack's CPU when transcoding in real-time, making loading speeds of shows and movies take almost half as much time, from a consistent 4-7 sec to about less that 3 sec, and that's just with the hardware switch, I haven't tested Jellyfin version 12.0 performance yet
