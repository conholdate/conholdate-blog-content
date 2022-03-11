---
title: "'Excel 文件查看器 - 使用 C# 显示 Excel 数据'"
author: Muzammil Khan
date: 2022-02-25T06:43:17+00:00
summary: "作为 C# 开发人员，您可以在 HTML、PDF 或 .NET 应用程序中以编程方式呈现和查看 Excel 文件。在本文中，您将学习**如何使用 C# 创建 Excel 文件查看器并显示 Excel 数据**。"
url: /zh/2022/02/25/excel-file-viewer-display-excel-data-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "C# Excel 文件查看器"
  - "使用 C# 显示 Excel 数据"
  - "Excel 转 HTML"
  - "Excel 到图像"
  - "Excel转PDF"
  - "GroupDocs.Viewer .NET"
  - "在 C# 中将 Excel 渲染为图像"
  - "在 C# 中将 Excel 呈现为 PDF"
  - "在 C# 中渲染 Excel 文件"
  - "在 C# 中将 Excel 渲染为 HTML"

---


{{< figure align=center src="images/excel-file-viewer-display-excel-data-using-csharp.jpg" alt="Excel 文件查看器 - 使用 C# 显示 Excel 数据">}}
 

我们可以在 HTML、PDF 或 .NET 应用程序中以编程方式将 Excel 文件中的数据显示为图像。它允许在不共享实际 Excel 文件的情况下向其他人显示数据。在本文中，我们将学习如何使用 **C#** 创建**Excel 文件查看器**和**显示 Excel 数据**。

本文将涵盖以下主题：

  * [C# Excel 文件查看器 API — 免费下载][2]
  * [使用 C# 在 HTML 中显示 Excel 数据][3]
  * [使用 C# 以 PDF 格式呈现 Excel 数据][4]
  * [使用 C# 以 JPG 图像格式查看 Excel 文件][5]
  * [使用 C# 调整单元格中的文本溢出][6]
  * [渲染 Excel 的隐藏行和列][7] 
  * [跳过 Excel 中的空行和列][8]
  * [按行和列拆分 Excel 工作表][9]

## C# Excel 文件查看器 API — 免费下载 {#CSharp-Excel-File-Viewer-API-Free-Download}

为了显示来自 [XLS][10] 或 [XLSX][11] 电子表格的数据，我们将使用 [GroupDocs.Viewer for .NET][12] API。它允许以编程方式呈现和查看[支持的电子表格格式][13]。请[下载][14] API 的 DLL 或使用 [NuGet][15] 安装它。

```
PM> Install-Package GroupDocs.Viewer
```

## 使用 C# 在 HTML 中显示 Excel 数据 {#Display-Excel-Data-in-HTML-using-CSharp}

我们可以按照下面给出的简单步骤来渲染 Excel 文件并以 HTML 格式显示数据：

  1. 首先，使用 _**[Viewer][16]** _class 加载一个 Excel 文件。
  2. 为 [**_EmbeddedResources_**][18] 创建 [_**HtmlViewOptions**_ ][17] 类的实例。
  3. 提供输出文件路径作为参数。
  4. （可选）设置各种视图选项，例如_[RenderToSinglePage][19]_。
  5. 最后，调用 _**[View()][20]**_ 方法并将 _HtmlViewOptions_ 作为参数传递。

以下代码示例展示了**如何使用 C# 以 HTML 格式呈现 Excel 文件**。

```
// 此代码示例演示如何以 HTML 格式呈现 Excel 文件。
// 加载 Excel 文件
Viewer viewer = new Viewer(@"C:\Files\Viewer\sample.xlsx");

// 定义 HTML 视图选项
HtmlViewOptions viewOptions = HtmlViewOptions.ForEmbeddedResources(@"C:\Files\Viewer\sample_output.html");
viewOptions.RenderToSinglePage = true;

// 渲染视图
viewer.View(viewOptions);
```

{{< figure align=center src="images/Display-Excel-Data-in-HTML-using-CSharp-1024x512.jpg" alt="使用 C# 以 HTML 格式显示 Excel 数据。" caption="使用 C# 以 HTML 格式显示 Excel 数据。">}}
 

## 使用 C# 以 PDF 格式呈现 Excel 数据 {#Render-Excel-Data-in-PDF-using-CSharp}

我们可以按照以下步骤呈现 Excel 文件并以 PDF 格式显示数据：

  1. 首先，使用 [Viewer](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer) 类加载 Excel 文件。
  2. 创建 [PdfViewOptions](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions) 类的实例。
  3. 提供输出文件路径作为参数。
  4. 最后，调用 [View()](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view) 方法并将 **PdfViewOptions** 作为参数传递。

以下代码示例显示**如何使用 C# 以 PDF 格式呈现 Excel 文件**。

```
// 此代码示例演示如何以 PDF 格式呈现 Excel 文件。
// 加载 Excel 文件
看法er viewer = new 看法er(@"C:\Files\看法er\sample.xlsx");

// 定义 PDF 视图选项
Pdf看法Options viewOptions = new Pdf看法Options(@"C:\Files\看法er\sample_output.pdf");

// 看法
viewer.看法(viewOptions);
```

{{< figure align=center src="images/Render-Excel-Data-in-PDF-using-CSharp-1024x512.jpg" alt="使用 C# 以 PDF 格式呈现 Excel 数据。" caption="使用 C# 以 PDF 格式呈现 Excel 数据。">}}
 

## 使用 C# 以 JPG 图像格式查看 Excel 文件 {#View-Excel-File-as-JPG-Image-using-CSharp}

我们可以按照以下步骤渲染 Excel 文件并将数据显示为 JPG 图像：

  1. 首先，使用 [Viewer](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer) 类加载 Excel 文件。
  2. 创建 [JpgViewOptions](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/jpgviewoptions) 类的实例。
  3. 提供输出文件路径。
  4. 最后，调用 [View()](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view) 方法并将 **JpgViewOptions** 作为参数传递。

以下代码示例显示了**如何使用 C#** 将 Excel 文件呈现为 JPG。

```
// 此代码示例演示如何以 JPG 图像呈现 Excel 文件。
// 加载 Excel 文件
看法er viewer = new 看法er(@"C:\Files\看法er\sample.xlsx");

// 定义 JPG 视图选项
Jpg看法Options viewOptions = new Jpg看法Options(@"C:\Files\看法er\sample_output.jpg");

// 看法
viewer.看法(viewOptions);
```

{{< figure align=center src="images/View-Excel-File-as-JPG-Image-using-CSharp-1024x582.jpg" alt="使用 C# 以 JPG 图像格式查看 Excel 文件。" caption="使用 C# 以 JPG 图像格式查看 Excel 文件。">}}
 
同样，我们也可以将 Excel 文件渲染为 PNG 图像，如下所示：

```
// 此代码示例演示如何在 PNG 图像中呈现 Excel 文件。
// 加载 Excel 文件
看法er viewer = new 看法er(@"C:\Files\看法er\sample.xlsx");

// 定义 PNG 视图选项
Png看法Options viewOptions = new Png看法Options(@"C:\Files\看法er\sample_output.png");

// 看法
viewer.看法(viewOptions);
```

## 使用 C# 调整单元格中的文本溢出 {#Adjust-Text-Overflow-in-Cells-using-CSharp}

我们可以在渲染 Excel 工作表时调整单元格中的文本溢出。 API 提供以下类型的溢出调整：

  * _Overlay_ – 覆盖下一个单元格，即使它们不是空的。
  * _OverlayIfNextIsEmpty_ – 仅当它们为空时才覆盖下一个单元格。
  * _AutoFitColumn_ – 扩展列以适应文本。
  * _HideText_ – 隐藏溢出文本。

请按照以下步骤调整文本溢出：

  1. 首先，使用 _**[Viewer][16]** _class 加载一个 Excel 文件。
  2. 创建 [_**PdfViewOptions**_ ][24] 类的实例
  3. 提供输出文件路径。
  4. 将 SpreadsheetOptions 的 TextOverflowMode 属性设置为 _HideText_。
  5. （可选）将 RenderHeadings 和 RenderGridLines 设置为 true。
  6. 最后，调用 _**[View()][20]**_ 方法并将 _PdfViewOptions_ 作为参数传递。

以下代码示例显示了**如何在使用 C# 呈现 Excel 文件时调整文本溢出**。

```
// 此代码示例演示如何调整单元格中的文本溢出、渲染标题和网格线。
// 加载 Excel 文件
看法er viewer = new 看法er(@"C:\Files\看法er\sample.xlsx");

// 定义 PDF 视图选项
Pdf看法Options viewOptions = new Pdf看法Options(@"C:\Files\看法er\sample_overflow.pdf");

// 调整文字溢出
viewOptions.SpreadsheetOptions.TextOverflowMode = TextOverflowMode.HideText;

// 呈现 Excel 标题
viewOptions.SpreadsheetOptions.RenderHeadings = true;

// 渲染网格线
viewOptions.SpreadsheetOptions.RenderGridLines = true;

// 看法
viewer.看法(viewOptions);
```

{{< figure align=center src="images/Adjust-Text-Overflow-in-Cells-using-CSharp-1024x512.jpg" alt="使用 C# 调整单元格中的文本溢出。" caption="使用 C# 调整单元格中的文本溢出。">}}
 
## 渲染 Excel 的隐藏行和列 {#Render-Hidden-Rows-and-Columns-of-Excel}

我们可以按照前面提到的步骤来呈现 Excel 工作表的隐藏行和列。但是，我们只需要在第 4 步将以下属性设置为 true：

```
viewOptions.SpreadsheetOptions.RenderHiddenColumns = true;
viewOptions.SpreadsheetOptions.RenderHiddenRows = true;
```

以下代码示例展示了**如何使用 C#** 在 PDF 中显示 Excel 文件的隐藏行和列。

```
// 此代码示例演示如何呈现 Excel 工作表的隐藏行和列。
// 加载 Excel 文件
看法er viewer = new 看法er(@"C:\Files\看法er\sample.xlsx");

// 定义 PDF 视图选项
Pdf看法Options viewOptions = new Pdf看法Options(@"C:\Files\看法er\hidden_rows_columns.pdf");
viewOptions.SpreadsheetOptions.RenderHiddenColumns = true;
viewOptions.SpreadsheetOptions.RenderHiddenRows = true;

// 看法
viewer.看法(viewOptions);
```

{{< figure align=center src="images/Render-Hidden-Rows-and-Columns-of-Excel-1024x512.jpg" alt="渲染 Excel 的隐藏行和列。" caption="渲染 Excel 的隐藏行和列。">}}
 

## 使用 C# 跳过 Excel 中的空行和列 {#Skip-Empty-Rows-and-Columns-in-Excel-using-CSharp}

我们可以按照前面提到的步骤在查看 Excel 工作表时跳过空行和空列的呈现。但是，我们只需要在第 4 步将以下属性设置为 true：

```
viewOptions.SpreadsheetOptions.SkipEmptyColumns = true;
viewOptions.SpreadsheetOptions.SkipEmptyRows = true;
```

以下代码示例显示**如何使用 C# 跳过 Excel 文件的空行和空列的呈现**。

```
// 此代码示例演示如何跳过 Excel 工作表的隐藏行和列的呈现。
// 加载 Excel 文件
看法er viewer = new 看法er(@"C:\Files\看法er\sample.xlsx");

// 定义 PDF 视图选项
Pdf看法Options viewOptions = new Pdf看法Options(@"C:\Files\看法er\skip_empty.pdf");
viewOptions.SpreadsheetOptions.SkipEmptyColumns = true;
viewOptions.SpreadsheetOptions.SkipEmptyRows = true;

// 看法
viewer.看法(viewOptions);
```

{{< figure align=center src="images/Skip-Empty-Rows-and-Columns-in-Excel-using-CSharp-1024x512.jpg" alt="使用 C# 跳过 Excel 中的空行和列" caption="使用 C# 在 Excel 中跳过空行和空列。">}}
 

## 按行和列拆分 Excel 工作表 {#Split-Excel-Worksheet-by-Rows-and-Columns}

我们可以渲染大型 Excel 工作表，并按一页上的行数和列数对其进行拆分。我们可以按照以下步骤拆分工作表：

  1. 首先，使用 _**[Viewer][16]** _class 加载一个 Excel 文件。
  2. 创建 [_**PdfViewOptions**_ ][24] 类的实例
  3. 提供输出文件路径。
  4. 使用 _ForSplitSheetIntoPages_ 方法初始化 _SpreadsheetOptions_。它以每页的行数和列数作为参数。
  5. 最后，调用 _**[View()][20]**_ 方法并将 _PdfViewOptions_ 作为参数传递。

以下代码示例展示了**如何使用 C#按行和列拆分 Excel 工作表**。

```
// 此代码示例演示如何按行和列拆分 Excel 工作表。
// 加载 Excel 文件
Viewer viewer = new Viewer(@"C:\Files\Viewer\sample.xlsx");

int countRowsPerPage = 25;
int countColumnsPerPage = 5;

PdfViewOptions viewOptions = new PdfViewOptions(@"C:\Files\Viewer\sample_split.pdf");
viewOptions.SpreadsheetOptions = SpreadsheetOptions.ForSplitSheetIntoPages(countRowsPerPage, countColumnsPerPage);

viewer.View(viewOptions);
```

{{< figure align=center src="images/Split-Excel-Worksheet-by-Rows-and-Columns-1024x603.jpg" alt="按行和列拆分 Excel 工作表" caption="按行和列拆分 Excel 工作表。">}}
 

## 获得免费许可证

请通过申请 [免费的临时许可证][29] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了如何：

  * 使用 C# 呈现或查看 HTML、PDF、PNG 和 JPG 格式的 Excel 工作表；
  * 调整 Excel 单元格中的文本溢出和渲染网格线；
  * 显示 Excel 列和行的标题；
  * 跳过空行/列并显示隐藏的行和列；
  * 限制按行和列显示工作表。

此外，您可以使用 [documentation][30] 了解更多关于 GroupDocs.Viewer for .NET API 的信息。如有任何歧义，请随时在 [论坛][31] 上与我们联系。

## 也可以看看

  * [使用 C# 在 Excel 中插入或删除行和列][32]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/excel-file-viewer-display-excel-data-using-csharp.jpg
 [2]: #CSharp-Excel-File-Viewer-API-Free-Download
 [3]: #Display-Excel-Data-in-HTML-using-CSharp
 [4]: #Render-Excel-Data-in-PDF-using-CSharp
 [5]: #View-Excel-File-as-JPG-Image-using-CSharp
 [6]: #Adjust-Text-Overflow-in-Cells-using-CSharp
 [7]: #Render-Hidden-Rows-and-Columns-of-Excel
 [8]: #Skip-Empty-Rows-and-Columns-in-Excel-using-CSharp
 [9]: #Split-Excel-Worksheet-by-Rows-and-Columns
 [10]: https://docs.fileformat.com/spreadsheet/xls/
 [11]: https://docs.fileformat.com/spreadsheet/xlsx/
 [12]: https://products.groupdocs.com/viewer/net
 [13]: https://docs.groupdocs.com/viewer/net/view-excel-spreadsheets/#supported-spreadsheets-formats
 [14]: https://downloads.groupdocs.com/viewer/net
 [15]: https://www.nuget.org/packages/groupdocs.viewer
 [16]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
 [17]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
 [18]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options.htmlviewoptions/forembeddedresources/methods/4
 [19]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions/properties/rendertosinglepage
 [20]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
 [21]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Display-Excel-Data-in-HTML-using-CSharp.jpg
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Render-Excel-Data-in-PDF-using-CSharp.jpg
 [23]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/View-Excel-File-as-JPG-Image-using-CSharp.jpg
 [24]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
 [25]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Adjust-Text-Overflow-in-Cells-using-CSharp.jpg
 [26]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Render-Hidden-Rows-and-Columns-of-Excel.jpg
 [27]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Skip-Empty-Rows-and-Columns-in-Excel-using-CSharp.jpg
 [28]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Split-Excel-Worksheet-by-Rows-and-Columns.jpg
 [29]: https://purchase.conholdate.com/temporary-license
 [30]: https://docs.groupdocs.com/viewer/net/
 [31]: https://forum.groupdocs.com/c/viewer/9
 [32]: https://blog.conholdate.com/2021/10/06/insert-or-delete-rows-and-columns-in-excel-using-csharp/

