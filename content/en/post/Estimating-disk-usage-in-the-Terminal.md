---
title: "Estimating Disk Usage in the Terminal"
subtitle: "Disk Usage"
date: 2024-04-23T21:17:34+08:00
tags: ["macOS"]
draft: false
---

## Name
`du` - estimate file space usage

## Syntax
`-s` : summarize the disk usage in the current directory, not for each directory therein contained

`-h` : sum of directories in human-readable format (-h : Byte, Kilobyte, Megabyte, Gigabyte, Terabyte and Petabyte)

## Examples
Sum of the usage of a specified file or directory
```shell
du -sh {TARGET}
```

Sum of the usage in the current directory in human-readable format
```shell
du -sh *
```

## References
[du (Unix) - Wikipedia](https://en.wikipedia.org/wiki/Du_(Unix))