---
title: "'使用 C# 在 Word 文档中添加文本或图像水印'"
author: Muzammil Khan
date: 2021-10-22T10:35:19+00:00
summary: "作为 C# 开发人员，您可以轻松地以编程方式在 Word 文档中添加文本或图像水印。在本文中，您将学习**如何使用 C# 在 Word 文档中添加文本或图像水印。**"
url: /zh/2021/10/22/add-text-or-image-watermarks-in-word-documents-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 CSharp 添加图像水印"
  - "使用 CSharp 添加文本水印"
  - "加水印"
  - "加水印 Image"
---


{{< figure align=center src="images/add-text-or-image-watermarks-in-word-documents-using-csharp.jpg" alt="使用 C# 在 Word 文档中添加文本或图像水印">}}
 

作为 C# 开发人员，您可以轻松地以编程方式在 Word 文档中添加文本或图像水印。水印是一种文本或图像形式的信息，通常用于通过显示版权信息、免责声明、徽标、印章或签名来识别或保护文档。在本文中，您将学习**如何使用 C# 在 Word 文档中添加文本或图像水印**。

本文讨论/涵盖了以下主题：

  * [在 Word 文档中添加水印的 C# API][2]
  * [使用 C# 在 Word 文档中添加文本水印][3]
  * [使用 C# 在 Word 文档中添加图像水印][4]
  * [使用 C# 为 Word 文档的图像添加水印][5]
  * [使用 C# 将水印添加到 Word 文档中的特定页面][6]
  * [使用 C# 将水印添加到 Word 文档的页眉或页脚][7]

## 在 Word 文档中添加水印的 C# API {#CSharp-API-to-Add-Watermark-in-Word-Documents}

为了在 [DOC][8] 或 [DOCX][9] 文件中添加文本或图像水印，我们将使用 [GroupDocs.Watermark for .NET][10] API。它使您能够添加、编辑、搜索和删除 [支持的文件格式][11] 中的图像和文本水印。它还允许获取有关源文档的基本信息，例如文件类型、大小、页数、页面高度和宽度等。API 的文档预览功能允许生成文档页面的图像表示，以便更好地理解文档。

您可以[下载][12] API 的 DLL 或使用 [NuGet][13] 安装它。

```
Install-Package GroupDocs.Watermark
```

## 使用 C# 在 Word 文档中添加文本水印 {#Add-Text-Watermark-in-Word-Documents-using-CSharp}

您可以按照以下步骤在 Word 文档中添加文本水印：

  * 首先，使用 [Watermarker][14] 类加载 DOCX 文件。
  * 使用 [Font][15] 类初始化用于水印文本的字体。
  * 创建 [TextWatermark][16] 类的实例以创建文本水印。传递文本以显示为水印，并将定义的字体对象作为输入参数。
  * 现在，设置各种[水印属性][17]，例如前景色、背景色、旋转角度、高度、宽度、不透明度等。
  * 然后，调用 [Watermarker.Add()][18] 方法将文本水印添加到文档中。
  * 最后调用[Watermarker.Save()][19]方法保存加水印的Word文档。

以下代码示例展示了**如何使用 C#** 在 DOCX 文件中添加文本水印。

```
// 创建者水印
Watermarker watermarker = new Watermarker(@"C:\Files\Watermark\sample.docx");

// 初始化用于水印的字体
Font font = new Font("Arial", 19, FontStyle.Bold | FontStyle.Italic);

// 创建水印对象
TextWatermark watermark = new TextWatermark("Simple Text Watermark", font);

// 设置水印属性
watermark.ForegroundColor = Color.Red;
watermark.BackgroundColor = Color.Blue;
watermark.TextAlignment = TextAlignment.Right;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Bottom;

// 设置水印大小
watermark.Width = 150;
watermark.Height = 40;

// 设置不透明度级别
watermark.Opacity = 0.9;

// 加水印
watermarker.Add(watermark);

// 保存输出文件
watermarker.Save(@"C:\Files\Watermark\addTextWatermark_output.docx");
```

{{< figure align=center src="images/Add-Text-Watermark-in-Word-Documents-using-CSharp-1024x620.jpg" alt="使用 C# 在 Word 文档中添加文本水印。" caption="使用 C# 在 Word 文档中添加文本水印">}}
 

## 使用 C# 在 Word 文档中添加图像水印 {#Add-Image-Watermark-in-Word-Documents-using-CSharp}

您可以按照以下步骤将图像作为水印添加到 Word 文档：

  * 首先，使用 [Watermarker][14] 类加载 DOCX 文件。
  * 使用图像路径创建 [ImageWatermark][21] 类的实例以创建图像水印。
  * 现在，设置各种[水印属性][17]，例如对齐、高度、宽度等。
  * 然后，调用[Watermarker.Add()][18]方法将图片水印添加到文档中。
  * 最后调用[Watermarker.Save()][19]方法保存加水印的Word文档。

以下代码示例展示了**如何使用 C#** 在 DOCX 文件中添加图像水印。

```
// 创建水印
Watermarker watermarker = new Watermarker(@"C:\Files\Watermark\sample.docx");

// 创建水印对象
ImageWatermark watermark = new ImageWatermark(@"C:\Files\Watermark\logo.png");

// 设置水印对齐
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Bottom;

// 设置水印大小
watermark.Width = 100;
watermark.Height = 100;

// 加水印
watermarker.Add(watermark);

// 保存输出文件
watermarker.Save(@"C:\Files\Watermark\AddImageWatermark_output.docx");
```

{{< figure align=center src="images/Add-Image-Watermark-in-Word-Documents-using-CSharp-1024x617.jpg" alt="使用 C# 在 Word 文档中添加图像水印。" caption="使用 C# 在 Word 文档中添加图像水印">}}
 

## 使用 C# 为 Word 文档的图像添加水印 {#Watermark-Images-in-Word-Documents-using-CSharp}

您可以按照以下步骤为 Word 文档中的图像添加文本水印：

  * 首先，使用 [Watermarker][14] 类加载 DOCX 文件。
  * 创建 [TextWatermark][16] 类的实例以创建文本水印。使用 [Font][15] 类作为输入参数传递要显示为水印的文本和用于水印文本的字体。
  * 现在，设置各种[水印属性][17]，例如前景色、对齐方式、旋转角度、比例因子等。
  * 然后，调用 [Watermarker.GetImages()][23] 方法查找文档中的所有图像，并在 [WatermarkableImageCollection][24] 类对象中获取结果。
  * 对于 WatermarkableImageCollection 中的每个图像，通过调用 TextWatermark 对象的 [WatermarkableImage.Add()][25] 方法添加水印。
  * 最后调用[Watermarker.Save()][19]方法保存加水印的Word文档。

以下代码示例展示了**如何使用 C#** 向 DOCX 文件中的图像添加文本水印。

```
// 创建水印
Watermarker watermarker = new Watermarker(@"C:\Files\Watermark\sample.docx");

// 创建者文字水印
TextWatermark watermark = new TextWatermark("Protected image", new Font("Arial", 8));

// 设置水印属性
watermark.ForegroundColor = Color.Black;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;
watermark.RotateAngle = 45;
watermark.SizingType = SizingType.ScaleToParentDimensions;
watermark.ScaleFactor = 1;

// 查找内容中的所有图像。
WatermarkableImageCollection images = watermarker.GetImages();

// 加水印。
foreach (WatermarkableImage watermarkableImage in images)
{
    watermarkableImage.Add(watermark);
}

// 保存输出文件
watermarker.Save(@"C:\Files\Watermark\AddWatermarkToImages_output.docx");
```

{{< figure align=center src="images/Watermark-Images-in-Word-Documents-using-CSharp-1024x925.jpg" alt="使用 C# 在 Word 文档中添加水印图像。" caption="使用 C# 在 Word 文档中添加水印图像。">}}
 

## 使用 C# 将水印添加到 Word 文档中的特定页面 {#Add-Watermark-to-Specific-Pages-in-Word-Documents-using-CSharp}

您可以按照以下步骤将水印添加到 Word 文档的特定页面：

  * 首先，使用 [Watermarker][14] 类加载 DOCX 文件。
  * 使用 [Font][15] 类初始化用于水印文本的字体。
  * 创建 [TextWatermark][16] 类的实例以创建文本水印。传递文本以显示为水印，并将定义的字体对象作为输入参数。
  * 现在，设置各种[水印属性][17]，例如前景色、背景色、对齐方式等。
  * 创建 [WordProcessingWatermarkPagesOptions][27] 类的实例
  * 现在，设置 [PageNumbers][28] 以添加水印。您可以设置单个页码或以逗号分隔的页码列表。我们将其设置为 [WordProcessingContent.PageCount][29]，它表示此处文档的最后一页。
  * 然后，调用[Watermarker.Add()][18]方法添加定义好的水印。
  * 最后调用[Watermarker.Save()][19]方法保存加水印的Word文档。

以下代码示例展示了**如何使用 C#** 将文本水印添加到 DOCX 文件中的特定页面。

```
// 创建水印
Watermarker watermarker = new Watermarker(@"C:\Files\Watermark\sample.docx");

// 创建文字水印
TextWatermark watermark = new TextWatermark("This is simple watermark!", new Font("Arial", 26));

// 设置水印属性
watermark.ForegroundColor = Color.Red;
watermark.BackgroundColor = Color.Blue;
watermark.TextAlignment = TextAlignment.Right;

watermark.HorizontalAlignment = HorizontalAlignment.Left;
watermark.VerticalAlignment = VerticalAlignment.Top;

// 在最后一页添加水印
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
WordProcessingWatermarkPagesOptions options = new WordProcessingWatermarkPagesOptions();
options.PageNumbers = new int[] { content.PageCount };

// 加水印
watermarker.Add(watermark, options);

// 保存输出文件
watermarker.Save(@"C:\Files\Watermark\AddToSpecificPage_output.docx");
```

## 使用 C# 将水印添加到 Word 文档的页眉或页脚 {#Add-Watermark-to-Header-or-Footer-of-Word-Documents-using-CSharp}

您可以按照以下步骤将水印添加到 Word 文档的页眉或页脚部分：

  * 首先，使用 [Watermarker][14] 类加载 DOCX 文件。
  * 使用图像路径创建 [ImageWatermark][21] 类的实例以创建图像水印。
  * 然后，设置各种[水印属性][17]，如Alignment、Height、Width等。
  * 创建 [WordProcessingWatermarkSectionOptions][30] 类的实例。
  * 现在，将 [WordProcessingWatermarkSectionOptions.SectionIndex][31] 设置为 0 以将水印添加到文档的第一部分。
  * 然后，调用 [Watermarker.Add()][18] 方法将图像水印添加到第一部分。
  * 调用 [Watermarker.GetContent()][32] 方法获取加载文档的内容，并在 [WordProcessingContent][33] 类对象中获取结果。
  * 循环遍历所有部分并使用真正的布尔值作为输入参数调用 [LinkToPrevious()][34] 方法。它将所有节的所有页眉和页脚与第一节链接。
  * 最后调用[Watermarker.Save()][19]方法保存加水印的Word文档。

以下代码示例展示了**如何使用 C#** 在 DOCX 文件的页眉或页脚部分添加水印。

```
// 创建水印
Watermarker watermarker = new Watermarker(@"C:\Files\Watermark\sample.docx");

// 创建图像水印
using (ImageWatermark watermark = new ImageWatermark(@"C:\Files\Watermark\logo.png"))
{
    // Set watermark properties
    watermark.Height = 100;
    watermark.Width = 100;
    watermark.HorizontalAlignment = HorizontalAlignment.Right;

    // Add watermark to all headers of the first section
    WordProcessingWatermarkSectionOptions options = new WordProcessingWatermarkSectionOptions();
    options.SectionIndex = 0;
    watermarker.Add(watermark, options);
}

// 将所有其他页眉和页脚链接到第一部分的相应页眉和页脚
WordProcessingContent content = watermarker.GetContent<WordProcessingContent>();
for (int i = 1; i < content.Sections.Count; i++)
{
    content.Sections[i].HeadersFooters.LinkToPrevious(true);
}

// 保存输出文件
watermarker.Save(@"C:\Files\Watermark\AddWatermarkToHeadersFooters_output.docx");
```

{{< figure align=center src="images/Add-Watermark-to-Header-or-Footer-of-Word-Documents-using-CSharp-1024x603.jpg" alt="使用 C# 将水印添加到 Word 文档的页眉或页脚。" caption="使用 C# 将水印添加到 Word 文档的页眉或页脚。">}}
 

## 获得免费许可证

您可以通过请求 [免费的临时许可证][36] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C# 在 Word 文档中添加文本或图像水印**。此外，您还了解了**如何以编程方式将水印添加到 Word 文档的特定页面**。本文还解释了**如何使用 C# 为 DOCX 文件中的图像添加水印**。此外，您可以使用 [documentation][37] 了解有关 .NET API 的 GroupDocs.Watermark 的更多信息。如有任何歧义，请随时在 [论坛][38] 上与我们联系。

## 也可以看看

  * [使用 C# 将水印添加到 PDF][39]
  * [在 C# 中向演示文稿添加水印][40]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/add-text-or-image-watermarks-in-word-documents-using-csharp.jpg
 [2]: #CSharp-API-to-Add-Watermark-in-Word-Documents
 [3]: #Add-Text-Watermark-in-Word-Documents-using-CSharp
 [4]: #Add-Image-Watermark-in-Word-Documents-using-CSharp
 [5]: #Watermark-Images-in-Word-Documents-using-CSharp
 [6]: #Add-Watermark-to-Specific-Pages-in-Word-Documents-using-CSharp
 [7]: #Add-Watermark-to-Header-or-Footer-of-Word-Documents-using-CSharp
 [8]: https://docs.fileformat.com/word-processing/doc
 [9]: https://docs.fileformat.com/word-processing/docx
 [10]: https://products.groupdocs.com/watermark/java
 [11]: https://docs.groupdocs.com/watermark/net/supported-document-formats/
 [12]: https://downloads.groupdocs.com/watermark/net
 [13]: https://www.nuget.org/packages/groupdocs.watermark
 [14]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/Watermarker
 [15]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/font
 [16]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
 [17]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark/properties/index
 [18]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add
 [19]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarker/save/methods/4
 [20]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Add-Text-Watermark-in-Word-Documents-using-CSharp.jpg
 [21]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/imagewatermark
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Add-Image-Watermark-in-Word-Documents-using-CSharp.jpg
 [23]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/getimages
 [24]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.contents.image/watermarkableimagecollection
 [25]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.contents.image/watermarkableimage/methods/add
 [26]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Watermark-Images-in-Word-Documents-using-CSharp.jpg
 [27]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.options.wordprocessing/wordprocessingwatermarkpagesoptions
 [28]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.options.wordprocessing/wordprocessingwatermarkpagesoptions/properties/pagenumbers
 [29]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.contents.wordprocessing/wordprocessingcontent/properties/pagecount
 [30]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.options.wordprocessing/wordprocessingwatermarksectionoptions
 [31]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.options.wordprocessing/wordprocessingwatermarksectionoptions/properties/sectionindex
 [32]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/getcontent/_1
 [33]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.contents.wordprocessing/wordprocessingcontent
 [34]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.contents.wordprocessing/wordprocessingheaderfootercollection/methods/linktoprevious
 [35]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Add-Watermark-to-Header-or-Footer-of-Word-Documents-using-CSharp.jpg
 [36]: https://purchase.groupdocs.com/temporary-license
 [37]: https://docs.groupdocs.com/watermark/net/
 [38]: https://forum.groupdocs.com/c/watermark/
 [39]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
 [40]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/








