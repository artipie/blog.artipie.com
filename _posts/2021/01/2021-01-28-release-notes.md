---
layout: post
date: 2021-01-28
title: "0.15: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version 0.15, released just a few hours ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - docker-adapter
  - helm-adapter
  - debian-adapter
---

[v0.NN](https://example/link) was released on January NN. 
We are happy to announce that minimal support for [Debian repository](https://wiki.debian.org/DebianRepository) was added to Artipie:
you can [configure](https://github.com/artipie/artipie/tree/master/examples/debian) the repository 
which [`apt-get`](https://en.wikipedia.org/wiki/APT_(software)) will be able to work with. 

[Npm-adapter](https://github.com/artipie/npm-adapter) functionality was extended with the following commands support:
- [`npm dist-tag`](https://github.com/artipie/npm-adapter/issues/155) for managing tags of package versions
- [`npm deprecate`](https://github.com/artipie/npm-adapter/issues/156) for deprecating and un-deprecating the package
- [`npm unpublish`](https://github.com/artipie/npm-adapter/issues/154) to un-publish entire package

[Docker-adapter](https://github.com/artipie/docker-adapter) evolution:
- In practice, it seems that blobs are always uploaded in single chunk, that's why we 
[optimized](https://github.com/artipie/docker-adapter/issues/424) this particular upload case
- Image level permissions are now [supported](https://github.com/artipie/docker-adapter/issues/417), meaning, that
you can define which user has `read` or `write` access to particular image

And here is the list of other implemented features:
- Helm-adapter now [supports](https://github.com/artipie/helm-adapter/issues/84) `deleteByName` 
and `deleteByNameAndVersion` commands and `--merge` flag for [indexing](https://github.com/artipie/helm-adapter/issues/89) 
- Php-adapter became fully [non-blocking](https://github.com/artipie/composer-adapter/issues/66)
- Nuget-adapter endpoints were [refactored](https://github.com/artipie/nuget-adapter/issues/124) not to 
interact with data storage directly 
