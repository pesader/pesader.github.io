---
title: "Run a command from a flatpak runtime"
date: 2023-04-14T18:36:10-03:00
draft: false
tags: [ffmpeg, flatpak]
---

To run commands that are available on flatpak runtimes, use:

```bash
flatpak run --command=$COMMAND $RUNTIME
```

For example, to run ffmpeg from the Freedesktop runtime:

```bash
flatpak run --command=ffmpeg org.freedesktop.Platform
```

**Sources**: [\[1\]](https://www.reddit.com/r/flatpak/comments/uhhy7y/how_can_i_use_flatpaks_ffmpeg_on_the_terminal/)
