---
layout: post
date: 2022-12-22
title: "v0.28.0: Release Notes"
author: olenagerasimova
description: |
  Key features and improvements description in the recent
  version v0.28.0, released just a few days ago.
keywords:
  - artipie
  - binary artifacts
  - hosting of artifacts
  - Abstract storage
  - Monitoring
  - Micrometer metrics
  - Prometheus
  - JFR
---

At the end of November, [Dzone](https://dzone.com/) has published our article:
[Private Remote Maven Repository With Artipie](https://dzone.com/articles/private-remote-maven-repository-with-artipie-1). 
We will be happy to get any feedback!

Artipie new version [v0.28.0](https://github.com/artipie/artipie/releases/tag/v0.28.0) was released on December 28. 
The previous two months we were working on Artipie monitoring and metrics. The goal is to provide easy to
use and understand monitoring system, which will allow us to know what is happening in the Artipie, how fast
the artifacts are uploaded and downloaded, catch and fix any problems right on time. We approached monitoring from two
different directions: gathering metrics with [Micrometer](https://micrometer.io/) and providing measurements 
in [Prometheus](https://prometheus.io/) compatible format and implementing diagnostics and profiling data with 
[Java Flight Records](https://docs.oracle.com/javacomponents/jmc-5-4/jfr-runtime-guide/about.htm#JFRUH170).

[Micrometer](https://micrometer.io/) metrics can gather the following statistics:
- Vert.x embedded [Micrometer metrics](https://vertx.io/docs/3.9.14/vertx-micrometer-metrics/java/) generate various 
[HTTP server-related metrics](https://vertx.io/docs/3.9.14/vertx-micrometer-metrics/java/#_vert_x_core_tools_metrics) 
(opened and stalled connection, processing time and processed bytes, etc)
- [JVM and system metrics](https://micrometer.io/docs/ref/jvm) includes loaded classes counts, memory usage, 
GC statistic, processor and threads metrics
- [Artipie storage metrics](https://github.com/artipie/artipie/wiki/Configuration-Metrics#artipie-metrics) gather statistics about storage operation
- [Artipie HTTP metrics](https://github.com/artipie/artipie/wiki/Configuration-Metrics#artipie-metrics) gather HTTP requests and responses related statistics

To learn more about each metrics type, check our [Wiki](https://github.com/artipie/artipie/wiki/Configuration-Metrics#metrics).

Artipie JFR events are generated on each HTTP request and storage operation. 
Check the [Wiki](https://github.com/artipie/artipie/wiki/jfr-events) for more details.  
