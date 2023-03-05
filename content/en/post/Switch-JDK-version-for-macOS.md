---
title: "Switch JDK Version for macOS"
date: 2022-04-06T11:02:04+08:00
tags: ["Java", "macOS"]
---

## Find all of JDK root paths
```shell
/usr/libexec/java_home -V
```
## Switch Java JDK via alias
Setup `JAVA_HOME` path in `~/.zshrc`
```shell
# JDK11 JDK8
export JAVA_11_HOME=/Library/Java/JavaVirtualMachines/jdk-11.0.14.jdk/Contents/Home
export JAVA_8_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_291.jdk/Contents/Home
# default JDK11
export JAVA_HOME=$JAVA_11_HOME
# alias JDK version
alias jdk11="export JAVA_HOME=$JAVA_11_HOME"
alias jdk8="export JAVA_HOME=$JAVA_8_HOME"
```
Refresh to activate
```shell
source ~/.zshrc
```

## Check Java Version
Java 8:
```shell
java -version
```

Java 9 +:
```shell
java --version
```