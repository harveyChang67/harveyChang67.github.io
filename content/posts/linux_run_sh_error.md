---
title: "Linux_run_sh_error"
date: 2021-12-29T08:28:12Z
draft: false
categories: ["misc"]
---

Linux 執行 .sh 後出現 Syntax Error
> Syntax error: end of file unexpected (expecting “then”)

問題不是語法錯誤，而是檔案編碼問題。

解決辦法是：

> dos2unix <filename>

或是 VSCode 右下方從 `CRLF --> LF`