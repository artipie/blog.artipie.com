---
layout: post
date: 2022-07-29
title: "v0.25.0: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version v0.25.0, released just a few hours ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - Abstract storage
  - dashboard
---

This month we mostly focused on Artipie documentation and wiki improvements, we are also preparing 
some articles and posts. The links will be available here as soon as we publish them. Besides, the
following changes were made: 
- [Single repository on port](https://github.com/artipie/artipie/wiki/Configuration-Repository#single-repository-on-port) use case was [fixed](https://github.com/artipie/artipie/issues/1041): 
Artipie allows to serve repository on individual port;
- Artipie asto (abstract data storages implementation) module [was restructured](https://github.com/artipie/asto/issues/436) into Maven multi-module project; 
now each storage implementation can be added as a new module
- [Redis](https://redis.io/) storage was [implemented](https://github.com/artipie/asto/pull/444) 
- File proxy adapter now supports [caching](https://github.com/artipie/artipie/issues/1056) 

Several month ago, we extended rpm-adapter with the feature to set a schedule for repository update. 
This feature can be enabled in repository configuration:

```yaml
repo:
  type: rpm
  storage:
    type: fs
    path: /var/artipie/centos
  settings:
    digest: sha256 # digest algorithm for rpm packages checksum calculation, sha256 (default) and sha1 are supported
    naming-policy: sha1 # naming policy for metadata files: plain, sha1 or sha256 (default) prefixed
    filelists: true # calculate metadata filelists.xml, true by default
    # repository update mode:
    update:
      # update metadata on package upload
      on: upload
      # or schedule the update
      on:
       cron: 0 2 * * *
```

New `update` section allows to set update mode: either update the repository when the package is uploaded via HTTP
```yaml
repo:
  type: rpm
  ...
  settings:
    update:
      on: upload
```
or schedule the update via `cron` field. As rpm repository update process can be time-consuming for large 
repositories and new packages as a rule are not often added, it can be convenient to schedule the update for every night at 2 AM:
```yaml
repo:
  type: rpm
  ...
  settings:
    update:
      on: 
        cron: 0 2 * * *
```

If you have any question, suggestion or notes, please, do not hesitate to comment this blog post or
contact us in [Telegram](https://t.me/artipie).