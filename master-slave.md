# 使用主从代码模板

在前面的教程 CodeSmith 使用教程(3): 自动生成 Yii Framework ActiveRecord 我们使用了主，从模板来实现了从数据库为 Yii Framework 生成多个表的 ActiveRecord 类定义，中 CodeSmith 项目中通过主模板和从模板的配合可以实现复杂的代码生成过程，主模板和从模板的关系有点类似主程序和子函数的关系。使用主-从模板的基本步骤如下：

- 定义从模板，从模板可以定义属性
- 定义主模板，中主模板中如果要使用从模板，首先需要在主模板中注册从模板，主模板中也也可以定义属性，主模板和从模板中的属性可以通过定义“合并”模式构造最终模板所定义的属性集合。
- 调用主模板，设置主模板和从模板所需的属性生成所需代码

## 注册子模板

```
<%@ Register Name="Header" Template="Header.cst"
  MergeProperties="True" ExcludeProperties="IncludeMeta" %>
```

Name：子模板在主模板中的类型名称，在主要模板中可以通过该类型创建子模板的实例
Template: 子模板文件名
MergeProperties： 是否需要把子模板中定义的属性：“合并”到主模板中。缺省为 False
ExcludeProperties： 如果子模板的属性合并到主模板中时需要排除的属性列表，以逗号分隔。

## 子模板复制主模板中的属性

MergeProperties=”True” 可以把从模板中的属性合并到主模板中，如果从模板需要引用主模板的属性，比如主模板中定义了服务器地址，在多个子模板中都需要引用这个属性，此时可以通过复制父模板属性 CopyPropertiesTo 来实现：

```
// instantiate the sub-template
Header header = this.Create<Header>();

// copy all properties with matching name and type to the sub-template instance
this.CopyPropertiesTo(header);
```

CopyPropertiesTo 方法比较主模板中定义的属性和子模板中定义的属性，如果发现从模板中定义的属性和主模板中定义的属性名称类型相同（匹配）则把主模板中属性值复制到子模板中。

## 设置子模板属性

在主模板中要创建子模板的实例，可以直接通过 Create 方法

```
// instantiate the sub-template
Header header = this.Create<Header>();

// include the meta tag
header.IncludeMeta = true;
```

Create 中的 Header 为注册子模板时 Name 来定义的类型，通过 Create 创建子模板的实例后，就直接可以通过该实例的属性来访问子模板中的属性，比如上面代码中 IncludeMeta 为子模板中定义的一个属性。

## 从子模板输出结果

创建好子模板的实例，设置好子模板的属性，在主模板中就可以让子模板输出结果，有几种方法可以从子模板输出内容。

第一种是把子模板生成的结果直接插入到主模板中

```
// instantiate the sub-template.
Header header = this.Create<Header>();
// render the sub-template to the current output stream.
header.Render(this.Response);
```

第二种方法是把结果输出到单独的文件中：

```
// instantiate the sub-template.
Header header = this.Create<Header>();
// render the sub-template to a separate file.
header.RenderToFile("Somefile.txt");
```

具体的例子可以参见 [CodeSmith 使用教程(3): 自动生成 Yii Framework ActiveRecord](http://www.imobilebbs.com/wordpress/archives/4196)

Tags: [CodeSmith](http://www.imobilebbs.com/wordpress/archives/tag/codesmith)