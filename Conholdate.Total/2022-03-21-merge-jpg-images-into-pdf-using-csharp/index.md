---
title: 'Merge JPG Images into PDF using C#'
author: Muzammil Khan
date: 2022-03-21T06:43:17+00:00
summary: 'We can easily convert and combine multiple JPG images into a single PDF document programmatically in C#. In this article, you will learn **how to merge JPG images into a PDF using C#**.'
url: /2022/03/21/merge-jpg-images-into-pdf-using-csharp/

categories:
  - Conholdate.Total Product Family
tags:
  - 'C# API to Merge JPG to PDF'
  - 'Convert JPG to PDF in C#'
  - 'Merge JPG in PDF using C#'
  - 'Combine JPG Images in PDF using C#'
  - JPG to PDF
  - Merge JPG into PDF
  - Merge Images into PDF
  - 'Aspose.Imaging for C#'
  - 'GroupDocs.Merger for .NET'
---

{{< figure align=center src="images/merge-jpg-images-into-pdf-using-csharp.jpg" alt="Merge JPG to PDF using C#">}}
 
[JPG][1] is the most widely used image file format for storing compressed images. [PDF][2], on the other hand, permits documents to be shared in a read-only format without compromising their style or layout. We may occasionally need to combine numerous JPG photos into a PDF document. In this article, we will learn **how to merge JPG images into a PDF document using C#**.

The following topics shall be covered in this article:

  * [C# API to Merge JPG Images into PDF][3]
  * [Convert JPG to PDF in C#][4]
  * [Append JPG Image in PDF using C#][5]
  * [Merge Multiple JPG Images into PDF using C#][6]

## C# API to Merge JPG Images into PDF {#CSharp-API-to-Merge-JPG-Images-into-PDF}

For merging two or more JPG images into a PDF document, we will follow a two-step procedure. Firstly, we will be using [Aspose.Imaging for .NET][7] to convert JPG to PDF, and then we will merge into a PDF document using [GroupDocs.Merger for.NET][8] API. Please either [download][9] the DLLs for the APIs or install them using [NuGet][10].

```
PM> Install-Package Aspose.Imaging
PM> Install-Package GroupDocs.Merger
```

## Convert JPG to PDF in C# {#Convert-JPG-to-PDF-in-CSharp}

We can convert any JPG image into a PDF document by following the steps given below:

  1. Load a JPG image using the _**[Image.Load()][11]**_ method.
  2. Finally, call the _**[Image.Save()][12]**_  method to save the image as PDF. It takes output file path as an argument.

The following code sample shows **how to convert a JPG to a PDF using C#**.

{{< gist conholdate-gists 0f339b7a9627b5f63555ad736cababa0 "MergeJPGImagesIntoPDF_CSharp_Convert.cs" >}}

{{< figure align=center src="images/Convert-JPG-to-PDF-in-CSharp.jpg" alt="Convert JPG to PDF in C#." caption="Convert JPG to PDF in C#.">}}

## Append JPG Image in PDF using C# {#Append-JPG-Image-in-PDF-using-CSharp}

We can append a JPG image into an existing PDF document by following the steps given below:

  1. Load a JPG image using the _**[Image.Load()][11]**_ method.
  2. Convert loaded image to a PDF and save in FileStream using the _**[Image.Save()][13]**_  method.
  3. Load an existing PDF using the _**[Merger][14]**_ class.
  4. Call the _**[Merger.Join()][15]**_ method to join the JPG converted PDF with the loaded PDF.
  5. Finally, call the _**[Merger.Save()][16]**_  method to save the merged PDF. It takes output file path as an argument.

The following code sample shows **how to append a JPG image into an existing PDF document using C#**.

{{< gist conholdate-gists 0f339b7a9627b5f63555ad736cababa0 "MergeJPGImagesIntoPDF_CSharp_Append.cs" >}}

{{< figure align=center src="images/Append-JPG-Image-in-PDF-using-CSharp.jpg" alt="Append JPG Image in PDF using C#." caption="Append JPG Image in PDF using C#.">}}

## Merge Multiple JPG Images into PDF using C# {#Merge-Multiple-JPG-Images-into-PDF-using-CSharp}

We can merge multiple JPG images into a PDF document by following the steps given below:

  1. Read all JPG image files from a directory one by one
  2. Load a JPG image using the _**[Image.Load()][11]**_ method.
  2. If it is first image then save a PDF file. Otherwise convert and save in FileStream.
  3. Load previously saved PDF using the _**[Merger][14]**_ class.
  4. Call the _**[Merger.Join()][15]**_ method to join the JPG converted PDF with the loaded PDF.
  5. Finally, call the _**[Merger.Save()][16]**_  method to save the merged PDF. It takes output file path as an argument.

The following code sample shows **how to merge multiple JPG images into a PDF document using C#**.

{{< gist conholdate-gists 0f339b7a9627b5f63555ad736cababa0 "MergeJPGImagesIntoPDF_CSharp_Combine.cs" >}}

{{< figure align=center src="images/Merge-Multiple-JPG-Images-into-PDF-using-CSharp.jpg" alt="Merge Multiple JPG Images into PDF using C#." caption="Merge Multiple JPG Images into PDF using C#.">}}

## Get a Free License

Please try the API without evaluation limitations by requesting [a free temporary license][17].

## Conclusion

In this article, we have learned how to:
  * save JPG image as a PDF document in C#;
  * insert image in a PDF document programmatically;
  * combine multiple images in a PDF document. 
 
Besides, you can learn more about Aspose.Email for C# API using the [documentation][18]. In case of any ambiguity, please feel free to contact us on the [forum][19].

## See Also

  * [Crop and Resize JPEG Images using C#][20]
  * [Merge Word Documents using C#][21]

  [1]: https://docs.fileformat.com/image/jpeg/
  [2]: https://docs.fileformat.com/pdf/
  [3]: #CSharp-API-to-Merge-JPG-Images-into-PDF
  [4]: #Convert-JPG-to-PDF-in-CSharp
  [5]: #Append-JPG-Image-in-PDF-using-CSharp
  [6]: #Merge-Multiple-JPG-Images-into-PDF-using-CSharp
  [7]: https://products.aspose.com/imaging/net/
  [8]: https://products.groupdocs.com/merger/net/
  [9]: https://downloads.aspose.com/imaging/net
  [10]: https://www.nuget.org/packages/Aspose.Imaging/
  [11]: https://apireference.aspose.com/imaging/net/aspose.imaging.image/load/methods/2
  [12]: https://apireference.aspose.com/imaging/net/aspose.imaging.image/save/methods/3
  [13]: https://apireference.aspose.com/imaging/net/aspose.imaging.datastreamsupporter/save/methods/1
  [14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
  [15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/join
  [16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.merger/save/methods/1
  [17]: https://purchase.conholdate.com/temporary-license
  [18]: https://docs.aspose.com/imaging/C#/
  [19]: https://forum.aspose.com/c/imaging/
  [20]: https://blog.conholdate.com/2022/01/05/crop-and-resize-jpeg-images-using-csharp/
  [21]: https://blog.conholdate.com/2021/11/19/merge-word-documents-using-csharp/