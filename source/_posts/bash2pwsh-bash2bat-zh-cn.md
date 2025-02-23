---
title: 将 Bash 脚本转为 PowerShell 或者 Batch 的工具
date: 2025-01-19 22:09:03
categories: ZH-CN
tags:
    - Bash
    - Batch
    - PowerShell
    - Tools
---

## 前言

各位写脚本的时候是否遇见过要为每个平台都写一份脚本的麻烦事？明明 python 很好用，但是为了无依赖运行只能用原生脚本？前段时间我写校园网登录脚本的时候就遇见了这个麻烦。  
一开始，我想通过设计一种能编译为其他脚本的语言，就像 haxe 和 cmake 那样，但想了想，还是直接翻译现成的 bash 脚本来的实在一点。于是我在 github 上一番翻找，终于找到了以下两个开源项目，他们分别实现了 bash 转 powershell 和 bash 转 bat。

## Bash -> Bat

-   项目：[bash-shell-to-bat-converter](https://github.com/daniel-sc/bash-shell-to-bat-converter)
-   作者：[daniel-sc](https://github.com/daniel-sc)
-   协议：MIT

这是一个由 typescript 写的脚本程序，因此你既可以克隆到在本地运行：

```bash
npx bash-converter FILE_TO_CONVERT.sh
```

也可以在线体验：  
https://daniel-sc.github.io/bash-shell-to-bat-converter/

### 注意

该脚本不能保证翻译 100%正确。

## Bash -> PowerShell

-   项目：[bash-to-powershell-converter](https://github.com/nyabkun/bash-to-powershell-converter)
-   作者：[nyabkun](https://github.com/nyabkun)
-   协议：MIT

这个项目也是使用 js 写的，因此同样可以克隆到本地然后用 nodejs 执行：

```bash
node bash2pwsh.js ./You-can-test-with-this-bash-script/.bash_profile bash_profile.ps1
```

因为作者没有提供网页版，所以我写了一个简易的网页套壳：  
https://chifahe.github.io/bash-to-powershell-converter-online/

### 注意

该脚本仅支持一些简单的语法，如 imports 和 aliases。

## 结语

虽然但是，在实际使用中我们往往会用到一些特定平台才会有的指令，比如 windows 下的计划任务 schtasks，linux 下的 systemd，又或者是在 linux 和 macos 下语法相似但细节又不同的的 sed，导致实际上减少不了多少工作量。这么看来，还是 python 好用～
