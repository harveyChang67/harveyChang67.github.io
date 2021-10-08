---
title: "Azure Pipelines Key Concepts"
date: 2021-10-08T08:06:53Z
draft: false
---

最近當了「Yaml 檔工程師」玩了 Azure Devops Pipelines，終於完成 Azure 編譯 Winforms 專案 並 部署到測試環境（VM）上面，過程中花了點時間找路，這邊紀錄一下。

## Key concepts for new Azure Pipelines

優先參考：

- [Key concepts for new Azure Pipelines users](https://docs.microsoft.com/en-us/azure/devops/pipelines/get-started/key-pipelines-concepts?view=azure-devops)
- [新 Azure Pipelines 使用者的重要概念](https://docs.microsoft.com/zh-tw/azure/devops/pipelines/get-started/key-pipelines-concepts?view=azure-devops)

文內地一張圖片有說明了 Azure Pipelines YAML 的結構階層關係，所以 YAML 檔案內的結構看啟回會像是這樣：

```YAML
trigger:

pool:

stages:
- stage: A
  jobs:
  - job: 1
    steps:
    - task: 

- stage: B
  jobs:
  - deployment: VMDeploy
  
```

這也能從 [YAML 結構描述參考](https://docs.microsoft.com/zh-tw/azure/devops/pipelines/yaml-schema?tabs=schema%2Cparameter-schema&view=azure-devops#deployment-job)找到資訊印證。

好玩的來了...

## Deploy to VM

會從 [Environment - virtual machine resource](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/environments-virtual-machines?view=azure-devops)找到從 Pipeline deploy 到 VM 的方法，恰好裡面有一段：

```YAML
trigger: 
- main

pool: 
   vmImage: ubuntu-latest

jobs:
- deployment: VMDeploy
  displayName: Deploy to VM
```

那段 `jobs` 就是關鍵了！
如果你的 YAML 在編譯那一段所參考的範例是以 `steps` 為主的，就必須先微調一下以 `stage` 來區隔，成為上面說的正確的結構。

## 更多資訊
- [Specify jobs in your pipeline](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/phases?view=azure-devops&tabs=yaml)
- [指定管線中的作業](https://docs.microsoft.com/zh-tw/azure/devops/pipelines/process/phases?view=azure-devops&tabs=yaml)
- [使用預先定義的變數](https://docs.microsoft.com/zh-tw/azure/devops/pipelines/build/variables?view=azure-devops&tabs=yaml)