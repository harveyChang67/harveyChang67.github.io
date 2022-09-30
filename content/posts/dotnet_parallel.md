---
title: "Dotnet_parallel"
date: 2022-09-30T02:40:01Z
draft: false
categories: [".NET"]
tags: [".NET","C#"]
---

一個 Batch Task 遇到一段 Code，
SQL.Select in a for-loop that runs 25k times

我請團隊在 Parallel 的修改版本加上限制。

```csharp
    var parallel = new ParallelOptions
    {
        MaxDegreeOfParallelism = 5
    };
```

也與另一個做法 `Task.Run`, `Task.WhenAll` 進一步區隔。

---

ref:

- [Running Async Foreach Loop C# async await](https://stackoverflow.com/a/41561544)
- [Parallel.ForEach vs Task.Run and Task.WhenAll](https://stackoverflow.com/a/19103047)
- <https://gitter.im/npgsql/npgsql?at=595a0319c101bc4e3a46654d>
