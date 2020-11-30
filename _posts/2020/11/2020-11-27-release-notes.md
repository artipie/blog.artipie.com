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
  - bearer authentication
  - rpm-adapter
  - docker-adapter
  - nuget-adapter
  - pypi-adapter
---

[v0.13](https://github.com/artipie/artipie/releases/tag/0.13) was released on November 27. 
Here is the list of the key changes:

- [rpm-adapter](https://github.com/artipie/rpm-adapter): we introduce an [instrument](https://github.com/artipie/rpm-adapter/issues/359) to properly 
verify correctness of `repomd.xml`, any errors with metadata `xmls` are [properly](https://github.com/artipie/rpm-adapter/issues/323) handled now,
added [subdirectories support](artipie/rpm-adapter#376) in RPM repository, improved  [test coverage](https://github.com/artipie/rpm-adapter/issues/227) 
and finalize incremental update feature

- [docker-adapter](https://github.com/artipie/docker-adapter) was [migrated](https://github.com/artipie/docker-adapter/issues/341) to Java 8, 
[configurable Docker storage](https://github.com/artipie/docker-adapter/issues/349) layout was added to the adapter

- [nuget-adapter](https://github.com/artipie/nuget-adapter/issues/117) became non-blocking

- [management-api](https://github.com/artipie/management-api) repository was created to contain
 all Artipie API and dashboard related classes

- [helm-adapter](https://github.com/artipie/helm-adapter): we [added verification](https://github.com/artipie/helm-adapter/issues/77) for `index.yaml` 

- [pypi-adapter](https://github.com/artipie/pypi-adapter) now supports [names normalization](https://github.com/artipie/pypi-adapter/issues/147) in proxy 

- We implemented minimal support for [Bearer authentication](https://github.com/artipie/http/issues/261)

- Integration tests for Ruby Gems and Helm were implemented, thus all [repository types are now covered](https://github.com/artipie/artipie/issues/389) with end-to-end tests