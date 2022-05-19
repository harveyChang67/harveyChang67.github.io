---
title: "Compare: String Text or String Length?"
date: 2021-10-13T02:33:44Z
draft: false
category: ["C#"]
---

近日看到一篇討論文章：
[c# string performance - what is faster to compare, string text or string length](https://stackoverflow.com/questions/3652036/c-sharp-string-performance-what-is-faster-to-compare-string-text-or-string-le)

被接受的答案雖然蠻合理的，但有其他補充關於 C# `String` 的 source code 可以發現：

![Snipaste_2021-10-13_10-38-37](https://i.imgur.com/SpPfwpb.png)

都考量到了

所以可以直接比對...
