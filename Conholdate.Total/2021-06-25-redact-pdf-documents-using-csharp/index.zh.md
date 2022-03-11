---
title: "'使用 C# 编辑 PDF 文档'"
author: Muzammil Khan
date: 2021-06-25T05:04:20+00:00
summary: "您可以在 .NET 应用程序中使用 C# 以编程方式轻松编辑 PDF 文档。本文将重点介绍**如何使用 C# 编辑 PDF 文档**。"
url: /zh/2021/06/25/redact-pdf-documents-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 CSharp 在 PDF 中进行多重编辑"
  - "编辑 PDF 中的图像"
  - "编辑 PDF 中的元数据"
  - "使用 CSharp 编辑 PDF"
  - "编辑 PDF 中的文本"

---


{{< figure align=center src="images/Redact-PDF-Documents-using-CSharp.jpg" alt="使用 C# 编辑 PDF 文档">}}
 

您可以通过编程方式编辑 PDF 文档，而无需安装任何外部应用程序。作为 C# 开发人员，您可以轻松地在 .NET 应用程序中编辑 PDF 文档。本文将重点介绍**如何使用 C# 编辑 PDF 文档**。

本文讨论/涵盖了以下主题：

  * [用于 PDF 编辑的 C# API][2]
  * [使用 C# 编辑 PDF 中的文本][3]
  * [使用 C# 编辑 PDF 中的元数据][4]
  * [使用 C# 编辑 PDF 中的图像][5]
  * [使用 C# 在 PDF 中应用多个密文][6]

## 用于 PDF 编辑的 C# API {#api-for-pdf-redaction}

对于 [PDF][7] 文档中的编辑，我将使用 [GroupDocs.Redaction for .NET][8] API。它允许您编辑 PDF、Word、Excel、PowerPoint 和图像文件。它还使您能够从 30 多种支持的格式中删除分类信息。您可以应用各种类型的密文，例如文本密文、元数据密文、注释密文和表格文档密文。

您可以 [下载][9] API 的 DLL 或使用 [NuGet][10] 安装它。

```
Install-Package GroupDocs.Redaction
```

## 使用 C# 编辑 PDF 中的文本 {#Redact-Text-in-PDF}

您可以按照以下提到的简单步骤轻松地在 PDF 文档中应用文本编辑：

  * 使用输入文件路径创建 _[**Redactor**][11]_ 类的实例
  * 使用 _SearchPhrase_ 和 _**[ReplacementOptions][13]**_ 创建 **_[ExactPhraseRedaction][12]_** 类实例
  * 调用 _[Redactor.Apply()][14]_ 方法
  * 在 _**[RedactorChangeLog][15]**_ 类对象中获取结果
  * 调用 [Redactor.Save()][16] 方法

以下代码示例展示了**如何使用 C#** 编辑 PDF 文档中的文本。

```
// 创建编辑器
Redactor redactor = new Redactor("C:\\Files\\sample.pdf");

// 创建精确的短语编辑
ExactPhraseRedaction redaction = new ExactPhraseRedaction("John Doe", true, new ReplacementOptions("[personal]"));

// 应用编辑
RedactorChangeLog result = redactor.Apply(redaction);
if (result.Status != RedactionStatus.Failed)
{
    redactor.Save();
};
```

{{< figure align=center src="images/Redact-Text-in-PDF-using-csharp-1024x457.jpg" alt="使用 C# 编辑 PDF 中的文本" caption="使用 C# 编辑 PDF 中的文本">}}
 

[Redactor][11] 是主要类，提供各种方法来执行文档编辑过程。它还使您能够打开、编辑和保存文档。此类的 _Apply()_ 方法将定义的编辑应用到文档。此外，该类的_Save()_ 方法将文档保存到文件中。

[ExactPhraseRedaction][12] 提供了执行文本编辑以替换文档中的确切短语的方法。它还允许通过将 _IsCaseSensitive_ 设置为 true 来搜索区分大小写的数据。

[ReplacementOptions][13] 表示匹配文本替换的选项。

[RedactorChangeLog][15] 类表示编辑列表的结果，传递给 [Redactor][11] 类的 Apply() 方法。

## 使用 C# 编辑 PDF 中的元数据 {#Redact-Metadata-in-PDF}

您可以按照以下提到的简单步骤在 PDF 文档中应用元数据编辑：

  * 使用输入文件路径创建 _[**Redactor**][11]_ 类的实例
  * 使用 **_[MetadataFilter][19]_** 创建 **_[EraseMetadataRedaction][18]_** 类实例以包含
  * 调用 _[Redactor.Apply()][14]_ 方法
  * 调用 [Redactor.Save()][16] 方法

以下代码示例展示了**如何使用 C#** 编辑 PDF 文档中的元数据。

```
// 创建编辑器
Redactor redactor = new Redactor("C:\\Files\\sample.pdf");

// 删除作者、经理和公司
EraseMetadataRedaction redaction = new EraseMetadataRedaction(MetadataFilters.Author | MetadataFilters.Manager | MetadataFilters.Company);

// 应用编辑
redactor.Apply(redaction);
redactor.Save();
```

{{< figure align=center src="images/Redact-Metadata-in-PDF-using-csharp-1024x835.jpg" alt="使用 C# 编辑 PDF 中的元数据" caption="使用 C# 编辑 PDF 中的元数据">}}
 

[EraseMetadataRedaction][21] 类提供了擦除所有元数据的方法。它还可以从文档中删除与特定 MetadataFilters 匹配的元数据。

[MetadataFilters][19] 是最常见的文档元数据类型的列表，例如作者、评论、公司。

## 使用 C# 编辑 PDF 中的图像 {#Redact-Images-in-PDF}

您可以按照以下提到的简单步骤在 PDF 文档中应用图像编辑：

  * 使用输入文件路径创建 _[**Redactor**][11]_ 类的实例
  * 定义绘图点和大小
  * 使用绘图点和 **_[RegionReplacementOptions][23]_** 创建 **_[ImageAreaRedaction][22]_** 类实例
  * 调用 _[Redactor.Apply()][14]_ 方法
  * 调用 [Redactor.Save()][16] 方法

以下代码示例展示了**如何使用 C#** 编辑 PDF 文档中的图像。

```
// 创建编辑器
Redactor redactor = new Redactor("C:\\Files\\sample_with_images.pdf");

// 定义大小和点
System.Drawing.Point samplePoint = new System.Drawing.Point(0, 0);
System.Drawing.Size sampleSize = new System.Drawing.Size(300, 240);

// 定义图像区域编辑
ImageAreaRedaction redaction = new ImageAreaRedaction(samplePoint,
             new RegionReplacementOptions(System.Drawing.Color.Blue, sampleSize));

// 应用编辑
RedactorChangeLog result = redactor.Apply(redaction);

if (result.Status != RedactionStatus.Failed)
{
    redactor.Save();
};
```

{{< figure align=center src="images/Redact-Images-in-PDF-using-csharp-1024x457.jpg" alt="使用 C# 编辑 PDF 中的图像" caption="使用 C# 编辑 PDF 中的图像">}}
 

[ImageAreaRedaction][22] 类允许在图像文档的给定区域放置一个彩色矩形。

[RegionReplacementOption][23] 类表示要替换为图像的区域的颜色和面积参数。

## 使用 C# 在 PDF 中应用多个密文 {#Apply-Multiple-Redactions-in-PDF}

您可以按照以下提到的简单步骤在 PDF 文档中应用多个编辑：

  * 使用输入文件路径创建 _[**Redactor**][11]_ 类的实例
  * 创建 **_[ExactPhraseRedaction][12]_**、**_[RegexRedaction][25]_** 和 **_[EraseMetadataRedaction][21]_**
  * 将创建的密文添加到密文列表
  * 调用 _[Redactor.Apply()][26]_ 方法
  * 调用 [Redactor.Save()][16] 方法, show errors if failed

以下代码示例显示了**如何使用 C#** 在 PDF 文档中应用多个修订。

```
// 创建编辑器
Redactor redactor = new Redactor("C:\\Files\\sample.pdf");

// 定义多个编辑
var redactionList = new Redaction[]
{
    new ExactPhraseRedaction("John Doe", new ReplacementOptions("[Client]")),
    new RegexRedaction("Redaction", new ReplacementOptions("[Product]")),
    new RegexRedaction("\\d{2}\\s*\\d{2}[^\\d]*\\d{6}", new ReplacementOptions(System.Drawing.Color.Blue)),
    new EraseMetadataRedaction(MetadataFilters.All)
};

// 应用编辑
RedactorChangeLog result = redactor.Apply(redactionList);

// 如果应用则保存否则显示错误
if (result.Status == RedactionStatus.Applied)
{
    redactor.Save();
}
else if (result.Status == RedactionStatus.Failed)
{
    for (int i = 0; i < result.RedactionLog.Count; i++)
    {
        RedactorLogEntry logEntry = result.RedactionLog[i];
        if (logEntry.Result.Status != RedactionStatus.Applied)
        {
            Console.WriteLine("{0} status is {1}, details: {2}",
                logEntry.Redaction.GetType().Name,
                logEntry.Result.Status,
                logEntry.Result.ErrorMessage);
        }
    }
};
```

{{< figure align=center src="images/Apply-Multiple-Redactions-in-PDF-using-csharp-1-1024x536.jpg" alt="使用 C# 在 PDF 中应用多个密文" caption="使用 C# 在 PDF 中应用多个密文">}}
 

[RegexRedaction][25] 类允许执行文本编辑。您可以通过使用正则表达式匹配文本来搜索和替换文档中的任何文本。

## 获得免费许可证

您可以通过申请 [免费的临时许可证][28] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C# 编辑 PDF 文档**。您还学习了如何编辑 PDF 文档中的文本、元数据和图像。此外，您还学习了如何使用 C# 在 PDF 中应用多个编辑。您可以使用 [文档][29] 了解有关 .NET API 的 GroupDocs.Redaction 的更多信息。如有任何歧义，请随时在 [论坛][30] 上与我们联系。

## 也可以看看

  * [使用 C# 以编程方式查找和替换文档中的文本][31]
  * [如何使用 C# 或 Java 编辑文字处理文档][32]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/06/Redact-PDF-Documents-using-CSharp.jpg
 [2]: #api-for-pdf-redaction
 [3]: #Redact-Text-in-PDF
 [4]: #Redact-Metadata-in-PDF
 [5]: #Redact-Images-in-PDF
 [6]: #Apply-Multiple-Redactions-in-PDF
 [7]: https://docs.fileformat.com/pdf/
 [8]: https://products.groupdocs.com/redaction/net
 [9]: https://downloads.groupdocs.com/redaction/net
 [10]: https://www.nuget.org/packages/GroupDocs.Redaction
 [11]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor
 [12]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/exactphraseredaction
 [13]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/replacementoptions
 [14]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply
 [15]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactorchangelog
 [16]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/06/Redact-Text-in-PDF-using-csharp.jpg
 [18]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/metadatasearchredaction
 [19]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/metadatafilters
 [20]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/06/Redact-Metadata-in-PDF-using-csharp.jpg
 [21]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/erasemetadataredaction
 [22]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/imagearearedaction
 [23]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/regionreplacementoptions
 [24]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/06/Redact-Images-in-PDF-using-csharp.jpg
 [25]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/regexredaction
 [26]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactor/apply/methods/1
 [27]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/06/Apply-Multiple-Redactions-in-PDF-using-csharp-1.jpg
 [28]: https://purchase.groupdocs.com/temporary-license
 [29]: https://docs.groupdocs.com/redaction/net/
 [30]: https://forum.groupdocs.com/c/redaction/
 [31]: https://blog.groupdocs.com/2019/09/20/find-and-replace-text-in-word-excel-powerpoint-pdf-documents-net-api/
 [32]: https://blog.groupdocs.com/2019/12/05/how-to-redact-in-word/








