---
title: "使用 Java 比较 Word 文档并突出显示差异"
author: Muzammil Khan
date: 2021-08-03T17:17:27+00:00
summary: "作为 Java 开发人员，您可以轻松地以编程方式比较您的两个或多个 Word 文档。在本文中，您将学习**如何使用 Java 比较两个或多个 Word 文档并突出差异**。"
url: /zh/2021/08/03/compare-word-documents-and-highlight-differences-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "比较多个 DOCX 文件"
  - "比较 Word 文档"
  - "使用 Java 比较 Word 文件"
  - "用于比较文档的 Java API"

---


{{< figure align=center src="images/compare-word-documents-and-highlight-differences-using-java.jpg" alt="使用 Java 比较 Word 文档并突出显示差异">}}
 

您可以轻松地比较两个或多个 Word 文档并以编程方式突出显示差异。您可能需要比较同一 Word 文件或不同文件的多个版本，以了解 Java 应用程序中的差异和相似之处。在本文中，您将学习**如何使用 Java 比较两个或多个 Word 文档并突出差异**。

本文讨论/涵盖了以下主题：

  * [用于比较 Word 文档的 Java API][2]
  * [使用 Java 比较 Word 文档][3]
  * [使用 Java 获取更改的文本][4]
  * [比较 Word 文档中的书签][5]

## 用于比较 Word 文档的 Java API {#java-comparison-api}

我将使用 [GroupDocs.Comparison for Java API][6] 来比较 [DOCX][7] 文档。它进行比较以检测单词、段落和字符的内容变化，同时提供列出差异摘要的比较文档。它还使您能够检测相似文档格式之间文本样式的变化和差异。 API 支持比较所有行业标准文档格式，例如 PDF、HTML、Word、Excel、PowerPoint、Outlook 电子邮件、Visio 图表、OpenDocument、AutoCAD 和图像。

您可以 [下载][8] API 的 JAR 或在您的基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置来尝试下面提到的代码示例。

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
        <artifactId>groupdocs-comparison</artifactId>
        <version>21.6</version> 
</dependency>
```

## 使用 Java 比较 Word 文档 {#Compare-Word-Documents-using-Java}

您可以按照下面给出的简单步骤比较两个或多个 Word 文档：

  1. 创建 _**[Comparer][9]**_ 类的实例
  2. 向构造函数提供源 DOCX 文件路径
  3. **_[添加][10]_** 目标 DOCX 文件进行比较
  4. 调用 _**[Compare()][11]**_ 方法以及输出文件路径

以下代码示例展示了**如何比较 Word 文档并突出显示使用 Java 的差异**。

```
// 初始化比较器
Comparer comparer = new Comparer("C:\\Files\\source.docx");

// 添加目标文件
comparer.add("C:\\Files\\target.docx");

// 比较并保存比较结果
comparer.compare("C:\\Files\\result.docx");
```

{{< figure align=center src="images/source-and-target-word-documents-1024x671.jpg" alt="源和目标 Word 文档" caption="源文件和目标文件">}}
 

{{< figure align=center src="images/result-1024x679.jpg" alt="使用 Java 比较两个 Word 文档" caption="使用 Java 比较两个 Word 文档">}}
 

生成的文档还包括文档末尾的摘要页面。它显示了所有更改的摘要。

**[Comparer][9]** 类是控制文档比较过程的主类。此类的 [Compare()][11] 方法比较源文档和目标文档。此方法将结果保存到作为输入参数提供的文件路径中。该类的 [Add()][10] 方法，将文件添加到比较过程中。您可以使用 Add() 方法轻松地将多个文件添加到比较中，如下所示：

```
comparer.Add("target2.docx");
comparer.Add("target3.docx");
```

## 使用 Java 获取更改的文本 {#Get-Changes-Text-using-Java}

您可以按照下面给出的简单步骤以编程方式获取更改的文本：

  1. 创建 _**[Comparer][9]**_ 类的实例
  2. 向构造函数提供源 DOCX 文件路径
  3. _**[添加][10]**_ 目标 DOCX 文件进行比较
  4. 调用 _**[Compare()][11]**_ 方法
  5. 调用**_[getChanges()][14]_**方法，获取变更详情
  6. 显示更改

以下代码示例显示了**如何使用 Java 获取更改的文本**。

```
// 初始化比较器
Comparer 比较r = new Comparer("C:\\Files\\source.docx");

// 添加目标文件
比较r.add("C:\\Files\\target.docx");

// 比较
final Path resultPath = 比较r.比较();

// 获取更改
ChangeInfo[] changes = 比较r.getChanges();
System.out.println("Count of changes: " + changes.length);

for (ChangeInfo change : changes) {
    System.out.printf("Change Type: %d, Text: %s%n", change.getType(), change.getText());
}
```

```
Count of changes: 10
Change Type: 2, Text: 
Change Type: 2, Text:  Company  HYPERLINK "http://www.aspose.com/" Aspose Pty Ltd Division GroupDocs 
Change Type: 2, Text: 
Change Type: 2, Text: Cool 
Change Type: 3, Text: test 
Change Type: 2, Text:  
Change Type: 2, Text: signatures
Change Type: 2, Text: Our 
Change Type: 2, Text: char&#091;
Change Type: 2, Text: 255] 
```

您可以通过调用 _Comparer_ 类的 **[getChanges()][14]** 方法来获取源文件和目标文件之间的更改列表。它返回 [ChangeInfo][15] 对象的列表。 _ChangeInfo_ 类提供了获取更改详细信息的方法，例如 [_getText()_][16] 以获取特定更改的文本。

## 比较 Word 文档中的书签 {#Compare-Bookmarks-in-Word-Documents-using-Java}

您可以按照以下给出的简单步骤以编程方式比较 Word 文档中存在的书签：

  1. 创建 _**[Comparer][9]**_ 类的实例
  2. 向构造函数提供源 DOCX 文件路径
  3. **_[添加][10]_** 目标 DOCX 文件进行比较
  4. 创建 **_[CompareOptions][17]_** 的实例
  5. 将 _**[CompareBookmarks][18]**_ 设置为 true
  6. 调用 [**_Compare()_**][19] 方法以及输出文件路径和 _CompareOptions_ 对象

以下代码示例展示了**如何使用 Java 比较 Word 文档中的书签**。

```
// 初始化比较器
Comparer comparer = new Comparer("C:\\Files\\source.docx");

// 添加目标文件
comparer.add("C:\\Files\\target.docx");

// 定义比较选项
CompareOptions compareOptions = new CompareOptions();
compareOptions.setCompareBookmarks(true);

// 比较并保存比较结果
comparer.compare("C:\\Files\\result.docx", compareOptions);
```

{{< figure align=center src="images/Compare-Bookmarks-in-Word-Documents-using-Java-1024x333.jpg" alt="使用 Java 比较 Word 文档中的书签" caption="使用 Java 比较 Word 文档中的书签">}}
 

您可以通过应用各种比较选项来增强比较过程。为此，[**CompareOptions**][17] 类允许您通过提供各种方法来设置不同的比较选项。 _setCompareBookmarks()_ 方法使您能够比较源文档和目标文档中可用的书签。

## 获得免费许可证

您可以通过请求 [免费的临时许可证][21] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 Java 比较两个或多个 Word 文档并突出显示** **差异**。您还学习了**如何获取突出显示更改的文本。** 此外，您还学习了**如何以编程方式比较 Word 文档中的书签**。您可以使用 [文档][22] 了解有关 Java API 的 GroupDocs.Comparison 的更多信息。如有任何歧义，请随时在 [论坛][23] 上与我们联系。

## 也可以看看

  * [比较 Java 中的图像以突出显示差异][24]
  * [使用 Java 比较库比较文本、Word 和 PDF 文件][25]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/compare-word-documents-and-highlight-differences-using-java.jpg
 [2]: #java-comparison-api
 [3]: #Compare-Word-Documents-using-Java
 [4]: #Get-Changes-Text-using-Java
 [5]: #Compare-Bookmarks-in-Word-Documents-using-Java
 [6]: https://products.groupdocs.com/comparison/java
 [7]: https://docs.fileformat.com/word-processing/docx/
 [8]: https://downloads.groupdocs.com/comparison/java
 [9]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer
 [10]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#add(java.nio.file.Path)
 [11]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#Comparer(java.lang.String)
 [12]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/source-and-target-word-documents.jpg
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/result.jpg
 [14]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#getChanges()
 [15]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison.result/ChangeInfo
 [16]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison.result/ChangeInfo#getText()
 [17]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison.options/CompareOptions
 [18]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison.options/CompareOptions#setCompareBookmarks(boolean)
 [19]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#compare(java.lang.String,%20com.groupdocs.comparison.options.CompareOptions)
 [20]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/Compare-Bookmarks-in-Word-Documents-using-Java.jpg
 [21]: https://purchase.groupdocs.com/temporary-license
 [22]: https://docs.groupdocs.com/comparison/java/
 [23]: https://forum.groupdocs.com/c/comparison/
 [24]: https://blog.groupdocs.com/2021/06/16/compare-images-in-java/
 [25]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/








