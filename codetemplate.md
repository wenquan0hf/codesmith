# 基本语法-CodeTemplate 指令

前面的几篇介绍了使用 CodeSmith 模板自动生成代码和编写代码模板的基本知识。也说过 CodeSmith最核心的部分是代码模板，从本篇开始介绍 CodeSmith 代码模板的基本语法，对于 Asp.Net 程序员来说，可以说是碰到老朋友了:-) ，CodeSmith 的代码模板和 Asp.Net Page 几乎如出一辙。

本篇介绍 CodeTemplate 指令，这个是模板中唯一必须的声明，包含一些模板特殊的属性，包含模板使用的语言、生成的语言和一些对于模板的描述。比如：

```
<%@ CodeTemplate Language="C#" TargetLanguage="C#" Description="This is a demo template" %>
```

参数的介绍：

- Language：在开发编写模板时使用的语言，例如 C#，VB.NET，Jscript 等。
- TargetLanguage：只是对模板代码的一个分类，不会影响生成的代码语言。是模板的一个属性，说明模板要基于那种语言生成相应的代码。例如你可以用 CodeSmith 从任何一种语言生成C#代码。
- Description：对于模板的一些说明信息，在 CodeSmith Explorer 中选中该模板时会显示这里的信息。
- Inherits：所有 CodeSmith 模板默认继承自 CodeSmith.Engine.CodeTemplate，这个类提供模板使用的一些基本功能，像 ASP.NET 页面的 Page 类，这些被继承的类的属性可以被修改，但是这些新的类也必须继承 CodeSmith.Engine.CodeTemplate。CodeSmith 也同样可以找到这个类，当然你要引入一个组件包含这个类。
- Src：在某些方面 Src 和继承 Inherits 比较相似，它们都允许你从其他的类包含一些功能进模板。这两个属性的区别是，Src 可以让类与你的模板被动态编译，而 Inherits 仅允许你提供一个已经编译好的类或组件。
- Debug：可以确定是否在模板中可以包含调试符号。如果将这个属性设置为 True，则可以使用System.Diagnostics.Debugger.Break()方法来设置断点。
- LinePragmas：设置为 True，模板的错误将被指向到模板的源代码。设置为 False，模板的错误将被指向到编译的源代码。
- ResponseEncoding 指明代码模板的输出文件的编码方式，可以为 System.Text.Encoding.GetEncoding 支持的所有编码方式，如果输出文件已存在并且和要生成的内容一致，输出文件的编码方式不会变化。
- OutputType 指明输出文件的的输出模式，可以有三种模式:

Normal: 正常模式，代码模板输出内容写到正常的输出流（Response Stream）。
Trace： 输出内容写到 Trace（调试）输出流中。
None： 控制代码模板不输出任何内容，主要用在主-从模板的主模板中，有些情况下无需主模板输出任何内容。

- NoWarn 不显示某些编译警告，Warning 的 ID 使用逗号分隔，主要用在编译 C# 和 VB.Net 时用到。
- ClassName  使用 Code-Behind 时对应的类名称，类似于 Asp.Net 代码。
- Namespace 使用 Code-Behind 时对应的类命名空间名称。
- Encoding  代码模板自身使用的编码方式，缺省为 UTF-8.

Tags: [CodeSmith](http://www.imobilebbs.com/wordpress/archives/tag/codesmith)