---
title: "Moongodb_data_modeling"
date: 2022-08-10T07:03:15Z
draft: false
---

紀錄一下

## 考量點

- schema_version。
- 幾乎可以優先從「商業邏輯」、「畫面呈現」 等 high level來開始規劃。
- document 是原子操作（atomic operation），規劃時必須考量「寫入、更新」頻繁程度，適度將 document 分散。
- 預先安插可用於 sharding 的設定欄位。

## [The Bucket Pattern](https://www.mongodb.com/blog/post/building-with-patterns-the-bucket-pattern)

很適合 IoT、巡查表單類 的資料放置。

## [The Subset Pattern](https://www.mongodb.com/blog/post/building-with-patterns-the-subset-pattern)

文中提到的 Product - Reviews 案例很實用。
Product Collention 內紀錄前 10個 Review，
可以做為產品資訊頁「第一擊」的資訊儲存，
進一步的資訊再從其他 Collection 撈取。（如：Review）

Reference：

- [Data Modeling for MongoDB](https://www.slideshare.net/mongodb/data-modeling-for-mongodb)
- [Building with Patterns: A Summary](https://www.mongodb.com/blog/post/building-with-patterns-a-summary)