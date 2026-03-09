---
title: "sysmon — 单文件系统监控探针"
date: 2025-06-20
tags: ["Go", "Linux", "运维", "监控"]
summary: "一个 Go 写的轻量系统探针，自带 Web 终端，单文件部署，扔上去就能用。"
---

## 为什么又造轮子

市面上监控工具不少，Prometheus + Grafana 一套下来确实强大，但有时候就是想在一台小机器上快速看看 CPU、内存、磁盘情况，再开个终端敲两下命令。装一整套监控栈太重了。

所以写了 sysmon：**一个二进制文件，扔上去运行，浏览器打开就能用。**

## 功能

该有的都有：

- CPU、内存、磁盘、网络实时监控，WebSocket 推送
- 进程列表，支持按 CPU/内存排序
- 历史趋势图，看一段时间内的变化
- Docker 容器状态自动检测
- **Web 终端**（WebShell）— 浏览器里直接操作服务器，完整 PTY 支持
- 密码认证，终端和监控页面可以设不同密码
- 前端资源全部 embed 进二进制，真·单文件

## 部署

一行命令：

```bash
bash <(curl -sL https://raw.githubusercontent.com/xiaoxinmm/sysmon/master/install.sh)
```

自动下载二进制、创建配置、注册 systemd 服务。装完访问 `http://你的IP:8888`。

也可以手动编译：

```bash
git clone https://github.com/xiaoxinmm/sysmon.git
cd sysmon && go build -o sysmon . && ./sysmon
```

配置支持 JSON 文件和环境变量两种方式，看场景选择。

## 一些设计考虑

- Go 的 `embed` 包把前端打进去，部署就是复制一个文件
- WebSocket 做实时推送，不轮询
- Web 终端用 xterm.js + PTY，体验接近真终端
- 密码用 HMAC-SHA256，不存明文

手机上也能看，做了响应式适配。服务器出问题的时候掏出手机就能查状态、敲命令，比 SSH 客户端方便。

> 项目地址：[github.com/xiaoxinmm/sysmon](https://github.com/xiaoxinmm/sysmon)
