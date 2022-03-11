---
title: "'使用 C# 删除 Excel 中的空白行和列'"
author: Muhammad Sohail
date: 2020-12-25T13:06:24+00:00
summary: "在本文中，我将解释如何使用 C# 删除 Excel 文件中的空白行和列。我还将解释为什么在删除空白行和列时应该自动更新引用（用于公式、图表和表格）。"
url: /zh/2020/12/25/delete-blank-rows-and-columns-in-excel-using-csharp/
categories:
  - "Conholdate.Total 产品系列"

---
在本文中，我将解释如何使用 C# 删除 Excel 文件中的空白行和列。我还将解释如何在删除空白行和列的同时自动更新引用（用于公式、图表和表格）。

  * [使用 C# 删除 Excel 中的空白行][1]
  * [删除空白行时自动更新参考][2]
  * [使用 C# 删除 Excel 中的空白列][3]

## 用于删除空白行和列的 C# API

[Aspose.Cells for .NET][4] 是一个著名的电子表格操作 API，可让您在 .NET 应用程序中创建和处理 Excel 文件。该 API 允许您在几行代码中删除 Excel 文件中的空白行和列。您可以 [下载][5] API 的二进制文件或使用 [NuGet][6] 安装它。

```
PM> Install-Package Aspose.Cells
```

## 使用 C# 删除 Excel 中的空白行 {#Delete-Blank-Rows-in-Excel}

以下是使用 C# 删除 Excel 中所有空白行的步骤。

  * 使用 [Workbook][7] 对象打开一个 Excel 文件。
  * 访问具有空白行的工作表。可以按索引（从零开始）或按名称访问工作表。
  * 调用 [Cells.DeleteBlankRows()][8] 方法删除所有不包含任何数据的空白行。

以下示例代码显示了如何使用 C# 在 Excel 中删除空白行。

```
using Aspose.Cells;

// 打开现有的 Excel 文件。
Workbook wb = new Workbook("SampleInput.xlsx");

// 获取电子表格中的工作表集合。
WorksheetCollection sheets = wb.Worksheets;

// 通过索引从 WorksheetCollection 中获取第一个 Worksheet。
Worksheet sheet = sheets[0];
// 或按名称。
// 工作表 sheet = sheet["Sheet1"];

// 从工作表中删除空白行。
sheet.Cells.DeleteBlankRows();

// 保存excel文件。
wb.Save("SampleOutput.xlsx");
```

{{< figure align=center src="images/Remove-Blank-Rows.jpg" alt="删除空白行" caption="图 1：删除空白行">}}
 

请注意 [Cells.DeleteBlankRows][8] 方法会删除空白行，即使对它们应用了某种格式。它还会删除数据下方的格式化空白行。

{{< figure align=center src="images/Formatted-Blank-Rows.jpg" alt="删除格式化的空白行" caption="图 2：删除格式化的空白行">}}
 

如果要从 Excel 文档中的所有工作表中删除空白行，只需遍历 [WorksheetCollection][11] 并在每个工作表上调用 [DeleteBlankRows][8] 方法，如下代码所示：

```
// 打开现有的 Excel 文件。
Workbook workbook = new Workbook("SampleInput.xlsx");

// 遍历工作表。
foreach (Worksheet sheet in workbook.Worksheets)
{
    // Delete the Blank Rows from the worksheet.
    sheet.Cells.DeleteBlankRows();
}

// 保存excel文件。
workbook.Save("SampleOutput.xlsx");
```

## 删除空白行时自动更新参考 {#Update-References-Automatically}

删除空白行会破坏公式、图表和表格中的引用。例如，第二个工作表中的单元格 B2 有一个公式 **=Sheet1!C3** 指的是第一个工作表中的单元格 C3，如下图所示。

{{< figure align=center src="images/Worksheet-With-Formula-1024x640.jpg" alt="A cell in Sheet2 is referring to a value in Sheet1." caption="图 3：Sheet2 中的单元格引用 Sheet1 中的值。">}}
 

If we remove blank rows in Sheet1, the value **lima@gmail.com** will move to cell C1. 但公式 (=Sheet1!C3) 不会更新，单元格 B2 将包含无效值，如下所示。

{{< figure align=center src="images/Cell-with-Invalid-Value-1024x640.jpg" alt="删除空白行后，单元格 B2 中的公式未更新。" caption="图 4：删除空白行后，单元格 B2 中的公式没有更新。">}}
 

我们可以通过使用 [DeleteOptions.UpdateReference][14] 属性并将其设置为 **true** 来避免此问题。它将确保在删除空白行时更新引用。以下示例代码展示了如何使用 **DeleteOptions.UpdateReference** 属性。

```
// 打开现有的 Excel 文件。
Workbook wb = new Workbook("SampleInput.xlsx");

// 获取电子表格中的工作表集合。
WorksheetCollection sheets = wb.Worksheets;

// 通过索引从 WorksheetCollection 中获取第一个 Worksheet。
Worksheet sheet = sheets[0];

// 此选项将确保引用（在公式、图表中）
// 在删除空白行时更新。
DeleteOptions options = new DeleteOptions();
options.UpdateReference = true;

// 从工作表中删除空白行。
sheet.Cells.DeleteBlankRows(options);

// 保存excel文件。
wb.Save("SampleOutput.xlsx");
```

如下图所示，公式已更新，单元格 B2 包含有效值。

{{< figure align=center src="images/Cell-with-Valid-value-1024x640.jpg" alt="公式已更新，单元格包含有效值。" caption="图 5：公式已更新，单元格包含有效值。">}}
 

## 使用 C# 删除 Excel 中的空白列 {#Delete-Blank-Columns-in-Excel}

删除空白列的步骤与删除空白行的步骤相同。我们使用 [Cells.DeleteBlankColumns][16] 方法删除所有不包含任何数据的空白列。以下示例代码显示了如何在 C# 中删除空白行和列。

```
// 打开现有的 Excel 文件。
Workbook wb = new Workbook("SampleInput.xlsx");

// 获取电子表格中的工作表集合。
WorksheetCollection sheets = wb.Worksheets;

// 通过索引从 WorksheetCollection 中获取第一个 Worksheet。
Worksheet sheet = sheets[0];

// 此选项将确保引用（在公式、图表中）
// 在删除空白行和列时更新。
DeleteOptions options = new DeleteOptions();
options.UpdateReference = true;

// 删除空白行和列。
sheet.Cells.DeleteBlankRows(options);
sheet.Cells.DeleteBlankColumns(options);

// 计算工作簿的公式
wb.CalculateFormula();

// 保存excel文件。
wb.Save("SampleOutput.xlsx");
```

{{< figure align=center src="images/Delete-Blank-Rows-and-Columns-1024x640.jpg" alt="删除空白行和列" caption="图 6：删除空白行和列">}}
 

## 结论

在本文中，您学习了如何使用 C# 删除 Excel 文件中的空白行和列。此外，您还学习了如何在删除空白行和列的同时自动更新引用（用于公式、图表和表格）。请查看 Aspose.Cells for .NET 的 [文档][18] 了解更多信息。如果您有任何问题，请随时在我们的 [支持论坛][19] 上发布。我们将在几个小时内回复他们。

## 也可以看看

  * [在没有 MS Office 的 C# 中以编程方式创建 MS Excel 文件][20]
  * [使用 C# 将 MS Excel XLSX 文件转换为 DOCX][21]

 [1]: #Delete-Blank-Rows-in-Excel
 [2]: #Update-References-Automatically
 [3]: #Delete-Blank-Columns-in-Excel
 [4]: https://products.aspose.com/cells/net
 [5]: https://downloads.aspose.com/cells/net
 [6]: http://nuget.org/packages/Aspose.Cells
 [7]: https://apireference.aspose.com/cells/net/aspose.cells/workbook
 [8]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/deleteblankrows
 [9]: https://blog.conholdate.com/wp-content/uploads/sites/27/2020/12/Remove-Blank-Rows.jpg
 [10]: https://blog.conholdate.com/wp-content/uploads/sites/27/2020/12/Formatted-Blank-Rows.jpg
 [11]: https://apireference.aspose.com/cells/net/aspose.cells/worksheetcollection
 [12]: https://blog.conholdate.com/wp-content/uploads/sites/27/2020/12/Worksheet-With-Formula.jpg
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2020/12/Cell-with-Invalid-Value.jpg
 [14]: https://apireference.aspose.com/cells/net/aspose.cells/deleteoptions/properties/updatereference
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2020/12/Cell-with-Valid-value.jpg
 [16]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/deleteblankcolumns
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2020/12/Delete-Blank-Rows-and-Columns.jpg
 [18]: https://docs.aspose.com/cells/net/
 [19]: https://forum.aspose.com/
 [20]: https://blog.aspose.com/2020/01/21/create-excel-xls-xlsx-programmatically-in-csharp-net/
 [21]: https://blog.aspose.com/2020/10/15/convert-excel-xlsx-to-docx-using-csharp/








