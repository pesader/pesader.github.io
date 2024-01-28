---
title: "View new commits on git submodule"
date: 2024-01-28T16:32:01-03:00
draft: false
tags: []
---

To see a list commits that have been added to a git submodule, run:

```bash
git diff --submodule
```

It may also be useful to know which commit the submodule points to:

```bash
git submodule status
```

**Sources**:
[\[1\]](https://git-scm.com/book/fa/v2/Git-Tools-Submodules)
[\[2\]](https://stackoverflow.com/questions/20655073/how-to-see-which-commit-a-git-submodule-points-at)

