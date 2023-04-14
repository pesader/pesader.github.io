---
title: "Set an environment variable for a single command"
date: 2023-04-02T10:54:36-03:00
draft: false
---

You may want to set an environment variable for a single command, to test out a
translation without having to change your system-wide language settings (e.g.
`LANG=pt_BR.UTF-8`) or to enable debug flags (e.g. `G_MESSAGES_DEBUG=all`).

To do that, simply prepend the variable attribution to the command like so:

```bash
VARIABLE=value command
```

For flatpaks, which run on their own isolated environment, you must use the
`--env` flag:

```bash
flatpak run com.example.Application --env VARIABLE=value
```
