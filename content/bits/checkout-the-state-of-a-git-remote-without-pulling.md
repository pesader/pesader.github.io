---
title: "Checkout the state of a git remote without pulling"
date: 2023-04-02T10:27:41-03:00
draft: false
tags: [git]
---

Sometimes you want to see what someone else has been up to in their own fork of
a project but you don't to merge their changes into any branch just yet. To do
that, run:

```bash
git remote add downstream https://gitlab.com/$CONTRIBUTOR/$REPONAME
git checkout downstream/$BRANCH
```

Later, if you want to update your local references, run:

```bash
git remote update
```

**Sources**:
[\[1\]](https://linuxhint.com/git-pull-remote-branch-without-merge/)
[\[2\]](https://stackoverflow.com/questions/17712468/what-is-the-difference-between-git-remote-update-git-fetch-and-git-pull)
