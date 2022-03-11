---
title: "MS Word 自动化——使用 Java 创建、编辑或转换 Word 文档"
author: Muzammil Khan
date: 2021-12-01T06:16:36+00:00
summary: "作为 Java 开发人员，您可以自动化 Word 以创建新的 Word 文档、编辑或修改现有文档，或者将它们转换为其他格式，而无需使用 Microsoft Office。在本文中，我们将学习**如何使用 Java 自动化 MS Word 以创建、编辑或转换 Word 文档**。"
url: /zh/2021/12/01/ms-word-automation-create-edit-or-convert-word-documents-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 Java 将 Word 转换为 PDF"
  - "在 Java 中创建 Word 文档"
  - "使用 Java 编辑 DOCX"
  - "使用 Java 编辑 Word 文档"
  - "Java 文字自动化"
  - "在 Java 中解析 Word 文档"

---


{{< figure align=center src="images/automate-word-to-create-edit-or-convert-word-documents-using-java.jpg" alt="Microsoft Word 自动化 — 使用 Java 创建、编辑或转换 Word 文档">}}
 

Word 的自动化使您能够创建新的 Word 文档、编辑或修改现有的文档，或者将它们转换为其他格式，而无需使用 Microsoft Office。我们可以通过 MS Word 的用户界面执行的所有操作也可以使用自动化以编程方式执行。在本文中，我们将学习**如何使用 Java 自动化 MS Word 以创建、编辑或转换 Word 文档**。

本文将涵盖以下主题：

  * [用于创建、编辑或转换 Word 文档的 Java Word 自动化 API][2]
  * [使用 Java 创建 Word 文档][3]
  * [使用 Java 编辑或修改 Word 文档][4]
  * [使用 Java 查找和替换 Word 文档中的文本][5]
  * [使用 Java 转换 Word 文档][6]
  * [使用 Java 解析 Word 文档][7]

## 用于创建、编辑或转换 Word 文档的 Java Word 自动化 API {#Java-Word-Automation-API}

对于自动化 Word，我们将使用 [Aspose.Words for Java][8] API。它是一个完整且功能丰富的 Word 自动化解决方案，用于以编程方式创建、编辑或分析 Word 文档。请[下载][9] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置。

```
<repository>
    <id>AsposeJavaAPI</id>
    <name>Aspose Java API</name>
    <url>https://repository.aspose.com/repo/</url>
</repository>
```

```
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>21.11</version>
    <type>pom</type>
</dependency>
```

## 使用 Java 创建 Word 文档 {#Create-Word-Documents-using-Java}

我们可以按照以下步骤以编程方式创建 Word 文档：

  * 首先，创建 **_[Document][10]_** 类的实例。此类表示一个 Word 文档。
  * 接下来，使用 **_Document_** 对象作为参数创建 **_[DocumentBuilder][11]_** 类的实例。此类提供插入文本、图像和其他内容、指定字体、段落和节格式的方法。
  * 然后，使用 **_DocumentBuilder_** 对象插入/写入元素以添加一些文本、段落、表格或图像。
  * 最后，使用输出文件路径调用**_[Document.save()][12]_**方法保存创建的文件。

以下代码示例展示了**如何使用 Java 创建 Word 文档 (DOCX)**。

```
// 打开文档。
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 为下一个元素设置字体
Font font = builder.getFont();
font.setSize(25);
font.setBold(true);
font.setColor(Color.BLACK);
font.setName("Arial");

// 插入文本
builder.writeln("Welcome!");

// 为下一个元素设置字体
font.setSize(12);
font.setBold(false);

// 插入段落
builder.writeln("Aspose.Words for Java is a class library that enables your applications to perform a great range of document processing tasks.\r\n"
    + "\r\n"
    + "Aspose.Words supports most of the popular document formats such as DOC, DOCX, RTF, HTML, Markdown, PDF, XPS, EPUB, and others.\r\n"
    + "\r\n"
    + "With Aspose.Words for Java, you can generate, modify, convert, render, and print documents without third-party applications or Office Automation.");
builder.writeln();

font.setBold(true);
builder.writeln("This is a sample table");

font.setBold(false);
// 插入表格
Table table = builder.startTable();
builder.insertCell();
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);

builder.getCellFormat().setVerticalAlignment(CellVerticalAlignment.CENTER);

builder.write("This is row 1 cell 1");
builder.insertCell();
builder.write("This is row 1 cell 2");
builder.endRow();
builder.insertCell();
builder.write("This is row 2 cell 1");
builder.insertCell();
builder.write("This is row 2 cell 2");
builder.endRow();
builder.endTable();
builder.writeln();

// 插入图像
builder.insertImage("C:\\Files\\Words\\words_java.jpg");

// 插入分页符 
builder.insertBreak(BreakType.PAGE_BREAK);             
// 分页符后的所有元素都将插入到下一页。

// 保存文档
doc.save("C:\\Files\\Words\\document.docx");
```

{{< figure align=center src="images/Create-Word-Documents-using-Java.png" alt="使用 Java 创建 Word 文档" caption="使用 Java 创建 Word 文档。">}}
 

## 使用 Java 编辑或修改 Word 文档 {#Edit-or-Modify-Word-Documents-using-Java}

在上一节中，我们创建了一个 Word 文档。现在，让我们编辑它并更改文档的内容。我们可以按照以下步骤以编程方式编辑 Word 文档：

  * 首先，使用 **_[Document][10]_** 类以输入文件路径作为参数加载 Word 文档。
  * 接下来，通过索引访问特定部分。
  * 然后，将第一段内容作为 **_[Run][14]_** 类的对象访问。 **_Run_** 类表示具有相同字体格式的一系列字符。文档的所有文本都存储在文本运行中。
  * 之后，为访问的段落设置要更新的文本。
  * 最后，使用输出文件路径调用**_[Document.save()][12]_**方法来保存更新的文件。

以下代码示例展示了**如何使用 Java 编辑 Word 文档 (DOCX)**。

```
// 加载文档
Document doc = new Document("C:\\Files\\Words\\document.docx");

// 访问段落
Run paragraph = doc.getSections().get(0).getBody().getFirstParagraph().getRuns().get(0);
paragraph.setText("This is updated text");  

// 保存文档
doc.save("C:\\Files\\Words\\Document_updated.docx");
```

{{< figure align=center src="images/Edit-or-Modify-Word-Documents-using-Java.jpg" alt="使用 Java 编辑或修改 Word 文档" caption="使用 Java 编辑或修改 Word 文档。">}}
 

## 使用 Java 查找和替换 Word 文档中的文本 {#Find-and-Replace-Text-in-Word-Documents-using-Java}

我们还可以使用 API 的查找和替换机制来更新 Word 文档的内容。我们可以按照以下步骤以编程方式执行此操作：

  * 首先，使用 **_[Document][10]_** 类以输入文件路径作为参数加载 Word 文档。
  * 接下来，创建 **_[FindReplaceOptions][16]_** 类的实例。
  * 然后，使用搜索字符串、替换字符串和 **_FindReplaceOptions_** 对象作为参数调用 [**_replace()_**][17] 方法。此方法应使用替换字符串替换每次出现的搜索字符串。
  * 最后，使用输出文件路径调用**_[Document.save()][12]_**方法来保存更新的文件。

以下代码示例展示了**如何使用 Java 查找和替换 Word 文档 (DOCX) 中的特定文本**。

```
// 加载文档
Document doc = new Document("C:\\Files\\Words\\document.docx");

// 使用查找和替换进行更新
// 使用 Replace 方法指定搜索字符串和替换字符串。
doc.getRange().replace("Aspose.Words", "Hello", new FindReplaceOptions());

// 保存文档
doc.save("C:\\Files\\Words\\Document_updated.docx");
```

{{< figure align=center src="images/Find-and-Replace-Text-in-Word-Documents-using-Java-1024x457.jpg" alt="使用 Java 查找和替换 Word 文档中的文本" caption="使用 Java 查找和替换 Word 文档中的文本">}}
 

## 使用 Java 转换 Word 文档 {#Convert-Word-Documents-using-Java}

我们可以按照以下步骤以编程方式将 Word 文档转换为其他格式，例如 PDF、XPS、EPUB、HTML、JPG、PNG 等：

  * 首先，使用 **_[Document][10]_** 类以输入文件路径作为参数加载 Word 文档。
  * 接下来，使用 **_Document_** 对象作为参数创建 **_[PdfSaveOptions][19]_** 类的实例。将文档保存到 PDF 时，此类提供附加选项。
  * 然后，通过将 _**[PdfSaveOptions.Compliance][20]**_ 设置为 **_[PdfCompliance.PDF_17][21]_** 来指定输出文档的 PDF 标准合规级别。
  * 最后，使用输出文件路径和 **_PdfSaveOptions_** 对象作为参数调用 **_[Document.save()][12]_** 方法来保存 PDF 文件。

以下代码示例展示了**如何使用 Java 将 Word 文档 (DOCX) 转换为 PDF**。

```
// 加载文档
Document doc = new Document("C:\\Files\\Words\\document.docx");

// 为 PDF17 提供 PDFSaveOption 合规性
PdfSaveOptions options = new PdfSaveOptions();
options.setCompliance(PdfCompliance.PDF_17);

// 将 Word 转换为 PDF
doc.save("C:\\Files\\Words\\output.pdf", options);
```

{{< figure align=center src="images/Convert-Word-Documents-using-Java.jpg" alt="将 Word 文档转换为 PDF。" caption="使用 Java 转换 Word 文档">}}
 

## 使用 Java 解析 Word 文档 {#Parse-Word-Documents-using-Java}

我们可以按照以下步骤以编程方式解析 Word 文档并将内容提取为纯文本：

  * 使用 **_[Document][10]_** 类以输入文件路径作为参数加载 Word 文档。
  * 调用 **_[Document.save()][12]_** 方法将 Word 文档保存为文本文件。此方法将输出文件的路径作为参数。

以下代码示例展示了**如何使用 Java 解析 Word 文档 (DOCX)**。

```
// 从磁盘加载文档。
Document doc = new Document("C:\\Files\\Words\\document.docx");

// 另存为纯文本 
doc.save("C:\\Files\\Words\\output.txt");
```

{{< figure align=center src="images/Parse-Word-Documents-using-Java-1024x554.jpg" alt="从 Word 文档中提取文本。" caption="使用 Java 解析 Word 文档。">}}
 

## 获得免费许可证

请通过请求 [免费的临时许可证][24] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了**如何使用 Java 自动化 Word 以创建、编辑或转换 Word 文档**。我们还看到了**如何以编程方式查找和替换 Word 文档中的文本**。此外，您可以使用 [documentation][25] 了解有关 Aspose.Words for Java API 的更多信息。如有任何歧义，请随时在 [论坛][26] 上与我们联系。

## 也可以看看

  * [使用 Java 从 Word 文档中提取文本][27]
  * [使用 Java 合并 Word 文档][28]
  * [使用 Java 编辑 Word 文档][29]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/automate-word-to-create-edit-or-convert-word-documents-using-java.jpg
 [2]: #Java-Word-Automation-API
 [3]: #Create-Word-Documents-using-Java
 [4]: #Edit-or-Modify-Word-Documents-using-Java
 [5]: #Find-and-Replace-Text-in-Word-Documents-using-Java
 [6]: #Convert-Word-Documents-using-Java
 [7]: #Parse-Word-Documents-using-Java
 [8]: https://products.aspose.com/words/java/
 [9]: https://downloads.aspose.com/words/java
 [10]: https://apireference.aspose.com/words/java/com.aspose.words/Document
 [11]: https://apireference.aspose.com/words/java/com.aspose.words/DocumentBuilder
 [12]: https://apireference.aspose.com/words/java/com.aspose.words/document#save(java.lang.String)
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/Create-Word-Documents-using-Java.png
 [14]: https://apireference.aspose.com/words/java/com.aspose.words/Run
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/Edit-or-Modify-Word-Documents-using-Java.jpg
 [16]: https://apireference.aspose.com/words/java/com.aspose.words/FindReplaceOptions
 [17]: https://apireference.aspose.com/words/java/com.aspose.words/range#replace(java.util.regex.Pattern,java.lang.String,com.aspose.words.FindReplaceOptions)
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/Find-and-Replace-Text-in-Word-Documents-using-Java.jpg
 [19]: https://apireference.aspose.com/words/java/com.aspose.words/PdfSaveOptions
 [20]: https://apireference.aspose.com/words/java/com.aspose.words/pdfsaveoptions#Compliance
 [21]: https://apireference.aspose.com/words/java/com.aspose.words/pdfcompliance#PDF_17
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/Convert-Word-Documents-using-Java.jpg
 [23]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/Parse-Word-Documents-using-Java.jpg
 [24]: https://purchase.conholdate.com/temporary-license
 [25]: https://docs.aspose.com/words/java/
 [26]: https://forum.aspose.com/c/words
 [27]: https://blog.conholdate.com/2021/10/13/extract-text-from-word-documents-using-java/
 [28]: https://blog.conholdate.com/2021/06/21/merge-word-documents-using-java/
 [29]: https://blog.conholdate.com/2021/06/07/edit-word-documents-using-java/








