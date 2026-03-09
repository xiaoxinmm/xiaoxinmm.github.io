---
title: "我的开源项目整理"
date: 2026-03-09
tags: ["开源", "总结"]
summary: "整理一下自己在 GitHub 上公开的几个项目，记录一下当时为什么做、解决了什么问题。"
weight: 1
---

陆陆续续写了一些开源项目，有的是工作中用到的，有的是自己折腾着玩的。趁搭博客的机会整理一下。

## 🎮 FuckYourACE

**[GitHub](https://github.com/xiaoxinmm/FuckYourACE)** · Go / Wails · ⭐ 124

限制游戏反作弊进程 CPU 占用的工具。不杀进程，而是把它绑到小核上并降低优先级。打腾讯游戏的应该都懂这个痛点。

👉 [详细介绍](/posts/fuckyourace/)

## 📊 sysmon

**[GitHub](https://github.com/xiaoxinmm/sysmon)** · Go · ⭐ 15

轻量系统探针，单文件部署。CPU/内存/磁盘/网络实时监控 + Web 终端。给小机器用的，一个二进制扔上去就完事。

👉 [详细介绍](/posts/sysmon/)

## 📋 学生会违纪管理系统

**[GitHub](https://github.com/xiaoxinmm/Student-Union-Violation)** · Go + Gin + MySQL

学校内部用的系统，原来 PHP 那版漏洞太多，用 Go 重写的。录入、查询、公示、导出，Docker 一键部署。

👉 [详细介绍](/posts/student-union-violation/)

## 🔧 donut-lite

**[GitHub](https://github.com/xiaoxinmm/donut-lite)** · C

donut shellcode 生成器的精简版，只保留命令行工具，去掉了 loader 源码和 Python 绑定。快速编译、快速使用。

👉 [详细介绍](/posts/donut-lite/)

---

## 归档项目

以下项目已经不再维护：

- **Zray** / **Zray-for-Android** — 尝试用 AI 重写过一次，效果不太理想，精力有限就不继续了。有兴趣的可以自行 fork。

---

后面有新项目会继续更新这个列表。
