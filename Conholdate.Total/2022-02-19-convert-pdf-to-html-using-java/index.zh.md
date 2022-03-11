---
title: "使用 Java 将 PDF 转换为 HTML"
author: Muzammil Khan
date: 2022-02-19T17:14:51+00:00
summary: "您可以轻松地将 PDF 文档转换为 HTML 网页，以便在任何浏览器中查看它们。在本文中，**您将学习如何使用 Java 将 PDF 文档转换为 HTML 网页**。"
url: /zh/2022/02/19/convert-pdf-to-html-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "将 PDF 转换为 HTML"
  - "将 PDF 转换为 HTML Java API"
  - "GroupDocs.Conversion 对于 Java"
  - "Java PDF 转换器"
  - "PDF 转 HTML"
  - "PDF 转 HTML in Java"

---


{{< figure align=center src="images/convert-pdf-to-html-using-java.jpg" alt="使用 Java 将 PDF 转换为 HTML">}}
 

[PDF][2] 提供共享和打印只读文档而不会丢失文档格式。我们可以轻松地将 PDF 文档转换为 [HTML][3] 网页并在任何浏览器中查看。在本文中，我们将学习**如何使用 Java 将 PDF 文档转换为 HTML 网页**。

本文将涵盖以下主题：

  * [用于将 PDF 转换为 HTML 的 Java API — 免费下载][4]
  * [使用 Java 将 PDF 转换为 HTML][5]
  * [将页面范围从 PDF 转换为 HTML][6]
  * [将 PDF 的特定页面转换为 HTML][7]
  * [Java中受密码保护的PDF到HTML的转换][8]
  * [Java 中带水印的 PDF 到 HTML 转换][9]

## 用于将 PDF 转换为 HTML 的 Java API — 免费下载 {#Java-API-to-Convert-PDF-to-HTML—Free-Download}

为了将 PDF 转换为 HTML，我们将使用 [GroupDocs.Conversion for Java][10] API。它为最终用户提供快速、高效、可靠的文件转换解决方案。请[下载][11] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置。

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
        <version>21.10.1</version> 
</dependency>
```

## 使用 Java 将 PDF 转换为 HTML {#PDF-to-HTML-Conversion-using-Java}

我们可以按照下面给出的简单步骤，以编程方式轻松地将 PDF 文档转换为 HTML 网页：

  1. 首先，使用 **_[Converter][12]_** 类加载 PDF 文档。
  2. 接下来，创建 [**_MarkupConvertOptions_**][13] 类的实例。
  3. 然后，可选择设置各种转换选项，例如_FixedLayout_、_FixedLayoutShowBorders_等。
  4. 最后，使用 _**[Converter.Convert()][14]**_ 方法将 PDF 转换为 HTML。它将输出文件路径和转换选项作为参数。

以下代码示例展示了**如何使用 Java 将 PDF 文档转换为 HTML 网页**。

```
// 此代码示例演示如何将 PDF 文档转换为 HTML 文件。
// 初始化转换类对象
转变er converter = new 转变er("C:\\Files\\Conversion\\sample.pdf");

// 定义转换选项
Markup转变Options options = new Markup转变Options();
options.setFixedLayout(true);

// 转变
String outputFile =  "C:\\Files\\Conversion\\sample.html";
converter.convert(outputFile, options);
```

{{< figure align=center src="images/PDF-to-HTML-Conversion-using-Java-1024x512.jpg" alt="使用 Java 将 PDF 转换为 HTML" caption="使用 Java 将 PDF 转换为 HTML。">}}
 

## 将页面范围从 PDF 转换为 HTML {#Convert-Range-of-Pages-from-PDF-to-HTML}

我们可以按照以下步骤将 PDF 文档的一系列页面转换为 HTML：

  1. 首先，使用 **_[Converter][12]_** 类加载 PDF 文档。
  2. 接下来，创建 [**_MarkupConvertOptions_**][13] 类的实例。
  3. 然后，设置页码以开始转换。
  4. 之后，设置页数以转换总页数。
  5. 最后，使用 _**[Converter.Convert()][14]**_ 方法将 PDF 转换为 HTML。

以下代码示例展示了 ****如何使用 Java** 将 **一系列页面从 PDF 文档** 转换为 HTML 文件**。

```
// 此代码示例演示如何将一系列 PDF 页面转换为 HTML 文件。
// 初始化转换类对象
转变er converter = new 转变er("C:\\Files\\Conversion\\sample.pdf");

// 定义转换选项
Markup转变Options options = new Markup转变Options();
options.setPageNumber(1);	// Starting page number
options.setPagesCount(2);	// Total number of pages to convert

// 转变
String outputFile =  "C:\\Files\\Conversion\\sample_N_pages.html";
converter.convert(outputFile, options);
```

## 将 PDF 的特定页面转换为 HTML {#Convert-Specific-Pages-of-PDF-to-HTML}

我们可以按照以下步骤将 PDF 文档的特定页面转换为 HTML：

  1. 首先，使用 **_[Converter][12]_** 类加载 PDF 文档。
  2. 接下来，创建 [**_MarkupConvertOptions_**][13] 类的实例。
  3. 然后，在逗号分隔的列表中提供要转换的特定页码。
  4. 最后，使用 _**[Converter.Convert()][14]**_ 方法将 PDF 转换为 HTML。

以下代码示例展示了 ****如何使用 Java** 将 **PDF 文档的特定页面** 转换为 HTML 文件**。

```
// 此代码示例演示如何将 PDF 文档的特定页面转换为 HTML 文件。
// 初始化转换类对象
转变er converter = new 转变er("C:\\Files\\Conversion\\sample.pdf");

// 定义转换选项
Markup转变Options options = new Markup转变Options();
options.setPages(Arrays.asList( 1, 3)); // Page numbers to convert

// 转变
String outputFile =  "C:\\Files\\Conversion\\sample_pages.html";
converter.convert(outputFile, options);
```

## 在 Java 中将受密码保护的 PDF 转换为 HTML {#Convert-Password-Protected-PDF-to-HTML-in-Java}

我们还可以按照以下步骤将受密码保护的 PDF 文档转换为 HTML 网页：

  1. 首先，使用 _**[PdfLoadOptions ][16]**_ 类对象提供密码。
  2. 接下来，使用带有 _**PdfLoadOptions**_ 的 **_[Converter][12]_** 类加载 PDF 文档。
  3. 然后，创建 [**_MarkupConvertOptions_**][13] 类的实例。
  4. 最后，使用 _**[Converter.Convert()][14]**_ 方法将 PDF 转换为 HTML。

以下代码示例展示了**如何使用 Java 将受密码保护的 PDF 文档转换为 HTML 文档**。

```
// 此代码示例演示如何将受密码保护的 PDF 转换为 HTML。
// 定义负载选项
PdfLoadOptions loadOptions = new PdfLoadOptions();
loadOptions.setPassword("12345");

// 初始化转换类对象
转变er converter = new 转变er("C:\\Files\\Conversion\\sample.pdf", loadOptions);

// 定义转换选项
Markup转变Options options = new Markup转变Options();

// 转变
String outputFile =  "C:\\Files\\Conversion\\sample.html";
converter.convert(outputFile, options);
```

## Java 中带水印的 PDF 到 HTML 转换 {#PDF-to-HTML-Conversion-with-Watermark-in-Java}

我们可以按照以下步骤将 PDF 文档转换为 HTML 网页，并为转换后的 HTML 文件添加水印：

  1. 首先，使用 **_[Converter][12]_** 类加载 PDF 文档。
  2. 接下来，创建 _**[WatermarkOptions][17]**_ 类的实例。
  3. 然后，设置各种选项，例如_Text_、_Color_、_Width_、_Height_、_Font_等。
  4. 接下来，创建 [**_MarkupConvertOptions_**][13] 类的实例。
  5. 之后，将 _**WatermarkOptions**_ 分配给 **_MarkupConvertOptions_**。
  6. 最后，使用 _**[Converter.Convert()][14]**_ 方法将 PDF 转换为 HTML。

以下代码示例展示了**如何将 PDF 文档转换为带水印的 HTML 文档**。

```
// 此代码示例演示如何将 PDF 转换为带水印的 HTML。
// 初始化转换类对象
转变er converter = new 转变er("C:\\Files\\Conversion\\sample.pdf");

// 定义水印 
WatermarkOptions watermark = new WatermarkOptions();
watermark.setText("This is a Sample watermark");
watermark.setColor(Color.red);
watermark.setWidth(500);
watermark.setHeight(100);
watermark.setTop(0);
watermark.setLeft(300);
watermark.setBackground(true);

// 定义转换选项
Markup转变Options options = new Markup转变Options();
options.setWatermark(watermark);

// 输出文件路径
String outputFile =  "C:\\Files\\Conversion\\sampleWithWatermark.html";

// 转变
converter.convert(outputFile, options);
```

{{< figure align=center src="images/PDF-to-HTML-Conversion-with-Watermark-in-Java-1024x512.jpg" alt="Java 中带水印的 PDF 到 HTML 转换" caption="Java 中带水印的 PDF 到 HTML 转换。">}}
 

## 获得免费许可证

请通过请求 [免费的临时许可证][19] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了**如何使用 Java 将 PDF 文档转换为 HTML 网页**。我们还看到了**如何以编程方式将受密码保护的 PDF 文件转换为 HTML 并为转换后的文件添加水印**。此外，您可以使用 [documentation][20] 了解有关 Java API 的 GroupDocs.Conversion 的更多信息。如有任何歧义，请随时在 [论坛][21] 上与我们联系。

## 也可以看看

  * [使用 Java 将 HTML 转换为 PDF][22]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/convert-pdf-to-html-using-java.jpg
 [2]: https://docs.fileformat.com/pdf/
 [3]: https://docs.fileformat.com/web/html/
 [4]: #Java-API-to-Convert-PDF-to-HTML—Free-Download
 [5]: #PDF-to-HTML-Conversion-using-Java
 [6]: #Convert-Range-of-Pages-from-PDF-to-HTML
 [7]: #Convert-Specific-Pages-of-PDF-to-HTML
 [8]: #Convert-Password-Protected-PDF-to-HTML-in-Java
 [9]: #PDF-to-HTML-Conversion-with-Watermark-in-Java
 [10]: https://products.groupdocs.com/conversion/java
 [11]: https://downloads.groupdocs.com/conversion/java
 [12]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
 [13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/markupconvertoptions
 [14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/PDF-to-HTML-Conversion-using-Java.jpg
 [16]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.load/PdfLoadOptions
 [17]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/WatermarkOptions
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/PDF-to-HTML-Conversion-with-Watermark-in-Java.jpg
 [19]: https://purchase.conholdate.com/temporary-license
 [20]: https://docs.groupdocs.com/conversion/java/
 [21]: https://forum.groupdocs.com/c/conversion/11
 [22]: https://blog.conholdate.com/2021/09/10/convert-html-to-pdf-using-java/







