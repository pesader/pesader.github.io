---
title: "Show which files were changed by a commit"
date: 2023-10-19T20:10:17-03:00
draft: false
tags: [git]
---

Don't you love the summary of modified, deleted, and created files that pops up
when you run `git pull`? You can get the same summary on `git log` with:

```bash
git log --stat --summary
```

Here's an explanation of each flag:

- `--stat`: shows the modified files
- `--summary`: shows the created and deleted files

**Sources**:
[\[1\]](https://stackoverflow.com/a/1230094)
