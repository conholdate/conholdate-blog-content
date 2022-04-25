---
title: 'Import XML into Excel in Node.js'
author: Muhammad Mustafa
date: 2022-04-25T07:56:46+00:00
summary: "Quickly **import XML into an Excel spreadsheet** using an easy-to-install library. Let's learn how can we set up & enable this provision in our Node.js application."
url: /2022/04/25/import-xml-into-excel-in-nodejs/
categories:
  - Conholdate.Cells Product Family
tags:
  - XML File to Excel
  - Import XML Data into Excel
  - Import XML File into Excel
  - Convert XML to Excel JavaScript 
  - XML to XLSX

---


{{< figure align=center src="images/import-xml-into-excel.png" alt="Import XML into Excel in Node.js" caption="Import XML data into Excel file.">}}

[Extensible markup language][1] is a widely-used file format for data representation. It is highly efficient when it comes to transferring data from one database to another without any critical data loss. However, tags are used to structure an XML document and page designers can define customized meaningful tags to meet the structural needs. On the other side, businesses are leveraging [Excel sheets][2] as it offers rich data storage options. In addition, you can perform complex calculations and compile raw data. In this blog post, we will learn the steps to install file format manipulation and conversion library and we will show you how can you **import XML into Excel in Node.js**.

We will cover the following points:

  * [A brief introduction of Aspose.Cells][3]
  * [How to set up Aspose.Cells in Node.js project?][4]
  * [Code snippet to populate XML into Excel Sheet][5]

## A brief introduction of Aspose.Cells {#A-brief-introduction-of-Aspose.Cells}

[Aspose.cells][6] offers enterprise-level APIs and SDKs to convert, create, edit and manipulate Excel files on any platform. There is a complete package that contains a wide range of features linked to spreadsheet processing. In addition, these APIs are highly scalable, efficient, rich-featured, and available in almost all popular programming languages such as Aspose.Cells for Java, Aspose.Cells for .Net, Aspose.Cells for C++ and more. Aspose.Cells for Node.js is based on Aspose.Cells for Java that provides Excel sheet file conversion, styling, data export/import (i.e. **XML file to Excel**), and many other provisions. Above all, there a comprehensive [documentation][7] available regarding usage along with the example code snippets.

## How to set up Aspose.Cells in Node.js project? {#How-to-set-up-Aspose.Cells-in-Node.js-project?}

In this section, we will go through the step to enable Aspose.Cells for Node.js on a local machine. You can visit the [docs][8] to know about the installation instructions for your operating system.

I am using macOS, therefore, I will follow the following steps to set up Aspose.Cells.

Pre-requisites:

  1. [Node.js][9]
  2. [Oracle JDK 1.8][10]
  3. [Python][11]

Once pre-requites are installed, run the following command to install Aspose.Cells from [Npm][12].

```
npm install aspose.cells
```

Also, run the following command to enable Java in the Node.js project.

```
npm install java
```

That's it. Now, you are all set to start writing code to **import XML data into Excel sheet**.

## Code snippet to populate XML into Excel Sheet {#Code-snippet-to-populate-XML-into-Excel-Sheet}

The code snippet will comprise the following classes and methods to **import XML file into Excel** spreadsheet programmatically.

  1. First, import the parent [Cells][13] class to enable Aspose.Cells in your project.
  2. We will be using [Workbook][14] child class also in this code snippet.
  3. Call this method [createWorkbookFromStream(stream, callback)][15] that accepts the XML file data as a stream and parses it to the Excel file.
  4. Another method [save(fileName)][16] will be called to save the file on the root directory of the project.

Now, open the main file of your project and paste the following code snippet that will **import XML data into Excel** programmatically.

```
// create sheet from stream(e.g. xml to xlsx)
var aspose = aspose || {};

//get the aspose.cells module in to your project.
aspose.cells = require("aspose.cells");

// load the fs module for reading/writing files
var fs = require("fs");

// creates the read stream of the source file
var readStream = fs.createReadStream("myxml.xml");

// accepts the data stream and populates/import XML data into Excel file
aspose.cells.Workbook.createWorkbookFromStream(readStream, function(workbook, err) {

  if (err) {
      console.log("open workbook error");
      return;
  }

// save the file 
  workbook.save('result.xlsx');
  console.log('Successfully imported XML file to Excel');
});
```

In the code snippet above, you can see that I have placed a source XML file named 'myxml.xml'. However, you must have your source XML file that you want to import into Excel sheet.

Finally, start the server, and the function to import XML data into Excel should have been executed successfully. Moreover, you can see the output of this method in the image below.

{{< figure align=center src="images/import-xml-into-excel-in-nodejs" alt="Import XML into Excel in Node.js" caption="Import XML data into Excel Spreadsheet">}}

## Get a Free License

Please feel free to use [a free temporary license][17] to use Aspose.Cells for Node.js beyond evaluation limitations.

## Conclusion

This brings us to the end of this blog post. We have gone covered the whole process through which you can **import XML into Excel in Node.js**. This article will surely help you if you are looking to opt for a Node.js library to import XML data into Excel file. Further, conholdate.com is in a consistent process to write articles on further interesting topics. Therefore, please stay connected for regular updates.

## Ask a question

Feel free to visit our [forum][18] which is very active to respond to questions and queries/discussions.

## See Also

  * [Search Data in Excel using Java][19]

 [1]: https://docs.fileformat.com/web/xml/
 [2]: https://docs.fileformat.com/spreadsheet/_xlsx/
 [3]: #A-brief-introduction-of-Aspose.Cells
 [4]: #How-to-set-up-Aspose.Cells-in-Node.js-project?
 [5]: #Code-snippet-to-populate-XML-into-Excel-Sheet
 [6]: https://products.aspose.com/cells/family/
 [7]: https://apireference.aspose.com/cells/nodejs
 [8]: https://docs.aspose.com/cells/nodejsjava/getting-started/
 [9]: https://nodejs.org/en/download/
 [10]: https://www.oracle.com/java/technologies/downloads/
 [11]: https://www.python.org/
 [12]: https://www.npmjs.com/package/aspose.cells
 [13]: https://apireference.aspose.com/cells/nodejs/cells
 [14]: https://apireference.aspose.com/cells/nodejs/Workbook#importXml
 [15]: https://apireference.aspose.com/cells/nodejs/Workbook#.createWorkbookFromStream
 [16]: https://apireference.aspose.com/cells/nodejs/Workbook#save
 [17]: https://purchase.conholdate.com/temporary-license
 [18]: https://forum.conholdate.com/
 [19]: https://blog.conholdate.com/2022/02/17/search-data-in-excel-using-java/