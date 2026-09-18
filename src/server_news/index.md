---
title: Server News
layout: home
nav_order: 2
description: "Where I will detail what I am doing with my website"
permalink: /server_news
has_toc: false
---
# Server News

[Links to website services!](https://pizza2d1.github.io/server_links){: .btn .fs-5 .mb-4 .mb-md-0 .btn-purple }
[Check out my other projects!](https://github.com/pizza2d1){: .btn .fs-5 .mb-4 .mb-md-0 .btn-green }

[Table of Contents](#table-of-contents){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }

---

{: .warning }
> This part of the webpage is still continuing to be worked on, so there might be some broken links here and there, as Jekyll is not very intuiative

{: .new-title }
> Quick Note
>
> If the website is down it is totally fine to contact me to let me know. I plan on having my services be used by more people in the future once I get a proper setup and would like to know how to fix issues that arise early in the server-management side of hobbies, which means quickly snuffing out issues



### Contact me!
[![LinkedIn Logo](../../assets/images/linkedin.png){: width="20" }](https://www.linkedin.com/in/pizza2d1/)
[LinkedIn](https://www.linkedin.com/in/pizza2d1/)

[![Discord Logo](../../assets/images/discord.png){: width="20" }](https://discordapp.com/users/714918826831118436)
[Discord](https://discordapp.com/users/714918826831118436)

[![Github Logo](../../assets/images/github.png){: width="20" }](https://github.com/pizza2d1)
[Github](https://github.com/pizza2d1)

[![Signal Logo](../../assets/images/signal.png){: width="20" }](https://signal.me/#eu/14nA-tBiLDlv3Z1DzDlmNSd_hpqwEk2EcjhmY0uWcjbTAQWx9NZGiJfkVOkMR4mS)
[Signal](https://signal.me/#eu/14nA-tBiLDlv3Z1DzDlmNSd_hpqwEk2EcjhmY0uWcjbTAQWx9NZGiJfkVOkMR4mS)


I currently don't really have an easy way to update this quite yet, since I am mostly just using the Jekyll markdown files for editing these, but eventually I will try and have it work the same way that I previously had with my RSS feed where I can just type into a new text file, run a command and have it published to the website all formatted and pretty


## MAJOR NEWS
### The server's way of accessing network filesystems will change very soon from [SAMBA](https://www.samba.org/) to [SSHFS](https://github.com/libfuse/sshfs), allowing for accurate file permissions and faster bandwidth between server cluster devices.

### Due to this, many services that were previously run on NAS1 will soon be ran on the main laptop server, including [copyparty](https://copyparty.happylizard.me), [immich](https://immich.happylizard.me), and [happy-ripper](https://happy-ripper.happylizard.me).

### There will also be a change in how backups are done, previously the server was being backed up "syncronously" with the main server's media files, where the server would periodically just send a rsync command to have a perfect filesystem copy on the other NAS2. This was stupid, very stupid and dumb and caused literal TERABYTES of storage to be wasted.

### We are now using a OSS backup service called [BorgBackup](https://www.borgbackup.org/) (rather than [restic](https://restic.net/)/[duplicity](https://duplicity.gitlab.io/)), for it's reliability and familiarity, and because it includes de-duplication, incremental backups, and FUSE restoring (my personal favourite)

### The server cluster may also grow in coming weeks, as I plan on adding a broken laptop to the cluster for specifically rstack docker containers, so that I can stop using my NAS1's CPU to max whenever we download online.


___

## <u>Table of contents</u>

### - **[Website News]({% link src/server_news/website/index.md %})**
### - **[Gitea News]({% link src/server_news/gitea/index.md %})**
### - **[Jellyfin News]({% link src/server_news/jellyfin/index.md %})**
### - **[Rstack News]({% link src/server_news/rstack/index.md %})**
### - **[Server Links]({% link src/server_news/links/index.md %})**