---
title: Search Data in Excel using Java
author: Muzammil Khan
date: 2022-02-17T07:34:30+00:00
summary: 'You can easily search cells containing specific data values or strings in Excel Spreadsheets programmatically in Java applications. In this article, you will learn **how to search data in Excel using Java**.'
url: /2022/02/17/search-data-in-excel-using-java/
categories:
  - Conholdate.Total Product Family
tags:
  - API for Searching Text
  - Case-Sensitive Search
  - Find Formula in Excel using Java
  - Find Text
  - Find Text in Excel using Java
  - Search Cells
  - Search Formula in Excel
  - Search Text in Excel

---


{{< figure align=center src="images/search-data-in-excel-using-java.jpg" alt="Search Data in Excel using Java">}}
 

Excel spreadsheets allow storing a huge amount of data in tabular form. In certain cases, we may need to search cells containing specific data values or strings from stored data. Although Excel provides built-in functionality to search through all the spreadsheets, we may need to perform the search operation programmatically in Java applications. In this article, we will learn **how to search data in Excel using Java**.

The following topics shall be covered in this article:

  * [Java API to Search Data in Excel][2]
  * [Find Specific Text in Excel using Java][3]
  * [Find Text Starting with Specific Letters][4]
  * [Search Text Ending with Specific Letters][5]
  * [Find Text containing Specific Letters][6]
  * [Search with Regular Expression in Excel using Java][7]
  * [Case-Sensitive Search in Excel using Java][8]
  * [Search Formula in Excel using Java][9]

## Java API to Search Data in Excel

We will be using [Aspose.Cells for Java][10] API to perform search operation on [XLSX][11] file. It allows performing Excel automation features programmatically without needing a Microsoft Excel application. Please either [download][12] the JAR of the API or just add the following **_pom.xml_** configuration in a Maven-based Java application.

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

## Find Specific Text in Excel using Java {#Find-Specific-Text-in-Excel-using-Java}

We can search any text, number, or date values in an Excel file by following the steps given below:

  * Firstly, load an Excel file using the [**_Workbook_**][13] class.
  * Next, accessing the first [worksheet][14] in the Excel file.
  * Then, get [cells][15] of the accessed sheet.
  * Next, create an instance of the **_[FindOptions][16]_** class.
  * After that, set the **_[LookAtType][17]_** as “_ENTIRE_CONTENT_”.
  * Finally, find the text using the **_[Cells.find()][18]_** method. It takes, search string and **_FindOptions_** as arguments.

The following code sample shows **how to find a specific text in an Excel file using Java.**

{{< gist conholdate-gists 445fdbbc111f880b7c60d171b59d49a6 "SearchDataInExcel_Java_FindEntireContent.java" >}}

{{< figure align=center src="images/Find-Specific-Text-in-Excel-using-Java-1024x455.jpg" alt="Find Specific Text in Excel using Java" caption="Find Specific Text in Excel using Java.">}}
 

## Find Text Starting with Specific Letters {#Find-Text-Starting-with-Specific-Letters}

We can search any text value that starts with specific letters by following the steps mentioned above. However, we just need to set **_LookAtType_** as “_START_WITH_”.

The following code sample shows how to find a specific text that starts with the letter “H” in an Excel file using Java.

{{< gist conholdate-gists 445fdbbc111f880b7c60d171b59d49a6 "SearchDataInExcel_Java_FindThatStartsWith.java" >}}

{{< figure align=center src="images/Find-Text-Starting-with-Specific-Letters-1024x463.jpg" alt="" caption="Find Text Starting with Specific Letters.">}}
 

## Search Text Ending with Specific Letters {#Search-Text-Ending-with-Specific-Letters}

We can search any text value that ends with specific letters by following the steps mentioned above. However, we just need to set **_LookAtType_** as “_END_WITH_”.

The following code sample shows how to find a specific text that ends with the letters “any” in an Excel file using Java.

{{< gist conholdate-gists 445fdbbc111f880b7c60d171b59d49a6 "SearchDataInExcel_Java_FindThatEndsWith.java" >}}

## Find Text Containing Specific Letters {#Find-Text-Containing-Specific-Letters}

We can search any text value that contains any specific substring by following the steps mentioned above. However, we just need to set **_LookAtType_** as “_CONTAINS_”.

The following code sample shows how to find a text that contains “comp” in an Excel file using Java.

{{< gist conholdate-gists 445fdbbc111f880b7c60d171b59d49a6 "SearchDataInExcel_Java_FindThatContains.java" >}}

## Search with Regular Expression in Excel using Java {#Search-with-Regular-Expression-in-Excel-using-Java}

We can also search a cell value using regular expressions by following the steps mentioned above. However, we just need to set the **_Regex Key_** to true and the **_LookAtType_** as “_CONTAINS_”.

The following code sample shows **how to find text using a regular expression in an Excel file using Java**.

{{< gist conholdate-gists 445fdbbc111f880b7c60d171b59d49a6 "SearchDataInExcel_Java_FindWithRegEx.java" >}}

{{< figure align=center src="images/Search-with-Regular-Expression-in-Excel-using-Java-1024x465.jpg" alt="Search with Regular Expression in Excel using Java" caption="Search with Regular Expression in Excel using Java.">}}
 

## Case-Sensitive Search in Excel using Java {#Case-Sensitive-Search-in-Excel-using-Java}

We can perform a search operation and find any case-sensitive text string by following the steps mentioned above. However, we just need to set the **_CaseSensitive_** property to true.

The following code sample shows **how to find a case-sensitive text in an Excel file using Java**.

{{< gist conholdate-gists 445fdbbc111f880b7c60d171b59d49a6 "SearchDataInExcel_Java_FindCaseSensitive.java" >}}

## Search Formula in Excel using Java {#Search-Formula-in-Excel-using-Java}

We can search a cell containing formula in an Excel file by following the steps given below:

  * Firstly, load an Excel file using the [**_Workbook_**][13] class.
  * Next, accessing the first worksheet in the Excel file.
  * Then, get cells of the accessed sheet.
  * Next, create an instance of the **_FindOptions_** class.
  * After that, set the **_[LookInType][22]_** as “__FORMULAS__”.
  * Finally, find the text using the Cells.find() method. It takes, search string and **_FindOptions_** as arguments.

The following code sample shows **how to find a formula cell in an Excel file using Java.**

{{< gist conholdate-gists 445fdbbc111f880b7c60d171b59d49a6 "SearchDataInExcel_Java_FindFormula.java" >}}

{{< figure align=center src="images/Search-Formula-in-Excel-using-Java-1024x453.jpg" alt="Search Formula in Excel using Java." caption="Search Formula in Excel using Java.">}}
 

## Get a Free License

Please try the API without evaluation limitations by requesting [a free temporary license][24].

## Conclusion

In this article, we have learned **how to find text or formulas in Excel using Java**. Specifically, we have learned **how to search any text in Excel that starts, ends, or contains specific letters** programmatically. We have also seen **how to search using regular expressions** in Excel files. Besides, you can learn more about Aspose.Cells for Java API using the [documentation][25]. In case of any ambiguity, please feel free to contact us on the [forum][26].

## See Also

  * [Find and Replace Text in Excel in Java][27]

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






