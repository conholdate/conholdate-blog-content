---
title: 'How to Edit Excel Sheet Programmatically in Node.js'
author: Muhammad Mustafa
date: 2022-05-06T07:56:46+00:00
summary: "Use a robust Node.js library to learn **How to edit Excel sheet in Node.js programmatically**. Search & replace data, edit specific cells using Node.js."
url: /2022/05/06/how-to-edit-excel-sheet-programmatically-in-nodejs/
categories:
  - Conholdate.Cells Product Family
tags:
  - How to edit Spreadsheet
  - Node.js edit Excel file
  - Node.js Excel library
  - How to Edit Excel Sheet in Node.js
  - Node.js edit Excel file

---


{{< figure align=center src="images/How-to-Edit-Excel-Sheet-in-Nodejs.png" alt="How to Edit Excel Sheet in Node.js" caption="How to Edit Excel Sheet in Node.js">}}

[MS Excel][1] is an integral component of any business operational structure as it offers a stack of rich features such as data entry, complex calculations, data analysis, report generation, task management, and many more. Users can perform financial analysis and then visualize the data using charts. Moreover, data changes occur so often, and Excel spreadsheets need to be updated to reflect those changes. However, we can save time by automating this whole process. In this article, we will learn **how to edit Excel Sheet in Node.js programmatically.**

We will cover the following topics in this article:


  * [Node.js library to edit Excel file][2]
  * [Search and replace in Excel using Node.js][3]
  * [How to edit cells in Excel programmatically?][4]
  * [Clear data from Excel spreadsheet][5]


## Node.js library to edit Excel file {#Nodejs-library-to-edit-Excel-file}

Please run the following commands to set up the [**Node.js Excel library**][6] to start editing Excel spreadsheets programmatically. 

```
npm install aspose.cells
```
```
npm install java
```

Please follow this [blog post][7] to know about the complete setup info and pre-requisites. Also, you may explore the [library][8], as there is comprehensive documentation available regarding usage.

**Note: You must have a source XLSX file in the root directory of your project as we have placed the "sample.xlsx" file in this tutorial.**


## Search and replace in Excel using Node.js {#Search-and-replace-in-Excel-using-Nodejs}

The search and replace method offers a great deal when there is a huge amount of data stored in an Excel spreadsheet. However, the following are the steps and code snippet to perform this action programmatically:

  1. Import and create an object of the [Cells][9] class.
  2. Instantiates the [WorkBook][10] child class with an XLSX file.
  3. Call the [replace(placeHolder, newValue)][11] method to search a value and replace it with a new value.
  4. Save the file using [save(fileName)][12] method.

{{< gist conholdate-gists 1157cf4321ac86dd6cca73bc2735c71c "How-to-Edit-Excel-Sheet-in-Nodejs.js" >}}

Now, start the server and you will see the output as shown below in the image.

{{< figure align=center src="images/Edit-Excel-Sheet-in-Nodejs.png" alt="How to Edit Excel Sheet in Node.js" caption="How to Edit Excel Sheet in Node.js">}}

## How to edit cells in Excel programmatically? {#How-to-edit-cells-in-Excel-programmatically}

[Node.js Excel library][6] also lets you update a value in a specific cell of an Excel sheet. Follow the following steps to achieve this functionality in your Node.js file:

  1. Create an object of the [Cells][9] class.
  2. Create an object of the [WorkBook][10] child class by instantiating it with an XLSX file.
  3. Access the workbook, get the cells by calling the getCells() method and call [putValue(string)][13] method to update a specific cell(i.e. B2) of the Excel sheet.
  4. Call the [save(fileName)][12] method to save the file.

  {{< gist conholdate-gists 5e90bb7352fc7fbedfa3e6a61a26524d "How-to-Edit-Excel-Sheet-in-Nodejs.js" >}}

  The out of this code snippet will be something like shown in the image below.

  {{< figure align=center src="images/how-to-edit-spreadsheet.png" alt="how to edit spreadsheet" caption="how to edit spreadsheet">}}

## Clear data from Excel spreadsheet {#Clear-data-from-Excel-spreadsheet}

In this section, we will learn how can we clear data from an Excel sheet using Node.js programmatically. We will perform the following steps:

  1. Create an object of the [Cells][9] class.
  2. Instantiates [WorkBook][10] child class with an XLSX file.
  3. Call the [clear()][14] method to clear all cell and row objects.
  4. Call the [save(fileName)][12] method to save the file.

{{< gist conholdate-gists 44bc96798dbf6ae039981c701fffe786 "clear-data-from-Excel-spreadsheet.js" >}}

Start the server and you may see the output shown in the image below.

{{< figure align=center src="images/ Nodejs-Excel-library.png" alt=" Nodej.s Excel library" caption=" Nodej.s Excel library">}}

## Get a Free License

You may use [a free temporary license][17] to use Aspose.Cells for Node.js without evaluation limitations.

## Conclusion

 This brings us to the end of this blog post. We have gone learned **how to edit Excel Sheet in Node.js programmatically**. We have used the [Node.js Excel library][6] to edit a specific cell and clear the file data. There are many further methods available [here][25] that you may explore and practice yourself. Further, [conholdate.com][26] is consistently writing on new topics. Therefore, please stay connected for regular updates. 

## Ask a question

Feel free to visit our [forum][18] which is very active to respond to questions and queries/discussions.

## See Also

  * [Import XML into Excel in Node.js][21]
  * [Convert CSV into Excel using Node.js][22]

 [1]: https://docs.fileformat.com/spreadsheet/_xlsx/
 [2]: #Nodejs-library-to-edit-Excel-file
 [3]: #Search-and-replace-in-Excel-using-Nodejs
 [4]: #How-to-edit-cells-in-Excel-programmatically
 [5]: #Clear-data-from-Excel-spreadsheet
 [6]: https://apireference.aspose.com/cells/nodejs
 [7]: https://blog.conholdate.com/2022/04/25/import-xml-into-excel-in-nodejs/
 [8]: https://apireference.aspose.com/cells/nodejs
 [9]: https://apireference.aspose.com/cells/nodejs/cells
 [10]: https://apireference.aspose.com/cells/nodejs/Workbook
 [11]: https://apireference.aspose.com/cells/nodejs/Workbook#replace
 [12]: https://apireference.aspose.com/cells/nodejs/Workbook#save
 [13]: https://apireference.aspose.com/cells/net/aspose.cells.gridweb.data/webcell/methods/putvalue/index
 [14]: https://apireference.aspose.com/cells/nodejs/Cells#clear
 [15]: https://apireference.aspose.com/cells/nodejs/Workbook#.createWorkbookFromStream
 [16]: https://apireference.aspose.com/cells/nodejs/Workbook#save
 [17]: https://purchase.conholdate.com/temporary-license
 [18]: https://forum.conholdate.com/
 [19]: https://blog.conholdate.com/2022/02/17/search-data-in-excel-using-java/
 [20]: https://www.conholdate.com/
 [21]: https://blog.conholdate.com/2022/04/25/import-xml-into-excel-in-nodejs/
 [22]: https://blog.conholdate.com/2022/04/28/convert-csv-into-excel-using-nodejs/
 [23]: https://nodejs.dev/learn/the-nodejs-fs-module
 [24]: https://apireference.aspose.com/cells/nodejs/Cells#getCell
 [25]: https://apireference.aspose.com/cells/nodejs
 [26]: https://conholdate.com/