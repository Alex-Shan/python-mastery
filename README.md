# 精通 Python 高级编程

> 本分支为简体中文文字教材，保留原目录结构、示例代码和数据。
> [英文原版](https://github.com/dabeaz-course/python-mastery) · [中文练习目录](Exercises/index.md) · [许可原文](LICENSE.md)
> `PythonMastery.pdf` 保留为英文原版。本版仅翻译文字，不修改课程或修复版本兼容问题。翻译与修订沿用 CC BY-SA 4.0 许可。
> 下文保留了作者不同时期的说明；涉及最新版兼容性的旧说明，请结合 2026 年 10 月 22 日的归档通知阅读。


课程作者：David Beazley (https://www.dabeaz.com)<br>
Copyright (C) 2007-2026

## 重要说明（2026 年 10 月 22 日）

最近的 Python 版本似乎使本课程的部分内容无法正常工作。我没有动力继续更新，因此决定将课程归档并停止维护。感谢大家多年来的支持。——Dave

## 课程简介

这是一门以练习驱动的高级 Python 编程课程，十余年间在企业培训中经过数百次实战检验。作者 David Beazley 同时著有 [《Python Cookbook》第 3 版](https://www.dabeaz.com/cookbook.html)（O'Reilly）和 [《Python Distilled》](https://www.dabeaz.com/python-distilled/index.html)（Addison-Wesley）。课程以知识共享许可发布，不含广告、跟踪、弹窗、邮件订阅或 AI。

本课程的所有内容本应能在最新版 Python 上运行，但主要面向 Python 3.6 的特性，因此不涵盖某些现代功能。坦率地说，除非你打算写特别炫技的代码，否则这通常不会产生太大影响。

## 适合人群

本课程面向希望从短脚本迈向更复杂程序的 Python 程序员。为此，了解流行库和框架中的编程技巧很有帮助。因此，课程主要帮助你更完整地理解 Python 语言本身及其工作方式，最终将这些知识用于自己的项目。

## 预备知识

你应已掌握一些 Python 知识。本课程不面向初学者。入门内容可参阅[《Python 实用编程》](https://dabeaz-course.github.io/practical-python)。

## 如何学习

首先，将 GitHub 仓库 fork 或克隆到本机。

课程假设你在合适的本地 Python 开发环境工作，包括正确安装的 Python、编辑器或 IDE，以及平时使用的其他开发工具。由于涉及多个文件和模块导入，不建议使用 Notebook。

[`PythonMastery.pdf`](PythonMastery.pdf) 包含详细演示幻灯片，并明确标注课程练习和建议用时。建议将其放在手边，下载后用本地 PDF 阅读器查看。从这里开始！该文件保留为英文原版。

[Exercises/](Exercises/index.md) 包含全部课程练习。

[Solutions/](Solutions/) 包含完整解答代码。

[Data/](Data/) 包含课程使用的数据文件。

课程最初采用 4–5 天的面授形式，结合讲授与动手练习。完整学习通常需要 30–50 小时。练习往往逐步衔接；遇到困难时，始终有解答可供参考。

## 补充材料

本课程经常推荐针对特定主题的深入教程。这些教程曾在 PyCon 大会讲授，或许值得一看：

* [面向系统程序员的生成器技巧](https://www.dabeaz.com/generators/)
* [协程与并发趣味课程](http://dabeaz.com/coroutines/index.html)
* [Python 3 元编程](https://dabeaz.com/py3meta/index.html)
* [生成器：最后的边界](https://dabeaz.com/finalgenerator/index.html)
* [模块与包：生存与消亡](https://dabeaz.com/modulepackage/index.html)

## 问答

**问：有视频吗？**

**答：** 没有。阅读包含技术信息的幻灯片会更快。不过，O'Reilly Safari 平台上的 [《Python 编程语言：视频课程》](https://www.safaribooksonline.com/library/view/python-programming-language/9780134217314/) 视频与本课程内容密切相关。

**问：可以在自己的课程中使用这些材料吗？**

**答：** 可以，只需适当注明出处。

**问：接受错误报告或拉取请求吗？**

**答：** 发现错误请报告！不过，我不打算通过新主题或练习扩充或重组课程。

**问：幻灯片还有 PDF 以外的格式吗？**

**答：** 没有。

**问：有没有讨论课程的论坛或聊天室？**

**答：** 可以使用 [GitHub Discussions](https://github.com/dabeaz-course/python-mastery/discussions) 讨论课程。

**问：为什么没有涵盖某个主题、工具或库？**

**答：** 课程设计为高强度的 4 天面授，不可能涵盖所有内容。因此主要聚焦 Python 核心语言，而不是第三方库或工具。

**问：为什么没有涵盖 typing、async 或模式匹配等特性？**

**答：** 主要受开发时间和范围所限。课程大部分内容在疫情前开发，反映当时的 Python。一些主题，例如 typing 或 async，足够复杂，更适合独立课程。

**问：有计划更新课程以适应现代 Python 吗？**

**答：** 我的本意是让所有内容适用于最新版 Python。除非 Python 对核心语言作出不向后兼容的修改，否则应能保持。尽管课程并不涵盖所有新特性，我也不排除未来修改的可能。这很大程度上取决于时间和兴趣，因此不作承诺。

**问：为什么公开这门课程？**

**答：** 疫情前，这门课已广泛讲授。疫情后，我的教学转向项目与计算机科学基础。不过，为什么要让一门好课闲置在自己的电脑上呢？

**问：我能如何帮忙？**

**答：** 如果喜欢本课程，最好的支持方式是向其他人推荐它。

----
`>>>` 精通 Python 高级编程<br>
`...` 课程作者： [dabeaz](https://www.dabeaz.com)<br>
`...` Copyright 2007-2023

![](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)。 本作品采用 [知识共享 署名—相同方式共享 4.0 国际许可协议](http://creativecommons.org/licenses/by-sa/4.0/)
