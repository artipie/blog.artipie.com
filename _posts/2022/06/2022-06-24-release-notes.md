---
layout: post
date: 2022-06-24
title: "v0.24.0: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version v0.24.0, released just a few hours ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - Abstract storage
  - dashboard
---

Hello, it's been a while since the last Artipie blog post. Dispute of the absence of the posts, 
Artipie has been constantly developing, growing and improving the whole time. 
Today, we want to introduce our [roadmap](https://github.com/orgs/artipie/projects/3), invite you to
join our [Telegram](https://t.me/artipie) group and remind you, that we have 
[central.artipie.com](https://central.artipie.com/) for private repository hosting. Artipie central now
supports authorization via GitHub, generate [github access token](https://github.com/settings/tokens) and 
use `github.com/your_username` as login (your GitHub username with `github.com/` prefix) and
access token as password in Artipie central. If any questions appear, contact us in 
[Telegram](https://t.me/artipie).

Here is a list of the repositories types Artipie now support:
- Maven - Java artifacts and dependencies
- Docker - Docker containers repository
- NPM - JavaScript code sharing and packages store
- PyPI - Python packages index
- Anaconda - built packages for data science
- RPM - `.rpm` (linux binaries) packages repository
- GEM - RubyGem hosting service
- Go - Go packages storages
- Files (binary) storage - host any files you like
- Helm - Helm charts repository
- NuGet - hosting service for `.NET` packages
- Debian - Debian linux packages repository
- Composer - Package source for PHP packages

You can find example usages and settings for each repository type in this Artipie
[examples](https://github.com/artipie/artipie/tree/master/examples) directory.

In the past several month, we were working on:

- Developing Artipie [dashboard](https://github.com/artipie/front/issues/6) and [management API](https://github.com/artipie/front/issues/5). 
Dashboard is already hosted in Artipie Cental, management API documentation is available [here](https://github.com/artipie/front#public-api).
- We are developing [Conan-adapter](https://github.com/artipie/conan-adapter) to support C/C++ packages repository. 
[Integration tests](https://github.com/artipie/conan-adapter/issues/31) are already implemented
- S3 storage [multipart upload](https://github.com/artipie/asto/issues/421) was optimized and improved 
- [Developed SDK](https://github.com/artipie/asto/issues/432) to transform Publishers of ByteBuffers into IOStreams. 
These methods are often required to update repository metadata
- We are [validating and actualizing](https://github.com/artipie/artipie/issues/1031) documentation for each Artipie repository 
