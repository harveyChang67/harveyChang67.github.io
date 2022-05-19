---
title: "AWS API Gateway 對外時能走固定IP的作法"
date: 2021-10-26T09:18:39Z
draft: false
tags: ["AWS"]
---

大部分資料、使用情境是
> 外面 -> 固定 -> API Gateway -> ...

使用情境若反過來的具體解答較少，
這邊分享一下測試過的方式。

![Snipaste_2021-10-26_17-21-18](https://i.imgur.com/6RpK6Gx.png)

- ENI + Static Public IP
- NAT Gateway
- Private Subnet -> NAT Gateway
- Lambda 網路設定綁 Private Subnet

可以在 AWS 另建 API Gateway + Resource Policy 限定IP 來測試。

## References

- [Setting a Static IP for AWS Lambda (or any AWS instance)](https://dev.to/alexanderdamiani/aws-lambda-with-a-static-ip-2g3l)
- [AWS Lambda functions with a static IP](https://matthewleak.medium.com/aws-lambda-functions-with-a-static-ip-89a3ada0b471)
- [Tutorial: Build a Hello World REST API with Lambda proxy integration](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-create-api-as-simple-proxy-for-lambda.html)
- [Create a REST API with Lambda proxy integration](https://medium.com/javascript-in-plain-english/create-a-rest-api-with-lambda-proxy-integration-d33e4786349)
