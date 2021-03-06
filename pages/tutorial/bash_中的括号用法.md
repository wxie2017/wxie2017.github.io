---
layout: page
title: BASH 中括号的用法
description: braket in BASH for 35 coral anniversary of FSF
---


10 月 4 日是自由软件基金会（FSF）成立的日子，今年是 35 周年——珊瑚年庆。

自由软件基金会是一个非盈利组织。其使命是在全球范围内促进计算机用户的自由，并捍卫
所有软件用户的权利。

自由软件社区正如珊瑚生态一样。珊瑚礁是由许许多多不同物种聚集而成的巨大生命集体，
大家共享资源、互相支持、繁衍不息。自由软件社区也是由许许多多热爱自由、乐于助人、
热爱技术的人互相鼓励、互相学习、共同贡献而成的。软件自由目前正面临着与日俱增的威
胁，同样地，世界各地的珊瑚生态也面临着严重生存挑战。保护珊瑚的呼声日渐高涨。

我觉得要写一些什么作为纪念，以示 35 年的自由软件运动还要继续，直至每个计算机用户
都拥有完全的计算自由。

[BASH](https://www.gnu.org/software/bash/) 在我看来是一个最常用的自由软件，它也
是 GNU 工程最早的软件之一。每当你打开电脑终端，你就进入了 BASH 的世界。无论你是
查找文件，还是编译软件，BASH 都为你打开了通道。BASH 遵循 IEEE POSIX P1003.2/ISO
9945.2 标准，可以运行大多数的 shell 脚本，包括 ksh 和 csh 脚本。

BASH 脚本语言非常强大，也是图灵完备的编程语言。今天我们就以 BASH 中的括号用法小
结来纪念自由软件基金会的 35 年珊瑚庆。

* 圆括号/小括号：()

1. (cd ~/public; pwd)
在一个子 shell 进程里执行括号里的一组用分号 `;` 号隔开的命令。

2. VAR=$(cat file.txt)
执行括号内的命令并将结果赋值给变量。

3.x=(1 2 3)
创建一个数组 x。

4.x=$((2+3))
$(()) 进行数学运算。

* 方括号/中括号：[]

1. if [ ... ]
[ ] 会执行其内部的命令或测试，根据结果返回 0 或 1 的状态。

2. if [[ ... ]]
[[ ]] 是 BASH 特有的语法，和 [ ] 比更丰富、强大。

* 花括号/大括号：{}

1. {cd ~/music; pwd}
在当前 shell 里执行括号里一组用 `;` 号隔开的命令。

2. echo {a,b}.png
扩展为 a.png b.png。

3. echo ${var}
解析变量，和 $var 及 "$var" 一样。

4. ${var//search/replace}
${...} 是一个具有丰富功能的命令。它可以替换字符串，可以取子字符串，可以算字符串长度，
可以切换大小写等等。

当然，BASH 的括号还有其他用法——主要是在脚本里使用，我们就不再一一列举了。括号只
是 BASH 语法的冰山一角，此处抛砖引玉，让大家了解：

自由软件不仅给你自由，而且自由软件本身也很出色。
祝自由软件基金会 35 年珊瑚庆快乐！
