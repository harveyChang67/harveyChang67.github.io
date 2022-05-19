---
title: "C_sharp_big5"
date: 2022-05-18T07:19:28Z
draft: false
---

## 需求

老式需求

3 個欄位的資訊，
希望擷取出中間的 16 bytes 的欄位

```
20040609台北市第81分公司0800-000123
20040609彰化縣第1分公司 0800-000123
```

通常會困擾於 編譯器對於資料型態長度的判定、編碼。
（其他程式語言也會遇到類似狀況）

在 C# 中則會遇到 string Length 變動的問題無法如預期做切割，
因此運用「==Big5編碼==」方式在 中文佔用 2 bytes、英數佔用 1 bytes 的特性，
再轉為 sub string。

```c#
System.Text.Encoding encoding = System.Text.Encoding.GetEncoding(950);

string tempstr = "";

byte[] strBytes = encoding.GetBytes(str);

tempstr = encoding.GetString(strBytes, start, lengths);
```