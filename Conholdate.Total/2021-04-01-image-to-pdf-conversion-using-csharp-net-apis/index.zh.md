---
title: "'使用 C# .NET API 将图像转换为 PDF'"
author: Nayyer Shahbaz
date: 2021-04-01T17:42:08+00:00
url: /zh/2021/04/01/image-to-pdf-conversion-using-csharp-net-apis/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - ".NET API 用于 JPEG 到 PDF"
  - "将图像转换为 PDF"
  - "图像到 PDF 转换"
  - "JPEG 到 PDF 转换 API"
  - "PNG到PDF转换API"

---


{{< figure align=center src="images/JPEG-PDF.jpg" alt="图像到 PDF 转换">}}
 

“**一张图片胜过千言万语**”。这些想法可以通过一个有效的机制通过一个静止的**图像**来传达，而不是仅仅通过口头描述。因此，图像在日常生活中被广泛使用。包括[JPEG][2]、[PNG][3]、[BMP][4]、[GIF][5]、[TIFF][6]等多种图像格式用于信息共享。但是，如果我们偶然发现需要共享大量图像，我们要么需要将它们归档到一个包中，要么制作一个小册子，其格式可以在接收端轻松查看。因此，我们的选择是便携式文档格式 ([PDF][7])，因为它可以保持文档的保真度，而与用于查看文件的应用软件、硬件以及操作系统无关。因此，在本文中，我们将讨论使用 [Conholdate.Total for .NET][8] API 的图像到 PDF 转换功能。

<blockquote class="wp-block-quote">
  
但是，在我们继续之前，让我们讨论一些要点，突出 .NET 的 Conholdate.Total 和 .NET 的 Aspose.Total 之间的区别。
  
</blockquote>

[Aspose.Total for .NET][9] 是一组专门为创建、操作和转换主要文件格式而开发的编程 API。它包括 Word、Excel、PDF、PowerPoint、Outlook、Diagram、MS Project、HTML 以及标准桌面、控制台、ASP.NET 和 VB.NET 应用程序中的其他 100 多种文件格式。

尽管如此，[Conholdate.Total for .NET][8] 还包括 Aspose.Total for .NET。但是，它还包括 [GroupDocs.Total for .NET][10]。它提供了额外的功能来查看、转换、注释、比较、签名、组合、编辑、搜索和解析最常用的文档格式。因此，在这个单一包中，您可以加载文件、查看文件、操作文件并以其他支持的格式呈现输出，即[加载 MS Word 文件并保存为 JPEG 格式][11]。

因此，在本文中，我们将讨论使用 C# .NET 加载 [光栅图像文件][12] 并以 [PDF][7] 格式保存输出的功能。

  * [在 C# 中将图像转换为 PDF][13]
  * [获得免费许可证][14]

## 在 C# 中将图像转换为 PDF {#Convert-Image-to-PDF-in-Csharp}

API 是领先的编程解决方案，提供处理 MS Word（[DOC][15]、[DOCX][16]、[RTF][17]、[DOT][18]、[DOTX][19] 的能力, [DOTM][20], [DOCM][21]), **OpenOffice:** [ODT][22], [OTT][23] 文件。 API 使开发人员能够在不使用 Microsoft Word 的情况下修改、生成、渲染、转换和打印文档。它支持在 [DOC][15]、[RTF][17]、[HTML][24]、[OpenDocument][22]、[PDF][7]、[XPS][25] 中呈现输出的功能、[EPUB][26] 等等。所以我们可以使用这个 API 进行图像到 PDF 的转换。

为了使用 API，您可以 [下载][27] .dll 或打开 [NuGet][28] 包管理器，搜索 **Aspose.Words** 并安装。请在 Package Manager Console 上运行以下命令进行安装。

```
Install-Package Aspose.Words -Version 21.3.0  
```

请按照以下步骤执行转换操作

**C#.NET**

  * 创建 [Document][29] 类的实例。
  * 创建 [DocumentBuilder][30] 的实例并将 Document 对象作为参数传递。
  * 调用 DocumentBuilder 类的 [InsertImage(…)][31] 方法并将源图像路径作为参数传递。
  * 调用 [Save][32](..) 方法并提供结果文件名作为参数。

```
// 如需完整的示例和数据文件，请访问 https://github.com/aspose-words/Aspose.Words-for-.NET
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.InsertImage(dataDir + "Watermark.png");
dataDir = dataDir + "DocumentBuilderInsertInlineImage_out.doc";
doc.Save(dataDir);
```

## 获得免费许可证 {#Get-a-Free-License}

为了不受任何限制地使用 API，请考虑申请 [免费临时许可证][33]。

## 结论

在本文中，我们了解了 [Conholdate.Total for .NET][8] 包将光栅图像转换为 PDF 格式的功能。

## **相关文章**

您可以考虑访问以下链接以获取详细信息

  * [使用 C# 将 PDF 文件转换为 SVG][34]
  * [使用 C# 将 PDF 页面转换为 PNG 图像][35]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/03/JPEG-PDF.jpg
 [2]: https://docs.fileformat.com/image/jpeg/
 [3]: https://docs.fileformat.com/image/png/
 [4]: https://docs.fileformat.com/image/bmp/
 [5]: https://docs.fileformat.com/image/gif/
 [6]: https://docs.fileformat.com/image/tiff/
 [7]: https://docs.fileformat.com/pdf/
 [8]: https://products.conholdate.com/total/net
 [9]: https://products.aspose.com/total/net
 [10]: https://products.groupdocs.com/total/net
 [11]: https://docs.aspose.com/words/net/converting-to-fixed-page-format/
 [12]: https://docs.fileformat.com/image/
 [13]: #Convert-Image-to-PDF-in-Csharp
 [14]: #Get-a-Free-License
 [15]: https://docs.fileformat.com/word-processing/doc/
 [16]: https://docs.fileformat.com/word-processing/docx/
 [17]: https://docs.fileformat.com/word-processing/rtf/
 [18]: https://docs.fileformat.com/word-processing/dot/
 [19]: https://docs.fileformat.com/word-processing/dotx/
 [20]: https://docs.fileformat.com/word-processing/dotm/
 [21]: https://docs.fileformat.com/word-processing/docm/
 [22]: https://docs.fileformat.com/word-processing/odt/
 [23]: https://docs.fileformat.com/word-processing/ott/
 [24]: https://docs.fileformat.com/web/html/
 [25]: https://docs.fileformat.com/page-description-language/xps/
 [26]: https://docs.fileformat.com/ebook/epub/
 [27]: https://downloads.aspose.com/words/net
 [28]: https://www.nuget.org/packages/Aspose.Words/
 [29]: https://apireference.aspose.com/words/net/aspose.words/document
 [30]: https://apireference.aspose.com/words/net/aspose.words/documentbuilder
 [31]: https://apireference.aspose.com/words/net/aspose.words.documentbuilder/insertimage/methods/9
 [32]: https://apireference.aspose.com/words/net/aspose.words.document/save/methods/2
 [33]: https://purchase.aspose.com/temporary-license
 [34]: https://blog.aspose.com/2021/02/04/convert-pdf-files-to-svg-using-csharp/
 [35]: https://blog.aspose.com/2020/11/25/pdf-to-png-using-csharp/








