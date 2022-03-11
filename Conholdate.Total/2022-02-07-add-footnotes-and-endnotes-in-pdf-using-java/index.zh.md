---
title: "使用 Java 在 PDF 中添加脚注和尾注"
author: Muzammil Khan
date: 2022-02-07T07:18:39+00:00
summary: "作为 Java 开发人员，您可以通过编程向 PDF 文档添加脚注/尾注。在本文中，您将学习**如何使用 Java 在 PDF 文档中添加脚注和尾注**。"
url: /zh/2022/02/07/add-footnotes-and-endnotes-in-pdf-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "在 Java 中为 PDF 添加脚注"
  - "在 PDF 中添加脚注"
  - "在 PDF 中添加脚注 using Java"
  - "使用 Java 将图像添加到脚注"
  - "使用 Java 将表格添加到脚注"

---


{{< figure align=center src="images/add-footnotes-and-endnotes-in-pdf-using-java.jpg" alt="使用 Java 在 PDF 中添加脚注和尾注。">}}
 
脚注是在特定页面底部给出的注释或文本，而尾注是放置在文档末尾的注释。我们通常在文档中使用脚注或尾注作为参考、解释或评论。我们可以通过编程向 PDF 文档添加脚注/尾注。在本文中，我们将学习**如何使用 Java 在 PDF 文档中添加脚注和尾注**。

本文将涵盖以下主题：

  - "[在 PDF 中添加脚注和尾注的 Java API](#Java-API-to-Add-Footnotes-and-Endnotes-in-PDF")"
  - "[使用 Java 为 PDF 添加脚注](#Add-Footnotes-to-a-PDF-using-Java)"
  - "[在 PDF 的脚注中添加图像](#Add-an-Image-to-Footnote-in-PDF)"
  - "[在 PDF 中插入表格到脚注](#Insert-a-Table-to-Footnote-in-PDF)"
  - "[使用 Java 自定义脚注标签和线条样式](#Customize-Footnote-Label-and-Line-Style-using-Java)"
  - "[使用 Java 为现有 PDF 添加脚注](#Add-Footnotes-to-Existing-PDF-using-Java)"
  - "[使用 Java 为 PDF 添加尾注](#Add-Endnotes-to-PDF-using-Java)"
 
## 用于在 PDF 中添加脚注和尾注的 Java API {#Java-API-to-Add-Footnotes-and-Endnotes-in-PDF}

为了向 [PDF][2] 文档添加脚注和尾注，我们将使用 [Aspose.PDF for Java API][3]。它允许我们在不使用 Adobe Acrobat 的情况下生成、修改、转换、渲染、保护和打印 [支持的文档][4]。请[下载][5] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置。

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
    <artifactId>aspose-pdf</artifactId>
    <version>22.1</version>
</dependency>
```

## 使用 Java 将脚注添加到 PDF {#Add-Footnotes-to-a-PDF-using-Java}

我们可以按照以下步骤在 PDF 文档的页面末尾添加脚注：

  1. 首先，创建一个 [**_Document_**][6] 类的实例。
  2. 接下来，将 **_[Page][7]_** 添加到文档的 **_[PagesCollection][8]_**。
  3. 然后，创建一个 **_[TextFragment][9]_**。
  4. 接下来，为 _TextFragment_ 对象设置 **_[脚注][10]_** 值。
  5. 然后，将 _TextFragment_ 添加到 **[_Paragraphs_][11]** 集合中
  6. 或者，重复上述步骤为多个 _Footnote_ 值添加更多 _TextFragments_。
  7. 最后，使用 **_[Document.Save()][12]_** 方法保存 PDF 文件。它将输出文件的路径作为参数。

以下代码示例展示了**如何使用 Java 向 PDF 文档添加脚注**。

```
// 此代码示例演示如何向 PDF 文档添加脚注。
// 创建文档实例
Document document = new Document();

// 将页面添加到 PDF 的页面集合
Page page = document.getPages().add();

// 创建一个文本片段
TextFragment text = new TextFragment("Hello World");

// 为 TextFragment 设置脚注值
text.setFootNote(new Note("foot note for Hello World!"));

// 将 TextFragment 添加到文档第一页的段落集合中
page.getParagraphs().add(text);

// 创建另一个 TextFragment
text = new TextFragment("Aspose.Pdf for Java");

// 为第二个 TextFragment 设置脚注
text.setFootNote(new Note("foot note for second text fragment!"));

// 将第二个文本片段添加到 PDF 文件的段落集合
page.getParagraphs().add(text);

// 保存文档
document.save("C:\\Files\\PDF\\sample_footnote.pdf");
```

{{< figure align=center src="images/Add-Footnotes-to-a-PDF-using-Java.jpg" alt="使用 Java 为 PDF 添加脚注。" caption="使用 Java 为 PDF 添加脚注。">}}
 

## 在 PDF 的脚注中添加图像 {#Add-an-Image-to-Footnote-in-PDF}

我们可以按照以下步骤在 PDF 文档的脚注中添加图像：

  1. 首先，创建一个 [**_Document_**][6] 类的实例。
  2. 接下来，将 **_[Page][7]_** 添加到文档的 **_[PagesCollection][8]_**。
  3. 然后，创建一个 **_[TextFragment][9]_**。
  4. 接下来，为 _TextFragment_ 对象设置 **_[脚注][10]_** 值。
  5. 然后，将图像添加到 _TextFragment_ 对象。
  6. 之后，将 _TextFragment_ 添加到 **[_Paragraphs_][11]** 集合中
  7. 最后，使用 **_[Document.Save()][12]_** 方法保存 PDF 文件。它将输出文件的路径作为参数。

以下代码示例展示了**如何使用 Java 在 PDF 文档的脚注中添加图像**。

```
// 此代码示例演示如何将图像插入脚注。
// 创建文档实例
Document document = new Document();

// 将页面添加到 PDF 的页面集合
Page page = document.getPages().add();

// 创建一个文本片段
TextFragment text = new TextFragment("Hello World");

// 为 TextFragment 设置脚注值
text.setFootNote(new Note());

// 添加图片
Image image = new Image();
image.setFile("C:\\Files\\PDF\\aspose_logo.jpg");
image.setFixHeight(20);
text.getFootNote().getParagraphs().add(image);

// 创建文本片段
TextFragment footNote = new TextFragment(" foot note for Hello World!");
footNote.getTextState().setFontSize(20);
footNote.setInLineParagraph(true);
text.getFootNote().getParagraphs().add(footNote);

// 将 TextFragment 添加到文档第一页的段落集合中
page.getParagraphs().add(text);

// 保存文档
document.save("C:\\Files\\PDF\\image_footnote.pdf");
```

{{< figure align=center src="images/Add-an-Image-to-Footnote-in-PDF-1024x972.jpg" alt="" caption="Add an Image to Footnote in PDF.">}}
 

## 在 PDF 中将表格插入脚注 {#Insert-a-Table-to-Footnote-in-PDF}

我们还可以按照以下步骤在 PDF 文档的脚注中添加表格：

  1. 首先，创建一个 [**_Document_**][6] 类的实例。
  2. 接下来，将 **_[Page][7]_** 添加到文档的 **_[PagesCollection][8]_**。
  3. 然后，创建一个 **_[TextFragment][9]_**。
  4. 接下来，为 _TextFragment_ 对象设置 **_[脚注][10]_** 值。
  5. 然后，将 **_[table][15]_** 添加到 _TextFragment_ 对象。
  6. 之后，将 _TextFragment_ 添加到 **[_Paragraphs_][11]** 集合中
  7. 最后，使用 **_[Document.Save()][12]_** 方法保存 PDF 文件。它将输出文件的路径作为参数。

以下代码示例展示了**如何使用 Java 在 PDF 文档的脚注中添加表格**。

```
// 此代码示例演示如何将表格添加到脚注。
// 创建文档实例
Document document = new Document();

// 将页面添加到 PDF 的页面集合
Page page = document.getPages().add();

// 创建 TextFragment 实例
TextFragment text = new TextFragment("Hello World");

// 为 TextFragment 设置脚注值
text.setFootNote(new Note());

// 插入表格
Table table = new Table();
table.getRows().add().getCells().add().getParagraphs().add(new TextFragment("Row 1 Cell 1"));
table.getRows().get_Item(0).getCells().add().getParagraphs().add(new TextFragment("Row 1 Cell 2"));
table.getRows().add().getCells().add().getParagraphs().add(new TextFragment("Row 2 Cell 1"));
table.getRows().get_Item(1).getCells().add().getParagraphs().add(new TextFragment("Row 2 Cell 2"));
text.getFootNote().getParagraphs().add(table);

// 将 TextFragment 添加到文档第一页的段落集合中
page.getParagraphs().add(text);

// 保存文档
document.save("C:\\Files\\PDF\\Table_footnote.pdf");
```

{{< figure align=center src="images/Insert-a-Table-to-Footnote-in-PDF.jpg" alt="在 PDF 中将表格插入脚注。" caption="在 PDF 中将表格插入脚注。">}}
 

## 使用 Java 自定义脚注标签和线型 {#Customize-Footnote-Label-and-Line-Style-using-Java}

我们可以按照以下步骤自定义 PDF 文档中的脚注标签和脚注线条样式：

  1. 首先，创建一个 [**_Document_**][6] 类的实例。
  2. 接下来，将 **_[Page][7]_** 添加到文档的 **_[PagesCollection][8]_**。
  3. 然后，初始化一个 **_[GraphInfo][17]_** 对象来自定义线型。
  4. 设置 GraphInfo 对象属性，如 LineWidth、Color、DashArray 等。
  5. 接下来，创建一个 **_[TextFragment][9]_**。
  6. 然后，为 _TextFragment_ 对象设置 **_[脚注][10]_** 值。
  7. 接下来，初始化 TextState 对象并设置各种属性，例如 ForegroundColor、FontStyle 等。
  8. 之后，将 _TextFragment_ 添加到 **[_Paragraphs_][11]** 集合中
  9. 或者，重复上述步骤为多个 _Footnote_ 值添加更多 _TextFragments_。
 10. 最后，使用 **_[Document.Save()][12]_** 方法保存 PDF 文件。它将输出文件的路径作为参数。

以下代码示例展示了**如何使用 Java 添加自定义脚注标签和线条样式**。

```
// 此代码示例演示如何自定义脚注标签和线条样式。
// 创建文档实例
Document document = new Document();

// 将页面添加到 PDF 的页面集合
Page page = document.getPages().add();

// 自定义线条样式
// 创建 GraphInfo 对象
GraphInfo graph = new GraphInfo();

// 将线宽设置为 2
graph.setLineWidth(2);

// 设置图形对象的颜色
graph.setColor(Color.getRed());

// 将破折号数组值设置为 3
graph.setDashArray(new int[] { 3 });

// 将破折号相位值设置为 1
graph.setDashPhase(1);

// 将页面的脚注线条样式设置为图形
page.setNoteLineStyle(graph);

// 创建 TextFragment 实例
TextFragment text = new TextFragment("Hello World");

// 为 TextFragment 设置脚注值
text.setFootNote(new Note("foot note for Hello World!"));

// 自定义标签
text.getFootNote().setText("FOOTNOTE-1");
TextState ts = new TextState();
ts.setForegroundColor(Color.getBlue());
ts.setFontStyle(FontStyles.Italic);
text.getFootNote().setTextState(ts);

// 将 TextFragment 添加到文档第一页的段落集合中
page.getParagraphs().add(text);

// 创建另一个 TextFragment
text = new TextFragment("Aspose.Pdf for Java");

// 为第二个文本片段设置脚注
text.setFootNote(new Note("foot note for second text fragment!"));

// 将第二个文本片段添加到 PDF 文件的段落集合
page.getParagraphs().add(text);

// 保存文档
document.save("C:\\Files\\PDF\\customize_footnote.pdf");
```

{{< figure align=center src="images/Customize-Footnote-Label-and-Line-Style-using-Java.jpg" alt="使用 Java 自定义脚注标签和线条样式。" caption="使用 Java 自定义脚注标签和线条样式。">}}
 

## 使用 Java 为现有 PDF 添加脚注 {#Add-Footnotes-to-Existing-PDF-using-Java}

我们可以按照以下步骤为现有 PDF 文档添加脚注：

  1. 首先，使用 [**_Document_**][6] 类加载 PDF 文件。
  2. 接下来，通过索引获取特定的 **_[page][7]_**。
  3. 然后，创建一个带有搜索短语作为输入的 **_[TextFragmentAbsorber][19]_** 对象。
  4. 之后，调用 [_**accept()**_][20] 方法从页面中搜索输入短语。
  5. 接下来，从 _**[TextFragmentCollection][21]**_ 中获取第一次出现的搜索短语。
  6. 然后，创建一个空的 **_TextFragment_** 并设置它在页面上的位置。
  7. 此外，为 _TextFragment_ 对象设置 **_[脚注][10]_** 值。
  8. 之后，将 _TextFragment_ 添加到 **[_Paragraphs_][11]** 集合中
  9. 最后，使用 **_[Document.Save()][12]_** 方法保存 PDF 文件。它将输出文件的路径作为参数。

以下代码示例展示了**如何使用 Java 向现有 PDF 文档添加脚注**。

```
// 此代码示例演示如何将脚注添加到现有 PDF 文档。
// 加载现有的 PDF 文档
Document document = new Document("C:\\Files\\PDF\\sample.pdf");

// 创建 TextAbsorber 对象以查找文本短语的所有实例
TextFragmentAbsorber textFragmentAbsorber = new TextFragmentAbsorber("Class");

// 获取特定页面
Page page = document.getPages().get_Item(2);

// 接受文件第二页的吸收体
page.accept(textFragmentAbsorber);

// 将提取的文本片段放入集合中
TextFragmentCollection textFragmentCollection = textFragmentAbsorber.getTextFragments();

// 获取文本的第一次出现
TextFragment textFragment = textFragmentCollection.get_Item(1);

// 创建一个空的 TextFragment
TextFragment text = new TextFragment("");

// 设置位置
Position position = textFragment.getPosition();
position = new Position(position.getXIndent() + 26, position.getYIndent());
text.setPosition(position);

// 为 TextFragment 设置脚注值
text.setFootNote(new Note("This is example footnote added in an existing PDF!"));

// 将第二个文本片段添加到 PDF 文件的段落集合
page.getParagraphs().add(text);

// 保存文档
document.save("C:\\Files\\PDF\\Text_Added.pdf");
```

{{< figure align=center src="images/Add-Footnotes-to-Existing-PDF-using-Java-1024x970.jpg" alt="使用 Java 将脚注添加到现有 PDF" caption="使用 Java 为现有 PDF 添加脚注。">}}
 

## 使用 Java 将尾注添加到 PDF {#Add-Endnotes-to-PDF-using-Java}

我们还可以按照以下步骤在 PDF 文档的末尾添加尾注：

  1. 首先，创建一个 [**_Document_**][6] 类的实例。
  2. 接下来，将 **_[Page][7]_** 添加到文档的 **_[PagesCollection][8]_**。
  3. 然后，创建一个 **_[TextFragment][9]_**。
  4. 接下来，为 _TextFragment_ 对象设置 **_[Endnote][10]_** 值。
  5. （可选）为尾注设置自定义标签。
  6. 之后，将 _TextFragment_ 添加到 **[_Paragraphs_][11]** 集合中.
  7. 最后，使用 **_[Document.Save()][12]_** 方法保存 PDF 文件。它将输出文件的路径作为参数。

以下代码示例展示了**如何使用 Java 向 PDF 文档添加尾注**。

```
// 此代码示例演示如何将尾注添加到 PDF 文档。
// 创建一个文档实例
Document doc = new Document();

// 将页面添加到 PDF 的页面集合
Page page = doc.getPages().add();

// 创建 TextFragment 实例
TextFragment text = new TextFragment("Hello World");

// 为 TextFragment 设置脚注值
text.setEndNote(new Note("sample End note"));

// 为脚注指定自定义标签
text.getEndNote().setText(" Aspose(2015)");

// 将 TextFragment 添加到文档第一页的段落集合中
page.getParagraphs().add(text);

// 保存 PDF 文件
doc.save("C:\\Files\\PDF\\EndNote.pdf");
```

## 获取免费 API 许可证 {#Get-a-Free-License}

您可以通过请求 [免费的临时许可证][23] 来试用该 API，而不受评估限制。

## 结论

在本文中，我们学习了如何：

  * 使用 Java 为 PDF 文档添加脚注和尾注；
  * 在 PDF 的脚注中添加图像或表格；
  * 使用Java自定义脚注标签和线条样式；
  * 使用 Java 为现有 PDF 文档添加脚注。

此外，您可以使用 [文档][24] 了解更多关于 Aspose.PDF for Java API 的信息。如有任何歧义，请随时在 [论坛][25] 上与我们联系。

## 也可以看看

  * [使用 Java 将 PDF 转换为 Word][26]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/add-footnotes-and-endnotes-in-pdf-using-java.jpg
 [2]: https://docs.fileformat.com/pdf/
 [3]: https://products.aspose.com/pdf/java/
 [4]: https://docs.aspose.com/pdf/net/supported-file-formats/
 [5]: https://downloads.aspose.com/pdf/java
 [6]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/document
 [7]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Page
 [8]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/PageCollection
 [9]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/TextFragment
 [10]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Note
 [11]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Paragraphs
 [12]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Document#save-java.lang.String-
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Add-Footnotes-to-a-PDF-using-Java.jpg
 [14]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Add-an-Image-to-Footnote-in-PDF.jpg
 [15]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Table
 [16]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Insert-a-Table-to-Footnote-in-PDF.jpg
 [17]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/GraphInfo
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Customize-Footnote-Label-and-Line-Style-using-Java.jpg
 [19]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/TextFragmentAbsorber
 [20]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Page#accept-com.aspose.pdf.TextFragmentAbsorber-
 [21]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/TextFragmentCollection
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Add-Footnotes-to-Existing-PDF-using-Java.jpg
 [23]: https://purchase.conholdate.com/temporary-license
 [24]: https://docs.aspose.com/pdf/java
 [25]: https://forum.aspose.com/c/pdf/10
 [26]: https://blog.conholdate.com/2021/07/26/convert-pdf-to-word-using-java/







