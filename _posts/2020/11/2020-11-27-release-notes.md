---
layout: post
date: 2020-11-27
title: "0.13: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version 0.13, released just a few hours ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - maven
  - artipie rest api
  - users
  - permissions
---

[v0.13](https://add/link) was released on November 30. 
Here is the list on the key changes:

- [rpm-adapter](https://github.com/artipie/rpm-adapter): we introduce an [instrument](https://github.com/artipie/rpm-adapter/issues/359) to properly 
verify correctness of `repomd.xml`, any errors with metadata `xmls` are [properly](https://github.com/artipie/rpm-adapter/issues/323) handled now,
added [subdirectories support](artipie/rpm-adapter#376) in RPM repository, increased [test coverage](https://github.com/artipie/rpm-adapter/issues/227)

- [docker-adapter](https://github.com/artipie/docker-adapter) was [migrated](https://github.com/artipie/docker-adapter/issues/341) to Java 8, 
[configurable Docker storage](https://github.com/artipie/docker-adapter/issues/349) layout was added to the adapter

- [nuget-adapter](https://github.com/artipie/nuget-adapter/issues/117) became non-blocking

- [management-api](https://github.com/artipie/management-api) repository was created to contain
 all Artipie API and dashboard related classes

- [helm-adapter](https://github.com/artipie/helm-adapter): we [added verification](https://github.com/artipie/helm-adapter/issues/77) for `index.yaml` 

- [pypi-adapter](https://github.com/artipie/pypi-adapter) now supports [names normalization](https://github.com/artipie/pypi-adapter/issues/147) in proxy 

- We implemented minimal support for [Bearer authentication](https://github.com/artipie/http/issues/261)