---
title: "Mongo Docker on Mac"
date: 2023-03-16T00:38:26Z
draft: true
categories: ["Docker"]
tags: ["Mongo","Docker"]
---


`docker-compose.yml` 中使用 Mongo：

```
version: '3.7'

services:

  mongo:
    image: mongo:latest
    restart: always
    environment:
      MONGO_INITDB_ROOT_USERNAME: root
      MONGO_INITDB_ROOT_PASSWORD: example
```

收到以下錯誤：

> ERROR: child process failed, exited with 51

夥伴們調查後發現改 image tag：

```
version: '3.7'

services:

  mongo:
    image: mongo:6.0-focal
    restart: always
    environment:
      MONGO_INITDB_ROOT_USERNAME: root
      MONGO_INITDB_ROOT_PASSWORD: example
```
