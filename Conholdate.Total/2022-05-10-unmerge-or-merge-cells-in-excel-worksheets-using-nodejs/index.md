---
title: 'UnMerge or Merge Cells in Excel Worksheets using Node.js'
author: Muhammad Mustafa
date: 2022-05-10T07:56:46+00:00
summary: "Follow this article to learn about Node.js library for unMerging or merging cells in Excel sheets. UnMerge or Merge Excel cells programmatically using Node.js."
url: /2022/05/10/unmerge-or-merge-cells-in-excel-worksheets-using-nodejs/
categories:
  - Conholdate.Cells Product Family
tags:
  - UnMerge or Merge cells in Excel Sheets using Node.js
  - UnMerge cells in Excel
  - Excel unmerge cells
  - Combine cells in Excel using Node.js
  - nodejs excel

---


{{< figure align=center src="images/Unmerge-or-Merge-Cells-in-Excel-Worksheet-using-Nodejs.png" alt="unMerge or Merge Excel cells in Node.js" caption="unMerge or Merge Excel cells in Node.js">}}

Working with [Excel sheets][1] becomes a challenging task when a huge amount of data is to be managed or manipulated. Merging or unMerging cells in an Excel worksheet is a frequent operation performed by the users. It lets you merge multiple cells and rows to place content in the center. Therefore, automating this whole process will bring efficiency and robustness and there will be no chance of data loss. However, in this blog post, we will **unMerge or merge cells in Excel sheets using Node.js**. 

We will cover the following points in this blog post:


  * [Merge Excel cells in Node.js programmatically][2]
  * [Node.js library to UnMerge cells in Excel Sheets][3]
  * [How to clear content of a range in an Excel Sheet?][4]

**Note: Place a source XLSX file in the project root directory as we have placed the “sample.xlsx” file in this article.**

## Merge Excel cells in Node.js programmatically {#Merge-cells-in-Excel-Sheets-using-Nodejs}

[Node.js Excel library][5] provides powerful methods to merge several cells of an Excel worksheet programmatically.

Following are the steps to **merge cells in an Excel Sheet using Node.js**:

  1. Instantiate an object of the [Cells][6] class.
  2. Initialize an object of the [WorkBook][7] child class with an Excel file.
  3. Access your worksheet and call the [merge(firstRow, firstColumn, totalRows, totalColumns)][8] method to merge a specified range of cells into a single cell.
  4. Call the [save(fileName)][9] method to save the file.

The following code snippet is to merge cells in an Excel Sheet programmatically.

{{< gist conholdate-gists 10e7991c5128cb8bcb7b9e7634c331b0 "merge-cells-in-Excel-Sheets-using-Nodejs.js" >}}

The output of the above code snippet can be seen below in the image.

{{< figure align=center src="images/combine-cells-in-Excel.png" alt="combine cells in Excel" caption="Combine cells in Excel using Node.js">}}


## Node.js library to UnMerge cells in Excel Sheets {#Nodejs-library-to-UnMerge-cells-in-Excel-Sheets}

Users need to unMerge multiple cells on many occasions and the **Node.js Excel library** enables you to automate this process.

We can achieve this functionality by following the steps mentioned below:

  1. Create an object of the [Cells][6] class.
  2. Initialize an object of the [WorkBook][7] child class and initialize it with an Excel file.
  3. Access your Excel sheet and call the [unMerge(firstRow, firstColumn, totalRows, totalColumns)][10] method to **unMerge cells in an Excel sheet programmatically**. 
  4. Save the file using [save(fileName)][9] method.

The code snippet is mentioned below to unMerge cells in an Excel worksheet using Node.js.

{{< gist conholdate-gists 10e7991c5128cb8bcb7b9e7634c331b0 "nodejs-library-to-unMerge-cells-in-Excel-sheets.js" >}}

Now, start the server and you will see the output as shown below in the image.

{{< figure align=center src="images/unmerge-cells-in-excel.png" alt="unmerge cells in Excel" caption="unMerge cells in excel using Node.js">}}

## How to clear content of a range in an Excel Sheet? {#How-to-clear-content-of-a-range-in-an-Excel-Sheet}

Perform the following steps to **clear data from a specified range of cells in an Excel worksheet programmatically in a Node.js app**:

  1. Initialize an object of the [Cells][6] class.
  2. Now, create an object of the [WorkBook][7] child class and instantiate it with an Excel file.
  3. Call the [clearContents(startRow, startColumn, endRow, endColumn)][11] method to delete data of a range of cells in an Excel file.
  4. Save the file using the [save(fileName)][9] method.

  Copy and paste the following code snippet into your main file to **clear data from a range in an Excel worksheet**.

  {{< gist conholdate-gists 10e7991c5128cb8bcb7b9e7634c331b0 "clear-content-of-a-range-in-an-Excel-sheet.js" >}}

  The output of this code snippet will be something like shown in the image below.

  {{< figure align=center src="images/clear-content-of-a-range.png" alt="clear content of a range" caption="clear content of a range in an Excel sheet">}}


## Get a Free License

You can try [a free temporary license][12] to use Aspose.Cells for Node.js without evaluation limitations.

## Conclusion

 This is the end of this blog post. We have gone through some important topics such as **unMerge or merge cells in Excel sheets using Node.js** and clearing data from a specific range of cells. There are some other relevant methods available that you may explore in this [Node.js Excel library][6]. Moreover, [conholdate.com][13] is in a consistent process of writing new articles. Therefore, please stay connected for regular updates. 

## Ask a question

You can share your questions or queries on our [forum.][14]

## See Also

  * [Import XML into Excel in Node.js][15]
  * [How to Edit Excel Sheet Programmatically in Node.js][16]
  * [Convert CSV into Excel using Node.js][17]

 [1]: https://docs.fileformat.com/spreadsheet/_xlsx/
 [2]: #Merge-cells-in-Excel-Sheets-using-Nodejs
 [3]: #Nodejs-library-to-UnMerge-cells-in-Excel-Sheets
 [4]: #How-to-clear-content-of-a-range-in-an-Excel-Sheet
 [5]: https://apireference.aspose.com/cells/nodejs
 [6]: https://apireference.aspose.com/cells/nodejs/cells
 [7]: https://apireference.aspose.com/cells/nodejs/Workbook
 [8]: https://apireference.aspose.com/cells/nodejs/Cells#merge
 [9]: https://apireference.aspose.com/cells/nodejs/Workbook#save
 [10]: https://apireference.aspose.com/cells/nodejs/Cells#unMerge
 [11]: https://apireference.aspose.com/cells/nodejs/Cells#clearContents
 [12]: https://purchase.conholdate.com/temporary-license
 [13]: https://conholdate.com/
 [14]: https://forum.conholdate.com/
 [15]: https://blog.conholdate.com/2022/04/28/convert-csv-into-excel-using-nodejs/
 [16]: https://blog.conholdate.com/2022/05/06/how-to-edit-excel-sheet-programmatically-in-nodejs/
 [17]: https://blog.conholdate.com/2022/04/28/convert-csv-into-excel-using-nodejs/
