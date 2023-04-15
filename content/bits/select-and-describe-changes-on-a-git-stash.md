---
title: "Select and describe changes on a git stash"
date: 2023-03-31T18:45:05-03:00
draft: false
---

Running the command line below will allow you to interactively select which
hunks of change you want to stash.

```bash
git stash push -p -m "message explaining the stashed changes"
```

**Sources**:
[\[1\]](https://stackoverflow.com/questions/3040833/how-do-i-stash-only-one-file-out-of-multiple-files-that-have-changed)
