---
title: "Entering the rabbit hole of GNOME Network Displays"
date: 2023-04-03T15:34:02-03:00
draft: false
hero: hero.png
thumbnail: thumbnail.png
tags: [GNOME, GSoC]
---

In this blog post I'll walk you through my journey of builiding and
contributing to GNOME Network Displays, a standalone application for
screencasting. Fasten your seatbelts, it's gonna be a bumpy ride!

# Building the application

First, I cloned the
[repository](https://gitlab.gnome.org/GNOME/gnome-network-displays) of the
application and created a fresh Fedora Rawhide (currently labelled as 39)
toolbx for this project. To do that I ran:

```bash
toolbox create gnome-network-displays --image registry.fedoraproject.org/fedora-toolbox:39
```

Following the build instructions on the `README.md` file I ran:

```bash
sudo dnf builddep gnome-network-displays
meson build
ninja -C build
```

But I got this error:

```log
ninja: error: '/usr/lib64/libavahi-gobject.so', needed by 'src/gnome-network-displays', missing and no known rule to make it
```

That's when one of my favorite `dnf` subcommands came into play: `dnf provides`
tells you which package provides a given file path. So, to find out how to
install the missing `/usr/lib64/libavahi-gobject.so` on my toolbx, I ran:

```bash
$ dnf provides /usr/lib64/libavahi-client.so
Fedora rawhide openh264 (From Cisco) - x86_64                                              426  B/s | 2.5 kB     00:05    
Fedora - Rawhide - Developmental packages for the next Fedora release                      4.3 MB/s |  66 MB     00:15    
Fedora - Modular Rawhide - Developmental packages for the next Fedora release              351 kB/s | 1.6 MB     00:04    
avahi-devel-0.8-20.fc38.x86_64 : Libraries and header files for avahi development
Repo        : @System
Matched from:
Filename    : /usr/lib64/libavahi-client.so

avahi-devel-0.8-20.fc38.x86_64 : Libraries and header files for avahi development
Repo        : rawhide
Matched from:
Filename    : /usr/lib64/libavahi-client.so
```

Alright, so the missing package is `avahi-devel`. After installing that, I got
a another error:

```log
ninja: error: '/usr/lib64/libavahi-gobject.so', needed by 'src/gnome-network-displays', missing and no known rule to make it
```

Let's hear what `dnf provides` has to say about this one:

```bash
$ dnf provides /usr/lib64/libavahi-gobject.so
Last metadata expiration check: 0:30:58 ago on Mon 03 Apr 2023 04:28:17 PM -03.
avahi-gobject-devel-0.8-20.fc38.x86_64 : Libraries and header files for Avahi GObject development
Repo        : rawhide
Matched from:
Filename    : /usr/lib64/libavahi-gobject.so
```

Looks like `avahi-gobject-devel` was the culprit this time around, so I
installed it and attempted to build the application again and... Success!

Since the build dependencies of the `gnome-network-displays` rpm package were
clearly outdated, I made a [pull
request](https://src.fedoraproject.org/rpms/gnome-network-displays/pull-request/2)
over the Fedora Package Sources to update it.

# Running the application

Equipped with my own build of GNOME Network Displays, I decided to see what it
was all about. I enabled Miracast on my TV and waited for the application to
pick it up. And waited. And waited. And waited.

Something was off.

My first suspicion was firewall configuration and (thankfully) I was right.
Browsing the repository of GNOME Network Displays I found out that [this
commit](https://gitlab.gnome.org/GNOME/gnome-network-displays/-/commit/c2a81a501ec1eb231c05dd47416fe935d6573c13)
added integration with the default firewall utility of Fedora Silverblue.

All I needed to do was change my firewall zone to WiFi P2P.

{{< figure src="firewall.png" alt="Firewall configuration screenshot" width=100% >}}

Upon doing that, my device started being detected! Once I clicked it though:

{{< figure src="codecs.png" alt="Codec disclaimer screenshot" width=100% >}}

To proceed, I installed the GStreamer OpenH264 Encoder (which is provided by
the `gstreamer1-plugin-openh264` package). With that I was finally able to
start the connection, but the display mirroring didn't actually work.

```log
** (gnome-network-displays:17808): DEBUG: 17:47:13.929: Got state change notification from streaming sink to state ND_SINK_STATE_WAIT_SOCKET
** (gnome-network-displays:17808): DEBUG: 17:47:59.487: WFDP2PProvider: Device state changed. It is now 120. Reason: 11
** (gnome-network-displays:17808): DEBUG: 17:47:59.494: WfdServer: Finalize
** (gnome-network-displays:17808): DEBUG: 17:47:59.495: WfdMediaFactory: Finalize
** (gnome-network-displays:17808): DEBUG: 17:47:59.495: Got state change notification from streaming sink to state ND_SINK_STATE_ERROR
** (gnome-network-displays:17808): DEBUG: 17:47:59.518: WFDP2PProvider: Device state changed. It is now 30. Reason: 0
** (gnome-network-displays:17808): DEBUG: 17:47:59.771: WFDP2PProvider: Peer removed
** (gnome-network-displays:17808): DEBUG: 17:47:59.771: MetaSink: Priority sink updated. Priority: 100
```

From the logs, it looks like timeout, but I decided to investigate that later.

# Making a contribution

One of the first things I noticed upon launching GNOME Network Displays was
that I could not move its window by dragging its header bar not resize its
window by dragging its borders. I spent some hours trying to fix that but
didn't manage to.

After all, I acknowledged my own defeat and decided to make [a simple
contribution](https://gitlab.gnome.org/GNOME/gnome-network-displays/-/merge_requests/182)
fixing some typos. However, there will be no truce! Mark my words:

GNOME Network Displays, we will meet again!
