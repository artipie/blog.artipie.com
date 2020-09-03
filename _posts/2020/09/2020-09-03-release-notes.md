---
layout: post
date: 2020-09-03
title: "0.10: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version 0.10, released just a few days ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - maven
  - pypi
  - docker
---

[v0.10](https://github.com/artipie/artipie/releases/tag/0.10) was released on August 31,
here is the list of key features introduced this month.

<!--more-->

Maven deploy workflow improved:
- [support checksum and etag headers](https://github.com/artipie/maven-adapter/issues/117)
- [artifacts validation on upload](https://github.com/artipie/maven-adapter/issues/113)
- [proxy cache verification](https://github.com/artipie/maven-adapter/issues/146) implemented

[Pypi-adapter](https://github.com/artipie/pypi-adapter) was released and added to Artipie, we
now provide Python Repository which `pip` or `twine` can perfectly understand.

We implemented distributed cluster [lock](https://github.com/artipie/asto/issues/214) mechanism
to provide safe storage modification, [expiration](https://github.com/artipie/asto/issues/231)
and retry operations are also supported.
Distributed storage locks are already used in
[rpm-adapter](https://github.com/artipie/rpm-adapter/issues/340).

Artipie evolution:

- Metrics for traffic (upload and download) and repository sizes
[are now visible](https://github.com/artipie/artipie/issues/425) on the dashboard.
- Health check endpoints [added](https://github.com/artipie/artipie/issues/425)

[Authorization mechanisms added](https://github.com/artipie/gem-adapter/issues/45)
to gem-adapter.