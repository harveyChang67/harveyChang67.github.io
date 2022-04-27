---
title: "RepoDB_C#"
date: 2022-04-27T11:21:06Z
draft: false
---


RepoDB 在 Generic Repository Pattern 中很好用，
免去使用 Dapper 去自建 SQL 產生器，
但是有幾個限制 [RepoDB Limitations](https://github.com/mikependon/RepoDb/blob/master/RepoDb.Docs/limitations.md)，
其中一個令人訝異 -> Composite Keys。

RepoDB 只會處理 1 個 Primary Key....
