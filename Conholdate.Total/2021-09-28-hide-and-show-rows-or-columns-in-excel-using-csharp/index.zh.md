---
title: "'使用 C# 在 Excel 中隐藏和显示行或列'"
author: Muzammil Khan
date: 2021-09-28T05:53:10+00:00
summary: "作为 C# 开发人员，您可以轻松地以编程方式隐藏和显示 Excel 工作表中的行或列。在本文中，您将学习**如何使用 C# 隐藏和显示 Excel 工作表的行或列**。"
url: /zh/2021/09/28/hide-and-show-rows-or-columns-in-excel-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "在 Excel 中隐藏列"
  - "隐藏行和列"
  - "在 Excel 中隐藏行"
  - "隐藏/取消隐藏行和列"

---


{{< figure align=center src="images/hide-or-show-rows-and-columns-in-excel-using-csharp.jpg" alt="使用 C# 在 Excel 中隐藏或显示行和列">}}
 

作为 C# 开发人员，您可以轻松地以编程方式隐藏和显示 Excel 工作表中的行或列。在本文中，您将学习**如何使用 C# 隐藏和显示 Excel 工作表的行或列**。

本文讨论/涵盖了以下主题：

  * [用于隐藏和显示行或列的 C# API][2]
  * [使用 C# 隐藏行和列][3]
  * [使用 C# 显示隐藏的行和列][4]
  * [使用 C# 隐藏多行和多列][5]
  * [使用 C# 显示所有隐藏的行和列][6]

## 用于隐藏和显示行或列的 C# API {#CSharp-API-to-Hide-and-Show-Rows-or-Columns}

为了隐藏和显示 [Excel][7] 工作表中的行和列，我将使用 [Aspose.Cells for .NET API][8]。它是一个著名的电子表格操作 API，可让您在 .NET 应用程序中创建和处理 Excel 文件。 API 允许您隐藏 Excel 文件中的任何行和列，或以编程方式显示隐藏的行和列。

您可以 [下载][9] API 的 DLL 或使用 [NuGet][10] 安装它。

```
Install-Package Aspose.Cells
```

## 使用 C# 隐藏行和列 {#Hide-Rows-and-Columns-using-CSharp}

您可以按照以下步骤以编程方式隐藏 Excel 工作表中的行和列：

  * 使用输入文件路径创建 [Workbook][11] 类的实例。
  * 创建 [Worksheet][12] 类的实例。
  * 通过索引访问 [Worksheets][13] 集合中的工作表。
  * 通过调用 [HideRow()][14] 方法隐藏行并传递行索引以隐藏。
  * 通过调用 [HideColumn()][15] 方法隐藏列并传递列索引以隐藏。
  * 使用输出文件路径调用 _[Save()][16]_ 方法。

以下代码示例显示**如何使用 C# 隐藏 Excel 工作表中的行和列**。

```
// 实例化工作簿
Workbook workbook = new Workbook(@"C:\Files\Book1.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.Worksheets[0];

// 隐藏工作表的第三行
worksheet.Cells.HideRow(2);

// 隐藏工作表的第二列
worksheet.Cells.HideColumn(1);

// 保存修改后的 Excel 文件
workbook.Save(@"C:\Files\HideRowsColumns.xlsX");
```

{{< figure align=center src="images/Hide-Rows-and-Columns-using-CSharp-1024x457.jpg" alt="使用 C# 隐藏行和列" caption="使用 C# 隐藏行和列。">}}
 

[Workbook][11] 类表示 Excel 工作簿，并提供了几个属性和方法来使用该工作簿。此类的 [Worksheets][13] 属性表示可用工作表的集合。 [Worksheet][12] 类表示 Excel 工作簿的单个工作表。它公开了几个属性和方法来在工作表上执行各种操作。此类的 [Cells][18] 属性表示工作表中可用的单元格集合。

[Cells][19] 类的 [HideRow()][14] 方法隐藏特定行。它将行索引作为输入参数来隐藏该行。 Cells 类还提供了 [HideColumn()][15] 方法，用于根据作为输入参数提供的列索引隐藏特定列。

Workbook 类的 [Save()][16] 方法将工作簿保存在作为输入参数提供的指定文件路径中。

## 使用 C# 显示隐藏的行和列 {#Show-Hidden-Rows-and-Columns-using-CSharp}

您可以按照以下步骤以编程方式在 Excel 工作表中显示特定的隐藏行和列：

  * 使用输入文件路径创建 [Workbook][11] 类的实例。
  * 创建 [Worksheet][12] 类的实例。
  * 通过索引访问 [Worksheets][13] 集合中的工作表。
  * 通过调用 [UnhideRow()][20] 方法显示隐藏行
  * 通过隐藏行的行索引和行高来设置。
  * 通过调用 [UnhideColumn()][21] 方法显示隐藏列
  * 通过隐藏列的列索引和列宽来设置。
  * 使用输出文件路径调用 _[Save()][16]_ 方法。

以下代码示例展示了**如何使用 C#** 在 Excel 工作表中显示特定的隐藏行和列。

```
// 实例化工作簿
Workbook workbook = new Workbook(@"C:\Files\HideRowsColumns.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.Worksheets[0];

// 取消隐藏第三行并将其高度设置为 13.5
worksheet.Cells.UnhideRow(2, 13.5);

// 取消隐藏第二列并将其宽度设置为 8.5
worksheet.Cells.UnhideColumn(1, 20.5);

// 保存修改后的 Excel 文件
workbook.Save(@"C:\Files\ShowRowsColumns.xlsx");
```

{{< figure align=center src="images/Show-Hidden-Rows-and-Columns-using-CSharp-1024x457.jpg" alt="使用 C# 显示隐藏的行和列" caption="使用 C# 显示隐藏的行和列">}}
 

[Cells][19] 类的 [UnhideRow()][20] 方法在工作表中显示特定的隐藏行。它将隐藏行的行索引作为输入参数使其可见。 Cells 类还提供了 [unhideColumn()][21] 方法来根据作为输入参数提供的列索引显示隐藏列。

## 使用 C# 隐藏多行和多列 {#Hide-Multiple-Rows-and-Columns-using-CSharp}

您可以按照以下步骤以编程方式隐藏 Excel 工作表中的多行和多列：

  * 使用输入文件路径创建 [Workbook][11] 类的实例。
  * 创建 [Worksheet][12] 类的实例。
  * 通过索引访问 [Worksheets][13] 集合中的工作表。
  * 调用 [HideRows()][23] 方法，传递起始行索引和总行数来隐藏。
  * 调用 [HideColumns()][24] 方法，传递起始列索引和总列进行隐藏。
  * 通过使用输出文件路径调用 _[Save()][16]_ 方法进行保存。

以下代码示例显示**如何使用 C# 隐藏 Excel 工作表中的多行和多列**。

```
// 实例化工作簿
Workbook workbook = new Workbook(@"C:\Files\Book1.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.Worksheets[0];

// 在工作表中隐藏 3,4 和 5 行
worksheet.Cells.HideRows(2, 3);

// 在工作表中隐藏 2 和 3 列
worksheet.Cells.HideColumns(1, 2);

// 保存修改后的 Excel 文件
workbook.Save(@"C:\Files\HideMultiple.xlsx");
```

{{< figure align=center src="images/Hide-Multiple-Rows-and-Columns-using-CSharp-1024x457.jpg" alt="使用 C# 隐藏多行和多列" caption="使用 C# 隐藏多行和多列。">}}
 

Cells 类提供了 [HideRows()][23] 方法来隐藏多行。您需要指定起始行索引和要隐藏的总行数作为输入参数。类似地，为了隐藏多个列，Cells 类提供了 [HideColumns()][24] 方法，该方法将列索引和要隐藏的总列数作为输入参数。

## 使用 C# 显示所有隐藏的行和列 {#Show-All-Hidden-Rows-and-Columns-using-CSharp}

您可以按照下面提到的步骤以编程方式显示 Excel 工作表中的所有隐藏行和列：

  * 使用输入文件路径创建 [Workbook][11] 类的实例。
  * 创建 [Worksheet][12] 类的实例。
  * 通过索引访问 [Worksheets][13] 集合中的工作表。
  * 逐一检查所有行的 [IsHidden][26] 属性，如果为真则
      * 调用 [UnhideRow()][20] 方法，设置行索引和行高。
  * 逐一检查所有列的 [IsHidden][27] 属性，如果为真，则
      * 调用 [UnhideColumn()][21] 方法，设置列索引和列宽。
  * 使用输出文件路径调用 _[Save()][16]_ 方法。

以下代码示例展示了**如何使用 C#** 在 Excel 工作表中显示所有隐藏的行和列。

```
// 实例化工作簿
Workbook workbook = new Workbook(@"C:\Files\HideMultiple.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.Worksheets[0];

// 显示所有行
var AllRows = worksheet.Cells.Rows;
foreach (Row row in AllRows)
{
    if (row.IsHidden)
    {
        worksheet.Cells.UnhideRow(row.Index, 20.5);
    }
}

// 显示所有列
var AllColumns = worksheet.Cells.Columns;
foreach (var column in AllColumns)
{
    if (column.IsHidden)
    {
        worksheet.Cells.UnhideColumn(column.Index, 20.5);
    }
}

// 保存修改后的 Excel 文件
workbook.Save(@"C:\Files\ShowAllRowsColumns.xlsx");
```

{{< figure align=center src="images/Show-All-Rows-and-Columns-using-CSharp-1024x457.jpg" alt="使用 C# 显示所有隐藏的行和列" caption="使用 C# 显示所有隐藏的行和列。">}}
 

[Row][29] 类的 [IsHidden][26] 属性指示该行是否隐藏。类似地，[Column][30] 类的 [IsHidden][27] 属性指示列是否隐藏。

## 获得免费许可证

您可以通过申请 [免费的临时许可证][31] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C# 在 Excel 文件中隐藏列和行**。您还学习了**如何以编程方式在 Excel 文件中显示隐藏的列和行**。此外，您还学习了**如何在 Excel 工作表中隐藏多行和多列**。本文还解释了**如何使用 C#** 在 Excel 中显示所有隐藏的行和列。您可以使用 [文档][32] 了解更多关于 Aspose.Cells for .NET API 的信息。如有任何歧义，请随时在 [论坛][33] 上与我们联系。

## 也可以看看

  * [使用 C# 删除 Excel 中的空白行和列][34]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/hide-or-show-rows-and-columns-in-excel-using-csharp.jpg
 [2]: #CSharp-API-to-Hide-and-Show-Rows-or-Columns
 [3]: #Hide-Rows-and-Columns-using-CSharp
 [4]: #Show-Hidden-Rows-and-Columns-using-CSharp
 [5]: #Hide-Multiple-Rows-and-Columns-using-CSharp
 [6]: #Show-All-Hidden-Rows-and-Columns-using-CSharp
 [7]: https://docs.fileformat.com/spreadsheet/xlsx/
 [8]: https://products.aspose.com/cells/net/
 [9]: https://downloads.aspose.com/cells/net
 [10]: https://www.nuget.org/packages/aspose.cells
 [11]: https://apireference.aspose.com/cells/net/aspose.cells/workbook
 [12]: https://apireference.aspose.com/cells/net/aspose.cells/worksheet
 [13]: https://apireference.aspose.com/cells/net/aspose.cells/workbook/properties/worksheets
 [14]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/hiderow
 [15]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/hidecolumn
 [16]: https://apireference.aspose.com/cells/net/aspose.cells.workbook/save/methods/2
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Hide-Rows-and-Columns-using-CSharp.jpg
 [18]: https://apireference.aspose.com/cells/net/aspose.cells/worksheet/properties/cells
 [19]: https://apireference.aspose.com/cells/net/aspose.cells/cells
 [20]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/unhiderow
 [21]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/unhidecolumn
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Show-Hidden-Rows-and-Columns-using-CSharp.jpg
 [23]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/hiderows
 [24]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/hidecolumns
 [25]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Hide-Multiple-Rows-and-Columns-using-CSharp.jpg
 [26]: https://apireference.aspose.com/cells/net/aspose.cells/row/properties/ishidden
 [27]: https://apireference.aspose.com/cells/net/aspose.cells/column/properties/ishidden
 [28]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Show-All-Rows-and-Columns-using-CSharp.jpg
 [29]: https://apireference.aspose.com/cells/net/aspose.cells/row
 [30]: https://apireference.aspose.com/cells/net/aspose.cells/column
 [31]: https://purchase.aspose.com/temporary-license
 [32]: https://docs.aspose.com/cells/net/
 [33]: https://forum.aspose.com/c/cells/9
 [34]: https://blog.conholdate.com/2020/12/25/delete-blank-rows-and-columns-in-excel-using-csharp/








