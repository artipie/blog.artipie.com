---
layout: post
date: 2021-02-26
title: "0.16: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version 0.16, released just a few hours ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - docker-adapter
  - composer-adapter
  - debian-adapter
  - npm-adapter
  - asto
---

[v0.16](https://github.com/artipie/artipie/releases/tag/0.16) was released on February 16. 
Here is the list of other implemented features and important fixes:
- Docker-adapter now supports [overwrite](https://github.com/artipie/docker-adapter/issues/434) 
permission for tags
- Release index file is now fully [supported](https://github.com/artipie/debian-adapter/issues/41) in Debian-adapter
- `FileStorage` `delete` operation was improved: now we also remove [empty directories](https://github.com/artipie/asto/issues/302) 
recursively along with the removed file. This change fixed connected 
[bug](https://github.com/artipie/docker-adapter/issues/435) in Docker-adapter
- Basic authentication was [added](https://github.com/artipie/composer-adapter/issues/71) to Composer-adapter
- Writing big files operation performance was [improved](https://github.com/artipie/asto/pull/304) in Asto
- Npm-adapter now [supports](https://github.com/artipie/npm-adapter/issues/188) `tgz` upload, 
to publish the package simple `curl` call can be used: `curl PUT your-archive.tgz`. Also, `unpublish`
command now can remove the specified version of the package, not only the package entirely.

#### Granular Permissions For Docker Registry
Docker-adapter supports granular permissions, which means that some operations can be granted for 
specific scope and image. Here is the example docker repository settings yaml:
```yaml
repo:
  type: docker
  storage:
    type: fs
    path: /var/artipie/data
  permissions:
    alice:
      - repository:my-alpine:*
      - repository:ubuntu-latest:pull
      - repository:some-image:overwrite
      - repository:some-image:push
    mike:
      - repository:some-image:push
      - repository:some-image:pull
    bob:
      - registry:base:*
      - registry:catalog:*
```
Each permission consists of three parts: `scope:name:action`, `scope` can be either "registry" for 
the registry level operations or "repository". `Name` is the access resource name, `action` can be 
one of `pull`, `push`, `overwrite` or `*` (`*` stands for any action), `overwrite` works 
for overwriting existing tags and allows creating new tags by default. 
