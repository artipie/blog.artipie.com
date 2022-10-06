---
layout: post
date: 2022-10-06
title: "v0.27.0: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version v0.27.0, released just a few days ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - Abstract storage
  - rest api
---

[v0.27.0](https://github.com/artipie/artipie/releases/tag/v0.27.0) was released on September 30. 
This time we are releasing management Rest API. The API allows to manage Artipie repositories, 
storages and users. API is self-documented with [Swagger](https://swagger.io/)
interface. 

We implemented Rest API using [Vert.x](https://vertx.io/) web framework and 
[OpenAPI specification v3.0.0](https://spec.openapis.org/oas/v3.0.0). Endpoints can be (by user's choose) 
protected with [SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security#SSL_1.0,_2.0,_and_3.0), 
authentication is implemented with [JWT-tokens](https://jwt.io/). 
Here is simple and short instructions, how to run latest Artipie Docker image and check new Rest API:

First, make sure you have already installed [Docker Engine](https://docs.docker.com/get-docker/).
Then, open command line and instruct Docker Engine to run Artipie container:

```bash
docker run -it -p 8080:8080 -p 8086:8086 artipie/artipie:latest
```

Artipie image generates default configuration, prints a list of running repositories, test
credentials and a link to the [Swagger](https://swagger.io/) documentation to console. To check
existing repositories using Artipie Rest API:
- go to Swagger documentation page `http://localhost:8086/api/index-org.html`,
  choose "Auth token" in "Select a definition" list,
- generate and copy authentication token for default user `artipie/artipie`,
- switch to "Repositories" definition, press "Authorize" button and paste the token
- then perform `GET /api/v1/repository/list` request.
  Response should be a json list with three default repositories:
```json
[
  "artipie/my-bin",
  "artipie/my-docker",
  "artipie/my-maven"
]
```
To learn more about Rest API, check [Wiki documentation](https://github.com/artipie/artipie/wiki/Rest-api).

At the beginning of September another article about Artipie was published in Russian IT resource,
check it [here](https://habr.com/ru/post/687394/). Habr is the largest and the most well known 
Russian IT resource. 

If you have any question, suggestion or notes, please, do not hesitate to comment this blog post or
contact us in [Telegram](https://t.me/artipie).