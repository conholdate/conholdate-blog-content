---
title: "'使用 C# 渲染 ZIP 档案'"
author: Muzammil Khan
date: 2021-07-06T10:34:08+00:00
summary: "您可以在 .NET 应用程序中以编程方式轻松呈现您的 ZIP 档案。在本文中，您将学习**如何使用 C# 渲染 ZIP 档案**。"
url: /zh/2021/07/06/render-zip-archives-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "CSharp API 查看 ZIP 文件"
  - "GroupDocs.Viewer .NET"
  - "以 HTML 格式呈现 ZIP 档案"
  - "以 PDF 格式呈现 ZIP 档案"
  - "将 ZIP 档案渲染为 JPG"

---

{{< figure align=center src="images/render-zip-archives-using-csharp.jpg" alt="使用 C# 渲染 ZIP 档案">}}
 
ZIP 文件包含一个或多个压缩文件或文件夹以充当单个文件。这些被广泛用于节省存储空间并提高计算机的性能。您可以有效地将 ZIP 存档中的文件和文件夹从一个位置传输到另一个位置。作为 C# 开发人员，您可以轻松呈现 ZIP 存档并以编程方式查看其内容。本文将重点介绍**如何使用 C# 呈现 ZIP 档案**。

本文讨论/涵盖了以下主题：

  * [C# API 查看 ZIP 文件][2]
  * [以 HTML 格式呈现 ZIP 档案][3]
  * [以 HTML 格式呈现 ZIP 档案中的特定文件夹][4]
  * [以 PDF 格式查看 ZIP 档案的内容][5]
  * [将 ZIP 档案渲染为 JPG][6]
  * [从 ZIP 档案中获取文件夹列表][7]
  * [渲染和重命名 ZIP 文件][8]

## C# API 查看 ZIP 文件 {#csharp-zip-viewer-api}

对于 ZIP 文件的呈现，我将使用 [GroupDocs.Viewer for .NET API][9]。它是一个强大的文档查看器 API，支持 170 多种文件和文档类型。 API 提供最灵活的文档查看解决方案，无需安装任何外部软件即可在任何地方呈现和显示广泛使用的文件格式。它还使您能够轻松快速地查看 PDF、HTML、XML、Microsoft Office Word、Excel 工作表、PowerPoint 演示文稿、Outlook 电子邮件、Visio 图表、项目、元文件、图像和各种其他文件格式，并且减少编程风险。

您可以[下载][10] API 的 DLL 或使用 [NuGet][11] 安装它。

```
Install-Package GroupDocs.Viewer
```

## 以 HTML 格式呈现 ZIP 档案 {#render-zip-to-html}

您可以按照下面给出的简单步骤以 HTML 格式呈现 ZIP 文件：

  1. 创建 _**[Viewer][12]**_ 类的实例
  2. 提供输入文件路径
  3. 创建 [_**HtmlViewOptions**_][13] 类的实例
  4. 提供输出文件路径
  5. 调用 _**[View()][14]**_ 方法并传递 HtmlViewOptions

以下代码示例展示了**如何使用 C# 以 HTML 格式呈现 ZIP 文件**。

```
// 初始化查看器
Viewer viewer = new Viewer("C:\\Files\\sample.zip");

// 定义 HTML 视图选项
HtmlViewOptions viewOptions = HtmlViewOptions.ForEmbeddedResources("C:\\Files\\output.html");
viewOptions.RenderToSinglePage = true;

// 创建视图
viewer.View(viewOptions);
```

{{< figure align=center src="images/render-zip-to-html-1024x499.jpg" alt="以 HTML 格式呈现 ZIP 档案" caption="以 HTML 格式呈现 ZIP 档案">}}
 
**[Viewer][12]** 类是提供控制文档呈现过程的功能的主类。此类的 [View()][14] 方法创建所有文档页面的视图。

**[HtmlViewOptions ][13]** 类提供了将文档呈现为 HTML 格式的选项。 [ForEmbeddedResources][16] 构造方法创建一个新的 _HtmlViewOptions_ 类实例，用于渲染成带有嵌入资源的 HTML。如您所见，我在代码示例中提供了输出文件路径。

您可以在文档中找到有关“[Document HTML Viewer][17]”的更多详细信息。

## 以 HTML 格式呈现 ZIP 档案中的特定文件夹 {#Render-Specific-Folder-from-ZIP-Archives}

您可以按照下面给出的简单步骤以 HTML 格式呈现 ZIP 文件中可用的特定文件夹：

  1. 创建 _**[Viewer][12]**_ 类的实例
  2. 提供输入文件路径
  3. 创建 [_**HtmlViewOptions**_][13] 类的实例
  4. 提供输出文件路径
  5. 设置要渲染的文件夹名称
  6. 调用 _**[View()][14]**_ 方法并传递 HtmlViewOptions

以下代码示例展示了**如何使用 C# 以 HTML 格式从 ZIP 文件呈现特定文件夹**。

```
// 初始化查看器
Viewer viewer = new Viewer("C:\\Files\\sample.zip");

// 定义 HTML 视图选项
HtmlViewOptions viewOptions = HtmlViewOptions.ForEmbeddedResources("C:\\Files\\output.html");
// 设置文件夹名称
viewOptions.ArchiveOptions.Folder = "ThirdFolderWithItems";

// 创建视图
viewer.View(viewOptions);
```

{{< figure align=center src="images/Render-Specific-Folder-from-ZIP-Archives-1024x457.jpg" alt="以 HTML 格式呈现 ZIP 档案中的特定文件夹" caption="以 HTML 格式呈现 ZIP 档案中的特定文件夹">}}
 
**[ArchiveOptions][19]** 类为归档文件的呈现提供了选项。它使您能够通过提供存档中可用文件夹的名称来呈现 ZIP 存档中的特定文件夹。

## 以 PDF 格式查看 ZIP 档案的内容 {#render-zip-to-pdf}

您可以按照以下简单步骤将 ZIP 文件呈现为 PDF 文档：

  1. 创建 _**[Viewer][12]**_ 类的实例
  2. 提供输入文件路径
  3. 创建 [_**PdfViewOptions**_][20] 类的实例
  4. 提供输出文件路径
  5. 调用 _**[View()][14]**_ 方法并传递 PdfViewOptions

以下代码示例展示了**如何使用 C#** 以 PDF 格式呈现 ZIP 文件。

```
// 初始化查看器
Viewer viewer = new Viewer("C:\\Files\\sample.zip");

// 定义 PDF 视图选项
PdfViewOptions options = new PdfViewOptions("C:\\Files\\output.pdf");

// 创建视图
viewer.View(viewOptions);
```

{{< figure align=center src="images/render-zip-to-pdf-1024x539.jpg" alt="以 PDF 格式查看 ZIP 档案的内容" caption="以 PDF 格式查看 ZIP 档案的内容">}}
 
**[PdfViewOptions][20]** 类提供了将文档呈现为 PDF 格式的选项。您可以在文档中找到有关“[文档 PDF 查看器][22]”的更多详细信息。

## 将 ZIP 档案渲染为 JPG {#render-zip-to-jpg}

您可以按照以下简单步骤将 ZIP 文件渲染为 JPG 图像：

  1. 创建 _**[Viewer][12]**_ 类的实例
  2. 提供输入文件路径
  3. 创建 [_**JpgViewOptions**_][23] 类的实例
  4. 提供输出文件路径
  5. 调用 _**[View()][14]**_ 方法并传递 JpgViewOptions

以下代码示例显示了**如何使用 C# 以 JPG 图像呈现 ZIP 文件**。

```
// 初始化查看器
Viewer viewer = new Viewer("C:\\Files\\sample.zip");

// 定义 JPG 视图选项
JpgViewOptions options = new JpgViewOptions("C:\\Files\\output_page_{0}.jpg");

// 创建视图
viewer.View(viewOptions);
```

{{< figure align=center src="images/render-zip-to-jpg-1024x537.jpg" alt="将 ZIP 档案渲染为 JPG" caption="将 ZIP 档案渲染为 JPG">}}
 
您可以将文档呈现为 JPG 或 PNG 图像格式。 **[JpgViewOptions][23]** 类提供了将文档呈现为 JPG 格式的选项。同样，**[PngViewOptions][25]** 类提供了将文档呈现为 PNG 格式的选项。

您可以在文档中找到有关“[Document Image Viewer][26]”的更多详细信息。

## 从 ZIP 档案中获取文件夹列表 {#Get-a-List-of-Folders-from-ZIP-archives}

您可以按照以下步骤以编程方式从 ZIP 文件中获取所有文件夹和子文件夹的列表：

  1. 创建 _**[Viewer][12]**_ 类的实例
  2. 提供输入文件路径
  3. 创建 **_[ViewInfoOptions][27]_**
  4. 通过调用 [_**GetViewInfo()**_][29] 方法创建 **_[ViewInfo][28]_** 实例
  5. 获取 **_[ArchiveViewInfo][30]_**
  6. 显示结果

以下代码示例展示了**如何使用 C#** 从 ZIP 文件中获取文件夹列表。

```
// 初始化查看器
Viewer viewer = new Viewer("C:\\Files\\sample.zip");

// 创建视图信息选项
ViewInfoOptions viewInfoOptions = ViewInfoOptions.ForHtmlView();
ViewInfo viewInfo = viewer.GetViewInfo(viewInfoOptions);

Console.WriteLine("File type: " + viewInfo.FileType);
Console.WriteLine("Pages count: " + viewInfo.Pages.Count);
Console.WriteLine("Folders: ");
Console.WriteLine(" - /");

string rootFolder = string.Empty;
viewInfoOptions.ArchiveOptions.Folder = rootFolder;

// 获取查看信息
ArchiveViewInfo viewFolderInfo = viewer.GetViewInfo(viewInfoOptions) as ArchiveViewInfo;

foreach (string subFolder in viewFolderInfo.Folders)
{
    Console.WriteLine($" - {subFolder}");
    PrintFolders(viewer, subFolder);
}
```

{{< figure align=center src="images/Get-a-List-of-Folders-from-ZIP-archives-1024x598.jpg" alt="从 ZIP 档案中获取文件夹列表" caption="从 ZIP 档案中获取文件夹列表">}}
 
**[ViewInfoOptions][27]** 类提供用于检索有关视图的信息的选项。它提供了各种方法来获取特定格式的视图信息。我使用 [ForHtmlView()][32] 方法初始化 ViewInfoOptions 类的新实例，以在呈现为 HTML 时检索有关视图的信息。

**[ViewInfo][28]** 类提供通用文档的视图信息。 Viewer 类的 [GetViewInfo()][29] 方法返回有关视图的信息和特定于文档的信息。

**[ArchiveViewInfo][30]** 类提供存档文件的视图信息。

## 渲染和重命名 ZIP 文件 {#Render-and-Rename-ZIP-Files}

您可以按照以下步骤在以编程方式呈现时重命名 ZIP 文件：

  1. 创建 _**[Viewer][12]**_ 类的实例
  2. 提供输入文件路径
  3. 创建 [_**PdfViewOptions**_][20] 类的实例
  4. 提供输出文件路径
  5. 设置要显示的新文件名
  6. 调用 _**[View()][14]**_ 方法并传递 PdfViewOptions

以下代码示例显示了**如何在使用 C# 渲染时重命名 ZIP 文件**。

```
// 初始化查看器
Viewer viewer = new Viewer("C:\\Files\\sample.zip");

// 定义 PDF 视图选项
PdfViewOptions viewOptions = new PdfViewOptions("C:\\Files\\output.pdf");
// 设置新文件名
viewOptions.ArchiveOptions.FileName = new FileName("MyFiles");

viewer.View(viewOptions);
```

{{< figure align=center src="images/Render-and-Rename-ZIP-Files-1024x538.jpg" alt="渲染和重命名 ZIP 文件" caption="渲染和重命名 ZIP 文件">}}
 
**[ArchiveOptions][19]** 类提供 _FileName_ 属性，用于在标题中显示文件名。您可以设置一个新的显示名称，如上面的代码示例所示。默认情况下，它显示源文件的名称。

## 获得免费许可证

您可以通过申请 [免费的临时许可证][34] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C# 渲染 ZIP 档案**。您还学习了**如何在 HTML、PDF 和 JPG 图像中转换和查看 ZIP 文件的内容**。此外，您还学习了**如何在 C# 中以编程方式从 ZIP 存档中获取文件夹和子文件夹的列表**。您可以使用 [documentation][35] 了解有关 .NET API 的 GroupDocs.Viewer 的更多信息。如有任何歧义，请随时在 [论坛][36] 上与我们联系。

## 也可以看看

  * [使用 .NET API 在 C# 中查看 CAD 文件][37]
  * [使用 C# 播放和暂停动画 GIF 和 APNG 图像][38]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/07/render-zip-archives-using-csharp.jpg
 [2]: #csharp-zip-viewer-api
 [3]: #render-zip-to-html
 [4]: #Render-Specific-Folder-from-ZIP-Archives
 [5]: #render-zip-to-pdf
 [6]: #render-zip-to-jpg
 [7]: #Get-a-List-of-Folders-from-ZIP-archives
 [8]: #Render-and-Rename-ZIP-Files
 [9]: https://products.groupdocs.com/viewer/net
 [10]: https://downloads.groupdocs.com/viewer/net
 [11]: https://www.nuget.org/packages/GroupDocs.Viewer
 [12]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
 [13]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
 [14]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/07/render-zip-to-html.jpg
 [16]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options.htmlviewoptions/forembeddedresources/methods/4
 [17]: https://docs.groupdocs.com/viewer/net/document-viewer-html-viewer/
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/07/Render-Specific-Folder-from-ZIP-Archives.jpg
 [19]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/archiveoptions
 [20]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
 [21]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/07/render-zip-to-pdf.jpg
 [22]: https://docs.groupdocs.com/viewer/net/document-viewer-pdf-viewer/
 [23]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/jpgviewoptions
 [24]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/07/render-zip-to-jpg.jpg
 [25]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pngviewoptions
 [26]: https://docs.groupdocs.com/viewer/net/document-viewer-image-viewer/
 [27]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/viewinfooptions
 [28]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.results/viewinfo
 [29]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/getviewinfo
 [30]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.results/archiveviewinfo
 [31]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/07/Get-a-List-of-Folders-from-ZIP-archives.jpg
 [32]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/viewinfooptions/methods/forhtmlview
 [33]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/07/Render-and-Rename-ZIP-Files.jpg
 [34]: https://purchase.groupdocs.com/temporary-license
 [35]: https://docs.groupdocs.com/viewer/net/
 [36]: https://forum.groupdocs.com/c/viewer/
 [37]: https://blog.groupdocs.com/2021/04/27/view-cad-documents-using-charp/
 [38]: https://blog.groupdocs.com/2021/02/28/play-pause-animated-gif-and-apng-in-web-pages-using-csharp/

