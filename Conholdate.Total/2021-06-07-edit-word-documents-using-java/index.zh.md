---
title: "使用 Java 编辑 Word 文档"
author: Muzammil Khan
date: 2021-06-07T10:47:00+00:00
summary: "您可以轻松地以编程方式编辑 Word 文档（DOC、DOCX 或 DOTM）。在本文中，您将学习**如何使用 Java 编辑 Word 文档**。"
url: /zh/2021/06/07/edit-word-documents-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 Java 编辑 DOCX"
  - "使用 Java 编辑 Word 文档"
  - "GroupDocs.Editor 对于 Java"
  - "GroupDocs.Editor 产品系列"

---


{{< figure align=center src="images/Edit-docx-documents-using-Java.jpg" alt="使用 Java 编辑 Word DOCX">}}
 

您可以轻松地以编程方式编辑所有文字处理文档格式，例如 DOC、DOCX 或 DOTM。作为 Java 开发人员，您可以在 Java 应用程序中编辑 Word 文档。在本文中，您将学习**如何使用 Java 编辑 Word 文档**。

本文讨论/涵盖了以下主题：

  * [用于编辑 Word 文档的 Java API][2]
  * [使用 Java 编辑 Word 文档][3]

## 用于编辑 Word 文档的 Java API {#api-for-editing-word-documents}

为了编辑 [DOCX][4] 文件，我将使用 [GroupDocs.Editor for Java][5] API。它允许您以编程方式编辑文字处理文档、Excel 工作表或其他受支持格式的文档。该 API 使您能够加载文档并将其转换为 HTML。它将 HTML 提供给外部 UI 进行编辑，然后在处理后将 HTML 保存到原始文档。

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
        <artifactId>groupdocs-editor</artifactId>
        <version>20.11.0</version> 
</dependency>
```

## 使用 Java 编辑 Word 文档 {#Edit-DOCX-using-Java}

您可以按照以下提到的简单步骤以编程方式轻松编辑 Word 文档：

  * 定义 **_[WordProcessingLoadOptions][7]_**
  * 创建 **_[Editor][8]_** 类的实例
  * 指定输入 DOCX 文件的路径
  * 定义 **_[WordProcessingEditOptions][9]_**
  * 调用**_[edit()][10]_**方法，获取**_[EditableDocument][11]_**对象
  * 从 **_EditableDocument_ 获取文档内容和相关资源
  * 调用 [_**getEmbeddedHtml()**_][12] 方法将文档获取为单个 base64 编码的字符串
  * 通过调用 _**replace()**_ 方法更新内容
  * 调用 **_[fromMarkup()][13]_** 方法并创建一个新的 EditableDocument 实例
  * 定义 [**_WordProcessingSaveOptions_**][14]
  * 调用 **_[save()][15]_** 方法并保存更新的文件
  * 处理对象

以下代码示例展示了如何使用 Java 编辑 DOCX 文件。

```
//输入文件
String inputFilePath = "C:\\Files\\Sample.docx";

//使用加载选项加载文档
WordProcessingLoadOptions wordLoadOptions = new WordProcessingLoadOptions();
wordLoadOptions.setPassword("some password"); // Password if required
Editor editor = new Editor(inputFilePath, wordLoadOptions);

// 指定编辑选项
WordProcessingEditOptions editOptions = new WordProcessingEditOptions();
editOptions.setEnableLanguageInformation(true);
editOptions.setEnablePagination(true);

//打开要编辑的输入文档
EditableDocument beforeEdit = editor.edit(editOptions);

//从可编辑文档中获取文档内容和相关资源
String content = beforeEdit.getContent();
List<IImageResource> images = beforeEdit.getImages();
List<FontResourceBase> fonts = beforeEdit.getFonts();
List<CssText> stylesheets = beforeEdit.getCss();

//将文档作为单个 base64 编码字符串获取，其中所有资源（图像、字体等）与主要文本内容一起嵌入到此字符串中
String allEmbeddedInsideString = beforeEdit.getEmbeddedHtml();
//编辑内容
String allEmbeddedInsideStringEdited = allEmbeddedInsideString.replace("Subtitle", "Edited subtitle");

//从编辑的内容和资源创建一个新的 EditableDocument 实例
EditableDocument afterEdit = EditableDocument.fromMarkup(allEmbeddedInsideStringEdited, null);

//输出文档路径
String outputPath = "C:\\Files\\Sample_output.docx";
//保存选项
WordProcessingSaveOptions saveOptions = new WordProcessingSaveOptions(WordProcessingFormats.Docx);
//最后，保存到路径
editor.save(afterEdit, outputPath, saveOptions);

//处置对象
beforeEdit.dispose();
afterEdit.dispose();
editor.dispose();
```

{{< figure align=center src="images/Edit-Word-Documents-using-Java-1024x457.jpg" alt="使用 Java 编辑 Word 文档" caption="使用 Java 编辑 Word 文档">}}
 

[WordprocessingLoadOptions][7] 类提供了将 Word 文档（如 DOC、DOCX、RTF、ODT 等）加载到 Editor 类的各种选项。

  * [setPassword][17] 方法允许指定打开受密码保护的文档的密码。

[Editor][8] 类是提供加载、编辑和保存所有可支持格式的文档的方法的主要类。

[WordProcesingEditOptions][9] 类使您能够指定用于打开要编辑的字处理文档的自定义选项。

  * [setEnabledLanguageInformation][18] 方法指定语言信息是否以'lang' HTML 属性的形式导出到 HTML 标记。
  * [setEnablePagination][19] 方法允许在生成的 HTML 文档中启用或禁用分页。

[EditableDocument][11] 类在内部存储文档并提供生成 HTML 标记和生成资源的方法。

[WordProcessingSaveOptions][14] 类提供了用于在编辑后生成和保存 Word 文档的自定义选项。

## 获得免费许可证

您可以通过请求 [免费的临时许可证][20] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 Java 编辑 Word 文档**。您可以使用 [文档][21] 了解有关 Java API 的 GroupDocs.Editor 的更多信息。如有任何歧义，请随时在 [论坛][22] 上与我们联系。

## 也可以看看

  * [使用 REST API 编辑 Word 文档或 Excel 表格][23]
  * [在 C# 中编辑 Word 文档 |构建您自己的 .NET Word 编辑器][24]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/06/Edit-docx-documents-using-Java.jpg
 [2]: #api-for-editing-word-documents
 [3]: #Edit-DOCX-using-Java
 [4]: https://docs.fileformat.com/word-processing/docx/
 [5]: https://products.groupdocs.com/editor/java
 [6]: https://downloads.groupdocs.com/editor/java
 [7]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor.options/WordProcessingLoadOptions
 [8]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor
 [9]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor.options/wordprocessingeditoptions
 [10]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#edit()
 [11]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument
 [12]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument#getEmbeddedHtml()
 [13]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument#fromMarkup(java.lang.String,%20java.util.List)
 [14]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor.options/WordProcessingSaveOptions
 [15]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#save(com.groupdocs.editor.EditableDocument,%20java.lang.String,%20com.groupdocs.editor.options.ISaveOptions)
 [16]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/06/Edit-Word-Documents-using-Java.jpg
 [17]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor.options/WordProcessingLoadOptions#setPassword(java.lang.String)
 [18]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor.options/WordProcessingEditOptions#setEnableLanguageInformation(boolean)
 [19]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor.options/WordProcessingEditOptions#setEnablePagination(boolean)
 [20]: https://purchase.groupdocs.com/temporary-license
 [21]: https://docs.groupdocs.com/editor/java/
 [22]: https://forum.groupdocs.com/c/editor/
 [23]: https://blog.groupdocs.cloud/2021/02/12/edit-word-or-excel-documents-using-rest-api/
 [24]: https://blog.groupdocs.com/2021/03/26/edit-word-documents-in-csharp/








