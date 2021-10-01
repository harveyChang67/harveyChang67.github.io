---
title: "Azure Pipeline 試用時遇到的一個錯誤"
date: 2021-10-01T07:26:54Z
draft: false
---

嘗試用 Azure Pipeline 編譯 WinForms 的程式遇到一個問題：
> 「No hosted parallelism has been purchased or granted」

直接依照指示到 [https://aka.ms/azpipelines-parallelism-request](https://aka.ms/azpipelines-parallelism-request)
填寫完成後 1-2個工作日可以完成

原因是因為微軟發現有不少人趁著試用作些其他布樂見的事情而產生許多流量，
因此在 2021 年初增加了這項限制的政策。
