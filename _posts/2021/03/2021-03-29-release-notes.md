---
layout: post
date: 2021-03-27
title: "0.17: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version 0.17, released just a few hours ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - composer-adapter
  - debian-adapter
  - npm-adapter
---

[v0.NN](https://github.com/artipie/artipie/releases/tag/0.NN) was released on March NN. 
Several important features were implemented in Debian-adapter: 
- [GPG](https://en.wikipedia.org/wiki/GNU_Privacy_Guard) clearsign signature is now [supported](https://github.com/artipie/debian-adapter/issues/29) 
by the adapter, meaning that `Release` index files are now signed with gpg;
- [Duplicated packages handling](https://github.com/artipie/debian-adapter/issues/74): while updating 
`Packages` index we now check that the package to add is not present in the repository yet. 
If it does, the old package and metadata are removed and replaced with the new one;
- Debian-repository now [provides](https://github.com/artipie/debian-adapter/issues/51) some `sdk` 
and can be used as a dependency for the debian repository batch-update and indexes generation. For 
more details check [`Debian`](https://github.com/artipie/debian-adapter/blob/master/src/main/java/com/artipie/debian/Debian.java) 
interface and its `Debian.Asto` implementation.

We started to [restructure](https://github.com/artipie/artipie/issues/855) Artipie integration tests, 
changes are mostly infrastructural: now there are two Docker containers started on each integration test, 
Artipie docker image built on package state and client image. Client image differs depending on the 
repository we are testing, it could be `maven:3.6.3-jdk-11` for `maven` repository tests 
or `centos:centos8` to verify `rpm` repository. Thus, our tests work with the image we provide for 
our users guaranteeing its efficiency and credibility.

Here is the list of other implemented features and important fixes:
- Helm-adapter now support [index merging](https://github.com/artipie/helm-adapter/issues/102)
- Composer-adapter [supports](https://github.com/artipie/composer-adapter/issues/23) uploading packages via `PUT` HTTP request,
also we start implementing [remote repository](https://github.com/artipie/composer-adapter/issues/77) support for composer
- Bug with [incorrect paths](https://github.com/artipie/npm-adapter/issues/169) in metadata was fixed in npm-adapter
