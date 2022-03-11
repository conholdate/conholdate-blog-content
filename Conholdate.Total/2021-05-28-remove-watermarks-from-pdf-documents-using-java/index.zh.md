---
title: "使用 Java 从 PDF 文档中删除水印"
author: Muzammil Khan
date: 2021-05-28T09:39:06+00:00
summary: "您可以通过编程轻松地从文档中删除水印。在本文中，您将学习**如何使用 Java 去除 PDF 文档中的水印**。"
url: /zh/2021/05/28/remove-watermarks-from-pdf-documents-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 Java 删除文本水印"
  - "去除水印"
  - "从 PDF 中删除水印"
  - "使用 Java 去除水印"

---


{{< figure align=center src="images/Remove-Watermarks-from-PDF-Documents-using-Java.jpg" alt="使用 Java 从 PDF 文档中删除水印">}}
 

水印图像或文本用于识别文档的作者或版权信息。您可以检测文档中所有可用的水印，然后将其删除。作为 Java 开发人员，您可以轻松地以编程方式从文档中删除水印。在本文中，您将学习**如何使用 Java 去除 PDF 文档中的水印**。

本文讨论/涵盖了以下主题：

  * [用于去除水印的 Java API][2]
  * [使用Java从PDF中删除所有水印][3]
  * [使用Java从PDF中去除纯文本水印][4]
  * [删除具有特定文本格式的水印][5]
  * [使用Java从PDF中去除仅图像水印][6]

## 用于去除水印的 Java API {#api-for-extracting-text}

我将使用 [GroupDocs.Watermark for Java][7] API 从 [PDF][8] 文档中删除水印。它允许执行图像和文本水印操作。它还使您能够应用新水印、搜索和删除支持格式的文件（如 Word、Excel、Powerpoint 和 PDF）中的现有水印。

您可以 [下载][9] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置来尝试以下代码示例。

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
        <artifactId>groupdocs-watermark</artifactId>
        <version>20.5</version> 
</dependency>
```

## 使用Java从PDF中删除所有水印 {#Remove-All-Watermarks-from-PDF-using-Java}

您可以按照以下提到的简单步骤轻松删除 PDF 文档中的所有水印：

  * 创建 _[Watermarker][10]_ 类的实例
  * 指定输入 PDF 文件的路径
  * 通过调用 _[search()][12]_ 方法填充 _[PossibleWatermarkCollection][11]_
  * 调用[clear()][13]方法去除所有水印
  * 保存更新的文件

以下代码示例显示了如何使用 Java 删除 PDF 文档中的所有可用水印。

```
// 创建实例
Watermarker watermarker = new Watermarker("C:\\Files\\sample.pdf");

// 搜索所有可能的水印
PossibleWatermarkCollection possibleWatermarks = watermarker.search();

// 删除所有找到的水印
possibleWatermarks.clear();

// 保存更新的文件
watermarker.save("C:\\Files\\output.pdf");

watermarker.close();
```

{{< figure align=center src="images/Remove-All-Watermarks-from-PDF-using-Java-1024x602.jpg" alt="使用Java从PDF中删除所有水印" caption="使用Java从PDF中删除所有水印">}}
 

[Watermarker][10] 类有助于在文档中添加、删除和搜索水印。

_[PossibleWatermarkCollection][11]_ 类表示在内容中找到的可能水印的集合。

Watermarker 类的 [search()][12] 方法搜索文档中所有可能的水印。它将结果集作为 PossibleWatermarkCollection 返回。

## 使用Java从PDF中去除纯文本水印 {#Text-Only-Watermarks-Removal-from-PDF-using-Java}

按照下面提到的简单步骤，您可以轻松地从 PDF 文档中删除所有纯文本水印：

  * 创建 _[Watermarker][10]_ 类的实例
  * 指定输入 PDF 文件的路径
  * 通过调用 _[search()][12]_ 方法填充 _[PossibleWatermarkCollection][11]_
  * 检查所有可能水印的 getText() 是否不为空或为空
  * 然后将索引传递给 [_removeAt()_][15] 方法以将其删除
  * 保存更新的文件

以下代码示例显示了如何使用 Java 仅删除 PDF 文档中可用的文本水印。

```
// 创建实例
Watermarker watermarker = new Watermarker("C:\\Files\\sample.pdf");

// 搜索所有可能的水印
PossibleWatermarkCollection possibleWatermarks = watermarker.search();

// 删除所有找到的水印
for (int i = possibleWatermarks.getCount() - 1; i >= 0; i--)
{
  if(possibleWatermarks.get_Item(i).getText() != null && possibleWatermarks.get_Item(i).getText() != "")
  {
    possibleWatermarks.removeAt(i);
  }
}

// 保存更新的文档
watermarker.save("C:\\Files\\output.pdf");

watermarker.close();
```

{{< figure align=center src="images/Text-Only-Watermarks-Removal-from-PDF-using-Java-1024x591.jpg" alt="使用Java从PDF中去除纯文本水印" caption="使用Java从PDF中去除纯文本水印">}}
 

[_removeAt()_][15] 方法从 PossibleWatermarksCollection 中移除指定索引处的项目。

## 删除具有特定文本格式的水印 {#Remove-Watermark-with-Particular-Text-Formatting}

您可以按照以下提到的简单步骤从 PDF 文档中删除具有特定格式的文本水印：

  * 创建 _[Watermarker][10]_ 类的实例
  * 指定输入 PDF 文件的路径
  * 定义_[TextFormattingSearchCriteria][17]_
  * 通过调用 _[search()][12]_ 方法填充 _[PossibleWatermarkCollection][11]_
  * 调用[clear()][13]方法去除所有找到的水印
  * 保存更新的文件

以下代码示例显示了如何使用 Java 从 PDF 文档中删除具有特定文本格式的文本水印。

```
// 创建实例
Watermarker watermarker = new Watermarker("C:\\Files\\sample.pdf");

// 定义文本格式搜索条件
TextFormattingSearchCriteria criteria = new TextFormattingSearchCriteria();
criteria.setFontName("Arial");
criteria.setMinFontSize(19);
criteria.setMaxFontSize(42);
criteria.setFontBold(false);

// 搜索可能的水印
PossibleWatermarkCollection watermarks = watermarker.search(criteria);
watermarks.clear();

// 保存更新的文档
watermarker.save("C:\\Files\\output.pdf");

watermarker.close();
```

{{< figure align=center src="images/Remove-Watermarks-with-Particular-Text-Formatting-1024x599.jpg" alt="删除具有特定文本格式的水印" caption="删除具有特定文本格式的水印">}}
 

## 使用Java从PDF中去除仅图像水印 {#Image-Only-Watermarks-Removal-from-PDF-using-Java}

按照下面提到的简单步骤，您可以轻松地从 PDF 文档中删除所有仅图像水印：

  * 创建 _[Watermarker][10]_ 类的实例
  * 指定输入 PDF 文件的路径
  * 通过调用 _[search()][12]_ 方法填充 _[PossibleWatermarkCollection][11]_
  * 检查所有可能水印的 getImageData() 是否不为空
  * 然后将索引传递给 [_removeAt(_)][15] 方法以将其删除
  * 保存更新的文件

以下代码示例显示了如何使用 Java 仅删除 PDF 文档中可用的图像水印。

```
// 创建实例
Watermarker watermarker = new Watermarker("C:\\Files\\sample.pdf");

// 搜索所有可能的水印
PossibleWatermarkCollection possibleWatermarks = watermarker.search();

// 删除所有图像水印
for (int i = possibleWatermarks.getCount() - 1; i >= 0; i--)
{
  if(possibleWatermarks.get_Item(i).getImageData() != null)
  {
    possibleWatermarks.removeAt(i);
  }
}

// 保存更新的文档
watermarker.save("C:\\Files\\output.pdf");

watermarker.close();
```

{{< figure align=center src="images/Image-Only-Watermarks-Removal-from-PDF-using-Java-1024x599.jpg" alt="使用Java从PDF中去除仅图像水印" caption="使用Java从PDF中去除仅图像水印">}}
 

## 获得免费许可证

您可以通过请求 [免费的临时许可证][20] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 Java 从 PDF 文档中删除文本或图像水印**。此外，您还学习了如何从文档中删除纯文本或纯图像水印。您可以使用 [文档][21] 了解有关 Java API 的 GroupDocs.Watermark 的更多信息。如有任何歧义，请随时在 [论坛][22] 上与我们联系。

## 也可以看看

  * [在 Java 中查找和删除文档中的水印][23]
  * [使用 REST API 查找和替换文档中的水印][24]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/05/Remove-Watermarks-from-PDF-Documents-using-Java.jpg
 [2]: https://blog.conholdate.com/2021/05/21/extract-text-from-doc-or-docx-using-csharp/#api-for-extracting-text
 [3]: #Remove-All-Watermarks-from-PDF-using-Java
 [4]: #Text-Only-Watermarks-Removal-from-PDF-using-Java
 [5]: #Remove-Watermark-with-Particular-Text-Formatting
 [6]: #Image-Only-Watermarks-Removal-from-PDF-using-Java
 [7]: https://products.groupdocs.com/watermark/java
 [8]: https://docs.fileformat.com/pdf/
 [9]: https://downloads.groupdocs.com/watermark/java
 [10]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
 [11]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.search/PossibleWatermarkCollection
 [12]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#search()
 [13]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.common/RemoveOnlyListBase#clear()
 [14]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/05/Remove-All-Watermarks-from-PDF-using-Java.jpg
 [15]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.common/RemoveOnlyListBase#removeAt(int)
 [16]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/05/Text-Only-Watermarks-Removal-from-PDF-using-Java.jpg
 [17]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.search/TextFormattingSearchCriteria
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/05/Remove-Watermarks-with-Particular-Text-Formatting.jpg
 [19]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/05/Image-Only-Watermarks-Removal-from-PDF-using-Java.jpg
 [20]: https://purchase.groupdocs.com/temporary-license
 [21]: https://docs.groupdocs.com/watermark/java/
 [22]: https://forum.groupdocs.com/c/watermark/
 [23]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/
 [24]: https://blog.groupdocs.cloud/2021/02/09/find-and-replace-watermark-using-rest-api/








