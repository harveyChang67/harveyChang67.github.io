---
title: "幾項關於 Azure Pipelines 的紀錄"
date: 2021-10-18T02:10:08Z
draft: false
---

## 基本原則

- Variables in trigger block is not supported.
- Maybe all YAML file of Pipelines are same in all branches.

## template

- <http://thecodemanual.pl/2020/04/02/build-templates-on-azure-devops.html>
- <https://docs.microsoft.com/zh-tw/azure/devops/pipelines/process/templates?view=azure-devops>

## detect CHANGED Dir to build & deploy

- coding in PowerShell to detect What files are changed,
- get DIR and combine ARRAY
- build & deploy via FACTORY PATTERN

References:

- <https://stackoverflow.com/questions/54541602/pass-array-as-inputs-to-azure-devops-yaml-task>
- <https://stackoverflow.com/questions/62835740/loops-and-arrays-in-azure-devops-pipelines>
- <https://stackoverflow.com/questions/53227343/triggering-azure-devops-builds-based-on-changes-to-sub-folders>
- <https://stackoverflow.com/questions/65088433/how-to-get-only-changed-files-using-azure-devops-pipelines>
- <https://stackoverflow.com/questions/67483194/pass-array-of-files-into-the-parameter-of-awscli1-task/67498247#67498247>
- <https://stackoverflow.com/questions/68504910/can-i-loop-an-azure-pipelines-task-on-a-runtime-array-variable-instead-of-an-arr>
- <https://docs.microsoft.com/zh-tw/powershell/scripting/learn/deep-dives/everything-about-arrays?view=powershell-7.1#adding-to-arrays>

開始 try 的：

```yaml
variables:
  f1Flag: false
  f2Flag: false

trigger:
  branches:
    include:
      - master
  # paths:
  #   include:
  #     - "test_pipelines/*"

steps:
  - powershell: |
      ## get the changed files
      $files=$(git diff-tree --no-commit-id --name-only -r $(Build.SourceVersion))
      $temp=$files -split ' '
      $count=$temp.Length
      echo "Total changed $count files"
     
      For ($i=0; $i -lt $temp.Length; $i++)
      {
        $name=$temp[$i]
        echo "this is $name file"
        if ($name -like 'test_pipelines/*')  #if test_pipelines is a subfolder under a folder use "- like '*/f1/*'"
        {
          ##set the flag variable f1Flag to true
          Write-Host "##vso[task.setvariable variable=f1Flag]true"
        }
      }
  - script: echo $(f1Flag)
  - script: echo $(f2Flag)
```

## just clone DIR

- <https://www.google.com/search?q=azure+checkout+path&rlz=1C1GCEU_zh-TWTW969TW969&oq=azure+checkout+path&aqs=chrome..69i57j0i19i30j0i8i19i30l5j69i60.7638j0j1&sourceid=chrome&ie=UTF-8>
- <https://github.com/microsoft/azure-pipelines-yaml/blob/master/design/checkout-path.md>
