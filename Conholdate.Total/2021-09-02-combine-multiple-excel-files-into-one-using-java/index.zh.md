---
title: "使用 Java 将多个 Excel 文件合并为一个"
author: Muzammil Khan
date: 2021-09-02T05:12:15+00:00
summary: "作为一名 Java 开发人员，您可以通过编程轻松地将多个 Excel 文件合并到一个文件中。在本文中，您将学习**如何使用 Java 将多个 Excel 文件合并为一个。**"
url: /zh/2021/09/02/combine-multiple-excel-files-into-one-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 Java 合并 Excel 文件"
  - "将多个工作簿合并为一个"
  - "将多个工作表合并为一个"
  - "将列合并到单个工作表中"
  - "将特定工作表合并为一个"

---


{{< figure align=center src="images/combine-multiple-excel-files-into-one-using-java.jpg" alt="使用 Java 将多个 Excel 文件合并为一个">}}
 

您有多个 Excel 工作簿，并且希望将它们组合到一个文件中以进行报告或将数据保存在一个位置。作为一名 Java 开发人员，您可以通过编程轻松地将多个 Excel 文件合并到一个文件中。在本文中，您将学习**如何使用 Java 将多个 Excel 文件合并为一个文件**。

本文讨论/涵盖了以下主题：

  * [用于合并 Excel 文件的 Java API][2]
  * [使用 Java 将多个 Excel 文件合并为一个][3]
  * [使用 Java 将多个 Excel 文件的特定工作表合并为一个][4]
  * [使用 Java 将多个工作表合并为一个工作表][5]
  * [使用 Java 将多个工作表的列合并为一个][6]

## 用于合并 Excel 文件的 Java API {#Java-API-to-Merge-Excel-Files}

为了合并多个 [Excel][7] 文件，我将使用 [Aspose.Cells for Java API][8]。此 API 使您能够在不依赖 Microsoft Excel 的情况下创建、操作、转换、保护或打印电子表格。它允许您在 Java 应用程序中以编程方式执行 Excel 自动化功能。

您可以 [下载][9] API 的 JAR 或在您的基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置来尝试下面提到的代码示例。

```
<repository>
    <id>AsposeJavaAPI</id>
    <name>Aspose Java API</name>
    <url>https://repository.aspose.com/repo/</url>
</repository>
```

```
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-cells</artifactId>
    <version>21.8</version>
</dependency>
```

## 使用 Java 将多个 Excel 文件合并为一个 {#Combine-Multiple-Excel-Files-using-Java}

您可以按照以下提到的步骤以编程方式轻松地将多个 Excel 文件合并到一个文件中：

  * 使用第一个源文件创建 _[Workbook][10]_ 类的实例
  * 使用第二个源文件创建 _[Workbook][10]_ 类的实例
  * 重复上述步骤以合并两个以上的文件
  * 使用第二个源文件实例调用 [_combine()_][11] 方法
  * 对所有源文件一一重复上述步骤
  * 通过调用 _Workbook_ 类的 _[save()][12]_ 方法保存输出文件

以下代码示例展示了**如何使用 Java 将多个 Excel 文件合并为一个文件**。

```
// 打开第一个excel文件。
Workbook SourceBook1 = new Workbook("C:\\Files\\Quarter_1.xlsx");

// 打开第二个excel文件。
Workbook SourceBook2 = new Workbook("C:\\Files\\Quarter_2.xlsx");

// 打开第三个excel文件。
Workbook SourceBook3 = new Workbook("C:\\Files\\Quarter_3.xlsx");

// 将第二个 Excel 文件的工作表复制到第一个工作簿。
SourceBook1.combine(SourceBook2);

// 将第三个 Excel 文件的工作表复制到第一个工作簿。
SourceBook1.combine(SourceBook3);

// 将更新的第一个 excel 文件另存为新文件。
SourceBook1.save("C:\\Files\\CombinedFile.xlsx");
```

{{< figure align=center src="images/Combine-Multiple-Excel-Files-using-Java-1024x727.jpg" alt="使用 Java 将多个 Excel 文件合并为一个" caption="使用 Java 将多个 Excel 文件合并为一个">}}
 

API 的 **[Workbook][10]** 类是用于创建 Excel 电子表格的主要类。它使您能够打开和保存本机 Excel 文件。它还提供了几个使用 Excel 电子表格的属性和方法。该类的 **_[combine()][11]_** 方法将当前工作簿与另一个 Workbook 对象组合在一起。 _Workbook_ 类的**[_save()_][12]** 方法将输出文件保存在指定的文件路径。

## 使用 Java 将多个 Excel 文件的特定工作表合并为一个 {#Combine-Specific-Worksheets-of-Multiple-Excel-Files-into-One-using-Java}

您可以按照以下提到的步骤以编程方式轻松地将多个 Excel 文件中的特定工作表合并到一个文件中：

  * 为源文件 1 创建 _[Workbook][10]_ 类的实例
  * 为源文件 2 创建 _[Workbook][10]_ 类的实例
  * 重复上述步骤以组合来自两个以上文件的工作表
  * 为目标文件创建 _[Workbook][10]_ 类的实例
  * 使用 _WorksheetCollection_ 类的 _[add()][14]_ 方法添加工作表
  * 调用 _[copy()][15]_ 方法将指定工作表从源文件 1 复制到目标文件
  * 调用 _copy()_ 方法将指定工作表从源文件 2 复制到目标文件
  * 使用 _[setName()][16]_ 方法重命名目标文件中的工作表
  * 通过调用 _Workbook_ 类的 _[save()][12]_ 方法保存目标文件

以下代码示例展示了**如何使用 Java 将多个 Excel 文件中的特定工作表合并到一个文件中**。

```
String sourceFile1 = "Quarter_1.xlsx";
String sourceFile2 = "Quarter_2.xlsx";

// 打开第一个 Excel 文件。
Workbook excelA = new Workbook("C:\\Files\\" + sourceFile1);

// 打开第二个 Excel 文件。
Workbook excelB = new Workbook("C:\\Files\\" + sourceFile2);

// 创建目标工作簿。
Workbook destWorkbook = new Workbook();

// 第一个工作表默认添加到工作簿。添加第二个工作表。
destWorkbook.getWorksheets().add();

// 将第一个 Excel 文件的 Jan 工作表复制到目标文件。
destWorkbook.getWorksheets().get(0).copy(excelA.getWorksheets().get("Jan"));

// 将第二个 Excel 文件的 Jul 工作表复制到目标文件。
destWorkbook.getWorksheets().get(1).copy(excelB.getWorksheets().get("Jul"));

// 默认情况下，工作表名称分别为“Sheet1”和“Sheet2”。
// 让我们给他们起有意义的名字。
destWorkbook.getWorksheets().get(0).setName(sourceFile1 + " - Jan");
destWorkbook.getWorksheets().get(1).setName(sourceFile2 + " - Jul");

// 保存目标文件。
destWorkbook.save("C:\\Files\\CombinedSpecificSheetsInFile.xlsx");
```

{{< figure align=center src="images/Combine-Specific-Worksheets-of-Multiple-Excel-Files-into-One-using-Java-1024x561.jpg" alt="使用 Java 将多个 Excel 文件的特定工作表合并为一个" caption="使用 Java 将多个 Excel 文件的特定工作表合并为一个">}}
 

Workbook 类的 **[getWorksheets()][18]** 属性方法返回 Workbook 中所有工作表的集合。您可以使用 **[add()][14]** 方法将工作表添加到工作表集合中。

此 API 的 [**Worksheet**][19] 类表示单个工作表。它提供了几个使用工作表的属性和方法。此类的 **[copy()][20]** 方法从另一个工作表复制内容和格式。 Worksheet 类还提供 **get()** 方法来通过索引或名称获取特定工作表。 **[setName()][16]** 属性方法设置工作表的名称。

## 使用 Java 将多个工作表合并为一个工作表 {#Merge-Multiple-Worksheets-into-One-Worksheet-using-Java}

您可以按照以下提到的步骤以编程方式轻松地将 Excel 文件的多个工作表合并到一个工作表中：

  * 为源文件创建 _[Workbook][10]_ 类的实例
  * 使用 _add()_ 方法添加新工作表
  * 遍历源工作表并执行以下操作：
      * 使用 _[createRange()][21]_ 方法为一个工作表创建一系列单元格和列
      * 使用 _[copy()][22]_ 方法将数据从源范围复制到目标范围
  * 通过调用 _Workbook_ 类的 _[save()][12]_ 方法保存输出文件

以下代码示例展示了**如何使用 Java 将多个工作表合并为一个工作表**。

```
// 打开包含工作表的 Excel 文件：
// 一月、二月、三月和四月
Workbook workbook = new Workbook("C:\\Files\\Quarter_1.xlsx");

// 添加一个名为 Summary_sheet 的工作表
Worksheet summarySheet = workbook.getWorksheets().add("Summary_sheet");

// 遍历源工作表以将数据复制到
// 摘要工作表
String[] nameOfSourceWorksheets = { "Jan", "Feb", "Mar", "Apr" };
int totalRowCount = 0;

for (String sheetName : nameOfSourceWorksheets)
{
  // Get worksheet
    Worksheet sourceSheet = workbook.getWorksheets().get(sheetName);

    Range sourceRange = null;
    Range destRange = null;

    // In case of Jan worksheet, include all rows and columns.
    if (sheetName.equals("Jan"))
    {
        sourceRange = sourceSheet.getCells().getMaxDisplayRange();

        destRange = summarySheet.getCells().createRange(
                sourceRange.getFirstRow() + totalRowCount,
                sourceRange.getFirstColumn(),
                sourceRange.getRowCount(),
                sourceRange.getColumnCount());
    }
    // In case of other worksheets,
    // exclude the first row (which contains headings).
    else
    {
        int mdatarow = sourceSheet.getCells().getMaxDataRow(); // Zero-based
        int mdatacol = sourceSheet.getCells().getMaxDataColumn(); // Zero-based
        sourceRange = sourceSheet.getCells().createRange(0 + 1, 0, mdatarow, mdatacol + 1);

        destRange = summarySheet.getCells().createRange(
                sourceRange.getFirstRow() + totalRowCount -1,
                sourceRange.getFirstColumn(),
                sourceRange.getRowCount(),
                sourceRange.getColumnCount());
    }

    // Copies data, formatting, drawing objects etc. from a
    // source range to destination range.
    destRange.copy(sourceRange);
    totalRowCount = sourceRange.getRowCount() + totalRowCount;
}

// 保存工作簿 
workbook.save("C:\\Files\\Summarized.xlsx");
```

{{< figure align=center src="images/Merge-Multiple-Worksheets-into-One-Worksheet-using-Java-1024x623.jpg" alt="使用 Java 将多个工作表合并为一个工作表" caption="使用 Java 将多个工作表合并为一个工作表">}}
 

Worksheet 类的 **[getCells()][24]** 属性方法提供了工作表中可用单元格的集合。 API 的 **[Cells][25]** 类表示与单元格相关的对象的集合，例如 [Cell][26]、[Row][27] 等。 **[getMaxDisplayRange( )][28]** Cells 类的属性方法提供了包括数据、合并单元格和形状的最大范围。 **[Range][29]** 类表示电子表格中的一系列单元格。

Cells 类提供以下方法来创建一系列单元格：

  * **[createRange][21]**(int firstIndex, int number, boolean isVertical) 方法从单元格行或单元格列创建 Range 对象。
  * **[createRange][30]**(int firstRow, int firstColumn, int totalRows, int totalColumns) 方法从单元格区域创建 Range 对象。
  * **[createRange][31]**(java.lang.String address) 方法从范围的地址创建 Range 对象。
  * **[createRange][32]**(java.lang.String upperLeftCell, java.lang.String lowerRightCell) 方法从一系列单元格创建 Range 对象。

Range 类的**[copy()][22]** 方法将各种数据（包括公式）、格式、绘图对象等从源范围复制到目标范围。

## 使用 Java 将多个工作表的列合并为一个 {#Consolidate-Columns-of-Multiple-Worksheets-into-One-using-Java}

您可以按照以下提到的步骤以编程方式轻松地将多个工作表的列合并到一个工作表中：

  * 为源文件创建 _[Workbook][10]_ 类的实例
  * 使用 _add()_ 方法添加新工作表
  * 遍历源工作表并执行以下操作：
      * 使用带有源工作表单元格和列索引的 _[copyColumn()][33]_ 方法一一复制所有列
  * 通过调用 _Workbook_ 类的 _[save()][12]_ 方法保存输出文件

以下代码示例展示了**如何使用 Java 将多个工作表的列合并到一个工作表中**。

```
// 打开工作簿。
Workbook workbook = new Workbook("C:\\Files\\sample.xlsx");

// 添加一个名为 Summary_sheet 的工作表
Worksheet summarySheet = workbook.getWorksheets().add("Summary_sheet");

// 遍历工作表以将列复制到
// 摘要工作表
String[] nameOfSourceWorksheets = { "Products", "Sales", "Customers" };
int totalCol = 0; 

for (String sheetName : nameOfSourceWorksheets) {
  Worksheet sourceSheet = workbook.getWorksheets().get(sheetName);

  if (sheetName.equals("Products")) {
    // Get worksheet columns collection
    ColumnCollection columns = sourceSheet.getCells().getColumns();

    // copy column to summaySheet
    for (Column column : (Iterable<Column>) columns)
    {
      summarySheet.getCells().copyColumn(sourceSheet.getCells(), column.getIndex(), totalCol);
      totalCol = totalCol + 1;
    }
    }
  else {
    // Get worksheet columns collection
    ColumnCollection columns = sourceSheet.getCells().getColumns();

    // copy column to summaySheet
    for (Column column : (Iterable<Column>) columns)
    {
      summarySheet.getCells().copyColumn(sourceSheet.getCells(), column.getIndex(), totalCol);
      totalCol = totalCol + 1;
    }
  }
}

// 保存excel文件。
workbook.save("C:\\Files\\CopyingColumns_out.xlsx");
```

{{< figure align=center src="images/Consolidate-Columns-of-Multiple-Worksheets-into-One-using-Java-1024x527.jpg" alt="使用 Java 将多个工作表的列合并为一个" caption="使用 Java 将多个工作表的列合并为一个">}}
 

Cells 类的 **[getColumns()][35]** 属性方法提供了工作表中可用列的集合。 **[ColumnCollection][36]** 类表示工作表中各个列的集合，而 **[Column][37]** 类表示工作表中的单个列。

Cells 类的 **[copyColumn()][33]** 方法复制整列的数据和格式。 Cells 类还提供了重载的 copyColumn() 方法，以使用 PasteOptions、列号、源和目标总列等复制数据。

## 获得免费许可证

您可以通过申请 [免费的临时许可证][38] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何将多个 Excel 文件合并为一个文件**。您还学习了**如何使用 Java 组合多个 Excel 文件的特定工作表**。此外，您还学习了**如何以编程方式将多个工作表合并为一个工作表**。本文还解释了**如何使用 Java 将多个工作表的列合并为一个**。您可以使用 [documentation][39] 了解有关 Aspose.Cells for Java API 的更多信息。如有任何歧义，请随时在 [论坛][40] 上与我们联系。

## 也可以看看

  * [在 Java 中将数据导出到 Excel][41]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/combine-multiple-excel-files-into-one-using-java.jpg
 [2]: #Java-API-to-Merge-Excel-Files
 [3]: #Combine-Multiple-Excel-Files-using-Java
 [4]: #Combine-Specific-Worksheets-of-Multiple-Excel-Files-into-One-using-Java
 [5]: #Merge-Multiple-Worksheets-into-One-Worksheet-using-Java
 [6]: #Consolidate-Columns-of-Multiple-Worksheets-into-One-using-Java
 [7]: https://docs.fileformat.com/spreadsheet/xlsx/
 [8]: https://products.aspose.com/cells/java/
 [9]: https://downloads.aspose.com/cells/java
 [10]: https://apireference.aspose.com/cells/java/com.aspose.cells/Workbook
 [11]: https://apireference.aspose.com/cells/java/com.aspose.cells/workbook#combine(com.aspose.cells.Workbook)
 [12]: https://apireference.aspose.com/cells/java/com.aspose.cells/workbook#save(java.lang.String)
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Combine-Multiple-Excel-Files-using-Java.jpg
 [14]: https://apireference.aspose.com/cells/java/com.aspose.cells/worksheetcollection#add()
 [15]: https://apireference.aspose.com/cells/java/com.aspose.cells/workbook#copy(com.aspose.cells.Workbook)
 [16]: https://apireference.aspose.com/cells/java/com.aspose.cells/worksheet#Name
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Combine-Specific-Worksheets-of-Multiple-Excel-Files-into-One-using-Java.jpg
 [18]: https://apireference.aspose.com/cells/java/com.aspose.cells/workbook#Worksheets
 [19]: https://apireference.aspose.com/cells/java/com.aspose.cells/Worksheet
 [20]: https://apireference.aspose.com/cells/java/com.aspose.cells/worksheet#copy(com.aspose.cells.Worksheet)
 [21]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#createRange(int,%20int,%20boolean)
 [22]: https://apireference.aspose.com/cells/java/com.aspose.cells/range#copy(com.aspose.cells.Range)
 [23]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Merge-Multiple-Worksheets-into-One-Worksheet-using-Java.jpg
 [24]: https://apireference.aspose.com/cells/java/com.aspose.cells/worksheet#Cells
 [25]: https://apireference.aspose.com/cells/java/com.aspose.cells/Cells
 [26]: https://apireference.aspose.com/cells/java/com.aspose.cells/Cell
 [27]: https://apireference.aspose.com/cells/java/com.aspose.cells/Row
 [28]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#MaxDisplayRange
 [29]: https://apireference.aspose.com/cells/java/com.aspose.cells/Range
 [30]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#createRange(int,%20int,%20int,%20int)
 [31]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#createRange(java.lang.String)
 [32]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#createRange(java.lang.String,%20java.lang.String)
 [33]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#copyColumn(com.aspose.cells.Cells,%20int,%20int)
 [34]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Consolidate-Columns-of-Multiple-Worksheets-into-One-using-Java.jpg
 [35]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#Columns
 [36]: https://apireference.aspose.com/cells/java/com.aspose.cells/ColumnCollection
 [37]: https://apireference.aspose.com/cells/java/com.aspose.cells/Column
 [38]: https://purchase.aspose.com/temporary-license
 [39]: https://docs.aspose.com/cells/java/
 [40]: https://forum.aspose.com/c/cells/9
 [41]: https://blog.conholdate.com/2021/08/27/export-data-to-excel-in-java/








