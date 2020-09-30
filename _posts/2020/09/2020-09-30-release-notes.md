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

Artipie [REST API](https://github.com/artipie/artipie/blob/master/REST_API.md) allows:
- create repositories
- manage users
- manage repository permission
- list repository items

We also introduced the following features in Artipie:
- [user groups](https://github.com/artipie/artipie/issues/573): users can be added to the groups and 
repository permissions can be granted to the group, not individual users. [Readers group](https://github.com/artipie/artipie/issues/572) 
may be assigned to users by default
- [different ports for repositories](https://github.com/artipie/artipie/issues/570): Artipie can now be 
configured to listen on multiple ports, port can be specified for each repository
- integration tests were implemented for [docker](https://github.com/artipie/artipie/issues/449), 
[maven](https://github.com/artipie/artipie/issues/535) 
and [files](https://github.com/artipie/artipie/issues/603) adapters 

