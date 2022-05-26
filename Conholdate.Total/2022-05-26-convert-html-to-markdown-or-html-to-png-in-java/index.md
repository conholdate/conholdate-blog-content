---
title: 'Convert HTML to Markdown or HTML to PNG in Java'
author: Muhammad Mustafa
date: 2022-05-26T07:56:46+00:00
summary: "Learn how to **convert HTML to Markdown or HTML to PNG in Java programmatically** using an easy-to-install Java library. Convert web page to an image or .md file. "
url: /2022/05/24/convert-html-to-markdown-or-html-to-png-in-java/
categories:
  - Conholdate.HTML Product Family
tags:
  - HTML to Markdown in Java
  - HTML to PNG
  - Convert HTML to PNG using Java 
  - HTML to .md converter 
  - Java library for file conversion 

---


{{< figure align=center src="images/html-to-markdown.png" alt="Convert HTML to Markdown or HTML to PNG in Java" caption="Convert HTML to Markdown or HTML to PNG in Java">}}

[Markdown][1] and [HTML][2] are the two most popular mark-up languages used on the web. Markdown is an easy, lightweight language to format text using symbols. Whereas, HTML lets users design complex web structures with the help of pre-defined and custom tags. In some cases, users prefer Markdown over HTML due to its robustness and simplicity. Therefore, in this article, we will **convert HTML to Markdown or HTML to PNG in Java programmatically** using API methods offered by [Aspose.HTML for Java][3].

We will cover the following sections in this blog post:


  * [Convert HTML to Markdown or HTML to PNG in Java - API installation ][4]
  * [Java library to convert HTML to Markdown programmatically][5]
  * [HTML to PNG conversion library in Java  ][6]

## Convert HTML to Markdown or HTML to PNG in Java - API installation {#Convert-HTML-to-Markdown-or-HTML-to-PNG-in-Java---API-installation}

[Aspose.HTML for Java][3] offers a rich stack of file manipulation and conversion methods. It allows users to perform these actions with simple configurations. Therefore, the installation procedure of this HTML to Markdown or HTML to PNG conversion library is quite easy. You can either download the [jar files][7] or follow the following Maven configurations.

**Repository**
```
<repository>
    <id>AsposeJavaAPI</id>
    <name>Aspose Java API</name>
    <url>https://repository.aspose.com/repo/</url>
</repository>
```

**Dependency**

```
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-html</artifactId>
    <version>21.12</version>
    <classifier>jdk1.8</classifier>
</dependency>
```

## Java library to convert HTML to Markdown {#Java-library-to-convert-HTML-to-Markdown}

The following steps will be performed to **convert HTML to .md file in a Java application**.

 1. Create an object of [HTMLDocument][8] class and load the source HTML file.
 2. Initialize an object of [MarkdownSaveOptions()][9] class.
 3. Invoke this method [convertHTML(HTMLDocument document, MarkdownSaveOptions options, java.lang.String outputPath)][10] to convert a web page to Markdown file. This method will save the converted file at the mentioned path.

Now, copy and paste the following code snippet in your Java file:

{{< gist conholdate-gists fd62540910d2758d35180203599ab467 "convert-HTML-to-markdown.java" >}}

## HTML to PNG conversion library in Java {#HTML-to-PNG-conversion-library-in-Java}

This section will demonstrate the steps and the code snippet to **convert an HTML file to PNG file programmatically** in Java.

Lets go through the following steps:

 1. Initiate an instance of [HTMLDocument][8] class and load the source HTML file.
 2. Create an object of [ImageSaveOptions][11] class to access the image attributes.
 3. Make a call to this [convertHTML(HTMLDocument document, ImageSaveOptions options, java.lang.String outputPath)][12] method to convert a HTML to PNG.

{{< gist conholdate-gists fd62540910d2758d35180203599ab467 "HTML-to-PNG-conversion-library.java" >}}

## Get a Free License

You can avail a [free temporary license][13] to try the API without evaluation limitations.

## Summing up

In this blog post, we have learned how to **convert HTML to Markdown or HTML to PNG in Java programmatically**. We have noted down the steps and the code examples to test the **HTML to .md & HTML to PNG conversion APIs**. In addition, you can explore the [documentation][14] to learn about the other features. Moreover, [conholdate.com][15] is continuously writing new blog posts. Therefore, please stay in touch for the latest updates.

## Ask a question

In case of any queries please feel free to write to us at the [forum][16].

## See Also

  * [Convert VSDX to PDF and PNG using Node.js][17]
  * [Convert SVG to PDF Programmatically in Java][18]
  * [Import XML into Excel in Node.js][19]
  * [Insert Rows and Columns in Excel Files using Node.js][20]
  * [UnMerge or Merge Cells in Excel Worksheets using Node.js][21]

 [1]: https://docs.fileformat.com/word-processing/md/
 [2]: https://docs.fileformat.com/web/html/
 [3]: https://products.aspose.com/html/java/
 [4]: #Convert-HTML-to-Markdown-or-HTML-to-PNG-in-Java---API-installation
 [5]: #Java-library-to-convert-HTML-to-Markdown
 [6]: #HTML-to-PNG-conversion-library-in-Java
 [7]: https://downloads.aspose.com/html/java
 [8]: https://apireference.aspose.com/html/java/com.aspose.html/HTMLDocument
 [9]: https://apireference.aspose.com/html/java/com.aspose.html.saving/MarkdownSaveOptions
 [10]: https://apireference.aspose.com/html/java/com.aspose.html/HTMLDocument
 [11]: https://apireference.aspose.com/html/java/com.aspose.html.saving/ImageSaveOptions
 [12]: https://apireference.aspose.com/html/java/com.aspose.html.converters/Converter#convertHTML-com.aspose.HTMLDocument-com.aspose.saving.ImageSaveOptions-java.lang.String-
 [13]: https://purchase.conholdate.com/temporary-license
 [14]: https://docs.aspose.com/html/java/
 [15]: https://www.conholdate.com/
 [16]: https://forum.conholdate.com/
 [17]: https://blog.conholdate.com/2022/05/19/convert-vsdx-to-pdf-and-png-using-nodejs/
 [18]: https://blog.conholdate.com/2022/05/17/convert-svg-to-pdf-programmatically-in-java/
 [19]: https://blog.conholdate.com/2022/04/25/import-xml-into-excel-in-nodejs/
 [20]: https://blog.conholdate.com/2022/05/12/insert-rows-and-columns-in-excel-files-using-nodejs/
 [21]: https://blog.conholdate.com/2022/05/10/unmerge-or-merge-cells-in-excel-worksheets-using-nodejs/
 