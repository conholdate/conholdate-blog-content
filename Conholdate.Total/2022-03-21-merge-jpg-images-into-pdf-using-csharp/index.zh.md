---
title: "'使用 C# 将 JPG 图像合并为 PDF'"
author: Muzammil Khan
date: 2022-03-21T06:43:17+00:00
summary: "我们可以在 C# 中以编程方式轻松地将多个 JPG 图像转换并组合成一个 PDF 文档。在本文中，您将学习**如何使用 C# 将 JPG 图像合并到 PDF 中**。"
url: /zh/2022/03/21/merge-jpg-images-into-pdf-using-csharp/

categories:
  - "Conholdate.Total 产品系列"
tags:
  - "C# API 将 JPG 合并为 PDF"
  - "在 C# 中将 JPG 转换为 PDF"
  - "使用 C# 在 PDF 中合并 JPG"
  - "使用 C# 在 PDF 中合并 JPG 图像"
  - "JPG转PDF"
  - "将 JPG 合并为 PDF"
  - "将图像合并为 PDF"
  - "Aspose.Imaging 对于 C#"
  - "GroupDocs.Merger .NET"
---

{{< figure align=center src="images/merge-jpg-images-into-pdf-using-csharp.jpg" alt="使用 C# 将 JPG 合并为 PDF">}}
 
[JPG][1] 是用于存储压缩图像的最广泛使用的图像文件格式。另一方面，[PDF][2] 允许以只读格式共享文档，而不会影响其样式或布局。我们有时可能需要将大量 JPG 照片合并成一个 PDF 文档。在本文中，我们将学习**如何使用 C# 将 JPG 图像合并到 PDF 文档中**。

本文将涵盖以下主题：

  * [将 JPG 图像合并为 PDF 的 C# API][3]
  * [在 C# 中将 JPG 转换为 PDF][4]
  * [使用 C# 在 PDF 中附加 JPG 图像][5]
  * [使用 C# 将多个 JPG 图像合并为 PDF][6]

## 将 JPG 图像合并为 PDF 的 C# API {#CSharp-API-to-Merge-JPG-Images-into-PDF}

要将两个或多个 JPG 图像合并到 PDF 文档中，我们将遵循两步过程。首先，我们将使用 [Aspose.Imaging for .NET][7] 将 JPG 转换为 PDF，然后我们将使用 [GroupDocs.Merger for .NET][8] API 将它们合并为 PDF 文档。请[下载][9] API 的 DLL 或使用 [NuGet][10] 安装它们。

```
PM> Install-Package Aspose.Imaging
PM> Install-Package GroupDocs.Merger
```

## 在 C# 中将 JPG 转换为 PDF {#Convert-JPG-to-PDF-in-CSharp}

我们可以按照以下步骤将任何 JPG 图像转换为 PDF 文档：

  1. 使用 _**[Image.Load()][11]**_ 方法加载 JPG 图像。
  2. 最后调用_**[Image.Save()][12]**_ 方法将图片保存为PDF。它将输出文件路径作为参数。

以下代码示例展示了**如何使用 C# 将 JPG 转换为 PDF**。

```
// 此代码示例演示如何将 JPG 图像转换为 PDF 文档。
// 加载 JPG 图片
Image image = Image.Load(@"sample1.jpg");

// 另存为 PDF
image.Save(@"converted.pdf");
```

{{< figure align=center src="images/Convert-JPG-to-PDF-in-CSharp.jpg" alt="在 C# 中将 JPG 转换为 PDF。" caption="在 C# 中将 JPG 转换为 PDF。">}}

## 使用 C# 在 PDF 中附加 JPG 图像 {#Append-JPG-Image-in-PDF-using-CSharp}

我们可以按照以下步骤将 JPG 图像附加到现有的 PDF 文档中：

  1. 使用 _**[Image.Load()][11]**_ 方法加载 JPG 图像。
  2. 使用 _**[Image.Save()][13]**_ 方法将加载的图像转换为 PDF 并保存在 FileStream 中。
  3. 使用 _**[Merger][14]**_ 类加载现有 PDF。
  4. 调用 _**[Merger.Join()][15]**_ 方法将 JPG 转换的 PDF 与加载的 PDF 连接。
  5. 最后，调用 _**[Merger.Save()][16]**_ 方法保存合并的 PDF。它将输出文件路径作为参数。

以下代码示例展示了**如何使用 C# 将 JPG 图像附加到现有 PDF 文档中**。

```
// 此代码示例演示如何在现有 PDF 中附加 JPG。
// 加载 JPG 图片
Image image = Image.Load(@"sample1.jpg");

// 转换为 PDF 并保存在 FileStream 中
FileStream fs = new FileStream("image.pdf", FileMode.Create);
image.Save(fs);

// 加载现有 PDF
Merger merger = new Merger(@"sample.pdf");

// 将 JPG 转换后的 PDF 与加载的 PDF 连接起来
merger.Join(fs);

// 保存合并的 PDF
merger.Save(@"Merged.pdf");
```

{{< figure align=center src="images/Append-JPG-Image-in-PDF-using-CSharp.jpg" alt="使用 C# 在 PDF 中附加 JPG 图像。" caption="使用 C# 在 PDF 中附加 JPG 图像。">}}

## 使用 C# 将多个 JPG 图像合并为 PDF {#Merge-Multiple-JPG-Images-into-PDF-using-CSharp}

我们可以按照以下步骤将多个 JPG 图像合并到一个 PDF 文档中：

  1. 一张一张地读取一个目录下的所有JPG图片文件。
  2. 使用 _**[Image.Load()][11]**_ 方法加载 JPG 图像。
  2. 将第一个图像转换为 PDF 并将文件保存在本地磁盘上。否则，转换并保存在 FileStream 中。
  3. 使用 _**[Merger][14]**_ 类加载以前保存的 PDF。
  4. 调用 _**[Merger.Join()][15]**_ 方法将 JPG 转换的 PDF 与加载的 PDF 连接。
  5. 最后，调用 _**[Merger.Save()][16]**_ 方法保存合并的 PDF。它将输出文件路径作为参数。

以下代码示例展示了**如何使用 C# 将多个 JPG 图像合并到 PDF 文档中**。

```
// 此代码示例演示如何将 JPG 图像合并到 PDF 中。
int count = 0;
foreach (string fileName in Directory.GetFiles(@"D:\Files\Images\", "*.jpg"))
{
    // Load JPG image
    Image image = Image.Load(fileName);

    if (count == 0)
    {
        // Save PDF file
        image.Save(@"D:\Files\Images\converted.pdf");
        count = 1;   
    }
    else
    {
        // Convert to PDF and save in FileStream
        FileStream fs = new FileStream(fileName + ".pdf", FileMode.Create);
        image.Save(fs);

        // Merge
        using (Merger merger = new Merger(@"D:\Files\images\converted.pdf"))
        {
            merger.Join(fs);
            merger.Save(@"D:\Files\images\converted.pdf");
        }
    }
}
```

{{< figure align=center src="images/Merge-Multiple-JPG-Images-into-PDF-using-CSharp.jpg" alt="使用 C# 将多个 JPG 图像合并为 PDF。" caption="使用 C# 将多个 JPG 图像合并为 PDF。">}}

## 获得免费许可证

请通过请求 [免费的临时许可证][17] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了如何：
  * 在 C# 中将 JPG 图像保存为 PDF 文档；
  * 以编程方式在 PDF 文档中插入图像；
  * 在 PDF 文档中合并多个图像。
 
此外，您可以使用 [文档][18] 了解更多关于 Aspose.Imaging for .NET API 的信息。如有任何歧义，请随时在 [论坛][19] 上与我们联系。

## 也可以看看

  * [使用 C# 裁剪和调整 JPEG 图像大小][20]
  * [使用 C# 合并 Word 文档][21]

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
  [18]: https://docs.aspose.com/imaging/net/
  [19]: https://forum.aspose.com/c/imaging/14
  [20]: https://blog.conholdate.com/2022/01/05/crop-and-resize-jpeg-images-using-csharp/
  [21]: https://blog.conholdate.com/2021/11/19/merge-word-documents-using-csharp/
