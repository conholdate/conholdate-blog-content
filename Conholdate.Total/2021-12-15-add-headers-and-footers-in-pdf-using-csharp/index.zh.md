---
title: "'使用 C# 在 PDF 中添加页眉和页脚'"
author: Muzammil Khan
date: 2021-12-15T04:38:40+00:00
summary: "作为 C# 开发人员，您可以在 PDF 文档的页眉和页脚中添加文本或图像。在本文中，您将学习**如何使用 C# 在 PDF 文档中添加页眉和页脚**。"
url: /zh/2021/12/15/add-headers-and-footers-in-pdf-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "在 CSharp 中添加页眉和页脚"
  - "使用 CSharp 在页脚中添加图像"
  - "使用 CSharp 在标题中添加图像"
  - "使用 CSharp 在页脚中添加页码"
  - "使用 CSharp 在页脚中添加文本"
  - "使用 CSharp 在标题中添加文本"

---


{{< figure align=center src="images/add-headers-and-footers-in-pdf-using-csharp.jpg" alt="使用 C# 在 PDF 中添加页眉和页脚">}}
 

文档中的页眉和页脚部分显示文档信息，例如文档标题、徽标、章节标题、页码等。我们可以通过编程在 PDF 文档的页眉/页脚中添加任何文本或图像。在本文中，我们将学习**如何使用 C# 在 PDF 文档中添加页眉和页脚**。

本文将涵盖以下主题：

  - "[在 PDF 文档中添加页眉和页脚的 C# API](#CSharp-API-to-Add-Headers-and-Footers-in-PDF-Documents")"
  - "[使用 C# 在 PDF 的页眉中添加文本](#Add-Text-in-Header-of-PDF-using-CSharp)"
  - "[使用 C# 在 PDF 的页脚中添加文本](#Add-Text-in-Footer-of-PDF-using-CSharp)"
  - "[使用 C# 在 PDF 的页眉中插入图像](#Insert-Image-in-Header-of-PDF-using-CSharp)"
  - "[使用 C# 在 PDF 的页脚中插入图像](#Insert-Image-in-Footer-of-PDF-using-CSharp)"
  - "[在不同页面上添加不同的页眉和页脚](#Add-Different-Headers-and-Footers-on-Different-Pages)"
  - "[使用 C# 在 PDF 的页脚中添加页码](#Add-Page-Numbers-in-Footer-of-PDF-using-CSharp)"
  
## 在 PDF 文档中添加页眉和页脚的 C# API {#CSharp-API-to-Add-Headers-and-Footers-in-PDF-Documents}

为了在 [PDF][2] 文件中添加页眉和页脚，我们将使用 [Aspose.PDF for .NET API][3]。它允许我们在不使用 Adobe Acrobat 的情况下生成、修改、转换、渲染、保护和打印 [支持的文档][4]。请[下载][5] API 的 DLL 或使用 [NuGet][6] 安装它。

```
Install-Package Aspose.PDF
```

## 使用 C# 在 PDF 的标题中添加文本 {#Add-Text-in-Header-of-PDF-using-CSharp}

我们可以按照以下步骤在现有 PDF 文档的标题中添加文本：

  1. 首先，使用 [**_Document_**][7] 类以输入文件路径作为参数加载 PDF 文档。它是代表 PDF 文档并允许执行各种功能的主要类。
  2. 接下来，创建 _**[TextStamp][8]**_ 类的实例，其中包含要显示在文档标题中的文本。
  3. 然后，将_TopMargin_、_HorizontalAlignment_、_VerticalAlignment_等各种属性设置为Top等。
  4. （可选）为文本设置 _ForegroundColor_、_Font_、_FontStyle_、_FontSize_、_BackgroundColor_、_RotateAngle_ 和 _Zoom_ 级别。
  5. 之后，遍历所有页面并使用带有 _TextStamp_ 对象的 **_[Page.AddStamp()][9]_** 方法添加页眉。
  6. 最后，调用**_[Document.Save()][10]_**方法，将输出文件路径作为参数保存输出文件。

以下代码示例展示了**如何使用 C# 在 PDF 文档的标题中添加文本**。

```
// 此代码示例演示如何在现有 PDF 文档的页眉中添加文本。
// 加载 PDF 文档
Document pdfDocument = new Document(@"C:\Files\sample.pdf");

// 创建标题
TextStamp textStamp = new TextStamp("Header Text");

// 设置图章的属性
textStamp.TopMargin = 10;
textStamp.HorizontalAlignment = HorizontalAlignment.Center;
textStamp.VerticalAlignment = VerticalAlignment.Top;

// 指定字体样式
textStamp.TextState.FontStyle = FontStyles.Bold;
textStamp.TextState.ForegroundColor = Color.Red;
textStamp.TextState.FontSize = 14;
textStamp.TextState.BackgroundColor = Color.Pink;
textStamp.TextState.Font = FontRepository.FindFont("Verdana");

// 在所有页面上添加标题
foreach (Page page in pdfDocument.Pages)
{
    page.AddStamp(textStamp);
}

// 保存更新的文档
pdfDocument.Save(@"C:\Files\output.pdf");
```

{{< figure align=center src="images/Add-Text-In-Header-of-PDF-using-CSharp.jpg" alt="使用 C# 在 PDF 的页眉中添加文本。" caption="使用 C# 在 PDF 的页眉中添加文本。">}}
 

## 使用 C# 在 PDF 的页脚中添加文本 {#Add-Text-in-Footer-of-PDF-using-CSharp}

我们可以按照前面提到的步骤以编程方式在 PDF 文档的页脚中添加文本。但是，我们需要将 _BottomMargin_ 和 _VerticalAlignment_ 设置为底部以在页脚中显示文本。

以下代码示例展示了**如何使用 C# 在 PDF 文档的页脚中添加文本**。

```
// 此代码示例演示如何在现有 PDF 文档的页脚中添加文本。
// 加载 PDF 文档
Document pdfDocument = new Document(@"C:\Files\sample.pdf");

// 创建页脚
TextStamp textStamp = new TextStamp("Footer Text");

// 设置图章的属性
textStamp.BottomMargin = 10;
textStamp.HorizontalAlignment = HorizontalAlignment.Center;
textStamp.VerticalAlignment = VerticalAlignment.Bottom;

// 在所有页面上添加页脚
foreach (Page page in pdfDocument.Pages)
{
    page.AddStamp(textStamp);
}

// 保存更新的文档
pdfDocument.Save(@"C:\Files\output.pdf");
```

{{< figure align=center src="images/Add-Text-In-Footer-of-PDF-using-CSharp-1024x396.jpg" alt="使用 C# 在 PDF 的页脚中添加文本。" caption="使用 C# 在 PDF 的页脚中添加文本。">}}
 

## 使用 C# 在 PDF 的页眉中插入图像 {#Insert-Image-in-Header-of-PDF-using-CSharp}

我们还可以按照以下步骤在现有 PDF 文档的标题中添加图像：

  1. 首先，使用 [**_Document_**][7] 类以输入文件路径作为参数加载 PDF 文档。
  2. 接下来，使用图像文件路径作为参数创建 _**[ImageStamp][13]**_ 类的实例。
  3. 然后，将_TopMargin_、_HorizontalAlignment_、_VerticalAlignment_等各种属性设置为Top等。
  4. 之后，遍历所有页面并使用带有 _ImageStamp_ 对象的 **_[Page.AddStamp()][9]_** 方法添加页眉。
  5. 最后，调用**_[Document.Save()][10]_**方法，将输出文件路径作为参数保存输出文件。

以下代码示例展示了**如何使用 C# 在 PDF 文档的标题中添加图像**。

```
// 此代码示例演示如何在现有 PDF 文档的页眉中添加图像。
// 加载 PDF 文档
Document pdfDocument = new Document(@"C:\Files\sample.pdf");

// 创建标题
ImageStamp imageStamp = new ImageStamp(@"C:\Files\conholdate-logo.jpg");

// 设置图章的属性
imageStamp.TopMargin = 10;
imageStamp.HorizontalAlignment = HorizontalAlignment.Center;
imageStamp.VerticalAlignment = VerticalAlignment.Top;

// 在所有页面上添加标题
foreach (Page page in pdfDocument.Pages)
{
    page.AddStamp(imageStamp);
}

// 保存更新的文档
pdfDocument.Save(@"C:\Files\output.pdf");
```

{{< figure align=center src="images/Add-Image-In-Header-of-PDF-using-CSharp-1024x498.jpg" alt="使用 C# 在 PDF 的页眉中插入图像。" caption="使用 C# 在 PDF 的页眉中插入图像。">}}
 

## 使用 C# 在 PDF 的页脚中插入图像 {#Insert-Image-in-Footer-of-PDF-using-CSharp}

我们可以按照前面提到的步骤以编程方式在 PDF 文档的页脚中添加图像。但是，我们需要将 _BottomMargin_ 和 _VerticalAlignment_ 设置为底部以在页脚中显示图像。

以下代码示例展示了**如何使用 C# 在 PDF 文档的页脚中添加图像**。

```
// 此代码示例演示如何在现有 PDF 文档的页脚中添加图像。
// 加载 PDF 文档
Document pdfDocument = new Document(@"C:\Files\sample.pdf");

// 创建页脚
ImageStamp imageStamp = new ImageStamp(@"C:\Files\conholdate-logo.jpg");

// 设置图章的属性
imageStamp.BottomMargin = 10;
imageStamp.HorizontalAlignment = HorizontalAlignment.Center;
imageStamp.VerticalAlignment = VerticalAlignment.Bottom;

// 在所有页面上添加页脚
foreach (Page page in pdfDocument.Pages)
{
    page.AddStamp(imageStamp);
}

// 保存更新的文档
pdfDocument.Save(@"C:\Files\output.pdf");
```

{{< figure align=center src="images/Add-Image-In-Footer-of-PDF-using-CSharp-1024x498.jpg" alt="使用 C# 在 PDF 的页脚中插入图像。" caption="使用 C# 在 PDF 的页脚中插入图像。">}}
 

## 在不同的页面上添加不同的页眉和页脚 {#Add-Different-Headers-and-Footers-on-Different-Pages}

我们可以按照以下步骤为单个 PDF 文档中的不同页面添加不同的页眉/页脚：

  1. 首先，使用 [**_Document_**][7] 类以输入文件路径作为参数加载 PDF 文档。 
  2. 接下来，创建带有图像文件路径的 _**[ImageStamp][13]**_ 类和/或带有要显示的文本的 _**[TextStamp][8]**_ 类的多个实例。
  3. 然后，将_TopMargin_、_HorizontalAlignment_ 和_VerticalAlignment_ 等各种属性设置为页眉的Top，将_BottomMargin_ 和_VerticalAlignment_ 设置为页脚的Bottom。
  4. 之后，使用带有 _ImageStamp_ 或 _TextStamp_ 对象的 **_[Page.AddStamp()][9]_** 方法添加页眉或页脚。
  5. 最后，调用**_[Document.Save()][10]_**方法，将输出文件路径作为参数保存输出文件。

以下代码示例展示了**如何使用 C# 在单个 PDF 文档中添加多个页眉和页脚**。

```
// 此代码示例演示了如何为单个 PDF 文档中的不同页面添加不同的页眉。
// 加载 PDF 文档
Document pdfDocument = new Document(@"C:\Files\sample.pdf");

// 创建三个邮票
ImageStamp stamp1 = new ImageStamp(@"C:\Files\PDF\conholdate-logo.jpg");
TextStamp stamp2 = new TextStamp("Header Stamp 2");
TextStamp stamp3 = new TextStamp("Header Stamp 3");

// 为 stamp1 设置图章对齐
stamp1.VerticalAlignment = VerticalAlignment.Top;
stamp1.HorizontalAlignment = HorizontalAlignment.Center;

// 为 stamp2 设置图章对齐
stamp2.VerticalAlignment = VerticalAlignment.Top;
// 将图章的水平对齐信息设置为居中对齐
stamp2.HorizontalAlignment = HorizontalAlignment.Center;
// 设置图章对象的缩放系数
stamp2.Zoom = 10;

// 为 stamp3 设置图章对齐方式
stamp3.VerticalAlignment = VerticalAlignment.Top;
// 将图章对象的水平对齐信息设置为居中对齐
stamp3.HorizontalAlignment = HorizontalAlignment.Center;
// 设置图章对象的旋转角度
stamp3.RotateAngle = 35;


// 在第一页添加第一个印章；
pdfDocument.Pages[1].AddStamp(stamp1);

// 在第二页添加第二个印章；
pdfDocument.Pages[2].AddStamp(stamp2);

// 在第三页添加第三个印章。
pdfDocument.Pages[3].AddStamp(stamp3);

// 保存更新的文档
pdfDocument.Save(@"C:\Files\output.pdf");
```

## 使用 C# 在 PDF 的页脚中添加页码 {#Add-Page-Numbers-in-Footer-of-PDF-using-CSharp}

我们可以按照以下步骤在 PDF 文档的页脚部分添加页码：

  1. 首先，使用 [**_Document_**][7] 类以输入文件路径作为参数加载 PDF 文档。
  2. 接下来，对 **_[Document.Pages][16]_** 集合中的每个页面执行以下操作。
      * 创建 _**[TextStamp][8]**_ 类的实例，其中包含与当前页码连接的文本。
      * 然后，将_BottomMargin_、_HorizontalAlignment_、_VerticalAlignment_等各种属性设置为Bottom等。
      * 之后，使用 _TextStamp_ 对象调用 **_[Page.AddStamp()][9]_** 方法在页脚中添加页码。
  3. 最后，调用**_[Document.Save()][10]_**方法，将输出文件路径作为参数保存输出文件。

以下代码示例展示了**如何使用 C# 为 PDF 文档页脚中的每一页添加页码**。

```
// 此代码示例演示如何在 PDF 文档的每一页的页脚中添加页码。 
// 加载 PDF 文档
Document pdfDocument = new Document(@"C:\Files\sample.pdf");

// 在所有页面上添加页脚
foreach (Page page in pdfDocument.Pages)
{
    // Create footer
    TextStamp textStamp = new TextStamp("Page " + page.Number + " of " + pdfDocument.Pages.Count + " pages.");
    
    // Set properties of the stamp
    textStamp.BottomMargin = 10;
    textStamp.HorizontalAlignment = HorizontalAlignment.Center;
    textStamp.VerticalAlignment = VerticalAlignment.Bottom;

    // Add stamp
    page.AddStamp(textStamp);
}

// 保存更新的文档
pdfDocument.Save(@"C:\Files\PDF\output.pdf");
```

{{< figure align=center src="images/Add-Page-No-In-Footer-of-PDF-using-CSharp-1024x501.jpg" alt="在页脚中添加页码。" caption="使用 C# 在 PDF 的页脚中添加页码。">}}
 

## 获取免费 API 许可证 {#Get-a-Free-License}

您可以通过请求 [免费的临时许可证][18] 来试用该 API，而不受评估限制。

## 结论

在本文中，我们学习了**如何使用 C# 在现有 PDF 文件的页眉/页脚中添加文本或图像**。我们还看到了**如何在 PDF 文档的不同页面上添加不同的页眉**和**如何在文档的页脚中添加页码**。此外，您可以使用 [文档][19] 了解更多关于 Aspose.PDF for .NET API 的信息。如有任何歧义，请随时在 [论坛][20] 上与我们联系。

## 也可以看看

  * [使用 C# 在 PDF 文档中添加形状][21]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/12/add-headers-and-footers-in-pdf-using-csharp.jpg
 [2]: https://docs.fileformat.com/pdf/
 [3]: https://products.aspose.com/pdf/net/
 [4]: https://docs.aspose.com/pdf/net/supported-file-formats/
 [5]: https://downloads.aspose.com/pdf/net
 [6]: https://www.nuget.org/packages/aspose.pdf
 [7]: https://apireference.aspose.com/pdf/net/aspose.pdf/document
 [8]: https://apireference.aspose.com/pdf/net/aspose.pdf/textstamp
 [9]: https://apireference.aspose.com/pdf/net/aspose.pdf/page/methods/addstamp
 [10]: https://apireference.aspose.com/pdf/net/aspose.pdf.document/save/methods/4
 [11]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/12/Add-Text-In-Header-of-PDF-using-CSharp.jpg
 [12]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/12/Add-Text-In-Footer-of-PDF-using-CSharp.jpg
 [13]: https://apireference.aspose.com/pdf/net/aspose.pdf/imagestamp
 [14]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/12/Add-Image-In-Header-of-PDF-using-CSharp.jpg
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/12/Add-Image-In-Footer-of-PDF-using-CSharp.jpg
 [16]: https://apireference.aspose.com/pdf/net/aspose.pdf/document/properties/pages
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/12/Add-Page-No-In-Footer-of-PDF-using-CSharp.jpg
 [18]: https://purchase.conholdate.com/temporary-license
 [19]: https://docs.aspose.com/pdf/net/
 [20]: https://forum.aspose.com/
 [21]: https://blog.conholdate.com/2021/11/11/add-shapes-in-pdf-documents-using-csharp/








