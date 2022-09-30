---
title: "Materialized_Views"
date: 2022-09-30T02:52:30Z
draft: false
categories: ["Database"]
---

紀錄

`Materialized Views` 與 實體表的副本 做法真的一樣？

What’s the catch?

差異在 前者 會額外占用 memory，
因此最好用在更有價值的查詢結果快取上，
別想著拿來替代 AB表切換。

---

ref:

- [Understanding Materialized Views — Part 1](https://medium.com/event-driven-utopia/understanding-materialized-views-bb18206f1782)
- [Materialized Views: The Cost-Effective Way To Extract Insights](https://towardsdatascience.com/materialized-views-the-cost-effective-way-to-extract-insights-b4a066f85fb)
- [Why Use a Materialized View?](https://materialize.com/blog/why-use-a-materialized-view/)
