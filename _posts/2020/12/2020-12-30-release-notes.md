---
layout: post
date: 2020-12-30
title: "0.14: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version 0.14, released just a few hours ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - docker-adapter
  - gem-adapter
  - debian-adapter
  - REST API
---

[v0.14](https://github.com/artipie/artipie/releases/tag/0.14) was released on December 30. 
This month our two main directions were Docker-adapter and 
management-api transfer. Features added to Docker-adapter:
- Local [catalogs](https://github.com/artipie/docker-adapter/issues/374) and 
[tags](https://github.com/artipie/docker-adapter/issues/373) listing
- Support for mount blob endpoint in [remote](https://github.com/artipie/docker-adapter/issues/390) and 
[local](https://github.com/artipie/docker-adapter/issues/394) repositories
- [Catalogs](https://github.com/artipie/docker-adapter/issues/367) and 
[tags](https://github.com/artipie/docker-adapter/issues/375) support was added for local and proxy repositories

Artipie [API](https://github.com/artipie/management-api/blob/master/REST_API.md) and dashboard were 
transferred to [management-api](https://github.com/artipie/management-api) repository and added minimal 
integration tests for API endpoints in Artipie.

Here is the list of other changes:
- Artipie now [supports](https://github.com/artipie/artipie/issues/797) both .yml and .yaml 
extensions for configs
- Proper path handling in Npm-Proxy was [implemented](https://github.com/artipie/artipie/issues/738)
- Invalid repository configurations are now [properly handled](https://github.com/artipie/artipie/issues/804) on start,
we also added separate setting for [repo configs location](https://github.com/artipie/artipie#additional-configuration)
- Basic authentication support [was added](https://github.com/artipie/gem-adapter/issues/81) to Gem-adapter

We also started to develop [Debian-adapter](https://github.com/artipie/debian-adapter) to support Debian repository. 