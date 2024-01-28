---
title: "bbmalloc"
date: 2024-01-28T17:11:53-03:00
draft: false
tags: [Linux, C]
summary: A custom implementation of malloc and free
---

bbmalloc is a custom implementation of malloc (and free), optimized for big buffers. It uses "sbrk" to request memory to operating system and a doubly linked list to keeps track of available memory chunks.

- Source code: [GitHub](https://github.com/pesader/bbmalloc)
- Technologies: C
