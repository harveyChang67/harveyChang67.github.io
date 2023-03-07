---
title: "Bloom_filter"
date: 2023-03-05T03:27:20Z
draft: false
categories: ["misc"]
---

## `Bloom Filter` 布隆過濾器：「`不存在` 為可確定，`存在` 為＂可能＂」

聽朋友聊到 `Bloom Filter` 布隆過濾器覺得有趣，
做了點調查。

這篇文章說明得較清楚：
[深入浅出BloomFilter原理 - 刘训灼的文章 - 知乎](https://zhuanlan.zhihu.com/p/140545941)

由於 `Bloom Filter` 的原理特性 使得「`不存在` 為可確定，`存在` 為＂可能＂」，
存在可以推的（可控的）誤判率，
因此合適其優勢的情境有些特徵，如：

- `大數據` 下 希望運用類 Hash 來過濾，希望避免 Hash 衝突
- 合適的 二元向量 數量
- 合適的 Hash function 數量

特別好奇於把一個對其＂存在＂具有一定誤判率的東西，
拿來用在「判断一个元素是否在集合中」的方式...
頗有趣的可以強調 正面用、反面用。

「`不存在`為確定」特性
> 緩存穿透 的攻擊，優先排除掉 不合規Key 的 request 訪問。
> 延伸課題：緩存做水平擴展、熱點調教、...

運用「`存在`判斷有可控極低的誤判率」特性
> 爬蟲過濾掉疑似曾經訪問過的 URL。（代價是可能少抓到頁面）

特殊運用：
[資料採集之：巧用布隆過濾器提取資料摘要](https://tw511.com/a/01/45235.html)

## Reference

[什么是缓存雪崩、缓存击穿、缓存穿透？ - java技术爱好者的文章 - 知乎](https://zhuanlan.zhihu.com/p/346651831)
[什么是缓存雪崩、击穿、穿透？](https://xiaolincoding.com/redis/cluster/cache_problem.html#%E7%BC%93%E5%AD%98%E9%9B%AA%E5%B4%A9)
[布隆过滤器与布谷鸟过滤器 - 终端研发部的文章 - 知乎](https://zhuanlan.zhihu.com/p/462815302)
[硬核 | Redis 布隆（Bloom Filter）过滤器原理与实战 - 码哥字节的文章 - 知乎](https://zhuanlan.zhihu.com/p/496584545)
