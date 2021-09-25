---
title: "Hello World"
date: 2021-09-25T07:26:54Z
draft: false
---

Hugo + GitHub 的方式架設簡單的 Blog 很有趣，這邊紀錄幾個資訊。

## Hugo 編譯環境：[klakegg/hugo](https://hub.docker.com/r/klakegg/hugo/)

環境指令：
>   docker run --rm -it -v $(pwd):/src klakegg/hugo:0.83.1

Windows 環境指令：
>   docker run --rm -it -v %cd%:/src klakegg/hugo:0.83.1

其後接 Hugo 的[指令](https://gohugo.io/getting-started/usage/)即可。


## Themes：PaperMod
https://github.com/adityatelange/hugo-PaperMod

裡面的安裝指引可供參考