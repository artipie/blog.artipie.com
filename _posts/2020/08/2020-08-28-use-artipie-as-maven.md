---
layout: post
date: 2020-08-28
title: "Using Artipie as a maven repository"
author: Sammers21
description: This blog post explains how to use Artipie as maven repository.
keywords:
  - artipie
  - maven
  - java
  - hosting of artifacts
---

## Introduction

Almost every company that does Java development has private Maven repository,
where they store all the artifacts. As a developer you might be wondering
how to setup our own.

This blog post will cover how you can setup your own Maven repository with Artipie.

## Installation

Create a separated directory with the following `artipie.yaml` file inside:

```yml
meta:
  storage:
    type: fs
    path: /var/artipie/configs
  layout: flat
```

Then you can install and run artipie with docker:

```bash
$ docker run -d --name artipie \
             -v $(pwd)/artipie.yaml:/etc/artipie.yml \
             -v $(pwd):/var/artipie \
             -p 8080:80 \
             artipie/artipie:latest
```

## Configuring Artipie as a maven repository

Create `configs` directory and the following `my-maven.yaml` file inside:

```yml
repo:
  type: maven
  storage:
    type: fs
    path: /var/artipie/data
```

As a results, you will have the following files structure:

```bash
.
├── artipie.yaml
├── configs
    └── my-maven.yaml
```

If you have completed all the instructions correctly now you should be able to use the repository: deploy and install Maven artifacts.

## Configuring project to use your Artipie maven repository

If you want to `mvn deploy` your project to Artipie, add the following to project's `pom.xml`:

```xml
<distributionManagement>
    <repository>
        <id>artipie</id>
        <url>http://localhost:8080/my-maven</url>
    </repository>
</distributionManagement>
```

If you want to `mvn install` deployed packages from Artipie, add the following to project's `pom.xml`:

```xml
<repositories>
    <repository>
        <id>artipie</id>
        <url>http://localhost:8080/my-maven</url>
    </repository>
</repositories>
```

That is it.

## Advanced options

Apart from demonstrated possibilities, Artipie Maven supports:
group repositories, proxies and authorization.
Check out the corresponding
[documentation section](https://github.com/artipie/artipie/tree/master/examples/maven)
for more details.

## Conclusion

In this blog post it's been explained how to setup own Maven repository and how to
configure your project to use it.
