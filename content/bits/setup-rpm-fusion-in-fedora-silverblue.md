---
title: "Setup RPM Fusion in Fedora Silverblue"
date: 2023-03-31T16:24:18-03:00
draft: false
---

If you follow the [official instructions](https://rpmfusion.org/Configuration)
to setup RPM Fusion on Fedora Silverblue, you will install version specific
packages (e.g. `rpmfusion-free-release-37-1.noarch`) that will cause you
trouble on major updates. Fortunately, you can easily replace them with
packages that will follow whichever version of Fedora you are in, thus not
breaking between updates. To do so, simply run:

```bash
rpm-ostree update \
    --uninstall rpmfusion-free-release-<version>.noarch \
    --uninstall rpmfusion-nonfree-release-<version>.noarch \
    --install rpmfusion-free-release \
    --install rpmfusion-nonfree-release
```

Where `<version>` is the version targetted by your current RPM Fusion
installation. You can check that out by running:

```bash
rpm-ostree status
```
