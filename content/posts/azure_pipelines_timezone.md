---
title: "Azure_pipelines_timezone"
date: 2022-06-19T12:36:19Z
draft: false
tags: ["Azure"]
---

使用 Azure Pipelines 編譯 dotnet 時遇到一個狀況記錄下來。

專案中有使用了沒有綁定 TimeZone 的時間相關函式，
造成資料寫入 DB 時有偏差，
（DB 已設定）

可以嘗試設定 Agent 的 TimeZone 設定，
（透過 PowerShell task）：
Win:

```bash
Get-TimeZone
Set-TimeZone "Taipei Standard Time"
Get-TimeZone
```

Ubuntu:

```bash
sudo timedatectl set-timezone Asia/Taipei
```