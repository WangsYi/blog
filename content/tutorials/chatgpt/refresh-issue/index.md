---
title: "ChatGPT隔断时间报错临时解决方案"
date: 2023-04-17T04:24:26+08:00
draft: false
tags: ["chatgpt"]
---

> 以前只要用可用的代理登录获取Cookie后，就可以用其他代理使用ChatGPT了，昨天openAI加强了封禁力度，即使有Cookie也会直接被阻止，导致手头只有一个美国的VPN能够访问，但是隔几分钟再提问就会报错，需要重新刷新页面。
> 以下是搜索得到的一个临时解决方案

- 首先保证你安装了油猴插件
  - edge: https://microsoftedge.microsoft.com/addons/detail/tampermonkey/iikmkjmpaadaobahmlepeloendndfphd
  - chrome: https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo
  - firefox: https://addons.mozilla.org/zh-CN/firefox/addon/tampermonkey/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search
- 安装以下脚本
  - https://greasyfork.org/zh-CN/scripts/462967-chatgpt-heartbeat


经测试，安装前等待10分钟会报错，安装后暂时正常