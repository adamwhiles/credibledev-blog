---
title: "Fix Virtual Keyboard in Chromium Apps in KDE Wayland"
created: 2024-08-17
date: 2024-08-17
categories: 
  - linux
authors: 
  - thecd
description: "KDE Wayland edition may have issues displaying the virtual keyboard in Chromium apps such as Chrome and Microsoft Edge. This is easily fixed with launch flags"
---

I have a 2-1 laptop from Lenovo and recently installed Arch linux from scratch on it, only to find out that the onscreen keyboard didn't function properly when I launched Microsoft Edge or Chrome. This seems to only be a problem with the Wayland edition of KDE and Chromium based apps. Even if I manually opened the virtual keyboard, the key mappings were not correct. When I pressed the number 1 on the virtual keyboard would output a ! instead.

Through a bit a research and many forums posts, I found a solution that worked. In my specific case, I use the Flatpak version of Microsoft Edge which required a bit more research to apply the fix.

> If you are thinking about using Linode but don't have an account yet. Take advantage of the [free $100 60-day credit using this link.](https://www.linode.com/lp/refer/?r=25859d5135efc6f773fd56ab42ec3e7a1cc5e83b) Plus, you’re helping me to keep creating content.

## Fix for Virtual Keyboard

If you don't have the Flatpak version of the Chromium based app like Chrome or Edge, you can simply add these additional flags to the command you use to launch the app.

```
--enable-wayland-ime --ozone-platform=wayland --enable-features=UseOzonePlatform
```

Whenever you launch the app with these flags, the virtual keyboard will appear and the keys will be mapped properly.

## Fix for Virtual Keyboard and Flatpak Apps

The fix for Flatpak apps, such as Microsoft Edge in my case, is to edit the edge-flags.conf file with the flags shown below. 

The edge-flags.conf or chrome-flags.conf (if you're using Chrome) may not exist by default. If it doesn't, go ahead and create it with the following file contents.

The edge-flags.conf or chrome-flags conf file should be placed in the following directory: **~/.var/app/com.microsoft.edge/config/** or for **~/.var/app/com.google.chrome/config/**
```
--enable-wayland-ime
--ozone-platform=wayland
--enable-features=UseOzonePlatform
```

That's it, next time you launch Chrome or Edge, the virtual keyboard will work properly.

## BONUS: Which Virtual Keyboard to Use on Arch Linux With KDE?

Personally I use Maliit as my virtual keyboard and it works fine for my use cases. After the changes I made above, it appears when in tablet mode and works as expected. On arch, you can install it using the following command.

```
sudo pacman -S maliit-keyboard
```

After install, you may need to logout and back in.

If your screen doesn't rotate properly in tablet mode, you may also want to install iio-sensor-proxy as well.

```
sudo pacman -S iio-sensor-proxy
```