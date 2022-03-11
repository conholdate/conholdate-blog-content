---
title: "'在 C# 中合并 JPG 图像 - .NET Imaging API'"
author: Muhammad Sohail
date: 2020-12-16T08:15:30+00:00
summary: "有时我们需要通过将多个 JPG 图像组合在一起来创建图像。本文介绍了如何在 C# 中执行此操作。"
url: /zh/2020/12/16/merge-jpg-images-in-csharp/
categories:
  - "Conholdate.Total 产品系列"

---
有时我们需要通过将多个 JPG 图像组合在一起来创建图像。本文介绍了如何在 C# 中执行此操作。

  * [C# 成像 API – 免费下载][1]
  * [在 C# 中水平合并 JPG 图像][2]
  * [在 C# 中垂直合并 JPG 图像][3]
  * [在 C# 中将 JPG 图像合并为 PDF][4]
  * [在 C# 中将 JPG 图像合并为 PNG][5]

## C# 成像 API – 免费下载 {#CSharp-Imaging-API}

[Aspose.Imaging for .NET][6] 提供了许多灵活的例程，用于在 .NET 应用程序中创建和操作图像。它可以让您在几行代码中组合 JPG 文件。您可以使用 [NuGet][7] 或 [下载][8] API 的 DLL 将其安装在您的 .NET 应用程序中。

```
Install-Package Aspose.Imaging
```

## 在 C# 中水平合并 JPG 图像 {#Merge-JPG-Images-Horizontally}

以下是在 C# 中水平合并 JPEG 图像的步骤。

  * 创建要合并的 JPEG 图像数组。
  * 通过添加数组中所有图像的宽度和通过找到数组中图像的最大高度来计算结果图像的宽度。
  * 使用 [JpegImage][9] 类创建一个新图像，并将其宽度和高度设置为上一步中计算的值。
  * 遍历图像数组（您要合并）并对每个图像执行以下任务：
      * 使用 [LoadArgb32Pixels][10] 方法加载图像的像素，并使用 [SaveArgb32Pixels][11] 方法将它们保存在结果图像中。此方法还将 [Rectangle][12] 对象作为参数，用于定义图像在结果图像中的位置。
  * 将生成的图像另存为 JPEG 图像。

以下代码示例显示了如何在 C# 中水平连接 JPEG 图像。

```
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Imaging;
using Aspose.Imaging.FileFormats.Jpeg;
using Aspose.Imaging.ImageOptions;
using Aspose.Imaging.Sources;

// 要合并的图像数组。
string[] imagePaths = { "Image1.jpeg", "Image2.jpg" };

// 输出/结果文件的名称。
string outputPath = "MergeImages_Horizontally.jpg";

// 获取生成的图像大小。
List<Size> imageSizes = new List<Size>();
foreach (string imagePath in imagePaths)
{
    using (RasterImage image = (RasterImage)Image.Load(imagePath))
    {
        imageSizes.Add(image.Size);
    }
}

// 结果图像的宽度和高度
int newWidth = imageSizes.Sum(size => size.Width);
int newHeight = imageSizes.Max(size => size.Height);

// 将图像合并为一个。
Source tempFileSource = new FileCreateSource("temp.jpg", isTemporal: true);
JpegOptions options = new JpegOptions() { Source = tempFileSource, Quality = 100 };
using (JpegImage newImage = (JpegImage)Image.Create(options, newWidth, newHeight))
{
    int stitchedWidth = 0;
    foreach (string imagePath in imagePaths)
    {
        using (RasterImage image = (RasterImage)Image.Load(imagePath))
        {
            Rectangle bounds = new Rectangle(stitchedWidth, 0, image.Width, image.Height);
            newImage.SaveArgb32Pixels(bounds, image.LoadArgb32Pixels(image.Bounds));
            stitchedWidth += image.Width;
        }
    }

    newImage.Save(outputPath);
}
```

**输入图像**

{{< figure align=center src="images/Image1.jpeg" alt="" caption="First Image">}}
 

{{< figure align=center src="images/Image2.jpg" alt="" caption="Second Image">}}
 

**输出图像**

{{< figure align=center src="images/MergeImages_Horizontally-1024x470.jpg" alt="" caption="Horizontally Merged Image">}}
 

## 在 C# 中垂直合并 JPG 图像 {#Merge-JPG-Images-Vertically}

垂直合并JPEG图像的步骤同上。一点不同是，我们通过将数组中所有图像的高度相加来计算结果图像的高度，并通过找到数组中图像的最大宽度来计算宽度。以下代码示例展示了如何在 C# 中垂直连接 JPEG 图像。

```
// 要合并的图像数组
string[] imagePaths = { "Image1.jpeg", "Image2.jpg" };

string outputPath = "MergeImages_Vertically.jpg";

// 获取生成的图像大小。
List<Size> imageSizes = new List<Size>();
foreach (string imagePath in imagePaths)
{
    using (RasterImage image = (RasterImage)Image.Load(imagePath))
    {
        imageSizes.Add(image.Size);
    }
}

// 结果图像的宽度和高度
int newWidth = imageSizes.Max(size => size.Width);
int newHeight = imageSizes.Sum(size => size.Height);

// 将图像合并为一个。
using (MemoryStream memoryStream = new MemoryStream())
{
    StreamSource outputStreamSource = new StreamSource(memoryStream);
    JpegOptions options = new JpegOptions() { Source = outputStreamSource, Quality = 100 };
    using (JpegImage newImage = (JpegImage)Image.Create(options, newWidth, newHeight))
    {
        int stitchedHeight = 0;
        foreach (string imagePath in imagePaths)
        {
            using (RasterImage image = (RasterImage)Image.Load(imagePath))
            {
                Rectangle bounds = new Rectangle(0, stitchedHeight, image.Width, image.Height);
                newImage.SaveArgb32Pixels(bounds, image.LoadArgb32Pixels(image.Bounds));
                stitchedHeight += image.Height;
            }
        }

        newImage.Save(outputPath);
    }
}
```

{{< figure align=center src="images/MergeImages_Vertically-709x1024.jpg" alt="" caption="Vertically Merged Image">}}
 

## 在 C# 中将 JPG 图像合并为 PDF {#Merge-JPG-Images-into-PDF}

您可能需要将 JPEG 图像组合成 PDF。您可以通过在 [Image.Save][17] 方法中进行微小的更改（使用 **.pdf** 扩展名而不是 **.jpg**）来做到这一点。

```
// 要合并的图像数组。
string[] imagePaths = { "Image1.jpeg", "Image2.jpg" };

string outputPath = "MergeHorizontalAsPDF";
string tempFilePath = "temp.jpg";

// 获取生成的图像大小。
List<Size> imageSizes = new List<Size>();
foreach (string imagePath in imagePaths)
{
    using (RasterImage image = (RasterImage)Image.Load(imagePath))
    {
        imageSizes.Add(image.Size);
    }
}

// 结果图像的宽度和高度。
int newWidth = imageSizes.Sum(size => size.Width);
int newHeight = imageSizes.Max(size => size.Height);

// 将图像合并为一个。
Source tempFileSource = new FileCreateSource(tempFilePath, isTemporal: true);
JpegOptions options = new JpegOptions() { Source = tempFileSource, Quality = 100 };
using (JpegImage newImage = (JpegImage)Image.Create(options, newWidth, newHeight))
{
    int stitchedWidth = 0;
    foreach (string imagePath in imagePaths)
    {
        using (RasterImage image = (RasterImage)Image.Load(imagePath))
        {
            Rectangle bounds = new Rectangle(stitchedWidth, 0, image.Width, image.Height);
            newImage.SaveArgb32Pixels(bounds, image.LoadArgb32Pixels(image.Bounds));
            stitchedWidth += image.Width;
        }
    }

    newImage.Save(outputPath + ".pdf", new PdfOptions());
}
```

## 在 C# 中将 JPG 图像合并为 PNG {#Merge-JPG-Images-into-PNG}

同样，您可能希望将 JPEG 图像组合成 PNG。如上所示，您只需要在 [Image.Save][17] 方法中使用 **.png** 扩展名而不是 **.jpg** 即可。

```
// 要合并的图像数组。
string[] imagePaths = { "Image1.jpeg", "Image2.jpg" };

string outputPath = "MergeHorizontalAsPNG";

// 获取生成的图像大小。
List<Size> imageSizes = new List<Size>();
foreach (string imagePath in imagePaths)
{
    using (RasterImage image = (RasterImage)Image.Load(imagePath))
    {
        imageSizes.Add(image.Size);
    }
}

// 结果图像的宽度和高度。
int newWidth = imageSizes.Sum(size => size.Width);
int newHeight = imageSizes.Max(size => size.Height);

// 将图像合并为一张并另存为PNG
using (MemoryStream memoryStream = new MemoryStream())
{
    StreamSource outputStreamSource = new StreamSource(memoryStream);
    JpegOptions options = new JpegOptions() { Source = outputStreamSource, Quality = 100 };
    using (JpegImage newImage = (JpegImage)Image.Create(options, newWidth, newHeight))
    {
        int stitchedWidth = 0;
        foreach (string imagePath in imagePaths)
        {
            using (RasterImage image = (RasterImage)Image.Load(imagePath))
            {
                Rectangle bounds = new Rectangle(stitchedWidth, 0, image.Width, image.Height);
                newImage.SaveArgb32Pixels(bounds, image.LoadArgb32Pixels(image.Bounds));
                stitchedWidth += image.Width;
            }
        }

        newImage.Save(outputPath + ".png", new PngOptions());
    }
}
```

## 结论

在本文中，您学习了如何在 C# 中加入 JPEG 图像。您可以水平或垂直组合它们。您还学习了如何将合并的图像保存为 PDF 或 PNG。有关更多信息，请查看 Aspose.Imaging for .NET 的[文档][18]。如果您有任何问题，请随时通过 [我们的支持论坛][19] 与我们联系。

## 也可以看看

  * [使用 C# 压缩 PNG、JPEG 和 TIFF 图像][20]
  * [将 PNG、JPG 转换为 TGA 或使用 C# 操作 TGA][21]

 [1]: #CSharp-Imaging-API
 [2]: #Merge-JPG-Images-Horizontally
 [3]: #Merge-JPG-Images-Vertically
 [4]: #Merge-JPG-Images-into-PDF
 [5]: #Merge-JPG-Images-into-PNG
 [6]: https://products.aspose.com/imaging/net
 [7]: https://www.nuget.org/packages/Aspose.Imaging/
 [8]: https://downloads.aspose.com/imaging/net
 [9]: https://apireference.aspose.com/imaging/net/aspose.imaging.fileformats.jpeg/jpegimage
 [10]: https://apireference.aspose.com/imaging/net/aspose.imaging/rasterimage/methods/loadargb32pixels
 [11]: https://apireference.aspose.com/imaging/net/aspose.imaging/rasterimage/methods/saveargb32pixels
 [12]: https://apireference.aspose.com/imaging/net/aspose.imaging/rectangle
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2020/12/Image1.jpeg
 [14]: https://blog.conholdate.com/wp-content/uploads/sites/27/2020/12/Image2.jpg
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2020/12/MergeImages_Horizontally.jpg
 [16]: https://blog.conholdate.com/wp-content/uploads/sites/27/2020/12/MergeImages_Vertically.jpg
 [17]: https://apireference.aspose.com/imaging/net/aspose.imaging.image/save/methods/3
 [18]: https://docs.aspose.com/imaging/net/
 [19]: https://forum.aspose.com/
 [20]: https://blog.aspose.com/2020/11/27/compress-png-jpeg-and-tiff-images-using-csharp/
 [21]: https://blog.aspose.com/2020/10/11/convert-png-jpg-to-tga-manipulaute-csharp/








