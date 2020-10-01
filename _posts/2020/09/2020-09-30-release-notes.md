---
layout: post
date: 2020-09-30
title: "0.11: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version 0.11, released just a few days ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - maven
  - artipie rest api
  - users
  - permissions
---

[v0.11](https://github.com/add/link/to/release) was released on October XX. This month we focused 
on creating [HTTP REST API](https://github.com/artipie/artipie/issues/575) to make Artipie compatible 
with existing products.

Artipie [REST API](https://github.com/artipie/artipie/blob/master/REST_API.md) allows to:
- create repositories
- manage users
- manage repository permission
- list repository items

We also introduced the following features in Artipie:
- [User groups](https://github.com/artipie/artipie/issues/573): users can be added to multiple groups 
and repository permissions can be granted to a group, not to individual users only. [Readers group](https://github.com/artipie/artipie/issues/572) 
may be assigned to users by default
- [Different ports for repositories](https://github.com/artipie/artipie/issues/570): Artipie can now be 
configured to listen on multiple ports, port can be specified for each repository
- Integration tests were implemented for [docker](https://github.com/artipie/artipie/issues/449), 
[maven](https://github.com/artipie/artipie/issues/535) 
and [files](https://github.com/artipie/artipie/issues/603) adapters 
- Files adapter now [supports](https://github.com/artipie/files-adapter/issues/15) `DELETE` operation to remove files from the storage
- [Basic authentication](https://github.com/artipie/go-adapter/issues/62) support was added to Go adapter
- [Distributed locks](https://github.com/artipie/asto/issues/214) were added to Maven and NuGet adapters to avoid race conditions on adding artifacts
- [Maven proxy](https://github.com/artipie/maven-adapter/issues/197) was covered with tests and fixed
- We improved our benchmarks to [compare](https://artipie.github.io/artipie/benchmarks/index.html) performance of multiple Artipie versions