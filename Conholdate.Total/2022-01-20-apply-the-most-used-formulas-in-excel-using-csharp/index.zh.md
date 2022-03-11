---
title: "'使用 C# 在 Excel 中应用最常用的公式'"
author: Muzammil Khan
date: 2022-01-20T10:41:26+00:00
summary: "作为 C# 开发人员，您可以轻松地以编程方式在 Excel 工作表中执行 Excel 支持的公式。在本文中，您将学习**如何使用 C# 在 Excel 中应用最常用的公式**。"
url: /zh/2022/01/20/apply-the-most-used-formulas-in-excel-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "计算 Excel 公式"
  - "Excel 公式"
  - "C# 中的 Excel 公式"
  - "公式计算"
  - "使用 C# 在 Excel 中的公式"
  - "Excel 中最常用的公式"
  - "C#中的百分比公式"
---


{{< figure align=center src="images/most-used-formulas-in-excel-using-csharp.jpg" alt="使用 C# 的 Excel 中最常用的公式">}}
 
Excel 是最流行和广泛使用的电子表格应用程序之一。它提供了一个内置功能来应用各种公式/函数来处理数据。这些公式有助于执行不同类型的计算或计算。公式是计算单元格值的表达式。 Excel 还提供了预定义公式的函数，这些函数很容易使用。在本文中，我们将学习**如何使用 C# 在 Excel 中应用最常用的公式**。

本文将涵盖以下主题：

  * [C# API 在 Excel 中执行最常用的公式][2]
  * [使用 C# 计算 Excel 中的单元格][3]
  * [使用 C# 在 Excel 中求和函数][4]
  * [使用 C# 在 Excel 中计算平均值][5]
  * [Excel中的IF函数使用C#][6]
  * [Excel中的百分比公式使用C#][7]

## C# API 在 Excel 中执行最常用的公式 {#CSharp-API-to-Execute-Most-Used-Formulas-in-Excel}

我们将使用 [Aspose.Cells for .NET][8] API 来使用 [XLSX][9] 文件中的公式。它支持大量的数学、字符串、布尔值、日期/时间、统计、数据库、查找和参考 [公式][10]。请[下载][11] API 的 DLL 或使用 [NuGet][12] 安装它。

```
PM> Install-Package Aspose.Cells
```

## 使用 C# 计算 Excel 中的单元格 {#Count-Cells-in-Excel-using-CSharp}

COUNT 函数计算提供的包含数字的范围内的单元格数。我们可以按照以下步骤以编程方式使用计数公式：

  1. 首先，使用 [Workbook][13] 类加载一个 Excel 文件。
  2. 接下来，通过索引（从零开始）或名称访问 [worksheet][14]。
  3. 然后，为通过其名称访问的 [cell][16] 设置 [formula][15]。
  4. 之后调用函数[CalculateFormula()][17]计算公式结果。
  5. 最后，使用 [Save()][18] 方法保存 Excel 文件。它将输出文件路径作为参数。

以下代码示例展示了**如何使用 C#** 在 Excel 中执行 COUNT** 公式。

```
// 此代码示例演示如何在 Excel 中使用 COUNT 函数。
// 加载现有的 Excel 文件
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// 通过传递工作表索引来访问工作表
Worksheet worksheet = workbook.Worksheets[0];

// 向单元格添加公式
worksheet.Cells["B12"].Formula = "=COUNT(B1:B11)";

// 计算公式的结果
workbook.CalculateFormula();

// 保存 Excel 文件
workbook.Save("C:\\Files\\Cells\\output_Count.xlsx");
```

{{< figure align=center src="images/Count-Cells-in-Excel-using-CSharp-1024x618.jpg" alt="使用 C# 计算 Excel 中的单元格。" caption="使用 C# 计算 Excel 中的单元格。">}}
 
同样，我们可以使用 COUNTA 函数来计算所有不为空的单元格。在这种情况下，COUNTA 函数应返回 10。

## 使用 C# 在 Excel 中求和函数 {#SUM-Function-in-Excel-using-CSharp}

Excel 中的 SUM 函数将给定范围内的所有值相加。请按照前面提到的步骤计算值的总和。但是，我们只需要在第 3 步设置 SUM 公式。

以下代码示例显示**如何使用 C# 在 Excel 中应用 SUM 公式**。

```
// 此代码示例演示如何在 Excel 中使用 SUM 函数。
// 加载现有的 Excel 文件
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// 通过传递工作表索引来访问工作表
Worksheet worksheet = workbook.Worksheets[0];

// 向单元格添加公式
worksheet.Cells["B12"].Formula = "=SUM(B2:B11)";

// 计算公式的结果
workbook.CalculateFormula();

// 保存 Excel 文件
workbook.Save("C:\\Files\\Cells\\output_sum.xlsx");
```

{{< figure align=center src="images/SUM-Function-in-Excel-using-CSharp-1024x674.jpg" alt="使用 C# 在 Excel 中求和函数。" caption="使用 C# 在 Excel 中求和函数。">}}
 
## 使用 C# 在 Excel 中计算平均值 {#Calculate-Average-in-Excel-using-CSharp}

我们可以使用 AVERAGE 函数计算 Excel 中提供的值范围的平均值。请按照前面提到的步骤计算给定值的平均值。但是，我们只需要在第 3 步设置 AVERAGE 公式。

以下代码示例显示**如何使用 C# 在 Excel 中计算平均值**。

```
// 此代码示例演示如何在 Excel 中使用 AVERAGE 函数。
// 加载现有的 Excel 文件
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// 通过传递工作表索引来访问工作表
Worksheet worksheet = workbook.Worksheets[0];

// 向单元格添加公式
worksheet.Cells["B12"].Formula = "=AVERAGE(B2:B11)";

// 计算公式的结果
workbook.CalculateFormula();

// 保存 Excel 文件
workbook.Save("C:\\Files\\Cells\\output_average.xlsx");
```

{{< figure align=center src="images/Calculate-Average-in-Excel-using-CSharp-1024x654.jpg" alt="使用 C# 在 Excel 中计算平均值。" caption="使用 C# 在 Excel 中计算平均值。">}}
 

## Excel中的IF函数使用C# {#IF-Function-in-Excel-using-CSharp}

我们可以在 Excel 中以编程方式应用 IF 函数来检查是否满足条件。如果为真则返回一个值，如果为假则返回另一个值。请按照前面提到的步骤使用 IF 功能。但是，我们只需要在步骤 3 中设置 IF 条件。

以下代码示例显示**如何使用 C# 在 Excel 中应用 IF 函数**。

```
// 此代码示例演示如何在 Excel 中使用 IF 函数。
// 加载现有的 Excel 文件
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// 通过传递工作表索引来访问工作表
Worksheet worksheet = workbook.Worksheets[0];

// 将 SUM 公式添加到“A4”单元格
worksheet.Cells["C2"].Formula = "=IF(B2>=A2,\"Target Acheived\",\"Not Acheived\")";

// 计算公式的结果
workbook.CalculateFormula();

// 保存 Excel 文件
workbook.Save("C:\\Files\\Cells\\output_if.xlsx");
```

{{< figure align=center src="images/IF-Function-in-Excel-using-CSharp.jpg" alt="使用 C# 在 Excel 中的 IF 函数。" caption="使用 C# 在 Excel 中的 IF 函数。">}}
 

## Excel中的百分比公式使用C# {#Percentage-Formula-in-Excel-using-CSharp}

我们还可以使用基本百分比公式在 Excel 中应用百分比公式，例如，**“（部分/总计）*100”**。请按照下面提到的步骤在 Excel 中计算百分比。

  1. 首先，创建一个 [Workbook][13] 类的实例。
  2. 接下来，将新的 [Worksheet][14] 添加到新创建的 Workbook。
  3. 然后，通过索引（从零开始）或名称访问添加的工作表。
  4. 接下来，使用 [PutValue][24] 函数将值添加到所需的 [Cells][23]。
  5. 然后，为按其名称访问的单元格设置百分比 [公式][15]。
  6. 之后，调用函数[CalculateFormula()][17]计算公式结果。
  7. 最后，使用 [Save()][18] 方法保存 Excel 文件。它将输出文件路径作为参数。

以下代码示例显示**如何使用 C# 在 Excel 中应用百分比公式**。

```
// 此代码示例演示如何在 Excel 中计算百分比。
// 实例化工作簿对象
Workbook workbook = new Workbook();

// 向 Excel 对象添加新工作表
int sheetIndex = workbook.Worksheets.Add();

// 通过传递其工作表索引来获取新添加工作表的引用
Worksheet worksheet = workbook.Worksheets[0];

// 向“A1”单元格添加值
worksheet.Cells["A1"].PutValue(35000);

// 向“B1”单元格添加值
worksheet.Cells["B1"].PutValue(39000);

// 将百分比公式添加到“C1”单元格
worksheet.Cells["C1"].Formula = "=((B1-A1)/A1)*100";

// 计算公式的结果
workbook.CalculateFormula();

// 保存 Excel 文件
workbook.Save("C:\\Files\\Cells\\output_percentage.xlsx");
```

{{< figure align=center src="images/Percentage-Formula-in-Excel-using-CSharp.jpg" alt="Excel中的百分比公式使用C#" caption="Excel中使用C#的百分比公式。">}}
 

## 获得免费许可证

请通过请求 [免费的临时许可证][26] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了**如何使用 C# 在 Excel 中应用最常用的公式**。具体来说，我们学习了**如何以编程方式在 Excel 中计算 SUM、Count 和 Average**。我们还看到了**如何在 Excel 中应用百分比公式**。此外，您可以使用 [文档][27] 了解更多关于 Aspose.Cells for .NET API 的信息。如有任何歧义，请随时在 [论坛][28] 上与我们联系。

## 也可以看看

  * [使用 C# 在 Excel 中插入或删除行和列][29]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/most-used-formulas-in-excel-using-csharp.jpg
 [2]: #CSharp-API-to-Execute-Most-Used-Formulas-in-Excel
 [3]: #Count-Cells-in-Excel-using-CSharp
 [4]: #SUM-Function-in-Excel-using-CSharp
 [5]: #Calculate-Average-in-Excel-using-CSharp
 [6]: #IF-Function-in-Excel-using-CSharp
 [7]: #Percentage-Formula-in-Excel-using-CSharp
 [8]: https://products.aspose.com/cells/net/
 [9]: https://docs.fileformat.com/spreadsheet/xlsx/
 [10]: https://docs.aspose.com/cells/net/supported-formula-functions/
 [11]: https://downloads.aspose.com/cells/net
 [12]: https://www.nuget.org/packages/aspose.cells
 [13]: https://apireference.aspose.com/cells/net/aspose.cells/workbook
 [14]: https://apireference.aspose.com/cells/net/aspose.cells/worksheet
 [15]: https://apireference.aspose.com/cells/net/aspose.cells/cell/properties/formula
 [16]: https://apireference.aspose.com/cells/net/aspose.cells/cells
 [17]: https://apireference.aspose.com/cells/net/aspose.cells/workbook/methods/calculateformula
 [18]: https://apireference.aspose.com/cells/net/aspose.cells.workbook/save/methods/2
 [19]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/Count-Cells-in-Excel-using-CSharp.jpg
 [20]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/SUM-Function-in-Excel-using-CSharp.jpg
 [21]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/Calculate-Average-in-Excel-using-CSharp.jpg
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/IF-Function-in-Excel-using-CSharp.jpg
 [23]: https://apireference.aspose.com/cells/net/aspose.cells/cell
 [24]: https://apireference.aspose.com/cells/net/aspose.cells.cell/putvalue/methods/3
 [25]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/Percentage-Formula-in-Excel-using-CSharp.jpg
 [26]: https://purchase.conholdate.com/temporary-license
 [27]: https://docs.aspose.com/cells/net/
 [28]: https://forum.aspose.com/c/cells/9
 [29]: https://blog.conholdate.com/2021/10/06/insert-or-delete-rows-and-columns-in-excel-using-csharp/







