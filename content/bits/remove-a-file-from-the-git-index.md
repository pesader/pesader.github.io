---
title: "Remove a file from the git index"
date: 2023-05-16T18:50:26-03:00
draft: false
tags: [git]
---

If you want to stop tracking a file that you commited ages ago (thus not worth
fixing with a `git rebase`), you want to run:

```bash
git rm --cached $FILE
```

**Sources**:
[\[1\]](https://unix.stackexchange.com/questions/1818/how-to-remove-a-file-from-the-git-index)
