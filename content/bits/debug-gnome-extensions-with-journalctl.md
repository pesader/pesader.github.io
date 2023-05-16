---
title: "Debug GNOME extensions with journalctl"
date: 2023-04-02T11:00:19-03:00
draft: false
tags: [journalctl, systemd, GNOME]
---

To get the logs of a GNOME Extension, you must first find out its UUID (which
will look like `name@author.address.com`). Look for it in the output of:

```bash
ls $HOME/.local/share/gnome-shell/extensions
```

You can then get its logs with the command:

```bash
journalctl -f -o cat GNOME_SHELL_EXTENSION_UUID=name@author.address.com
```

Some logs from ` gjs` (GNOME JavaScript) may also interest you, so you can
checkout the output of:

```bash
journalctl -f -o cat /usr/bin/gjs
```

**Sources**:
[\[1\]](https://gjs.guide/extensions/development/debugging.html#logging)
[\[2\]](https://github.com/GSConnect/gnome-shell-extension-gsconnect/blob/main/CONTRIBUTING.md#typical-workflow)
