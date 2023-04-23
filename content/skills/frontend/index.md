---
title: "Macos+chrome系浏览器中文输入法文本框回车问题"
date: 2023-04-23T12:07:26+08:00
draft: false
tags: ["前端", "Vue"]
---

Vue中聊天窗口监听enter键的keydown事件来触发消息发送，windows下正常，mac下firefox正常，但是chrome系浏览器中输入中文时，不按空格直接回车也会触发消息发送，这显然是不对的，经过查资料和实践，找到两种解决办法。

- 事件里有个isComposing，isComposing为true时代表输入法是打开状态，isComposing为false代表输入法是关闭状态，可以通过这个属性来判断是否是中文输入法下按enter键。
- 中文输入法下按enter键，在keydown事件里获取到的keyCode为229，而英文状态下为13。

参考：https://zhuanlan.zhihu.com/p/580324346