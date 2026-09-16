---
title: Gitea Server News
layout: home
nav_order: 3
description: "Gitea News"
permalink: /server_news/gitea
parent: Server News
---
# Gitea Server News

A list of updates that I add when upgrading or adding things to gitea

---

## Latest update:

### 2026/9/15:
Gitea now supports repository agents for running workflows in the Actions tab of each repository

They currently use containerized "runners" that are specific to each repository and are to be run BY THE REPO OWNER, as they are currently not set up to be automatically made for each repo

To make a repo runner, here is [Gitea's own guide](https://docs.gitea.com/usage/actions/quickstart/), or you can use this quick guide: [Adding gitea runner](https://pizza2d1.github.io/server_info/gitea_runner_setup)