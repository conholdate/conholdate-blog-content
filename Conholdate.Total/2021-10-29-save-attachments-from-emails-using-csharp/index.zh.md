---
title: "'使用 C# 从电子邮件中保存附件'"
author: Muzammil Khan
date: 2021-10-29T11:03:23+00:00
summary: "作为 C# 开发人员，您可以轻松地以编程方式从电子邮件中提取和保存附件。在本文中，您将学习**如何使用 C# 保存电子邮件中的附件**。"
url: /zh/2021/10/29/save-attachments-from-emails-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 CSharp 保存附件"
  - "在 CSharp 中保存电子邮件附件"
  - "使用 CSharp 查看附件"
  - "以 PDF 格式查看电子邮件附件"

---


{{< figure align=center src="images/save-attachments-from-emails-using-csharp.jpg" alt="使用 C# 保存电子邮件中的附件">}}
 

作为 C# 开发人员，您可以轻松地以编程方式从电子邮件中提取和保存附件。在本文中，您将学习**如何使用 C# 保存电子邮件中的附件**。

本文讨论/涵盖了以下主题：

  * [用于保存电子邮件附件的 C# API][2]
  * [使用 C# 从电子邮件中提取和保存附件][3]
  * [使用 C# 将电子邮件中的附件另存为 PDF][4]

## 用于保存电子邮件附件的 C# API {#CSharp-API-to-Save-Email-Attachments}

为了保存 [MSG][5] 文件中的附件，我们将使用 [GroupDocs.Viewer for .NET API][6]。它是一个强大的文档查看器 API，无需安装任何外部软件即可呈现和显示广泛使用的文件格式。它还可以让您快速查看[Word][8]、[Excel][9]、[PowerPoint][10]、[Outlook emails][11]、[Project][的流行[支持的文件格式][7] 12]、[PDF][13]、[HTML][14] 和 [XML][15]。

您可以 [下载][16] API 的 DLL 或使用 [NuGet][17] 安装它。

```
Install-Package GroupDocs.Viewer
```

## 使用 C# 从电子邮件中提取和保存附件 {#Extract-and-Save-Attachments-from-Emails-using-CSharp}

您可以按照以下步骤以编程方式从电子邮件 MSG 文件中提取和保存附件：

  * 首先，使用 [Viewer][18] 类加载 MSG 文件。
  * 然后，调用[Viewer.GetAttachments()][19]方法获取加载的MSG文件的所有附件。以附件集合的形式获取结果。
  * 对于集合中的每个附件，通过调用 [Viewer.SaveAttachment()][20] 方法保存附件。传递附件对象和文件路径以保存它。

以下代码示例显示**如何使用 C# 提取和保存电子邮件 MSG 文件中包含的附件*。

```
string outputPath = @"C:\Files\Viewer\";

// 初始化 API 并加载 MSG 文件
Viewer viewer = new Viewer(@"C:\Files\Viewer\with_attachments.msg");

// 获取附件
IList<Attachment> attachments = viewer.GetAttachments();

foreach (Attachment attachment in attachments)
{
    // Save attachment
    string filePath = Path.Combine(outputPath, attachment.FileName);
    viewer.SaveAttachment(attachment, File.OpenWrite(filePath));
}
```

{{< figure align=center src="images/Extract-and-Save-Attachments-from-Emails-using-CSharp-1024x511.jpg" alt="使用 C# 从电子邮件中提取和保存附件" caption="使用 C# 从电子邮件中提取和保存附件。">}}
 

## 使用 C# 将电子邮件中的附件另存为 PDF {#Save-Attachments-as-PDF-from-Emails-using-CSharp}

您可以按照以下步骤以编程方式将电子邮件附件保存为 PDF：

  * 使用附加的文件名和文件路径创建 [Attachment][22] 类的实例。
  * 初始化 MemoryStream 类的实例。
  * 使用 [Viewer][18] 类加载 MSG 文件。
  * 然后，调用 [Viewer.SaveAttachment()][20] 方法并将 Attachment 和 MemoryStream 对象作为输入参数传递。它将提取并保存在内存流中的指定附件。
  * 现在，使用 [Viewer][18] 类加载 MemoryStream 对象。
  * 然后，使用输出 PDF 文件路径创建 [PdfViewOptions][23] 类的实例。
  * 最后，调用 [Viewer.View()][24] 方法将附件保存为 PDF 并查看。

以下代码示例展示了**如何使用 C#** 将电子邮件 MSG 文件中的附件保存为 PDF 格式并进行查看。

```
// 初始化附件
Attachment attachment = new Attachment("attachment-word.doc", "attachment-word.doc");
MemoryStream attachmentStream = new MemoryStream();

// 初始化 API 并加载 MSG 文件
using (Viewer viewer = new Viewer(@"C:\Files\Viewer\with_attachments.msg"))
{
    // Save attachment in stream
    viewer.SaveAttachment(attachment, attachmentStream);
}

// 初始化 API 并加载附件流
using (Viewer viewer = new Viewer(attachmentStream))
{
    // Define PDF view options
    PdfViewOptions viewOptions = new PdfViewOptions("C:\\Files\\Viewer\\output.pdf");

    // View as PDF
    viewer.View(viewOptions);
}
```

{{< figure align=center src="images/Save-Attachments-as-PDF-from-Emails-using-CSharp-1024x561.jpg" alt="" caption="Save attachments as PDF from emails using C#.">}}
 

## 获得免费许可证

您可以通过请求 [免费的临时许可证][26] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用** C#** **提取和保存电子邮件 MSG 文件中包含的附件。此外，您还了解了**如何以编程方式将特定附件另存为 PDF**。此外，您可以使用 [documentation][27] 了解有关 .NET API 的 GroupDocs.Viewer 的更多信息。如有任何歧义，请随时在 [论坛][28] 上与我们联系。

## 也可以看看

  * [使用 C# 渲染 ZIP 档案][29]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/save-attachments-from-emails-using-csharp.jpg
 [2]: #CSharp-API-to-Save-Email-Attachments
 [3]: #Extract-and-Save-Attachments-from-Emails-using-CSharp
 [4]: #Save-Attachments-as-PDF-from-Emails-using-CSharp
 [5]: https://docs.fileformat.com/email/msg/
 [6]: https://products.groupdocs.com/viewer/net
 [7]: https://docs.groupdocs.com/viewer/net/supported-document-formats/
 [8]: https://docs.fileformat.com/word-processing/
 [9]: https://docs.fileformat.com/spreadsheet/
 [10]: https://docs.fileformat.com/presentation/
 [11]: https://docs.fileformat.com/email/
 [12]: https://docs.fileformat.com/project-management/
 [13]: https://docs.fileformat.com/pdf/
 [14]: https://docs.fileformat.com/web/html/
 [15]: https://docs.fileformat.com/web/xml/
 [16]: https://downloads.groupdocs.com/viewer/net
 [17]: https://www.nuget.org/packages/GroupDocs.Viewer
 [18]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/Viewer
 [19]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/getattachments
 [20]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/saveattachment
 [21]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Extract-and-Save-Attachments-from-Emails-using-CSharp.jpg
 [22]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.results/attachment
 [23]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
 [24]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
 [25]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Save-Attachments-as-PDF-from-Emails-using-CSharp.jpg
 [26]: https://purchase.groupdocs.com/temporary-license
 [27]: https://docs.groupdocs.com/viewer/net/
 [28]: https://forum.groupdocs.com/c/viewer/
 [29]: https://blog.conholdate.com/2021/07/06/render-zip-archives-using-csharp/








