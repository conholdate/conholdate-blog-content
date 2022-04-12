---
title: Extract Text and Images from PDF Documents using Java
author: Muzammil Khan
date: 2022-04-12T03:52:00+00:00
summary: 'As a Java developer, you can easily extract text and images from your PDF documents programmatically. In this article, you will learn **how to extract text and images from PDF documents using Java**.'
url: /2022/04/12/extract-text-and-images-from-pdf-documents-using-java/
categories:
  - Conholdate.Total Product Family
tags:
  - Document Text Extraction
  - Document Image Extraction
  - Extract Text
  - Extract Images
  - Extract Text from PDF
  - Extract Images from PDF
  - Text Extraction
  - Text Extraction API
  - Text Extractor API for Java
  - Image Extraction
  - Image Extration API
  - Image Extractor API for Java
---

{{< figure align=center src="images/extract-text-and-images-from-pdf-documents-using-java.jpg" alt="Extract Text and Images from PDF Documents using Java">}}

[PDF][1] is the most widely used digital document format. We can parse PDF documents and extract text and images from them programmatically. It could be useful in several cases, such as text analysis, information retrieval, document conversion, etc. In this article, we will learn **how to extract text and images from PDF documents using Java**.

The following topics shall be covered in this article:

  * [Java API to Extract Text and Images from PDF Documents][2]
  * [Extract Text from PDF Documents using Java][3]
  * [Extract Text from Specific Pages of a PDF Document using Java][4]
  * [Get Images from PDF Documents using Java][5]
  * [Extract Images from Specific Pages of a PDF Document using Java][6]
  * [Extract and Save Images to Files using Java][7]

## Java API to Extract Text and Images from PDF Documents {#Java-API-to-Extract-Text-and-Images-from-PDF-Documents}

For extracting text and images from PDF documents, we will be using [GroupDocs.Parser for Java][8] API. It allows the extraction of raw, formatted, and structured text, metadata, and images from files of the [supported formats][9]. Please either [download][10] the JAR of the API or add the following _pom.xml_ configuration in a Maven-based Java application.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
```

```
<dependency>
	<groupId>com.groupdocs</groupId>
	<artifactId>groupdocs-parser</artifactId>
	<version>22.3</version> 
</dependency>
```

## Extract Text from PDF Documents using Java {#Extract-Text-from-PDF-Documents-using-Java}

We can parse any PDF document and extract text by following the steps given below:

  * Firstly, load the PDF file using the [Parser][11] class.
  * Next, call the _[Parser.getText()][12]_ method to extract text from the loaded document.
  * Then, get results in the _[TextReader][13]_ class object.
  * Finally, call the _[TextReader.readToEnd()][14]_ method to read all characters from the current position to the end of the text reader and return them as one string.

The following code sample shows how to extract text from a PDF file using Java.

{{< gist conholdate-gists 3a3e972fa3e60818765be325c49d6615 "ExtractTextAndImagesPDF_Java_ExtractText.java" >}}

{{< figure align=center src="images/Extract-Text-from-PDF-Documents-using-Java.jpg" alt="Extract Text from PDF Documents using Java" caption="Extract Text from PDF Documents using Java">}}
 
## Extract Text from Specific Page of a PDF Document using Java {#Extract-Text-from-Specific-Page-of-a-PDF-Document-using-Java}

You can parse a PDF document and extract text from a specific page by following the simple steps mentioned below:

  * Firstly, load the PDF file using the [Parser][11] class.
  * Next, get document information using the _[Parser.getDocumentInfo()][15]_ method.
  * Then, check if the _[IDocumentInfo.getPageCount()][16]_ is not zero.
  * After that, call the [Parser.getText()][12] method with page index to extract text from that specific page and get results in [TextReader][13] class object.
  * Finally, show results by calling the [TextReader.readToEnd()][14] method to read the extracted text.

The following code sample shows how to extract text from a specific page using Java.

{{< gist conholdate-gists 3a3e972fa3e60818765be325c49d6615 "ExtractTextAndImagesPDF_Java_ExtractTextFromAPage.java" >}}

The API also enables to check whether the document supports the text sxtraction feature. For this purpose, we can use [Parser.getFeatures().isText()][17] property. Please read more about [supported features][18].

## Get Images from PDF Documents using Java {#Get-Images-from-PDF-Documents-using-Java}

We can parse any PDF document and extract images by following the steps given below:

  * Firstly, load the PDF file using the [Parser][11] class.
  * Next, call the _[Parser.getImages()][19]_ method and obtain collection of _[PageImageArea][20]_ objects from the loaded document.
  * Then, Check if the collection is not null.
  * After that, iterate over all the found images.
  * Finally, show images details.

The following code sample shows how to get images details from a PDF file using Java.

{{< gist conholdate-gists 3a3e972fa3e60818765be325c49d6615 "ExtractTextAndImagesPDF_Java_GetImages.java" >}}

{{< figure align=center src="images/Get-Images-from-PDF-Documents-using-Java.jpg" alt="Get images from PDF Documents using Java" caption="Get Images from PDF Documents using Java">}}

## Extract Images from Specific Page of a PDF Document using Java {#Extract-Images-from-Specific-Page-of-a-PDF-Document-using-Java}

We can extract images from a specific page by following the simple steps mentioned below:

  * Firstly, load the PDF file using the [Parser][11] class.
  * Next, get document information using the _[Parser.getDocumentInfo()][15]_ method.
  * Then, check if the _[IDocumentInfo.getPageCount()][16]_ is not zero.
  * After that, call the [Parser.getImages()][21] method with page index to extract images from that specific page.
  * Finally, iterate over all the found images and show details.

The following code sample shows how to extract images from a specific page using Java.

{{< gist conholdate-gists 3a3e972fa3e60818765be325c49d6615 "ExtractTextAndImagesPDF_Java_GetImagesFromPage.java" >}}

## Extract and Save Images to Files using Java {#Extract-and-Save-Images-to-Files-using-Java}

We can also save the extracted images by following the steps given below:

  * Firstly, load the PDF file using the [Parser][11] class.
  * Next, call the _[Parser.getImages()][19]_ method and obtain collection of PageImageArea objects from the loaded document.
  * Then, create an instance of the _[ImageOptions][22]_ class and set the image format.
  * After that, iterate over all the found images.
  * Finally, save using the _[save()][23]_ method. It takes the output file path and ImageOptions as arguments.

The following code sample shows how to extract and save images to files using Java.

{{< gist conholdate-gists 3a3e972fa3e60818765be325c49d6615 "ExtractTextAndImagesPDF_Java_SaveImages.java" >}}

{{< figure align=center src="images/Extract-and-Save-Images-to-Files-using-Java.jpg" alt="Extract and Save images to files using Java" caption="Extract and Save images to files using Java">}}

## Get a Free License
You can try the API without evaluation limitations by requesting [a free temporary license][24].

## Conclusion
In this article, we have learned how to:

  * extract all the text from a whole PDF document or specific pages of the document using Java;
  * extract images from a PDF file programmatically;
  * save extracted images on a local disk.

Besides, you can learn more about GroupDocs.Parser for Java API using the [documentation][25]. In case of any ambiguity, please feel free to contact us on the [forum][26].

## See Also

  * [Extract Text from Word Documents using Java][27]

 [1]: https://docs.fileformat.com/pdf/
 [2]: https://docs.fileformat.com/PDF-processing/doc/
 [3]: https://docs.fileformat.com/PDF-processing/docx/
 [4]: #Java-API-to-Extract-Text-from-PDF-Documents
 [5]: #Extract-Text-from-PDF-Documents-using-Java
 [6]: #Extract-Text-from-Specific-Pages-of-a-Document-using-Java
 [7]: #Get-Highlight-from-Documents-using-Java
 [8]: https://products.groupdocs.com/parser/java/
 [9]: https://docs.groupdocs.com/parser/java/supported-document-formats/
 [10]: https://downloads.groupdocs.com/parser/java
 [11]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser
 [12]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getText()
 [13]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/TextReader
 [14]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/TextReader#readToEnd()
 [15]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getDocumentInfo()
 [16]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/IDocumentInfo#getPageCount()
 [17]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/Features#isText()
 [18]: https://docs.groupdocs.com/parser/java/get-supported-features/
 [19]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getImages()
 [20]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/PageImageArea
 [21]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getImages(int)
 [22]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/ImageOptions
 [23]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/PageImageArea#save(java.lang.String,%20com.groupdocs.parser.options.ImageOptions)
 [24]: https://purchase.groupdocs.com/temporary-license
 [25]: https://docs.groupdocs.com/parser/java/
 [26]: https://forum.groupdocs.com/c/parser/
 [27]: https://blog.conholdate.com/2021/10/13/extract-text-from-word-documents-using-java/







