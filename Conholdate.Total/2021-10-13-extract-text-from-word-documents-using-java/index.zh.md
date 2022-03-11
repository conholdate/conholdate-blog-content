---
title: "使用 Java 从 Word 文档中提取文本"
author: Muzammil Khan
date: 2021-10-13T03:52:00+00:00
summary: "作为 Java 开发人员，您可以通过编程轻松地从 Word（DOC 或 DOCX）文件中提取文本。在本文中，您将学习**如何使用 Java 从 Word 文档中提取文本**。"
url: /zh/2021/10/13/extract-text-from-word-documents-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "文档文本提取"
  - "使用 Java 提取格式化文本"
  - "提取文本"
  - "提取文本 from DOCX"
  - "提取文本 from Word"
  - "文本提取"
  - "文本提取 API"
  - "用于 Java 的文本提取器 API"

---


{{< figure align=center src="images/Extract-Text-from-Word-using-Java.jpg" alt="使用 Java 从 Word 文档中提取文本">}}
 

在某些情况下，您可能需要出于各种目的从 Word 文档中提取文本。作为 Java 开发人员，您可以通过编程轻松地从 [DOC][2] 或 [DOCX][3] 文件中提取文本。在本文中，您将学习**如何使用 Java 从 Word 文档中提取文本**。

本文讨论/涵盖了以下主题：

  * [Java API 从 Word 文档中提取文本][4]
  * [使用 Java 从 Word 文档中提取文本][5]
  * [使用 Java 从 Word 文档的特定页面中提取文本][6]
  * [使用 Java 从 Word 文档中获取高亮显示][7]
  * [使用 Java 从 DOCX 中提取格式化文本][8]
  * [使用 Java 按目录提取文本][9]

## Java API 从 Word 文档中提取文本 {#Java-API-to-Extract-Text-from-Word-Documents}

为了从 DOC 或 DOCX 文件中提取文本，我们将使用 [GroupDocs.Parser for Java][10] API。它允许从 [Word][11]、[PDF][12]、[Excel][13] 和 [PowerPoint][14] 的流行文件格式中提取文本、元数据和图像。它还支持从[支持格式][15]的文件中提取原始、格式化和结构化文本。

您可以 [下载][16] API 的 JAR 或在您的基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置来尝试下面提到的代码示例。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
```

```
<dependency>
	<groupId>com.groupdocs</groupId>
	<artifactId>groupdocs-parser</artifactId>
	<version>21.2</version> 
</dependency>
```

## 使用 Java 从 Word 文档中提取文本 {#Extract-Text-from-Word-Documents-using-Java}

您可以按照以下提到的简单步骤解析任何 Word 文档并提取文本：

  * 首先，使用 [Parser][17] 类加载 DOCX 文件。
  * 然后，调用 _[Parser.getText()][18]_ 方法从加载的文档中提取文本。
  * 获取 _[TextReader][19]_ 类对象中的 _[Parser.getText()][18]_ 方法的结果。
  * 最后，调用<span><a style="font-style: italic" href="https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/TextReader#readToEnd()">TextReader.readToEnd()</a></span> _ _方法读取从当前位置到文本阅读器末尾的所有字符，并将它们作为一个字符串返回。

以下代码示例展示了如何使用 Java 从 DOCX 文件中提取文本。

```
// 创建 Parser 类的实例
Parser parser = new Parser("C:\\Files\\sample.docx");

// 将原始文本提取到阅读器中
try (TextReader reader = parser.getText()) {
    // Print a text from the document
    // If text extraction isn't supported, a reader is null
    System.out.println(reader == null ? "Text extraction isn't supported" : reader.readToEnd());
}
```

{{< figure align=center src="images/Extract-Text-from-Word-Documents-using-Java-1024x457.jpg" alt="使用 Java 从 Word 文档中提取文本" caption="使用 Java 从 Word 文档中提取文本">}}
 
## 使用 Java 从 Word 文档的特定页面中提取文本 {#Extract-Text-from-Specific-Pages-of-a-Document-using-Java}

您可以按照以下提到的简单步骤解析 Word 文档并从特定页面中提取文本：

  * 首先，使用 [Parser][17] 类加载 DOCX 文件。
  * 然后，使用 [Parser.getFeatures().isText()][21] 检查文档是否支持文本提取功能。阅读有关 [支持的功能][22] 的更多信息。
  * 现在，调用 _[Parser.getDocumentInfo()][23]_ 方法来获取有关文档的一般信息。如文件类型、页数、大小等。
  * 获取 [IDocumentInfo][24] 接口对象中的 _[Parser.getDocumentInfo()][23]_ 方法的结果。
  * 然后，检查 _[IDocumentInfo.getPageCount()][25]_ 是否不为零。此方法返回文档页的总数。
  * 遍历所有页面并为每个页面索引调用 [Parser.getText()][26] 方法以提取文本并在 [TextReader][19] 类对象中获取结果。
  * 最后，通过调用[TextReader.readToEnd()][27]方法读取提取的文本来显示结果。

以下代码示例显示了如何使用 Java 逐页提取文本。

```
// 创建 Parser 类的实例
Parser parser = new Parser("C:\\Files\\sample.docx");

// 检查文档是否支持文本提取
if (!parser.getFeatures().isText()) {
    System.out.println("The document doesn't support text extraction.");
    return;
}

// 获取文档信息
IDocumentInfo documentInfo = parser.getDocumentInfo();

// 检查文档是否有页面
if (documentInfo.getPageCount() == 0) {
    System.out.println("The document has zero pages.");
    return;
}

// 遍历页面
for (int p = 0; p < documentInfo.getPageCount(); p++) {
    // Print a page number
    System.out.println(String.format("Page number: %d/%d", p + 1, documentInfo.getPageCount()));
    // Extract a text into the reader
    try (TextReader reader = parser.getText(p)) {
        // Print a text from the document
        // We ignore null-checking as we have checked text extraction feature support earlier
        System.out.println(reader.readToEnd());
    }
}
```

{{< figure align=center src="images/Get-Text-from-Pages-using-Java-1-1024x710.jpg" alt="使用 Java 从文档的特定页面中提取文本" caption="使用 Java 从文档的特定页面中提取文本">}}
 
## 使用 Java 从 Word 文档中获取高亮显示 {#Get-Highlight-from-Documents-using-Java}

突出显示是文本的一部分，通常用于解释在搜索功能中找到的文本的上下文。您可以按照以下提到的简单步骤从文档中提取亮点：

  * 首先，使用 [Parser][17] 类加载 DOCX 文件。
  * 创建 [HighlightOptions][29] 类对象的实例，并将最大长度作为输入参数传递给其构造函数以提取固定长度的高亮。
  * 然后，调用带有起始位置和 [HighlightOptions][29] 类对象的 [Parser.getHighlight()][30] 方法，从文档中提取高亮作为 [HighlightItem][31] 类的对象。
  * 最后调用[Highlight.getPosition()][32]和[HighlightItem.getText()][33]方法获取高亮的位置和文字。

以下代码示例展示了如何使用 Java 从文档中提取突出显示。

```
// 创建 Parser 类的实例
try (Parser parser = new Parser("C:\\Files\\sample.docx")) {
    // Extract a highlight:
    HighlightItem hl = parser.getHighlight(0, true, new HighlightOptions(8));
    // Check if highlight extraction is supported
    if (hl == null) {
        System.out.println("Highlight extraction isn't supported");
        return;
    }
    // Print an extracted highlight
    System.out.println(String.format("At %d: %s", hl.getPosition(), hl.getText()));
}
```

```
At 0: Overview
```

## 使用 Java 从 DOCX 中提取格式化文本 {#Extract-Formatted-Text-from-DOCX-using-Java}

您可以按照以下提到的简单步骤解析 Word 文档并提取文本而不会丢失样式格式：

  * 首先，使用 [Parser][17] 类加载 DOCX 文件。
  * 定义 _[FormattedTextOptions][34]_ 并将 _[FormattedTextMode][35]_ 设置为 HTML。它使您能够从文档中提取 HTML 格式的文本。
  * 然后，调用 [Parser.getFormattedText()][26] 方法提取格式化文本。
  * 获取 _[TextReader][19]_ 类对象中的 _[Parser.getText()][18]_ 方法的结果。
  * 最后，调用 [TextReader.readToEnd()][27] 方法读取所有文本。

以下代码示例展示了如何使用 Java 从 DOCX 文件中提取格式化文本。

```
// 创建 Parser 类的实例
try (Parser parser = new Parser("C:\\Files\\sample.docx")) {
    // Extract a formatted text into the reader
    try (TextReader reader = parser.getFormattedText(new FormattedTextOptions(FormattedTextMode.Html))) {
        // Print a formatted text from the document
        // If formatted text extraction isn't supported, a reader is null
        System.out.println(reader == null ? "Formatted text extraction isn't suppported" : reader.readToEnd());
    }
}
```

{{< figure align=center src="images/Extract-Formatted-Text-from-DOCX-using-Java-1024x365.jpg" alt="使用 Java 从 DOCX 中提取格式化文本" caption="使用 Java 从 DOCX 中提取格式化文本">}}
 
## 使用 Java 按目录提取文本 {#Extract-Text-by-Table-of-Contents-using-Java}

您可以按照以下提到的简单步骤，按目录从文档中提取文本：

  * 首先，使用 [Parser][17] 类加载 DOCX 文件。
  * 然后，调用 [Parser.getToc()][37] 方法将目录提取为 [TocItem][38] 类对象的集合。 [TocItem][38] 表示在目录提取功能中使用的项目。
  * 现在，检查集合是否不是_null_。
  * 然后，遍历 TocItem 的集合并调用 [TocItem.extractText()][39] 方法从 [TocItem][38] 对象引用的文档中提取文本。
  * 在 [TextReader][19] 类对象中获取结果。
  * 最后，调用 [TextReader.readToEnd()][27] 方法读取所有文本。

以下代码示例展示了如何使用 Java 从 Word 文档中按目录提取文本。

```
// 创建 Parser 类的实例
try (Parser parser = new Parser("C:\\Files\\sampleTOC.docx")) {
    // Get table of contents
    Iterable<TocItem> tocItems = parser.getToc();
    // Check if toc extraction is supported
    if (tocItems == null) {
        System.out.println("Table of contents extraction isn't supported");
    }
    else
    {
        // Iterate over items
        for (TocItem tocItem : tocItems) {
            // Print the text of the chapter
            try (TextReader reader = tocItem.extractText()) {
                System.out.println("----");
                System.out.println(reader.readToEnd());
            }
        }
    }
}
```

{{< figure align=center src="images/Extract-Text-by-Table-of-Contents-using-Java-1024x457.jpg" alt="使用 Java 按目录提取文本" caption="使用 Java 按目录提取文本">}}
 
## 获得免费许可证
您可以通过申请 [免费的临时许可证][41] 来试用该 API，而不受评估限制。

## 结论
在本文中，您学习了**如何使用 Java 从 Word 文档中提取文本**。此外，您还了解了**如何以编程方式从 DOCX 文件中提取格式化文本**。本文还解释了**如何按目录提取文本**并从文档中提取亮点。此外，您可以使用 [documentation][42] 了解有关 Java API 的 GroupDocs.Parser 的更多信息。如有任何歧义，请随时在 [论坛][43] 上与我们联系。

## 也可以看看

  * [在 Java 中从发票或收据中提取数据][44]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Extract-Text-from-Word-using-Java.jpg
 [2]: https://docs.fileformat.com/word-processing/doc/
 [3]: https://docs.fileformat.com/word-processing/docx/
 [4]: #Java-API-to-Extract-Text-from-Word-Documents
 [5]: #Extract-Text-from-Word-Documents-using-Java
 [6]: #Extract-Text-from-Specific-Pages-of-a-Document-using-Java
 [7]: #Get-Highlight-from-Documents-using-Java
 [8]: #Extract-Formatted-Text-from-DOCX-using-Java
 [9]: #Extract-Text-by-Table-of-Contents-using-Java
 [10]: https://products.groupdocs.com/parser/net
 [11]: https://docs.fileformat.com/word-processing/
 [12]: https://docs.fileformat.com/pdf/
 [13]: https://docs.fileformat.com/spreadsheet/
 [14]: https://docs.fileformat.com/presentation/
 [15]: https://docs.groupdocs.com/parser/java/supported-document-formats/
 [16]: https://downloads.groupdocs.com/parser/java
 [17]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser
 [18]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getText()
 [19]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/TextReader
 [20]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Extract-Text-from-Word-Documents-using-Java.jpg
 [21]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/Features#isText()
 [22]: https://docs.groupdocs.com/parser/java/get-supported-features/
 [23]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getDocumentInfo()
 [24]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/IDocumentInfo
 [25]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/IDocumentInfo#getPageCount()
 [26]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getFormattedText(com.groupdocs.parser.options.FormattedTextOptions)
 [27]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/TextReader#readToEnd()
 [28]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Get-Text-from-Pages-using-Java-1.jpg
 [29]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/HighlightOptions
 [30]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getHighlight(int,%20boolean,%20com.groupdocs.parser.options.HighlightOptions)
 [31]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/HighlightItem
 [32]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/HighlightItem#getPosition()
 [33]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/HighlightItem#getText()
 [34]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/FormattedTextOptions
 [35]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/FormattedTextMode
 [36]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Extract-Formatted-Text-from-DOCX-using-Java.jpg
 [37]: https://apireference.groupdocs.com/java/parser/com.groupdocs.parser/Parser#getToc()
 [38]: https://apireference.groupdocs.com/java/parser/com.groupdocs.parser.data/TocItem
 [39]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/TocItem#extractText()
 [40]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Extract-Text-by-Table-of-Contents-using-Java.jpg
 [41]: https://purchase.groupdocs.com/temporary-license
 [42]: https://docs.groupdocs.com/parser/java/
 [43]: https://forum.groupdocs.com/c/parser/
 [44]: https://blog.groupdocs.com/2021/01/22/extract-data-from-invoices-or-receipts-in-java/








