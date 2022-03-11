---
title: "'使用 C# 将 Word 文档转换为 TIFF 图像'"
author: Muzammil Khan
date: 2022-01-26T07:56:46+00:00
summary: "作为 C# 开发人员，您可以通过编程轻松地将 Word 文档转换为多页 TIFF 图像。在本文中，您将学习**如何使用 C# 将 Word 文档转换为 TIFF 图像**。"
url: /zh/2022/01/26/convert-word-document-to-tiff-image-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "将 Word 转换为 TIFF"
  - "在 C# 中将 Word 转换为 TIFF"
  - "DOCX 转 TIFF"
  - "DOCX 到 TIFF 使用 C#"
  - "单词到 TIFF"
  - "使用 C# 将 Word 转换为 TIFF"

---


{{< figure align=center src="images/convert-word-document-to-tiff-image-using-csharp.jpg" alt="使用 C# 将 Word 文档转换为 TIFF 图像">}}
 

我们可以轻松地将 Word 文档（[DOC][2] 或 [DOCX][3]）转换为光栅图像。光栅图像能够呈现复杂和多色的视觉效果。 [TIFF][4] 是一种流行的存储光栅图像的格式。它支持以页面的形式保存多个图像。 TIFF 格式的这一显着特征使其成为以只读格式呈现 Word 文档的合适选择。在本文中，我们将学习**如何使用 C# 将 Word 文档转换为 TIFF 图像**。

本文将涵盖以下主题：

  * [将 Word 转换为 TIFF 的 C# API][5]
  * [在 C# 中将 Word 文档转换为 TIFF][6]
  * [在 C# 中自定义 Word 到 TIFF 的转换][7]

## 将 Word 转换为 TIFF 的 C# API {#CSharp-API-to-Convert-Word-to-TIFF}

为了将 **DOC 转换为 TIFF** 或 **DOCX 转换为 TIFF**，我们将使用 [Aspose.Words for .NET][8] API。它使我们能够生成、修改、转换、渲染和打印文件，而无需直接在跨平台应用程序中使用 Microsoft Word。请[下载][9] API 的 DLL 或使用 [NuGet][10] 安装它。

```
PM> Install-Package Aspose.Words
```

## 在 C# 中将 Word 文档转换为 TIFF {#Convert-Word-Document-to-TIFF-in-CSharp}

我们可以按照以下步骤将 Word 文档转换为多页 TIFF：

  1. 使用 _**[Document][11]**_ 类加载 Word 文档。
  2. 使用 _**[Save()][12]**_ 方法将文档保存为 TIFF 文件。它将输出文件的路径作为参数。

以下代码示例演示如何使用 C# 将 Word 文档转换为 TIFF。

```
// 此代码示例演示如何将 DOCX 转换为 TIFF。
// 加载 Word 文档
Document doc = new Document("C:\\Files\\Document.docx");

// 将 Word 转换为 TIFF
doc.Save("C:\\Files\\SaveWordAsTiff.tiff");
```

{{< figure align=center src="images/Convert-Word-Document-to-TIFF-in-CSharp-1024x611.jpg" alt="在 C# 中将 Word 文档转换为 TIFF。" caption="在 C# 中将 Word 文档转换为 TIFF。">}}
 

## 在 C# 中自定义 Word 到 TIFF 的转换 {#Customize-Word-to-TIFF-Conversion-in-CSharp}

我们可以使用不同的选项来自定义 Word 文档到 TIFF 的转换。为此，API 提供了 _ImageSaveOptions _class。它允许设置图像亮度、分辨率、要转换的页面范围、压缩方案等。请按照下面提到的步骤在将 Word 转换为 TIFF 时设置其他选项。

  1. 首先，使用 [Document](https://apireference.aspose.com/words/net/aspose.words/Document) 类加载 Word 文档。
  2. 接下来，使用输入图像格式作为参数创建 [ImageSaveOptions](https://apireference.aspose.com/words/net/aspose.words.saving/imagesaveoptions) 类的实例。
  3. 之后，设置所需的选项，例如 [TiffCompression](https://apireference.aspose.com/words/net/aspose.words.saving/imagesaveoptions/properties/tiffcompression)、分辨率等。
  4. 最后调用[Save(string, ImageSaveOptions)](https://apireference.aspose.com/words/net/aspose.words.document/save/methods/4)方法将Word转为TIFF。

以下代码示例展示了**如何使用附加选项将 Word 文档转换为 TIFF 图像**。

```
// 此代码示例演示如何使用附加选项将 DOCX 转换为 TIFF。
// 加载 Word 文档
Document doc = new Document("C:\\Files\\Document.docx");

// 创建一个 ImageSaveOptions 对象以传递给 Save 方法
ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Tiff);

// 设置要呈现的页面
options.PageSet = new PageSet(1);

// 应用 CCITT4 压缩
options.TiffCompression = TiffCompression.Ccitt4;

// 设置图像的亮度和对比度。
// 两者的比例均为 0-1，默认为 0.5。
options.ImageBrightness = 0.3f;
options.ImageContrast = 0.7f;

// 设置水平和垂直分辨率 
// 生成的图像，以每英寸点数为单位。
// 将“分辨率”属性设置为“72”以以 72dpi 呈现文档。
options.Resolution = 72;

// 将 Word 转换为 TIFF
doc.Save("C:\\Files\\Convert_with_Options.tiff");
```

## 获得免费许可证

请通过请求 [免费的临时许可证][14] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了**如何使用 C# 将 Word 文档转换为 TIFF 图像**。我们还了解了如何以编程方式应用其他选项，例如 TIFF 压缩和分辨率。此外，您可以使用 [文档][15] 了解更多关于 Aspose.Words for .NET API 的信息。如有任何歧义，请随时在 [论坛][16] 上与我们联系。

## 也可以看看

  * [使用 C# 合并 Word 文档][17]

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







