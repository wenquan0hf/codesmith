# CodeTemplateInfo 对象

通过 CodeTemplateInfo 对象可以获取代码模板文件本身的一些信息，比如文件名，源语言，编码方法，其支持的属性有：

| 属性名               | 描述                                                        |
|:------------------- |:------------------------------------------------------------|
| CodeBehind          | 该模板的 Code-behind 的文件名或者模板不使用 CodeBehind 时为空字符串  |
| ContentHashCode     | 返回代码模板的一个 Hash 值                                      |
| DateCreated         | 返回模板创建的时间                                            |
|DateModified         |	返回模板修改的时间                                            |
|Description          |	返回模板说明                                                 |
|DirectoryName        |	返回模板所处的目录                                            |
|FileName             |	返回模板的文件名                                              |
|FullPath             |	返回模板的完整路径                                            |
|Language             |	返回模板的源语言类型                                          |
|TargetLanguage       |	返回模板生成的目标语言类型                                     |

本例通过 CodeTempalte 对象的 CodeTemplateInfo 属性对象中输出文件中显示上面个各个属性值：

```
<%@ CodeTemplate Language="C#" TargetLanguage="Text"
Description="Demonstrates CodeTemplateInfo." %>
<% DumpInfo(); %>
<script runat="template">
public void DumpInfo()
{
    Response.WriteLine("Template: {0}", CodeTemplateInfo.FileName);
    Response.WriteLine("Created: {0}", CodeTemplateInfo.DateCreated);
    Response.WriteLine("Description: {0}", CodeTemplateInfo.Description);
    Response.WriteLine("Location: {0}", CodeTemplateInfo.FullPath);
    Response.WriteLine("Language: {0}", CodeTemplateInfo.Language);
    Response.WriteLine("Target Language: {0}", CodeTemplateInfo.TargetLanguage);
}
</script>
```

显示结果如下：

```
Template: CodeTemplateInfo.cst
Created: 6/01/2013 12:49:57 PM
Description: Demonstrates CodeTemplateInfo.
Location: D:\tmp\CodeTemplateInfoDemo\CodeTemplateInfoDemo\CodeTemplateInfo.cst
Language: C#
Target Language: Text
```

本例[下载](http://www.imobilebbs.com/download/codesmith/CodeTemplateInfoDemo.zip)

Tags: [CodeSmith](http://www.imobilebbs.com/wordpress/archives/tag/codesmith)

