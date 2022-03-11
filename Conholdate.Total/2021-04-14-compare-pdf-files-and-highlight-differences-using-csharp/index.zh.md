---
title: "'使用 C# 比较 PDF 文件并突出显示差异'"
author: Muzammil Khan
date: 2021-04-14T07:04:18+00:00
summary: "比较两个或多个 PDF 文件，并以编程方式突出显示单独 PDF 文件中的差异。在 .NET 应用程序中使用 C# 比较受密码保护的文件。在本文中，您将学习**如何使用 C# 比较两个或多个 PDF 文档并突出显示差异**。"
url: /zh/2021/04/14/compare-pdf-files-and-highlight-differences-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "比较多个 PDF 文件"
  - "比较 PDF 文件"
  - "使用 CSharp 比较 PDF 文件"

---


{{< figure align=center src="images/Compare-PDF-Files.jpg" alt="">}}
 

在某些情况下，您可能需要在 .NET 应用程序中比较两个或多个 PDF 文档。您可以轻松地以编程方式比较和突出差异。在本文中，您将学习**如何使用 C# 比较两个或多个 PDF 文件并突出显示差异**。

本文讨论/涵盖了以下主题：

  * [用于比较 PDF 文档的 C# API][2]
  * [使用 C# 比较两个 PDF 文件][3]
  * [使用 C# 比较受密码保护的 PDF 文件][4]

## 用于比较 PDF 文档的 C# API {#csharp-comparison-api}

为了比较 [PDF][5] 文档，我将使用 [GroupDocs.Comparison for .NET API][6]。它进行比较以检测单词、段落和字符的内容变化，同时提供列出差异摘要的比较文档。 .NET 比较库支持检查流行图像和文档格式（如 PDF、HTML、Outlook 电子邮件、Microsoft Office Word 文档、Excel 电子表格、PowerPoint 演示文稿、OneNote、Visio 图表、文本）的内容和文本样式的差异, 和图像。它可用于在任何面向 .NET 平台的开发环境中开发应用程序。

您可以[下载][7] API 的 DLL 或使用 [NuGet][8] 安装它。

```
Install-Package GroupDocs.Comparison
```

## 使用 C# 比较两个 PDF 文件 {#Compare-Two-PDF-Files-using-Csharp}

您可以按照以下简单步骤比较两个 PDF 文档：

  1. 创建 _**[Comparer][9]**_ 类的实例
  2. 向构造函数提供源 PDF 文件路径
  3. [添加][10]目标PDF文件到比较
  4. 调用 _**[Compare][11]**_ 方法以及输出文件路径

以下代码示例展示了**如何使用 C# 比较两个 PDF 文档并突出显示差异**。

```
using (Comparer comparer = new Comparer("C:\\Files\\source.pdf"))
{
    comparer.Add("C:\\Files\\target.pdf");
    comparer.Compare("C:\\Files\\result.pdf");
}
```

{{< figure align=center src="images/ComparePDFFilesUsingC-1024x644.png" alt="使用 C# 比较两个 PDF 文件" caption="使用 C# 比较两个 PDF 文件">}}
 

生成的文档在文档末尾包含一个摘要页面，显示更改摘要，如下所示：

{{< figure align=center src="images/image.png" alt="变更摘要" caption="变更摘要">}}
 

如果要比较多个 PDF 文件，则只需将多个目标 PDF 文件添加到比较中，如下所示：

```
comparer.Add("target2.docx");
comparer.Add("target3.docx");
```

## 使用 C# 比较受密码保护的 PDF 文件 {#Compare-Password-Protected-PDF-Files-using-Csharp}

您可以按照以下简单步骤比较受密码保护的 PDF 文档：

  1. 创建 _**[Comparer][9]**_ 类的实例
  2. 向构造函数提供源 PDF 文件路径
  3. 使用 _LoadOptions_ 为源文件提供密码
  4. 将目标 PDF 文件添加到比较中
  5. 使用 _LoadOptions_ 为目标文件提供密码
  6. 调用 _**[Compare][11]**_ 方法以及输出文件路径

以下代码示例展示了**如何使用 C# 比较受密码保护的 PDF 文档**。

```
using (Comparer comparer = new Comparer("C:\\Files\\source.pdf", new LoadOptions() { Password = "1234" }))
{
    comparer.Add("C:\\Files\\target.pdf", new LoadOptions() { Password = "5678" });
    comparer.Compare("C:\\Files\\result.pdf");
}
```

## 获得免费许可证

您可以通过请求 [免费的临时许可证][14] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何**如何使用 C# 比较两个或多个 PDF 文档并突出显示差异****。您可以使用 [文档][15] 了解有关 GroupDocs.Comparison .NET API 的更多信息。如有任何歧义，请随时在 [论坛][16] 上与我们联系。

## 也可以看看

  * [使用 Java 在 HTML、PDF 和图像中呈现 Visio 图表][17]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/Compare-PDF-Files.jpg
 [2]: #csharp-comparison-api
 [3]: #Compare-Two-PDF-Files-using-Csharp
 [4]: #Compare-Password-Protected-PDF-Files-using-Csharp
 [5]: https://docs.fileformat.com/pdf/
 [6]: https://products.groupdocs.com/comparison/net
 [7]: https://downloads.groupdocs.com/comparison/net
 [8]: https://www.nuget.org/packages/GroupDocs.Comparison
 [9]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
 [10]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.comparer/add/methods/2
 [11]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.comparer/compare/methods/7
 [12]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/ComparePDFFilesUsingC.png
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/image.png
 [14]: https://purchase.groupdocs.com/temporary-license
 [15]: https://docs.groupdocs.com/comparison/net/
 [16]: https://forum.groupdocs.com/c/comparison/
 [17]: https://blog.conholdate.com/2021/04/07/render-visio-diagrams-in-html-pdf-and-image-using-java/








