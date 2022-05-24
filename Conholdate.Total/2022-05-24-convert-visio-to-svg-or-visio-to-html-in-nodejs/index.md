---
title: 'Convert Visio to SVG or Visio to HTML in Node.js'
author: Muhammad Mustafa
date: 2022-05-24T07:56:46+00:00
summary: "Programmatically **convert Visio to SVG or Visio to HTML in Node.js** application Install this Node.js library to manipulate & convert VSDX or VSD files robustly."
url: /2022/05/24/convert-visio-to-svg-or-visio-to-html-in-nodejs/
categories:
  - Conholdate.Diagram Product Family
tags:
  - Visio to SVG in Node.js
  - Visio to HTML
  - Convert Visio to SVG
  - Convert Visio to HTML
  - JavaScript Visio like library

---


{{< figure align=center src="images/convert-visio-to-svg-or-visio-to-html-in-nodejs.png" alt="Convert Visio to SVG or Visio to HTML in Node.js" caption="Convert Visio to SVG or Visio to HTML in Node.js">}}

In our previous [blog post][1], we went through how to convert [VSDX][2] files to PDF and PNG programmatically in the Node.js application. However, this article will go through the steps and the code snippet to **convert Visio to [SVG][3] or Visio to [HTML][4] in Node.js**. This [Visio Node.js library][5] enables you to edit, create and convert VSDX files from one format to another easily and quickly. Further, you may save your diagram as a web page to embed in your business websites.

The following points shall be covered in this blog post:


  * [Convert Visio to SVG using Node.js ][6]
  * [Node.js library to convert VSDX or Visio to HTML][7]
  * [Convert Visio to SVG or Visio to HTML in Node.js - advance options ][8]

## Convert Visio to SVG using Node.js {#Convert-Visio-to-SVG-using-Nodejs}

In this section, we will learn how to convert VSDX or VSD file to SVG programmatically by writing a few lines of source code. You may visit this [article][9] to know about the installation of this API.

The following steps will be performed:

  1. Invoke the [Diagram()][10] constructor to load a VSDX file.
  2. Initialize a new instance of [SVGSaveOptions()][11] to specify additional options.
  3. Call [setSVGFitToViewPort(true)][12] method will make the generated SVG fit to viewport.
  4. Use this [setExportElementAsRectTag(true)][13] method to set export element as Rectangle.
  5. [save(filename, format)][14] method to save the file in SVG format.

Copy and paste the following code snippet into your file.

{{< gist conholdate-gists de268ff1bf718acadc3de3a3f9ee78af "VSDX-to-SVG-in-Nodejs.js" >}}

{{< figure align=center src="images/VSDX-to-SVG-in-Nodejs.png" alt="VSDX to SVG in Node.js" caption="VSDX to SVG in Node.js">}}


## Node.js library to convert VSDX or Visio to HTML {#Nodejs-library-to-convert-VSDX-or-Visio-to-HTML}

We will follow the steps mentioned below to **convert the VSDX file to a web page**:

 1. Initialize the [Diagram()][10] constructor to load a VSDX file.
 2. Instantiate a new instance of [HTMLSaveOptions()][15] to define additional options.
 3. Call this [setTitle(string)][16] method to set the title of the HTML document.
 4. [setSaveToolBar(true)][17] will specify whether to include the toolbar or not.
 5. Invoke [setDefaultFont(string)][18] method to set the font.
 6. [save(filename, format)][14] method to save the file in HTML format.

The following code snippet converts a Visio diagram to a PNG file.

{{< gist conholdate-gists de268ff1bf718acadc3de3a3f9ee78af "VSDX-to-SVG-in-Nodejs.js" >}}

{{< figure align=center src="images/vsdx-to-html.png" alt="Convert VSDX to PNG in Node.js" caption="VSDX to PNG in Node.js">}}

## Convert Visio to SVG or Visio to HTML in Node.js - advance options {#Convert-Visio-to-SVG-or-Visio-to-HTML-in-Nodejs---advance-options}

In addition, this [Node.js Diagram library][5] also provides many features related to HTML and SVG file formats. However, you may find some code snippets also that demonstrate the usage of methods.

## Get a Free License

Please try the API beyond evaluation limitations by requesting a [free temporary license][19].

## Summing up

This brings us to end this blog post. We have gone through some interesting points that include converting **Visio to SVG and Visio to HTML in Node.js**application. This blog post will really help you if you are looking to integrate [Aspose.Diagram library][20] to convert VSDX files to other popular file formats. In addition, you may explore the documentation for further features. Moreover, [conholdate.com][21] is continuously writing new articles. Therefore, please stay connected for the latest updates.

## Ask a question

You can share your questions or queries on our [forum][22].

## See Also

  * [Convert VSDX to PDF and PNG using Node.js][23]
  * [Convert SVG to PDF Programmatically in Java][24]
  * [Import XML into Excel in Node.js][25]
  * [Insert Rows and Columns in Excel Files using Node.js][26]
  * [UnMerge or Merge Cells in Excel Worksheets using Node.js][27]

 [1]: https://blog.conholdate.com/2022/05/19/convert-vsdx-to-pdf-and-png-using-nodejs/
 [2]: https://docs.fileformat.com/visio/vsdx/
 [3]: https://docs.fileformat.com/page-description-language/svg/
 [4]: https://docs.fileformat.com/web/html/
 [5]: https://docs.aspose.com/diagram/java/aspose-diagram-for-node-js-via-java/
 [6]: #Convert-Visio-to-SVG-using-Nodejs
 [7]: #Nodejs-library-to-convert-VSDX-or-Visio-to-HTML
 [8]: #Convert-Visio-to-SVG-or-Visio-to-HTML-in-Nodejs---advance-options
 [9]: https://blog.conholdate.com/2022/05/19/convert-vsdx-to-pdf-and-png-using-nodejs/#Convert-VSDX-to-PDF-and-PNG-using-Nodejs---Visio-API-installation
 [10]: https://apireference.aspose.com/diagram/nodejs/Diagram
 [11]: https://apireference.aspose.com/diagram/nodejs/SVGSaveOptions
 [12]: https://apireference.aspose.com/diagram/nodejs/SVGSaveOptions#setSVGFitToViewPort
 [13]: https://apireference.aspose.com/diagram/nodejs/SVGSaveOptions#setExportElementAsRectTag
 [14]: https://apireference.aspose.com/diagram/nodejs/Diagram#save
 [15]: https://apireference.aspose.com/diagram/nodejs/HTMLSaveOptions
 [16]: https://apireference.aspose.com/diagram/nodejs/HTMLSaveOptions#setTitle
 [17]: https://apireference.aspose.com/diagram/nodejs/HTMLSaveOptions#setSaveToolBar
 [18]: https://apireference.aspose.com/diagram/nodejs/HTMLSaveOptions#setDefaultFont
 [19]: https://purchase.conholdate.com/temporary-license
 [20]: https://products.aspose.com/diagram/nodejs-java/
 [21]: https://www.conholdate.com/
 [22]: https://forum.conholdate.com/
 [23]: https://blog.conholdate.com/2022/05/19/convert-vsdx-to-pdf-and-png-using-nodejs/
 [24]: https://blog.conholdate.com/2022/05/17/convert-svg-to-pdf-programmatically-in-java/
 [25]: https://blog.conholdate.com/2022/04/25/import-xml-into-excel-in-nodejs/
 [26]: https://blog.conholdate.com/2022/05/12/insert-rows-and-columns-in-excel-files-using-nodejs/
 [27]: https://blog.conholdate.com/2022/05/10/unmerge-or-merge-cells-in-excel-worksheets-using-nodejs/