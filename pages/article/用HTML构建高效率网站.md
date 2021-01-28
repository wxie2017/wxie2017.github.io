---
layout: page
title: 用HTML构建高效率网站
description: an article about HTML websites
---


最近在看 [GNUnited
Nations](https://www.gnu.org/software/trans-coord/manual/gnun/gnun.html#Introduction)
的使用手册。它是一个让 [GNU 官网](https://www.gnu.com)的多语言网页及时上线的工具。

GNU 官网内容非常之多，而且支持的语言也非常之多，所以维护的工作量很大。无论是原文
的变化，还是翻译的变化，都是通过 GNUnited Nations（简称 GNUN）来完成的。GNUN 是
一系列基于 GNUmakefile 的脚本，它能够完成如此大的工作量部分得益于 GNU 官网是完全
基于简单HMTL设计的。

相对于当下大多数网站使用复杂的架构，有前端，有后端，有中台等，简单HTML构建的网站
兼容性和普适性很强，而且无需耗费大量的系统资源和流量。这些对使用较低端电脑和设备
的用户是非常大的帮助——并不是每个人都使用 16 GB 内存的 8 核手机，也不是每个人都在
使用无限制 5G 流量套餐。但是，很多人都有需求打开网站——他们的需求有时非常必要。

当你通过简单的 HTML 表单可以完成在线申请的时候，为什么需要使用复杂的文档编辑插件？

当简单的 HTML 加上 CSS 可以构建清爽亮丽的网页时，为什么需要使用复杂的 JavaScript？

当<div>可以实现按钮功能的时候，为什么还要进行各种曲折的对象调用？

当有大量图片加载的时候，为什么不使用<alt>为低流量预算用户提供方便？

当HTML支持无障碍标准的时候，为什么还要陷入 PDF 的泥潭？

有很多工具可以帮助你自动生成 HTML 页面，其中有 GNU Emacs 的 Org-mode。GNUN 可以
帮助你实现所有 HTML 页面的多语言构建，并检查其中的语法错误。

请使用简单的 HTML 让互联网变得更高效。
