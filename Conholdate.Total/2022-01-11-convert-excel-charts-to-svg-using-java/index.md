---
title: Convert Excel Charts to SVG using Java
author: Muzammil Khan
date: 2022-01-11T05:11:47+00:00
summary: 'As a Java developer, you can easily convert data charts from Excel workbooks to SVG files programmatically. In this article, you will learn **how to convert Excel charts to SVG using Java**.'
url: /2022/01/11/convert-excel-charts-to-svg-using-java/
categories:
  - Conholdate.Total Product Family
tags:
  - Aspose.Cells for Java
  - Convert Charts to SVG in Java
  - Convert Excel Charts to SVG
  - Convert Excel Charts to SVG in Java
  - Export Charts to SVG in Java
  - Java API to Convert Excel Charts

---


{{< figure align=center src="images/convert-excel-charts-to-svg-using-java.jpg" alt="Convert Excel Charts to SVG using Java">}}
 

[SVG (_Scalable Vector Graphics_)][2] is an XML-based vector image format that stores an image in a two-dimensional vector graphic format. SVG images can also be edited with any text editor. We can convert data charts from Excel workbooks to SVG files programmatically. In this article, we will learn **how to convert Excel charts to SVG using Java**.

The following topics shall be covered in this article:

  * [Java API to Convert Excel Charts to SVG][3]
  * [Convert Excel Charts to SVG in Java][4]
  * [Export Chart and Scale SVG to Fit Viewport][5] 

## Java API to Convert Excel Charts to SVG {#Java-API-to-Convert-Excel-Charts-to-SVG}

For converting charts from [XLSX][6] files to SVG, we will be using [Aspose.Cells for Java][7] API.  It allows performing Excel automation features programmatically without needing a Microsoft Excel application. Please either [download][8] the JAR of the API or just add the following **_pom.xml_** configuration in a Maven-based Java application.

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

## Convert Excel Charts to SVG in Java {#Convert-Excel-Charts-to-SVG-in-Java}

We can convert charts from Excel worksheets to SVG by following the steps given below:

  1. Firstly, load an Excel file using the [**_Workbook_**][9] class.
  2. Next, access the worksheet that has a chart to convert from worksheets collection, either by its index (zero-based) or by name.
  3. Then, access the chart to convert by its index (zero-based) from charts collection.
  4. After that, set the **_ImageOrPrintOptions.setSaveFormat_** to SVG.
  5. Finally, convert the chart to SVG using the [**_Chart.toImage()_**][10] method and save the output file.

The following sample code shows **how to convert a chart from Excel to SVG using Java**.

{{< gist conholdate-gists aca03417d1b648fb7da34bc1fbe07783 "ConvertExcelChartsToSVG_Java_Convert.java" >}}

{{< figure align=center src="images/Convert-Excel-Charts-to-SVG-in-Java-1024x576.jpg" alt="Convert Excel Charts to SVG in Java" caption="Convert Excel Charts to SVG in Java.">}}
 

## Export Chart and Scale SVG to Fit Viewport in Java {#Export-Chart-and-Scale-SVG-to-Fit-Viewport-in-Java}

In XML, the **viewBox** attribute defines the position and dimension for the content of the SVG viewport. We can export any chart from Excel worksheets to SVG and set it to fit in the viewport by following the steps given below:

  1. Firstly, load an Excel file using the [**_Workbook_**][9] class.
  2. Next, access the worksheet that has a chart to convert from worksheets collection, either by its index (zero-based) or by name.
  3. Then, access the chart to export by its index (zero-based) from charts collection.
  4. Set the **_ImageOrPrintOptions.setSaveFormat_** to SVG.
  5. After that, set **_ImageOrPrintOptions.setSVGFitToViewPort_** to true.
  6. Finally, call the [**_Chart.toImage()_**][10] method to save the output file.

The following sample code shows **how to export a chart from Excel to SVG to fit in the viewport using Java**.

{{< gist conholdate-gists aca03417d1b648fb7da34bc1fbe07783 "ConvertExcelChartsToSVG_Java_FitToViewPort.java" >}}

{{< figure align=center src="images/Export-Chart-and-Scale-SVG-to-Fit-Viewport-in-Java-1024x512.jpg" alt="Export Chart and Scale SVG to Fit Viewport in Java" caption="Export Chart and Scale SVG to Fit Viewport in Java.">}}
 

## Get a Free License

Please try the API without evaluation limitations by requesting [a free temporary license][13].

## Conclusion

In this article, we have learned **how to convert a chart from Excel to SVG in Java**. We have also seen **how to export an Excel chart to SVG to fit in the viewport** programmatically. Besides, you can learn more about Aspose.Cells for Java API using the [documentation][14]. In case of any ambiguity, please feel free to contact us on the [forum][15].

## See Also

  * [Export Data to Excel in Java][16]
  * [Delete Blank Rows and Columns in Excel using Java][17]

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






