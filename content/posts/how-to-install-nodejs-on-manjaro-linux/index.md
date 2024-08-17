---
title: "Install NodeJS on Manjaro Linux - 2023 Update"
created: 2022-05-09
date: 2022-05-09
categories: 
  - javascript
  - linux
  - manjaro
  - programming
tags: 
  - javascript
  - linux
  - manjaro
  - nodejs
  - npm
  - nvm
authors: 
  - thecd
description: "How to install NodeJS on Manjaro Linux. This guide walks you through the steps to install NodeJS to get your next code project started."
cover:
    image: images/1200px-Node.js_logo.svg_.png
url: "/how-to-install-nodejs-on-manjaro-linux"
---

If you plan on getting into Javascript development and you use Manjaro, you will likely run across the need to install [NodeJS](https://nodejs.org/en/) on Manjaro Linux. It's quite simple to do on Manjaro, especially when using [NVM](https://github.com/nvm-sh/nvm) - Node Version Manager. NVM allows you to easily install, update and switch between different releases of NodeJS, such as LTS, which is what we will be installing today. Typically you would want to develop on LTS for better support unless you really need the newest features not available in LTS, or you are simply testing some new functionality.

#### Ready to start coding using NodeJS on Manjaro? Check out our guide on installing [VScode on Manjaro Linux](https://credibledev.com/install-vs-code-on-manjaro-linux/)

If you're not the reading type, check out our simple video guide on how to install NodeJS on Manjaro Linux on the credibleDEV YouTube channel.

https://youtu.be/f1Yqrg8gyKY

## Install NVM Manjaro Linux

In order to install NodeJS on Manjaro, we will first install the Node Version Manager, NVM, by running the following command in a terminal.

```
sudo pacman -S nvm
```

Next, run the following two commands to complete the setup of NVM on Manjaro. If you are using something other than ZSH, you will need to edit this line to match your shell type, such as bashrc.

## Install NVM on EndeavourOS

On EndeavourOS, you may not find NVM using pacman, instead you can do one of the following.

If you have yay or some other AUR helper you can try this.

```
yay -S nvm
```

Now close your terminal and re-open it.

Didn't work for you? Try following the same instructions used for Ubuntu and other Linux distros below. You may need to close your terminal and re-open it after following those steps as well.

## Install NVM for Ubuntu and Other Linux Distributions

If you are trying to install the Node Version Manager on another Linux distribution such as Ubuntu or something Debian based, you can run the following command in the terminal to get NVM. You may need to close and open a new terminal after the installation completes.

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
```

Once the installation is complete, you can close your terminal window and then launch a new one in the case that running the command nvm reports that it is not found. After launching a new terminal the nvm command should be working.

## Install NodeJS on Manjaro Linux, Ubuntu and Other Linux Distributions

Now that we have NVM installed, we can move on the installing NodeJS. These commands will work on Manjaro Linux and other distributions such as Ubuntu as well. As I stated before, we are going to install the latest LTS version, which is done with the following command.

### NVM Command Not Found

If you try to run the following command and get "**nvm command not found**". You can fix this error by running one of the following commands, whichever matches the shell that you are running. Most commonly this is bash for example. After running the command, open a new terminal and the "nvm" command will be working.

```
echo 'source /usr/share/nvm/init-nvm.sh' >> ~/.bashrc
echo 'source /usr/share/nvm/init-nvm.sh' >> ~/.zshrc
```

### Install NodeJS Using NVM

```
nvm install --lts
```

Once the installation is complete, you can verify that node and npm are both installed with the following commands. Which should return the currently installed version of each.

### Check if NodeJS and NPM are Installed

We can check if Node is installed by running the following command which will check the NodeJS version. If the command in successful then it is installed and will report the version to the terminal. Since NPM is included with Node, we will also verify that it is installed as well with the second command.

```
node -v
npm -v
```

If you wish to install multiple versions of NodeJS on your Linux system, you can do so by using some of these nvm commands. To find more commands refer to the NVM documentation or by running nvm --help in your terminal.

- nvm install 19.6.0 - This installs a specific version

- nvm install node - This installs the latest available version (Possibly not an LTS version)

- nvm use --lts - Tells the system to use the installed LTS version of node

- nvm use 19.6.0 - Tells the system to use this specific version of node

## NPM - Node Package Manager

Now that you have NodeJS installed on your Manjaro Linux system, you also have access to the Node Package Manager, known as NPM. Since NPM is included with the installation of NodeJS, there is no need to install NPM separately, you're ready to go. With NPM, you can easily install packages to extend the apps and programs that you write using Javascript. You can read more about how to use NPM on their [docs page](https://docs.npmjs.com/), but the syntax to install packages from NPM is simple.

```
npm install "package name"
```

Just replace "package name" with the name of the NPM package that you want to install. You can search the large database of packages using the search bar on the [NPM site](https://www.npmjs.com/). Some of my favorite NPM packages are Express and PM2. Express allows you to quickly spin up a NodeJS web server and PM2 allows you to easily manage them.

### NPM Command Not Found

If you see this error, it means that either the install failed or the location of NPM is not in your path. The simplest thing to verify this would be to close your terminal, open a new one and try again or reboot. You can also use the "which" command in the terminal to try and locate the NPM executable to confirm that it is installed. You would type "which npm" into the terminal, you should then see the location such as, "/home/thecd/.nvm/versions/node/v18.14.0/bin/npm". If you don't get a location back, then something went wrong during the NodeJS install.

## Uninstall NodeJS

To uninstall NodeJS, you can use NVM again, using the uninstall option it provides. In this example, we are uninstalling the LTS version of Node. If you need to uninstall a specific version number, just replace "--lts" with the version number, such as "v18.14.0".

```
nvm uninstall --lts
```

If you have any questions about NodeJS or writing Javascript code, leave a comment down below
