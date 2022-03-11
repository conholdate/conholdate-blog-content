---
title: "'使用 C# 将 PDF 转换为图像'"
author: Muzammil Khan
date: 2021-09-23T06:07:49+00:00
summary: "作为 C# 开发人员，您可以在 .NET 应用程序中以编程方式轻松地将 PDF 文件的所有页面转换为 PNG、JPG、TIFF 或 BMP 图像。在本文中，您将学习**如何使用 C# 将 PDF 转换为图像**。"
url: /zh/2021/09/23/convert-pdf-to-images-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "CSharp API 将 PDF 转换为图像"
  - "从PDF中提取图像"
  - "PDF转BMP"
  - "PDF转图片"
  - "PDF转图片 conversion"
  - "PDF转JPG"
  - "PDF转PNG"
  - "PDF 转 TIFF"

---


{{< figure align=center src="images/convert-pdf-to-images-using-csharp.jpg" alt="使用 C# 将 PDF 转换为图像">}}
 

您可能需要将 PDF 文档的页面作为图像文件与他人共享。作为 C# 开发人员，您可以在 .NET 应用程序中以编程方式轻松地将 PDF 文件转换为 PNG、JPG、TIFF 或 BMP。在本文中，您将学习**如何使用 C# 将 PDF 转换为图像**。

本文讨论/涵盖了以下主题：

  * [PDF 到图像转换 C# API][2]
  * [使用 C# 将 PDF 转换为 PNG 图像][3]
  * [使用 C# 将 PDF 转换为 JPG 图像][4]
  * [C# 中的 PDF 到 BMP 转换][5]
  * [C# 中的 PDF 到 TIFF 转换][6]
  * [使用 C# 从 PDF 文档中提取图像][7]

## PDF 到图像转换 C# API {#PDF-to-Image-Conversion-CSharp-API}

为了将 [PDF][8] 转换为图像，我将使用 [Aspose.PDF for .NET API][9]。它是一个功能强大的 PDF 文件管理 API，可让您在 .NET 应用程序中操作 PDF 文档。它允许您在不使用 Adobe Acrobat 的情况下创建、修改、转换、渲染、保护和打印文档。

您可以[下载][10] API 的 DLL 或使用 [NuGet][11] 安装它。

```
Install-Package Aspose.Pdf
```

## 使用 C# 将 PDF 转换为 PNG 图像 {#Convert-PDF-to-PNG-Images-using-CSharp}

您可以按照以下步骤以编程方式将 PDF 文件转换为 PNG 图像：

  * 使用输入 PDF 文件路径创建 **_[Document][12]_** 类的实例。
  * 使用 [**_Document.Pages_**][13] 集合循环浏览 PDF 的所有页面并执行以下操作：
      * 创建 **_[Resolution][14]_** 类的实例并设置其值。
      * 创建 [**_PngDevice_**][15] 类的实例并传递 Width、Height 和 Resolution 对象。
      * 使用页码和输出 PNG 图片路径调用 [**_Process(Page, String)_**][16] 方法，将页面转换为 PNG。

以下代码示例展示了如何使用 C# 将 PDF 页面转换为 PNG 图像。

```
// 打开文档
Document pdfDocument = new Document("C:\\Files\\sample.pdf");

foreach (var page in pdfDocument.Pages)
{
    // Define Resolution
    Resolution resolution = new Resolution(300);

    // Create Png device with specified attributes
    // Width, Height, Resolution
    PngDevice PngDevice = new PngDevice(500, 700, resolution);

    // Convert a particular page and save the image to stream
    PngDevice.Process(pdfDocument.Pages[page.Number], "C:\\Files\\image" + page.Number + "_out" + ".Png");
}
```

{{< figure align=center src="images/Convert-PDF-to-PNG-Images-using-CSharp-1024x604.jpg" alt="使用 C# 将 PDF 转换为 PNG 图像" caption="使用 C# 将 PDF 转换为 PNG 图像">}}
 

[Document][12] 类表示 PDF 文档。它提供了几个属性和方法来执行各种功能。 [Document.Pages][13] 集合是文档页面的集合，页面编号从集合中的 1 开始。 [Resolution][14] 类定义图像分辨率。 [PngDevice][15] 类允许将 PDF 文档的页面保存为 PNG 图像。此类提供以下方法将页面保存为 PNG 图像：

  * [进程（页面，字符串）][16] — Performs some operation on the given page and saves results into the file at given path.
  * [进程（页面，流）][18] — Converts the page into PNG and saves it in the output stream.

## 使用 C# 将 PDF 转换为 JPG 图像 {#Convert-PDF-to-JPG-Images-using-CSharp}

您可以按照以下步骤以编程方式将 PDF 文件转换为 JPG 图像：

  * 使用输入文件路径创建 **_[Document][12]_** 类的实例。
  * 使用 [**_Document.Pages_**][13] 集合循环浏览 PDF 的所有页面并执行以下操作：
      * 创建 **_[Resolution][14]_** 类的实例并设置其值。
      * 创建 [**_JpegDevice_**][19] 类的实例并传递 Width、Height 和 Resolution 对象。
      * 使用页码和输出的 JPG 图片路径调用 [**_Process(Page, String)_**][16] 方法，将页面转换为 JPG。

以下代码示例展示了如何使用 C# 将 PDF 页面转换为 JPG 图像。

```
// 打开文档
Document pdfDocument = new Document("C:\\Files\\sample.pdf");

foreach (var page in pdfDocument.Pages)
{
    // Define Resolution
    Resolution resolution = new Resolution(300);
    
    // Create Jpeg device with specified attributes
    // Width, Height, Resolution
    JpegDevice JpegDevice = new JpegDevice(500, 700, resolution);

    // Convert a particular page and save the image to stream
    JpegDevice.Process(pdfDocument.Pages[page.Number], "C:\\Files\\image" + page.Number + "_out" + ".Jpg");
}
```

{{< figure align=center src="images/Convert-PDF-to-JPG-Images-using-CSharp-1024x605.jpg" alt="使用 C# 将 PDF 转换为 JPG 图像" caption="使用 C# 将 PDF 转换为 JPG 图像">}}
 

## 使用 C# 将 PDF 转换为 BMP {#PDF-to-BMP-Conversion-using-CSharp}

您可以按照以下步骤以编程方式将 PDF 文件转换为 BMP 图像：

  * 使用输入文件路径创建 **_[Document][12]_** 类的实例。
  * 使用 [**_Document.Pages_**][13] 集合循环浏览 PDF 的所有页面并执行以下操作：
      * 创建 _**[Resolution][14]**_ 类的实例并设置其值。
      * 创建 [**_BmpDevice_**][21] 类的实例并传递 Width、Height 和 Resolution 对象。
      * 使用页码和输出BMP图像路径调用[**_Process(Page, String)_**][16]方法，将页面转换为BMP。

以下代码示例展示了如何使用 C# 将 PDF 页面转换为 BMP 图像。

```
// 打开文档
Document pdfDocument = new Document("C:\\Files\\sample.pdf");

foreach (var page in pdfDocument.Pages)
{
    // Define Resolution
    Resolution resolution = new Resolution(300);
    
    // Create PNG device with specified attributes
    // Width, Height, Resolution
    BmpDevice BmpDevice = new BmpDevice(500, 700, resolution);

    // Convert a particular page and save the image to stream
    BmpDevice.Process(pdfDocument.Pages[page.Number], "C:\\Files\\image" + page.Number + "_out" + ".bmp");
}
```

{{< figure align=center src="images/Convert-PDF-to-BMP-Images-using-CSharp-1024x603.jpg" alt="使用 C# 将 PDF 转换为 BMP" caption="使用 C# 将 PDF 转换为 BMP">}}
 

## 使用 C# 将 PDF 转换为 TIFF {#PDF-to-TIFF-Conversion-using-CSharp}

您可以按照以下步骤以编程方式将 PDF 文件转换为 TIFF：

  * 使用输入文件路径创建 **_[Document][12]_** 类的实例。
  * 初始化 **_[Resolution][14]_** 类的实例并设置其值。
  * 创建 **_[TiffSettings][23]_** 类的实例。
  * 设置各种属性，例如_Compression_、_Depth_、_Shape_和_SkipBlankPages_等。
  * 使用 **_Resolution_** 和 **_TiffSettings_** 对象创建 [**_TiffDevice_**][24] 类的实例。
  * 使用 Document 对象和输出 TIFF 文件路径调用 [**_Process(Document, String)_**][25] 方法，将文档转换为 TIFF。

以下代码示例展示了如何使用 C# 将 PDF 文件转换为 TIFF。

```
// 打开文档
Document pdfDocument = new Document("C:\\Files\\sample.pdf");

// 定义分辨率
Resolution resolution = new Resolution(300);

// 创建 TiffSettings 对象
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.None,
    Depth = ColorDepth.Default,
    Shape = ShapeType.Portrait,
    SkipBlankPages = false
};

// 创建 TIFF 设备
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);

// 转换特定页面并将图像保存到流
tiffDevice.Process(pdfDocument, "C:\\Files\\AllPagesToTIFF_out.tif");
```

{{< figure align=center src="images/Convert-PDF-to-TIFF-Images-using-CSharp-1024x603.jpg" alt="使用 C# 将 PDF 转换为 TIFF" caption="使用 C# 将 PDF 转换为 TIFF">}}
 

[TiffSettings][23] 类提供了几个用于将 PDF 转换为 TIFF 的设置。在将 PDF 转换为 TIFF 时，您可以设置亮度、压缩、坐标类型、深度、边距、形状和 SkipBlankPages。

## 使用 C# 从 PDF 文档中提取图像 {#Extract-Images-from-PDF-Documents-using-CSharp}

您可以按照以下步骤以编程方式从任何 PDF 文件中提取所有图像：

  * 使用输入文件路径创建 **_[Document][12]_** 类的实例。
  * 对于每个页面，为 [Page.Resources.Images][28] 集合中的每个图像创建 [XImage][27] 实例。
  * 使用输出图像文件路径创建 [FileStream][29] 类的实例。
  * 使用 FileStream 对象调用 **_[Save()][30]_** 方法保存图像
  * 最后，使用 Close() 方法关闭 _FileStream_。

以下代码示例展示了如何使用 C# 从 PDF 文档中提取图像。

```
// 打开文档
Document pdfDocument = new Document("C:\\Files\\sample.pdf");

// 循环浏览页面
foreach (var page in pdfDocument.Pages)
{
    int imageCounter = 1;
    // Loop through all images
    foreach (XImage image in page.Resources.Images)
    {
        // Create file stream for image
        FileStream outputImage = new FileStream(String.Format("C:\\Files\\Page{0}_Image{1}.jpg", page.Number, imageCounter), FileMode.Create);

        // Save output image
        image.Save(outputImage);

        // Close stream
        outputImage.Close();

        imageCounter++;
    }
}
```

{{< figure align=center src="images/Extract-Images-from-PDF-Documents-using-CSharp-1024x604.jpg" alt="使用 C# 从 PDF 文档中提取图像" caption="使用 C# 从 PDF 文档中提取图像">}}
 

[XImage][32] 类表示图像 X-Object。它提供了几个处理图像的属性和方法。 XImage 类提供以下方法来保存图像对象：

  * [保存（流）][30] — Saves image data into stream as JPEG image.
  * [保存（流，图像格式）][33] — Saves image into stream with requested format.
  * [Save(Stream, Int32)][34] 方法 — 将图像数据以指定分辨率的 JPEG 图像形式保存到流中。
  * [Save(Stream, ImageFormat, Int32)][35] 方法 — 以请求的格式和指定的分辨率将图像保存到流中。

[Page.Resources.Images][28] 集合表示特定页面的图像集合。

## 获得免费许可证

您可以通过请求 [免费的临时许可证][36] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C#** 将 PDF 文件页面转换为图像**。您还学习了**如何以编程方式将 PDF 转换为 PNG、PDF 转换为 JPG、PDF 转换为 BMP 以及 PDF 转换为 TIFF**。此外，您还学习了**如何使用 C#从 PDF 文件中提取图像**。 API 还提供压缩选项、表格创建和操作、图形和图像功能、广泛的超链接功能、印章和水印任务、扩展的安全控制和自定义字体处理。您可以使用 [文档][37] 了解更多关于 Aspose.PDF for .NET API 的信息。如有任何歧义，请随时在 [论坛][38] 上与我们联系。

## 也可以看看

  * [使用 C# 对 PDF 文档进行分类][39]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/convert-pdf-to-images-using-csharp.jpg
 [2]: #PDF-to-Image-Conversion-CSharp-API
 [3]: #Convert-PDF-to-PNG-Images-using-CSharp
 [4]: #Convert-PDF-to-JPG-Images-using-CSharp
 [5]: #PDF-to-BMP-Conversion-using-CSharp
 [6]: #PDF-to-TIFF-Conversion-using-CSharp
 [7]: #Extract-Images-from-PDF-Documents-using-CSharp
 [8]: https://docs.fileformat.com/pdf/
 [9]: https://products.aspose.com/pdf
 [10]: https://downloads.aspose.com/pdf/net
 [11]: https://www.nuget.org/packages/Aspose.PDF/
 [12]: https://apireference.aspose.com/pdf/net/aspose.pdf/document
 [13]: https://apireference.aspose.com/pdf/net/aspose.pdf/document/properties/pages
 [14]: https://apireference.aspose.com/pdf/net/aspose.pdf.devices/resolution
 [15]: https://apireference.aspose.com/pdf/net/aspose.pdf.devices/pngdevice
 [16]: https://apireference.aspose.com/pdf/net/aspose.pdf.devices.pagedevice/process/methods/1
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Convert-PDF-to-PNG-Images-using-CSharp.jpg
 [18]: https://apireference.aspose.com/pdf/net/aspose.pdf.devices/pngdevice/methods/process
 [19]: https://apireference.aspose.com/pdf/net/aspose.pdf.devices/jpegdevice
 [20]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Convert-PDF-to-JPG-Images-using-CSharp.jpg
 [21]: https://apireference.aspose.com/pdf/net/aspose.pdf.devices/bmpdevice
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Convert-PDF-to-BMP-Images-using-CSharp.jpg
 [23]: https://apireference.aspose.com/pdf/net/aspose.pdf.devices/tiffsettings
 [24]: https://apireference.aspose.com/pdf/net/aspose.pdf.devices/tiffdevice
 [25]: https://apireference.aspose.com/pdf/net/aspose.pdf.devices.documentdevice/process/methods/3
 [26]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Convert-PDF-to-TIFF-Images-using-CSharp.jpg
 [27]: https://apireference.aspose.com/net/pdf/aspose.pdf/ximage
 [28]: https://apireference.aspose.com/pdf/net/aspose.pdf/resources/properties/images
 [29]: https://docs.microsoft.com/en-us/dotnet/api/system.io.filestream
 [30]: https://apireference.aspose.com/pdf/net/aspose.pdf/ximage/methods/save
 [31]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Extract-Images-from-PDF-Documents-using-CSharp.jpg
 [32]: https://apireference.aspose.com/pdf/net/aspose.pdf/ximage
 [33]: https://apireference.aspose.com/pdf/net/aspose.pdf.ximage/save/methods/1
 [34]: https://apireference.aspose.com/pdf/net/aspose.pdf.ximage/save/methods/3
 [35]: https://apireference.aspose.com/pdf/net/aspose.pdf.ximage/save/methods/2
 [36]: https://purchase.aspose.com/temporary-license
 [37]: https://docs.aspose.com/pdf/net/
 [38]: https://forum.aspose.com/c/pdf/10
 [39]: https://blog.conholdate.com/2021/07/01/classify-pdf-documents-using-csharp/

