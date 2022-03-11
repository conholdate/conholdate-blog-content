---
title: Convert HTML to PDF using Java
author: Muzammil Khan
date: 2021-09-10T13:37:34+00:00
summary: 'As a Java developer, you can easily convert HTML files or HTML web pages from live URLs into PDF documents. In this article, you will learn **how to convert HTML to PDF using Java**.'
url: /2021/09/10/convert-html-to-pdf-using-java/
categories:
  - Conholdate.Total Product Family
tags:
  - Convert HTML to PDF
  - Convert HTML to PDF in Java
  - Convert HTML Web Pages to PDF
  - HTML to PDF conversion API
  - HTML to PDF Conversion Java API

---


{{< figure align=center src="images/Convert-HTML-to-PDF.jpg" alt="Convert HTML to PDF using Java">}}
 

As a Java developer, you can easily convert HTML files or web pages from live web URLs into PDF documents programmatically in your Java applications. In this article, you will learn **how to convert HTML to PDF using Java**.

The following topics are discussed/covered in this article:

  * [HTML to PDF Conversion Java API][2]
  * [Convert HTML to PDF using Java][3]
  * [Convert HTML to PDF with Advanced Options][4]
  * [HTML to PDF Conversion from a URL][5]
  * [Convert Specific Page Range of HTML to PDF][6]
  * [Convert HTML to PDF and Add Watermark][7]

## HTML to PDF Conversion Java API {#HTML-to-PDF-Conversion-Java-API}

For converting [HTML][8] to [PDF][9], I will be using [GroupDocs.Conversion for Java API][10]. It is a fast, efficient, and reliable file conversion solution for your Java applications without installing any external software. You can convert among all popular business document formats such as PDF, HTML, Email, Word, Excel, PowerPoint, Project, raster image file formats, and many more. It also allows you to display the whole document, or render it partially to speed up the process. The API is compatible with all Java versions and supports popular operating systems (Windows, Linux, macOS) that are capable to run Java runtime.

You can [download][11] the JAR of the API or just add the following **_pom.xml_** configuration in your Maven-based Java application to try the below-mentioned code examples.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```

```
<dependency>
  <groupId>com.groupdocs</groupId>
  <artifactId>groupdocs-conversion</artifactId>
  <version>21.7</version> 
</dependency>
```

## Convert HTML to PDF using Java {#Convert-HTML-to-PDF-using-Java}

You can easily convert HTML files to PDF documents by following the simple steps given below:

  1. Create an instance of the _**[Converter][12]**_ class with the input file path
  2. Create an instance of the [**_PdfConvertOptions_**][13]
  3. Call the _**[convert()][14]**_ method with the output file path and convert options

The following code sample shows **how to convert an HTML document to a PDF document using Java**.

{{< gist conholdate-gists 0e90868fedd7c20948490fb5f458432e "ConvertHTMLtoPDF_Java_Convert.java" >}}

{{< figure align=center src="images/Convert-HTML-to-PDF-using-Java-1024x510.jpg" alt="Convert HTML to PDF using Java" caption="Convert HTML to PDF using Java">}}
 

The [Converter][12] class is the main class that controls the document conversion process. It provides various methods to fulfill the conversion requests. The [convert()][14] method of this class converts the source document into the specified target format and saves the converted document at the given file path. It provides several overloaded _convert()_ methods to convert supported file formats.

## Convert HTML to PDF with Advanced Options {#Convert-HTML-to-PDF-with-Advanced-Options-using-Java}

You can use some advanced settings while converting the HTML files to PDF documents by following the steps given below:

  1. Create an instance of the _**[Converter][12]**_ class with the input file path
  2. Create an instance of [**_PdfConvertOptions_**][13]
  3. Set various options such as _Rotation_, _Dpi_, _Width_, _Height_, etc.
  4. Call the _**[convert()][14]**_ method with the output file path and convert options

The following code sample shows **how to convert an HTML file to a PDF document with advanced settings.**

{{< gist conholdate-gists 0e90868fedd7c20948490fb5f458432e "ConvertHTMLtoPDF_Java_ConvertWithOptions.java" >}}

{{< figure align=center src="images/Convert-HTML-to-PDF-with-Advanced-Options-using-Java-1024x478.jpg" alt="Convert HTML to PDF with Advanced Options using Java" caption="Convert HTML to PDF with Advanced Options using Java">}}
 
The [PdfConvertOptions][13] class provides several options to convert specified input files to PDF documents. I have used the following options:

  * [Width][17] — the setWidth() property sets the image width after conversion
  * [Height][18] — the setHeight() property sets the desired image height after conversion
  * [Dpi][19] — the setDpi() property sets the desired page DPI after conversion
  * [Password][20] — the setPassword() property protects the converted document with a password
  * [Rotate][21] — the setRotate() property allows page rotation with the following available options: _None, On90, On180, On270_

You can find more details about “[Convert to PDF with Advanced Options][22]” in the documentation.

## HTML to PDF Conversion from a URL {#HTML-to-PDF-Conversion-from-a-URL}

You can convert the HTML web pages from the live URLs to the PDF documents by following the steps given below:

  1. Provide URL to an input stream object and open the stream
  2. Create an instance of the _**[Converter][12]**_ class with the input stream object
  3. Create an instance of the [**_PdfConvertOptions_**][13]
  4. Call the _**[convert()][14]**_ method with the output file path and convert options

The following code sample shows **how to convert HTML from a web URL to a PDF document using Java**.

{{< gist conholdate-gists 0e90868fedd7c20948490fb5f458432e "ConvertHTMLtoPDF_Java_ConvertFromURL.java" >}}

## Convert Specific Page Range of HTML to PDF {#Convert-Specific-Page-Range-of-HTML-to-PDF-using-Java}

You can convert specific pages from multipage HTML documents to PDF documents by following the steps given below:

  1. Create an instance of the _**[Converter][12]**_ class with the input file path
  2. Create an instance of [**_PdfConvertOptions_**][13]
  3. Set page number to start conversion from
  4. Set pages count to convert total number of pages
  5. Call the _**[convert()][14]**_ method with the output file path and convert options

The following code sample shows **how to convert specific pages from HTML to a PDF document using Java**.

{{< gist conholdate-gists 0e90868fedd7c20948490fb5f458432e "ConvertHTMLtoPDF_Java_ConvertNPages.java" >}}

## Convert HTML to PDF and Add Watermark {#Convert-HTML-to-PDF-and-Add-Watermark-using-Java}

You can convert HTML files to watermarked PDF documents by following the steps given below:

  1. Create an instance of the _**[Converter][12]**_ class 
  2. Provide the input file path to the constructor
  3. Create an instance of the [**_PdfConvertOptions_**][13]
  4. Create an instance of the **_[WatermarkOptions][23]_**
  5. Set various options such as _Text_, _Color_, _Width_, _Height_, _RotatationAngle_, etc.
  6. Call the _**[convert()][14]**_ method with the output file path and convert options

The following code sample shows **how to convert an HTML document to a watermarked PDF document using Java**.

{{< gist conholdate-gists 0e90868fedd7c20948490fb5f458432e "ConvertHTMLtoPDF_Java_ConvertAndAddWatermark.java" >}}

{{< figure align=center src="images/Convert-HTML-to-PDF-and-Add-Watermark-using-Java-1024x485.jpg" alt="Convert HTML to PDF and Add Watermark using Java" caption="Convert HTML to PDF and Add Watermark using Java">}}
 

The [WatermarkOptions][23] class provides several options to add watermark to the converted documents. It enables you to add text or image watermarks to the converted documents.

## Get a Free License

You can try the API without evaluation limitations by requesting [a free temporary license][25].

## Conclusion

In this article, you have learned **how to convert HTML to PDF documents** using Java. You have also learned **how to add watermarks to the converted PDF documents**. Moreover, you have learned **how to convert HTML using advanced PDF convert options** programmatically. This article also explained **how to convert HTML webpages from a live URL to a PDF document** using Java. You can learn more about GroupDocs.Conversion Java API using the [documentation][26]. In case of any ambiguity, please feel free to contact us on the [forum][27].

## See Also

  * [Convert PDF to Word using Java][28]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Convert-HTML-to-PDF.jpg
 [2]: #HTML-to-PDF-Conversion-Java-API
 [3]: #Convert-HTML-to-PDF-using-Java
 [4]: #Convert-HTML-to-PDF-with-Advanced-Options-using-Java
 [5]: #HTML-to-PDF-Conversion-from-a-URL
 [6]: #Convert-Specific-Page-Range-of-HTML-to-PDF-using-Java
 [7]: #Convert-HTML-to-PDF-and-Add-Watermark-using-Java
 [8]: https://docs.fileformat.com/web/html/
 [9]: https://docs.fileformat.com/pdf/
 [10]: https://products.groupdocs.com/conversion/java
 [11]: https://downloads.groupdocs.com/conversion/java
 [12]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
 [13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/PdfConvertOptions
 [14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Convert-HTML-to-PDF-using-Java.jpg
 [16]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Convert-HTML-to-PDF-with-Advanced-Options-using-Java.jpg
 [17]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions#setWidth(int)
 [18]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions#setHeight(int)
 [19]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions#setDpi(double)
 [20]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions#setPassword(java.lang.String)
 [21]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions#setRotate(com.groupdocs.conversion.options.convert.Rotation)
 [22]: https://docs.groupdocs.com/conversion/java/convert-to-pdf-with-advanced-options/
 [23]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/WatermarkOptions
 [24]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Convert-HTML-to-PDF-and-Add-Watermark-using-Java.jpg
 [25]: https://purchase.groupdocs.com/temporary-license
 [26]: https://docs.groupdocs.com/conversion/java/
 [27]: https://forum.groupdocs.com/c/conversion/11
 [28]: https://blog.conholdate.com/2021/07/26/convert-pdf-to-word-using-java/







