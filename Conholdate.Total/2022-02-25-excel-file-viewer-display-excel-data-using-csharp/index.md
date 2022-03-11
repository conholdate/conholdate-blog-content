---
title: 'Excel File Viewer – Display Excel Data using C#'
author: Muzammil Khan
date: 2022-02-25T06:43:17+00:00
summary: 'As a C# developer, you can render and view Excel files in HTML, PDF, or as an image programmatically in .NET applications. In this article, you will learn **how to create an Excel file viewer and display Excel data using C#**.'
url: /2022/02/25/excel-file-viewer-display-excel-data-using-csharp/
categories:
  - Conholdate.Total Product Family
tags:
  - 'C# Excel File Viewer'
  - 'Display Excel Data using C#'
  - Excel to HTML
  - Excel to Image
  - Excel to PDF
  - GroupDocs.Viewer for .NET
  - 'Render Excel as Image in C#'
  - 'Render Excel as PDF in C#'
  - 'Render Excel Files in C#'
  - 'Render Excel to HTML in C#'

---


{{< figure align=center src="images/excel-file-viewer-display-excel-data-using-csharp.jpg" alt="Excel File Viewer – Display Excel Data using C#">}}
 

We can display data from Excel files in HTML, PDF, or as an image programmatically in .NET applications. It allows showing data to others without sharing the actual Excel files. In this article, we will learn how to create an **Excel file viewer** and **display Excel data** using **C#**.

The following topics shall be covered in this article:

  * [C# Excel File Viewer API — Free Download][2]
  * [Display Excel Data in HTML using C#][3]
  * [Render Excel Data in PDF using C#][4]
  * [View Excel File as JPG Image using C#][5]
  * [Adjust Text Overflow in Cells using C#][6]
  * [Render Hidden Rows and Columns of Excel][7] 
  * [Skip Empty Rows and Columns in Excel][8]
  * [Split Excel Worksheet by Rows and Columns][9]

## C# Excel File Viewer API — Free Download {#CSharp-Excel-File-Viewer-API-Free-Download}

For displaying data from [XLS][10] or [XLSX][11] spreadsheets, we will be using [GroupDocs.Viewer for .NET][12] API. It allows rendering and viewing of [supported spreadsheet formats][13] programmatically. Please either [download][14] the DLL of the API or install it using [NuGet][15].

```
PM> Install-Package GroupDocs.Viewer
```

## Display Excel Data in HTML using C# {#Display-Excel-Data-in-HTML-using-CSharp}

We can render the Excel file and display data in HTML by following the simple steps given below:

  1. Firstly, load an Excel file using the _**[Viewer][16]** _class.
  2. Create an instance of the [_**HtmlViewOptions**_ ][17]class for [**_EmbeddedResources_**][18].
  3. Provide the output file path as an argument.
  4. Optionally, set various view options, such as _[RenderToSinglePage][19]_.
  5. Finally, call the _**[View()][20]**_ method and pass _HtmlViewOptions_ as an argument.

The following code sample shows **how to render an Excel file in HTML using C#**.

{{< gist conholdate-gists 5055558b7d8d9486f8abc485e108bd5c "ExcelFileViewer_CSharp_RenderInHTML.cs" >}}

{{< figure align=center src="images/Display-Excel-Data-in-HTML-using-CSharp-1024x512.jpg" alt="Display Excel Data in HTML using C#." caption="Display Excel Data in HTML using C#.">}}
 

## Render Excel Data in PDF using C# {#Render-Excel-Data-in-PDF-using-CSharp}

We can render the Excel file and display data in PDF by following the steps given below:

  1. Firstly, load an Excel file using the [Viewer](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer) class.
  2. Create an instance of the [PdfViewOptions](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions) class.
  3. Provide the output file path as an argument.
  4. Finally, call the [View()](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view) method and pass **PdfViewOptions** as an argument.

The following code sample shows **how to render an Excel file in PDF using C#**.

{{< gist conholdate-gists 5055558b7d8d9486f8abc485e108bd5c "ExcelFileViewer_CSharp_RenderInPDF.cs" >}}

{{< figure align=center src="images/Render-Excel-Data-in-PDF-using-CSharp-1024x512.jpg" alt="Render Excel Data in PDF using C#." caption="Render Excel Data in PDF using C#.">}}
 

## View Excel File as JPG Image using C# {#View-Excel-File-as-JPG-Image-using-CSharp}

We can render the Excel file and display data as JPG images by following the steps given below:

  1. Firstly, load an Excel file using the [Viewer](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer) class.
  2. Create an instance of the [JpgViewOptions](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/jpgviewoptions) class.
  3. Provide the output file path.
  4. Finally, call the [View()](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view) method and pass **JpgViewOptions** as an argument.

The following code sample shows **how to render an Excel file as JPG using C#**.

{{< gist conholdate-gists 5055558b7d8d9486f8abc485e108bd5c "ExcelFileViewer_CSharp_RenderInJPG.cs" >}}

{{< figure align=center src="images/View-Excel-File-as-JPG-Image-using-CSharp-1024x582.jpg" alt="View Excel File as JPG Image using C#." caption="View Excel File as JPG Image using C#.">}}
 
Similarly, we can also render an Excel file to PNG images as shown below:

{{< gist conholdate-gists 5055558b7d8d9486f8abc485e108bd5c "ExcelFileViewer_CSharp_RenderInPNG.cs" >}}

## Adjust Text Overflow in Cells using C# {#Adjust-Text-Overflow-in-Cells-using-CSharp}

We can adjust the text-overflow in cells while rendering an Excel worksheet. The API provides the following types of overflow adjustments:

  * _Overlay_ – Overlay next cells even they are not empty.
  * _OverlayIfNextIsEmpty_ – Overlay next cells only if they are empty.
  * _AutoFitColumn_ – Expand columns to fit the text.
  * _HideText_ – Hide overflow text.

Please follow the steps given below to adjust the text-overflow:

  1. Firstly, load an Excel file using the _**[Viewer][16]** _class.
  2. Create an instance of [_**PdfViewOptions**_ ][24]class
  3. Provide the output file path.
  4. Set TextOverflowMode property of SpreadsheetOptions to _HideText_.
  5. Optionally, set RenderHeadings and RenderGridLines to true.
  6. Finally, call the _**[View()][20]**_ method and pass _PdfViewOptions_ as an argument.

The following code sample shows **how to adjust text-overflow while rendering an Excel file using C#**.

{{< gist conholdate-gists 5055558b7d8d9486f8abc485e108bd5c "ExcelFileViewer_CSharp_AdjustTextOverflow.cs" >}}

{{< figure align=center src="images/Adjust-Text-Overflow-in-Cells-using-CSharp-1024x512.jpg" alt="Adjust Text Overflow in Cells using C#." caption="Adjust Text Overflow in Cells using C#.">}}
 
## Render Hidden Rows and Columns of Excel {#Render-Hidden-Rows-and-Columns-of-Excel}

We can render the hidden rows and columns of an Excel worksheet by following the steps mentioned earlier. However, we just need to set the following properties to true at step # 4:

```
viewOptions.SpreadsheetOptions.RenderHiddenColumns = true;
viewOptions.SpreadsheetOptions.RenderHiddenRows = true;
```

The following code sample shows **how to show hidden rows and columns of an Excel file in PDF using C#**.

{{< gist conholdate-gists 5055558b7d8d9486f8abc485e108bd5c "ExcelFileViewer_CSharp_RenderHiddenRows.cs" >}}

{{< figure align=center src="images/Render-Hidden-Rows-and-Columns-of-Excel-1024x512.jpg" alt="Render Hidden Rows and Columns of Excel." caption="Render Hidden Rows and Columns of Excel.">}}
 

## Skip Empty Rows and Columns in Excel using C# {#Skip-Empty-Rows-and-Columns-in-Excel-using-CSharp}

We can skip the rendering of empty rows and columns while viewing the Excel worksheet by following the steps mentioned earlier. However, we just need to set the following properties to true at step # 4:

```
viewOptions.SpreadsheetOptions.SkipEmptyColumns = true;
viewOptions.SpreadsheetOptions.SkipEmptyRows = true;
```

The following code sample shows **how to skip the rendering of empty rows and columns of an Excel file using C#**.

{{< gist conholdate-gists 5055558b7d8d9486f8abc485e108bd5c "ExcelFileViewer_CSharp_SkipEmpty.cs" >}}

{{< figure align=center src="images/Skip-Empty-Rows-and-Columns-in-Excel-using-CSharp-1024x512.jpg" alt="Skip Empty Rows and Columns in Excel using C#" caption="Skip Empty Rows and Columns in Excel using C#.">}}
 

## Split Excel Worksheet by Rows and Columns {#Split-Excel-Worksheet-by-Rows-and-Columns}

We can render large Excel worksheets and split them by the number of rows and columns on one page. We can split the worksheet by following the steps given below:

  1. Firstly, load an Excel file using the _**[Viewer][16]** _class.
  2. Create an instance of [_**PdfViewOptions**_ ][24]class
  3. Provide the output file path.
  4. Initialize _SpreadsheetOptions_ using the _ForSplitSheetIntoPages_ method. It takes count of rows and columns per page as arguments.
  5. Finally, call the _**[View()][20]**_ method and pass _PdfViewOptions_ as an argument.

The following code sample shows **how to split an Excel worksheet by rows and columns using C#**.

{{< gist conholdate-gists 5055558b7d8d9486f8abc485e108bd5c "ExcelFileViewer_CSharp_SplitWorksheet.cs" >}}

{{< figure align=center src="images/Split-Excel-Worksheet-by-Rows-and-Columns-1024x603.jpg" alt="Split Excel Worksheet by Rows and Columns" caption="Split Excel Worksheet by Rows and Columns.">}}
 

## Get a Free License

Please try the API without evaluation limitations by requesting [a free temporary license][29].

## Conclusion

In this article, we have learned how to:

  * render or view Excel worksheets in HTML, PDF, PNG, and JPG using C#;
  * adjust text overflow in Cells of Excel and render grid lines;
  * display headings of Excel columns and rows;
  * skip empty rows/columns and show hidden rows and columns;
  * limit display of worksheets by rows and columns.

Besides, you can learn more about GroupDocs.Viewer for .NET API using the [documentation][30]. In case of any ambiguity, please feel free to contact us on the [forum][31].

## See Also

  * [Insert or Delete Rows and Columns in Excel using C#][32]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/excel-file-viewer-display-excel-data-using-csharp.jpg
 [2]: #CSharp-Excel-File-Viewer-API-Free-Download
 [3]: #Display-Excel-Data-in-HTML-using-CSharp
 [4]: #Render-Excel-Data-in-PDF-using-CSharp
 [5]: #View-Excel-File-as-JPG-Image-using-CSharp
 [6]: #Adjust-Text-Overflow-in-Cells-using-CSharp
 [7]: #Render-Hidden-Rows-and-Columns-of-Excel
 [8]: #Skip-Empty-Rows-and-Columns-in-Excel-using-CSharp
 [9]: #Split-Excel-Worksheet-by-Rows-and-Columns
 [10]: https://docs.fileformat.com/spreadsheet/xls/
 [11]: https://docs.fileformat.com/spreadsheet/xlsx/
 [12]: https://products.groupdocs.com/viewer/net
 [13]: https://docs.groupdocs.com/viewer/net/view-excel-spreadsheets/#supported-spreadsheets-formats
 [14]: https://downloads.groupdocs.com/viewer/net
 [15]: https://www.nuget.org/packages/groupdocs.viewer
 [16]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
 [17]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
 [18]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options.htmlviewoptions/forembeddedresources/methods/4
 [19]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions/properties/rendertosinglepage
 [20]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
 [21]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Display-Excel-Data-in-HTML-using-CSharp.jpg
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Render-Excel-Data-in-PDF-using-CSharp.jpg
 [23]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/View-Excel-File-as-JPG-Image-using-CSharp.jpg
 [24]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
 [25]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Adjust-Text-Overflow-in-Cells-using-CSharp.jpg
 [26]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Render-Hidden-Rows-and-Columns-of-Excel.jpg
 [27]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Skip-Empty-Rows-and-Columns-in-Excel-using-CSharp.jpg
 [28]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Split-Excel-Worksheet-by-Rows-and-Columns.jpg
 [29]: https://purchase.conholdate.com/temporary-license
 [30]: https://docs.groupdocs.com/viewer/net/
 [31]: https://forum.groupdocs.com/c/viewer/9
 [32]: https://blog.conholdate.com/2021/10/06/insert-or-delete-rows-and-columns-in-excel-using-csharp/
