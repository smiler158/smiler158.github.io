---
layout: post
category: "reading"
title: "静态代码分析"
tags: ["代码分析"]
---

#### 什么是静态代码分析
静态代码分析是指无需运行被测代码，仅通过分析或检查源程序的语法、结构、过程、接口等来检查程序的正确性，找出代码隐藏的错误和缺陷，如参数不匹配，有歧义的嵌套语句，错误的递归，非法计算，可能出现的空指针引用等等。
在软件开发过程中，静态代码分析往往先于动态测试之前进行，同时也可以作为制定动态测试用例的参考。统计证明，在整个软件开发生命周期中，30% 至 70% 的代码逻辑设计和编码缺陷是可以通过静态代码分析来发现和修复的。

## 现有主流 Java 静态分析工具

1. Checkstyle 是 SourceForge 的开源项目，通过检查对代码编码格式，命名约定，Javadoc，类设计等方面进行代码规范和风格的检查，从而有效约束开发人员更好地遵循代码编写规范。
    ![Smaller icon](/images/checkstyle.gif "checkstyle")

2. FindBugs 是由马里兰大学提供的一款开源 Java 静态代码分析工具。FindBugs 通过检查类文件或 JAR 文件，将字节码与一组缺陷模式进行对比从而发现代码缺陷，完成静态代码分析。FindBugs 既提供可视化 UI 界面，同时也可以作为 Eclipse 插件使用。文本将主要使用将 FindBugs 作为 Eclipse 插件。在安装成功后会在 eclipse 中增加 FindBugs perspective，用户可以对指定 Java 类或 JAR 文件运行 FindBugs，此时 FindBugs 会遍历指定文件，进行静态代码分析，并将代码分析结果显示在 FindBugs perspective 的 bugs explorer 中。

    ![Smaller icon](/images/findbug.gif "findbug")

3. PMD 是由 DARPA 在 SourceForge 上发布的开源 Java 代码静态分析工具。PMD 通过其内置的编码规则对 Java 代码进行静态检查，主要包括对潜在的 bug，未使用的代码，重复的代码，循环体创建新对象等问题的检验。PMD 提供了和多种 Java IDE 的集成，例如 Eclipse，IDEA，NetBean 等。
    ![Smaller icon](/images/pmd.gif "pmd")
4. Jtest 是 Parasoft 公司推出的一款针对 Java 语言的自动化代码优化和测试工具，Jtest 的静态代码分析功能能够按照其内置的超过 800 条的 Java 编码规范自动检查并纠正这些隐蔽且难以修复的编码错误。同时，还支持用户自定义编码规则，帮助用户预防一些特殊用法的错误。


####功能对比



| 代码缺陷分类 | 示例                |	 Checkstyle | FindBugs | PMD | Jtest |

| ---------- | ----                | ------------ | -------- | --- | ————— |

| 引用操作      | 空指针引用          |   √         |     √   | 	  √	|  √   |

| 对象操作      | 对象比较（使用 == 而不是 equals）|  | √        |   √   | √    |

| 表达式复杂化   | 多余的 if 语句		|             |          |   √  |        |

| 数组使用      | 数组下标越界			|             |         |      |  √     |

| 未使用变量或代码段 | 未使用变量	    |             |     √    |   √  |  √    |

| 资源回收      | I/O 未关闭		    |             |      √    |      | √     |

| 方法调用      | 未使用方法返回值		|              |  √       |      |      |

| 代码设计      | 空的 try/catch/finally 块 |	       |           |   √  |      |


#### 总结
本文分别从功能、特性和内置编程规范等方面详细介绍了包括 Checkstyle，FindBugs，PMD，Jtest 在内的四种主流 Java 静态代码分析工具，并通过一段 Java 代码示例对这四种工具的代码分析能力进行比较。由于这四种工具内置编程规范各有不同，因此它们对不同种类的代码问题的发现能力也有所不同。其中 Checkstyle 更加偏重于代码编写格式检查，而 FindBugs，PMD，Jtest 着重于发现代码缺陷。最后，希望本文能够帮助 Java 软件开发和测试人员进一步了解以上四种主流 Java 静态分析工具，并帮助他们根据需求选择合适的工具。