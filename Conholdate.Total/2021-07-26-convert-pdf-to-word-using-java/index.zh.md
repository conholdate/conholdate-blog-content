---
title: "使用 Java 将 PDF 转换为 Word"
author: Muzammil Khan
date: 2021-07-26T15:22:27+00:00
summary: "作为 Java 开发人员，您可以通过编程轻松地将 PDF 文档转换为 Word 文档（.docx 或 .doc）。本文将重点介绍**如何使用 Java 将 PDF 文档转换为 Word 文档**。"
url: /zh/2021/07/26/convert-pdf-to-word-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "将 PDF 转换为 DOCX"
  - "将 PDF 转换为 Word"
  - "使用 Java 转换 PDF"
  - "使用 Java 转换特定页面"
  - "GroupDocs.Conversion 对于 Java"

---


{{< figure align=center src="images/convert-pdf-to-word-using-java.jpg" alt="">}}
 

您可以在 Java 应用程序中以编程方式轻松地将 PDF 文档转换为 Word 文档 (_.docx _or_ .doc_)。当您需要编辑 PDF 文档的文本或可能需要应用文本格式时，这种转换很有用。在本文中，您将学习**如何使用 Java 将 PDF 转换为 Word**。

本文讨论/涵盖了以下主题：

  * [用于将 PDF 转换为 Word 的 Java API][2]
  * [使用 Java 将 PDF 转换为 Word][3]
  * [将 PDF 的特定页面转换为 Word][4]
  * [加载受密码保护的 PDF 并转换为 Word][5]

## 用于将 PDF 转换为 Word 的 Java API {#java-conversion-api}

我将使用 [GroupDocs.Conversion for Java API][6] 将 [PDF][7] 转换为 [DOCX][8]。该 API 为 Java 应用程序提供了一种快速、高效、可靠的文件转换解决方案，无需安装任何外部软件。它支持所有流行的商业文档格式之间的转换，例如 PDF、HTML、电子邮件、Word、Excel、PowerPoint、Project、Photoshop、CorelDraw、AutoCAD、光栅图像文件格式等等。它还允许您显示整个文档，或部分渲染它以加快处理速度。该 API 与所有 Java 版本兼容，并支持能够运行 Java 运行时的流行操作系统（Windows、Linux、macOS）。

### 下载并配置

您可以 [下载][9] API 的 JAR 或在您的基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置来尝试下面提到的代码示例。

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
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.7</version> 
</dependency>
```

## 使用 Java 将 PDF 转换为 Word {#convert-pdf-to-docx}

您可以按照以下简单步骤将 PDF 文档转换为 Word：

  1. 创建 _**[Converter][10]**_ 类的实例
  2. 提供输入文件路径
  3. 创建 [**_WordProcessingConvertOptions_**][11] 的实例
  4. 设置起始页码
  5. 提供要转换的总页数
  6. 设置输出文件格式
  7. 调用 _**[Convert()][12]**_ 方法以及输出文件路径和转换选项

以下代码示例展示了**如何使用 Java 将 PDF 文件转换为 Word 文档**。

```
// 创建转换器
Converter 转变er = new Converter("C:\\Files\\sample.pdf");

// 设置 Word 转换选项
WordProcessingConvertOptions options = new WordProcessingConvertOptions();
options.setPageNumber(1);
options.setPagesCount(1);
options.setFormat(WordProcessingFileType.Docx);

// 转变
转变er.转变("C:\\Files\\output.docx", options);
```

{{< figure align=center src="images/convert-pdf-to-docx-1024x549.jpg" alt="使用 Java 将 PDF 转换为 Word" caption="使用 Java 将 PDF 转换为 Word">}}
 

[Converter][10] 类是控制文档转换过程的主类。它提供了多种方法来转换支持的文件格式的文档。此类的 [Convert()][12] 方法转换源文档并采用两个输入参数，源文档的文件路径和 [ConvertOptions][14] 将特定源文档转换为所需的目标文件类型。

[WordProcessingConvertOptions][11] 类提供了转换为 WordProcessing 文件类型的选项。 _setPageNumber()_ 方法允许设置起始页码以开始转换。而 _setPagesCount()_ 方法定义了从定义的页码开始转换的总页数。此类的 setFormat() 方法使您可以设置转换后文档的输出格式。它将 [WordProcessingFileType][15] 枚举类型作为输入。

## 将 PDF 的特定页面转换为 Word {#convert-specific-pages-of-pdf-to-docx}

您可以按照以下简单步骤将 PDF 文档的特定页面转换为 Word：

  1. 创建 _**[Converter][10]**_ 类的实例
  2. 提供输入文件路径
  3. 创建 [**_WordProcessingConvertOptions_**][11] 的实例
  4. 设置要转换的页码列表
  5. 调用 _**[Convert()][12]**_ 方法以及输出文件路径和转换选项

以下代码示例展示了**如何使用 Java 将特定页面从 PDF 文件转换为 Word 文档**。

```
// 创建转换器
Converter 转变er = new Converter("C:\\Files\\sample.pdf");

// 定义 Word 转换选项
WordProcessingConvertOptions options = new WordProcessingConvertOptions();
options.setPages(Arrays.asList(2, 3));

// 转变
转变er.转变("C:\\Files\\output.docx", options);
```

[WordProcessingConvertOptions][11] 类提供 _setPages()_ 方法来转换源文档中以逗号分隔的列表中定义的特定页码。

## 加载受密码保护的 PDF 并转换为 Word {#convert-password-protected-pdf-to-docx}

您可以按照以下简单步骤将受密码保护的 PDF 文档转换为 Word：

  1. 创建 **_[PdfLoadOptions][16]_**
  2. 设置密码
  3. 创建 _**[Converter][10]**_ 类的实例
  4. 提供输入文件路径
  5. 创建 [**_WordProcessingConvertOptions_**][11] 的实例
  6. 调用 _**[Convert()][12]**_ 方法以及输出文件路径和转换选项

以下代码示例显示****如何使用 Java**** 将受密码保护的 PDF 文件转换为 Word 文档。

```
// PDF 加载选项
PdfLoadOptions loadOptions = new PdfLoadOptions();
loadOptions.setPassword("password");

// 创建转换器
Converter 转变er = new Converter("C:\\Files\\sample.pdf", loadOptions);

// 定义 Word 转换选项
WordProcessingConvertOptions options = new WordProcessingConvertOptions();

// 转变
转变er.转变("C:\\Files\\output.docx", options);
```

[PdfLoadOptions][16] 类提供了加载 PDF 文档的各种选项。此类的 _setPassword()_ 方法使您可以通过提供密码来解除受保护文档的保护。

您可以在文档中找到有关“[使用选项加载 PDF 文档][17]”的更多详细信息。

## 获得免费许可证

您可以通过请求 [免费的临时许可证][18] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 Java 将 PDF 文档转换为 Word**。您还学习了**如何将受密码保护的 PDF 文件转换为 Word 文档**。此外，您还学习了**如何以编程方式将特定页面从 PDF 转换为 Word 文档**。您可以使用 [文档][19] 了解有关 GroupDocs.Conversion Java API 的更多信息。如有任何歧义，请随时在 [论坛][20] 上与我们联系。

## 也可以看看

  * [][21][Convert Any Image to PDF in Java][22]
  * [在 Java 中将演示文稿转换为 PDF][23]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/07/convert-pdf-to-word-using-java.jpg
 [2]: #java-conversion-api
 [3]: #convert-pdf-to-docx
 [4]: #convert-specific-pages-of-pdf-to-docx
 [5]: #convert-password-protected-pdf-to-docx
 [6]: https://products.groupdocs.com/conversion/java
 [7]: https://docs.fileformat.com/pdf/
 [8]: https://docs.fileformat.com/word-processing/docx/
 [9]: https://downloads.groupdocs.com/conversion/java
 [10]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
 [11]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/WordProcessingConvertOptions
 [12]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/07/convert-pdf-to-docx.jpg
 [14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ConvertOptions
 [15]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.filetypes/WordProcessingFileType
 [16]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.load/PdfLoadOptions
 [17]: https://docs.groupdocs.com/conversion/java/load-pdf-document-with-options/
 [18]: https://purchase.groupdocs.com/temporary-license
 [19]: https://docs.groupdocs.com/conversion/java/
 [20]: https://forum.groupdocs.com/c/conversion/11
 [21]: https://blog.conholdate.com/2021/03/31/convert-pdf-to-excel-using-csharp/
 [22]: https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/
 [23]: https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/








