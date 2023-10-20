---
title: "Export a public GPG key in plain text"
date: 2023-10-19T20:29:09-03:00
draft: false
tags: [gpg]
---

Replace `$NAME` with the name of your key and run:

```bash
gpg --export --armor $NAME
```

You can also abbreviate the `--armor` flag with `-a`.

**Sources:**
[\[1\]](https://www.gnupg.org/gph/en/manual/x56.html)
[\[2\]](http://irtfweb.ifa.hawaii.edu/~lockhart/gpg/)
