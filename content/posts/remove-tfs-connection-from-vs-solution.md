---
title: "Remove Tfs Connection From vs Solution"
date: 2021-10-07T05:59:56Z
draft: false
---

1. 刪除專案中 `*.vssscc`、`*.vspscc` 副檔名的檔案。
2. 刪除 `.sln` 內的 `GlobalSection(TeamFoundationVersionControl)` 區塊。
3. 內部的 `*.__proj` 檔案內的這幾項也必須刪除：

    ```xml
    <SccProjectName>XXX</SccProjectName>
    <SccLocalPath>XXX</SccLocalPath>
    <SccAuxPath>XXX</SccAuxPath>
    <SccProvider>XXX</SccProvider>
    ```

    萬一實在太多了，請這條正規表示式 `/^\s*(?:<Scc\w+>).+$/`，使用 Notepad++ search & replace。
