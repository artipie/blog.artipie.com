---
layout: post
date: 2023-05-02
title: "v0.30.0: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version v0.30.0, released just a few days ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - Abstract storage
  - Security policy
  - Permissions
  - Filtering
  - Rest API
---

Artipie new version [v0.30.0](https://github.com/artipie/artipie/releases/tag/v0.30.0) was released on May 2. 
In the previous month we added several features, here are the main three of them:

- Artifacts filtering provides means to filter out resources of a repository by specifying patterns of resource location. 
Two types of patterns are supported: [regular expressions](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/regex/Pattern.html) and [globs](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/FileSystem.html#getPathMatcher(java.lang.String)).
Also, we support patterns to exclude and to include repository resources. Check our [wiki](https://github.com/artipie/artipie/wiki/Configuration-Repository#filters) for more details.

- Permissions for REST API operation were added. Now, it's possible to configure access for API endpoints and control
what users are allowed to view and/or manage repositories, storage aliases, users, roles. All the details are described 
in [wiki](https://github.com/artipie/artipie/wiki/Configuration-Policy#rest-api-permissions).

- [S3 storage configuration](https://github.com/artipie/artipie/wiki/Configuration-Storage#s3-storage) does not require 
credentials in YAML configuration anymore. Credentials for S3 storage can set via Java System Properties, environmental 
variables, in `~/.aws/credentials` file or any other way supported by default AWS provider.

Thanks for reading, if you have any questions or suggestions, feel free to [create an issue](https://github.com/artipie/artipie/issues/new) or contact us on [Telegram](https://t.me/artipie).
