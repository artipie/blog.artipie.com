---
layout: post
date: 2020-10-28
title: "0.12: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version 0.12, released just a few hours ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - maven
  - artipie rest api
  - users
  - permissions
---

v0.12 was released on NN. In October, we focused on extending and adding proxy for our adapters. 
First, we implemented basic and bearer authentication in our [http-client](https://github.com/artipie/http-client), 
then supported authentication for proxy in different adapters. Here is the list of the proxy adapters, 
authentication and caching in the local storage can be configured for each proxy:

- [docker-proxy](https://github.com/artipie/artipie/tree/master/examples/docker#docker-proxy-repo) 
(also supports `push` operation to the local storage)
- [maven-proxy](https://github.com/artipie/artipie/tree/master/examples/maven) (multiple remotes are supported)
- [npm-proxy](https://github.com/artipie/artipie/tree/master/examples/npm#npm-proxy-repo)
- [pypi-proxy](https://github.com/artipie/artipie/tree/master/examples/pypi#python-proxy)
- [files-proxy](https://github.com/artipie/artipie/tree/master/examples/binary#proxy-binary-repo)

We also worked on another features in Artipie:
- pypi-adapter now [supports](https://github.com/artipie/pypi-adapter/issues/135) `pip search` command
- field `time` is [supported](https://github.com/artipie/npm-adapter/issues/119) now on update in npm-adapter 
- we introduced different local storage [cache mechanisms](https://github.com/artipie/asto/issues/284) in asto, these implementations 
are used in all our proxy-adapters
- [authentication mechanisms](https://github.com/artipie/http/issues/247) in http was simplified and improved 
- integration tests were implemented in artipie for [maven-proxy](https://github.com/artipie/artipie/issues/628), [NuGet](https://github.com/artipie/artipie/issues/602), 
[npm](https://github.com/artipie/artipie/issues/604) and [pypi-proxy](https://github.com/artipie/artipie/issues/715)