---
title: "'使用 C# .NET API 将 HTML 转换为 PDF'"
author: Nayyer Shahbaz
date: 2021-04-08T17:54:18+00:00
url: /zh/2021/04/08/convert-html-to-pdf-using-csharp-net-api/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "用于 PDF 到 HTML 的 CSharp .NET API"
  - "CSharp API 将 HTML 转换为 PDF"
  - "将 HTML 转换为 PDF"
  - "使用 CSharp 将 PDF 转换为 HTML"
  - "HTML 到 PDF 转换 API"
---


{{< figure align=center src="images/icon-1.png" alt="PDF到HTML的转换">}}
 

[PDF][2]（_Portable Document Format_）是广泛使用的跨平台数据和信息共享的文档格式之一。它的一项独特功能包括，根据 Adobe 规范使用应用程序在任何平台上查看时，文档的保真度保持不变。此外，[HTML][3]（_超文本标记语言_）也是网页开发的主要文件格式，大多数网络浏览器都支持这种格式。然而，PDF 被广泛接受，因为它可以在任何设备上轻松查看而不会丢失文档格式。因此，在本文中，我们将讨论如何使用 .NET API 将 [HTML][3] 文件转换为 [PDF][2] 格式的步骤。

  * [C# API 将 HTML 转换为 PDF][4]
  * [在 C# 中将 HTML 转换为 PDF][5]
  * [在转换期间嵌入字体][6]
  * [将网页转换为 PDF][7]
  * [在单个页面上呈现完整的 HTML][8]

## C# API 将 HTML 转换为 PDF {#CSharp-API-to-Convert-HTML-to-PDF}

为了执行转换操作，首先，我们需要在系统上安装[Aspose.PDF for .NET][9]。该 API 在 [NuGet][10] 库中可用。请在 Package Manager Console 上运行以下命令进行安装：

```
Install-Package Aspose.Pdf
```

安装完成后，Aspose.PDF for .NET 将出现在解决方案资源管理器的 Packages 文件夹下。

## 在 C# 中将 HTML 转换为 PDF {#Convert-HTML-to-PDF-in-CSharp}

下面给出了如何使用 C# 将 HTML 转换为 PDF 的步骤

1. 创建 [License](https://apireference.aspose.com/pdf/net/aspose.pdf/license) 类的实例，以消除 PDF 文件生成过程中的任何限制。
2. 创建 [HtmlLoadOptions](https://apireference.aspose.com/pdf/net/aspose.pdf/htmlloadoptions) 类的对象，同时将输入的 HTML 基本 url 作为参数传递给 [HtmlLoadOptions(...)](https:// /apireference.aspose.com/pdf/net/aspose.pdf/htmlloadoptions) 构造函数。
3. 初始化 [Document](https://apireference.aspose.com/pdf/net/aspose.pdf/document) 类的对象并通过 [HtmlLoadOptions](https://apireference.aspose.com/pdf/net/aspose. pdf/htmlloadoptions) 对象作为其构造函数的参数。
4. 调用 Document 对象的 [Save(...)](https://apireference.aspose.com/pdf/net/aspose.pdf.document/save/methods/4) 方法并以 PDF 格式呈现输出。

```
// 创建一个对象来启动许可
Aspose.Pdf.License license = new Aspose.Pdf.License();

// 提供许可证文件的路径
license.SetLicense("/Downloads/Conholdate.Total.NET.lic");

// 创建 HtmlLoadOptions 类的实例
Aspose.Pdf.HtmlLoadOptions htmlLoadOptions = new Aspose.Pdf.HtmlLoadOptions("User/Documents/");

// 创建 Document 对象并提供输入 HTML 文件路径
Aspose.Pdf.Document document = new Aspose.Pdf.Document("/Documents/input.html", htmlLoadOptions);

// 将生成的 HTML 保存为 PDF 格式
document.Save("/Documents/Converted.pdf");
```

## 在转换期间嵌入字体 {#Embed-fonts-during-conversion}

大多数 HTML 页面经常使用字体（例如本地文件夹中的字体、Google 字体等），并且为了保留页面的布局，在渲染过程中应嵌入相同的字体。因此，为了控制结果文档中字体的嵌入，我们需要使用 [IsEmbedFonts][11] 属性。

```
// 在转换期间嵌入字体
HtmlLoadOptions options = new HtmlLoadOptions {IsEmbedFonts = true};
```

Aspose.PDF 中的测量单位是点。而且，我们知道 A3 的尺寸为 297 × 420 毫米或 11.69 × 16.54 英寸。因此，尺寸四舍五入为 842 × 1190 点。在以下代码片段中，我们将生成文档的页面大小调整为 A3，将页面方向调整为横向。

```
// 将页面大小设置为 A3，页面方向设置为横向
HtmlLoadOptions options = new HtmlLoadOptions(url)
{
  PageInfo = {Width = 842, Height = 1191, IsLandscape = true}
};
```

## 将网页转换为 PDF {#Convert-Web-page-to-PDF}

除了 HTML 文件的转换，我们可能还需要将网页直接转换为 PDF 格式。所以为了完成这个需求，首先我们将使用 HttpClient 实例获取远程网页内容，创建一个 Stream 对象，然后将 Stream 实例传递给 Document 对象。我们需要 Stream 中的内容的原因是 Document 实例只接受文件或 steam 对象。

以下部分介绍如何使用 C# 将网页转换为 PDF 的步骤

  1. 使用 [HttpClient][12] 对象读取页面内容。
  2. 实例化 [HtmlLoadOptions][13] 对象并设置基本 URL。
  3. 初始化一个 [Document][14] 对象并将流对象和 [HtmlLoadOptions][13] 实例作为参数传递。
  4. 从 Document 类调用 [Save(String)][15] 方法以生成输出。

```
public static void ConvertHTMLtoPDFAdvanced_WebPage()
{
    const string url = "https://en.wikipedia.org/wiki/Aspose_API";
    
    // Set page size A3 and Landscape orientation; 
    HtmlLoadOptions options = new HtmlLoadOptions(url)
    {
        // Set the page dimensions
        PageInfo = {Width = 842, Height = 1191, IsLandscape = true}
    };
    
    // Create an instance of Document object
    Document pdfDocument= new Document(GetContentFromUrlAsStream(url), options);
    
    // Save the resultant
    pdfDocument.Save(_dataDir + "html_test.PDF");
}

private static Stream GetContentFromUrlAsStream(string url, ICredentials credentials = null)
{
    
    using (var handler = new HttpClientHandler { Credentials = credentials })
    using (var httpClient = new HttpClient(handler))
    {
        // fetch and return results in stream instance
        return httpClient.GetStreamAsync(url).GetAwaiter().GetResult();
    }
}
```

## 在单个页面上呈现完整的 HTML {#Render-complete-HTML-on-a-single-page}

在 HTML 到 PDF 的转换过程中，结果文件的长度取决于输入 HTML 文档的内容长度。因此，如果输入 HTML 由多个页面组成，那么生成的文件也将跨越多个页面。但是，我们可以将输出限制为单个 PDF 页面。为了完成这个要求，可以使用 HtmlLoadOptions 类的 [IsRenderToSinglePage][16] 属性。

下面给出了使用 C# 在单个 PDF 页面上呈现完整 HTML 内容的代码片段。

```
// 如需完整的示例和数据文件，请访问 https://github.com/aspose-pdf/Aspose.PDF-for-.NET
// 初始化 HtmlLoadOptions 对象
HtmlLoadOptions options = new HtmlLoadOptions();

// 将渲染设置为单页属性
options.IsRenderToSinglePage = true;

// 加载文档源 HTML 内容
Document pdfDocument= new Document("/Documents/HTMLToPDF.html", options);

// 保存生成的 PDF 文件
pdfDocument.Save("/Documents/MyRenderContentToSamePage.pdf");
```

## 获得免费许可证

您可以请求 [免费的临时许可证](https://purchase.aspose.com/temporary-license) 试用 API，没有任何评估限制。

## 结论 {#Conclusion}

在本文中，我们了解了使用 .NET API 将 HTML 文件转换为 PDF 格式的方法。如果您有兴趣了解 Aspose.PDF for .NET 提供的其他令人兴奋的功能，请访问 [主要功能][17] 页面。可以在 [GitHub 存储库][18] 上找到完整的示例集。

## 小建议

我们还开发了免费的在线应用程序来快速检查我们的 API 提供的功能。因此，您可以查看 [Aspose.PDF Conversion App][19] 将 HTML 文件转换为 PDF 格式。此外，您还可以使用各种其他文件格式并完成您的转换要求。

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/icon-1.png
 [2]: https://docs.fileformat.com/pdf/
 [3]: https://docs.fileformat.com/web/html/
 [4]: #CSharp-API-to-Convert-HTML-to-PDF
 [5]: #Convert-HTML-to-PDF-in-CSharp
 [6]: #Embed-fonts-during-conversion
 [7]: #Convert-Web-page-to-PDF
 [8]: #Render-complete-HTML-on-a-single-page
 [9]: https://products.aspose.com/pdf/net
 [10]: https://www.nuget.org/packages/Aspose.PDF/
 [11]: https://apireference.aspose.com/pdf/net/aspose.pdf/htmlloadoptions/properties/isembedfonts
 [12]: https://docs.microsoft.com/en-us/dotnet/api/system.net.http.httpclient?view=net-5.0
 [13]: https://apireference.aspose.com/pdf/net/aspose.pdf/htmlloadoptions
 [14]: https://apireference.aspose.com/pdf/net/aspose.pdf/document
 [15]: https://apireference.aspose.com/pdf/net/aspose.pdf.document/save/methods/4
 [16]: https://apireference.aspose.com/pdf/net/aspose.pdf/htmlloadoptions/properties/isrendertosinglepage
 [17]: https://docs.aspose.com/pdf/net/key-features/
 [18]: https://github.com/aspose-pdf/Aspose.Pdf-for-.NET
 [19]: https://products.aspose.app/pdf/conversion








