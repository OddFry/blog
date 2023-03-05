---
title: "macOS 安装 Homebrew"
subtitle: The Missing Package Manager for macOS
date: 2022-05-23T15:11:30+08:00
tags: ["macOS"]
---

## 安装 Homebrew
[Homebrew site](https://brew.sh/)
```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## 更新
更新 Homebrew 版本：
```shell
brew update
```

检查可更新的安装包：
```shell
brew outdated
```

更新安装包：
```shell
brew upgrade             # 更新所有的包
brew upgrade $FORMULA    # 更新指定的包
```

锁定不想更新的包：
```shell
brew pin $FORMULA      # 锁定某个包
brew unpin $FORMULA    # 取消锁定
```

## 其他
列出已安装包
```shell
brew list
```

查看安装包的相关信息：
```shell
brew info $FORMULA    # 显示某个包的信息
brew info             # 显示安装了包数量，文件数量，和总占用空间
brew deps --installed --tree # 查看已安装的包的依赖，树形显示
```

清理旧版本：
```shell
brew cleanup             # 清理所有包的旧版本
brew cleanup $FORMULA    # 清理指定包的旧版本
brew cleanup -n          # 查看可清理的旧版本包，不执行实际操作
```

删除
```shell
brew rm $FORMULA                # 删除某个包
brew uninstall --force $FORMULA # 删除所有版本
```