---
title: "使用 Java 在 HTML、PDF 和图像中呈现 Visio 图表"
author: Muzammil Khan
date: 2021-04-07T08:54:39+00:00
summary: "以编程方式呈现 HTML、PDF 和其他流行图像格式的 Visio 图表（.vsdx、.vssx、.vstx）文件。在本文中，您将学习**如何使用 Java 以 HTML、PDF 和图像呈现 Visio 图表**。"
url: /zh/2021/04/07/render-visio-diagrams-in-html-pdf-and-image-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "呈现为 PDF"
  - "将 Visio 文件呈现为 HTML"
  - "将 Visio 文件呈现为图像"
  - "渲染 Visio 文件"
  - "将 VSDX 渲染为 PDF"

---


{{< figure align=center src="images/View-Visio-Files-using-Java-1024x576.jpg" alt="使用 Java 渲染 Visio 文件">}}
 

Microsoft Visio 是一种流行的矢量图形工具，可帮助您可视化数据连接的业务流程。它可用于绘制各种图表，例如流程图、组织结构图、建筑平面图、平面图、数据流程图、工艺流程图、业务流程建模、泳道图、3D 地图等等。作为 Java 开发人员，您可以轻松地以编程方式呈现 HTML、PDF 和其他流行图像格式的 Visio 图表。在本文中，您将学习**如何使用 Java 以 HTML、PDF 和图像呈现 Visio 图表**。

本文讨论/涵盖了以下主题：

  * [用于查看 Visio 文件的 Java API][2]
  * [在 HTML 中呈现 Visio VSSX][3]
  * [以 PDF 格式呈现 Visio VSTX][4]
  * [以图像形式查看 Visio VSDX][5]

## 用于查看 Visio 文件的 Java API {#java-viewer-api}

我将使用 [GroupDocs.Viewer for Java API][6] 来呈现 Visio 文件。它提供了最灵活的文档查看解决方案，可以在任何地方呈现和显示广泛使用的文件格式。使用此 API，您可以在 Java 中创建功能强大的文档和图像渲染应用程序，而无需安装任何外部软件。它使您能够轻松快速地查看 PDF、HTML、XML、Microsoft Office Word、Excel 工作表、PowerPoint 演示文稿、Outlook 电子邮件、Visio 图表、项目、元文件、图像和各种其他文件格式，并且减少编程风险。

### 下载并配置

[获取库][7] 从下载中获取或在基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置以尝试以下示例。

```
<repository>
	<id>GroupDocsArtifactRepository</id>
	<name>GroupDocs Artifact Repository</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
```

```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-viewer</artifactId>
        <version>21.2</version> 
</dependency>
```

## 在 HTML 中呈现 Visio VSSX {#render-vssx-to-html}

您可以按照下面给出的简单步骤以 HTML 格式呈现 Visio VSSX 文件：

  1. 创建 **[Viewer][8]** 类的实例
  2. 提供输入文件路径
  3. 创建 [_**HtmlViewOptions**_][9] 类的实例
  4. 提供输出文件路径
  5. 调用 _**[View][10]**_ 方法并传递 HtmlViewOptions

以下代码示例展示了**如何使用 Java 以 HTML 格式呈现 VSSX 文件**。

```
try (Viewer viewer = new Viewer("C:\\Files\\sample.vssx")) {
    HtmlViewOptions options = HtmlViewOptions.forEmbeddedResources("C:\\Files\\Output\\output.html");
    viewer.view(options);
}
```

{{< figure align=center src="images/Render-VSSX-in-HTML-1024x457.jpg" alt="在 HTML 中渲染 VSSX" caption="在 HTML 中渲染 VSSX">}}
 

**_HtmlViewOptions_ **类提供了将文档呈现为 HTML 格式的选项。 [ForEmbeddedResources][12] 构造函数创建一个新的 _HtmlViewOptions_ 类实例，用于渲染成带有嵌入资源的 HTML。它为各种文件格式提供了某些选项，例如 Visio 文件的 VisioRenderingOptions、用于设置文本水印的水印选项、安全选项、用于呈现隐藏页面、注释和评论的呈现选项等。

您可以在文档中找到有关“[Document HTML Viewer][13]”的更多详细信息。

## 以 PDF 格式呈现 Visio VSTX {#render-vstx-to-pdf}

您可以按照下面给出的简单步骤以 PDF 格式呈现 Visio VSTX 文件：

  1. 创建 **[Viewer][8]** 类的实例
  2. 提供输入文件路径
  3. 创建 [_**PdfViewOptions**_][14] 类的实例
  4. 提供输出文件路径
  5. 调用 _**[View][10]**_ 方法并传递 PdfViewOptions

以下代码示例展示了**如何使用 Java 以 PDF 格式呈现 VSTX 文件**。

```
try (Viewer viewer = new Viewer("C:\\Files\\sample_organization.vstx")){
    PdfViewOptions options = new PdfViewOptions("C:\\Files\\Output\\output.pdf");
    viewer.view(options);
}
```

{{< figure align=center src="images/Render-VSTX-in-PDF-1024x457.jpg" alt="以 PDF 格式渲染 VSTX" caption="以 PDF 格式渲染 VSTX">}}
 

**_PdfViewOptions_ **类提供了将文档呈现为 PDF 格式的选项。它还允许为不同的文件格式设置单独的选项，包括文本水印、安全选项以及隐藏页面、注释和评论的呈现等。

您可以在文档中找到有关“[文档 PDF 查看器][16]”的更多详细信息。

## 将 Visio VSDX 渲染为图像 {#render-vsdx-to-image}

您可以按照下面给出的简单步骤以 JPG 或 PNG 格式呈现 Visio VSDX 文件：

  1. 创建 **[Viewer][8]** 类的实例
  2. 提供输入文件路径
  3. 创建 [_**PngViewOptions**_][17] 类的实例
  4. 提供输出文件路径
  5. 调用 _**[View][10]**_ 方法并传递 PngViewOptions

以下代码示例显示了**如何使用 Java 以 PNG 格式呈现 VSDX 文件**。

```
try (Viewer viewer = new Viewer("C:\\Files\\sample_block.vsdx")){
    PngViewOptions options = new PngViewOptions("C:\\Files\\Output\\output.png");
    viewer.view(options);
}
```

{{< figure align=center src="images/Render-VSDX-in-PNG-1024x457.jpg" alt="将 VSDX 渲染为 PNG" caption="将 VSDX 渲染为 PNG">}}
 

您还可以使用 Java 以 JPG 格式呈现 Visio 文件，如下所示：

```
try (Viewer viewer = new Viewer("C:\\Files\\sample_network.vsdx")) {
    JpgViewOptions jpgOptions = new JpgViewOptions("C:\\Files\\Output\\output.jpg");
    viewer.view(jpgOptions);
}
```

{{< figure align=center src="images/Render-VSDX-in-JPG-1024x457.jpg" alt="将 VSDX 渲染为 JPG" caption="将 VSDX 渲染为 JPG">}}
 

**_PngViewOptions_ **类提供了将文档呈现为 PNG 格式的选项。同样，**_JpgViewOptions_ **类提供了将文档呈现为 JPG 格式的选项。这两个类还提供了其他格式的设置选项以及文本水印、安全选项以及隐藏页面、注释和评论的呈现等。

您可以在文档中找到有关“[Document Image Viewer][20]”的更多详细信息。

## 获得免费许可证

您可以通过请求 [免费的临时许可证][21] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 Java 以 HTML、PDF、PNG 和 Jpg 格式呈现 Visio（.vsdx、.vstx、.vssx）文件**。您可以使用 [文档][22] 了解有关 GroupDocs.Viewer Java API 的更多信息。如有任何歧义，请随时在 [论坛][23] 上与我们联系。

## 也可以看看

  * [[查看 Outlook 数据文件 (OST/PST) 中所需文件夹中的邮件][24]][25]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/View-Visio-Files-using-Java.jpg
 [2]: #java-viewer-api
 [3]: #render-vssx-to-html
 [4]: #render-vstx-to-pdf
 [5]: #render-vsdx-to-image
 [6]: https://products.groupdocs.com/viewer/java
 [7]: https://downloads.groupdocs.com/viewer/java
 [8]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
 [9]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions
 [10]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
 [11]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/Render-VSSX-in-HTML.jpg
 [12]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions#forEmbeddedResources(java.lang.String)
 [13]: https://docs.groupdocs.com/viewer/java/document-viewer-html-viewer/
 [14]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/Render-VSTX-in-PDF.jpg
 [16]: https://docs.groupdocs.com/viewer/java/document-viewer-pdf-viewer/
 [17]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PngViewOptions
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/Render-VSDX-in-PNG.jpg
 [19]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/Render-VSDX-in-JPG.jpg
 [20]: https://docs.groupdocs.com/viewer/java/document-viewer-image-viewer/
 [21]: https://purchase.groupdocs.com/temporary-license
 [22]: https://docs.groupdocs.com/viewer/java/
 [23]: https://forum.groupdocs.com/c/viewer/
 [24]: https://blog.groupdocs.com/2019/08/24/view-messages-from-desired-folders-in-outlook-data-files-ostpst/
 [25]: https://blog.conholdate.com/2020/08/10/export-data-to-excel-in-csharp/








