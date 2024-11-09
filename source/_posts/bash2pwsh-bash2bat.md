---
title: 将Bash脚本转为PowerShell或者Batch的工具 ｜ Tools can be used to convert Bash scripts into PowerShell or Batch
date: 2024-11-09 18:14:48
tags:
---
# 前言 ｜ Preface
各位写脚本的时候是否遇见过要为每个平台都写一份脚本的麻烦事？明明python很好用，但是为了无依赖运行只能用原生脚本？前段时间我写校园网登录脚本的时候就遇见了这个麻烦。  
Have you ever encountered the hassle of writing separate scripts for each platform when scripting? Despite Python being a great choice, it can only be used to run natively if it's an original script. I experienced this issue myself when writing a script to log in to the campus network recently.

一开始，我想通过设计一种能编译为其他脚本的语言来实现“一次编写，到处运行”，就像haxe和cmake那样，但想了想，还是直接翻译现成的bash脚本来的实在一点。于是我在github上一番翻找，终于找到了以下两个开源项目，他们分别实现了bash转powershell和bash转bat。  
At the beginning, I thought of designing a language that could compile to other scripts to achieve "one write, run anywhere", similar to Haxe and CMake. However, after thinking about it, I decided to translate existing bash scripts instead. So, I went on a search on GitHub and finally found two open-source projects, one implementing bash to PowerShell and the other implementing bash to BAT.

# Bash -> Bat
* 项目｜ Repository：[bash-shell-to-bat-converter](https://github.com/daniel-sc/bash-shell-to-bat-converter)
* 作者 ｜ Author：[daniel-sc](https://github.com/daniel-sc)
* 协议 ｜ License：MIT

这是一个由typescript写的脚本程序，因此你既可以克隆到在本地运行：  
This is a TypeScript program, so you can clone it and run it locally:
```bash
npx bash-converter FILE_TO_CONVERT.sh
```

也可以在线体验：  
Or try it online:  
https://daniel-sc.github.io/bash-shell-to-bat-converter/

## 注意 ｜ Note
该脚本不能保证翻译100%正确，但总比从头写一个好。  
This script cannot guarantee 100% accurate translation, but it's better than writing everything from scratch.

# Bash -> PowerShell
* 项目｜ Repository：[bash-to-powershell-converter](https://github.com/nyabkun/bash-to-powershell-converter)
* 作者 ｜ Author：[nyabkun](https://github.com/nyabkun)
* 协议 ｜ License：MIT

这个项目则是使用js写的，因此同样可以克隆到本地然后用nodejs执行：  
This project is written in JavaScript, so it can also be cloned and executed with Node.js:
```bash
node bash2pwsh.js ./You-can-test-with-this-bash-script/.bash_profile bash_profile.ps1
```
因为作者没有提供网页版，所以我写了一个简易的网页套壳：  
Because the author did not provide a web version, I created a simple one:  
https://chifahe.github.io/Convert-Bash-to-PowerShell-Online/

## 注意 ｜ Note
该脚本仅支持一些简单的语法，如imports和aliases。  
Only simple things like imports and aliases are supported.

# 结语 ｜ Conclusion
虽然但是，在实际使用中我们往往会用到一些特定平台才会有的指令，比如windows下的计划任务schtasks，linux下的systemd，又或者是在linux和macos下语法相似但细节又不同的的sed，导致实际上减少不了多少工作量。这么看来，还是python好用～  
Although, in reality, we often use specific commands that are unique to certain platforms like Windows' schedule tasks (schtasks), Linux's systemd, or the similar but detailed differences sed has on macOS. This is unlikely going to save many time after all, so I guess Python is still a good choice.