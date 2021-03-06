---
title: "Lock"
date: 2022-01-27T06:14:32Z
draft: false
categories: ["Architecture"]
---



## 單機鎖

`TODO`

## 分布式鎖 相關
- 單機鎖-->分布式鎖：[架構面試題 #1, 線上交易的正確性](https://columns.chicken-house.net/2018/03/25/interview01-transaction/)
- 將 Redlock 有關的問題整理清楚：
  - [如何做可靠的分布式锁，Redlock真的可行么](https://github.com/ChangAn223/Python-Interview/blob/master/docs/%E6%95%B0%E6%8D%AE%E5%BA%93/Redis/%E5%A6%82%E4%BD%95%E5%81%9A%E5%8F%AF%E9%9D%A0%E7%9A%84%E5%88%86%E5%B8%83%E5%BC%8F%E9%94%81%EF%BC%8CRedlock%E7%9C%9F%E7%9A%84%E5%8F%AF%E8%A1%8C%E4%B9%88.md)
  - [https://twgreatdaily.com/fGfHe28BMH2_cNUgKj2O.html](https://twgreatdaily.com/fGfHe28BMH2_cNUgKj2O.html)

---

## 概念

### 悲觀鎖（Pessimistic Lock）

`預期每次都會遇到資源爭奪。`

共享鎖（Share Lock）
排他鎖（Exclusive Lock）

作用範圍：

- 行鎖（row lock）
    FOR UPDATE、FOR UPDATE NO KEY、LOCK IN SHARE MODE
- 表鎖（table lock）

    ```SQL
    SELECT SUM(..) FROM ..
    ```

### 樂觀鎖（Optimistic Lock）
Optimistic Concurrency Control
`每次存取都認為不會有別人來搶。`

CAS（比較與交換，Compare and swap）
  > 非阻塞同步（Non-blocking Synchronization）、無鎖程式設計演算法（ Non-blocking algorithm）

適合：讀多寫少。
反之，將有很多的寫衝突造成等待

- CAS有3個運算元
  - 記憶體值V
  - 舊的預期值A
  - 要修改的新值B
  當且僅當預期值A和記憶體值V相同時，將記憶體值V修改為B，否則什麼都不做。
- 整個CAS操作是一個原子操作
- 判斷作法
  - TimeStamp
  - Version
  - 待更新欄位：更新前可以拿要更新的欄位的舊值和資料庫的現值進行比對，沒有變化則更新
    - https://stackoverflow.com/a/62959208
  - 所有欄位：相當於表鎖

#### implement
Entity Framework Core
- https://docs.microsoft.com/zh-tw/ef/core/saving/concurrency


## 延伸、變通

- Apache Ignite 避免 Deadlock 類似 MVCC... Oracle 9i...  PostgreSQL
- Redis 內部也有 lock
- optimistic locking in REST API
  - https://linuxtut.com/en/c4585a2373c15d84c1d9/
  - https://blog.appsignal.com/2021/10/20/optimistic-locking-in-rails-rest-apis.html
  - https://sookocheff.com/post/api/optimistic-locking-in-a-rest-api/
- 分布鎖
  - https://liulixiang1988.github.io/2021/08/13/2021-08-13-DistributedLockManager/