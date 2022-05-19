---
title: 'Convert VSDX to PDF and PNG using Node.js'
author: Muhammad Mustafa
date: 2022-05-19T07:56:46+00:00
summary: "Go through this blog post to **convert VSDX to PDF and PNG using Node.js**. Install a powerful library to convert VSDX to PDF in a Node.js-based application."
url: /2022/05/19/convert-vsdx-to-pdf-and-png-using-nodejs/
categories:
  - Conholdate.Diagram Product Family
tags:
  - convert VSDX to PDF in Node.js
  - Convert VSDX to PNG in Node.js
  - Node.js library for file manipulation
  - VSD to PDF, PNG
  - Visio API

---


{{< figure align=center src="images/Convert-VSD-to-PDF-in-nodejs.png" alt="Convert VSDX to PDF in Node.js" caption="Convert VSDX to PDF in Node.js">}}

[Aspose.Diagram][1] offers a set of provisions to manipulate Microsoft [Visio][2] diagrams. You can automate the processes of updating, exporting, and creating Visio diagrams in Node.js-based applications. Aspose.Diagram for Node.js library provides features to convert Visio files to other popular file formats such as [PDF][3], PNG, and more. In addition, you can export & print the diagrams in no time. However, in this blog post, we will demonstrate how to **convert VSDX to PDF in Node.js application**.

The following points will be covered in this article:


  * [Convert VSDX to PDF and PNG using Node.js - Visio API installation][4]
  * [How to convert VSDX to PDF in Node.js][5]
  * [Node.js library to convert VSDX to PNG][6]

## Convert VSDX to PDF and PNG using Node.js - Visio API installation {#Nodejs-library-to-convert-VSDX-to-PNG}

It is very easy to install this [Node.js library][7] in your Node.js project. Run the following command to enable this package:

```
npm install aspose.diagram --save
```

## How to convert VSDX to PDF in Node.js {#How-to-convert-VSDX-to-PDF-in-Nodejs}

In this section, we will write a code snippet that will convert [Visio diagram][8] to PDF in Node.js app programmatically.

These are the steps to convert vision files to PDF:

  1. Initialize the [Diagram()][9] constructor to load a VSDX file.
  2. Instantiate the [PdfSaveOptions()][10] object for access to various attributes of the PDF file.
  3. Invoke the [setSplitMultiPages(true)][11] method to define whether split diagram to multi-pages.
  4. Call the [save(filename, format)][12] method to save as PDF file.

Copy and paste the following code snippet into your file.

{{< gist conholdate-gists d072d683513c90fb319bd187fa1d3c7e "vddx-to-pdf.js" >}}

{{< figure align=center src="images/vsdx-to-pdf.png" alt="Convert VSDX to PDF in Node.js" caption="Convert VSDX to PDF in Node.js">}}


## Node.js library to convert VSDX to PNG {#Nodejs-library-to-convert-VSDX-to-PNG}

Let's explore the following steps to **convert VSDX file to PNG file programmatically:**

 1. Call the [Diagram()][9] constructor to load a VSDX file.
 2. Initialize a new instance of [ImageSaveOptions(saveFormat)][13] to specify additional options.
 3. You can specify the image resolution and brightness by calling [setResolution()][14], [setImageBrightness()][15] methods.
 4. Invoke the [save(filename, format)][16] method to save the file in PNG format.

The following code snippet converts a Visio diagram to a PNG file.

{{< gist conholdate-gists d072d683513c90fb319bd187fa1d3c7e "VSDX-to-PNG.js" >}}

{{< figure align=center src="images/vsdx-to-png.png" alt="Convert VSDX to PNG in Node.js" caption="VSDX to PNG in Node.js">}}


## Get a Free License

You can select a [free temporary license][17] to use [Aspose.Diagram][18] for Node.js without evaluation limitations.

## Summing up

We are ending this blog post here. We hope you have learned how to convert [VSDX][8] to PDF in Node.js programmatically. Moreover, we also have gone through the [Aspose.Diagram for Node.js][1] API that converts VSDX to PNG instantly. You can explore the [documentation][7] for further features. In addition, [conholdate.com][19] is continuously writing on new topics. Therefore, please stay connected for regular updates.

## Ask a question

In case of any queries please feel free to write to us at the [forum.][20]

## See Also

  * [Convert SVG to PDF Programmatically in Java][21]
  * [Import XML into Excel in Node.js][22]
  * [UnMerge or Merge Cells in Excel Worksheets using Node.js][23]

 [1]: https://products.aspose.com/diagram/nodejs-java/
 [2]: https://products.aspose.com/diagram/nodejs-java/
 [3]: https://docs.fileformat.com/pdf/
 [4]: #Nodejs-library-to-convert-VSDX-to-PNG
 [5]: #How-to-convert-VSDX-to-PDF-in-Nodejs
 [6]: #Nodejs-library-to-convert-VSDX-to-PNG
 [7]: https://docs.aspose.com/diagram/java/aspose-diagram-for-node-js-via-java/
 [8]: https://docs.fileformat.com/visio/vsdx/
 [9]: https://apireference.aspose.com/diagram/nodejs/Diagram
 [10]: https://apireference.aspose.com/diagram/nodejs/PdfSaveOptions
 [11]: https://apireference.aspose.com/diagram/nodejs/PdfSaveOptions#setSplitMultiPages
 [12]: https://apireference.aspose.com/diagram/nodejs/Diagram#save
 [13]: https://apireference.aspose.com/diagram/nodejs/ImageSaveOptions
 [14]: https://apireference.aspose.com/diagram/nodejs/ImageSaveOptions#setResolution
 [15]: https://apireference.aspose.com/diagram/nodejs/ImageSaveOptions#setImageBrightness
 [16]: https://apireference.aspose.com/diagram/nodejs/Diagram#save
 [17]: https://purchase.conholdate.com/temporary-license
 [18]: https://products.aspose.com/diagram/
 [19]: https://www.conholdate.com/
 [20]: https://forum.conholdate.com/
 [21]: https://blog.conholdate.com/2022/05/17/convert-svg-to-pdf-programmatically-in-java/
 [22]: https://blog.conholdate.com/2022/04/25/import-xml-into-excel-in-nodejs/
 [23]: https://blog.conholdate.com/2022/05/10/unmerge-or-merge-cells-in-excel-worksheets-using-nodejs/