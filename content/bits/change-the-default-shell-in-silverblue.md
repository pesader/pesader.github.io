---
title: "Change the default shell in Silverblue"
date: 2023-04-02T20:22:59-03:00
draft: false
tags: [Silverblue, shell]
---

Fedora does not include `chsh` for security reasons, but you can still change
your default shell using the command below:

```bash
sudo usermod -s $PATHTOSHELL $USERNAME
```

For example, to change the default shell to zsh:

```bash
sudo usermod -s $(which zsh) $USERNAME
```

In my experience, a reboot was necessary for it to take effect.

**Sources**:
[\[1\]](https://discussion.fedoraproject.org/t/how-to-change-the-default-shell-on-fedora-silverblue-chsh-is-not-available/78361/7)
