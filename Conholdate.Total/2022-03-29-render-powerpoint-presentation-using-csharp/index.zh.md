---
title: "'使用 C# 渲染 PowerPoint 演示文稿'"
author: Muzammil Khan
date: 2022-03-29T06:43:17+00:00
summary: "作为 C# 开发人员，您可以轻松地以编程方式呈现或查看 HTML 或 PDF 文档中的 PowerPoint 演示文稿 (PPT/PPTX)。在本文中，您将学习**如何使用 C# 呈现 PowerPoint 演示文稿**。"
url: /zh/2022/03/29/render-powerpoint-presentation-using-csharp/

categories:
  - "Conholdate.Total 产品系列"
tags:
  - "C# API 查看 PPTX"
  - "PPTX 查看器"
  - "C# PPTX 查看器"
  - "C# 中的 PowerPoint 查看器"
  - "在 C# 中将 PPTX 转换为 PDF"
  - "使用 C# 将 PPTX 转换为 HTML"
  - "渲染 PowerPoint"
  - "PPTX转PDF"
  - "PPTX 转 HTML"
  - "将 PPTX 幻灯片转换为 JPG"
  - "GroupDocs.Viewer .NET"
---

{{< figure align=center src="images/render-powerpoint-presentation-using-csharp.jpg" alt="使用 C# 渲染 PowerPoint 演示文稿">}}
 
MS PowerPoint 允许以演示幻灯片的形式呈现信息或数据。它还提供了一个 PowerPoint 查看器，可以将所有幻灯片作为幻灯片放映进行查看。在某些情况下，我们可能需要以其他格式呈现 PowerPoint 演示幻灯片，例如 [PDF][1]、[JPG][2] 图像或 [HTML][3]。在本文中，我们将学习**如何使用 C# 以其他格式呈现 PowerPoint 演示文稿**。

本文将涵盖以下主题：

  * [用于渲染 PowerPoint 演示文稿的 C# API][4]
  * [以 PDF 格式呈现 PowerPoint 演示文稿][5]
  * [以 HTML 格式查看 PowerPoint 演示文稿][6]
  * [以 HTML 格式呈现 PowerPoint 笔记][28]
  * [将 PowerPoint 幻灯片转换为 JPG 图像][7]

## 用于渲染 PowerPoint 演示文稿的 C# API {#CSharp-API-to-Render-PowerPoint-Presentation}

为了以其他格式呈现 [PPT][8] 或 [PPTX][9] 文件，我们将使用 [GroupDocs.Viewer for .NET][10] API。它允许以编程方式呈现和查看[支持的 PowerPoint 演示文稿格式][11]。请[下载][12] API 的 DLL 或使用 [NuGet][13] 安装它。

```
PM> Install-Package GroupDocs.Viewer
```

## 使用 C# 以 PDF 格式呈现 PowerPoint 演示文稿 {#Render-PowerPoint-Presentation-in-PDF-using-CSharp}

我们可以按照以下步骤将 PowerPoint 演示文稿呈现为 PDF 文档：

  1. 使用 _**[Viewer][14]**_ 类加载 PowerPoint 演示文稿。
  2. 使用输出 PDF 文件路径作为参数创建 _**[PdfViewOptions][15]**_ 类的实例。
  3. 最后调用 _**[View()][16]**_ 方法将 PPTX 保存为 PDF。它将 _**PdfViewOptions**_ 对象作为参数。

以下代码示例展示了**如何使用 C# 将 PPTX 文件呈现为 PDF**。

```
// 此代码示例演示如何在 PDF 中呈现 PPTX。
// 加载 PowerPoint PPTX 文件
看法er viewer = new 看法er(@"D:\Files\看法er\sample.pptx");

// 定义 PDF 视图选项。
// Pdf看法Options 类提供了将文档呈现为 PDF 格式的选项。
Pdf看法Options viewOptions = new Pdf看法Options(@"D:\Files\看法er\sample_output.pdf");

// 看法
viewer.看法(viewOptions);
```

{{< figure align=center src="images/Render-PowerPoint-Presentation-in-PDF-using-CSharp.jpg" alt="使用 C# 以 PDF 格式呈现 PowerPoint 演示文稿。" caption="使用 C# 以 PDF 格式呈现 PowerPoint 演示文稿。">}}

## 使用 C# 以 HTML 格式查看 PowerPoint 演示文稿 {#View-PowerPoint-Presentation-in-HTML-using-CSharp}

我们还可以按照以下步骤以 HTML 格式呈现 PowerPoint 演示文稿以在浏览器中查看：

  1. 使用 _**[Viewer][14]**_ 类加载 PowerPoint 演示文稿。
  2. 使用 _**[ForEmbeddedResources][18]**_ 方法创建 _**[HtmlViewOptions][17]**_ 类的实例。它将输出 HTML 文件路径作为参数。
  3. 设置各种_**HtmlViewOptions**_如RenderToSinglePage等。
  4. 最后，调用 **_[View()][16]_** 方法将 PPTX 保存为 HTML。它将 _**HtmlViewOptions**_ 对象作为参数。

以下代码示例展示了**如何使用 C# 将 PPTX 呈现为 HTML**。

```
// 此代码示例演示如何在 HTML 中呈现 PPTX。
// 加载 PowerPoint PPTX 文件
看法er viewer = new 看法er(@"D:\Files\看法er\sample.pptx");

// 定义 HTML 视图选项
// Html看法Options 类提供了将文档呈现为 HTML 格式的选项。
// 使用嵌入资源渲染为 HTML 将页面资源集成到 HTML 中，并使每个文档 
// 页面自给自足。缺点是页面大小和加载速度可能会降低。
Html看法Options viewOptions = Html看法Options.ForEmbeddedResources(@"D:\Files\看法er\sample_output.html");

// 在单个 HTML 页面中呈现所有幻灯片。
viewOptions.RenderToSinglePage = true;

// 看法
viewer.看法(viewOptions);
```

{{< figure align=center src="images/View-PowerPoint-Presentation-in-HTML-using-CSharp.jpg" alt="使用 C# 以 HTML 格式查看 PowerPoint 演示文稿。" caption="使用 C# 以 HTML 格式查看 PowerPoint 演示文稿。">}}

## 使用 C# 以 HTML 格式呈现 PowerPoint 笔记 {#Render-PowerPoint-Notes-in-HTML-using-CSharp}

我们可以按照前面提到的步骤以 HTML 格式呈现 PowerPoint 演示文稿笔记。但是，我们只需要启用注释的渲染，如下所示：

```
viewOptions.RenderNotes = true;
```

以下代码示例显示**如何使用 C# 以 HTML 格式呈现 PowerPoint 演示文稿注释**。

```
// 此代码示例演示如何在 HTML 中呈现 PPTX 演示文稿注释。
// 加载 PowerPoint PPTX 文件
看法er viewer = new 看法er(@"D:\Files\看法er\sample.pptx");

// 定义 HTML 视图选项
Html看法Options viewOptions = Html看法Options.ForEmbeddedResources(@"D:\Files\看法er\sample_output.html");

// 在单个 HTML 页面中呈现所有幻灯片。
viewOptions.RenderToSinglePage = true;

// 呈现演示文稿注释
viewOptions.RenderNotes = true;

// 看法
viewer.看法(viewOptions);
```

{{< figure align=center src="images/Render-PowerPoint-Presentation-Notes-in-HTML-using-CSharp.jpg" alt="使用 C# 以 HTML 格式呈现 PowerPoint 演示文稿注释。" caption="使用 C# 以 HTML 格式呈现 PowerPoint 演示文稿注释。">}}

## 使用 C# 将 PowerPoint 幻灯片转换为 JPG 图像 {#Convert-PowerPoint-Slides-into-JPG-images-using-CSharp}

我们可以按照以下步骤呈现 PowerPoint 演示文稿并将所有幻灯片保存为 JPG 图像：

  1. 使用 _**[Viewer][14]**_ 类加载 PowerPoint 演示文稿。
  2. 使用 _**[ForJpgView][20]**_ 方法创建 _**[ViewInfoOptions][19]**_ 类的实例。
  3. 使用 _**[GetViewInfo][22]**_ 方法获取 _**[ViewInfo][21]**_。
  4. 阅读 _**ViewInfo.Pages.Count**_ 属性并一张一张地遍历所有幻灯片。
  5. 创建 _**[JpgViewOptions][23]**_ 类的实例。
  6. 最后，调用_**[View()][16]**_ 方法将幻灯片保存为JPG。它将 JpgViewOptions 对象和页码作为参数。

以下代码示例显示**如何使用 C# 将 PowerPoint 幻灯片呈现为 JPG 图像**。

```
// 此代码示例演示如何在 JPG 中呈现 PPTX。
// 加载 PowerPoint PPTX 文件
Viewer viewer = new Viewer(@"D:\Files\Viewer\sample.pptx");

// 获取文件信息，例如文件类型和页数
// ViewInfoOptions 类提供用于检索有关视图的信息的选项。
// ForJpgView() 方法在渲染为 JPG 时检索信息。
ViewInfoOptions viewInfoOptions = ViewInfoOptions.ForJpgView();
ViewInfo viewInfo = viewer.GetViewInfo(viewInfoOptions);

// 显示文档信息
Console.WriteLine("Document type is: " + viewInfo.FileType);
Console.WriteLine("Pages count: " + viewInfo.Pages.Count);

// 将 easch 幻灯片另存为 JPG 图像
for(int count=1;count<=viewInfo.Pages.Count;count++)
{
    // Define JPG view options
    // JpgViewOptions class provides options for rendering documents into JPG format.
    JpgViewOptions viewOptions = new JpgViewOptions(@"D:\Files\Viewer\Images\"+ "slide_" + count + ".jpg");
    
    // Render view
    viewer.View(viewOptions, count);
}
```

{{< figure align=center src="images/Convert-PowerPoint-Slides-into-JPG-images-using-CSharp.jpg" alt="使用 C# 将 PowerPoint 幻灯片转换为 JPG 图像。" caption="使用 C# 将 PowerPoint 幻灯片转换为 JPG 图像。">}}

## 获得免费许可证

请通过请求 [免费的临时许可证][24] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了如何：
  * 在 C# 中将 PPTX 中的 PowerPoint 幻灯片渲染为 PDF；
  * 以编程方式在浏览器中查看 PowerPoint 幻灯片；
  * 将 PowerPoint 幻灯片转换为 JPG 图像。
 
此外，您可以使用 [documentation][25] 了解更多关于 GroupDocs.Viewer for .NET API 的信息。如有任何歧义，请随时在 [论坛][26] 上与我们联系。

## 也可以看看

  * [Excel 文件查看器 - 使用 C# 显示 Excel 数据][27]

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
