---
title: "Add a Hugo theme as a git submodule"
date: 2023-04-02T10:17:17-03:00
draft: false
tags: [Hugo, git]
---

Head to the root directory of your Hugo project and run:

```bash
git submodule add https://gitlab.com/$OWNER/$THEME themes/$THEME
git submodule init --recursive themes/$THEME
```

Later, when you want to sync the submodule with its remote, run:

```bash
git submodule update --remote themes/$THEME
```
