---
layout: post
date: 2022-09-05
title: "v0.26.0: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version v0.26.0, released just a few days ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - Abstract storage
  - hexpm
---

[DZone](https://dzone.com/articles/easy-way-to-get-your-own-binary-repository) has published our article about Artipie: 
[An Easy Way to Get Your Own Binary Repository](https://dzone.com/articles/easy-way-to-get-your-own-binary-repository). 
We will be happy to get any comments about it! 

[v0.26.0](https://github.com/artipie/artipie/releases/tag/v0.26.0) was released on August 31. We have 
great news:

> New release includes support for [HexPM](https://www.hex.pm/) repository - package manager for Elixir and Erlang. 

If you are interested how to configure and use HexPM repository, visit [this page](https://github.com/artipie/artipie/wiki/hexpm) 
in Wiki, to learn more about repository internals and implementation, check [hexpm-adapter GitHub repository](https://github.com/artipie/hexpm-adapter).

Here are several more important features we worked on in August:

- [Artipie Abstract Storages](https://github.com/artipie/asto) were restructured and improved to 
provide a possibility to integrate and use [custom storage](https://github.com/artipie/artipie/wiki/Configuration-Storage#custom-storage) implementations;
- We [started to develop test framework](https://github.com/artipie/asto/issues/445) that will allow 
verifying any Storage implementation;
- [Added tests](https://github.com/artipie/artipie/issues/1104) to verify [user groups permissions for repository](https://github.com/artipie/artipie/wiki/Configuration-Repository-Permissions)
- Dependencies were updated in the following adapters: nuget, docker, conda, debian, files, maven, npm. These
adapters were released and updated in new Artipie release;
- Artipie [Wiki](https://github.com/artipie/artipie/wiki) was fully restructured and upgraded.

If you have any question, suggestion or notes, please, do not hesitate to comment this blog post or
contact us in [Telegram](https://t.me/artipie).