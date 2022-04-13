---
title: "使用 Java 从 PDF 文档中提取文本和图像"
author: "Muzammil Khan"
date: 2022-04-12T03:52:00+00:00
summary: "作为 Java 开发人员，您可以轻松地以编程方式从 PDF 文档中提取文本和图像。在本文中，您将学习**如何使用 Java 从 PDF 文档中提取文本和图像**。"
url: /zh/2022/04/12/extract-text-and-images-from-pdf-documents-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "文档文本提取"
  - "文档图像提取"
  - "提取文本"
  - "提取图像"
  - "提取文本 from PDF"
  - "提取图像 from PDF"
  - "文本提取"
  - "文本提取 API"
  - "用于 Java 的文本提取器 API"
  - "图像提取"
  - "图像提取 API"
  - "用于 Java 的图像提取器 API"
---

{{< figure align=center src="images/extract-text-and-images-from-pdf-documents-using-java.jpg" alt="使用 Java 从 PDF 文档中提取文本和图像">}}

[PDF][1] 是使用最广泛的数字文档格式。我们可以解析 PDF 文档并以编程方式从中提取文本和图像。它在多种情况下可能很有用，例如文本分析、信息检索、文档转换等。在本文中，我们将学习**如何使用 Java 从 PDF 文档中提取文本和图像**。

本文将涵盖以下主题：

  * [Java API 从 PDF 文档中提取文本和图像][2]
  * [使用 Java 从 PDF 文档中提取文本][3]
  * [使用 Java 从 PDF 文档的特定页面中提取文本][4]
  * [使用 Java 从 PDF 文档中获取图像][5]
  * [使用 Java 从 PDF 文档的特定页面中提取图像][6]
  * [使用 Java 提取图像并将其保存到文件][7]

## Java API 从 PDF 文档中提取文本和图像 {#Java-API-to-Extract-Text-and-Images-from-PDF-Documents}

为了从 PDF 文档中提取文本和图像，我们将使用 [GroupDocs.Parser for Java][8] API。它允许从 [支持的格式][9] 的文件中提取原始的、格式化的和结构化的文本、元数据和图像。请[下载][10] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 _pom.xml_ 配置。

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
	<version>22.3</version> 
</dependency>
```

## 使用 Java 从 PDF 文档中提取文本 {#Extract-Text-from-PDF-Documents-using-Java}

我们可以按照以下步骤解析任何 PDF 文档并提取文本：

  * 首先，使用 [Parser][11] 类加载 PDF 文件。
  * 接下来，调用 _[Parser.getText()][12]_ 方法从加载的文档中提取文本。
  * 然后，在 _[TextReader][13]_ 类对象中获取结果。
  * 最后，调用 _[TextReader.readToEnd()][14]_ 方法读取从当前位置到文本阅读器末尾的所有字符，并将它们作为一个字符串返回。

以下代码示例展示了如何使用 Java 从 PDF 文件中提取文本。

```
// 此代码示例演示如何解析 PDF 和提取文本。
// 创建 Parser 类的实例
Parser parser = new Parser("D:\\Files\\Parser\\sample.pdf");

// 将文本提取到阅读器中
try (TextReader reader = parser.getText()) {
    // Print a text from the document
    // If text extraction isn't supported, a reader is null
    System.out.println(reader == null ? "Text extraction isn't supported" : reader.readToEnd());
}
```

{{< figure align=center src="images/Extract-Text-from-PDF-Documents-using-Java.jpg" alt="使用 Java 从 PDF 文档中提取文本" caption="使用 Java 从 PDF 文档中提取文本">}}
 
## 使用 Java 从 PDF 文档的特定页面中提取文本 {#Extract-Text-from-Specific-Page-of-a-PDF-Document-using-Java}

您可以按照以下提到的简单步骤解析 PDF 文档并从特定页面提取文本：

  * 首先，使用 [Parser][11] 类加载 PDF 文件。
  * 接下来，使用 _[Parser.getDocumentInfo()][15]_ 方法获取文档信息。
  * 然后，检查 _[IDocumentInfo.getPageCount()][16]_ 是否不为零。
  * 之后，使用页面索引调用 [Parser.getText()][12] 方法以从该特定页面提取文本并在 [TextReader][13] 类对象中获取结果。
  * 最后，通过调用[TextReader.readToEnd()][14]方法读取提取的文本来显示结果。

以下代码示例展示了如何使用 Java 从特定页面中提取文本。

```
// 此代码示例演示如何解析 PDF 并从特定页面提取文本。
// 创建 Parser 类的实例
Parser parser = new Parser("D:\\Files\\Parser\\sample.pdf");

// 获取文档信息
IDocumentInfo documentInfo = parser.getDocumentInfo();

// 检查文档是否有页面
if (documentInfo == null || documentInfo.getRawPageCount() == 0) {
    System.out.println("Document hasn't pages.");
    return;
}

// 将文本提取到阅读器中
try (TextReader reader = parser.getText(1)) {
    // Print a text from the document
    // If text extraction isn't supported, a reader is null
    System.out.println(reader.readToEnd());
}
```

该 API 还可以检查文档是否支持文本提取功能。为此，我们可以使用 [Parser.getFeatures().isText()][17] 属性。请阅读有关 [支持的功能][18] 的更多信息。

## 使用 Java 从 PDF 文档中获取图像 {#Get-Images-from-PDF-Documents-using-Java}

我们可以按照以下步骤解析任何 PDF 文档并提取图像：

  * 首先，使用 [Parser][11] 类加载 PDF 文件。
  * 接下来，调用_[Parser.getImages()][19]_ 方法并从加载的文档中获取_[PageImageArea][20]_ 对象的集合。
  * 然后，检查集合是否不为空。
  * 之后，遍历所有找到的图像。
  * 最后，显示图像细节。

以下代码示例展示了如何使用 Java 从 PDF 文件中获取图像详细信息。

```
// 此代码示例演示如何解析 PDF 并获取图像。
// 创建 Parser 类的实例
Parser parser = new Parser("D:\\Files\\Parser\\images.pdf");

// 提取图像
Iterable<PageImageArea> images = parser.getImages();

// 检查是否支持图像提取
if (images == null) {
    System.out.println("Images extraction isn't supported");
    return;
}

// 迭代图像
for (PageImageArea image : images) {
    // Print a page index, rectangle and image type:
    System.out.println("Page: " + image.getPage().getIndex());
    System.out.println("Image Rectangle: " + image.getRectangle());
    System.out.println("Image Filetype: " + image.getFileType());
    System.out.println("----------------------------------------");
}
```

{{< figure align=center src="images/Get-Images-from-PDF-Documents-using-Java.jpg" alt="使用 Java 从 PDF 文档中获取图像" caption="使用 Java 从 PDF 文档中获取图像">}}

## 使用 Java 从 PDF 文档的特定页面中提取图像 {#Extract-Images-from-Specific-Page-of-a-PDF-Document-using-Java}

我们可以按照下面提到的简单步骤从特定页面中提取图像：

  * 首先，使用 [Parser][11] 类加载 PDF 文件。
  * 接下来，使用 _[Parser.getDocumentInfo()][15]_ 方法获取文档信息。
  * 然后，检查 _[IDocumentInfo.getPageCount()][16]_ 是否不为零。
  * 之后，使用页面索引调用 [Parser.getImages()][21] 方法以从该特定页面中提取图像。
  * 最后，遍历所有找到的图像并显示细节。

以下代码示例展示了如何使用 Java 从特定页面中提取图像。

```
// 此代码示例演示如何解析 PDF 并从特定页面获取图像。
// 创建 Parser 类的实例
Parser parser = new Parser("D:\\Files\\Parser\\images.pdf");

// 获取文档信息
IDocumentInfo documentInfo = parser.getDocumentInfo();

// 检查文档是否有页面
if (documentInfo.getPageCount() == 0) {
    System.out.println("Document hasn't pages.");
    return;
}

int pageIndex = 1;

// 迭代图像
// 我们忽略了空值检查，因为我们之前已经检查过图像提取功能支持
for (PageImageArea image : parser.getImages(pageIndex)) {
  // Print a page index, rectangle and image type:
    System.out.println("Page: " + image.getPage().getIndex());
    System.out.println("Image Rectangle: " + image.getRectangle());
    System.out.println("Image Filetype: " + image.getFileType());
    System.out.println("----------------------------------------");
}
```

## 使用 Java 提取图像并将其保存到文件 {#Extract-and-Save-Images-to-Files-using-Java}

我们还可以按照以下步骤保存提取的图像：

  * 首先，使用 [Parser][11] 类加载 PDF 文件。
  * 接下来，调用 _[Parser.getImages()][19]_ 方法并从加载的文档中获取 PageImageArea 对象的集合。
  * 然后，创建 _[ImageOptions][22]_ 类的实例并设置图像格式。
  * 之后，遍历所有找到的图像。
  * 最后，使用 _[save()][23]_ 方法保存。它将输出文件路径和 ImageOptions 作为参数。

以下代码示例展示了如何使用 Java 提取图像并将其保存到文件中。

```
// 此代码示例演示如何提取目录中的图像。
// 创建 Parser 类的实例
Parser parser = new Parser("D:\\Files\\Parser\\images.pdf");

// 从文档中提取图像
Iterable<PageImageArea> images = parser.getImages();

// 检查是否支持图像提取
if (images == null) {
    System.out.println("Page images extraction isn't supported");
    return;
}

// 创建以 PNG 格式保存图像的选项
ImageOptions options = new ImageOptions(ImageFormat.Png);

int imageNumber = 0;

// 迭代图像
for (PageImageArea image : images)
{
    // Save the image to the PNG file
    image.save(String.format("D:\\Files\\Parser\\Images\\%d.png", imageNumber), options);
    imageNumber++;
}
```

{{< figure align=center src="images/Extract-and-Save-Images-to-Files-using-Java.jpg" alt="使用 Java 提取图像并将其保存到文件" caption="使用 Java 提取图像并将其保存到文件">}}

## 获得免费许可证
您可以通过请求 [免费的临时许可证][24] 来试用该 API，而不受评估限制。

## 结论
在本文中，我们学习了如何：

  * 使用 Java 从整个 PDF 文档或文档的特定页面中提取所有文本；
  * 以编程方式从 PDF 文件中提取图像；
  * 将提取的图像保存在本地磁盘上。

此外，您可以使用 [documentation][25] 了解有关 Java API 的 GroupDocs.Parser 的更多信息。如有任何歧义，请随时在 [论坛][26] 上与我们联系。

## 也可以看看

  * [使用 Java 从 Word 文档中提取文本][27]

 [1]: https://docs.fileformat.com/pdf/
 [2]: #Java-API-to-Extract-Text-and-Images-from-PDF-Documents
 [3]: #Extract-Text-from-PDF-Documents-using-Java
 [4]: #Extract-Text-from-Specific-Page-of-a-PDF-Document-using-Java
 [5]: #Get-Images-from-PDF-Documents-using-Java
 [6]: #Extract-Images-from-Specific-Page-of-a-PDF-Document-using-Java
 [7]: #Extract-and-Save-Images-to-Files-using-Java
 [8]: https://products.groupdocs.com/parser/java/
 [9]: https://docs.groupdocs.com/parser/java/supported-document-formats/
 [10]: https://downloads.groupdocs.com/parser/java
 [11]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser
 [12]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getText()
 [13]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/TextReader
 [14]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/TextReader#readToEnd()
 [15]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getDocumentInfo()
 [16]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/IDocumentInfo#getPageCount()
 [17]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/Features#isText()
 [18]: https://docs.groupdocs.com/parser/java/get-supported-features/
 [19]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getImages()
 [20]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/PageImageArea
 [21]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getImages(int)
 [22]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/ImageOptions
 [23]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/PageImageArea#save(java.lang.String,%20com.groupdocs.parser.options.ImageOptions)
 [24]: https://purchase.groupdocs.com/temporary-license
 [25]: https://docs.groupdocs.com/parser/java/
 [26]: https://forum.groupdocs.com/c/parser/
 [27]: https://blog.conholdate.com/2021/10/13/extract-text-from-word-documents-using-java/