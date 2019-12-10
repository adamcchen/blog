---
title: 单指令多线程
date: 2019-11-20 12:00:00
tags: GPU
---

SIMT，Single Instruction Multiple Instructions，单指令多线程。

SIMT是为了实现时延隐藏。

> SIMT = SIMD + 多线程

在NVIDIA的GPU中，

> SIMT = SIMD + Warp

一个Warp为32个线程。
