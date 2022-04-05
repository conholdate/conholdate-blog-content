---
title: 'Edit PDF Properties and Metadata using Java'
author: Muzammil Khan
date: 2022-04-05T15:15:07+00:00
summary: 'You can add/edit and read document information and XMP metadata of a PDF document programmatically. In this article, you will learn **how to edit PDF properties and metadata using Java**.'
url: /2022/04/05/edit-pdf-properties-and-metadata-using-java/
categories:
  - Conholdate.Total Product Family
tags:
  - 'Add Custom XMP Metadata Java'
  - 'Get Document Information in Java'
  - 'Get XMP Metadata using Java'
  - Read Custom XMP Metadata
  - 'Read Custom XMP Metadata Java'
  - 'Set Document Information in Java'
  - 'Set XMP Metadata using Java'
  - PDF Properties in Java
---

{{< figure align=center src="images/edit-pdf-properties-and-metadata-using-java.jpg" alt="Edit Metadata of PDF Files using Java">}}

The metadata of a document contains basic information about the document in the form of properties such as title, author, subject, keywords, etc. The Extensible Metadata Platform (XMP) is an XML-based standard for storing document metadata as a key/value pair. We can add, edit or read the document information and XMP metadata of a PDF document programmatically. In this article, we will learn **how to edit PDF properties and metadata using Java**.

The following topics shall be covered in this article:

  * [Java API to Edit PDF Properties and Metadata][1]
  * [Edit PDF Properties using Java][2]
  * [Read PDF Properties using Java][3]
  * [Get XMP Metadata from a PDF File][4]
  * [Set XMP Metadata in a PDF File][5]
  * [Customize XMP Metadata Namespace in a PDF File][6]

## Java API to Edit PDF Properties and Metadata {#Java-API-to-Edit-PDF-Properties-and-Metadata}

To edit [PDF][7] properties and metadata information, we will be using [Aspose.PDF for Java API][8]. It allows us to generate, modify, convert, render, secure, and print [supported documents][9] without using Adobe Acrobat. Please either [download][10] the JAR of the API or add the following _pom.xml_ configuration in a Maven-based Java application.

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
    <artifactId>aspose-pdf</artifactId>
    <version>22.3</version>
</dependency>
```

## Edit PDF Properties using Java {#Edit-PDF-Properties-using-Java}

We can edit PDF document information using the **_[PdfFileInfo][11]_** class that represents the meta-information of a PDF document. We can set various pre-defined properties by following the steps given below:

  1. Firstly, load a PDF document using the _**[PdfFileInfo][11]**_ class.
  2. Set various properties such as _Author_, _Creator_, _Keywords_, _Subject_, _Title_, etc.
  4. Finally, save the PDF file using the **_[saveNewInfo()][12]_** method with the output file path as an argument.

The following code sample shows **how to edit meta properties of a PDF file using Java**.

{{< gist conholdate-gists 87eb32e4bf59289493cee7606396922a "EditMetadataPDFProperties_Java_SetMetadata.java" >}}

{{< figure align=center src="images/Edit-PDF-Properties-using-Java.jpg" alt="Edit Meta Properties of a PDF File in Java." caption="Edit Meta Properties of a PDF File in Java.">}}
 

## Read PDF Properties using Java {#Read-PDF-Properties-using-Java}

We can read the basic information of a PDF document by following the steps given below:

  1. Firstly, load a PDF document using the _**[PdfFileInfo][11]**_ class.
  2. Finally, show the document information by reading the values of meta properties.

The following code sample shows **how to get meta properties of a PDF file using Java**.

{{< gist conholdate-gists 87eb32e4bf59289493cee7606396922a "EditMetadataPDFProperties_Java_GetMetadata.java" >}}

```
Subject :PDF Information
Title :Editing Metadata
Keywords :Aspose.Pdf, DOM, API
Creator :Aspose
Creation Date :D:20170612160123-04'00'
Modification Date :D:20220405214422+05'00'
Is Valid PDF :true
Is Encrypted :false
```

## Get XMP Metadata of a PDF File in Java {#Get-XMP-Metadata-of-a-PDF-File-in-Java}

We can read the XMP metadata of a PDF document by following the steps given below:

  1. Firstly, load a PDF document using the _**[Document][13]**_ class.
  2. Finally, read metadata using the _**[get_Item()][14]**_ method of the _**[Metadata][15]**_ class and extract the information.

The following code sample shows **how to get XMP metadata of a PDF file using Java**.

{{< gist conholdate-gists 87eb32e4bf59289493cee7606396922a "EditMetadataPDFProperties_Java_GetXMPMetadata.java" >}}

```
xmp:CreateDate : 2022-04-05T10:05:24.4
xmp:Nickname : Nickname
xmp:CustomProperty : Custom Value
```

## Set XMP Metadata in a PDF File in Java {#Set-XMP-Metadata-in-a-PDF-File-in-Java}

We can set the XMP metadata in a PDF file by following the steps given below:

  1. Firstly, load a PDF document using the _**[Document][13]**_ class.
  2. Next, set metadata values using the _**[set_Item()][16]**_ method of the **_[Metadata][15]_** class.
  3. Finally, save the PDF file using the _**[Document.save()][17]**_ method with the output file path as an argument.

The following code sample shows **how to set XMP metadata of a PDF file using Java**.

{{< gist conholdate-gists 87eb32e4bf59289493cee7606396922a "EditMetadataPDFProperties_Java_SetXMPMetadata.java" >}}

## Customize XMP Metadata Namespace in a PDF File {#Customize-XMP-Metadata-Namespace-in-a-PDF-File}

We can set the customized namespace URI instead of defined XMP specifications in a PDF file. For this purpose, the API provides the **_[registerNamespaceUri][18]_** method in the **_[Metadata][15]_** class. We can create a new metadata namespace with a prefix by following the steps given below:

  1. Firstly, load a PDF document using the [**_Document_**][13] class.
  2. Next, call the **_registerNamespaceUri()_** method with a prefix and namespace URI as arguments.
  3. Then, set metadata values using the _**[set_Item()][16]**_ method.
  4. Finally, save the PDF file using the **_[Document.Save()][17]_** method with the output file path as an argument.

The following code sample shows **how to set custom metadata namespace in a PDF file using Java**.

{{< gist conholdate-gists 87eb32e4bf59289493cee7606396922a "EditMetadataPDFProperties_Java_CustomizeMetadata.java" >}}

We can read the customized XMP metadata properties by following the steps mentioned earlier.

```
NamespaceUri: http:// myown.xyz.com/xap/1.0/
myown:ModifyDate: 2022-04-05T10:18:45.9
myown:CreateDate: 2022-04-05T10:18:45.9
myown:DeveloperName: Developer Name
myown:MyProperty: My Custom Value
```

## Get a Free API License {#Get-a-Free-License}

You can try the API without evaluation limitations by requesting [a free temporary license][19].

## Conclusion

In this article, we have learned how to:

  * add/ edit the basic information of a PDF document using Java;
  * set/ get the XMP metadata in a PDF file using Java;
  * set custom metadata namespace URI with a prefix.

Besides, you can learn more about Aspose.PDF for Java API using the [documentation][20]. In case of any ambiguity, please feel free to contact us on the [forum][21].

## See Also

  * [Convert PDF to HTML using Java][22]
  * [Add Footnotes and Endnotes in PDF using Java][23]

 [1]: #Java-API-to-Edit-PDF-Properties-and-Metadata
 [2]: #Edit-PDF-Properties-using-Java
 [3]: #Read-PDF-Properties-using-Java
 [4]: #Get-XMP-Metadata-of-a-PDF-File-in-Java
 [5]: #Set-XMP-Metadata-in-a-PDF-File-in-Java
 [6]: #Customize-XMP-Metadata-Namespace-in-a-PDF-File
 [7]: https://docs.fileformat.com/pdf/
 [8]: https://products.aspose.com/pdf/java/
 [9]: https://docs.aspose.com/pdf/java/supported-file-formats/
 [10]: https://downloads.aspose.com/pdf/java
 [11]: https://apireference.aspose.com/pdf/java/com.aspose.pdf.facades/PdfFileInfo
 [12]: https://apireference.aspose.com/pdf/java/com.aspose.pdf.facades/PdfFileInfo#saveNewInfo-java.lang.String-
 [13]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Document
 [14]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Metadata#get_Item-java.lang.String-
 [15]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Metadata
 [16]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Metadata#set_Item-java.lang.String-com.aspose.pdf.XmpValue-
 [17]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Document#save-java.lang.String-
 [18]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Metadata#registerNamespaceUri-java.lang.String-java.lang.String-
 [19]: https://purchase.conholdate.com/temporary-license
 [20]: https://docs.aspose.com/pdf/java
 [21]: https://forum.aspose.com/c/pdf/10
 [22]: https://blog.conholdate.com/2022/02/19/convert-pdf-to-html-using-java/
 [23]: https://blog.conholdate.com/2022/02/07/add-footnotes-and-endnotes-in-pdf-using-java/