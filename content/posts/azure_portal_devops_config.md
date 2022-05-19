---
title: "Azure_portal_devops_config"
date: 2022-01-01T03:29:02Z
draft: false
tags: ["Azure"]
---

1. AAD >  Enterprise Application > devops > User :
![azure_portal_devops_config](/assets/azure_portal_devops_config.png)

2. Azure Devops 側還是無法.取得訂閱資訊

![azure_devops_no_subscriptions](/assets/azure_devops_no_subscriptions.png)

3. 就算由 Owner 建好 Service Connection 也無法讓 guest、member 直接使用，原因是操作 pipeline 的 account 對於訂閱的權限不夠。

![Snipaste_2022-01-01_13-23-43](/assets/Snipaste_2022-01-01_13-23-43.png)

4. 從 Azure Portal 處給予該 account 至少 Reader 的角色

> 訂閱 > IAM > add role assignment

但是此法有缺點，無法單一授權、指定 project 授權。
