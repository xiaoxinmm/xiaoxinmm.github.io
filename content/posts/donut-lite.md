---
title: "donut-lite — 精简版 shellcode 生成器"
date: 2025-03-01
tags: ["C", "安全", "工具"]
summary: "donut 的最小化构建，只保留命令行生成功能，去掉了 loader 源码和 Python 绑定。"
---

## 是什么

[donut](https://github.com/TheWover/donut) 是一个挺知名的 shellcode 生成器，能把 .NET 程序集、PE 文件之类的东西转成位置无关的 shellcode。

问题是原项目包含了一大堆东西：loader 源码、Python 绑定、各种示例……很多时候只需要那个命令行工具。

donut-lite 就是做了一次瘦身，**只保留 `./donut` 命令行工具需要的文件**。

## 构建

```bash
make        # Linux
make win    # Windows 交叉编译（需要 mingw）
```

没什么花哨的，Makefile 几行搞定。

## 为什么做这个

实际使用中经常需要在不同环境快速编译一个 donut 出来，原项目 clone 下来一堆文件，编译还容易出问题。精简之后 clone 快、编译快、没有多余依赖。

安全工具嘛，够用、能跑、不出错就行。

> 项目地址：[github.com/xiaoxinmm/donut-lite](https://github.com/xiaoxinmm/donut-lite)
