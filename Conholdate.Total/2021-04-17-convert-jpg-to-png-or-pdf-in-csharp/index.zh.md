---
title: "'在 C# 中将 JPG 转换为 PNG 或 PDF'"
author: Nayyer Shahbaz
date: 2021-04-17T00:54:23+00:00
url: /zh/2021/04/17/convert-jpg-to-png-or-pdf-in-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "用于 JPEG 到 PNG 转换的 CSharp API"
  - "在 CSharp 中将 JPEG 转换为 PDF"
  - "将jpg转换为png"
  - "JPEG2000 到 PNG 的转换 APII"
  - "在 CSharp 中将 jpg 转换为 png"

---


{{< figure align=center src="images/jpg-png.png" alt="将JPG转换为PNG">}}
 

[JPEG][2] 和 [PNG][3] 是流行的光栅图像格式之一，因其有损压缩方法而广受欢迎。您可以选择调整压缩级别以达到所需的质量级别，同时减少存储大小。但是，有时您的系统只接受特定格式，因此您需要加载现有的图像集并将它们保存到所需的输出。与使用功能有限的传统应用程序和手动提供输入文件不同，编程 API 因其灵活性和以批处理格式执行所有操作的能力而领先一步。

  * [图像处理 API][4]
  * [在 C# 中将 JPG 转换为 PNG][5]
  * [C#中的JPG到PDF转换][6]

## 图像处理 API {#Image-processing-API}

Aspose.Imaging for .NET 是一个了不起的编程 API，提供了创建、操作和转换 [支持的文件格式][7] 的功能。它独立于其他图形应用程序运行，不需要在机器上安装任何图像编辑器。它可以与 ASP.NET Web 应用程序或 Windows 桌面应用程序一起使用。 [Aspose.Imaging for .NET][8] 捆绑在 [Conholdate.Total for .NET][9] 套件中。因此，如果您购买了 [Conholdate.Total for .NET][9] 的订阅，那么您绝对可以使用 [Aspose.Imaging for .NET][8] API 执行所有图像处理操作。

为了使用 API，第一步是安装它。您可以按照任一步骤执行安装。

  * 下载 [DLL 文件][10] 并在您的项目中手动引用它们
  * 打开 [NuGet][11] 包管理器，搜索 **Aspose.Imaging** 并安装它。
  * 从 NuGet 包管理器控制台运行以下命令

```
Install-Package Aspose.Imaging
```

## 在 C# 中将 JPG 转换为 PNG {#Convert-JPG-to-PNG-in-C-}

API 足够强大，可以识别输入图像的格式，您只需以 Stream 实例的形式或通过提供本地系统上文件的路径来指定源图像。在以下步骤中，我们将解释如何加载 [JPEG][12] 图像并将输出保存为 [PNG][13] 格式。

  1. 首先，我们需要创建一个 [Aspose.Imaging.License][14] 对象的实例。调用 [SetLicense(…)][15] 并提供 Conholdate.Total.NET.lic 文件的路径作为参数
  2. 其次，创建一个 [Image][16] 类的对象，它是所有图像类型的基类，并传递 Aspose.Imaging.Image.Load(..) 方法的结果，该方法采用图像的 Steam 或字符串路径要加载的文件
  3. 创建 PngOptions 类的实例
  4. 最后，调用 [Image][16] 类的 [Save(String)][17] 方法并传递要保存生成的 [PNG][13] 文件的位置

```
// 创建一个对象来启动许可
Aspose.Imaging.License license = new Aspose.Imaging.License();

// 提供许可证文件的路径
license.SetLicense("/Documents/Conholdate.Total.NET.lic");

// 在 Image 类的实例中加载现有图像（JPEG 类型）
using (Aspose.Imaging.Image image = Aspose.Imaging.Image.Load("/Documents/samsung_galaxy.jpg"))
{
  // create an object of PngOptions class
  Aspose.Imaging.ImageOptions.PngOptions options = new Aspose.Imaging.ImageOptions.PngOptions();
  
  // save resultant image and pass PngOptions as argument
  image.Save(dataDir + "_output.png", options);
}
```

The PngOptions class also provides various properties and in the example below, we have specified to generate the color type of resultant image as Grayscale. Also, the compression level for a resultant image is specified as 4. 请注意，**CompressionLevel** 属性接受 0-9 之间的值，其中 9 是最大压缩，0 是默认值。

```
// 创建 PngOptions 对象
Aspose.Imaging.ImageOptions.PngOptions options = new Aspose.Imaging.ImageOptions.PngOptions();

// 将结果图像的颜色类型设置为 grayScale
options.ColorType = Aspose.Imaging.FileFormats.Png.PngColorType.Grayscale;

// 将结果文件的压缩级别设置为 4
options.CompressionLevel = 4;
```

源文件和生成的灰度图像可以从以下链接下载

  * [samsung_gaalxy.jpg][18]
  * [灰度.png][19]

## C#中的JPG到PDF转换 {#JPG-to-PDF-conversion-in-Csharp}

Aspose.Imaging for .NET 同样能够将 JPG 图像转换为 [PDF][20]（可移植文档格式）。在转换过程中，您还可以设置 DocumentInfo 以及 [PDF/A][21] 合规性详细信息。以下步骤说明了加载光栅图像及其转换为 [PDF][20] 格式的过程。

  1. 第一步是创建 [License][14] 类的实例。
  2. 其次，调用[SetLicense(…)][15]方法并提供Conholdate.Total.NET.lic文件的路径。初始化许可证以消除评估版本中存在的所有限制
  3. 第三，创建一个 [Image][16] 类的对象，它是所有图像类型的基类，并传递 [Aspose.Imaging.Image.Load(..)][22] 方法的输出
  4. 现在创建一个 [PdfOptions][23] 类的实例
  5. 为了设置 PDF 文档信息，如作者、标题、主题等，创建 [PdfDocumentInfo][24] 类的对象并将其值传递给 [PdfOptions][23] 类的 [PdfDocumentInfo][25] 对象
  6. 现在为了保存带有 PDF/A 合规性信息的 PDF 文件，请创建 [PdfCoreOptions][26] 类的实例并将其与 [PdfOptions][23] 对象的 [PdfCoreOptions][27] 属性相关联
  7. 最后调用[Image][16]类的[Save(String)][17]方法生成输出PDF文档

```
// 创建一个对象来启动许可
Aspose.Imaging.License license = new Aspose.Imaging.License();

// 提供许可证文件的路径
license.SetLicense("/Documents/Conholdate.Total.NET.lic");

// 在 Image 类的实例中加载现有图像（JPEG 类型）
using (Aspose.Imaging.Image image = Aspose.Imaging.Image.Load(dataDir+"samsung_galaxy.jpg"))
{
  // create an instance of PdfOptions class
  Aspose.Imaging.ImageOptions.PdfOptions pdfOptions = new Aspose.Imaging.ImageOptions.PdfOptions();
  
  // create PdfDocumentInfo object and pass it to PdfOptions instance
  pdfOptions.PdfDocumentInfo = new Aspose.Imaging.FileFormats.Pdf.PdfDocumentInfo
  {
    // set author name for the resultant file
    Author = "Nayyer Shahbaz",
    Title = "JPEG converted to PDF",
    Subject = "Aspose.Imaging for .NET"
  };
  
  // set the PDF compliance as PDF/A-1a
  pdfOptions.PdfCoreOptions = new Aspose.Imaging.FileFormats.Pdf.PdfCoreOptions()
  {
    PdfCompliance = Aspose.Imaging.PdfComplianceVersion.PdfA1b
  };
  
  // save the resultant PDF document
  image.Save(dataDir + "_output.pdf", pdfOptions);
}
```

上述示例中使用的示例文件可以从以下链接下载

  * [samsung_gaalxy.jpg][18]
  * [_输出.pdf][28]

## 获得免费许可证

您可以申请<a rel="noreferrer noopener" href="https://purchase.aspose.com/temporary-license" >免费的临时许可证</a>来试用 API，没有任何评估限制。

## 结论

在本文中，我们讨论了 [Aspose.Imaging for .NET][8] 的各种功能，专门用于将 JPG 转换为 PNG 格式以及将其渲染为 PDF 格式。请注意，与上面讨论的相比，[Aspose.Imaging for .NET][8] 功能更强大，并提供了过多的选项。它使您的 .NET 应用程序能够绘制以及执行光栅和矢量图像的基本到高级处理。

此外，[Aspose.Imaging for .NET][8] 通过本机字节访问和一系列高效算法提供强大的图像压缩和高处理速度。它不仅可以操作、导出和转换图像，还可以让您使用像素操作和图形路径动态绘制对象。有关更多信息，请浏览产品 [文档][29]，如果您在使用 API 时遇到任何问题，请随时通过 [产品支持论坛][30] 联系。

## 也可以看看

  * [使用 C# .NET REST API 将 GIF 转换为 DICOM 并将 JPEG 转换为 PNG][31]
  * [使用 Java Cloud SDK 通过图像进行对象识别][32]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/jpg-png.png
 [2]: https://wiki.fileformat.com/image/jpeg/
 [3]: https://wiki.fileformat.com/image/png/
 [4]: #Image-processing-API
 [5]: #Convert-JPG-to-PNG-in-C-
 [6]: #JPG-to-PDF-conversion-in-Csharp
 [7]: https://docs.aspose.com/imaging/net/supported-file-formats/
 [8]: https://products.aspose.com/imaging/net
 [9]: https://products.conholdate.com/total/net
 [10]: https://downloads.aspose.com/imaging/net
 [11]: https://www.nuget.org/packages/Aspose.Imaging/
 [12]: https://docs.fileformat.com/image/jpeg/
 [13]: https://docs.fileformat.com/image/png/
 [14]: https://apireference.aspose.com/imaging/net/aspose.imaging/license
 [15]: https://apireference.aspose.com/imaging/net/aspose.imaging.license/setlicense/methods/1
 [16]: https://apireference.aspose.com/imaging/net/aspose.imaging/image
 [17]: https://apireference.aspose.com/imaging/net/aspose.imaging.datastreamsupporter/save/methods/2
 [18]: https://www.dropbox.com/s/g2fobiwgjhvftfw/samsung_galaxy.jpg?dl=0
 [19]: https://www.dropbox.com/s/zrm1oxdetnpuogc/Grayscale.png?dl=0
 [20]: https://docs.fileformat.com/pdf/
 [21]: https://docs.fileformat.com/pdf/a/
 [22]: https://apireference.aspose.com/imaging/net/aspose.imaging.image/load/methods/2
 [23]: https://apireference.aspose.com/imaging/net/aspose.imaging.imageoptions/pdfoptions
 [24]: https://apireference.aspose.com/imaging/net/aspose.imaging.fileformats.pdf/pdfdocumentinfo
 [25]: https://apireference.aspose.com/imaging/net/aspose.imaging.imageoptions/pdfoptions/properties/pdfdocumentinfo
 [26]: https://apireference.aspose.com/imaging/net/aspose.imaging.fileformats.pdf/pdfcoreoptions
 [27]: https://apireference.aspose.com/imaging/net/aspose.imaging.imageoptions/pdfoptions/properties/pdfcoreoptions
 [28]: https://www.dropbox.com/s/pusa3gzj3umqjn6/_output.pdf?dl=0
 [29]: https://docs.aspose.com/imaging/net/
 [30]: https://forum.aspose.com/c/imaging/14
 [31]: https://blog.aspose.cloud/2021/04/04/convert-gif-to-dicom-and-jpeg-to-png-using-c-.net-rest-api/
 [32]: https://blog.aspose.cloud/2020/07/01/object-recognition-through-images-using-java-cloud-sdk/








