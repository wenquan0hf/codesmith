# 引用其它文件或 .Net 类库

在 CodeSmith 模板中可以引用 .Net 类库，和普通的 .Net 项目不同的是，对 .Net 库的引用不是通过项目的 Add reference 来实现，而是通过在代码模板中指明所要引用的 Assembly.

比如引用 CodeSmith 自带的 CodeSmith.CustomProperties.dll ，可以使用如下语句：

```
<%@ Assembly Name="CodeSmith.CustomProperties" %>
```

- Name指明所有需要引用的 Assembly 的名称，也可以使用 Assembly 的全名，比如ExampleAssembly, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null
- Src 指明可以动态编译的源码的相对路径名称
- Path 指明应用的 Assembly 存放的路径

引用合适的 Assembly 之后，和普遍 C# 语言类似，对于使用到的 .Net 类，需要通过 Import 引入该类所在的命名空间。

比如 [CodeSmith 使用教程(9): Progress对象](http://www.imobilebbs.com/wordpress/archives/4219)引入 Thread 类所在的 System.Threading

```
<%@ Import Namespace="System.Threading" %>
```

此外，如果在代码模板中需要引入一些源代码 （比如一些公用的代码）可以通过 include ,比如：

```
<!– #include file="CommonScript.cs" –>
```

共享代码的方法除了上面使用的 include 方法外，还可以通过设置 [CodeTemplate](http://docs.codesmithtools.com/display/Generator/The+CodeTemplate+Directive) 和 [Assembly](http://docs.codesmithtools.com/display/Generator/Referencing+Assemblies) 的Src 属性来实现等。

Tags: [CodeSmith](http://www.imobilebbs.com/wordpress/archives/tag/codesmith)
