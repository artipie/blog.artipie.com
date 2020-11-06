---
layout: post
date: 2020-11-06
title: "Using Artipie as a maven repository"
author: Alexander Krasnov
description: This blog post explains how to use Artipie as a Maven repository.
keywords:
  - artipie
  - private
  - maven
  - repository
  - registry
  - java
---

## Introduction

Nowadays Apache Maven is [one of the most popular](https://www.baeldung.com/java-in-2019#build-tools-adoption) build management tool for Java. Many companies that do Java development have private Maven repositories, where they store all the artifacts. For example, the team does not work in open source and has some private artifacts. This team needs to share easily and quickly among themselves and with other developers from their company. Or you might be wondering how to set up an own repository for a pet project. [Artipie](https://github.com/artipie/artipie) allows you to solve this problem as it is a binary artifact management tool. In the blog post I will share with you how to configure Artipie and project for this purpose. Let's start!

## Installation

In the simplest case, you need a file with the contents below. We want to use file storage therefore we specify `fs` as the type. At first, create a separate directory with the following `artipie.yaml` file inside:

```yml
meta:
  storage:
    type: fs
    path: /var/artipie/configs
```

If you want to use authentication for users then you need to add a section with credentials to the `artipie.yaml`. In this case, the file with settings should look like this:

```yml
meta:
  storage:
    type: fs
    path: /var/artipie/configs
  credentials:
    type: file
    path: _credentials.yml
```

After that you can install and run Artipie with docker:

```bash
$ docker run -d --name artipie \
             -v $(pwd)/artipie.yaml:/etc/artipie.yml \
             -v $(pwd):/var/artipie \
             -p 8080:80 \
             artipie/artipie:latest
```

## Configuring Artipie as a maven repository

In the previous step we created a file with settings for Artipie. Now let's see what the configuration file for the repository should look like. For this, we need to create `configs` directory and the following `my-maven.yaml` file inside:

```yml
repo:
  type: maven
  storage:
    type: fs
    path: /var/artipie/data
```

If you added a section with credentials to the `artipie.yaml`, you also need to create a `_credentials.yml` file in the `configs` directory. Each node is a user name. The supported types of password can be found [here](https://github.com/artipie/artipie/blob/700eb89352126e6f1bd12a0d3ff668abf2b44048/README.md#multitenancy) The file with credentials should look like this:

```yml
credentials:
  alice:
    type: plain
    pass: 123
  bob:
    type: plain
    pass: qwerty
```

As a results, you will have the following files structure:

```bash
.
├── artipie.yaml
├── configs
    ├── my-maven.yaml
    └── _credentials.yml # optinal
```

If you have completed all the instructions correctly now you should be able to use the repository: deploy and install Maven artifacts.

## Configuring project to use your Artipie maven repository

At this step, I will show you how to configure your project to use created Artipie maven repository. If you want to `mvn deploy` your project to Artipie, add the following to project's `pom.xml`:

```xml
<distributionManagement>
    <repository>
        <id>artipie</id>
        <url>http://localhost:8080/my-maven</url>
    </repository>
</distributionManagement>
```

In case you want to `mvn install` deployed packages from Artipie then add the following to project's `pom.xml`:

```xml
<repositories>
    <repository>
        <id>artipie</id>
        <url>http://localhost:8080/my-maven</url>
    </repository>
</repositories>
```

## Advanced options

Apart from demonstrated possibilities, Artipie Maven supports: group repositories, proxies and user groups.Check out the corresponding
[documentation section](https://github.com/artipie/artipie/tree/master/examples/maven)
for more details.

## Conclusion

In this blog post I explained how to setup own Maven repository with Artipie and how to
configure a Maven project to use it. 