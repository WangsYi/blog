---
title: "Powershell、cmd不重启刷新环境变量"
date: 2023-08-02T08:26:26+08:00
draft: false
tags: ["powershell", "环境变量", "env", "刷新"]
---

## 安装chocolatey

> 参考 https://chocolatey.org/install

## cmd

直接运行`refreshenv`即可刷新

## powershell

新建或修改文件（xxxx为你的用户名）`C:\Users\xxxx\Documents\WindowsPowerShell\profile.ps1`，添加以下命令：
```powershell
Import-Module $env:ChocolateyInstall\helpers\chocolateyProfile.psm1
```

重启powershell后，运行`refreshenv`即可
