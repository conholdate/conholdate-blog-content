---
title: "使用 Java 将 HTML 转换为 PDF"
author: Muzammil Khan
date: 2021-09-10T13:37:34+00:00
summary: "作为 Java 开发人员，您可以轻松地将 HTML 文件或 HTML 网页从实时 URL 转换为 PDF 文档。在本文中，您将学习**如何使用 Java 将 HTML 转换为 PDF**。"
url: /zh/2021/09/10/convert-html-to-pdf-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "将 HTML 转换为 PDF"
  - "将 HTML 转换为 PDF in Java"
  - "将 HTML 网页转换为 PDF"
  - "HTML 到 PDF 转换 API"
  - "HTML 到 PDF 转换 Java API"

---


{{< figure align=center src="images/Convert-HTML-to-PDF.jpg" alt="使用 Java 将 HTML 转换为 PDF">}}
 

作为 Java 开发人员，您可以在 Java 应用程序中以编程方式轻松地将 HTML 文件或网页从实时 Web URL 转换为 PDF 文档。在本文中，您将学习**如何使用 Java 将 HTML 转换为 PDF**。

本文讨论/涵盖了以下主题：

  * [HTML 到 PDF 转换 Java API][2]
  * [使用 Java 将 HTML 转换为 PDF][3]
  * [使用高级选项将 HTML 转换为 PDF][4]
  * [从 URL 转换 HTML 到 PDF][5]
  * [将 HTML 的特定页面范围转换为 PDF][6]
  * [将 HTML 转换为 PDF 并添加水印][7]

## HTML 到 PDF 转换 Java API {#HTML-to-PDF-Conversion-Java-API}

为了将 [HTML][8] 转换为 [PDF][9]，我将使用 [GroupDocs.Conversion for Java API][10]。它是一种快速、高效、可靠的 Java 应用程序文件转换解决方案，无需安装任何外部软件。您可以在所有流行的商业文档格式之间进行转换，例如 PDF、HTML、电子邮件、Word、Excel、PowerPoint、Project、光栅图像文件格式等等。它还允许您显示整个文档，或部分渲染它以加快处理速度。该 API 与所有 Java 版本兼容，并支持能够运行 Java 运行时的流行操作系统（Windows、Linux、macOS）。

您可以 [下载][11] API 的 JAR 或在您的基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置来尝试下面提到的代码示例。

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

## 使用 Java 将 HTML 转换为 PDF {#Convert-HTML-to-PDF-using-Java}

您可以按照下面给出的简单步骤轻松地将 HTML 文件转换为 PDF 文档：

  1. 使用输入文件路径创建 _**[Converter][12]**_ 类的实例
  2. 创建 [**_PdfConvertOptions_**][13] 的实例
  3. 使用输出文件路径和转换选项调用 _**[convert()][14]**_ 方法

以下代码示例展示了**如何使用 Java 将 HTML 文档转换为 PDF 文档**。

```
// 初始化转换器
Converter 转变er = new Converter("C:\\Files\\sample.html");

// 定义 PDF 转换选项
PdfConvertOptions options = new PdfConvertOptions();

// 转变
转变er.转变("C:\\Files\\HtmlToPdf.pdf", options);
```

{{< figure align=center src="images/Convert-HTML-to-PDF-using-Java-1024x510.jpg" alt="使用 Java 将 HTML 转换为 PDF" caption="使用 Java 将 HTML 转换为 PDF">}}
 

[Converter][12] 类是控制文档转换过程的主要类。它提供了各种方法来满足转换请求。该类的 [convert()][14] 方法将源文档转换为指定的目标格式，并将转换后的文档保存在给定的文件路径中。它提供了几个重载的 _convert()_ 方法来转换支持的文件格式。

## 使用高级选项将 HTML 转换为 PDF {#Convert-HTML-to-PDF-with-Advanced-Options-using-Java}

您可以按照以下步骤在将 HTML 文件转换为 PDF 文档时使用一些高级设置：

  1. 使用输入文件路径创建 _**[Converter][12]**_ 类的实例
  2. 创建 [**_PdfConvertOptions_**][13] 的实例
  3. 设置各种选项，如_Rotation_、_Dpi_、_Width_、_Height_等。
  4. 使用输出文件路径和转换选项调用 _**[convert()][14]**_ 方法

以下代码示例展示了**如何使用高级设置将 HTML 文件转换为 PDF 文档。**

```
// 初始化转换器
Converter 转变er = new Converter("C:\\Files\\sample.html");

// 定义 PdfConvertOptions
PdfConvertOptions options = new PdfConvertOptions();
options.setPassword("12345");
options.setRotate(Rotation.On180);
options.setDpi(300);
options.setWidth(1024);
options.setHeight(768);

// 转变
转变er.转变("C:\\Files\\ConvertWithAdvancedOptions.pdf", options);
```

{{< figure align=center src="images/Convert-HTML-to-PDF-with-Advanced-Options-using-Java-1024x478.jpg" alt="使用 Java 使用高级选项将 HTML 转换为 PDF" caption="使用 Java 使用高级选项将 HTML 转换为 PDF">}}
 
[PdfConvertOptions][13] 类提供了几个选项来将指定的输入文件转换为 PDF 文档。我使用了以下选项：

  * [宽度][17] — the setWidth() property sets the image width after conversion
  * [高度][18] — the setHeight() property sets the desired image height after conversion
  * [Dpi][19] — the setDpi() property sets the desired page DPI after conversion
  * [密码][20] — the setPassword() property protects the converted document with a password
  * [旋转][21] — the setRotate() property allows page rotation with the following available options: _None, On90, On180, On270_

您可以在文档中找到有关“[使用高级选项转换为 PDF][22]”的更多详细信息。

## 从 URL 转换 HTML 到 PDF {#HTML-to-PDF-Conversion-from-a-URL}

您可以按照以下步骤将 HTML 网页从实时 URL 转换为 PDF 文档：

  1. 提供输入流对象的 URL 并打开流
  2. 使用输入流对象创建 _**[Converter][12]**_ 类的实例
  3. 创建 [**_PdfConvertOptions_**][13] 的实例
  4. 使用输出文件路径和转换选项调用 _**[convert()][14]**_ 方法

以下代码示例展示了**如何使用 Java 将 HTML 从 Web URL 转换为 PDF 文档**。

```
// 输入流
InputStream stream = new URL("https://onlinebooks.library.upenn.edu/readers.html").openStream();

// 初始化转换器
Converter 转变er = new Converter(stream);

// 定义 PDF 转换选项
PdfConvertOptions options = new PdfConvertOptions();

// 转变
转变er.转变("C:\\Files\\LoadDocumentFromUrl.pdf", options);
```

## 将 HTML 的特定页面范围转换为 PDF {#Convert-Specific-Page-Range-of-HTML-to-PDF-using-Java}

您可以按照以下步骤将特定页面从多页 HTML 文档转换为 PDF 文档：

  1. 使用输入文件路径创建 _**[Converter][12]**_ 类的实例
  2. 创建 [**_PdfConvertOptions_**][13] 的实例
  3. 设置页码开始转换
  4. 设置页数以转换总页数
  5. 使用输出文件路径和转换选项调用 _**[convert()][14]**_ 方法

以下代码示例展示了**如何使用 Java 将特定页面从 HTML 转换为 PDF 文档**。

```
// 初始化转换器
Converter 转变er = new Converter("C:\\Files\\Conversion\\sample_2.html");

// 定义 PdfConvertOptions
PdfConvertOptions options = new PdfConvertOptions();
options.setPageNumber(2);
options.setPagesCount(1);

// 转变
转变er.转变("C:\\Files\\ConvertNConsecutivePages.pdf", options);
```

## 将 HTML 转换为 PDF 并添加水印 {#Convert-HTML-to-PDF-and-Add-Watermark-using-Java}

您可以按照以下步骤将 HTML 文件转换为带水印的 PDF 文档：

  1. 创建 _**[Converter][12]**_ 类的实例
  2. 向构造函数提供输入文件路径
  3. 创建 [**_PdfConvertOptions_**][13] 的实例
  4. 创建 **_[WatermarkOptions][23]_** 的实例
  5. 设置各种选项，例如_Text_、_Color_、_Width_、_Height_、_RotatationAngle_等。
  6. 使用输出文件路径和转换选项调用 _**[convert()][14]**_ 方法

以下代码示例展示了**如何使用 Java 将 HTML 文档转换为带水印的 PDF 文档**。

```
// 初始化转换器
Converter 转变er = new Converter("C:\\Files\\sample_2.html");

// 定义 PDF 转换选项
PdfConvertOptions options = new PdfConvertOptions();

// 定义水印选项
WatermarkOptions watermark = new WatermarkOptions();
watermark.setText("THIS IS A SAMPLE TEXT WATERMARK");
watermark.setColor(Color.red);
watermark.setTop(400);
watermark.setLeft(150);
watermark.getWatermarkFont().setBold(true);
watermark.setRotationAngle(30);
watermark.setWidth(1000);
watermark.setHeight(1000);
watermark.setBackground(false);
options.setWatermark(watermark);

// 转变
转变er.转变("C:\\Files\\HtmlToPDFAddWatermark.pdf", options);
```

{{< figure align=center src="images/Convert-HTML-to-PDF-and-Add-Watermark-using-Java-1024x485.jpg" alt="使用 Java 将 HTML 转换为 PDF 并添加水印" caption="使用 Java 将 HTML 转换为 PDF 并添加水印">}}
 

[WatermarkOptions][23] 类提供了几个选项来为转换后的文档添加水印。它使您可以在转换后的文档中添加文本或图像水印。

## 获得免费许可证

您可以通过请求 [免费的临时许可证][25] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 Java 将 HTML 转换为 PDF 文档**。您还学习了**如何在转换后的 PDF 文档中添加水印**。此外，您还学习了**如何使用高级 PDF 转换选项**以编程方式转换 HTML。本文还解释了**如何使用 Java 将 HTML 网页从实时 URL 转换为 PDF 文档**。您可以使用 [文档][26] 了解有关 GroupDocs.Conversion Java API 的更多信息。如有任何歧义，请随时在 [论坛][27] 上与我们联系。

## 也可以看看

  * [使用 Java 将 PDF 转换为 Word][28]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Convert-HTML-to-PDF.jpg
 [2]: #HTML-to-PDF-Conversion-Java-API
 [3]: #Convert-HTML-to-PDF-using-Java
 [4]: #Convert-HTML-to-PDF-with-Advanced-Options-using-Java
 [5]: #HTML-to-PDF-Conversion-from-a-URL
 [6]: #Convert-Specific-Page-Range-of-HTML-to-PDF-using-Java
 [7]: #Convert-HTML-to-PDF-and-Add-Watermark-using-Java
 [8]: https://docs.fileformat.com/web/html/
 [9]: https://docs.fileformat.com/pdf/
 [10]: https://products.groupdocs.com/conversion/java
 [11]: https://downloads.groupdocs.com/conversion/java
 [12]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
 [13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/PdfConvertOptions
 [14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Convert-HTML-to-PDF-using-Java.jpg
 [16]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Convert-HTML-to-PDF-with-Advanced-Options-using-Java.jpg
 [17]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions#setWidth(int)
 [18]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions#setHeight(int)
 [19]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions#setDpi(double)
 [20]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions#setPassword(java.lang.String)
 [21]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions#setRotate(com.groupdocs.conversion.options.convert.Rotation)
 [22]: https://docs.groupdocs.com/conversion/java/convert-to-pdf-with-advanced-options/
 [23]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/WatermarkOptions
 [24]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Convert-HTML-to-PDF-and-Add-Watermark-using-Java.jpg
 [25]: https://purchase.groupdocs.com/temporary-license
 [26]: https://docs.groupdocs.com/conversion/java/
 [27]: https://forum.groupdocs.com/c/conversion/11
 [28]: https://blog.conholdate.com/2021/07/26/convert-pdf-to-word-using-java/








