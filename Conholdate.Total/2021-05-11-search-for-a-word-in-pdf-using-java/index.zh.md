---
title: "使用 Java 在 PDF 中搜索单词"
author: Muzammil Khan
date: 2021-05-11T12:32:49+00:00
summary: "在 Java 应用程序中以编程方式搜索 PDF 文档中的单词或任何文本。在本文中，您将学习**如何使用 Java 搜索 PDF 文档中的单词**。"
url: /zh/2021/05/11/search-for-a-word-in-pdf-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "在 PDF 中搜索单词"
  - "在文档中搜索"
  - "使用 Java 在 PDF 中搜索"
  - "在 PDF 中搜索文本"
  - "在 PDF 中搜索文本 using Java"

---


{{< figure align=center src="images/Search-in-PDF-1.jpg" alt="使用 Java 在 PDF 中搜索单词">}}
 

您可能需要从 Word 或 PDF 文档中搜索特定文本。作为 Java 开发人员，您可以通过编程方式搜索 PDF 文档中的任何文本。在本文中，您将学习**如何使用 Java 搜索 PDF 文档中的单词**。

本文讨论/涵盖了以下主题：

  * [用于搜索文本的 Java API][2]
  * [使用 Java 在 PDF 中搜索文本][3]

## 用于搜索文本的 Java API {#api-for-searching-text}

我将使用 [GroupDocs.Search for Java][4] API 来搜索 [PDF][5] 文档。它允许您以所有流行的文档格式执行文本搜索操作，例如 PDF、Word、Excel、PowerPoint 等。您可以使用此 API 从文件、文档、电子邮件和档案中轻松获取所需信息。它还使您能够创建和合并多个索引。您可以使用简单、布尔、正则表达式 (Regex)、模糊和其他类型的查询来快速、智能地搜索索引。

### 下载并配置

您可以 [下载][6] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置，以尝试以下代码示例。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```

```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-search</artifactId>
        <version>20.11</version> 
</dependency>
```

## 使用 Java 在 PDF 中搜索文本 {#search-text-from-pdf}

您可以按照以下提到的简单步骤轻松搜索 PDF 文档中的任何文本或特定单词：

  * 创建一个 [索引][7]
  * 指定索引文件夹的路径
  * 订阅 [索引事件][8]
  * 通过调用 [add][9] 方法将文件添加到索引
  * 使用 [search][10] 方法执行搜索
  * 使用 [SearchResult][11] 并打印摘要
  * 使用 [highlight][12] 方法在输出中突出显示搜索结果

以下代码示例展示了如何使用 Java 从 PDF 文档中搜索单词。

```
String indexFolder = "C:\\Index\\"; // Specify the path to the index folder
String documentsFolder = "C:\\Files\\"; // Specify the path to a folder containing documents to search

// 创建新索引或
// 打开现有索引
Index index = new Index(indexFolder);

// 订阅索引事件
index.getEvents().ErrorOccurred.add(new EventHandler<IndexErrorEventArgs>() {
    public void invoke(Object sender, IndexErrorEventArgs args) {
        System.out.println(args.getMessage()); // Writing error messages to the console
    }
});

// 同步添加文件
index.add(documentsFolder); // Synchronous indexing documents from the specified folder

// 执行搜索
String query = "elementum"; // Specify a search query
SearchResult result = index.search(query); // Searching in the index

// 使用搜索结果
// 打印结果
System.out.println("Documents found: " + result.getDocumentCount());
System.out.println("Total occurrences found: " + result.getOccurrenceCount());
for (int i = 0; i < result.getDocumentCount(); i++) {
    FoundDocument document = result.getFoundDocument(i);
    System.out.println("\tDocument: " + document.getDocumentInfo().getFilePath());
    System.out.println("\tOccurrences: " + document.getOccurrenceCount());
}

// 突出显示文本中的出现
if (result.getDocumentCount() > 0) {
    FoundDocument document = result.getFoundDocument(0); // Getting the first found document
    String path = "C:\\Output\\Highlighted.html";
    OutputAdapter outputAdapter = new FileOutputAdapter(path); // Creating the output adapter to a file
    HtmlHighlighter highlighter = new HtmlHighlighter(outputAdapter); // Creating the HtmlHighlighter object
    index.highlight(document, highlighter); // Generating output HTML formatted document with highlighted search results

    System.out.println();
    System.out.println("Generated HTML file can be opened with Internet browser.");
    System.out.println("The file can be found by the following path:");
    System.out.println(Paths.get(path).toAbsolutePath().toString());
}
```

上述代码示例应生成以下输出：

```
Documents found: 1
Total occurrences found: 6
	Document: C:\Files\Lorem ipsum.pdf
	Occurrences: 6

Generated HTML file can be opened with Internet browser.
The file can be found by the following path:
C:\Output\Highlighted.html
```

{{< figure align=center src="images/Search-word-in-PDF-1-1024x531.jpg" alt="使用 Java 在 PDF 文档中搜索单词" caption="使用 Java 在 PDF 文档中搜索单词">}}
 

### 索引和索引事件

[Index][7] 类是索引文档和搜索文档的主要类。通过调用此类的构造函数，可以在内存或磁盘上创建索引。我已经在磁盘上创建了它，以便可以重复使用。

为了接收有关索引错误的信息，我订阅了 [ErrorOccurred][8] 事件。如果在索引文件期间发生任何错误，它将显示错误。

### 将文件添加到索引

Index 类的 [add][9] 方法通过绝对或相对路径添加一个文件或文件夹或子文件夹中的所有文件。给定路径上的所有文档都将被索引。

### 执行搜索操作

Index 类提供各种 [search][10] 方法来执行搜索操作。您可以通过简单的关键字或通过定义 [SearchQuery][14] 进行搜索。

[SearchResult][11] 类提供与搜索查询匹配的搜索结果的详细信息。这里描述了一些方法：

  * [getOccurrenceCount][15]() 方法返回找到的总次数
  * getDocumentCount() 方法提供在索引中找到的文档数
  * [getFoundDocument(int)][16] 方法返回 [FoundDocument][17]
  * [FoundDocument.getOccurrenceCount()][18] 方法返回在文档中找到的出现次数

### 突出显示搜索结果

[HtmlHighlighter][19] 类有助于在 HTML 格式的整个文档文本中突出显示搜索结果。

Index 类的 [highlight][12] 方法生成 HTML 输出，突出显示找到的术语的出现。您可以在文档中找到有关“[突出显示搜索结果][20]”的更多详细信息。

## 获得免费许可证

您可以通过请求 [免费的临时许可证][21] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 Java 搜索 PDF 文档中的单词**。您可以使用 [文档][22] 了解有关 GroupDocs.Search for Java API 的更多信息。如有任何歧义，请随时在 [论坛][23] 上与我们联系。

## 也可以看看

  * [使用 C# .NET 在 Word、Excel、PDF、ZIP 文档格式中搜索文本][24]
  * [在 C# 中以编程方式构建您的全文搜索解决方案][25]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/05/Search-in-PDF-1.jpg
 [2]: #api-for-searching-text
 [3]: #search-text-from-pdf
 [4]: https://products.groupdocs.com/search/java
 [5]: https://docs.fileformat.com/pdf/
 [6]: https://downloads.groupdocs.com/search/java
 [7]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index
 [8]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.events/EventHub#ErrorOccurred
 [9]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index#add(java.lang.String)
 [10]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index#search(java.lang.String)
 [11]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/SearchResult
 [12]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index#highlight(com.groupdocs.search.results.FoundDocument,%20com.groupdocs.search.highlighters.Highlighter)
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/05/Search-word-in-PDF-1.jpg
 [14]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/SearchQuery
 [15]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/SearchResult#getOccurrenceCount()
 [16]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/SearchResult#getFoundDocument(int)
 [17]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/FoundDocument
 [18]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/FoundDocument#getOccurrenceCount()
 [19]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.highlighters/HtmlHighlighter
 [20]: https://docs.groupdocs.com/search/java/highlighting-search-results/
 [21]: https://purchase.groupdocs.com/temporary-license
 [22]: https://docs.groupdocs.com/search/java/
 [23]: https://forum.groupdocs.com/c/search/
 [24]: https://blog.groupdocs.com/2020/05/29/search-text-in-word-excel-pdf-zip-document-formats-using-csharp-net/
 [25]: https://blog.groupdocs.com/2019/11/22/build-your-full-text-search-solution-in-csharp/








