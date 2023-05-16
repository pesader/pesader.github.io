---
title: "Keep your branch up to date with upstream"
date: 2023-04-02T10:42:46-03:00
draft: false
tags: [git]
---

First, pull the upstream changes to your main branch

```bash
git remote add upstream https://gitlab.com/$MAINTAINER/$REPONAME
git pull upstream main
```

Then, rebase your own branch to main:

```bash
git checkout $BRANCH
git rebase main
```

In this case, it is better to rebase instead of merge, because merging will
create a commit while rebasing won't.
