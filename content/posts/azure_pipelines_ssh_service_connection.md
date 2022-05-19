---
title: "Azure Pipelines 設定 SSH 不用密碼的 Service Connection"
date: 2021-11-09T02:12:18Z
draft: false
tags: ["Azure"]
---

因為 Azure Devops 的 Service Connection 上面沒有詳細說明，這邊紀錄下來。

1. 依照 [安裝 OpenSSH](https://docs.microsoft.com/zh-tw/windows-server/administration/openssh/openssh_install_firstuse) 在 VM 上安裝 SSH Server
2. 參考 [OpenSSH 金鑰管理](https://docs.microsoft.com/zh-tw/windows-server/administration/openssh/openssh_keymanagement) 建立使用者金鑰
3. **務必**參考這一段 [**部署公開金鑰**](https://docs.microsoft.com/zh-tw/windows-server/administration/openssh/openssh_keymanagement#deploying-the-public-key)