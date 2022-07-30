---
title: "Azure_pipelines_rdb"
date: 2022-06-25T08:58:34Z
draft: false
categories: ["Azure"]
tags: ["Azure"]
---

從 Azure Pipelines 內更動 DB 的方式

```bash
psql ....  
```

- SSH task --> Postgres + SSH
- Docker task(ver.1) + Run postres docker --> psql...