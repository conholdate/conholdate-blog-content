---
title: "使用 Java 删除 Excel 中的空白行和列"
author: Muzammil Khan
date: 2021-11-23T10:48:02+00:00
summary: "作为 Java 开发人员，您可以轻松地从 Excel 工作表中删除空白行和列。在本文中，您将学习**如何使用 Java 删除 Excel 中的空白行和列**。"
url: /zh/2021/11/23/delete-blank-rows-and-columns-in-excel-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 Java 删除 Excel 中的空白列"
  - "在 Java 中删除空白行和列"
  - "删除空白行列"
  - "使用 Java 删除 Excel 中的空白行"

---


{{< figure align=center src="images/delete-blank-rows-and-columns-in-excel-using-java.jpg" alt="使用 Java 删除 Excel 中的空白行和列">}}
 

我们可以通过编程轻松地从 Excel 工作表中删除空白行和列。在本文中，我们将学习**如何使用 Java 删除 Excel 中的空白行和列**。

本文将涵盖以下主题：

  * [用于删除 Excel 中的空白行和列的 Java API][2]
  * [使用 Java 删除 Excel 中的空白行][3]
  * [使用 Java 删除 Excel 中的空白列][4]
  * [删除空白行和列时自动更新参考][5]

## 用于删除 Excel 中的空白行和列的 Java API {#Java-API-to-Delete-Blank-Rows-and-Columns-in-Excel}

为了从 [XLSX][6] 文件中删除空白行和列，我们将使用 [Aspose.Cells for Java][7] API。请[下载][8] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置。

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
    <version>21.11</version>
</dependency>
```

## 使用 Java 删除 Excel 中的空白行 {#Delete-Blank-Rows-in-Excel-using-Java}

我们可以按照以下步骤以编程方式从 Excel 工作表中删除空白行：

  * 首先，使用 [Workbook][9] 类加载一个 Excel 文件。
  * 接下来，调用 [Workbook.getWorksheets()][10] 方法并在 [WorksheetCollection][11] 对象中获取工作表。
  * 然后，按索引（从零开始）或按名称访问具有空白行的工作表。
  * 之后，调用 [Cells.deleteBlankRows()][12] 方法从访问的工作表中删除空白行。
  * 最后，调用带有输出文件路径的[save()][13]方法保存输出文件。

以下示例代码展示了**如何使用 Java 从 Excel 中删除空白行**。

```
// 加载现有的 Excel 文件。
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample_rows_cols.xlsx");

// 获取电子表格中的工作表集合。
WorksheetCollection sheets = workbook.getWorksheets();

// 通过索引从 WorksheetCollection 中获取第一个 Worksheet。
Worksheet sheet = sheets.get(0);
// 或按名称。
// 工作表 sheet = sheet.get("Sheet1");

// 从工作表中删除空白行。
sheet.getCells().deleteBlankRows();

// 保存更新的 Excel 文件。
workbook.save("C:\\Files\\Cells\\output.xlsx");
```

{{< figure align=center src="images/Delete-Blank-Rows-in-Excel-using-Java-1024x457.jpg" alt="使用 Java 删除 Excel 中的空白行。" caption="使用 Java 删除 Excel 中的空白行。">}}
 

同样，我们可以从 Excel 文档中的所有工作表中删除空白行。我们将简单地遍历 WorksheetCollection 并在每个工作表上调用 [deleteBlankRows()][12] 方法，如以下代码示例所示：

```
// 打开现有的 Excel 文件。
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample_rows_cols.xlsx");

// 获取工作表集合
WorksheetCollection worksheets = workbook.getWorksheets();

// 遍历工作表。
for (int i=0; i<worksheets.getCount(); i++)
{
    // Access worksheets one by one
    Worksheet sheet = worksheets.get(i);
  
    // Delete the Blank Rows from the worksheet.
    sheet.getCells().deleteBlankRows();
}

// 保存更新的 Excel 文件。
workbook.save("C:\\Files\\Cells\\output.xlsx");
```

## 使用 Java 删除 Excel 中的空白列 {#Delete-Blank-Columns-in-Excel-using-Java}

我们可以按照以下步骤以编程方式从 Excel 工作表中删除空白列：

  * 首先，使用 [Workbook][9] 类加载一个 Excel 文件。
  * 接下来，调用 [Workbook.getWorksheets()][10] 方法并在 [WorksheetCollection][11] 对象中获取工作表。
  * 然后，通过索引（从零开始）或名称访问具有空白列的工作表。
  * 之后，调用 [Cells.deleteBlankColumns()][15] 方法从访问的工作表中删除空白列。
  * 最后，调用带有输出文件路径的[save()][13]方法保存输出文件。

以下示例代码显示了**如何使用 Java 从 Excel 中删除空白列**。

```
// 打开现有的 Excel 文件。
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample_rows_cols.xlsx");

// 获取电子表格中的工作表集合。
WorksheetCollection sheets = workbook.getWorksheets();

// 通过索引从 WorksheetCollection 中获取第一个 Worksheet。
Worksheet sheet = sheets.get(2);

// 删除空白列。
sheet.getCells().deleteBlankColumns(options);

// 保存更新的 Excel 文件。
workbook.save("C:\\Files\\Cells\\output_DeleteBlankColumns.xlsx");	
```

{{< figure align=center src="images/Delete-Blank-Columns-in-Excel-using-Java-1024x457.jpg" alt="使用 Java 删除 Excel 中的空白列。" caption="使用 Java 删除 Excel 中的空白列。">}}
 

## 删除空白行和列时自动更新参考 {#Update-References-Automatically-while-Deleting-Blank-Rows-and-Columns}

删除空白行或列可能会破坏公式、图表和表格中的引用。例如，Sheet2 中的单元格 A1 有一个公式 **=Sheet1!C7** 引用第一个工作表的单元格 C7，如下图所示。

{{< figure align=center src="images/A-cell-A1-in-Sheet2-is-referring-to-a-value-of-cell-C7-in-Sheet1-1024x542.jpg" alt="Sheet2 中的单元格 A1 引用 Sheet1 中单元格 C7 的值。" caption="Sheet2 中的单元格 A1 引用 Sheet1 中单元格 C7 的值。">}}
 

If we remove blank rows in Sheet1, the value of **C7 (650000)** will be moved to cell C6. 但公式 (=Sheet1!C7) 不会更新，单元格 A1 将显示 C7 的值，在这种情况下为 **550000**。我们可以通过将 [DeleteOptions.setUpdateReference][18] 设置为 **true** 来避免这个问题。它将确保在删除空白行时更新引用。

我们可以按照以下步骤以编程方式从 Excel 工作表中删除空白行时自动更新引用：

  * 首先，使用 [Workbook][9] 类加载一个 Excel 文件。
  * 接下来，调用 [Workbook.getWorksheets()][10] 方法并在 [WorksheetCollection][11] 对象中获取工作表。
  * 然后，按索引（从零开始）或按具有空白行的名称访问工作表。
  * 接下来，创建 [DeleteOptions][19] 类的实例
  * 然后，调用 [setUpdateReferences()][18] 为真。它将在删除空白行的同时更新其他工作表中的引用。
  * 之后，使用 DeleteOptions 对象作为参数调用 [Cells.deleteBlankRows()][12] 方法，以从访问的工作表中删除空白行。
  * 最后，调用带有输出文件路径的[save()][13]方法保存输出文件。

以下示例代码显示**如何在删除 Excel 中的空白行时更新引用**。

```
// 打开现有的 Excel 文件。
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample_rows_cols.xlsx");

// 获取电子表格中的工作表集合。
WorksheetCollection sheets = workbook.getWorksheets();

// 通过索引从 WorksheetCollection 中获取第一个 Worksheet。
Worksheet sheet = sheets.get(0);

// 此选项将确保引用（在公式、图表中）
// 在删除空白行时更新。
DeleteOptions options = new DeleteOptions();
options.setUpdateReference(true);

// 从工作表中删除空白行。
sheet.getCells().deleteBlankRows(options);

// 保存更新的 Excel 文件。
workbook.save("C:\\Files\\Cells\\output_UpdateReferencesAutomatically.xlsx");
```

同样，我们可以在删除 Excel 中的空白列的同时更新引用。但是，我们只需要使用 DeleteOptions 作为参数调用 [deleteBlankColumns()][20] 方法。

## 获得免费许可证

请通过申请 [免费的临时许可证][21] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了**如何使用 Java 删除 Excel 中的行和列**。我们还看到了**如何在以编程方式删除行和列的同时更新引用**。此外，您可以使用 [documentation][22] 了解有关 Aspose.Cells for Java API 的更多信息。如有任何歧义，请随时在 [论坛][23] 上与我们联系。

## 也可以看看

  * [在 Java 中将数据导出到 Excel][24]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/delete-blank-rows-and-columns-in-excel-using-java.jpg
 [2]: #Java-API-to-Delete-Blank-Rows-and-Columns-in-Excel
 [3]: #Delete-Blank-Rows-in-Excel-using-Java
 [4]: #Delete-Blank-Columns-in-Excel-using-Java
 [5]: #Update-References-Automatically-while-Deleting-Blank-Rows-and-Columns
 [6]: https://docs.fileformat.com/spreadsheet/xlsx/
 [7]: https://products.aspose.com/cells/java/
 [8]: https://downloads.aspose.com/cells/java
 [9]: https://apireference.aspose.com/cells/java/com.aspose.cells/workbook
 [10]: https://apireference.aspose.com/cells/java/com.aspose.cells/workbook#Worksheets
 [11]: https://apireference.aspose.com/cells/java/com.aspose.cells/WorksheetCollection
 [12]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#deleteBlankRows()
 [13]: https://apireference.aspose.com/cells/java/com.aspose.cells/workbook#save(java.lang.String)
 [14]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/Delete-Blank-Rows-in-Excel-using-Java.jpg
 [15]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#deleteBlankColumns()
 [16]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/Delete-Blank-Columns-in-Excel-using-Java.jpg
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/A-cell-A1-in-Sheet2-is-referring-to-a-value-of-cell-C7-in-Sheet1.jpg
 [18]: https://apireference.aspose.com/cells/java/com.aspose.cells/deleteoptions#UpdateReference
 [19]: https://apireference.aspose.com/cells/java/com.aspose.cells/DeleteOptions
 [20]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#deleteBlankColumns(com.aspose.cells.DeleteOptions)
 [21]: https://purchase.conholdate.com/temporary-license
 [22]: https://docs.aspose.com/cells/java/
 [23]: https://forum.aspose.com/c/cells/9
 [24]: https://blog.conholdate.com/2021/08/27/export-data-to-excel-in-java/








