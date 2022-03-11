---
title: 'Convert Word Document to TIFF Image using C#'
author: Muzammil Khan
date: 2022-01-26T07:56:46+00:00
summary: 'As a C# developer, you can easily convert your Word documents to multipage TIFF images programmatically. In this article, you will learn **how to convert Word documents to TIFF images using C#**.'
url: /2022/01/26/convert-word-document-to-tiff-image-using-csharp/
categories:
  - Conholdate.Total Product Family
tags:
  - Convert Word to TIFF
  - 'Convert Word to TIFF in C#'
  - DOCX to TIFF
  - 'DOCX to TIFF using C#'
  - Word to TIFF
  - 'Word to TIFF using C#'

---


{{< figure align=center src="images/convert-word-document-to-tiff-image-using-csharp.jpg" alt="Convert Word Document to TIFF Image using C#">}}
 

We can easily convert Word documents ([DOC][2] or [DOCX][3]) to raster images. Raster images are capable of rendering complex and multicolored visuals. [TIFF][4] is a popular format to store raster images. It supports saving of multiple images in the form of pages. This distinguishing feature of TIFF format makes it a suitable option to present the Word documents in a read-only format. In this article, we will learn **how to convert a Word document to TIFF image using C#**.

The following topics shall be covered in this article:

  * [C# API to Convert Word to TIFF][5]
  * [Convert Word Document to TIFF in C#][6]
  * [Customize Word to TIFF Conversion in C#][7]

## C# API to Convert Word to TIFF {#CSharp-API-to-Convert-Word-to-TIFF}

For converting **DOC to TIFF** or **DOCX to TIFF**, we will be using [Aspose.Words for .NET][8] API. It enables us to generate, modify, convert, render and print files without utilizing Microsoft Word directly within cross-platform applications. Please either [download][9] the DLL of the API or install it using [NuGet][10].

```
PM> Install-Package Aspose.Words
```

## Convert Word Document to TIFF in C# {#Convert-Word-Document-to-TIFF-in-CSharp}

We can convert a Word document to a multipage TIFF by following the steps given below:

  1. Load a Word document using the _**[Document][11]**_ class.
  2. Save the document as TIFF file using _**[Save()][12]**_ method. It takes the path of the output file as an argument.

The following code sample shows how to convert a Word document to a TIFF using C#.

{{< gist conholdate-gists a121b1f499913836efe0136816cf13d5 "ConvertWordtoTIFF_CSharp_DOCXtoTIFF.cs" >}}

{{< figure align=center src="images/Convert-Word-Document-to-TIFF-in-CSharp-1024x611.jpg" alt="Convert Word Document to TIFF in C#." caption="Convert Word Document to TIFF in C#.">}}
 

## Customize Word to TIFF Conversion in C# {#Customize-Word-to-TIFF-Conversion-in-CSharp}

We can use different options to customize the conversion of Word documents to TIFF. For this purpose, the API provides the _ImageSaveOptions _class. It allows setting the image brightness, resolution, range of pages to convert, compression scheme, and so on. Please follow the steps mentioned below to set additional options while converting Word to TIFF.

  1. Firstly, load a Word document using the [Document](https://apireference.aspose.com/words/net/aspose.words/Document) class.
  2. Next, create an instance of the [ImageSaveOptions](https://apireference.aspose.com/words/net/aspose.words.saving/imagesaveoptions) class with the input image format as an argument.
  3. After that, set the desired options such as [TiffCompression](https://apireference.aspose.com/words/net/aspose.words.saving/imagesaveoptions/properties/tiffcompression), Resolution, etc.
  4. Finally, call the [Save(string, ImageSaveOptions)](https://apireference.aspose.com/words/net/aspose.words.document/save/methods/4) method to convert Word to TIFF.

The following code sample shows **how to convert a Word document to a TIFF image with additional options**.

{{< gist conholdate-gists a121b1f499913836efe0136816cf13d5 "ConvertWordtoTIFF_CSharp_ConvertWithOptions.cs" >}}

## Get a Free License

Please try the API without evaluation limitations by requesting [a free temporary license][14].

## Conclusion

In this article, we have learned **how to convert a Word document to a TIFF image using C#**. We have also seen how to apply additional options such as TIFF compression and resolution programmatically. Besides, you can learn more about Aspose.Words for .NET API using the [documentation][15]. In case of any ambiguity, please feel free to contact us on the [forum][16].

## See Also

  * [Merge Word Documents using C#][17]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/convert-word-document-to-tiff-image-using-csharp.jpg
 [2]: https://docs.fileformat.com/word-processing/doc/
 [3]: https://docs.fileformat.com/word-processing/docx/
 [4]: https://docs.fileformat.com/image/tiff/
 [5]: #CSharp-API-to-Convert-Word-to-TIFF
 [6]: #Convert-Word-Document-to-TIFF-in-CSharp
 [7]: #Customize-Word-to-TIFF-Conversion-in-CSharp
 [8]: https://products.aspose.com/words/net/
 [9]: https://downloads.aspose.com/words/net
 [10]: https://www.nuget.org/packages/aspose.words
 [11]: https://apireference.aspose.com/words/net/aspose.words/Document
 [12]: https://apireference.aspose.com/words/net/aspose.words.document/save/methods/2
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/Convert-Word-Document-to-TIFF-in-CSharp.jpg
 [14]: https://purchase.conholdate.com/temporary-license
 [15]: https://docs.aspose.com/words/net/
 [16]: https://forum.aspose.com/c/words
 [17]: https://blog.conholdate.com/2021/11/19/merge-word-documents-using-csharp/






