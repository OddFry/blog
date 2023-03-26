---
title: "File Checksum on macOS"
subtitle: "Message Digest and Secure Hash Algorithm"
date: 2023-03-26T13:14:28+08:00
tags: ["Checksum", "macOS"]
draft: false
---

## Checksum command
MD5
```shell
md5 FILE
```

SHA-1
```shell
shasum -a 1 FILE
```

SHA-256
```shell
shasum -a 256 FILE
```

SHA-512
```shell
shasum -a 512 FILE
```

## OpenSSL
MD5
```shell
openssl md5 FILE
```

SHA-1
```shell
openssl sha1 FILE
```

SHA-256
```shell
openssl sha256 FILE
```

SHA-512
```shell
openssl sha512 FILE
```

## References
[Check MD5 Hash on your Mac](https://osxdaily.com/2009/10/13/check-md5-hash-on-your-mac/)

[Verify SHA1 Hash with openssl](https://osxdaily.com/2012/02/09/verify-sha1-hash-with-openssl/)

[Check SHA1 Checksum in Mac OS X](https://osxdaily.com/2012/02/05/check-sha1-checksum-in-mac-os-x/)

[How to Check sha256 Hash of a File on Mac](https://osxdaily.com/2021/12/17/check-sha256-hash-mac/)

[How to Check SHA512 Checksum on Mac](https://osxdaily.com/2022/05/08/how-to-check-sha512-checksum-on-mac/)
[How to use checksums on Mac to verify app downloads](https://www.securemac.com/news/how-to-use-checksums-on-mac-to-verify-app-downloads)