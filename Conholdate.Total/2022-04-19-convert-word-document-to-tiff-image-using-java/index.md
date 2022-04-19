---
title: 'Convert Word Document to TIFF Image using Java'
author: Muzammil Khan
date: 2022-04-19T07:56:46+00:00
summary: 'As a Java developer, you can easily convert your Word documents to multipage TIFF images programmatically. In this article, you will learn **how to convert Word documents to TIFF images using Java**.'
url: /2022/04/19/convert-word-document-to-tiff-image-using-java/
categories:
  - Conholdate.Total Product Family
tags:
  - Convert Word to TIFF
  - 'Convert Word to TIFF in Java'
  - DOCX to TIFF
  - 'DOCX to TIFF using Java'
  - Word to TIFF
  - 'Word to TIFF using Java'
  - Word2Tiff

---


{{< figure align=center src="images/convert-word-document-to-tiff-image-using-java.jpg" alt="Convert Word Document to TIFF Image using Java">}}

[TIFF][1] is a popular format to store multiple images in the form of pages. This distinguishing feature of the TIFF format allows sharing of Word documents in a read-only format. We can easily convert Word documents ([DOC][2] or [DOCX][3]) to TIFF images programmatically in Java applications. In this article, we will learn **how to convert a Word document to a TIFF image using Java**.

The following topics shall be covered in this article:

  * [Java API to Convert Word to TIFF][4]
  * [Convert Word Document to TIFF in Java][5]
  * [Customize Word to TIFF Conversion in Java][6]

## Java API to Convert Word to TIFF {#Java-API-to-Convert-Word-to-TIFF}

For converting **DOC to TIFF** or **DOCX to TIFF**, we will be using [Aspose.Words for Java][7] API. It enables us to generate, modify, convert, render and print Word documents without utilizing Microsoft Word directly within cross-platform applications. Please either [download][8] the JAR of the API or add the following pom.xml configuration in a Maven-based Java application.

```
<repository>
    <id>AsposeJavaAPI</id>
    <name>Aspose Java API</name>
    <url>https://repository.aspose.com/repo/</url>
</repository>
```
```
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>22.4</version>
    <type>pom</type>
</dependency>
```

## Convert Word Document to TIFF in Java {#Convert-Word-Document-to-TIFF-in-java}

We can convert a Word document to a multipage TIFF by following the steps given below:

  1. Load a Word document using the _**[Document][9]**_ class.
  2. Save the document as a TIFF file using the _**[Save()][10]**_ method. It takes the path of the output file as an argument.

The following code sample shows how to convert a Word document to a TIFF using Java.

{{< gist conholdate-gists f660c0b5e020a77f970c1b87f9eb2661 "WordToTiff_Java_Convert.java" >}}

{{< figure align=center src="images/Convert-Word-Document-to-TIFF-in-java.jpg" alt="Convert Word Document to TIFF in Java." caption="Convert Word Document to TIFF in Java.">}}
 

## Customize Word to TIFF Conversion in Java {#Customize-Word-to-TIFF-Conversion-in-java}

We can customize the conversion of Word documents to TIFF by applying various options provided by the API. For this purpose, the API provides the _ImageSaveOptions_ class. It allows setting the image brightness, resolution, range of pages to convert, compression scheme, and so on. Please follow the steps mentioned below to set additional options while converting Word to TIFF.

  1. Firstly, load a Word document using the [Document][9] class.
  2. Next, create an instance of the [ImageSaveOptions][11] class with the input image format as an argument.
  3. After that, set the desired options such as [TiffCompression][12], Resolution, etc.
  4. Finally, call the [Save(string, ImageSaveOptions)][13] method to convert Word to TIFF.

The following code sample shows **how to convert a Word document to a TIFF image with additional options**.

{{< gist conholdate-gists f660c0b5e020a77f970c1b87f9eb2661 "WordToTiff_Java_ConvertWithOptions.java" >}}

## Get a Free License

Please try the API without evaluation limitations by requesting [a free temporary license][14].

## Conclusion

In this article, we have learned **how to convert a Word document to a TIFF image using Java**. We have also seen how to apply additional options such as TIFF compression, brightness, and image resolution programmatically. Besides, you can learn more about Aspose.Words for Java API using the [documentation][15]. In case of any ambiguity, please feel free to contact us on the [forum][16].

## See Also

  * [MS Word Automation – Create, Edit, or Convert Word Documents using Java][17]

 [1]: https://docs.fileformat.com/image/tiff/
 [2]: https://docs.fileformat.com/word-processing/doc/
 [3]: https://docs.fileformat.com/word-processing/docx/
 [4]: #java-API-to-Convert-Word-to-TIFF
 [5]: #Convert-Word-Document-to-TIFF-in-java
 [6]: #Customize-Word-to-TIFF-Conversion-in-java
 [7]: https://products.aspose.com/words/java/
 [8]: https://downloads.aspose.com/words/java
 [9]: https://apireference.aspose.com/words/java/com.aspose.words/Document
 [10]: https://apireference.aspose.com/words/java/com.aspose.words/document#save(java.lang.String,int)
 [11]: https://apireference.aspose.com/words/java/com.aspose.words/ImageSaveOptions
 [12]: https://apireference.aspose.com/words/java/com.aspose.words/imagesaveoptions#TiffCompression
 [13]: https://apireference.aspose.com/words/java/com.aspose.words/document#save(java.lang.String,com.aspose.words.SaveOptions)
 [14]: https://purchase.conholdate.com/temporary-license
 [15]: https://docs.aspose.com/words/java/
 [16]: https://forum.aspose.com/c/words
 [17]: https://blog.conholdate.com/2021/12/01/ms-word-automation-create-edit-or-convert-word-documents-using-java/