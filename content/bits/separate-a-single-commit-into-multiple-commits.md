---
title: "Separate your latest commit into multiple commits"
date: 2023-03-31T18:55:47-03:00
draft: false
tags: [git]
---

Separating each non-breaking change into a different commit is a good way of
making the history of changes (`git log`) easily understandable for yourself
and for other people who may check out your code (e.g. reviewers, maintainers,
etc). To do that, run:

```bash
git reset --soft HEAD~
git restore --staged .
```
