---
title: "grep command in Linux"
subtitle: "Global Regular Expression Print"
date: 2023-03-14T20:33:02+08:00
tags: ["grep", "Linux"]
draft: false
---

## Syntax
```shell
grep [options] pattern [files]
```

Options:
* `-n` or `--line-number`: show line number
* `-i` or `--ignore-case`: case insensitive search
* `--color=auto`: color-highlighting the matched text or words in output
## Examples of pipe and grep
Check Java version
```shell
$ java --version
java 11.0.14 2022-01-18 LTS
Java(TM) SE Runtime Environment 18.9 (build 11.0.14+8-LTS-263)
Java HotSpot(TM) 64-Bit Server VM 18.9 (build 11.0.14+8-LTS-263, mixed mode)
```

Search for `java` and highlight it in the result
```shell
$ java --version | grep --color=auto 'java'
java 11.0.14 2022-01-18 LTS    # Highlight "java"
```

Search for `Java`, case sensitive and show line number
```shell
$ java --version | grep -n 'Java'
2:Java(TM) SE Runtime Environment 18.9 (build 11.0.14+8-LTS-263)
3:Java HotSpot(TM) 64-Bit Server VM 18.9 (build 11.0.14+8-LTS-263, mixed mode)
```

Search for `java`, case insensitive and show line number
```shell
$ java --version | grep -in 'java'
1:java 11.0.14 2022-01-18 LTS
2:Java(TM) SE Runtime Environment 18.9 (build 11.0.14+8-LTS-263)
3:Java HotSpot(TM) 64-Bit Server VM 18.9 (build 11.0.14+8-LTS-263, mixed mode)
```