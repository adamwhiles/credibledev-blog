---
title: "How to Add NodeJS to SiteGround Shared Hosting"
created: 2023-10-05
date: 2023-10-05
categories: 
  - linux
tags: 
  - nodejs
authors: 
  - thecd
description: "This guide explains how to install and set up NodeJS on a shared hosting provider like SiteGround who offer SSH."
cover:
    image: images/nodejs-on-shared-hosting.png
---

Maybe you have had shared hosting for a while or just signed up, in any case, now you have the desire to use NodeJS for your project. Many shared hosting providers will tell you that NodeJS is not supported on share hosting plans. Not supported doesn't mean that it isn't possible though.

In today's guide, I will show you how to install NodeJS on shared hosting such as SiteGround. This guide may work for other share hosts as well, so give it a try and leave feedback in the comments. All you need is SSH access, which many shared hosts provide.

[![Ad - Web Hosting from SiteGround - Crafted for easy site management. Click to learn more.](images/general_EN_general-hosting-leaderboard-light.jpg)](https://www.siteground.com/go/yqgtmjijv2) 

## Step 1: Enable SSH

Enabling SSH will be different for every hosting provider but you should be able to find a guide online for doing this on your provider, if it is supported. If SSH is not supported, you will not be able to use this method for install NodeJS.

For SiteGround, you login to your customer portal, head to your website and you should have a "devs" section where you can generate an SSH key. SiteGround doesn't support SSH using a password so you must generate a key and use that to connect.

## Step 2: Connect to SSH

The details of how to connect to a server over SSH are out of the scope of this guide. There are countless documents already online that describe this process in detail. Nonetheless, get connected via SSH and move on to the next step.

## Step 3: Download NodeJS

Now that you are connect to SSH, we can download NodeJS. You can use curl or wget to accomplish this from the terminal. As of this writing, the current LTS release of NodeJS is v18.18 which is what we will download.

```
wget https://nodejs.org/dist/v18.18.0/node-v18.18.0-linux-x64.tar.xz
```

```
curl https://nodejs.org/dist/v18.18.0/node-v18.18.0-linux-x64.tar.xz
```

Next, we need to extract this file and we'll rename the folder to make it easier to work with in the terminal.

```
tar -xvf node-v18.18.0-linux-x64.tar.xz
mv node-v18.18.0-linux-x64 nodejs
```

## Step 4: Use NodeJS on Shared Hosting

Now that we have NodeJS downloaded on our shared hosting provider, we need to pull out the binaries for node and npm and put them in their own directory. After this we will add that directory to the path so we can use them in the terminal.

```
mkdir ~/bin
cp nodejs/bin/node ~/bin
cd ~/bin
ln -s ../nodejs/lib/node_modules/npm/bin/npm-cli.js npm
PATH="$PATH:~/bin/"
```

You should now be able to use node and npm from your terminal. Congratulations, you now have NodeJS installed on your share hosting provider. This guide was written using SiteGround, so there are not guarantees that these exact commands or process will work with other hosting providers.
