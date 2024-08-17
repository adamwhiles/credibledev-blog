---
title: "3 Easy Steps: Install VirtualEnv on Arch Linux for Python"
created: 2021-02-24
date: 2021-02-24
categories: 
  - python
tags: 
  - python
  - virtualenv
authors: 
  - thecd
description: "How to setup and use VirtualEnv on Arch Linux. Virtual Python environments are useful when working on multiple Python projects."
cover:
    image: images/install-virtualenv-on-arch-linux.png
url: "/install-virtualenv-on-arch-linux-for-python"
---

## Why Use VirtualEnv?

[Virtualenv](https://pypi.org/project/virtualenv/) allows you to separate specific packages from one project to another. This guide will show you how to easily install virtualenv on Arch Linux. Using Virtualenv allows for easier collaboration and prevents you from having issues with globally installed python packages.

Imagine you have project A that needs a specific version of a package and project B that needs a different version. By using virtualenv, you can have those specific packages installed for each project and keep them separated.

## Setup

First, create a directory for your project and then cd into that directory.

## Install Virtualenv

Note: If you're using Python 3.3 or newer, you do not need to do this since venv is included as part of the base packages.

```
pip install virtualenv
```

## Create a Python Virtual Environment

Depending on how you installed it and what version you have, one of the following commands will create a new virtual environment called venv.

```
python -m venv venv
```

```
python3 -m venv venv
```

```
virtualenv venv
```

## Activate the Virtual Environment

Now that you have the virtual environment created, we still need to activate virtualenv in order to make use of the environment to install our packages.

```
. venv/bin/activate
```

After completing this step, you will notice that your terminal changes. Some will place (env) or (venv) at the beginning of your terminal line. Other terminals and terminal modifications may have different indications but something will change to indicate that you are now in the virtual environment.

At this point, you can proceed to install pip packages and they will be specific to this project.

```
pip install Flask
```

## Exit the Python Virtual Environment

In case you need to leave or deactivate the virtualenv environment run the following command.

```
deactivate
```

That's it, now that you're ready to start coding, check out our guide on [installing VS Code for Manjaro Linux](https://credibledev.com/install-vs-code-on-manjaro-linux/). If you have any questions or would like more information, please let me know in the comments.
