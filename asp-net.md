# 基本语法-转义Asp.Net标记

由于 CodeSmith 的代码模板使用了和 Asp.Net 类似的语法，因此如果要使用 CodeSmith 模板生成Asp.Net 脚本时比如“<%” 就碰到了问题， <% 会被 CodeSmith 解释成 CodeSmith 自己的标记，因此需要使用转义标签来代替需要插入到 Asp.Net 代码中的标签。

具体方法是使用 <%% 来替换需要生成的 Asp.Net 中的 <%标记。

比如我们要生成如下的 Asp.Net 代码：

```
<asp:FormView ID="FormView1" DataSourceID="SqlDataSource1" DataKeyNames="ProductID" RunAt="server">
  <ItemTemplate>
    <table>
      <tr>
        <td align="right"><b>Product ID:</b></td>       
        <td><%# Eval("ProductID") %></td>
      </tr>
    </table>                 
  </ItemTemplate>                 
</asp:FormView>
```

可以在 CodeSmith 的模板中使用<%% 来替换 <%

```
<asp:FormView ID="FormView1" DataSourceID="SqlDataSource1" DataKeyNames="ProductID" RunAt="server">
  <ItemTemplate>
    <table>
      <tr>
        <td align="right"><b>Product ID:</b></td>       
        <td><%%# Eval("ProductID") %></td>
      </tr>
    </table>                 
  </ItemTemplate>                 
</asp:FormView>
```

Tags: [CodeSmith](http://www.imobilebbs.com/wordpress/archives/tag/codesmith)