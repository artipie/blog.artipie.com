---
layout: post
date: 2020-08-13
title: "August 2020 release notes"
author: olenagerasimova
description: |
  Key features and improvements description.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - maven
  - pypi
  - docker
image: /images/2020/08/new-is-always-better.jpg
jb_picture:
  caption: How I Met Your Mother (2005-2014) by Craig Thomas and Carter Bays
---

{% jb_picture_body %}

[v0.10](https://github.com/artipie/artipie/releases/tag/0.10) was released on August 31, 
here is the list of key features introduced this month:

### Maven adapter
Maven deploy workflow improved:
- support checksum and etag headers
- artifacts validation on upload
- proxy cache verification implemented

### Pypi support
[Pypi-adapter](https://github.com/artipie/pypi-adapter) was released and added to Artipie, we
now provide Python Repository which `pip` or `twine` can perfectly understand.

### Storage locking system
We implemented distributed cluster [lock](https://github.com/artipie/asto/issues/214) mechanism 
to provide safe storage modification, [expiration](https://github.com/artipie/asto/issues/231) 
and retry operations are also supported. 
Distributed storage locks are already used in 
[rpm-adapter](https://github.com/artipie/rpm-adapter/issues/340).

### Artipie evolution
- Metrics for traffic (upload and download) and repository sizes 
[are now visible](https://github.com/artipie/artipie/issues/425) on the dashboard.
- Health check endpoints [added](https://github.com/artipie/artipie/issues/425)

### Permissions support in gem-adapter
[Authorization mechanisms added](https://github.com/artipie/gem-adapter/issues/45) 
to gem-adapter.