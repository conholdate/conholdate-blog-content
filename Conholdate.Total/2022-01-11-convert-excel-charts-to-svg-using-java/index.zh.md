---
title: "使用 Java 将 Excel 图表转换为 SVG"
author: Muzammil Khan
date: 2022-01-11T05:11:47+00:00
summary: "作为 Java 开发人员，您可以通过编程轻松地将 Excel 工作簿中的数据图表转换为 SVG 文件。在本文中，您将学习**如何使用 Java 将 Excel 图表转换为 SVG**。"
url: /zh/2022/01/11/convert-excel-charts-to-svg-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "Aspose.Cells 对于 Java"
  - "在 Java 中将图表转换为 SVG"
  - "将 Excel 图表转换为 SVG"
  - "将 Excel 图表转换为 SVG in Java"
  - "在 Java 中将图表导出为 SVG"
  - "用于转换 Excel 图表的 Java API"

---


{{< figure align=center src="images/convert-excel-charts-to-svg-using-java.jpg" alt="使用 Java 将 Excel 图表转换为 SVG">}}
 

[SVG (_Scalable Vector Graphics_)][2] 是一种基于 XML 的矢量图像格式，它以二维矢量图形格式存储图像。 SVG 图像也可以使用任何文本编辑器进行编辑。我们可以通过编程将 Excel 工作簿中的数据图表转换为 SVG 文件。在本文中，我们将学习**如何使用 Java 将 Excel 图表转换为 SVG**。

本文将涵盖以下主题：

  * [Java API 将 Excel 图表转换为 SVG][3]
  * [在 Java 中将 Excel 图表转换为 SVG][4]
  * [导出图表并缩放 SVG 以适应视口][5] 

## Java API 将 Excel 图表转换为 SVG {#Java-API-to-Convert-Excel-Charts-to-SVG}

为了将图表从 [XLSX][6] 文件转换为 SVG，我们将使用 [Aspose.Cells for Java][7] API。它允许以编程方式执行 Excel 自动化功能，而无需 Microsoft Excel 应用程序。请[下载][8] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置。

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
    <version>21.12</version>
</dependency>
```

## 在 Java 中将 Excel 图表转换为 SVG {#Convert-Excel-Charts-to-SVG-in-Java}

我们可以按照以下步骤将图表从 Excel 工作表转换为 SVG：

  1. 首先，使用 [**_Workbook_**][9] 类加载一个 Excel 文件。
  2. 接下来，通过索引（从零开始）或名称访问具有要从工作表集合转换的图表的工作表。
  3. 然后，访问图表以从图表集合中按其索引（从零开始）进行转换。
  4. 之后，将 **_ImageOrPrintOptions.setSaveFormat_** 设置为 SVG。
  5. 最后，使用 [**_Chart.toImage()_**][10] 方法将图表转换为 SVG 并保存输出文件。

以下示例代码展示了**如何使用 Java 将图表从 Excel 转换为 SVG**。

```
// 此代码示例演示如何将图表从 Excel 转换为 SVG
// 在工作簿对象中加载 Excel 文件
Workbook workbook = new Workbook("C:\\Files\\Cells\\Sample_Chart.xlsx");

// 访问第一个工作表
Worksheet worksheet = workbook.getWorksheets().get(0);

// 访问工作表中的第一个图表
Chart chart = worksheet.getCharts().get(0);

// 将图表保存为 SVG 格式的图像
ImageOrPrintOptions options = new ImageOrPrintOptions();
options.setSaveFormat(SaveFormat.SVG);

chart.toImage("C:\\Files\\Cells\\Sample_Chart_out.svg", options);
```

{{< figure align=center src="images/Convert-Excel-Charts-to-SVG-in-Java-1024x576.jpg" alt="在 Java 中将 Excel 图表转换为 SVG" caption="在 Java 中将 Excel 图表转换为 SVG。">}}
 

## 导出图表并缩放 SVG 以适应 Java 中的视口 {#Export-Chart-and-Scale-SVG-to-Fit-Viewport-in-Java}

在 XML 中，**viewBox** 属性定义了 SVG 视口内容的位置和尺寸。我们可以将 Excel 工作表中的任何图表导出为 SVG，并按照以下步骤将其设置为适合视口：

  1. 首先，使用 [**_Workbook_**][9] 类加载一个 Excel 文件。
  2. 接下来，通过索引（从零开始）或名称访问具有要从工作表集合转换的图表的工作表。
  3. 然后，访问图表以从图表集合中按其索引（从零开始）导出。
  4. 将 **_ImageOrPrintOptions.setSaveFormat_** 设置为 SVG。
  5. 之后，将 **_ImageOrPrintOptions.setSVGFitToViewPort_** 设置为 true。
  6. 最后调用[**_Chart.toImage()_**][10]方法保存输出文件。

以下示例代码展示了**如何使用 Java 将图表从 Excel 导出到 SVG 以适应视口**。

```
// 此代码示例演示如何将图表从 Excel 转换为 SVG 并将其设置为适合视口
// 在工作簿对象中加载 Excel 文件
Workbook workbook = new Workbook("C:\\Files\\Cells\\Sample_Chart.xlsx");

// 访问第一个工作表
Worksheet worksheet = workbook.getWorksheets().get(0);

// 访问工作表中的第一个图表
Chart chart = worksheet.getCharts().get(0);

// 设置图像或打印选项
// 使用 SVGFitToViewPort 为真
ImageOrPrintOptions options = new ImageOrPrintOptions();
options.setSaveFormat(SaveFormat.SVG);
options.setSVGFitToViewPort(true);

chart.toImage("C:\\Files\\Cells\\Sample_Chart_ViewPort_out.svg", options);
```

{{< figure align=center src="images/Export-Chart-and-Scale-SVG-to-Fit-Viewport-in-Java-1024x512.jpg" alt="导出图表并缩放 SVG 以适应 Java 中的视口" caption="导出图表并缩放 SVG 以适应 Java 中的视口。">}}
 

## 获得免费许可证

请通过申请 [免费的临时许可证][13] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了**如何在 Java 中将图表从 Excel 转换为 SVG**。我们还看到了**如何以编程方式将 Excel 图表导出到 SVG 以适应视口**。此外，您可以使用 [documentation][14] 了解有关 Aspose.Cells for Java API 的更多信息。如有任何歧义，请随时在 [论坛][15] 上与我们联系。

## 也可以看看

  * [在 Java 中将数据导出到 Excel][16]
  * [使用 Java 删除 Excel 中的空白行和列][17]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/convert-excel-charts-to-svg-using-java.jpg
 [2]: https://docs.fileformat.com/page-description-language/svg/
 [3]: #Java-API-to-Convert-Excel-Charts-to-SVG
 [4]: #Convert-Excel-Charts-to-SVG-in-Java
 [5]: #Export-Chart-and-Scale-SVG-to-Fit-Viewport-in-Java
 [6]: https://docs.fileformat.com/spreadsheet/xlsx/
 [7]: https://products.aspose.com/cells/java/
 [8]: https://downloads.aspose.com/cells/java
 [9]: https://apireference.aspose.com/cells/java/com.aspose.cells/workbook
 [10]: https://apireference.aspose.com/cells/java/com.aspose.cells/chart#toImage(java.lang.String,%20com.aspose.cells.ImageOrPrintOptions)
 [11]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/Convert-Excel-Charts-to-SVG-in-Java.jpg
 [12]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/Export-Chart-and-Scale-SVG-to-Fit-Viewport-in-Java.jpg
 [13]: https://purchase.conholdate.com/temporary-license
 [14]: https://docs.aspose.com/cells/java/
 [15]: https://forum.aspose.com/c/cells/9
 [16]: https://blog.conholdate.com/2021/08/27/export-data-to-excel-in-java/
 [17]: https://blog.conholdate.com/2021/11/23/delete-blank-rows-and-columns-in-excel-using-java/







