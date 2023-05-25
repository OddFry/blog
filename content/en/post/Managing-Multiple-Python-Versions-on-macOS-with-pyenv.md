---
title: "Managing Multiple Python Versions on macOS with pyenv"
subtitle: "Simple Python Version Management: pyenv"
date: 2023-05-25T10:35:26+08:00
tags: ["pyenv", "Python", "macOS"]
draft: false
---

[pyenv GitHub repository](https://github.com/pyenv/pyenv)
## Install pyenv
Installing with Homebrew
 ```shell
brew update
brew install pyenv
```

Set up shell environment
```
echo 'export PATH="$HOME/.pyenv/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```

## Install python
Installing a specific version of Python
```shell
pyenv install 3.11.3
```

Check the existing Python versions, the asterisk (\*) signifies the Python version currently in use.
```shell
pyenv versions
```

Switch between Python versions
```shell
pyenv global 3.11.3 # modify ~/.pyenv/version file
```

Check the current Python version
```shell
python -V
```

## Others
Switching Python back to the system version
```shell
pyenv global system
```

Uninstall
```shell
pyenv uninstall 3.11.3
```

## Reference
[Mac 使用 pyenv 管理 Python 环境](https://www.qazhe.com/2020/03/03/Mac%E4%BD%BF%E7%94%A8pyenv%E7%AE%A1%E7%90%86Python%E7%8E%AF%E5%A2%83/)
[Mac 电脑使用 pyenv 管理多版本 python 环境](https://www.cnblogs.com/rianley/p/14744595.html)