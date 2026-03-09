---
title: "FuckYourACE — 游戏反作弊进程限制工具"
date: 2025-08-15
tags: ["Go", "Windows", "Wails", "工具"]
summary: "打游戏被 SGuard 吃满 CPU？这个小工具帮你把它关进小黑屋。"
---

## 起因

玩腾讯游戏的都知道，`SGuard64.exe` 这玩意儿动不动就把 CPU 吃到 20%+，游戏本来就吃性能，再加上这个后台进程，帧数直接暴跌。

关掉？不行，游戏会闪退。杀进程？账号可能异常。

所以思路很简单：**不关它，但把它限制住**。

## 原理

程序做的事情不复杂：

1. 每 60 秒扫一遍系统进程，找到 `SGuard64.exe` 和 `SGuardSvc64.exe`
2. 检测 CPU 有没有能效核（E-Core），有的话就用 E-Core，没有就用最后一个逻辑核心
3. 把目标进程的 CPU 亲和性绑到那个核心上
4. 优先级降到最低（Idle）

相当于给它画了个圈："你就在这待着，别出来。"

循环执行是因为这些进程会自己恢复设置，所以得持续压制。

## 技术实现

用 [Wails v2](https://wails.io/) 做的桌面应用，Go 后端 + 前端 UI。选 Wails 是因为打包出来就一个 exe，不用装运行时，双击就能用。

核心逻辑都在 Go 这边，调的 Windows API：
- `SetProcessAffinityMask` 绑核
- `SetPriorityClass` 降优先级
- 大小核检测用的 `GetLogicalProcessorInformationEx`

进程名单后来改成云端下发了，这样加新的目标进程不用更新程序。

## 使用

下载 exe，右键管理员运行，完事。最小化挂着就行。

日志在 `%AppData%\FuckYourACE\app.log`，出问题可以看看。

> 项目地址：[github.com/xiaoxinmm/FuckYourACE](https://github.com/xiaoxinmm/FuckYourACE)

124 个 star，说明确实解决了不少人的痛点。
