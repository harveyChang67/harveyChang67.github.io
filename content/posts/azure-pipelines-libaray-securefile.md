---
title: "Azure Pipelines 編譯VS專案引用外部參考資源 － Libaray Securefile"
date: 2021-10-06T06:33:32Z
draft: false
---

若 WinForms 的專案有依些外部參考的 dll 在編譯時需要引入，數量有可能20-30個不等。
若因為並非這個專案內 Code Base所產生而不想放在 Git Repository 內，上去 Azure Devops 編譯可以這樣處理：

1. 全部壓縮一包 `.zip`
2. 上傳至「Library」
    ![azure-pipelines-library](https://i.imgur.com/owBH5fL.png)
3. 設定開放給 Pipeline 引用的權限
    ![secure-file-permission](https://i.imgur.com/u0RdNuO.png)
4. 在 Pipelines 的 yaml 設定內加上 Download & Extract
    ![Download & Extract in YAML](https://i.imgur.com/ywft9JA.png)
5. 編譯時可以加上參數指定這個暫時路徑：

    ```yaml
    - task: VSBuild@1
        inputs:
            solution: '**\*.csproj'
            platform: 'AnyCPU'
            configuration: '$(BuildConfiguration)'
            msbuildArgs: '/p:referencepath=$(Agent.TempDirectory)/reference'
            clean: true
    ```

就可以完成了。