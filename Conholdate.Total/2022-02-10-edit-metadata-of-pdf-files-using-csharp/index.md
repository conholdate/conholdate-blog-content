---
title: 'Edit Metadata of PDF Files using C#'
author: Muzammil Khan
date: 2022-02-10T15:15:07+00:00
summary: ' You can add/edit document information and XMP metadata in a PDF document programmatically. In this article, you will learn **how to edit the metadata of PDF files using C#**.'
url: /2022/02/10/edit-metadata-of-pdf-files-using-csharp/
categories:
  - Conholdate.Total Product Family
tags:
  - 'Add Custom XMP Metadata C#'
  - 'Get Document Information in C#'
  - 'Get XMP Metadata using C#'
  - Read Custom XMP Metadata
  - 'Read Custom XMP Metadata C#'
  - 'Set Document Information in C#'
  - 'Set XMP Metadata using C#'

---


{{< figure align=center src="images/edit-metadata-of-pdf-files-using-csharp.jpg" alt="Edit Metadata of PDF Files using C#">}}
 

Metadata is a business card of a particular digital doc­ument that consists of a set of properties. These properties contain basic information about the document such as title, author, subject, keywords, etc. Extensible Metadata Platform (XMP) is an XML-based for­mat that allows saving the document metadata in a key/value pair. We can add/edit document information and XMP metadata in a PDF document programmatically. In this article, we will learn **how to edit the metadata of PDF files using C#**.

The following topics shall be covered in this article:

  * [C# API to Edit Metadata of PDF Files][2]
  * [Edit Metadata of a PDF File][3]
  * [Get Metadata of a PDF File][4]
  * [Get XMP Metadata from a PDF File][5]
  * [Set XMP Metadata in a PDF File][6]
  * [Customize XMP Metadata Namespace in a PDF File][7]

## C# API to Edit Metadata of PDF Files {#CSharp-API-to-Edit-Metadata-of-PDF-Files}

To edit metadata information in a [PDF][8] document, we will be using [Aspose.PDF for .NET API][9]. It allows us to generate, modify, convert, render, secure and print [supported documents][10] without using Adobe Acrobat. Please either [download][11] the DLL of the API or install it using [NuGet][12].

```
PM> Install-Package Aspose.Pdf
```

## Edit Metadata of a PDF File in C# {#Edit-Metadata-of-a-PDF-File-in-CSharp}

We can edit PDF document information using the **_[DocumentInfo][13]_** class that represents the meta-information of a PDF document. We can set various pre-defined **[properties][14]** by following the steps given below:

  1. Firstly, load a PDF document using the [**_Document_**][15] class.
  2. Next, create an instance of the **_[DocumentInfo][13]_** class with the _Document_ class object as an argument.
  3. Then, set various properties such as _Author_, _CreationDate_, _Keywords_, _Subject_, _Title_, etc.
  4. Finally, save the PDF file using the **_[Document.Save()][16]_** method with the output file path as an argument.

The following code sample shows **how to edit metadata of a PDF file using C#**.

{{< gist conholdate-gists 1330a92300dfb2866eeb4b8c49510362 "EditMetadataPDF_CSharp_SetMetadata.cs" >}}

{{< figure align=center src="images/Edit-Metadata-of-a-PDF-File-in-CSharp-1024x940.jpg" alt="Edit Metadata of a PDF File in C#." caption="Edit Metadata of a PDF File in C#.">}}
 

## Get Metadata of a PDF File using C# {#Get-Metadata-of-a-PDF-File-using-CSharp}

We can read the basic information of a PDF document ****by following the steps given below:

  1. Firstly, load a PDF document using the [**_Document_**][15] class.
  2. Next, create an instance of the **_[DocumentInfo][13]_** class with the _Document_ class object as an argument.
  3. Finally, show the document information by reading the values of metadata properties.

The following code sample shows **how to get metadata of a PDF file using C#**.

{{< gist conholdate-gists 1330a92300dfb2866eeb4b8c49510362 "EditMetadataPDF_CSharp_GetMetadata.cs" >}}

```
Author: Aspose
Creation Date: 2/9/2022 9:47:00 AM
Keywords: Aspose.Pdf, DOM, API
Modify Date: 2/9/2022 9:47:00 AM
Subject: PDF Information
Title: Setting PDF Document Information
```

## Get XMP Metadata of a PDF File using C# {#Get-XMP-Metadata-of-a-PDF-File-using-CSharp}

We can read the XMP metadata of a PDF document ****by following the steps given below:

  1. Firstly, load a PDF document using the [**_Document_**][15] class.
  2. Finally, read the [**_Metadata_**][18] property and extract the information.

The following code sample shows **how to get XMP metadata of a PDF file using C#**.

{{< gist conholdate-gists 1330a92300dfb2866eeb4b8c49510362 "EditMetadataPDF_CSharp_GetXMPMetadata.cs" >}}

```
xmp:CreateDate: 2022-02-09T08:57:00.7+05:00
xmp:Nickname: Nickname
xmp:CustomProperty: Custom Value
```

## Set XMP Metadata in a PDF File using C# {#Set-XMP-Metadata-in-a-PDF-File-using-CSharp}

We can set the XMP metadata in a PDF file using the **_[Metadata][18]_** property of the **_[Document][19]_** class by following the steps given below:

  1. Firstly, load a PDF document using the [**_Document_**][15] class.
  2. Next, set metadata values using the [**_Metadata_**][18] property.
  3. Finally, save the PDF file using the **_[Document.Save()][16]_** method with the output file path as an argument.

The following code sample shows **how to set XMP metadata of a PDF file using C#**.

{{< gist conholdate-gists 1330a92300dfb2866eeb4b8c49510362 "EditMetadataPDF_CSharp_SetXMPMetadata.cs" >}}

## Customize XMP Metadata Namespace in a PDF File {#Customize-XMP-Metadata-Namespace-in-a-PDF-File}

Adobe XMP Specification defines the following four (4) core namespaces that we normally use:

  1. [Dublin Core][20] with namespace URI as “[http://purl.org/dc/elements/1.1/][21]” and its preferred namespace prefix is ‘dc’.
  2. The [XMP][22] with namespace URI as http://ns.adobe.com/xap/1.0/ and its preferred namespace prefix is ‘xmp’.
  3. [XMP Rights Management][24] with namespace URI as http://ns.adobe.com/xap/1.0/rights/ and its preferred namespace prefix is ‘xmpRights’.
  4. [XMP Media Management][26] with namespace URI as http://ns.adobe.com/xap/1.0/mm/ and its preferred namespace prefix is ‘xmpMM’.

We can also set the customized namespace URI instead of defined XMP specifications in a PDF file. For this purpose, the API provides the **_[RegisterNamespaceUri][28]_** method in the **_[Metadata][29]_** class. We can create a new metadata namespace with a prefix by following the steps given below:

  1. Firstly, load a PDF document using the [**_Document_**][15] class.
  2. Next, call the **_RegisterNamespaceUri_** method with a prefix and namespace URI as arguments.
  3. Then, set metadata values using the [**_Metadata_**][18] property.
  4. Finally, save the PDF file using the **_[Document.Save()][16]_** method with the output file path as an argument.

The following code sample shows **how to set custom metadata namespace in a PDF file using C#**.

{{< gist conholdate-gists 1330a92300dfb2866eeb4b8c49510362 "EditMetadataPDF_CSharp_SetCustomNamespace.cs" >}}

We can read the customized XMP metadata properties by following the steps mentioned earlier.

```
myown:ModifyDate: 2022-02-09T10:38:26.8+05:00
myown:CreateDate: 2022-02-09T10:38:26.8+05:00
myown:DeveloperName: Developer Name
myown:MyProperty: My Custom Value
```

## Get a Free API License {#Get-a-Free-License}

You can try the API without evaluation limitations by requesting [a free temporary license][30].

## Conclusion

In this article, we have learned how to:

  * add/ edit the basic information of a PDF documents using C#;
  * set/ get the XMP metadata in a PDF file using C#;
  * set custom metadata namespace URI with a prefix.

Besides, you can learn more about Aspose.PDF for .NET API using the [documentation][31]. In case of any ambiguity, please feel free to contact us on the [forum][32].

## See Also

  * [Add Headers and Footers in PDF using C#][33]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/edit-metadata-of-pdf-files-using-csharp.jpg
 [2]: #CSharp-API-to-Edit-Metadata-of-PDF-Files
 [3]: #Edit-Metadata-of-a-PDF-File-in-CSharp
 [4]: #Get-Metadata-of-a-PDF-File-using-CSharp
 [5]: #Get-XMP-Metadata-of-a-PDF-File-using-CSharp
 [6]: #Set-XMP-Metadata-in-a-PDF-File-using-CSharp
 [7]: #Customize-XMP-Metadata-Namespace-in-a-PDF-File
 [8]: https://docs.fileformat.com/pdf/
 [9]: https://products.aspose.com/pdf/net/
 [10]: https://docs.aspose.com/pdf/net/supported-file-formats/
 [11]: https://downloads.aspose.com/pdf/net
 [12]: https://www.nuget.org/packages/aspose.pdf
 [13]: https://apireference.aspose.com/pdf/net/aspose.pdf/documentinfo
 [14]: https://apireference.aspose.com/pdf/net/aspose.pdf/documentinfo/properties/index
 [15]: https://apireference.aspose.com/pdf/net/aspose.pdf/document
 [16]: https://apireference.aspose.com/pdf/net/aspose.pdf.document/save/methods/4
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Edit-Metadata-of-a-PDF-File-in-CSharp.jpg
 [18]: https://apireference.aspose.com/pdf/net/aspose.pdf/document/properties/metadata
 [19]: https://apireference.aspose.com/pdf/net/aspose.pdf/document/
 [20]: https://wwwimages2.adobe.com/content/dam/acom/en/devnet/xmp/pdfs/XMP%20SDK%20Release%20cc-2016-08/XMPSpecificationPart1.pdf#G5.785800
 [21]: http://purl.org/dc/elements/1.1/%22
 [22]: https://wwwimages2.adobe.com/content/dam/acom/en/devnet/xmp/pdfs/XMP%20SDK%20Release%20cc-2016-08/XMPSpecificationPart1.pdf#G5.810413
 [23]: http://ns.adobe.com/xap/1.0/%22
 [24]: https://wwwimages2.adobe.com/content/dam/acom/en/devnet/xmp/pdfs/XMP%20SDK%20Release%20cc-2016-08/XMPSpecificationPart1.pdf#G5.802526
 [25]: http://ns.adobe.com/xap/1.0/rights/%22
 [26]: https://wwwimages2.adobe.com/content/dam/acom/en/devnet/xmp/pdfs/XMP%20SDK%20Release%20cc-2016-08/XMPSpecificationPart1.pdf#G5.785832
 [27]: http://ns.adobe.com/xap/1.0/mm/%22
 [28]: https://apireference.aspose.com/pdf/net/aspose.pdf/metadata/methods/registernamespaceuri
 [29]: https://apireference.aspose.com/pdf/net/aspose.pdf/metadata
 [30]: https://purchase.conholdate.com/temporary-license
 [31]: https://docs.aspose.com/pdf/net
 [32]: https://forum.aspose.com/c/pdf/10
 [33]: https://blog.conholdate.com/2021/12/15/add-headers-and-footers-in-pdf-using-csharp/






