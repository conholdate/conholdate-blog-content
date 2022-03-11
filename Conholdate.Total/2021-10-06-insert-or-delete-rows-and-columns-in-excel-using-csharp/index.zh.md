---
title: "'使用 C# 在 Excel 中插入或删除行和列'"
author: Muzammil Khan
date: 2021-10-06T10:01:28+00:00
summary: "作为 C# 开发人员，您可以轻松地以编程方式在 Excel 工作表中插入或删除行和列。在本文中，您将学习**如何使用 C# 在 Excel 工作表中插入或删除行和列**。"
url: /zh/2021/10/06/insert-or-delete-rows-and-columns-in-excel-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "从 Excel 中删除列"
  - "从 Excel 中删除行"
  - "在 Excel 中插入列"
  - "在 Excel 中插入行"

---


{{< figure align=center src="images/insert-or-delete-rows-and-columns-in-excel-using-csharp.jpg" alt="使用 C# 在 Excel 中插入或删除行和列">}}
 
作为 C# 开发人员，您可以轻松地以编程方式在 Excel 工作表中插入或删除行和列。在本文中，您将学习**如何使用 C# 在 Excel 工作表中插入或删除行和列**。

本文讨论/涵盖了以下主题：

  * [用于插入或删除行和列的 C# API][2]
  * [使用 C# 在 Excel 工作表中插入行][3]
  * [使用 C# 在 Excel 工作表中插入带格式的行][4]
  * [使用 C# 从 Excel 工作表中删除行][5]
  * [使用 C# 在 Excel 工作表中插入列][6]
  * [使用 C# 从 Excel 工作表中删除列][7]

## 用于插入或删除行和列的 C# API {#CSharp-API-to-Insert-or-Delete-Rows-and-Columns}

为了在 [Excel][8] 工作表中插入或删除行和列，我将使用 [Aspose.Cells for .NET API][9]。它是一个著名的电子表格操作 API，可让您在 .NET 应用程序中创建和处理 Excel 文件。 API 允许您在 Excel 文件中插入单个或多个行和列。它还使您能够以编程方式删除行和列。

您可以 [下载][10] API 的 DLL 或使用 [NuGet][11] 安装它。

```
Install-Package Aspose.Cells
```

## 使用 C# 在 Excel 工作表中插入行 {#Insert-Rows-in-Excel-Worksheets-using-CSharp}

您可以按照以下提到的步骤以编程方式在 Excel 工作表中插入行：

  * 使用输入文件路径创建 [Workbook][12] 类的实例。
  * 创建 [Worksheet][13] 类的实例。
  * 通过索引访问 [Worksheets][14] 集合中的工作表。
  * 通过调用 [InsertRows()][15] 方法插入行，并传递要开始的行索引和要插入的总行数。
  * 使用输出文件路径调用 _[Save()][16]_ 方法。

以下代码示例展示了**如何使用 C#** 在 Excel 工作表中插入多行。

```
// 实例化工作簿对象
// 通过文件流打开Excel文件
Workbook workbook = new Workbook(@"C:\Files\Book1.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.Worksheets[0];

// 从第 3 行开始在工作表中插入 10 行
worksheet.Cells.InsertRows(2, 10);

// 保存修改后的 Excel 文件
workbook.Save(@"C:\Files\output.xlsx");
```

{{< figure align=center src="images/Insert-Multiple-Rows-in-Excel-Worksheets-using-CSharp-1024x426.jpg" alt="使用 C# 在 Excel 工作表中插入行" caption="使用 C# 在 Excel 工作表中插入多行。">}}
 
同样，您可以使用以下代码示例在 Excel 工作表中插入单行。

```
// 实例化工作簿对象
// 通过文件流打开Excel文件
Workbook workbook = new Workbook(@"C:\Files\Book1.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.Worksheets[0];

// 在工作表的第三个位置插入一行
worksheet.Cells.InsertRow(2);

// 保存修改后的 Excel 文件
workbook.Save(@"C:\Files\output.xlsx");
```

{{< figure align=center src="images/Insert-Rows-in-Excel-Worksheets-using-CSharp-1024x342.jpg" alt="使用 C# 在 Excel 工作表中插入单行" caption="使用 C# 在 Excel 工作表中插入单行">}}
 
API 的 [Workbook][12] 类表示 Excel 工作簿。您可以使用此类的 [Worksheets][14] 属性获取工作簿中所有可用工作表的集合。 Excel 工作簿的任何单个工作表都可以通过使用其索引从 Worksheets 的集合中访问。 [Worksheet][13] 类表示单个工作表。它公开了几个属性和方法来在工作表上执行各种操作。此类的 [Cells][19] 属性表示工作表中可用的单元格集合。 [Cells][20] 类表示工作表中的单个单元格。

[Cells][20] 类的 [InsertRow()][21] 方法允许在指定索引处插入单行。 Cells 类还提供了 [InsertRows()][15] 方法来同时插入多行。它需要从哪里开始插入行的行索引和要插入的新行总数作为输入参数。

Workbook 类的 [Save()][16] 方法将工作簿保存在指定为输入参数的给定文件路径中。

## 使用 C# 在 Excel 工作表中插入带格式的行 {#Insert-Rows-with-Formatting-in-Excel-Worksheets-using-CSharp}

您可以按照以下提到的步骤以编程方式在 Excel 工作表中插入带格式的行：

  * 使用输入文件路径创建 [Workbook][12] 类的实例。
  * 创建 [Worksheet][13] 类的实例。
  * 通过索引访问 [Worksheets][14] 集合中的工作表。
  * 创建 [InsertOptions][22] 类的实例。
  * 设置 [CopyFormatType][23] 属性
  * 使用行索引、要插入的总行数调用 [InsertRows()][24] 方法并传递 _InsertOptions_。
  * 使用输出文件路径调用 _[Save()][16]_ 方法。

以下代码示例显示**如何使用 C# 在 Excel 工作表中插入带格式的行**。

```
// 实例化工作簿对象
// 通过文件流打开Excel文件
Workbook workbook = new Workbook(@"C:\Files\Book1.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.Worksheets[0];

// 设置格式选项
InsertOptions insertOptions = new InsertOptions();
insertOptions.CopyFormatType = CopyFormatType.SameAsAbove;

// 在工作表的第三个位置插入一行
worksheet.Cells.InsertRows(2, 1, insertOptions);

// 保存修改后的 Excel 文件
workbook.Save(@"C:\Files\output.xlsx");
```

API 的 [InsertOptions][22] 类表示插入行或列时的选项。该类的[CopyFormatType][23]属性表示插入行时复制格式的类型，支持以下类型：

  * SameAsAbove — 允许复制与上述行相同的格式。
  * SameAsBelow — 允许复制与下一行相同的格式。
  * 清除 — 允许清除格式。

## 使用 C# 从 Excel 工作表中删除行 {#Delete-Rows-from-Excel-Worksheets-using-CSharp}

您可以按照以下步骤以编程方式从 Excel 工作表中删除行：

  * 使用输入文件路径创建 [Workbook][12] 类的实例。
  * 创建 [Worksheet][13] 类的实例。
  * 通过索引访问 [Worksheets][14] 集合中的工作表。
  * 通过调用 [DeleteRows()][25] 方法删除行并传递要删除的行索引和总行数。
  * 使用输出文件路径调用 _[Save()][16]_ 方法。

以下代码示例显示了**如何使用 C#** 从 Excel 工作表中删除行。

```
// 实例化工作簿对象
// 通过文件流打开Excel文件
Workbook workbook = new Workbook(@"C:\Files\Book1.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.Worksheets[0];

// 从第 3 行开始在工作表中删除 10 行
worksheet.Cells.DeleteRows(2, 10);

// 保存修改后的 Excel 文件
workbook.Save(@"C:\Files\output.xlsx");
```

[Cells][20] 类的 [DeleteRow()][26] 方法允许删除指定索引处的单行。同样，[DeleteRows()][25] 方法允许删除多于一行。它需要从哪里开始删除行的行索引和要删除的总行数作为输入参数。

## 使用 C# 在 Excel 工作表中插入列 {#Insert-Columns-in-Excel-Worksheets-using-CSharp}

您可以按照以下提到的步骤以编程方式在 Excel 工作表中插入列：

  * 使用输入文件路径创建 [Workbook][12] 类的实例。
  * 创建 [Worksheet][13] 类的实例。
  * 通过索引访问 [Worksheets][14] 集合中的工作表。
  * 通过调用 [InsertColumn()][27] 方法插入一列，并将列索引传递到插入新列的位置。
  * 使用输出文件路径调用 _[Save()][16]_ 方法。

以下代码示例展示了**如何使用 C#** 在 Excel 工作表中插入列。

```
// 实例化工作簿对象
// 通过文件流打开Excel文件
Workbook workbook = new Workbook(@"C:\Files\Book1.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.Worksheets[0];

// 在工作表的第二个位置插入一列
worksheet.Cells.InsertColumn(1);

// 保存修改后的 Excel 文件
workbook.Save(@"C:\Files\output.xlsx");
```

{{< figure align=center src="images/Insert-Column-in-Excel-Worksheets-using-CSharp-1024x332.jpg" alt="使用 C# 在 Excel 工作表中插入单列" caption="使用 C# 在 Excel 工作表中插入单个列。">}}
 
同样，您可以使用下面给出的代码示例在 Excel 工作表中插入多列：

```
// 实例化工作簿对象
// 通过文件流打开Excel文件
Workbook workbook = new Workbook(@"C:\Files\Book1.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.Worksheets[0];

// 从第二个位置开始将 5 列插入工作表
worksheet.Cells.InsertColumns(2, 5);

// 保存修改后的 Excel 文件
workbook.Save(@"C:\Files\output.xlsx");
```

{{< figure align=center src="images/Insert-Columns-in-Excel-Worksheets-using-CSharp-1024x430.jpg" alt="使用 C# 在 Excel 工作表中插入多列。" caption="使用 C# 在 Excel 工作表中插入多列。">}}
 
为了在 Excel 工作表中插入列，[Cells][20] 类提供了 [InsertColumns()][30] 方法来在工作表中插入多个列。它采用从哪里开始插入列的列索引和要插入的新列的总数作为输入参数。 Cells 类还提供了 [InsertColumn()][27] 方法在指定索引处插入单个列。

## 使用 C# 从 Excel 工作表中删除列 {#Delete-Columns-from-Excel-Worksheets-using-CSharp}

您可以按照以下提到的步骤以编程方式从 Excel 工作表中删除列：

  * 使用输入文件路径创建 [Workbook][12] 类的实例。
  * 创建 [Worksheet][13] 类的实例。
  * 通过索引访问 [Worksheets][14] 集合中的工作表。
  * 通过调用 [DeleteColumn()][31] 方法删除一列，并将列索引传递给删除。
  * 使用输出文件路径调用 _[Save()][16]_ 方法。

以下代码示例显示了**如何使用 C#** 从 Excel 工作表中删除列。

```
// 实例化工作簿对象
// 通过文件流打开Excel文件
Workbook workbook = new Workbook(@"C:\Files\Book1.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.Worksheets[0];

// 从工作表中删除第三列
worksheet.Cells.DeleteColumn(2);

// 保存修改后的 Excel 文件
workbook.Save(@"C:\Files\output.xlsx");
```

同样，您可以使用以下代码示例从 Excel 工作表中删除多个列。

```
// 实例化工作簿对象
// 通过文件流打开Excel文件
Workbook workbook = new Workbook(@"C:\Files\Book1.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.Worksheets[0];

// 从工作表中从第 3 列开始删除 5 列
worksheet.Cells.DeleteColumns(2, 5, false);

// 保存修改后的 Excel 文件
workbook.Save(@"C:\Files\output.xlsx");
```

[DeleteColumns()][32] 方法允许一次删除多个列。它需要三个参数，一个从哪里开始删除列的列索引，作为输入参数要删除的列总数，以及一个 true 或 false 值来指示是否更新其他工作表中的引用。同样，[Cells][20] 类的 [DeleteColumn()][31] 方法允许删除指定索引处的单个列。

## 获得免费许可证
您可以通过请求 [免费的临时许可证][33] 来试用该 API，而不受评估限制。

## 结论
在本文中，您学习了**如何使用 C# 在 Excel 文件中插入行或列**。您还学习了**如何以编程方式从 Excel 文件中删除行和列**。此外，您还学习了**如何在 Excel 工作表中插入多行或多列**。此外，您还学习了**如何使用 C#从 Excel 文件中删除多行或多列**。您可以使用 [文档][34] 了解更多关于 Aspose.Cells for .NET API 的信息。如有任何歧义，请随时在 [论坛][35] 上与我们联系。

## 也可以看看

  * [使用 C# 在 Excel 工作表中隐藏和显示行或列][36]
  * [使用 C# 删除 Excel 中的空白行和列][37]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/insert-or-delete-rows-and-columns-in-excel-using-csharp.jpg
 [2]: #CSharp-API-to-Insert-or-Delete-Rows-and-Columns
 [3]: #Insert-Rows-in-Excel-Worksheets-using-CSharp
 [4]: #Insert-Rows-with-Formatting-in-Excel-Worksheets-using-CSharp
 [5]: #Delete-Rows-from-Excel-Worksheets-using-CSharp
 [6]: #Insert-Columns-in-Excel-Worksheets-using-CSharp
 [7]: #Delete-Columns-from-Excel-Worksheets-using-CSharp
 [8]: https://docs.fileformat.com/spreadsheet/xlsx/
 [9]: https://products.aspose.com/cells/net/
 [10]: https://downloads.aspose.com/cells/net
 [11]: https://www.nuget.org/packages/aspose.cells
 [12]: https://apireference.aspose.com/cells/net/aspose.cells/workbook
 [13]: https://apireference.aspose.com/cells/net/aspose.cells/worksheet
 [14]: https://apireference.aspose.com/cells/net/aspose.cells/workbook/properties/worksheets
 [15]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/insertrows
 [16]: https://apireference.aspose.com/cells/net/aspose.cells.workbook/save/methods/2
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Insert-Multiple-Rows-in-Excel-Worksheets-using-CSharp.jpg
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Insert-Rows-in-Excel-Worksheets-using-CSharp.jpg
 [19]: https://apireference.aspose.com/cells/net/aspose.cells/worksheet/properties/cells
 [20]: https://apireference.aspose.com/cells/net/aspose.cells/cells
 [21]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/insertrow
 [22]: https://apireference.aspose.com/cells/net/aspose.cells/insertoptions
 [23]: https://apireference.aspose.com/cells/net/aspose.cells/insertoptions/properties/copyformattype
 [24]: https://apireference.aspose.com/cells/net/aspose.cells.cells/insertrows/methods/1
 [25]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/deleterows
 [26]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/deleterow
 [27]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/insertcolumn
 [28]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Insert-Column-in-Excel-Worksheets-using-CSharp.jpg
 [29]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Insert-Columns-in-Excel-Worksheets-using-CSharp.jpg
 [30]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/insertcolumns
 [31]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/deletecolumn
 [32]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/deletecolumns
 [33]: https://purchase.aspose.com/temporary-license
 [34]: https://docs.aspose.com/cells/net/
 [35]: https://forum.aspose.com/c/cells/9
 [36]: https://blog.conholdate.com/2021/09/28/hide-and-show-rows-or-columns-in-excel-using-csharp/
 [37]: https://blog.conholdate.com/2020/12/25/delete-blank-rows-and-columns-in-excel-using-csharp/








