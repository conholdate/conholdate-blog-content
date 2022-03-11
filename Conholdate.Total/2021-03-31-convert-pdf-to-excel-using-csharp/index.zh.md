---
title: "'使用 C# 将 PDF 转换为 Excel'"
author: Muzammil Khan
date: 2021-03-31T03:23:05+00:00
summary: "在 .NET 应用程序中以编程方式轻松地将表格数据从 PDF 文件导出到 Excel 工作表（.xlsx 或 .xls）。在本文中，您将学习**如何使用 C# 将 PDF 转换为 Excel**。"
url: /zh/2021/03/31/convert-pdf-to-excel-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "将 PDF 转换为 Excel"
  - "将 PDF 转换为 XLSX"
  - "将数据从 PDF 导出到 Excel"
  - "将数据表导出到 Excel"

---


{{< figure align=center src="images/Convert-PDF-to-Excel.jpg" alt="将 PDF 转换为 Excel">}}
 

您可以在 .NET 应用程序中以编程方式轻松地将表格数据从 PDF 文件导出到 Excel 工作表（_.xlsx_ 或 _.xls_）。当您需要编辑数据或需要应用 Excel 中可用的各种计算时，这种转换很有用。在本文中，您将学习**如何使用 C# 将 PDF 转换为 Excel**。

本文将涵盖以下主题：

  * [C# API 将 PDF 转换为 Excel][2]
  * [将 PDF 转换为 Excel][3]

## C# API 将 PDF 转换为 Excel {#net-conversion-api}

我将使用 [GroupDocs.Conversion for .NET API][4] 将 [PDF][5] 转换为 [XLSX][6]。该 API 提供了一种快速、高效、可靠的文件转换解决方案到 .NET 应用程序中，而无需安装任何外部软件。它还使您能够使用 C#、ASP.NET 和其他 .NET 相关技术构建功能强大的文档转换应用程序。

您可以[下载][7] API 的 DLL 或使用 [NuGet][8] 安装它。

```
Install-Package GroupDocs.Conversion
```

## 使用 C# 将 PDF 转换为 Excel {#convert-pdf-to-xlsx}

您可以按照以下简单步骤将 PDF 文档转换为 Excel：

  1. 如果适用，请设置 _**[PdfLoadOptions][9]**_。
  2. 使用 _**[SpreadsheetConvertOptions][10]**_ 设置转换选项
  3. 创建 _**[Converter][11]**_ 类的实例
  4. 提供文件路径和加载选项
  5. 调用 _**[Convert][12]**_ 方法以及输出文件路径和转换选项

以下代码示例展示了**如何使用 C# 将表格数据从 PDF 文件导出到 Excel 工作表**。

```
// PDF 加载选项
GroupDocs.Conversion.Contracts.Func<LoadOptions> getLoadOptions = () => new PdfLoadOptions
{
    FlattenAllFields = true,    // all fields in the source document will be flatten during conversion
    Password = "123"            // provide password if document is password protected
};

// Excel 转换选项
SpreadsheetConvertOptions options = new SpreadsheetConvertOptions
{
    PageNumber = 1,                     // Starting page number
    PagesCount = 1,                     // Total pages to convert
    Format = SpreadsheetFileType.Xlsx,  // Conversion format
    Password = "password",              // Set password for converted file
    Zoom = 110                          // Zoom level
};

// 将 PDF 转换为 XLSX
Converter converter = new Converter("C:\\Files\\sample.pdf", getLoadOptions);
converter.Convert("C:\\Files\\converted.xlsx", options);
```

{{< figure align=center src="images/ConvertPDFtoXLSX-1024x484.jpg" alt="将 PDF 转换为 XLSX" caption="将 PDF 转换为 XLSX">}}
 

**_PdfLoadOptions_** 类提供加载 PDF 文档的各种选项。这些 [properties][14] 包括 **FlattenAllFields、HidePdfAnnotations、Password** 和 **RemoveEmbeddedFiles**。您可以在 [文档][15] 中找到更多详细信息。

**SpreadsheetConvertOptions** 类提供某些 [properties][16] 用于将文件从其他格式转换为电子表格文件类型。

  * **_PageNumber_** 属性定义要转换的源文档的起始页码。
  * **_PagesCount_** 属性定义从 **_PageNumber_** 开始要转换的总页数。
  * 您可以通过向 **_Pages_** 属性提供页面索引列表来转换特定页面。
  * 您可以使用 **_Password_** 属性为转换后的文件设置密码。
  * **_Zoom_** 属性可用于设置转换文件的缩放级别（以百分比表示）。
  * **_Format_** 属性定义转换后文件的输出格式。

您可以在文档中找到有关“[使用高级选项转换为电子表格][17]”的更多详细信息。

## 获得免费许可证

您可以通过请求 [免费的临时许可证][18] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C# 将表格数据从** **PDF 文档导出到 Excel 工作表**。您可以使用 [文档][19] 了解有关 GroupDocs.Conversion .NET API 的更多信息。如有任何歧义，请随时在 [论坛][20] 上与我们联系。

## 也可以看看

  * [在 C# 中将数据导出到 Excel][21]
  * [在 C# .NET 中将 CAD 绘图转换为 PDF][22]
  * [C# 将 WebP 图像转换为 JPG、PNG、TIFF 和 PDF][23]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/03/Convert-PDF-to-Excel.jpg
 [2]: #net-conversion-api
 [3]: #convert-pdf-to-xlsx
 [4]: https://products.groupdocs.com/conversion/net
 [5]: https://docs.fileformat.com/pdf/
 [6]: https://docs.fileformat.com/spreadsheet/xlsx/
 [7]: https://downloads.groupdocs.com/conversion/net
 [8]: https://www.nuget.org/packages/GroupDocs.Conversion
 [9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.load/pdfloadoptions
 [10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions
 [11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
 [12]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.converter/convert/methods/16
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/03/ConvertPDFtoXLSX.jpg
 [14]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.load/pdfloadoptions/properties/index
 [15]: https://docs.groupdocs.com/conversion/net/load-pdf-document-with-options/
 [16]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions/properties/index
 [17]: https://docs.groupdocs.com/conversion/net/convert-to-spreadsheet-with-advanced-options/
 [18]: https://purchase.groupdocs.com/temporary-license
 [19]: https://docs.groupdocs.com/conversion/net/
 [20]: https://forum.groupdocs.com/c/conversion/11
 [21]: https://blog.conholdate.com/2020/08/10/export-data-to-excel-in-csharp/
 [22]: https://blog.groupdocs.com/2020/11/08/convert-cad-drawings-to-pdf-in-csharp/
 [23]: https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/








