---
title: 'Render PowerPoint Presentation using C#'
author: Muzammil Khan
date: 2022-03-29T06:43:17+00:00
summary: 'As a C# developer, you can easily render or view PowerPoint presentations (PPT/PPTX) in HTML or PDF documents programmatically. In this article, you will learn **how to render a PowerPoint presentation using C#**.'
url: /2022/03/29/render-powerpoint-presentation-using-csharp/

categories:
  - Conholdate.Total Product Family
tags:
  - 'C# API to View PPTX'
  - 'PPTX Viewer'
  - 'C# PPTX Viewer'
  - 'PowerPoint Viewer in C#'
  - 'Convert PPTX to PDF in C#'
  - 'Convert PPTX to HTML using C#'
  - Render PowerPoint
  - PPTX to PDF
  - PPTX to HTML
  - Convert PPTX Slides to JPG
  - 'GroupDocs.Viewer for .NET'
---

{{< figure align=center src="images/render-powerpoint-presentation-using-csharp.jpg" alt="Render PowerPoint Presentation using C#">}}
 
MS PowerPoint allows presenting information or data in the form of presentation slides. It also provides a PowerPoint viewer to view all the slides as a slide show. In certain cases, we may need to render PowerPoint presentation slides in other formats such as [PDF][1], [JPG][2] images, or [HTML][3]. In this article, we will learn **how to render a PowerPoint presentation in other formats using C#**.

The following topics shall be covered in this article:

  * [C# API to Render PowerPoint Presentation][4]
  * [Render PowerPoint Presentation in PDF][5]
  * [View PowerPoint Presentation in HTML][6]
  * [Render PowerPoint Notes in HTML][28]
  * [Convert PowerPoint Slides into JPG Images][7]

## C# API to Render PowerPoint Presentation {#CSharp-API-to-Render-PowerPoint-Presentation}

For rendering [PPT][8] or [PPTX][9] files in other formats, we will be using [GroupDocs.Viewer for .NET][10] API. It allows the rendering and viewing of [supported PowerPoint presentation formats][11] programmatically. Please either [download][12] the DLL for the API or install it using [NuGet][13].

```
PM> Install-Package GroupDocs.Viewer
```

## Render PowerPoint Presentation in PDF using C# {#Render-PowerPoint-Presentation-in-PDF-using-CSharp}

We can render a PowerPoint presentation into a PDF document by following the steps given below:

  1. Load a PowerPoint presentation using the _**[Viewer][14]**_ class.
  2. Create an instance of the _**[PdfViewOptions][15]**_ class with the output PDF file path as an argument.
  3. Finally, call the _**[View()][16]**_ method to save the PPTX as PDF. It takes _**PdfViewOptions**_ object as an argument.

The following code sample shows **how to render a PPTX file to a PDF using C#**.

{{< gist conholdate-gists a156e4aa9c6bc7c8009cabc0f14cf824 "RenderPPTX_CSharp_RenderInPDF.cs" >}}

{{< figure align=center src="images/Render-PowerPoint-Presentation-in-PDF-using-CSharp.jpg" alt="Render PowerPoint Presentation in PDF using C#." caption="Render PowerPoint Presentation in PDF using C#.">}}

## View PowerPoint Presentation in HTML using C# {#View-PowerPoint-Presentation-in-HTML-using-CSharp}

We can also render a PowerPoint presentation in HTML to view in the browser by following the steps given below:

  1. Load a PowerPoint presentation using the _**[Viewer][14]**_ class.
  2. Create an instance of the _**[HtmlViewOptions][17]**_ class using the _**[ForEmbeddedResources][18]**_ method. It takes the output HTML file path as an argument.
  3. Set various _**HtmlViewOptions**_ such as RenderToSinglePage, etc.
  4. Finally, call the **_[View()][16]_** method to save the PPTX as HTML. It takes _**HtmlViewOptions**_ object as an argument.

The following code sample shows **how to render a PPTX as HTML using C#**.

{{< gist conholdate-gists a156e4aa9c6bc7c8009cabc0f14cf824 "RenderPPTX_CSharp_RenderInHTML.cs" >}}

{{< figure align=center src="images/View-PowerPoint-Presentation-in-HTML-using-CSharp.jpg" alt="View PowerPoint Presentation in HTML using C#." caption="View PowerPoint Presentation in HTML using C#.">}}

## Render PowerPoint Notes in HTML using C# {#Render-PowerPoint-Notes-in-HTML-using-CSharp}

We can render PowerPoint presentation notes in HTML by following the steps mentioned earlier. However, we just need to enable rendering of notes as shown below:

```
viewOptions.RenderNotes = true;
```

The following code sample shows **how to render PowerPoint presentation notes in HTML using C#**.

{{< gist conholdate-gists a156e4aa9c6bc7c8009cabc0f14cf824 "RenderPPTX_CSharp_RenderNotesInHTML.cs" >}}

{{< figure align=center src="images/Render-PowerPoint-Presentation-Notes-in-HTML-using-CSharp.jpg" alt="Render PowerPoint Presentation Notes in HTML using C#." caption="Render PowerPoint Presentation Notes in HTML using C#.">}}

## Convert PowerPoint Slides into JPG Images using C# {#Convert-PowerPoint-Slides-into-JPG-images-using-CSharp}

We can render a PowerPoint presentation and save all slides as JPG images by following the steps given below:

  1. Load a PowerPoint presentation using the _**[Viewer][14]**_ class.
  2. Create an instance of the _**[ViewInfoOptions][19]**_ class using the _**[ForJpgView][20]**_ method.
  3. Get _**[ViewInfo][21]**_ using the _**[GetViewInfo][22]**_ method.
  4. Read the _**ViewInfo.Pages.Count**_ property and iterate over all the slides one by one.
  5. Create an instance of the _**[JpgViewOptions][23]**_ class.
  6. Finally, call the _**[View()][16]**_  method to save the slide as JPG. It takes the JpgViewOptions object and Page number as arguments.

The following code sample shows **how to render PowerPoint slides into JPG images using C#**.

{{< gist conholdate-gists a156e4aa9c6bc7c8009cabc0f14cf824 "RenderPPTX_CSharp_RenderInJPG.cs" >}}

{{< figure align=center src="images/Convert-PowerPoint-Slides-into-JPG-images-using-CSharp.jpg" alt="Convert PowerPoint Slides into JPG Images using C#." caption="Convert PowerPoint Slides into JPG Images using C#.">}}

## Get a Free License

Please try the API without evaluation limitations by requesting [a free temporary license][24].

## Conclusion

In this article, we have learned how to:
  * render PowerPoint slides from PPTX to a PDF in C#;
  * view PowerPoint slides in the browser programmatically;
  * convert PowerPoint slides into JPG images. 
 
Besides, you can learn more about GroupDocs.Viewer for .NET API using the [documentation][25]. In case of any ambiguity, please feel free to contact us on the [forum][26].

## See Also

  * [Excel File Viewer – Display Excel Data using C#][27]

  [1]: https://docs.fileformat.com/pdf/
  [2]: https://docs.fileformat.com/image/jpeg/
  [3]: https://docs.fileformat.com/web/html/
  [4]: #CSharp-API-to-Render-PowerPoint-Presentation
  [5]: #Render-PowerPoint-Presentation-in-PDF-using-CSharp
  [6]: #View-PowerPoint-Presentation-in-HTML-using-CSharp
  [7]: #Convert-PowerPoint-Slides-into-JPG-images-using-CSharp
  [8]: https://docs.fileformat.com/presentation/ppt/
  [9]: https://docs.fileformat.com/presentation/pptx/
  [10]: https://products.groupdocs.com/viewer/net/
  [11]: https://docs.groupdocs.com/viewer/net/view-powerpoint-presentations/#supported-presentation-formats
  [12]: https://downloads.groupdocs.com/viewer/net
  [13]: https://www.nuget.org/packages/GroupDocs.Viewer/
  [14]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
  [15]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
  [16]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
  [17]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
  [18]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options.htmlviewoptions/forembeddedresources/methods/4
  [19]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/viewinfooptions
  [20]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/viewinfooptions/methods/forjpgview
  [21]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.results/viewinfo
  [22]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/getviewinfo
  [23]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/jpgviewoptions
  [24]: https://purchase.conholdate.com/temporary-license
  [25]: https://docs.groupdocs.com/viewer/net/
  [26]: https://forum.groupdocs.com/c/viewer/
  [27]: https://blog.conholdate.com/2022/02/25/excel-file-viewer-display-excel-data-using-csharp/
  [28]: #Render-PowerPoint-Notes-in-HTML-using-CSharp