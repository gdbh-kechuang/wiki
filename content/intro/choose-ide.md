---
title: 选择并配置IDE
description: 
published: true
date: 2025-08-25T10:50:38.676Z
tags: arm, keil, c/c++
editor: markdown
dateCreated: 2025-03-13T11:34:55.761Z
---

## 开发环境（IDE）是？

集成开发环境（IDE, Integrated Development Environment），是将各种编程所需的工具整合一起的软件集合，旨在提升开发者的工作效率、简化开发流程、减少来回跳跃于不同工具之间的不便。

## 获取主流 IDE 

### Keil MDK (Keil μVision)

由德国软件开发商 Keil （2005 年 Keil 被 ARM 收购后）开发的经典老字号 IDE，应该是 ARM 生态使用最广泛的，至今依旧在维护。

1. 访问 Keil μVision 的下载地址：<https://www.keil.com/demo/eval/arm.htm>
2. 你会看到一个申请表单、**不必担心是不是要注册要会员什么的**，这个表单如今已经没有实际作用了，按要求随意填写，然後点击 Submit
   ![申请表单.webp](/assets/uvision-form.webp)
3. 然後跳转到真正的下载界面，点击链接下载
4. 打开下载完成的应用程序，进行安装
5. 运行 μVision，从上方的菜单栏依次找到： - File -> License Management... -> User-Based License - 点击 Activate / Deactive... 按钮
   ![软件内激活页面.webp](/assets/uvision-activate-utility.webp)
6. 跳转到 Arm License Management Utility 页面： - Activate with: 选中 License Server - 在下方填入“<https://mdk-preview.keil.arm.com>”并点击 Query 按钮 - 在下方选择 Keil MDK Community 版本并点击 Activate 按钮
   ![授权管理](/assets/uvision-license-management.webp)
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
