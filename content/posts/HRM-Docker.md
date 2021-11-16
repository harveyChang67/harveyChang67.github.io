---
title: "HRM Docker"
date: 2021-11-16T08:50:14Z
draft: false
---

vite.config.js 中加入：

```js
  server: {

    // for HRM in Docker
    host: '0.0.0.0',
    watch: {
      usePolling: true
    },
  }
```
