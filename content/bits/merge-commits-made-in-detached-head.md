---
title: "Merge commits made to detached HEAD"
date: 2023-03-31T17:05:16-03:00
draft: false
tags: [git]
---

Simply make a new branch out of it!

```bash
git branch temporary
git checkout main
git merge temporary
```

**Sources**:
[\[1\]](https://stackoverflow.com/questions/7124486/what-to-do-with-commit-made-in-a-detached-head)
