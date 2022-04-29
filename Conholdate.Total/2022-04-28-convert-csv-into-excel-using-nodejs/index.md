---
title: 'Convert CSV into Excel using Node.js'
author: Muhammad Mustafa
date: 2022-04-28T07:56:46+00:00
summary: "Follow this blog post to learn how to **convert CSV into Excel using Node.js**. A powerful library to convert CSV file to Excel without third-party dependencies."
url: /2022/04/28/convert-csv-into-excel-using-nodejs/
categories:
  - Conholdate.Cells Product Family
tags:
  - Convert CSV into Excel Using Node.js 
  - Convert csv file to Excel
  - CSV to Excel Node.js
  - Convert CSV to XLSX
  - CSV to XLSX

---


{{< figure align=center src="images/convert-csv-to-excel-nodejs.png" alt="Convert CSV into Excel using Node.js" caption="CSV to Excel Node.js">}}

Recently, we have published a blog post that is about [how to import XML into Excel programmatically using Node.js][1]. However, in this article, we will learn how to convert CSV into Excel using an enterprise-level Node.js library. A [CSV][2](comma separated values) format represents a plain text file that maintains content with comma-separated values. Moreover, [Excel][3] comes with rich data storage, and management features and is backed by [Microsoft][4]. So, we will learn **how to convert CSV into Excel using Node.js** by covering the following points:


  * [How to convert CSV to XLSX][5]
  * [Node.js library to convert CSV into Excel][7]


## How to convert CSV to XLSX {#How-to-convert-CSV-to-XLSX}

In this section, we will go through the pre-requisites, classes, and member functions exposed by Aspose.Cells for Node.js application.

Please visit our previous [tutorial blog post][10] in which we have mentioned the setting up process of Aspose.Cells on the local machine. 

We will follow the following steps to complete the workflow:

  1. Create an object of the [Cells][11] class.
  2. Require the [fs][23] module to create a read stream of the source file.
  3. Create an object of the [Workbook][12] class that generates an Excel spreadsheet.
  4. Get the cells object of a particular worksheet using the [getCells()][24] method. 
  5. Then we will call this method [importCSVFromStream(cells, stream, spliter, convertNumericData, firstRow, firstColumn, callback)][13] that accepts file data stream along with other options to **convert CSV file to Excel**. 
  6. Finally, [save(fileName)][14]  will save the file into the root directory.


## Node.js library to convert CSV into Excel {#Nodejs-library-to-convert-CSV-into-Excel}

Now, open your main server file and paste the following code. **You need to place your source CSV file as I have the source file 'sample.csv' placed in the root directory**. 


{{< gist conholdate-gists 8c541a79672b1beac9de511697dc2aa8 " Convert CSV into Excel using Node.js" >}}

After that, start your server and you will find an Excel file named 'result.xlsx' saved in the root of your directory. However, you can see the output in the image below.

{{< figure align=center src="images/convert-csv-to-xlsx.png" alt="Import XML into Excel in Node.js" caption="Import XML data into Excel Spreadsheet">}}

## Get a Free License

You always have the chance to use [a free temporary license][17] to use Aspose.Cells for Node.js without evaluation limitations.

## Conclusion

This is the end of this blog post. We have gone through the steps and code sample to **convert CSV into Excel using Node.js** programmatically. In addition, you can further explore the classes and methods used to **convert CSV to XLSX**. Moreover, there are some relevant links mentioned in the 'See Also' section below. Therefore, it is high time to opt for [Aspose.cells][9] if you are looking to install a CSV to Excel Node.js library for your business application. Further, [conholdate.com][20] is continuously writing on new interesting topics. Therefore, please stay connected for regular updates.

## Ask a question

Feel free to visit our [forum][18] which is very active to respond to questions and queries/discussions.

## See Also

  * [Import XML into Excel in Node.js][21]
  * [Convert Excel Charts to SVG using Java][22]

 [1]: https://blog.conholdate.com/2022/04/25/import-xml-into-excel-in-nodejs/
 [2]: https://docs.fileformat.com/spreadsheet/csv/
 [3]: https://docs.fileformat.com/spreadsheet/_xlsx/
 [4]: https://www.microsoft.com/
 [5]: #How-to-convert-CSV-to-XLSX
 [6]: #How-to-convert-CSV-to-XLSX-in
 [7]: #Nodejs-library-to-convert-CSV-into-Excel
 [8]: https://www.fileformat.com/
 [9]: https://products.aspose.com/cells/family/
 [10]: https://blog.conholdate.com/2022/04/25/import-xml-into-excel-in-nodejs/#How-to-set-up-Aspose.Cells-in-Nodejs-project
 [11]: https://apireference.aspose.com/cells/nodejs/cells
 [12]: https://apireference.aspose.com/cells/nodejs/Workbook
 [13]: https://apireference.aspose.com/cells/nodejs/Cells#.importCSVFromStream
 [14]: https://apireference.aspose.com/cells/nodejs/Workbook#save
 [15]: https://apireference.aspose.com/cells/nodejs/Workbook#.createWorkbookFromStream
 [16]: https://apireference.aspose.com/cells/nodejs/Workbook#save
 [17]: https://purchase.conholdate.com/temporary-license
 [18]: https://forum.conholdate.com/
 [19]: https://blog.conholdate.com/2022/02/17/search-data-in-excel-using-java/
 [20]: https://www.conholdate.com/
 [21]: https://blog.conholdate.com/2022/04/25/import-xml-into-excel-in-nodejs/
 [22]: https://blog.conholdate.com/2022/01/11/convert-excel-charts-to-svg-using-java/
 [23]: https://nodejs.dev/learn/the-nodejs-fs-module
 [24]: https://apireference.aspose.com/cells/nodejs/Cells#getCell