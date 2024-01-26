---
title: "Make electron apps sharp under Wayland"
date: 2024-01-26T16:49:03-03:00
draft: false
tags: [GNOME, Wayland, Electron]
---

Electron apps often look blurry on GNOME under Wayland, especially if you are using the experimental fractional scaling feature. To fix that, run the electron application with the following parameters:

```
--enable-features=UseOzonePlatform --ozone-platform=wayland
```

**Sources**:
[\[1\]](https://github.com/microsoft/vscode/issues/72759)
[\[2\]](https://discourse.joplinapp.org/t/enable-native-support-for-wayland-in-linux/15823/6)
