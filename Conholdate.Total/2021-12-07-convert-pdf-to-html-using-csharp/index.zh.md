---
title: "'使用 C# 将 PDF 转换为 HTML'"
author: Muzammil Khan
date: 2021-12-07T13:24:11+00:00
summary: "作为 C# 开发人员，您可以轻松地将 PDF 文档转换为 HTML 网页。在本文中，您将学习**如何使用 C# 将 PDF 文档转换为 HTML 网页**。"
url: /zh/2021/12/07/convert-pdf-to-html-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "用于 PDF 到 HTML 的 CSharp .NET API"
  - "将 PDF 转换为 HTML"
  - "使用 CSharp 将 PDF 转换为 HTML"
  - "PDF 转 HTML"

---


{{< figure align=center src="images/convert-pdf-to-html-using-csharp.jpg" alt="使用 C# 将 PDF 转换为 HTML">}}
 

[PDF][2] 是最流行的共享和打印文档格式。在某些情况下，我们可能需要将 PDF 文档转换为 [HTML][3] 网页。这种转换有助于共享 PDF 文档的内容，以便相关利益相关者可以在任何浏览器中轻松查看它们。在本文中，我们将学习**如何使用 C# 将 PDF 文档转换为 HTML 网页**。

本文将涵盖以下主题：

  * [用于将 PDF 转换为 HTML 的 C# API — 免费下载][4]
  * [使用 C# 将 PDF 转换为 HTML][5]
  * [将页面范围从 PDF 转换为 HTML][6]
  * [将 PDF 的特定页面转换为 HTML][7]
  * [C# 中带水印的 PDF 到 HTML 转换][8]

## 用于将 PDF 转换为 HTML 的 C# API — 免费下载 {#CSharp-API-to-Convert-PDF-to-HTML-Free-Download}

我们将使用 [GroupDocs.Conversion for .NET][9] API 将 PDF 转换为 HTML。它为最终用户提供快速、高效、可靠的文件转换解决方案。请[下载][10] API 的 DLL 或使用 [NuGet][11] 安装它。

```
Install-Package GroupDocs.Conversion
```

## 使用 C# 将 PDF 转换为 HTML {#PDF-to-HTML-Conversion-using-CSharp}

我们可以通过以下简单步骤以编程方式轻松地将 PDF 文档转换为 HTML 网页：

  1. 首先，使用 **_[Converter][12]_** 类以输入文件路径作为参数加载 PDF 文档。它是控制文档转换过程的主要类。
  2. 接下来，创建 [**_MarkupConvertOptions_**][13] 类的实例。它提供了各种转换为标记文件类型的选项。
  3. 然后，可选地设置各种转换选项，例如_FixedLayout_、_FixedLayoutShowBorders_等。
  4. 最后调用_**[Converter.Convert()][14]**_方法保存转换后的HTML文件。此方法采用输出文件的路径并将选项转换为参数。

以下代码示例展示了**如何使用 C#** 将**PDF 文档** 转换为 HTML 网页。

```
// 加载源 PDF 文件
Converter converter = new Converter(@"C:\Files\Conversion\sample.pdf");

// 设置 HTML 格式的转换选项
var options = new MarkupConvertOptions();
options.FixedLayout = true;
options.FixedLayoutShowBorders = false;

// 转换为 HTML 格式
converter.Convert(@"C:\Files\Conversion\converted.html", options);
```

{{< figure align=center src="images/Convert-PDF-to-HTML-in-CSharp-1024x512.jpg" alt="在 C# 中将 PDF 转换为 HTML。" caption="在 C# 中将 PDF 转换为 HTML。">}}
 

## 将页面范围从 PDF 转换为 HTML {#Convert-Range-of-Pages-from-PDF-to-HTML-in-CSharp}

我们可以按照以下步骤以编程方式将 PDF 文档的一系列页面转换为 HTML：

  1. 首先，使用 **_[Converter][12]_** 类以输入文件路径作为参数加载 PDF 文档。
  2. 接下来，创建 [**_MarkupConvertOptions_**][13] 类的实例。
  3. 然后，设置页码开始转换
  4. 之后，设置页数以转换总页数
  5. 最后，调用 _**[Converter.Convert()][14]**_ 方法，使用输出文件路径和转换选项保存转换后的 HTML 文件。

以下代码示例展示了**如何将**一系列页面从 PDF 文档** 转换为 C# 中的 HTML 文件。**

```
// 加载源 PDF 文件
Converter converter = new Converter(@"C:\Files\Conversion\sample.pdf");

// 设置 HTML 格式的转换选项
MarkupConvertOptions options = new MarkupConvertOptions();
options.PageNumber = 2; // Start page number
options.PagesCount = 3; // Total pages to convert

// 转换为 HTML 格式
converter.Convert(@"C:\Files\Conversion\converted_pages_range.pdf", options);
```

## 将 PDF 的特定页面转换为 HTML {#Convert-Specific-Pages-of-PDF-to-HTML-in-CSharp}

我们可以按照以下步骤将 PDF 文档的特定页面转换为 HTML：

  1. 首先，使用 **_[Converter][12]_** 类以输入文件路径作为参数加载 PDF 文档。
  2. 接下来，创建 [**_MarkupConvertOptions_**][13] 类的实例。
  3. 然后，在逗号分隔的列表中提供要转换的特定页码。
  4. 最后，调用 _**[Converter.Convert()][14]**_ 方法，使用输出文件路径和转换选项保存转换后的 HTML 文件。

以下代码示例展示了**如何将** PDF 文档的特定页面** 转换为 C# 中的 HTML 文件。**

```
// 加载源 PDF 文件
Converter converter = new Converter(@"C:\Files\Conversion\sample.pdf");

// 设置 HTML 格式的转换选项
MarkupConvertOptions options = new MarkupConvertOptions();
options.Pages = new List<int> { 1, 3 }; // List of page numbers to convert

// 转换为 HTML 格式
converter.Convert(@"C:\Files\Conversion\converted_specific_pages.pdf", options);
```

## C# 中带水印的 PDF 到 HTML 转换 {#PDF-to-HTML-Conversion-with-Watermark-in-CSharp}

我们可以按照以下步骤将 PDF 文档转换为 HTML 网页，并以编程方式为转换后的 HTML 文件添加水印：

  1. 首先，使用 **_[Converter][12]_** 类以输入文件路径作为参数加载 PDF 文档。
  2. 接下来，创建 _**[WatermarkOptions][16]**_ 类的实例。
  3. 然后，设置各种选项，例如_Text_、_Color_、_Width_、_Height_、_Font_等。
  4. 接下来，创建 [**_MarkupConvertOptions_**][13] 类的实例。
  5. 之后，将 _**WatermarkOptions**_ 分配给 **_MarkupConvertOptions_**。
  6. 最后，调用 _**[Converter.Convert()][14]**_ 方法，使用输出文件路径和转换选项保存转换后的 HTML 文件。

以下代码示例展示了**如何将 PDF 文档转换为带水印的 HTML 文档**。

```
// 加载源 PDF 文件
Converter converter = new Converter(@"C:\Files\Conversion\sample.pdf");

// 定义文本水印
WatermarkOptions watermark = new WatermarkTextOptions("This is a sample watermark!")
{
    Color = Color.Red,
    Width = 500,
    Height = 100,
    Top = 0,
    Left = 300,
    Background = true
};

// 设置 HTML 格式的转换选项
MarkupConvertOptions options = new MarkupConvertOptions();
options.Watermark = watermark;

// 转换为 HTML 格式
converter.Convert(@"C:\Files\Conversion\converted_with_watermark.html", options);
```

{{< figure align=center src="images/PDF-to-HTML-Conversion-with-Watermark-in-CSharp-1024x880.jpg" alt="C# 中带水印的 PDF 到 HTML 转换。" caption="C# 中带水印的 PDF 到 HTML 转换。">}}
 

## 获得免费许可证

请通过申请 [免费的临时许可证][18] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了**如何在 C# 中将 PDF 文档转换为 HTML 网页**。我们还看到了**如何以编程方式将 PDF 的特定页面转换为 HTML 并为转换后的文件添加水印**。此外，您可以使用 [documentation][19] 了解有关 .NET API 的 GroupDocs.Conversion 的更多信息。如有任何歧义，请随时在 [论坛][20] 上与我们联系。

## 也可以看看

  * [使用 C# 将 PDF 转换为图像][21]
  * [使用 C# 将 PDF 转换为 Excel][22]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/12/convert-pdf-to-html-using-csharp.jpg
 [2]: https://docs.fileformat.com/pdf/
 [3]: https://docs.fileformat.com/web/html/
 [4]: #CSharp-API-to-Convert-PDF-to-HTML-Free-Download
 [5]: #PDF-to-HTML-Conversion-using-CSharp
 [6]: #Convert-Range-of-Pages-from-PDF-to-HTML-in-CSharp
 [7]: #Convert-Specific-Pages-of-PDF-to-HTML-in-CSharp
 [8]: #PDF-to-HTML-Conversion-with-Watermark-in-CSharp
 [9]: https://products.groupdocs.com/conversion/net
 [10]: https://downloads.groupdocs.com/conversion/net
 [11]: https://www.nuget.org/packages/groupdocs.conversion
 [12]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/Converter
 [13]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/markupconvertoptions
 [14]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.converter/convert/methods/16
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/12/Convert-PDF-to-HTML-in-CSharp.jpg
 [16]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/WatermarkOptions
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/12/PDF-to-HTML-Conversion-with-Watermark-in-CSharp.jpg
 [18]: https://purchase.conholdate.com/temporary-license
 [19]: https://docs.groupdocs.com/conversion/net/
 [20]: https://forum.groupdocs.com/c/conversion/11
 [21]: https://blog.conholdate.com/2021/09/23/convert-pdf-to-images-using-csharp/
 [22]: https://blog.conholdate.com/2021/03/31/convert-pdf-to-excel-using-csharp/








