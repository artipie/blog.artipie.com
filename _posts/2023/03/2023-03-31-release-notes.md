---
layout: post
date: 2023-03-31
title: "v0.29.0: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version v0.23.0, released just a few days ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - Abstract storage
  - Security policy
  - Permissions
---

Artipie new version [v0.29.0](https://github.com/artipie/artipie/releases/tag/v0.29.0) was released on March 31. 
The previous months we were working on Artipie security policy and permissions. The goal is to introduce
flexible security model, that can be implemented by users themselves, and transparent 
permissions model, that can be extended in the repository adapter if necessary. We took [Java Security](https://docs.oracle.com/cd/E12839_01/core.1111/e10043/introjps.htm#JISEC1801)
as an example, and created a role-based model to grant and verify user access permissions.
The main implementation components are policy and permissions. 

Policy grants permissions to users and roles, or, in other words, in Artipie, policy is the format 
in which permissions and roles are assigned to users. We provide out of the box policy in `yaml` format, 
but it's also possible to implement any custom policy format and linked it up to Artipie.

Permission grants access to some operations in the repository. Repository (or adapter) requires some
specific permission for some operation and whether allows or not to perform the operation. 
Permissions are inherited from `java.security.Permission` and `java.security.PermissionCollection`, 
there is no way to directly prohibit the operation, it's only possible to allow it. User permissions
are joined from his individual permissions and roles permissions.

To learn more about permission types and settings, check our [Wiki page](https://github.com/artipie/artipie/wiki/Configuration-Policy).