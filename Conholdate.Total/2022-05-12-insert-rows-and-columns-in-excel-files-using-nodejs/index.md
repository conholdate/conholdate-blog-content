---
title: 'Insert Rows and Columns in Excel Files using Node.js'
author: Muhammad Mustafa
date: 2022-05-12T07:56:46+00:00
summary: "Learn how to **insert rows and columns in Excel files using Node.js programmatically.**  Now, you can automate the process of inserting cells in Excel worksheets."
url: /2022/05/10/insert-rows-and-columns-in-excel-files-using-nodejs/
categories:
  - Conholdate.Cells Product Family
tags:
  - insert rows and columns in excel files using Nodejs
  - insert rows and columns in excel
  - insert multiple rows in excel
  - insert columns in excel
  - insert cells in excel

---


{{< figure align=center src="images/insert-rows-and-columns-in-excel-using-Nodejs.png" alt="insert rows and columns in Excel files using Node.js" caption="insert rows and columns in Excel files using Node.js">}}

[Microsoft Excel][1] is one of the leading and most widely used software in this world of technology. Most organizations leverage this software for various purposes and maintain a huge amount of data in Excel files. In addition, modifying several data files manually is always a hassle. In this blog post, we will learn how to **insert rows and columns in Excel files programmatically using Nodejs**. However, automating this process will provide efficiency and a competitive edge to the business.

The following points will be covered in this blog post:


  * [Insert rows and columns in Excel files using Node.js - API installation][2]
  * [Insert multiple rows in Excel Worksheets Code Example][3]
  * [Node.js library to insert columns in Excel Sheets ][4]

## Insert rows and columns in Excel files using Node.js - API installation {#Insert-rows-and-columns-in-Excel-files-using-Nodejs}

We will use a powerful [Node.js Excel library][5] to insert rows and columns in an Excel sheet programmatically. You can easily install by running the following commands in the terminal.

```
npm install java
```
```
npm install aspose.cells
```

You can visit this [link][6] to know further about the installation procedure.

**Note: Place a source XLSX file in the project root directory as we have placed the “sample.xlsx” file in this article.**

## Insert multiple rows in Excel Worksheets Code Example {#Insert-multiple-rows-in-Excel-Worksheets-Code-Example}

In this section, we will go through the following steps and the code snippet to **insert rows in an Excel file using Node.js.**

  1. Create an object of the [Cells][7] class.
  2. Load an Excel file(i.e. sample.xlsx) by initializing an object of the [WorkBook][8] child class.
  3. Call the [insertRows(rowIndex, totalRows, options)][9] method to insert as many rows as needed anywhere in the worksheet.
  4. Save the file using the [save(fileName)][10] method.

The following code snippet is to insert multiple rows in an Excel Worksheet programmatically.

{{< gist conholdate-gists 3182b30debbddf9e3082fab78b0d53ea "insert-multiple-rows-in-Excel-Worksheets.js" >}}

The output can be seen in the image below.

{{< figure align=center src="images/Insert-multiple-rows-in-Excel-Worksheets.png" alt="insert rows and columns in an Excel file using Node.js" caption="insert rows in an Excel file using Node.js">}}


## Node.js library to insert columns in Excel Sheets {#Nodejs-library-to-insert-columns-in-Excel-Sheets}

This [Node.js Excel library][5] offers the provision to add columns in Excel files using simple lines of code.

Following are the steps to insert columns in the Excel worksheet using Node.js.

  1. Import and create an object of the [Cells][7] class.
  2. Create an object of the [WorkBook][8] child class by initializing it with an Excel file.
  3. Now, invoke the [insertColumns(columnIndex, totalColumns)][11] method to insert columns into the Excel worksheet.
  4. Finally, the [save(fileName)][10] method saves the file into the root directory.

Copy and paste the code snippet mentioned below to **insert columns in an Excel File programmatically using Node.js.**

{{< gist conholdate-gists 3182b30debbddf9e3082fab78b0d53ea "insert-multiple-rows-in-Excel-Worksheets.js" >}}

Now, start the server and you will see the output as shown below in the image.

{{< figure align=center src="images/Nodejs-library-to-insert-columns-in-Excel-Sheets.png" alt="insert columns in an Excel File programmatically" caption="insert columns in an Excel File programmatically">}}

## Get a Free License

You may use a [free temporary license][12] to use Aspose.Cells for Node.js without evaluation limitations.

## Conclusion

This blog post ends here. We have gone through how to **insert rows and columns in Excel files using Node.js**. In addition, you can explore the [documentation][13] to learn further about Aspose.Cells for Node.js. Moreover, [conholdate.com][14] will write on new engaging topics. Therefore, please stay in touch for the latest updates.

## Ask a question

In case of any queries please feel free to write to us at the [forum.][18]

## See Also

  * [Import XML into Excel in Node.js][15]
  * [How to Edit Excel Sheet Programmatically in Node.js][16]
  * [Convert CSV into Excel using Node.js][17]

 [1]: https://docs.fileformat.com/spreadsheet/_xlsx/
 [2]: #Insert-rows-and-columns-in-Excel-files-using-Nodejs
 [3]: #Insert-multiple-rows-in-Excel-Worksheets-Code-Example
 [4]: #Nodejs-library-to-insert-columns-in-Excel-Sheets
 [5]: https://apireference.aspose.com/cells/nodejs
 [6]: https://blog.conholdate.com/2022/04/25/import-xml-into-excel-in-nodejs/
 [7]: https://apireference.aspose.com/cells/nodejs/cells
 [8]: https://apireference.aspose.com/cells/nodejs/Workbook
 [9]: https://apireference.aspose.com/cells/nodejs/Workbook
 [10]: https://apireference.aspose.com/cells/nodejs/Workbook#save
 [11]: https://apireference.aspose.com/cells/nodejs/Cells#insertColumns
 [12]: https://purchase.conholdate.com/temporary-license
 [13]: https://docs.aspose.com/cells/
 [14]: https://conholdate.com/
 [18]: https://forum.conholdate.com/