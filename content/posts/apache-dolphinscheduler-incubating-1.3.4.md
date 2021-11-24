---
title: "Apache Dolphinscheduler Incubating 1.3"
date: 2021-11-24T03:42:14Z
draft: true
---

1. 下載 [apache-dolphinscheduler-incubating-1.3.4-src.zip](https://www.apache.org/dyn/closer.lua/dolphinscheduler/1.3.4/apache-dolphinscheduler-incubating-1.3.4-src.zip)
   https://www.apache.org/dyn/closer.lua/dolphinscheduler/1.3.4/apache-dolphinscheduler-incubating-1.3.4-src.zip
2. 解壓縮
3. cd apache-dolphinscheduler-incubating-1.3.4-src-release/docker/docker-swarm
4. docker pull dolphinscheduler.docker.scarf.sh/apache/dolphinscheduler:1.3.4
5. docker tag ==dolphinscheduler.docker.scarf.sh/apache/dolphinscheduler:1.3.4== apache/dolphinscheduler:latest
6. docker-compose up -d
7. http://127.0.0.1:8888/
    默认的用户是admin，默认的密码是dolphinscheduler123

Reference：<http://dolphinscheduler.incubator.apache.org/zh-cn/docs/1.3.4/user_doc/docker-deployment.html>
