---
title: Tools can be used to convert Bash scripts into PowerShell or Batch
date: 2025-01-19 22:09:03
categories: EN
tags:
    - Bash
    - Batch
    - PowerShell
    - Tools
---

## Preface

Have you ever encountered the hassle of writing separate scripts for each platform when scripting? Despite Python being a great choice, it can only be used to run natively if it's an original script. I experienced this issue myself when writing a script to log in to the campus network recently.  
At the beginning, I thought of designing a language that could compile to other scripts to achieve "one write, run anywhere", similar to Haxe and CMake. However, after thinking about it, I decided to translate existing bash scripts instead. So, I went on a search on GitHub and finally found two open-source projects, one implementing bash to PowerShell and the other implementing bash to BAT.

## Bash -> Bat

-   Repository：[bash-shell-to-bat-converter](https://github.com/daniel-sc/bash-shell-to-bat-converter)
-   Author：[daniel-sc](https://github.com/daniel-sc)
-   License：MIT

This is a TypeScript program, so you can clone it and run it locally:

```bash
npx bash-converter FILE_TO_CONVERT.sh
```

Or try it online:  
https://daniel-sc.github.io/bash-shell-to-bat-converter/

### Note

This script cannot guarantee 100% accurate translation, but it's better than writing everything from scratch.

## Bash -> PowerShell

-   Repository：[bash-to-powershell-converter](https://github.com/nyabkun/bash-to-powershell-converter)
-   Author：[nyabkun](https://github.com/nyabkun)
-   License：MIT

This project is written in JavaScript, so it can also be cloned and executed with Node.js:

```bash
node bash2pwsh.js ./You-can-test-with-this-bash-script/.bash_profile bash_profile.ps1
```

Because the author did not provide a web version, I created a simple one:  
https://chifahe.github.io/bash-to-powershell-converter-online/

### Note

Only simple things like imports and aliases are supported.

## Conclusion

Although, actually, we often use specific commands that are unique to certain platforms like Windows' schedule tasks (schtasks), Linux's systemd, or the similar but detailed differences sed has on macOS. This is unlikely going to save many time after all, so I guess Python is still a good choice.
