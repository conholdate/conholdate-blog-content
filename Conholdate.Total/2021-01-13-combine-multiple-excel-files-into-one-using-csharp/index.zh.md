---
title: "'使用 C# 将多个 Excel 文件合并为一个'"
author: Muhammad Sohail
date: 2021-01-13T12:34:29+00:00
summary: "在本文中，您将学习**如何使用 C# 将多个 Excel 工作簿中的工作表复制到一个工作簿中**。您还将学习<strong>如何将多个工作表中的数据复制到一张工作表<strong>中。</strong></strong>"
url: /zh/2021/01/13/combine-multiple-excel-files-into-one-using-csharp/
categories:
  - "Conholdate.Total 产品系列"

---
在本文中，您将学习**如何使用 C# 将多个 Excel 工作簿中的工作表复制到一个工作簿中**。您还将学习**如何将多个工作表中的数据复制到一张工作表中**。开始吧。

  * [使用 C# 将多个 Excel 文件合并为一个][1]
  * [将 Excel 文件的特定工作表合并到一个工作簿中][2] 
  * [使用 C# 将多个工作表合并为一个][3]

## C# API 合并多个 Excel 文件

[Aspose.Cells for .NET][4] 是一个著名的电子表格操作 API，可让您在 .NET 应用程序中创建和处理 Excel 文件。您可以 [下载][5] API 的二进制文件或使用 [NuGet][6] 安装它。

```
PM> Install-Package Aspose.Cells
```

## 使用 C# 将多个 Excel 文件合并为一个 {#Combine-Multiple-Excel-Files}

有时，您需要将多个 Excel 文件合并为一个文件。您希望将工作表从源工作簿复制到目标工作簿，如下所示。 Excel 文档可以是任何版本，例如 Excel 97、Excel 2010 或 Excel 2016。

{{< figure align=center src="images/Combine-Excel-Documents-1.jpg" alt="使用 C# 将多个 Excel 文件合并为一个" caption="图 1：合并 Excel 文件">}}
 

以下示例代码展示了如何使用 C# 将多个 Excel 文件合并为一个。

```
// 打开第一个excel文件。
Workbook SourceBook1 = new Workbook("Excel A.xlsx");

// 打开第二个excel文件。
Workbook SourceBook2 = new Workbook("Excel B.xlsx");

// 打开第三个excel文件。
Workbook SourceBook3 = new Workbook("Excel C.xlsx");

// 将第二个 Excel 文件的工作表复制到第一个工作簿。
SourceBook1.Combine(SourceBook2);

// 将第三个 Excel 文件的工作表复制到第一个工作簿。
SourceBook1.Combine(SourceBook3);

// 将更新的第一个 excel 文件另存为新文件。
SourceBook1.Save("CombinedFile.xlsx");
```

## 使用 C# 组合 Excel 文件的特定工作表 {#Combine-Specific-Worksheets-of-Excel-Files}

上面的代码将源文件中的所有工作表复制到目标文件。但是，您可能希望将特定工作表从源文件复制到目标文件。例如，您有两个 Excel 文件，每个文件都有三个名为 Sales、Employees 和 Expenses 的工作表。您只想将销售工作表从这两个文件复制到目标文件，如下图所示。

{{< figure align=center src="images/Selective-Merging.png" alt="使用 C# 组合 Excel 文件的特定工作表" caption="图 2：结合 Excel 文件的特定工作表">}}
 

以下示例代码展示了如何使用 C# 将源文件的特定工作表合并到目标文件中。

```
// 打开 Excel A 文件。
Workbook excelA = new Workbook("Excel A.xlsx");

// 打开 Excel B 文件。
Workbook excelB = new Workbook("Excel B.xlsx");

// 创建目标工作簿。
Workbook destWorkbook = new Workbook();
// 第一个工作表默认添加到工作簿。添加第二个工作表。
destWorkbook.Worksheets.Add();

// 将 Excel A 文件的销售工作表复制到目标文件。
destWorkbook.Worksheets[0].Copy(excelA.Worksheets["Sales"]);

// 将 Excel B 文件的销售工作表复制到目标文件。
destWorkbook.Worksheets[1].Copy(excelB.Worksheets["Sales"]);

// 默认情况下，工作表名称分别为“Sheet1”和“Sheet2”。
// 让我们给他们起有意义的名字。
destWorkbook.Worksheets[0].Name = excelA.FileName + " - Sales";
destWorkbook.Worksheets[1].Name = excelB.FileName + " - Sales";

// 保存目标文件。
destWorkbook.Save("CombinedFile.xlsx");
```

## 使用 C# 将多个工作表合并为一个 {#Merge-Multiple-Worksheets-into-One}

有时，您需要将多个工作表中的数据复制到一个工作表中。例如，您在 Excel 文件中有一些工作表，其中包含有关不同产品的信息，并且您希望将这些工作表合并到一个摘要工作表中，如下所示：

{{< figure align=center src="images/merge-sheets-excel.png" alt="使用 C# 将多个工作表合并为一个" caption="图 3：将多个工作表合并为一个">}}
 

以下代码片段显示了如何使用 C# 将数据从多个工作表复制到一个工作表中。

```
// 打开包含工作表的 Excel 文件：
// 产品 1、产品 2 和产品 3
Workbook workbook = new Workbook("Products.xlsx");

// 添加一个名为 Summary_sheet 的工作表
Worksheet summarySheet = workbook.Worksheets.Add("Summary_sheet");

// 遍历要复制其数据的源工作表
// 摘要工作表
string[] nameOfSourceWorksheets = { "Products1", "Products2", "Products3" };
int totalRowCount = 0;

foreach (string sheetName in nameOfSourceWorksheets)
{
    Worksheet sourceSheet = workbook.Worksheets[sheetName];

    Range sourceRange;
    Range destRange;
    // In case of Products1 worksheet, include all rows and cols.
    if (sheetName.Equals("Products1"))
    {
        sourceRange = sourceSheet.Cells.MaxDisplayRange;
        
        destRange = summarySheet.Cells.CreateRange(
                sourceRange.FirstRow + totalRowCount,
                sourceRange.FirstColumn,
                sourceRange.RowCount,
                sourceRange.ColumnCount);
    }
    // In case of Products2 and Products3 worksheets,
    // exclude the first row (which contains headings).
    else
    {
        int mdatarow = sourceSheet.Cells.MaxDataRow; // Zero-based
        int mdatacol = sourceSheet.Cells.MaxDataColumn; // Zero-based
        sourceRange = sourceSheet.Cells.CreateRange(0 + 1, 0, mdatarow, mdatacol + 1);

        destRange = summarySheet.Cells.CreateRange(
                sourceRange.FirstRow + totalRowCount -1,
                sourceRange.FirstColumn,
                sourceRange.RowCount,
                sourceRange.ColumnCount);
    }

    // Copies data, formatting, drawing objects etc. from a
    // source range to destination range.
    destRange.Copy(sourceRange);
    totalRowCount = sourceRange.RowCount + totalRowCount;
}

// 保存工作簿 
workbook.Save("Summarized.xlsx");
```

## 结论

在本文中，您学习了如何以编程方式将多个 Excel 文件合并为一个。您可以将源文件的所有工作表或特定工作表复制到目标文件。您还学习了如何将多个工作表的数据合并到一个工作表中。请查看 [Aspose.Cells for .NET 的文档][10] 了解更多信息。如果您有任何问题，请随时在我们的 [支持论坛][11] 中提问。我们将在几个小时内回复他们。

## 也可以看看

  * [使用 C# 删除 Excel 中的空白行和列][12]
  * [使用 C# 将 Excel 文件转换为图像][13]
  * [使用 C# VB.NET 将 CSV 转换为 Excel 文件或将 Excel 转换为 CSV][14]

 [1]: #Combine-Multiple-Excel-Files
 [2]: #Combine-Specific-Worksheets-of-Excel-Files
 [3]: #Merge-Multiple-Worksheets-into-One
 [4]: https://products.aspose.com/cells/net
 [5]: https://downloads.aspose.com/cells/net
 [6]: http://nuget.org/packages/Aspose.Cells
 [7]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/01/Combine-Excel-Documents-1.jpg
 [8]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/01/Selective-Merging.png
 [9]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/01/merge-sheets-excel.png
 [10]: https://docs.aspose.com/cells/net/
 [11]: https://forum.aspose.com/
 [12]: https://blog.conholdate.com/2020/12/25/delete-blank-rows-and-columns-in-excel-using-csharp/
 [13]: https://blog.aspose.com/2021/01/01/convert-excel-files-to-images-in-csharp/
 [14]: https://blog.aspose.com/2020/11/17/csv-excel-csharp-vb-net/








