---
title: "'使用 C# 进行网页抓取'"
author: Muzammil Khan
date: 2022-03-10T06:43:17+00:00
summary: "Web Scraping 是一种用于从网站中提取数据的技术。在本文中，您将学习**如何使用 C# 通过 HTML 解析执行 Web 抓取**。"
url: /zh/2022/03/10/web-scraping-using-csharp/

categories:
  - "Conholdate.Total 产品系列"
tags:
  - "C# 网页抓取 API"
  - "使用 C# 进行网络爬虫"
  - "从网站中提取数据"
  - "使用 C# 从网站中提取数据"
---

{{< figure align=center src="images/web-scraping-using-csharp.jpg" alt="使用 C# 进行网页抓取">}}
 
Web Scraping 是一种用于从网站中提取数据的技术。它有助于自动化从网站和 [HTML][16] 文件中提取数据的过程。作为 C# 开发人员，我们可以轻松地从网页中检查、捕获和提取数据，例如图像、视频、音频等。在本文中，我们将学习**如何使用 C# 通过 HTML 解析执行网页抓取**。

本文将涵盖以下主题：

  * [C# 网页抓取 API][1]
  * [使用 C# 读取和提取 HTML][2]
  * [使用 C# 检查文档元素][3]
  * [在 C# 中使用过滤器查找特定元素][4]
  * [使用 C# 从 HTML 查询数据][5]
  * [在 C# 中使用 CSS 选择器进行提取][6]

## C# 网页抓取 API {#CSharp-Web-Scraping-API}

对于 HTML 文件或 URL 的网络抓取，我们将使用 [Aspose.HTML for .NET][7] API。它是一种高级 HTML 处理 API，无需任何外部软件即可生成、修改、提取数据、转换和渲染 HTML 文档。请[下载][8] API 的 DLL 或使用 [NuGet][9] 安装它。

```
PM> Install-Package Aspose.Html
```

## 使用 C# 读取和提取 HTML {#Read-and-Extract-HTML-using-CSharp}

我们可以按照以下步骤从任何 HTML 文档中读取和提取 HTML：

  1. 使用 _**[HTMLDocument][10]**_ 类加载 HTML 文档。
  2. 将文件的内部 HTML 显示到控制台。

以下代码示例展示了**如何使用 C# 读取和提取 HTML 内容**。

```
// 此代码示例演示如何显示 HTML 文档的内容
// 加载 HTML 文档
var document = new HTMLDocument(@"D:\Files\html\input.html");

// 显示文档的内部 HTML
Console.WriteLine(document.Body.InnerHTML);
```

{{< figure align=center src="images/Read-and-Extract-HTML-using-CSharp.jpg" alt="使用 C# 读取和提取 HTML。" caption="使用 C# 读取和提取 HTML。">}}

同样，我们可以从实时网站中读取和提取 HTML，如下所示：

```
// 此代码示例演示如何显示来自实时网站 URL 的内容。
// 初始化网址
Url url = new Url("https://en.wikipedia.org/wiki/HTML");

// 使用 Url 实例加载 HTML 文件
HTMLDocument document = new HTMLDocument(url);

// 向控制台显示文件的内部 HTML
Console.WriteLine(document.Body.InnerHTML);
```
 

## 使用 C# 检查文档元素 {#Inspect-Document-Elements-using-CSharp}

我们可以按照以下步骤检查文档及其元素：

  1. 使用 _**[HTMLDocument][10]**_ 类加载 HTML 文档。
  2. 获取文档的 HTML 元素。
  3. 获取 HTML 元素的第一个/最后一个元素。
  4. 显示元素详细信息，例如 TagName、TextContent。

以下代码示例展示了**如何使用 C# 检查文档元素**。

```
// 此代码示例演示如何检查 HTML 元素。
// 从文件加载文档
string documentPath = @"D:\Files\html\input.html";
HTMLDocument document = new HTMLDocument(documentPath);

// 获取文档的html元素
var element = document.DocumentElement;
Console.WriteLine(element.TagName); // HTML

// 获取html元素的最后一个元素
element = element.LastElementChild;
Console.WriteLine(element.TagName); // BODY

// 获取body元素的第一个元素
element = element.FirstElementChild;
Console.WriteLine(element.TagName); // H1
Console.WriteLine(element.TextContent); // Header 1
```


## 在 C# 中使用过滤器查找特定元素 {#Find-Specific-Element-using-Filters-in-CSharp}

我们可以使用自定义过滤器来查找特定元素，例如获取所有图像、链接等。为此，API 提供了 TreeWalker 接口。它允许使用由 whatToShow 标志和过滤器（如果有）定义的文档视图来导航文档树或子树。我们可以按照以下步骤使用过滤器找到特定元素：

  1. 使用 NodeFilter 类定义过滤器并覆盖 AcceptNode() 方法。
  2. 使用 _**[HTMLDocument][10]**_ 类加载 HTML 文档。
  3. 调用 CreateTreeWalker() 方法。它以根节点、要显示的内容和 NodeFilter 作为参数。

以下代码示例展示了**如何使用 C# 读取和提取 HTML 内容**。

```
// 此代码示例演示如何使用过滤器查询数据。
// 加载 HTML 文档
HTMLDocument document = new HTMLDocument(@"D:\Files\html\input.html");

// 要启动 HTML 导航，我们需要创建一个 TreeWalker 实例。
// 指定参数表示从文档根开始走，
// 迭代所有节点并使用我们自定义的过滤器实现
using (var iterator = document.CreateTreeWalker(document, Dom.Traversal.Filters.NodeFilter.SHOW_ALL, new OnlyImageFilter()))
{
    while (iterator.NextNode() != null)
    {
        // Since we are using our own filter, the current node will always be an instance of the HTMLImageElement.
        // So, we don't need the additional validations here.
        var image = (HTMLImageElement)iterator.CurrentNode;

        System.Console.WriteLine(image.Src);
        // output: image1.png
        // output: image2.png
    }
}
```

```
// 此代码示例演示如何定义节点过滤器。
class OnlyImageFilter : Aspose.Html.Dom.Traversal.Filters.NodeFilter
{
    public override short AcceptNode(Aspose.Html.Dom.Node n)
    {
        // The current filter skips all elements, except IMG elements.
        return string.Equals("img", n.LocalName)
            ? FILTER_ACCEPT
            : FILTER_SKIP;
    }
}
```

## 使用 C# 从 HTML 查询数据 {#Query-Data-from-HTML-using-CSharp}

我们还可以按照以下步骤使用 XPath Query 从 HTML 文档中查询数据：

  1. 使用 _**[HTMLDocument][10]**_ 类加载 HTML 文档。
  2. 调用 Evaluate() 方法。它将 XPath 表达式字符串、文档和类型作为参数。
  3. 最后，遍历生成的节点并显示文本

以下代码示例展示了**如何使用 C# 使用 XPath 查询来查询数据**。

```
// 此代码示例演示如何使用 XPath 查询来查询数据。
// 准备 HTML 代码
var code = @"
    <div class='happy'>
        <div>
            <span>Hello!</span>
        </div>
    </div>
    <p class='happy'>
        <span>World</span>
    </p>
";

// 根据准备好的代码初始化一个文档
HTMLDocument document = new HTMLDocument(code, ".");

// 这里我们评估选择所有子 SPAN 元素的 XPath 表达式 
// 来自“class”属性等于“happy”的元素：
var result = document.Evaluate("//*[@class='happy']//span",
    document,
    null,
    Aspose.Html.Dom.XPath.XPathResultType.Any,
    null);

// 迭代结果节点
for (Aspose.Html.Dom.Node node; (node = result.IterateNext()) != null;)
{
    System.Console.WriteLine(node.TextContent);
    // output: Hello
    // output: World!
}
```
 
## 在 C# 中使用 CSS 选择器进行提取 {#Extract-using-CSS-Selector-in-CSharp}

我们也可以使用 CSS 选择器来提取 HTML 内容。为此，API 提供了 [QuerySelectorAll()][11] 方法，该方法允许在 HTML 文档中导航并搜索所需的元素。它将查询选择器作为参数并返回所有元素的匹配 NodeList。我们可以按照以下步骤使用 CSS 选择器进行查询：

  1. 使用 _**[HTMLDocument][10]**_ 类加载 HTML 文档。
  2. 调用 QuerySelectorAll() 方法。它将查询选择器作为参数。
  3. 最后，遍历生成的元素列表。

以下代码示例展示了**如何使用 C# 中的 CSS 选择器提取 HTML 内容**。

```
// 根据准备好的代码初始化一个文档
HTMLDocument document = new HTMLDocument(@"D:\Files\html\input.html");

// 这里我们创建了一个 CSS 选择器来提取所有 div 元素
var elements = document.QuerySelectorAll("div");

// 迭代结果的元素列表
foreach (Aspose.Html.HTMLElement element in elements)
{
    System.Console.WriteLine(element.InnerHTML);
}
```
 
## 获得免费许可证

请通过请求 [免费的临时许可证][12] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了如何：
  * 使用 C# 读取和提取 HTML 文档的内容；
  * 检查文档元素并从 HTML 中查找特定元素；
  * 使用 CSS 选择器查询特定数据并提取数据；

此外，您可以使用 [文档][13] 了解更多关于 Aspose.HTML for .NET API 的信息。如有任何歧义，请随时在 [论坛][14] 上与我们联系。

## 也可以看看

  * [C# 使用 .NET 将 HTML 转换为 JPG、PNG、BMP 和 GIF 图像][15]

  [1]: #CSharp-Web-Scraping-API
  [2]: #Read-and-Extract-HTML-using-CSharp
  [3]: #Inspect-Document-Elements-using-CSharp
  [4]: #Find-Specific-Element-using-Filters-in-CSharp
  [5]: #Query-Data-from-HTML-using-CSharp
  [6]: #Extract-using-CSS-Selector-in-CSharp
  [7]: https://products.aspose.com/html/net/
  [8]: https://downloads.aspose.com/html/net/
  [9]: https://www.nuget.org/packages/aspose.html
  [10]: https://apireference.aspose.com/html/net/aspose.html/htmldocument
  [11]: https://apireference.aspose.com/html/net/aspose.html.dom/document/methods/queryselectorall
  [12]: https://purchase.conholdate.com/temporary-license
  [13]: https://docs.aspose.com/html/net/
  [14]: https://forum.aspose.com/c/html/
  [15]: https://blog.aspose.com/2020/05/30/html-to-jpg-png-bmp-and-gif-images-csharp/
  [16]: https://docs.fileformat.com/web/html/
