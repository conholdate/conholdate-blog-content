---
title: "使用 Java 合并 Word 文档"
author: Muzammil Khan
date: 2021-06-21T15:26:55+00:00
summary: "作为 Java 开发人员，您可以在 Java 应用程序中轻松合并两个或多个 Word 文档或合并来自不同 Word 文件的页面。在本文中，您将学习**如何使用 Java 合并 Word 文档**。"
url: /zh/2021/06/21/merge-word-documents-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 Java 合并 Word 文件"
  - "使用 Java 合并 DOCX 文件"
  - "使用 Java 合并 Word 文档"
  - "将 Word 合并为 PDF"

---


{{< figure align=center src="images/Merge-Word-Documents-using-Java.jpg" alt="使用 Java 合并 Word 文档">}}
 

您可以以编程方式将两个或多个 Word 文档合并到一个文档中。作为 Java 开发人员，您可以轻松地将 Word 文档合并到 Java 应用程序中。在本文中，您将学习**如何使用 Java 合并 Word 文档**。

本文讨论/涵盖了以下主题：

  * [用于合并 Word 文档的 Java API][2]
  * [使用 Java 合并 Word 文档][3]
  * [使用 Java 组合 Word 文档的特定页面][4]
  * [使用 Java 使用密码进行合并和保护][5]
  * [使用 Java 将 Word 文档合并为 PDF][6]

## 用于合并 Word 文档的 Java API {#API-for-Merging-Word-Documents}

为了合并 [DOCX][7] 文件，我将使用 [GroupDocs.Merger for Java][8] API。它允许您开发高性能应用程序，可以在旅途中组合、翻录、随机播放、剪切或删除页面、幻灯片和图表。它使您能够重新排序或替换文档页面、更改页面方向、管理文档密码并执行对支持的文件格式（如 Word、Excel、PDF 和 PowerPoint）轻松进行其他操作。

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
        <artifactId>groupdocs-merger</artifactId>
        <version>20.11</version> 
</dependency>
```

## 使用 Java 合并 Word 文档 {#Merge-Multiple-Word-Documents-using-Java}

您可以按照下面提到的简单步骤以编程方式轻松合并两个或多个 Word 文档：

  * 创建 **_[Merger][10]_** 类的实例
  * 指定输入 DOCX 文件的路径
  * 调用**_[join()][11]_**方法并指定目标DOCX文件的路径
  * 重复上述步骤，添加更多文件进行合并
  * 调用**_[save()][12]_**方法，保存合并文件

以下代码示例展示了如何使用 Java 合并多个 DOCX 文件。

```
// 初始化 API
Merger merger = new Merger("C:\\Files\\sample.docx");

// 合并文件
merger.join("C:\\Files\\sample2.docx");
merger.join("C:\\Files\\sample3.docx");

// 保存合并的文件
merger.save("C:\\Files\\output.docx");
```

{{< figure align=center src="images/Merge-Multiple-Word-Documents-using-Java-1024x457.jpg" alt="使用 Java 合并多个 Word 文档" caption="使用 Java 合并多个 Word 文档">}}
 

**[Merger][10]** 类是控制文档合并过程的主类。它提供了多种方法来加入、提取、删除和拆分文档页面。

**Merger** 类的 **[Join()][11]** 方法将两个或多个文档连接到一个文档中。它从文件路径或输入流中获取一个文档作为输入参数。您也可以提供 **JoinOptions**。

**Merger** 类的 **[save()][12]** 方法将生成的文档保存到提供的文件路径。您也可以将文档保存到 OutputStream。

## 使用 Java 组合 Word 文档的特定页面 {#Combine-Specific-Pages-of-Word-Documents-using-Java}

您可以按照下面提到的简单步骤以编程方式组合 Word 文档的特定页面：

  * 创建 **_[Merger][10]_** 类的实例
  * 指定输入 DOCX 文件的路径
  * 定义**_[JoinOptions][14]_**并设置开始和结束页码
  * 调用**_[join()][11]_**方法并指定目标DOCX文件的路径
  * 调用**_[save()][12]_**方法，保存合并文件

以下代码示例展示了如何使用 Java 组合选定的 Word 文档页面。

```
// 初始化 API
合并r merger = new 合并r("C:\\Files\\merger\\sample.docx");

// 定义连接选项
JoinOptions joinOptions = new JoinOptions(1, 2);

// 合并
merger.join("C:\\Files\\merger\\sample2.docx", joinOptions);

// 保存合并的文件
merger.save("C:\\Files\\merger\\output.docx");
```

**[JoinOptions][14]** 类提供了诸如起始页码、结束页码和加入文档的模式等选项。

## 使用 Java 使用密码进行合并和保护 {#Merge-and-Secure-with-Password-using-Java}

您可以合并两个或多个 Word 文档，然后按照下面提到的简单步骤以编程方式使用密码保护：

  * 创建 **_[Merger][10]_** 类的实例
  * 指定输入 DOCX 文件的路径
  * 调用**_[join()][11]_**方法并指定目标DOCX文件的路径
  * 重复上述步骤，添加更多文件进行合并
  * 使用 **_[AddPasswordOptions][15]_** 设置密码
  * 使用 _AddPasswordOptions_ 调用 **_[addPassword()][16]_** 方法
  * 调用**_[save()][12]_**方法保存受密码保护的合并文件

以下代码示例显示了如何合并多个 DOCX 文件，然后使用 Java 使用密码保护合并的文件。

```
// 初始化 API
Merger merger = new Merger("C:\\Files\\sample.docx");

// 合并文件
merger.join("C:\\Files\\sample2.docx");
merger.join("C:\\Files\\sample3.docx");

// 设置密码
AddPasswordOptions addOptions = new AddPasswordOptions("password");
merger.addPassword(addOptions);

// 保存合并的文件
merger.save("C:\\Files\\output.docx");
```

**[AddPasswordOptions][15]** 类提供了设置密码以保护文档的选项。

**Merger** 类的 **[addPassword()][16]** 方法获取 **AddPasswordOptions** 作为输入参数，并使用密码保护文档。

## 使用 Java 将 Word 文档合并为 PDF {#Merge-Word-Document-into-PDF-using-Java}

您可以按照以下提到的简单步骤，以编程方式将两个或多个 Word 文档合并为 PDF 文档：

  * 创建 **_[Merger][10]_** 类的实例
  * 指定输入 PDF 文件的路径
  * 调用**_[join()][11]_**方法并指定目标DOCX文件的路径
  * 调用**_[save()][12]_**方法，保存合并的PDF文件

以下代码示例展示了如何使用 Java 将 DOCX 文件合并为 PDF 文件。

```
// 初始化 API
Merger merger = new Merger("C:\\Files\\sample.pdf");

// 合并文件
merger.join("C:\\Files\\sample.docx");

// 保存合并的文件
merger.save("C:\\Files\\output.pdf");
```

## 获得免费许可证

您可以通过请求 [免费的临时许可证][17] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 Java 合并 Word 文档**。您可以使用 [文档][18] 了解有关 Java API 的 GroupDocs.Merger 的更多信息。如有任何歧义，请随时在 [论坛][19] 上与我们联系。

## 也可以看看

  * [使用 Java 将多种文件类型合并为一个文件][20]
  * [拆分或合并 PDF、PowerPoint、Excel、Word、Java 文档][21]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/06/Merge-Word-Documents-using-Java.jpg
 [2]: #API-for-Merging-Word-Documents
 [3]: #Merge-Multiple-Word-Documents-using-Java
 [4]: #Combine-Specific-Pages-of-Word-Documents-using-Java
 [5]: #Merge-and-Secure-with-Password-using-Java
 [6]: #Merge-Word-Document-into-PDF-using-Java
 [7]: https://docs.fileformat.com/word-processing/docx/
 [8]: https://products.groupdocs.com/merger/java
 [9]: https://downloads.groupdocs.com/merger/java
 [10]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
 [11]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#join(java.lang.String)
 [12]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/06/Merge-Multiple-Word-Documents-using-Java.jpg
 [14]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/JoinOptions
 [15]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/AddPasswordOptions
 [16]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#addPassword(com.groupdocs.merger.domain.options.interfaces.IAddPasswordOptions)
 [17]: https://purchase.groupdocs.com/temporary-license
 [18]: https://docs.groupdocs.com/merger/java/
 [19]: https://forum.groupdocs.com/c/merger/
 [20]: https://blog.groupdocs.com/2021/06/13/merge-multiple-file-types-using-java/
 [21]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/








