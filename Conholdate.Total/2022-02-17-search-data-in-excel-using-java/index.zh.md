---
title: "使用 Java 在 Excel 中搜索数据"
author: Muzammil Khan
date: 2022-02-17T07:34:30+00:00
summary: "您可以在 Java 应用程序中以编程方式在 Excel 电子表格中轻松搜索包含特定数据值或字符串的单元格。在本文中，您将学习**如何使用 Java 在 Excel 中搜索数据**。"
url: /zh/2022/02/17/search-data-in-excel-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "文本搜索 API"
  - "区分大小写的搜索"
  - "使用 Java 在 Excel 中查找公式"
  - "查找文本"
  - "查找文本 in Excel using Java"
  - "搜索单元格"
  - "在 Excel 中搜索公式"
  - "在 Excel 中搜索文本"

---


{{< figure align=center src="images/search-data-in-excel-using-java.jpg" alt="使用 Java 在 Excel 中搜索数据">}}
 

Excel 电子表格允许以表格形式存储大量数据。在某些情况下，我们可能需要从存储的数据中搜索包含特定数据值或字符串的单元格。尽管 Excel 提供了搜索所有电子表格的内置功能，但我们可能需要在 Java 应用程序中以编程方式执行搜索操作。在本文中，我们将学习**如何使用 Java 在 Excel 中搜索数据**。

本文将涵盖以下主题：

  * [用于在 Excel 中搜索数据的 Java API][2]
  * [使用 Java 在 Excel 中查找特定文本][3]
  * [查找以特定字母开头的文本][4]
  * [搜索以特定字母结尾的文本][5]
  * [查找包含特定字母的文本][6]
  * [使用 Java 在 Excel 中使用正则表达式进行搜索][7]
  * [使用 Java 在 Excel 中进行区分大小写的搜索][8]
  * [使用 Java 在 Excel 中搜索公式][9]

## 用于在 Excel 中搜索数据的 Java API

我们将使用 [Aspose.Cells for Java][10] API 对 [XLSX][11] 文件执行搜索操作。它允许以编程方式执行 Excel 自动化功能，而无需 Microsoft Excel 应用程序。请[下载][12] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置。

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
    <version>22.1</version>
</dependency>
```

## 使用 Java 在 Excel 中查找特定文本 {#Find-Specific-Text-in-Excel-using-Java}

我们可以按照以下步骤在 Excel 文件中搜索任何文本、数字或日期值：

  * 首先，使用 [**_Workbook_**][13] 类加载一个 Excel 文件。
  * 接下来，访问 Excel 文件中的第一个 [worksheet][14]。
  * 然后，获取访问工作表的[cells][15]。
  * 接下来，创建 **_[FindOptions][16]_** 类的实例。
  * 之后，将 **_[LookAtType][17]_** 设置为“_ENTIRE_CONTENT_”。
  * 最后，使用 **_[Cells.find()][18]_** 方法查找文本。它需要搜索字符串和 **_FindOptions_** 作为参数。

以下代码示例展示了**如何使用 Java 在 Excel 文件中查找特定文本。**

```
// 加载 Excel 文件
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.getWorksheets().get(0);

// 获取 CellCollections 中的所有单元格
Cells cells = worksheet.getCells();

// 初始化 FindOptions
FindOptions findOptions = new FindOptions();

// 查找包含字符串值的单元格
findOptions.setLookAtType(LookAtType.ENTIRE_CONTENT);
Cell cell = cells.find("A Company", null, findOptions);

// 显示单元格名称及其值
System.out.println("Name of the cell containing String: " + cell.getName());
System.out.println("the cell value is: " + cell.getValue());
```

{{< figure align=center src="images/Find-Specific-Text-in-Excel-using-Java-1024x455.jpg" alt="使用 Java 在 Excel 中查找特定文本" caption="使用 Java 在 Excel 中查找特定文本。">}}
 

## 查找以特定字母开头的文本 {#Find-Text-Starting-with-Specific-Letters}

我们可以按照上述步骤搜索以特定字母开头的任何文本值。但是，我们只需要将 **_LookAtType_** 设置为“_START_WITH_”。

以下代码示例显示了如何使用 Java 在 Excel 文件中查找以字母“H”开头的特定文本。

```
// 加载 Excel 文件
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.getWorksheets().get(0);

// 获取 CellCollections 中的所有单元格
Cells cells = worksheet.getCells();

// 初始化 FindOptions
FindOptions findOptions = new FindOptions();

// 查找包含字符串值的单元格
findOptions.setLookAtType(LookAtType.START_WITH);
Cell cell = cells.find("H", null, findOptions);

// 显示单元格名称及其值
System.out.println("Name of the cell containing String: " + cell.getName());
System.out.println("the cell value is: " + cell.getValue());
```

{{< figure align=center src="images/Find-Text-Starting-with-Specific-Letters-1024x463.jpg" alt="" caption="Find Text Starting with Specific Letters.">}}
 

## 搜索以特定字母结尾的文本 {#Search-Text-Ending-with-Specific-Letters}

我们可以按照上述步骤搜索以特定字母结尾的任何文本值。但是，我们只需要将 **_LookAtType_** 设置为“_END_WITH_”。

以下代码示例显示了如何使用 Java 在 Excel 文件中查找以字母“any”结尾的特定文本。

```
// 加载 Excel 文件
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.getWorksheets().get(0);

// 获取 CellCollections 中的所有单元格
Cells cells = worksheet.getCells();

// 初始化 FindOptions
FindOptions findOptions = new FindOptions();

// 查找包含字符串值的单元格
findOptions.setLookAtType(LookAtType.ENDS_WITH);
Cell cell = cells.find("any", null, findOptions);

// 显示单元格名称及其值
System.out.println("Name of the cell containing String: " + cell.getName());
System.out.println("the cell value is: " + cell.getValue());
```

## 查找包含特定字母的文本 {#Find-Text-Containing-Specific-Letters}

我们可以按照上述步骤搜索包含任何特定子字符串的任何文本值。但是，我们只需要将 **_LookAtType_** 设置为“_CONTAINS_”。

以下代码示例显示了如何使用 Java 在 Excel 文件中查找包含“comp”的文本。

```
// 加载 Excel 文件
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.getWorksheets().get(0);

// 获取 CellCollections 中的所有单元格
Cells cells = worksheet.getCells();

// 初始化 FindOptions
FindOptions findOptions = new FindOptions();

// 查找包含字符串值的单元格
findOptions.setLookAtType(LookAtType.CONTAINS);
Cell cell = cells.find("comp", null, findOptions);

// 显示单元格名称及其值
System.out.println("Name of the cell containing String: " + cell.getName());
System.out.println("the cell value is: " + cell.getValue());
```

## 使用 Java 在 Excel 中使用正则表达式进行搜索 {#Search-with-Regular-Expression-in-Excel-using-Java}

我们还可以按照上述步骤使用正则表达式搜索单元格值。但是，我们只需要将 **_Regex Key_** 设置为 true，并将 **_LookAtType_** 设置为“_CONTAINS_”。

以下代码示例展示了**如何使用 Java 在 Excel 文件中使用正则表达式查找文本**。

```
// 加载 Excel 文件
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.getWorksheets().get(0);

// 获取 CellCollections 中的所有单元格
Cells cells = worksheet.getCells();

// 初始化 FindOptions
FindOptions findOptions = new FindOptions();

// 将其定义为正则表达式
findOptions.setRegexKey(true);
findOptions.setLookAtType(LookAtType.ENTIRE_CONTENT);
findOptions.setLookInType(LookInType.VALUES);
Cell cell = cells.find("[a-z]{1}[\\s]&[\\s][a-z]{1}", null, opt);

// 显示单元格名称及其值
System.out.println("Name of the cell containing String: " + cell.getName());
System.out.println("the cell value is: " + cell.getValue());
```

{{< figure align=center src="images/Search-with-Regular-Expression-in-Excel-using-Java-1024x465.jpg" alt="使用 Java 在 Excel 中使用正则表达式进行搜索" caption="使用 Java 在 Excel 中使用正则表达式进行搜索。">}}
 

## 使用 Java 在 Excel 中进行区分大小写的搜索 {#Case-Sensitive-Search-in-Excel-using-Java}

我们可以按照上述步骤执行搜索操作并查找任何区分大小写的文本字符串。但是，我们只需要将 **_CaseSensitive_** 属性设置为 true。

以下代码示例展示了**如何使用 Java 在 Excel 文件中查找区分大小写的文本**。

```
// 加载 Excel 文件
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.getWorksheets().get(0);

// 获取 CellCollections 中的所有单元格
Cells cells = worksheet.getCells();

// 初始化 FindOptions
FindOptions findOptions = new FindOptions();

// 查找包含公式的单元格
findOptions.setCaseSensitive(true);
findOptions.setLookAtType(LookAtType.CONTAINS);
Cell cell = cells.find("Ltd", null, findOptions);

// 显示单元格名称及其值
System.out.println("Name of the cell containing String: " + cell.getName());
System.out.println("the cell value is: " + cell.getValue());
```

## 使用 Java 在 Excel 中搜索公式 {#Search-Formula-in-Excel-using-Java}

我们可以按照以下步骤在 Excel 文件中搜索包含公式的单元格：

  * 首先，使用 [**_Workbook_**][13] 类加载一个 Excel 文件。
  * 接下来，访问 Excel 文件中的第一个工作表。
  * 然后，获取访问工作表的单元格。
  * 接下来，创建 **_FindOptions_** 类的实例。
  * 之后，将 **_[LookInType][22]_** 设置为“__FORMULAS__”。
  * 最后，使用 Cells.find() 方法查找文本。它需要搜索字符串和 **_FindOptions_** 作为参数。

以下代码示例展示了**如何使用 Java 在 Excel 文件中查找公式单元格。**

```
// 加载 Excel 文件
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// 访问 Excel 文件中的第一个工作表
Worksheet worksheet = workbook.getWorksheets().get(0);

// 获取 CellCollections 中的所有单元格
Cells cells = worksheet.getCells();

// 初始化 FindOptions
FindOptions findOptions = new FindOptions();

// 查找包含公式的单元格
findOptions.setLookInType(LookInType.FORMULAS);
Cell cell = cells.find("=SUM(C2:C10)", null, findOptions);

// 显示单元格名称及其值
System.out.println("Name of the cell containing String: " + cell.getName());
System.out.println("the cell value is: " + cell.getValue());
```

{{< figure align=center src="images/Search-Formula-in-Excel-using-Java-1024x453.jpg" alt="使用 Java 在 Excel 中搜索公式。" caption="使用 Java 在 Excel 中搜索公式。">}}
 

## 获得免费许可证

请通过请求 [免费的临时许可证][24] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了**如何使用 Java 在 Excel 中查找文本或公式**。具体来说，我们已经学习了**如何在 Excel 中以编程方式搜索任何开始、结束或包含特定字母的文本**。我们还看到了**如何在 Excel 文件中使用正则表达式进行搜索**。此外，您可以使用 [documentation][25] 了解更多关于 Aspose.Cells for Java API 的信息。如有任何歧义，请随时在 [论坛][26] 上与我们联系。

## 也可以看看

  * [在 Java 中的 Excel 中查找和替换文本][27]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/search-data-in-excel-using-java.jpg
 [2]: #
 [3]: #Find-Specific-Text-in-Excel-using-Java
 [4]: #Find-Text-Starting-with-Specific-Letters
 [5]: #Search-Text-Ending-with-Specific-Letters
 [6]: #Find-Text-Containing-Specific-Letters
 [7]: #Search-with-Regular-Expression-in-Excel-using-Java
 [8]: #Case-Sensitive-Search-in-Excel-using-Java
 [9]: #Search-Formula-in-Excel-using-Java
 [10]: https://products.aspose.com/cells/java/
 [11]: https://docs.fileformat.com/spreadsheet/xlsx/
 [12]: https://downloads.aspose.com/cells/java
 [13]: https://apireference.aspose.com/cells/java/com.aspose.cells/workbook
 [14]: https://apireference.aspose.com/cells/java/com.aspose.cells/Worksheet
 [15]: https://apireference.aspose.com/cells/java/com.aspose.cells/Cells
 [16]: https://apireference.aspose.com/cells/java/com.aspose.cells/FindOptions
 [17]: https://apireference.aspose.com/cells/java/com.aspose.cells/LookAtType
 [18]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#find(java.lang.Object,%20com.aspose.cells.Cell,%20com.aspose.cells.FindOptions)
 [19]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Find-Specific-Text-in-Excel-using-Java.jpg
 [20]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Find-Text-Starting-with-Specific-Letters.jpg
 [21]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Search-with-Regular-Expression-in-Excel-using-Java.jpg
 [22]: https://apireference.aspose.com/cells/java/com.aspose.cells/LookInType
 [23]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Search-Formula-in-Excel-using-Java.jpg
 [24]: https://purchase.conholdate.com/temporary-license
 [25]: https://docs.aspose.com/cells/java/
 [26]: https://forum.aspose.com/c/cells/9
 [27]: https://blog.aspose.com/2020/12/08/find-and-replace-text-in-spreadsheets-using-java/







