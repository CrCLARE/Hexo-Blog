---
abbrlink: bot-vs-gatekeeper
categories: []
date: '2026-10-07T10:16:40.593298+08:00'
tags: []
title: 赛博皇帝的滑铁卢：我的机器人被自家门卫“反杀”了
updated: '2026-10-07T10:16:45.606+08:00'
---
俗话说，每一个独立开发者，最后都会被迫成为半个运维。而我，CLARE，CrCLARE Studio 的绝对全栈苦力，今天亲身演绎了一部名为《论 .gitignore 与 Branch Protection 如何联合绞杀一个无辜 Bot》的赛博悲剧。

## 第一章：无辜机器人的“花式死法”

为了让 Chronos Seal 的内核签名仪式充满神圣的自动化感，我写了一个尽职尽责的 GitHub Actions Bot。它的任务很简单：跑完云端编译，给内核签名，然后把神圣的 `manifest.json` 和 `manifest.sig` 送回主分支。

结果，它死了，死得很憋屈。

第一刀，来自我自己的“洁癖”。因为我嫌弃构建产物污染源码树，顺手在 `.gitignore` 里加上了一句：

```text
Tools/**/manifest.json
Tools/**/manifest.sig
```


于是，Bot 辛辛苦苦干完活，准备提交时，系统弹出一行冷酷的提示：No changes to commit。


Bot：？我签的这是寂寞吗？

第二刀，来自我严谨的“防呆机制”。Bot 试图绕过 .gitignore 强推，结果迎头撞上我设下的 Branch Protection（分支保护）铁律：“Review all repository rules... Changes must be made through a pull request.”


Bot 既没有 PR 审批权，也没有老板的强制推送特权，只能原地报错暴毙。

那一晚，我看着日志里满屏的报错，发了一条朋友圈：“小小的老子 大大的报错（蠢炸了！）”。

## 第二章：壮士断腕的“反向操作”

最绝望的时刻，我做出了一个更蠢的决定：为了修扇窗户，把整栋楼的安保关了。

没错，我直接把分支保护条例给停了，手动 workflow_dispatch，硬生生把机器人提交的那几个文件按进了主分支。

看着仓库里那几个带着 github-actions[bot] 前缀的 commit，我一边擦冷汗一边庆幸：还好这是早期，还好没被黑客盯上，还好我是唯一的 Owner。

但这绝对不是长久之计。开源社区的秩序不能乱，帝国的大门不能一直敞着。于是，今天，我踏上了寻找终极武器的旅程——PAT（Personal Access Token）。

## 第三章：帝国的“做减法”哲学

在搞 PAT 的过程中，我不禁回顾这几个月走过的路：

我曾经造过底层内核，最后停更；我曾经追求极致的轻量去用 Tauri，被 Win7 的 WebView2 教做人，最后乖乖回归到了沉重但兼容性无敌的 Electron（ia32老版本+自签名证书）；我甚至搞了一套“三公九卿”制度，结果管事的还没开张，锦衣卫们还在抓杀软误报。

兜兜转转，我终于悟了那句我自己说过的话：加密工具，做减法比加法安全。

所以我释然了，乖乖建一个 Fine-grained PAT（只勾选 Contents: Read and write），让 Bot 学会走自动 PR 的流程。

### 尾声：Go for it. Here We Go!

从写 C++ N-API 底层，到做 Electron GUI，再到给 Cloudflare Workers 写无服务器后端，现在又和 GitHub DevOps 斗智斗勇。作为 CrCLARE Studio 的 Owner，我不仅要制定游戏世界的宇宙规则，还要给机器人们排班站岗。

每一次报错，都是在为帝国的基石打补丁。

好了，不多说了，我去给机器人发“特别通行证”（PAT）了。祝愿明天，Chronos Seal 的流水线能跑得比我的动森小岛还要顺畅。

> Time as the seal, action as the key.
> 小小的老子，终究要搞定大大的报错。
> Go for it. Here We Go! 🚀
