---
title: "'使用 C# 将 HTML 转换为 Word 文档'"
author: Muzammil Khan
date: 2021-12-21T10:40:33+00:00
summary: "作为 C# 开发人员，您可以轻松地从 HTML 文件或实时 URL 生成 Word 文档。在本文中，您将学习**如何使用 C# 将 HTML 转换为 Word 文档**。"
url: /zh/2021/12/21/convert-html-to-word-document-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "将 HTML 转换为 DOCX"
  - "在 CSharp 中将 HTML 转换为 DOCX"
  - "HTML 到 Word"
  - "CSharp 中的 HTML 到 Word"

---

{{< figure align=center src="images/Convert-HTML-to-Word-in-CSharp-1.jpg" alt="使用 C# 将 HTML 转换为 Word 文档">}}
 

[HTML][2]（_超文本标记语言_）是所有浏览器都支持的网页领先文件格式。在各种情况下，我们可能需要将 HTML 文件或来自实时网页的内容转换为 Word 文档（_[DOC][3]、[DOCX、][4] [DOT][5]、[DOTM][6]、[文档][7]_)。它有助于编辑 HTML 网页的文本或应用文本格式。在本文中，我们将学习**如何使用 C# 将 HTML 转换为 Word 文档。**

本文将涵盖以下主题：

  * [用于将 HTML 转换为 DOCX 的 C# API — 免费下载][8]
  * [在 C# 中将 HTML 转换为 Word][9]
  * [在 C# 中将网页从 URL 转换为 Word][10]
  * [使用 C# 将 HTML 字符串转换为单词][11]

## 用于将 HTML 转换为 DOCX 的 C# API — 免费下载 {#CSharp-API-to-Convert-HTML-to-DOCX-Free-Download}

为了将 HTML 文件或网页转换为文字处理文件格式，我们将使用 [Aspose.Words for .NET][12] API。它是一个以编程方式创建、编辑、转换或分析 Word 文档的完整解决方案。请[下载][13] API 的 DLL 或使用 [NuGet][14] 安装它。

```
Install-Package Aspose.Words
```

## 在 C# 中将 HTML 转换为 Word {#Convert-HTML-to-Word-in-CSharp}

我们可以按照下面给出的步骤，以编程方式轻松地将 HTML 文件转换为 Word 文档：

  1. 使用 _**[Document][15]**_ 类加载 HTML 文件。
  2. 调用 [**_Document.Save(string, SaveFormat)_**][16] 方法将 HTML 文件保存为“output.docx”。

_Document.Save()_ 方法中的 _**[SaveFormat][17]**_ 枚举指定要转换 HTML 文件的格式。以下代码示例展示了**如何使用 C# 将 HTML 文件转换为 DOCX**。

```
// 此代码示例演示如何使用 C# 将 HTML 文件转换为 Word 文档。
// 使用 Document 类加载 HTML 文件
Document document = new Document(@"C:\Files\sample.html");

// 将 HTML 文件转换为 Word DOCX 格式
document.Save(@"C:\Files\output.docx", SaveFormat.Docx);
```

{{< figure align=center src="images/Convert-HTML-to-Word-in-CSharp-1024x512.jpg" alt="" caption="Convert HTML to Word in C#.">}}
 
## 在 C# 中将网页从 URL 转换为 Word {#Convert-a-Web-Page-to-Word-from-URL-in-CSharp}

我们还可以按照以下步骤将 HTML 网页直接从实时 URL 转换为 Word 文档：

  1. 首先，从指定的 URL 下载网页内容为 _System.Byte_ 数组。
  2. 接下来，使用数组对象作为参数启动 _MemoryStream_ 对象。
  3. 然后，创建 **_[HtmlLoadOptions][19]_** 类的实例。
  4. 之后，创建 **_[Document][20]_** 类的实例并使用 _MemoryStream_ 和 _HtmlLoadOptions_ 对象对其进行初始化。
  5. 最后，调用 [**_Document.Save(string, SaveFormat)_**][16] 方法将 HTML 文件保存为“output.docx”。

以下代码示例展示了**如何使用 C# 将 HTML 网页转换为 DOCX**。

```
// 此代码示例演示如何使用 C# 将 HTML 网页直接从实时 URL 保存到 Word 文档。
// 网址
string Url = "https://en.wikipedia.org/wiki/Aspose.Words";

// 定义 HTML 加载选项 
HtmlLoadOptions options = new HtmlLoadOptions();

byte[] imageData = null;

// 从 URL 下载内容为字节数组
using (var wc = new System.Net.WebClient())
    imageData = wc.DownloadData(Url);

// 将字节数组转换为流
var urlStream =  new MemoryStream(imageData);

// 创建 Document 对象的实例
Document document = new Document(urlStream, options);

// 另存为 DOCX
document.Save(@"C:\Files\output_url.docx", SaveFormat.Docx);
```

## 使用 C# 将 HTML 字符串转换为 Word {#Convert-an-HTML-String-to-Word-using-CSharp}

我们可以按照以下步骤从 HTML 字符串动态生成 Word 文档：

  1. 首先，创建 **_[Document][20]_** 类的实例。
  2. 接下来，使用 _Document_ 对象创建 **_[DocumentBuilder][21]_** 类的实例。
  3. 然后，使用 [_**DocumentBuilder.InsertHtml(string)**_][22] 方法将 HTML 插入到文档中。
  4. 最后，使用 [**_Document.Save(string, SaveFormat)_**][16] 方法保存 Word 文档。

以下代码示例展示了**如何使用 C# 将 HTML 字符串转换为 DOCX**。

```
// 此代码示例演示如何使用 C# 从 HTML 字符串生成 Word 文档。
// 创建一个新文档
Document document = new Document();

// 创建文档构建器
DocumentBuilder builder = new DocumentBuilder(document);

// 插入 HTML
builder.InsertHtml("<ul>\r\n" +
    "<li>Item1</li>\r\n" +
    "<li>Item2</li>\r\n" +
    "</ul>");

// 另存为 DOCX
document.Save(@"C:\Files\html-string-as-word.docx", SaveFormat.Docx);
```

## 获得免费许可证

请通过申请 [免费的临时许可证][23] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了**如何使用 C# 将 HTML 转换为 Word 文档**。我们还看到了**如何以编程方式将实时网页从 URL 转换为 Word 文件**。此外，您可以使用 [文档][24] 了解更多关于 Aspose.Words for .NET API 的信息。如有任何歧义，请随时在 [论坛][25] 上与我们联系。

## 也可以看看

  * [使用 C# 在 Word 文档中创建图表][26]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/12/Convert-HTML-to-Word-in-CSharp-1.jpg
 [2]: https://docs.fileformat.com/web/html/
 [3]: https://docs.fileformat.com/word-processing/doc/
 [4]: https://docs.fileformat.com/word-processing/docx/
 [5]: https://docs.fileformat.com/word-processing/dot/
 [6]: https://docs.fileformat.com/word-processing/dotm/
 [7]: https://docs.fileformat.com/word-processing/docm/
 [8]: #CSharp-API-to-Convert-HTML-to-DOCX-Free-Download
 [9]: #Convert-HTML-to-Word-in-CSharp
 [10]: #Convert-a-Web-Page-to-Word-from-URL-in-CSharp
 [11]: #Convert-an-HTML-String-to-Word-using-CSharp
 [12]: https://products.aspose.com/words/net/
 [13]: https://downloads.aspose.com/words/net
 [14]: https://www.nuget.org/packages/aspose.words
 [15]: https://apireference.aspose.com/words/net/aspose.words/document
 [16]: https://apireference.aspose.com/words/net/aspose.words.document/save/methods/3
 [17]: https://apireference.aspose.com/words/net/aspose.words/SaveFormat
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/12/Convert-HTML-to-Word-in-CSharp.jpg
 [19]: https://apireference.aspose.com/words/net/aspose.words.loading/htmlloadoptions
 [20]: https://apireference.aspose.com/words/net/aspose.words/Document
 [21]: https://apireference.aspose.com/words/net/aspose.words/documentbuilder
 [22]: https://apireference.aspose.com/words/net/aspose.words/documentbuilder/methods/inserthtml
 [23]: https://purchase.conholdate.com/temporary-license
 [24]: https://docs.aspose.com/words/net/
 [25]: https://forum.aspose.com/c/words/8
 [26]: https://blog.conholdate.com/2021/10/31/create-charts-in-word-documents-using-csharp/
