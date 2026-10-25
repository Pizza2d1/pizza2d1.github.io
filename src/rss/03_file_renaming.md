---
parent: RSS feed
title: File Organization
layout: home
nav_order: 2
---

# File organization
The server media files have now been updated to be standardized and better organized so that when browsing and indexing files they are easier to identify.

### Shows
A big issue that was happening was that there would be many different season folders that would be fragmented and in different names that made it impossible for things like Jellyfin and the rstack to be able to read the files correctly, leading to incorrect episode listings e.g.:


Regular Show - Season 1                                                                                
Regular Show - Season 2                                                                                
Regular Show - Season 3                                                                                
Regular Show - Season 4                                                                                
Regular Show - Season 5                                                                                
Regular Show - Season 6                                                                                
Regular Show - Season 7                                                                                
Regular Show - Season 8                                                                                
Season 3                                                                                               
Season 4                                                                                               
Season 6                                                                                               
Shorts


The issue is that you would have things like episodes S03E05 - S03E08 in the "Season 3" folder with all the other season episodes in the proper "Regular Show - Season 3" folder, but Sonarr wouldn't see it as an issue and would just keep them separated, leading to there being multiple folders and incorrect indexing in Jellyfin and somewhat in copyparty


___


The fixed way would look more something like this:


Regular Show - Season 1                                                                                
Regular Show - Season 2                                                                                
Regular Show - Season 3                                                                                
Regular Show - Season 4                                                                                
Regular Show - Season 5                                                                                
Regular Show - Season 6                                                                                
Regular Show - Season 7                                                                                
Regular Show - Season 8                                                                                
Specials


Since Jellyfin will identify folders named as "Special" as a dedicated folder for extra files, rather than "Shorts" or "Extras"

### Movies
Movies didn't have much of a change since many of them were already fomatted correctly manually a while ago, the main changes were getting rid of video files that had simple names with no parse-able data for Jellyfin and Radarr, making it so that even though there was a valid video file, Jellyfin would mix up movies and Radarr wouldn't count it as a valid file to index e.g.:


In the "Django Unchained" folder:
- django.mkv


Django wouldn't be properly indexed, and radarr would show it as unavailable unless it was renamed


Fixed:
- Django Unchained (2012) 1080p BrRip x264 -YIFY.mp4
