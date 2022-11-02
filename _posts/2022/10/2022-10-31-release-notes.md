---
layout: post
date: 2022-11-02
title: "v0.27.4: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version v0.27.4, released just a few days ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - Abstract storage
  - rest api
---

Artipie was represented in [DevOops](https://devoops.ru/) conference on October 19 in 
Saint-Petersburg. Our current team-leader Denis Gurus told how to use Artipie with Maven and Docker
repositories. Find the workshop announce [here](https://devoops.ru/talks/827cdd91b1fb40cbae91d1335dcd54d1/).

[v0.27.4](https://github.com/artipie/artipie/releases/tag/v0.27.4) was released on October 27. The 
last and current months we are working on Artipie monitoring and metrics. The goal is to provide easy to
use and understand system, which will allow us to know what is happening in the Artipie, how fast
the artifacts can be uploaded and downloaded, catch and fix any problems right on time. The first
steps in this direction were made some time ago, and we already have some measurement instruments. 
To enable all currently available metrics, add the following section into [main configuration yaml](https://github.com/artipie/artipie/wiki/Configuration):

```yaml
meta:
  metrics:
    -
      type: log # Metrics type, `log` to print statistics into application log
      interval: 5 # Publishing interval in seconds, default value is 5
    -
      type: asto # Metrics type, `asto` to publish statistics into storage
      interval: 5 # Publishing interval in seconds, default value is 5
      storage: # Storage to publish the metrics to
        type: fs
        path: /tmp/artipie/statistict
    -
      type: prometheus # Obtain metrics in `promethium` compatible format
    -
      type: vertx # Metrics type, `vertx` for Vert.x embedded metrics
      endpoint: "/metrics/vertx" # Path of the endpoint, starting with `/`, where the metrics will be served
      port: 8087 # Port to serve the metrics
```

To learn more about each metrics type, check our [Wiki](https://github.com/artipie/artipie/wiki/Configuration-Metrics#metrics).
