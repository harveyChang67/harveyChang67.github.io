---
title: "C# 處理大 Text 檔案的實驗比對"
date: 2021-10-19T09:07:56Z
draft: false
categories: ["C#"]
tags: ["C#"]
---

直觀寫法肯定是：

- Readline()
- 每行比對、處理一次

這邊有兩個網頁做了 ＂充分的＂實驗比對，

- [C# .Net: Fastest Way to Read Text Files](https://cc.davelozinski.com/c-sharp/fastest-way-to-read-text-files)
- [The Fastest Way to Read and Process Text Files using C# .Net](https://cc.davelozinski.com/c-sharp/the-fastest-way-to-read-and-process-text-files)

結論是，
把檔案都讀進 Array （相當於進記憶體），
再運用平行運算處理完。
