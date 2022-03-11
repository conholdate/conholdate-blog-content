---
title: "'使用 C# 从 DOC 或 DOCX 中提取文本'"
author: Muzammil Khan
date: 2021-05-21T17:01:28+00:00
summary: "以编程方式轻松地从 Word 或 PDF 文档中提取文本。在本文中，您将学习**如何使用 C#从 DOC 或 DOCX 文档中提取文本**。"
url: /zh/2021/05/21/extract-text-from-doc-or-docx-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 CSharp 提取格式化文本"
  - "提取文本"
  - "提取文本 from DOCX"
  - "使用 CSharp 从页面中提取文本"
  - "提取文本 from Word"

---

{{< figure align=center src="images/Extract-Text-from-DOCX.jpg" alt="从 DOCX 中提取文本">}}
 
大多数数据在文档、图像和网络上都表示为可视文本，因此提取文本数据有时是最需要的事情。您可能需要从 Word 或 PDF 文档中提取文本或图像。作为 C# 开发人员，您可以轻松地以编程方式从文档中提取文本。在本文中，您将学习**如何使用 C#从 DOC 或 DOCX 文档中提取文本**。

本文讨论/涵盖了以下主题：

  * [用于文本提取的 C# API][2]
  * [使用 C# 从 DOCX 中提取文本][3]
  * [使用 C# 从 DOCX 获取格式化文本][4]
  * [使用 C# 从页面中提取格式化文本][5]

## 用于文本提取的 C# API {#api-for-extracting-text}

我将使用 [GroupDocs.Parser for .NET][6] API 从 [DOCX][7] 文档中提取文本。它允许从 Word、PDF、Excel 和 Powerpoint 等支持的文件格式文档中提取文本、元数据和图像。它还支持从支持格式的文件中提取原始、格式化和结构化文本以及元数据。

您可以 [下载][8] API 的 DLL 或使用 [NuGet][9] 安装它。

```
Install-Package GroupDocs.Parser
```

## 使用 C# 从 DOCX 中提取文本 {#Extract-Text-from-DOCX-using-CSharp}

您可以按照以下提到的简单步骤轻松解析任何文档并提取文本：

  * 创建 _[Parser][10]_ 类的实例
  * 指定文件路径
  * 调用Parser类的_[GetText][11]_方法提取文本
  * 在 _TextReader_ 类对象中获取结果
  * 通过调用 TextReader 类的 _ReadToEnd_ 方法显示结果

以下代码示例展示了如何使用 C# 从 DOCX 文件中提取文本。

```
// 创建 Parser 类的实例
Parser parser = new Parser(@"C:\Files\sample.docx");

// 将文本提取到阅读器中
using (TextReader reader = parser.GetText())
{
    // Print a text from the document
    // If text extraction isn't supported, a reader is null
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

{{< figure align=center src="images/Extract-Text-from-DOCX-using-CSharp-1024x528.jpg" alt="使用 C# 从 DOCX 中提取文本" caption="使用 C# 从 DOCX 中提取文本">}}
 

[Parser][10] 类是提供解析功能以及提取文本和图像的主要类。我在这个类的 [constructor][13] 中指定了输入文件路径。

Parser 类的 [GetText()][14] 方法从指定的文档中提取文本。

## 使用 C# 从 DOCX 获取格式化文本 {#Get-Formatted-Text-from-DOCX-using-CSharp}

您可以按照以下提到的简单步骤轻松解析 Word 文档并提取文本，而不会丢失样式格式：

  * 创建 _[Parser][10]_ 类的实例
  * 指定文件路径
  * 定义_[FormattedTextOptions][15]_
  * 将 _[FormattedTextMode][16]_ 设置为 HTML
  * 调用Parser类的[GetFormattedText][17]方法提取文本
  * 在 TextReader 类对象中获取结果
  * 通过调用 TextReader 类的 ReadToEnd 方法显示结果

以下代码示例展示了如何使用 C# 从 DOCX 文件中提取格式化文本。

```
// 创建 Parser 类的实例
Parser parser = new Parser(@"C:\Files\sample.docx");

// 将格式化的文本提取到阅读器中
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
{
    // Print a formatted text from the document
    // If formatted text extraction isn't supported, a reader is null
    Console.WriteLine(reader == null ? "Formatted text extraction isn't suppported" : reader.ReadToEnd());
}
```

{{< figure align=center src="images/image-1-1024x335.png" alt="使用 C# 从 DOCX 中提取格式化文本" caption="使用 C# 从 DOCX 中提取格式化文本">}}
 

[FormattedTextOptions][15] 类提供了用于格式化文本提取的选项，例如提取_[Mode][16]_。我将提取模式设置为将文档文本提取为 HTML 的<a rel="noreferrer noopener"  href="https://docs.groupdocs.com/display/parsernet/HTML">HTML</a> 。

Parser 类的 [GetFormattedText()][19] 方法从指定的文档中提取格式化文本。

## 使用 C# 从页面中提取格式化文本 {#Extract-Formatted-Text-from-Pages-using-CSharp}

您可以按照以下提到的简单步骤轻松解析 Word 文档并从文档的特定页面中提取格式化文本：

  * 创建 _[Parser][10]_ 类的实例
  * 指定文件路径
  * 检查 _[FormattedText][20]_ 是否为真
  * 调用 _[GetDocumentInfo][21]_ 获取页数
  * 检查 _[PageCount][22]_ 是否不为零
  * 定义_[FormattedTextOptions][15]_
  * 将 _[FormattedTextMode][16]_ 设置为 HTML
  * 为每个页面索引调用[GetFormattedText][17]方法提取文本
  * 在 TextReader 类对象中获取结果
  * 通过调用 TextReader 类的 ReadToEnd 方法显示结果

以下代码示例展示了如何使用 C# 逐页提取格式化文本。

```
// 创建 Parser 类的实例
using (Parser parser = new Parser(@"C:\Files\sample.docx"))
{
    // Check if the document supports formatted text extraction
    if (!parser.Features.FormattedText)
    {
        Console.WriteLine("Document isn't supports formatted text extraction.");
        return;
    }

    // Get the document info
    IDocumentInfo documentInfo = parser.GetDocumentInfo();
    // Check if the document has pages
    if (documentInfo.PageCount == 0)
    {
        Console.WriteLine("Document hasn't pages.");
        return;
    }

    // Iterate over pages
    for (int p = 0; p < documentInfo.PageCount; p++)
    {
        // Print a page number 
        Console.WriteLine(string.Format("Page {0}/{1}", p + 1, documentInfo.PageCount));
        // Extract a formatted text into the reader
        using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Html)))
        {
            // Print a formatted text from the document
            // We ignore null-checking as we have checked formatted text extraction feature support earlier
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

{{< figure align=center src="images/image-1024x363.png" alt="使用 C# 从页面中提取格式化文本" caption="使用 C# 从页面中提取格式化文本">}}
 

Parser 类提供表示 [Features][25] 类的 [Features][24] 属性。它可用于检查文档是否支持某个功能。您可以在“[获取支持的功能][26]”部分中阅读有关支持的功能的更多信息。

## 获得免费许可证

您可以通过请求 [免费的临时许可证][27] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用** C# 从 Word 文档中提取文本。您可以使用 [documentation][28] 了解有关 .NET API 的 GroupDocs.Parser 的更多信息。如有任何歧义，请随时在 [论坛][29] 上与我们联系。

## 也可以看看

  * [在 C# 中从 PDF、Excel、PPT、Word 文档中提取图像][30]
  * [使用 Python 从 PDF 中提取特定数据][31]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/05/Extract-Text-from-DOCX.jpg
 [2]: #api-for-extracting-text
 [3]: #Extract-Text-from-DOCX-using-CSharp
 [4]: #Get-Formatted-Text-from-DOCX-using-CSharp
 [5]: #Extract-Formatted-Text-from-Pages-using-CSharp
 [6]: https://products.groupdocs.com/parser/net
 [7]: https://docs.fileformat.com/word-processing/docx/
 [8]: https://downloads.groupdocs.com/parser/net
 [9]: https://www.nuget.org/packages/GroupDocs.Parser
 [10]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser
 [11]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/gettext/index
 [12]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/05/Extract-Text-from-DOCX-using-CSharp.jpg
 [13]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/constructors/7
 [14]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/gettext
 [15]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.options/formattedtextoptions
 [16]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.options/formattedtextoptions/properties/mode
 [17]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/getformattedtext/index
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/05/image-1.png
 [19]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/getformattedtext
 [20]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.options/features/properties/formattedtext
 [21]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/getdocumentinfo
 [22]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.options/idocumentinfo/properties/pagecount
 [23]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/05/image.png
 [24]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/properties/features
 [25]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.options/features
 [26]: https://docs.groupdocs.com/parser/net/get-supported-features/
 [27]: https://purchase.groupdocs.com/temporary-license
 [28]: https://docs.groupdocs.com/parser/net/
 [29]: https://forum.groupdocs.com/c/parser/
 [30]: https://blog.groupdocs.com/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/
 [31]: https://blog.groupdocs.cloud/2021/04/28/extract-specific-data-from-pdf-using-python/








