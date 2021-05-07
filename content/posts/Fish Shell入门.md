---
title: "Fish Shell 入门"
subtitle: ""
date: 2021-05-08T01:45:17+08:00
lastmod: 2021-05-08T01:45:17+08:00
draft: false
author: "英梨梨"
authorLink: ""
description: ""

tags: ["终端"]
categories: ["Linux"]

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: "http://shp.qpic.cn/ishow/2735042818/1619604171_84828260_25670_sProdImgNo_2.jpg/0"
featuredImagePreview: "http://shp.qpic.cn/ishow/2735042818/1619604171_84828260_25670_sProdImgNo_2.jpg/0"

toc:
  enable: true
math:
  enable: false
lightgallery: true
license: ""
---

<!--more-->

# Fish Shell 入门

三年啊！我终于忍受不了 `oh-my-zsh` 的臃肿，将日常 Shell 从 zsh 切换到了 fish shell。

虽然名为 fish，但它跟 “鱼” 一点关系都没有，它其实是 “the **f**riendly **i**nteractive **sh**ell” 的缩写。它最大特点就是方便易用。很多其他 Shell 需要折腾才有的功能，Fish 默认提供，并且开箱即用。

如果你想要一个好用的 Shell，又不喜欢折腾，那么你一定要尝试一下 fish shell。

![fish shell](fish_shell.jpg "测试哦")

## 安装

在 Archlinux 中安装：

```plaintext
sudo pacman -S fish
```

Copy

在 MacOS 中安装：

```plaintext
brew install fish
```

Copy

其他系统的安装请参考[官方网站](http://fishshell.com/#platform_tabs)。

安装好后直接在命令行中输入 `fish` 就可以运行 fish shell 了。

想要将 fish 设为默认 Shell，只需要执行：

```plaintext
# GNU/Linux 中
chsh -s /usr/bin/fish

# MacOS 中
chsh -s /usr/local/bin/ fish
```

Copy

## 命令行着色

fish 与 Bash 最大的不同，也是 fish 最好用的点之一便是命令行着色 (不同主题可能有所区别)：

```plaintext
# 无效命令显示为红色
$ cl
# 有效命令显示为蓝色
$ clear
```

Copy

有效路径下会有下划线：

```plaintext
$ cd ~/Downloads/
```

Copy

## 自动建议

fish 会根据命令行的上下文和历史记录智能的给出命令建议：

```plaintext
# 命令建议
$ yarn coverage
$ git checkout dev
# 路径建议
$ ls ~/Downloads/
```

Copy

如果采纳建议，可以按下`→` 或 `Tab`。如果只采纳一部分，可以按下 `Alt + →`。

对于按下 `Tab` 的命令补全，如果有多个可能的结果，fish 会把它们都列出，有的还带有简要介绍。

```plaintext
$ mkdir tmp
mkdir        (Executable, 54kB)  mkfs.minix       (Executable, 105kB)
mke2fs      (Executable, 134kB)  mkhomedir_helper  (Executable, 21kB)
mkfifo       (Executable, 38kB)  mklost+found      (Executable, 13kB)
mkfs         (Executable, 13kB)  mknod             (Executable, 42kB)
…and 5 more rows
```

Copy

除了补全命令，fish 还可以补全参数。

```plaintext
$ ls -
-1                                           (List one entry per line)
-A  --almost-all                         (Show hidden except . and ..)
-a  --all                                                (Show hidden)
-B  --ignore-backups                      (Ignore files ending with ~)
…and 51 more rows
```

Copy

你可能会说这些功能都可以用 zsh 实现。

确实，zsh 也能做到，但 fish 做得更好，并且这些功能都是 fish 默认支持的，不需要折腾插件，也不需要安装臃肿的 `oh-my-zsh`

## 配制

虽然 fish 功能强大，但其实并没有多少配置文件需要写，毕竟 fish 的优点之一就是开箱即用嘛。

fish 的配置文件是 `~/.config/fish/config.fish`，这个文件默认不存在，需要自己创建。

这个文件里可以写各种 fish 支持的各种命令和函数，相当于 Bash 的 `.bashrc`。

fish 还提供网页配置工具：

```plaintext
fish_config
```

Copy

在浏览器中可以交互式配置 fish 的配色、提示符、函数、变量、历史记录和快捷键。 命令补全

![fish_config](new-page.assets/fish_config.png)

### 关闭问候语

默认情况下，每次启动 fish，fish 都会打印问候语。要关闭问候语，可以在 fish 中运行：

```plaintext
set -U fish_greeting
```

Copy

### Aliases

fish 也是支持 `alias` 的，所以你可以在 `~/.config/fish/config.fish` 使用 `alias` 定义命令别名。

或者复用 `.bash_aliases` (要确保 `.bash_aliases` 在的语法与 fish 兼容)：

```fish
# ~/.config/fish/config.fish
set fish_aliases ~/.bash_aliases
test -r $fish_aliases; and source $fish_aliases
```

Copy

## 那么代价是什么？

fish 这么强大，就没有一点缺点吗？

**fish 最大的缺点就是它不兼容 POSIX**，也就是说它不能完全兼容 Bash 中的命令，并且没法运行为 Bash 编写的脚本 (这也是我将 fish 作为日常 Shell 最大的顾虑)。

不过在使用中我发现这并不是什么大问题，因为不兼容的命令大多是在编写脚本时使用的，平常用的很少。而 Shell 脚本大多都会在开头通过 `#!/bin/bash` 或者 `#!/bin/sh` 指定运行脚本的 Shell。实在是不行，也可以在命令行中运行 `bash` 临时切换到 bash 环境中。



·End·