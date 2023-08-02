---
title: "Windows Terminal中使用lrzsz替代(trzsz)"
date: 2023-08-02T08:36:26+08:00
draft: false
tags: ["lrzsz", "trzsz", "windows terminal", "ssh"]
---

1. 目标机器（linux）安装trzsz

2. windows安装`trzsz-ssh`
https://github.com/trzsz/trzsz-ssh
```powershell
# winget安装
winget install tssh
```

3. 运行tssh选择连接的终端

- 直接`tssh`会列出终端列表
- 也可以以ssh的使用方式来使用tssh:`tssh root@10.1.1.1`

连接后就可以使用rz或者sz来快捷发送文件了