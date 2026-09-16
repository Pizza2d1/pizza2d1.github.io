---
title: Gitea Runner Setup
layout: home
permalink: /server_info/gitea_runner_setup/
nav_exclude: true
search_enabled: true
---

# Setting up a gitea runner

___

### About
This guide will go through how to set up your own runner for gitea so that you are able to use gitea actions for your repository to run when certain flags trigger, such as when you push to gitea.

### Why
An example of how this might be useful is having a git repository that you want to have be ready to be packaged in a docker image automatically, so you include a Dockerfile in the repository and create a workflow action that triggers every time you push to a certain branch to make the docker image and push it to docker.io


## Installation
This can be downloaded on your main machine or server if you wish. The runner acts as a daemon that will run continually and will automatically check if a flag was hit to activate, so running it on a desktop PC shouldn't be an issue

### 1.
Download the latest gitea runner binary: https://dl.gitea.com/gitea-runner/3.5.0/

Quicklinks:
- [linux amd64](https://dl.gitea.com/gitea-runner/3.5.0/gitea-runner-3.5.0-linux-amd64)
- [windows amd64](https://dl.gitea.com/gitea-runner/3.5.0/gitea-runner-3.5.0-windows-amd64.exe)

___

### 2.
Create a runner repo token from gitea:

In the repository go to ***Settings > Actions > Runners***, and copy the runner token

https://gitea.happylizard.me/[OWNER]/[REPO]/settings/actions/runners

___

### 3.
Now with the binary that you downloaded, run this:

```
# Linux
./gitea-runner-3.5.0-linux-amd64 register --no-interactive --instance https://gitea.happylizard.me --token [TOKEN]

# Windows
./gitea-runner-3.5.0-windows-amd64.exe register --no-interactive --instance https://gitea.happylizard.me --token [TOKEN]
```

{: .new-title }
> Troubleshooting
>
> If you are not able to add this token, make sure that you have a gpg key that links to you that you can use to authenicate your token:
>
> gpg --generate-key

___

### 4.
Now that your runner is connected, run the daemon:
```
# Linux
./gitea-runner-3.5.0-linux-amd64 daemon

# Windows
./gitea-runner-3.5.0-windows-amd64.exe daemon
```

___

## Finish
Now that you have a runner that is automatically checking your repo, you can now use gitea actions to automatically run when you trigger a git flag

[Gitea's Example](https://docs.gitea.com/usage/actions/quickstart/#:~:text=name,job%2Estatus%20%7D%7D%2E%22):
```
name: Gitea Actions Demo
run-name: ${{ gitea.actor }} is testing out Gitea Actions 🚀
on: [push]

jobs:
  Explore-Gitea-Actions:
    runs-on: ubuntu-latest
    steps:
      - run: echo "🎉 The job was automatically triggered by a ${{ gitea.event_name }} event."
      - run: echo "🐧 This job is now running on a ${{ runner.os }} server hosted by Gitea!"
      - run: echo "🔎 The name of your branch is ${{ gitea.ref }} and your repository is ${{ gitea.repository }}."
      - name: Check out repository code
        uses: actions/checkout@v4
      - run: echo "💡 The ${{ gitea.repository }} repository has been cloned to the runner."
      - run: echo "🖥️ The workflow is now ready to test your code on the runner."
      - name: List files in the repository
        run: |
          ls ${{ gitea.workspace }}
      - run: echo "🍏 This job's status is ${{ job.status }}."
```