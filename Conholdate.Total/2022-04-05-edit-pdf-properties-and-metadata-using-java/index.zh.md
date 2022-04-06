---
title: "'使用 Java 编辑 PDF 属性和元数据'"
author: Muzammil Khan
date: 2022-04-05T15:15:07+00:00
summary: "您可以通过编程方式添加/编辑和读取 PDF 文档的文档信息和 XMP 元数据。在本文中，您将学习**如何使用 Java 编辑 PDF 属性和元数据**。"
url: /zh/2022/04/05/edit-pdf-properties-and-metadata-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "添加自定义 XMP 元数据 Java"
  - "在 Java 中获取文档信息"
  - "使用 Java 获取 XMP 元数据"
  - "读取自定义 XMP 元数据"
  - "读取自定义 XMP 元数据 Java"
  - "在 Java 中设置文档信息"
  - "使用 Java 设置 XMP 元数据"
  - "Java 中的 PDF 属性"
---

{{< figure align=center src="images/edit-pdf-properties-and-metadata-using-java.jpg" alt="使用 Java 编辑 PDF 文件的元数据">}}

文档的元数据以标题、作者、主题、关键字等属性的形式包含有关文档的基本信息。可扩展元数据平台 (XMP) 是一种基于 XML 的标准，用于将文档元数据存储为键/值一对。我们可以通过编程方式添加、编辑或读取 PDF 文档的文档信息和 XMP 元数据。在本文中，我们将学习**如何使用 Java 编辑 PDF 属性和元数据**。

本文将涵盖以下主题：

  * [用于编辑 PDF 属性和元数据的 Java API][1]
  * [使用 Java 编辑 PDF 属性][2]
  * [使用 Java 读取 PDF 属性][3]
  * [从 PDF 文件中获取 XMP 元数据][4]
  * [在 PDF 文件中设置 XMP 元数据][5]
  * [在 PDF 文件中自定义 XMP 元数据命名空间][6]

## 用于编辑 PDF 属性和元数据的 Java API {#Java-API-to-Edit-PDF-Properties-and-Metadata}

要编辑 [PDF][7] 属性和元数据信息，我们将使用 [Aspose.PDF for Java API][8]。它允许我们在不使用 Adobe Acrobat 的情况下生成、修改、转换、渲染、保护和打印 [支持的文档][9]。请[下载][10] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 _pom.xml_ 配置。

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
    <version>22.3</version>
</dependency>
```

## 使用 Java 编辑 PDF 属性 {#Edit-PDF-Properties-using-Java}

我们可以使用表示 PDF 文档元信息的 **_[PdfFileInfo][11]_** 类来编辑 PDF 文档信息。我们可以按照以下步骤设置各种预定义属性：

  1. 首先，使用 _**[PdfFileInfo][11]**_ 类加载 PDF 文档。
  2. 设置各种属性，例如_Author_、_Creator_、_Keywords_、_Subject_、_Title_等。
  4. 最后，使用 **_[saveNewInfo()][12]_** 方法保存 PDF 文件，并将输出文件路径作为参数。

以下代码示例展示了**如何使用 Java 编辑 PDF 文件的元属性**。

```
// 此代码示例演示了如何设置 PDF 文档的基本信息。
// 开源文档
PdfFileInfo fileInfo = new PdfFileInfo("D:\\Files\\PDF\\sample.pdf");

// 设置PDF信息
fileInfo.setAuthor("Aspose");
fileInfo.setTitle("Editing Metadata");
fileInfo.setKeywords("Aspose.Pdf, DOM, API");
fileInfo.setSubject("PDF Information");
fileInfo.setCreator("Aspose");

// 保存更新的文件
fileInfo.saveNewInfo("D:\\Files\\PDF\\Updated_Info_output.pdf");
```

{{< figure align=center src="images/Edit-PDF-Properties-using-Java.jpg" alt="用 Java 编辑 PDF 文件的元属性。" caption="用 Java 编辑 PDF 文件的元属性。">}}
 

## 使用 Java 读取 PDF 属性 {#Read-PDF-Properties-using-Java}

我们可以按照以下步骤阅读PDF文档的基本信息：

  1. 首先，使用 _**[PdfFileInfo][11]**_ 类加载 PDF 文档。
  2. 最后，通过读取元属性的值来显示文档信息。

以下代码示例展示了**如何使用 Java 获取 PDF 文件的元属性**。

```
// 此代码示例演示如何获取 PDF 文档的基本信息。
// 打开文档
PdfFileInfo fileInfo = new PdfFileInfo("D:\\Files\\PDF\\Updated_Info_output.pdf");

// 获取 PDF 信息
System.out.println("Subject :" + fileInfo.getSubject());
System.out.println("Title :" + fileInfo.getTitle());
System.out.println("Keywords :" + fileInfo.getKeywords());
System.out.println("Creator :" + fileInfo.getCreator());
System.out.println("Creation Date :" + fileInfo.getCreationDate());
System.out.println("Modification Date :" + fileInfo.getModDate());

// 查找它是否是有效的 PDF 并且它是否也被加密
System.out.println("Is Valid PDF :" + fileInfo.isPdfFile());
// 如果文件被加密，您需要提供文件打开密码
// 作为 PdfFileInfo 构造函数的第二个参数
System.out.println("Is Encrypted :" + fileInfo.isEncrypted());
```

```
Subject :PDF Information
Title :Editing Metadata
Keywords :Aspose.Pdf, DOM, API
Creator :Aspose
Creation Date :D:20170612160123-04'00'
Modification Date :D:20220405214422+05'00'
Is Valid PDF :true
Is Encrypted :false
```

## 用 Java 获取 PDF 文件的 XMP 元数据 {#Get-XMP-Metadata-of-a-PDF-File-in-Java}

我们可以按照以下步骤读取 PDF 文档的 XMP 元数据：

  1. 首先，使用 _**[Document][13]**_ 类加载 PDF 文档。
  2. 最后，使用 _**[Metadata][15]**_ 类的 _**[get_Item()][14]**_ 方法读取元数据并提取信息。

以下代码示例展示了**如何使用 Java 获取 PDF 文件的 XMP 元数据**。

```
// 此代码示例演示如何获取 PDF 文档的 XMP 元数据。
// 打开文档
Document pdfDocument = new Document("D:\\Files\\PDF\\SetXMPMetadata.pdf");

// 获取属性
System.out.println("xmp:CreateDate: " + pdfDocument.getMetadata().get_Item("xmp:CreateDate"));
System.out.println("xmp:Nickname: " + pdfDocument.getMetadata().get_Item("xmp:Nickname"));
System.out.println("xmp:CustomProperty: " + pdfDocument.getMetadata().get_Item("xmp:CustomProperty"));
```

```
xmp:CreateDate : 2022-04-05T10:05:24.4
xmp:Nickname : Nickname
xmp:CustomProperty : Custom Value
```

## 用 Java 在 PDF 文件中设置 XMP 元数据 {#Set-XMP-Metadata-in-a-PDF-File-in-Java}

我们可以按照以下步骤在 PDF 文件中设置 XMP 元数据：

  1. 首先，使用 _**[Document][13]**_ 类加载 PDF 文档。
  2. 接下来，使用 **_[Metadata][15]_** 类的 _**[set_Item()][16]**_ 方法设置元数据值。
  3. 最后，使用 _**[Document.save()][17]**_ 方法保存 PDF 文件，并将输出文件路径作为参数。

以下代码示例展示了**如何使用 Java 设置 PDF 文件的 XMP 元数据**。

```
// 此代码示例演示如何设置 PDF 文档的 XMP 元数据。
// 打开文档
Document pdfDocument = new Document("D:\\Files\\PDF\\sample.pdf");

// 设置属性
pdfDocument.getMetadata().set_Item("xmp:CreateDate", new XmpValue(new java.util.Date()));
pdfDocument.getMetadata().set_Item("xmp:Nickname", new XmpValue("Nickname"));
pdfDocument.getMetadata().set_Item("xmp:CustomProperty", new XmpValue("Custom Value"));

// 保存文档
pdfDocument.save("D:\\Files\\PDF\\SetXMPMetadata.pdf");
```

## 在 PDF 文件中自定义 XMP 元数据命名空间 {#Customize-XMP-Metadata-Namespace-in-a-PDF-File}

我们可以在 PDF 文件中设置自定义命名空间 URI，而不是定义 XMP 规范。为此，API 在 **_[Metadata][15]_** 类中提供了 **_[registerNamespaceUri][18]_** 方法。我们可以按照以下步骤创建一个带有前缀的新元数据命名空间：

  1. 首先，使用 [**_Document_**][13] 类加载 PDF 文档。
  2. 接下来，使用前缀和命名空间 URI 作为参数调用 **_registerNamespaceUri()_** 方法。
  3. 然后，使用 _**[set_Item()][16]**_ 方法设置元数据值。
  4. 最后，使用 **_[Document.Save()][17]_** 方法保存 PDF 文件，并将输出文件路径作为参数。

以下代码示例展示了**如何使用 Java 在 PDF 文件中设置自定义元数据命名空间**。

```
// 此代码示例演示如何设置 PDF 文档的自定义 XMP 元数据。
// 打开文档
Document pdfDocument = new Document("D:\\Files\\PDF\\sample.pdf");

// 设置自定义属性
pdfDocument.getMetadata().registerNamespaceUri("myown", "http:// myown.xyz.com/xap/1.0/");
pdfDocument.getMetadata().set_Item("myown:ModifyDate", new XmpValue(new java.util.Date()));
pdfDocument.getMetadata().set_Item("myown:CreateDate", new XmpValue(new java.util.Date()));
pdfDocument.getMetadata().set_Item("myown:DeveloperName", new XmpValue("Developer Name"));
pdfDocument.getMetadata().set_Item("myown:MyProperty", new XmpValue("My Custom Value"));

// 保存文档
pdfDocument.save("D:\\Files\\PDF\\CustomizedXMPMetadata.pdf");
```

我们可以按照前面提到的步骤读取自定义的 XMP 元数据属性。

```
NamespaceUri: http:// myown.xyz.com/xap/1.0/
myown:ModifyDate: 2022-04-05T10:18:45.9
myown:CreateDate: 2022-04-05T10:18:45.9
myown:DeveloperName: Developer Name
myown:MyProperty: My Custom Value
```

## 获取免费 API 许可证 {#Get-a-Free-License}

您可以通过请求 [免费的临时许可证][19] 来试用该 API，而不受评估限制。

## 结论

在本文中，我们学习了如何：

  * 使用Java添加/编辑PDF文档的基本信息；
  * 使用 Java 设置/获取 PDF 文件中的 XMP 元数据；
  * 使用前缀设置自定义元数据命名空间 URI。

此外，您可以使用 [documentation][20] 了解有关 Aspose.PDF for Java API 的更多信息。如有任何歧义，请随时在 [论坛][21] 上与我们联系。

## 也可以看看

  * [使用 Java 将 PDF 转换为 HTML][22]
  * [使用 Java 在 PDF 中添加脚注和尾注][23]

 [1]: #Java-API-to-Edit-PDF-Properties-and-Metadata
 [2]: #Edit-PDF-Properties-using-Java
 [3]: #Read-PDF-Properties-using-Java
 [4]: #Get-XMP-Metadata-of-a-PDF-File-in-Java
 [5]: #Set-XMP-Metadata-in-a-PDF-File-in-Java
 [6]: #Customize-XMP-Metadata-Namespace-in-a-PDF-File
 [7]: https://docs.fileformat.com/pdf/
 [8]: https://products.aspose.com/pdf/java/
 [9]: https://docs.aspose.com/pdf/java/supported-file-formats/
 [10]: https://downloads.aspose.com/pdf/java
 [11]: https://apireference.aspose.com/pdf/java/com.aspose.pdf.facades/PdfFileInfo
 [12]: https://apireference.aspose.com/pdf/java/com.aspose.pdf.facades/PdfFileInfo#saveNewInfo-java.lang.String-
 [13]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Document
 [14]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Metadata#get_Item-java.lang.String-
 [15]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Metadata
 [16]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Metadata#set_Item-java.lang.String-com.aspose.pdf.XmpValue-
 [17]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Document#save-java.lang.String-
 [18]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Metadata#registerNamespaceUri-java.lang.String-java.lang.String-
 [19]: https://purchase.conholdate.com/temporary-license
 [20]: https://docs.aspose.com/pdf/java
 [21]: https://forum.aspose.com/c/pdf/10
 [22]: https://blog.conholdate.com/2022/02/19/convert-pdf-to-html-using-java/
 [23]: https://blog.conholdate.com/2022/02/07/add-footnotes-and-endnotes-in-pdf-using-java/
