---
title: Convert PDF to HTML using Java
author: Muzammil Khan
date: 2022-02-19T17:14:51+00:00
summary: 'You can easily convert your PDF documents to HTML web pages to view them in any browser. In this article, **you will learn how to convert PDF documents to HTML webpages using Java**.'
url: /2022/02/19/convert-pdf-to-html-using-java/
categories:
  - Conholdate.Total Product Family
tags:
  - Convert PDF to HTML
  - Convert PDF to HTML Java API
  - GroupDocs.Conversion for Java
  - Java PDF Converter
  - PDF to HTML
  - PDF to HTML in Java

---


{{< figure align=center src="images/convert-pdf-to-html-using-java.jpg" alt="Convert PDF to HTML using Java">}}
 

[PDF][2] offers to share and print read-only documents without losing documents formatting. We can easily convert PDF documents to [HTML][3] web pages and view them in any browser. In this article, we will learn **how to convert PDF documents to HTML webpages using Java**.

The following topics shall be covered in this article:

  * [Java API to Convert PDF to HTML — Free Download][4]
  * [PDF to HTML Conversion using Java][5]
  * [Convert Range of Pages from PDF to HTML][6]
  * [Convert Specific Pages of PDF to HTML][7]
  * [Password-Protected PDF to HTML Conversion in Java][8]
  * [PDF to HTML Conversion with Watermark in Java][9]

## Java API to Convert PDF to HTML — Free Download {#Java-API-to-Convert-PDF-to-HTML—Free-Download}

For converting PDF to HTML, we will be using [GroupDocs.Conversion for Java][10] API. It provides fast, efficient, and reliable file conversion solutions to end-users. Please either [download][11] the JAR of the API or just add the following **_pom.xml_** configuration in a Maven-based Java application.

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
        <version>21.10.1</version> 
</dependency>
```

## PDF to HTML Conversion using Java {#PDF-to-HTML-Conversion-using-Java}

We can easily convert PDF documents to HTML webpages programmatically by following the simple steps given below:

  1. Firstly, load a PDF document using the **_[Converter][12]_** class.
  2. Next, create an instance of the [**_MarkupConvertOptions_**][13] class.
  3. Then, optionally set various convert options such as _FixedLayout_, _FixedLayoutShowBorders_, etc.
  4. Finally, convert PDF to HTML using the _**[Converter.Convert()][14]**_ method. It takes output file path and convert options as arguments.

The following code sample shows **how to convert a PDF document to an HTML webpage using Java**.

{{< gist conholdate-gists e185d60db439756a43186d91f1b3d602 "ConvertPDFtoHTML_Java_Convert.java" >}}

{{< figure align=center src="images/PDF-to-HTML-Conversion-using-Java-1024x512.jpg" alt="PDF to HTML Conversion using Java" caption="PDF to HTML Conversion using Java.">}}
 

## Convert Range of Pages from PDF to HTML {#Convert-Range-of-Pages-from-PDF-to-HTML}

We can convert a range of pages of a PDF document to HTML by following the steps given below:

  1. Firstly, load a PDF document using the **_[Converter][12]_** class.
  2. Next, create an instance of the [**_MarkupConvertOptions_**][13] class.
  3. Then, set page number to start conversion from.
  4. After that, set pages count to convert total number of pages.
  5. Finally, convert PDF to HTML using the _**[Converter.Convert()][14]**_ method.

The following code sample shows ****how to convert **a range of pages from a PDF document** to an HTML file** using Java**.

{{< gist conholdate-gists e185d60db439756a43186d91f1b3d602 "ConvertPDFtoHTML_Java_ConvertPageRange.java" >}}

## Convert Specific Pages of PDF to HTML {#Convert-Specific-Pages-of-PDF-to-HTML}

We can convert specific pages of a PDF document to HTML by following the steps given below:

  1. Firstly, load a PDF document using the **_[Converter][12]_** class.
  2. Next, create an instance of the [**_MarkupConvertOptions_**][13] class.
  3. Then, provide specific page numbers in a comma-separated list to convert.
  4. Finally, convert PDF to HTML using the _**[Converter.Convert()][14]**_ method.

The following code sample shows ****how to convert **specific pages of a PDF document** to an HTML file** using Java**.

{{< gist conholdate-gists e185d60db439756a43186d91f1b3d602 "ConvertPDFtoHTML_Java_ConvertSpecificPages.java" >}}

## Convert Password-Protected PDF to HTML in Java {#Convert-Password-Protected-PDF-to-HTML-in-Java}

We can also convert password-protected PDF documents to HTML webpages by following the steps given below:

  1. Firstly, provide password using the _**[PdfLoadOptions ][16]**_ class object.
  2. Next, load a PDF document using the **_[Converter][12]_** class with _**PdfLoadOptions**_.
  3. Then, create an instance of the [**_MarkupConvertOptions_**][13] class.
  4. Finally, convert PDF to HTML using the _**[Converter.Convert()][14]**_ method.

The following code sample shows **how to convert a password-protected PDF document to an HTML document using Java**.

{{< gist conholdate-gists e185d60db439756a43186d91f1b3d602 "ConvertPDFtoHTML_Java_ConvertPasswordProtected.java" >}}

## PDF to HTML Conversion with Watermark in Java {#PDF-to-HTML-Conversion-with-Watermark-in-Java}

We can convert PDF documents to HTML webpages and add watermarks to converted HTML files by following the steps given below:

  1. Firstly, load a PDF document using the **_[Converter][12]_** class.
  2. Next, create an instance of the _**[WatermarkOptions][17]**_ class.
  3. Then, set various options such as _Text_, _Color_, _Width_, _Height_, _Font_, etc.
  4. Next, create an instance of the [**_MarkupConvertOptions_**][13] class.
  5. After that, assign _**WatermarkOptions**_ to **_MarkupConvertOptions_**.
  6. Finally, convert PDF to HTML using the _**[Converter.Convert()][14]**_ method.

The following code sample shows **how to convert a PDF document to an HTML document with a watermark**.

{{< gist conholdate-gists e185d60db439756a43186d91f1b3d602 "ConvertPDFtoHTML_Java_ConvertWithWatermark.java" >}}

{{< figure align=center src="images/PDF-to-HTML-Conversion-with-Watermark-in-Java-1024x512.jpg" alt="PDF to HTML Conversion with Watermark in Java" caption="PDF to HTML Conversion with Watermark in Java.">}}
 

## Get a Free License

Please try the API without evaluation limitations by requesting [a free temporary license][19].

## Conclusion

In this article, we have learned **how to convert PDF documents to HTML webpages in Java**. We have also seen **how to convert a password-protected PDF file to HTML and add a watermark to the converted file** programmatically. Besides, you can learn more about GroupDocs.Conversion for Java API using the [documentation][20]. In case of any ambiguity, please feel free to contact us on the [forum][21].

## See Also

  * [Convert HTML to PDF using Java][22]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/convert-pdf-to-html-using-java.jpg
 [2]: https://docs.fileformat.com/pdf/
 [3]: https://docs.fileformat.com/web/html/
 [4]: #Java-API-to-Convert-PDF-to-HTML—Free-Download
 [5]: #PDF-to-HTML-Conversion-using-Java
 [6]: #Convert-Range-of-Pages-from-PDF-to-HTML
 [7]: #Convert-Specific-Pages-of-PDF-to-HTML
 [8]: #Convert-Password-Protected-PDF-to-HTML-in-Java
 [9]: #PDF-to-HTML-Conversion-with-Watermark-in-Java
 [10]: https://products.groupdocs.com/conversion/java
 [11]: https://downloads.groupdocs.com/conversion/java
 [12]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
 [13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/markupconvertoptions
 [14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/PDF-to-HTML-Conversion-using-Java.jpg
 [16]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.load/PdfLoadOptions
 [17]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/WatermarkOptions
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/PDF-to-HTML-Conversion-with-Watermark-in-Java.jpg
 [19]: https://purchase.conholdate.com/temporary-license
 [20]: https://docs.groupdocs.com/conversion/java/
 [21]: https://forum.groupdocs.com/c/conversion/11
 [22]: https://blog.conholdate.com/2021/09/10/convert-html-to-pdf-using-java/






