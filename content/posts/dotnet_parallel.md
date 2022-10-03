---
title: "Dotnet_parallel"
date: 2022-09-30T02:40:01Z
draft: false
categories: [".NET"]
tags: [".NET","C#"]
---

一個 Batch Task 遇到一段 Code，
SQL.Select in a for-loop that runs 25k times
特別是 for-loop 內 以 await 去使用了 async 的 DB Layer Func.

我請團隊在 Parallel 的修改版本加上限制。

```csharp
    var parallel = new ParallelOptions
    {
        MaxDegreeOfParallelism = 5
    };
```

也與另一個做法 `Task.Run`, `Task.WhenAll` 進一步區隔。

> ref:
>
> - [Running Async Foreach Loop C# async await](https://stackoverflow.com/a/41561544)
> - [Parallel.ForEach vs Task.Run and Task.WhenAll](https://stackoverflow.com/a/19103047)
> - <https://gitter.im/npgsql/npgsql?at=595a0319c101bc4e3a46654d>

## 系統式思考

這個課題在團隊內的討論很有趣，
討論過程中對於可能的問題不乏 AP Logic 有問題、SQL 有問題、...，
但卻不太動手實測每段時間。

那段邏輯在開發環境中執行一個 SQL SELECT Query 約 2ms，
但 For Loop 高達 3萬筆資料，
在 不修改 AP 主 Logic & SQL 的前提下可發揮的空間有限（數位轉型日常，除非先完成驗證過結果正確），
因此團隊將 部分邏輯 改為 Parallel 是可以進行嘗試的。
（前提是該 AP Logic 不會因此修改造成 髒資料）

事實上，
改為 Parallel 後在開發環境可以快速執行完，
反而證明這個情境中是 C# 造成延遲，
而非 SQL 造成延誤的直覺結論。
