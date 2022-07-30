---
title: "Signed Cert"
date: 2021-11-25T07:35:29Z
draft: false
categories: ["misc"]
---

## 產生並信任你自己的憑證

<https://letsencrypt.org/zh-tw/docs/certificates-for-localhost/>

```shell
openssl req -x509 -out localhost.crt -keyout localhost.key \
    -newkey rsa:2048 -nodes -sha256 \
    -subj '/CN=localhost' -extensions EXT -config <( \
    printf "[dn]\nCN=localhost\n[req]\ndistinguished_name = dn\n[EXT]\nsubjectAltName=DNS:localhost\nkeyUsage=digitalSignature\nextendedKeyUsage=serverAuth")
```

也說了 minica

### 2

<https://gist.github.com/cecilemuller/9492b848eb8fe46d462abeb26656c4f8>

有些方法
還有 mkcert <-- 最方便
