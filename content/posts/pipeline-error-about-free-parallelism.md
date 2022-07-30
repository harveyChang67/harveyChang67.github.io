---
title: "Pipeline Error About Free Parallelism"
date: 2021-10-01T02:14:31Z
draft: false
categories: ["Azure"]
tags: ["Azure"]
---

嘗試用 Azure Pipeline 編譯 WinForms 的程式遇到一個問題：
> 「No hosted parallelism has been purchased or granted」

直接依照指示到 [https://aka.ms/azpipelines-parallelism-request](https://aka.ms/azpipelines-parallelism-request)
填寫完成後 1-2個工作日可以完成
（操作步驟可以參考：[【把玩Azure DevOps】Day8 CI/CD從這裡：設定第一個Pipeline(成功與失敗)](https://ithelp.ithome.com.tw/articles/10268594)）

看國外論壇討論說，因為微軟發現有不少人趁著試用作些其他布樂見的事情而產生許多流量，因此在 2021 年初增加了這項限制的政策。
