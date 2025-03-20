---
title: 选择并配置IDE
description:
published: true
date: 2025-03-13T11:34:55.761Z
tags: arm, keil, c/c++
editor: markdown
dateCreated: 2025-03-13T11:34:55.761Z
---

## 开发环境 IDE 是？

集成开发环境（IDE, Integrated Development Environment），本质是将各种编程所需的各种工具整合一起的软件，主要目的是提升开发者的工作效率、简化开发流程、减少来回跳跃于不同工具之间。

想象一下不使用 IDE 的原始人情景：写代码要打开一个文件编辑器、编译代码工程要手敲命令行、编译出的程序上传到目标机器要用硬件开发商对应的软硬件，以及上述过程中遇到的问题都不能直观发现。让现代人这么折腾，极大概率光速弃坑 😇。

## 主流 IDE 介绍

### Arm Keil MDK (Keil μVision)

> 这个是 ARM 官方教程，如果你遇到什么问题或者单纯嫌麻烦，可以去找学长要那种 Keil 注册机 🎶💥💥

由德国软件开发商 Keil （2005 年 Keil 被 ARM 收购后）开发的经典老字号 IDE，应该是 ARM 生态使用最广泛的，至今依旧在维护。

1. 访问 Keil μVision 的下载地址：<https://www.keil.com/demo/eval/arm.htm>
2. 你会看到一个申请表单、**不必担心是不是要注册要会员什么的**，这个表单如今已经失去意义，按要求随意填写，然後点击 Submit
   ![申请表单.webp](/uvision-form.webp)
3. 然後跳转到真正的下载界面，点击链接下载
4. 打开下载完成的应用程序，进行安装
5. 运行 μVision，从上方的菜单栏依次找到： - File -> License Management... -> User-Based License - 点击 Activate / Deactive... 按钮
   ![软件内激活页面.webp](/uvision-activate-utility.webp)
6. 跳转到 Arm License Management Utility 页面： - Activate with: 选中 License Server - 在下方填入“<https://mdk-preview.keil.arm.com>”并点击 Query 按钮 - 在下方选择 Keil MDK Community 版本并点击 Activate 按钮
   ![授权管理](/uvision-license-management.webp)
7. 完成

### Arm Keil Studio

ARM 于 2023 年推出的新 IDE，但并不是一个独立的新软件，而是基于 VSCode 的插件。

> Keil Studio 的生态依旧不够成熟，可能无法做到完全和旧的 μVision 切割。

1. 首先当然是[下载 VSCode](https://code.visualstudio.com/)
2. 访问插件商城，获取 [Keil Stuido 插件](https://code.visualstudio.com/)
3. 完成

## 参考资料

[维基百科](https://en.wikipedia.org/wiki/Integrated_development_environment)
[获取社区版 MDK](https://www.keil.arm.com/mdk-community/)
