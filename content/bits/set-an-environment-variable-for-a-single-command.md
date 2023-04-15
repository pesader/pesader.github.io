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

**Sources**:
[\[1\]](https://wiki.gnome.org/Projects/GTK/Inspector)
[\[2\]](https://unix.stackexchange.com/questions/7309/set-the-language-for-a-single-program-execution)
[\[3\]](https://docs.flatpak.org/en/latest/flatpak-command-reference.html)
