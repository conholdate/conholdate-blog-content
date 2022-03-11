---
title: "'使用 C# 在 PDF 文档中搜索文本'"
author: Muzammil Khan
date: 2021-10-11T06:51:13+00:00
summary: "作为 C# 开发人员，您可以在 .NET 应用程序中以编程方式轻松搜索 PDF 文档中的任何文本。在本文中，您将学习**如何使用 C# 搜索 PDF 文档中的单词**。"
url: /zh/2021/10/11/search-text-in-pdf-documents-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "文本搜索 API"
  - "区分大小写的搜索"
  - "在 PDF 中搜索单词"
  - "在文档中搜索"
  - "在 PDF 中搜索文本"

---


{{< figure align=center src="images/search-for-a-word-in-pdf-using-csharp.jpg" alt="使用 C# 在 PDF 中搜索单词">}}
 

您可能需要从文档中搜索特定信息、文本短语或单词。作为 C# 开发人员，您可以在 .NET 应用程序中以编程方式轻松搜索 PDF 文档中的任何文本。在本文中，您将学习**如何使用 C# 搜索 PDF 文档中的文本**。

本文讨论/涵盖了以下主题：

  * [用于搜索文本的 C# API][2]
  * [使用 C# 在 PDF 文档中搜索文本][3]
  * [使用 C# 在 PDF 中进行区分大小写的文本搜索][4]

## 用于搜索文本的 C# API {#api-for-searching-text}

为了在 [PDF][5] 文档中搜索文本，我将使用 [GroupDocs.Search for .NET][6] API。它允许您以所有 [流行的文档格式][7] 执行文本搜索操作，例如 PDF、Word、Excel、PowerPoint 等等。它还使您能够从文件、文档、电子邮件和档案中获取所需的信息。您可以创建和合并多个索引，以使用简单、布尔、正则表达式 (Regex)、模糊和其他类型的查询快速智能地搜索它们。

您可以[下载][8] API 的 DLL 或使用 [NuGet][9] 安装它。

```
Install-Package GroupDocs.Search
```

## 使用 C# 在 PDF 文档中搜索文本 {#Search-Text-in-PDF-Documents-using-CSharp}

您可以按照以下提到的简单步骤以编程方式在 PDF 文档中搜索任何文本或特定单词：

  * 创建 [Index][10] 类的实例
  * 指定索引文件夹的路径
  * 订阅 [索引事件][11]
  * 通过调用 [Add()][12] 方法将 PDF 文件添加到索引
  * 定义搜索查询
  * 使用带有搜索查询的 [Search()][13] 方法执行搜索
  * 使用 [SearchResult][14] 并打印摘要
  * 使用 [Highlight()][15] 方法在输出中突出显示搜索结果

以下代码示例展示了**如何使用 C# 搜索 PDF 文档中的文本**。

```
// 指定索引文件夹的路径
string indexFolder = @"C:\Files\Index\";

// 指定包含要搜索的 PDF 文档的文件夹的路径
string documentsFolder = @"C:\Files\Files\"; 

// 创建或加载索引
Index index = new Index(indexFolder);

// 订阅索引事件
index.Events.ErrorOccurred += (sender, args) =>
{
    // Writing error messages to the console
    Console.WriteLine(args.Message);
};

// 同步添加文件
// 从指定文件夹同步索引文档
index.Add(documentsFolder); 

// 执行搜索
string query = "Vestibulum"; // Specify a search query
SearchResult result = index.Search(query); // Searching in the index

// 使用搜索结果
// 打印结果
Console.WriteLine("Documents found: " + result.DocumentCount);
Console.WriteLine("Total occurrences found: " + result.OccurrenceCount);

for (int i = 0; i < result.DocumentCount; i++)
{
    FoundDocument document = result.GetFoundDocument(i);
    Console.WriteLine("\tDocument: " + document.DocumentInfo.FilePath);
    Console.WriteLine("\tOccurrences: " + document.OccurrenceCount);
}

// 突出显示文本中的出现
if (result.DocumentCount > 0)
{
    // Getting the first found document
    FoundDocument document = result.GetFoundDocument(0);

    string path = documentsFolder + "Highlighted.html";

    // Creating the output adapter to a file
    OutputAdapter outputAdapter = new FileOutputAdapter(path);

    // Creating the highlighter object
    HtmlHighlighter highlighter = new HtmlHighlighter(outputAdapter);

    // Generating output HTML formatted document with highlighted search results
    index.Highlight(document, highlighter); 

    Console.WriteLine();
    Console.WriteLine("Generated HTML file can be opened with Internet browser.");
    Console.WriteLine("The file can be found by the following path:");
    Console.WriteLine(path);
}
```

上面的代码示例将生成以下输出：

```
Documents found: 1
Total occurrences found: 4
        Document: C:\Files\Files\sample.pdf
        Occurrences: 4

Generated HTML file can be opened with Internet browser.
The file can be found by the following path:
C:\Files\Files\Highlighted.html
```

{{< figure align=center src="images/Search-Text-or-Word-in-PDF-using-CSharp.jpg" alt="使用 CSharp 搜索 PDF 中的文本或单词" caption="使用 C# 突出显示 PDF 文档中的搜索文本">}}
 

### 索引和索引事件

[Index][10] 类是提供对文档进行索引和搜索的功能的主要类。通过调用此类的构造函数，可以在内存或磁盘上创建索引。在上面的代码示例中，我在磁盘上创建了索引，以便可以重复使用。

如果在索引文件期间发生任何错误，[ErrorOccurred][11] 事件将显示错误。因此，您需要订阅它才能接收有关索引错误的信息。

### 将文件添加到索引

Index 类的 [Add()][12] 方法通过绝对或相对路径添加指定文件夹或子文件夹中的文件或所有文件。给定路径上的所有文档都将被索引。

### 执行搜索操作

Index 类提供各种 [Search][13] 方法来执行搜索操作。您可以通过提供简单的关键字或定义 [SearchQuery][17] 进行搜索。

[SearchResult][14] 类提供与搜索查询匹配的搜索结果的详细信息。此类的以下方法和属性有助于获取搜索结果的详细信息：

  * [OccurrenceCount][18] 属性显示找到的事件总数。
  * [DocumentCount][19] 属性提供在索引中找到的文档数。
  * [GetFoundDocument(int)][20] 方法通过索引返回 [FoundDocument][21]。
  * [FoundDocument.OccurrenceCount][22] 属性返回在文档中找到的出现次数。

### 突出显示搜索结果

[HtmlHighlighter][23] 类在 HTML 格式的文档的整个文本中突出显示搜索结果。

Index 类的 [Highlight()][15] 方法生成 HTML 输出，突出显示找到的术语的出现。您可以在文档中找到有关“[突出显示搜索结果][24]”的更多详细信息。

## 使用 C# 在 PDF 中进行区分大小写的文本搜索 {#Case-Sensitive-Text-Search-in-Files-using-CSharp}

您可以按照下面提到的简单步骤，以编程方式在 PDF 文档中搜索任何特定的文本短语或考虑大写和小写字母的单词：

  * 创建 [Index][10] 类的实例
  * 指定索引文件夹的路径
  * 通过调用 [Add()][12] 方法将 PDF 文件添加到索引
  * 创建 [SearchOptions][25] 的实例
  * 将 [UseCaseSensitiveSearch][26] 属性设置为 true
  * 定义搜索查询
  * 使用带有搜索查询的 [Search()][13] 方法执行搜索 and the SearchOptions
  * 使用 [SearchResult][14] 并打印摘要

以下代码示例展示了**如何使用 C#** 在 PDF 文档中执行**区分大小写的文本**搜索。

```
// 指定索引文件夹的路径
string indexFolder = @"C:\Files\Index\";

// 指定包含要搜索的 PDF 文档的文件夹的路径
string documentsFolder = @"C:\Files\Files\";

// 在指定文件夹中创建索引
Index index = new Index(indexFolder);

// 索引指定文件夹中的文档
index.Add(documentsFolder); 

// 定义搜索选项
SearchOptions options = new SearchOptions();
options.UseCaseSensitiveSearch = true; // Enabling case sensitive search

// 搜索词
string query = "Vestibulum";

// 执行搜索
SearchResult result = index.Search(query, options);

// 打印结果
Console.WriteLine("Documents found: " + result.DocumentCount);
Console.WriteLine("Total occurrences found: " + result.OccurrenceCount);

for (int i = 0; i < result.DocumentCount; i++)
{
    FoundDocument document = result.GetFoundDocument(i);
    Console.WriteLine("\tDocument: " + document.DocumentInfo.FilePath);
    Console.WriteLine("\tOccurrences: " + document.OccurrenceCount);
}
```

```
Documents found: 1
Total occurrences found: 2
        Document: C:\Files\Files\sample.pdf
        Occurrences: 2
```

[SearchOptions][25] 类提供了执行搜索操作的选项。此类的 [UseCaseSensitiveSearch][26] 属性允许您对单词或文本执行区分大小写的搜索。

## 获得免费许可证

您可以通过申请 [免费的临时许可证][27] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C# 搜索 PDF 文档中的文本**。您还学习了**如何使用 C#** 在 PDF 文档中执行**区分大小写的文本搜索。您可以使用 [文档][28] 了解有关 GroupDocs.Search for .NET API 的更多信息。如有任何歧义，请随时在 [论坛][29] 上与我们联系。

## 也可以看看

  * [使用 C# .NET 在 Word、Excel、PDF、ZIP 文档格式中搜索文本][30]
  * [在 C# 中以编程方式构建您的全文搜索解决方案][31]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/search-for-a-word-in-pdf-using-csharp.jpg
 [2]: #api-for-searching-text
 [3]: #Search-Text-in-PDF-Documents-using-CSharp
 [4]: #Case-Sensitive-Text-Search-in-Files-using-CSharp
 [5]: https://docs.fileformat.com/pdf/
 [6]: https://products.groupdocs.com/search/net
 [7]: https://docs.groupdocs.com/search/net/supported-document-formats/
 [8]: https://downloads.groupdocs.com/search/net
 [9]: https://www.nuget.org/packages/groupdocs.search
 [10]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
 [11]: https://apireference.groupdocs.com/search/net/groupdocs.search.events/eventhub/events/erroroccurred
 [12]: https://apireference.groupdocs.com/search/net/groupdocs.search.index/add/methods/1
 [13]: https://apireference.groupdocs.com/search/net/groupdocs.search.index/search/methods/2
 [14]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult
 [15]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/highlight
 [16]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Search-Text-or-Word-in-PDF-using-CSharp.jpg
 [17]: https://apireference.groupdocs.com/search/net/groupdocs.search/SearchQuery
 [18]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult/properties/occurrencecount
 [19]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult/properties/documentcount
 [20]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult/methods/getfounddocument
 [21]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/FoundDocument
 [22]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocument/properties/occurrencecount
 [23]: https://apireference.groupdocs.com/search/net/groupdocs.search.highlighters/HtmlHighlighter
 [24]: https://docs.groupdocs.com/search/net/highlighting-search-results/
 [25]: https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions
 [26]: https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions/properties/usecasesensitivesearch
 [27]: https://purchase.groupdocs.com/temporary-license
 [28]: https://docs.groupdocs.com/search/net/
 [29]: https://forum.groupdocs.com/c/search/
 [30]: https://blog.groupdocs.com/2020/05/29/search-text-in-word-excel-pdf-zip-document-formats-using-csharp-net/
 [31]: https://blog.groupdocs.com/2019/11/22/build-your-full-text-search-solution-in-csharp/








