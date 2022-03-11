---
title: "使用 Java 使用数字签名对文档进行签名"
author: Muzammil Khan
date: 2021-04-23T07:09:03+00:00
summary: "在 Java 应用程序中以编程方式使用数字证书签署 PDF 或 Word 文档。本文将重点介绍**如何使用 Java 对带有数字签名的文档进行电子签名**。"
url: /zh/2021/04/23/sign-documents-with-digital-signatures-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 Java 对 PDF 进行数字签名"
  - "使用 Java 对 Word 文件进行数字签名"
  - "使用 Java 签署文档"
  - "使用数字证书签署文件"
  - "签署 PDF 文件"

---

{{< figure align=center src="images/Digitally-sign-PDF-using-Java-1.jpg" alt="">}}
 
数字签名是一种验证文档真实性的数学技术。对于文档，数字签名由带有私钥和公钥的证书表示。作为 Java 开发人员，您可以轻松地以编程方式使用数字证书对文档进行签名。本文将重点介绍**如何使用 Java 对带有数字签名的文档进行电子签名**。

本文讨论/涵盖了以下主题：

  * [用于签署文档的 Java API][2]
  * [使用 Java 使用数字签名签署 PDF 文档][3]
  * [使用 Java 使用数字签名对 Word 文档进行签名][4]

## 用于签署文档的 Java API {#api-for-signing-documents}

我将使用 [GroupDocs.Signature for Java][5] API 使用数字证书对文档进行签名。它可以帮助您开发 Java 应用程序以对 [支持的格式][6] 的数字文档进行电子签名。它还允许使用图像、二维码、条形码、元数据、文本和图章类型电子签名对图像和文档进行签名。

### 下载并配置

您可以 [下载][7] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置，以尝试以下代码示例。

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
        <artifactId>groupdocs-signature</artifactId>
        <version>20.9</version> 
</dependency>
```

## 使用 Java 使用数字签名签署 PDF 文档 {#sign-pdf-documents}

您可以按照以下提到的简单步骤使用数字签名对 PDF 文档进行电子签名：

  * 创建 _[Signature][8]_ 类的实例
  * 提供 PDF 文档的路径
  * 创建 _[DigitalSignOptions][9]_ 类的实例
  * 提供证书文件路径
  * 设置图片文件路径
  * 设置所需的符号选项，例如位置（上、左等）
  * 然后调用[_Sign_][10]方法对文档进行签名

以下代码示例显示了如何使用 Java 使用证书对 PDF 文档进行签名。

```
Signature signature = new Signature("sample.pdf");

// 定义数字签名选项  
DigitalSignOptions options = new DigitalSignOptions("Signature.pfx");
options.setImageFilePath("signature.jpg");
options.setLeft(100);
options.setTop(200);
options.setPageNumber(1);

// 签署文件归档
signature.sign("output.pdf", options);
```

{{< figure align=center src="images/Signed-PDF-1024x630.jpg" alt="使用 Java 使用数字证书签署 PDF 文档" caption="使用 Java 使用数字证书签署 PDF 文档">}}
 
[Signature][12] 类是控制文档签名过程的主要类。此类提供各种方法来签名、验证、更新和搜索签名。

[DigitalSignOptions][13] 类提供了各种方法来设置和获取表示数字签名的签名选项。

## 使用 Java 使用数字签名对 Word 文档进行签名 {#sign-word-documents}

您可以按照以下提到的简单步骤使用数字签名对您的 Word 文档进行电子签名：

  * 创建 _[Signature][8]_ 类的实例
  * 提供Word文件的路径
  * 创建 _[DigitalSignOptions][9]_ 类的实例
  * 提供证书文件路径
  * 设置图片文件路径
  * 设置所需的符号选项，例如位置（上、左等）
  * 然后调用_[Sign][10]_方法对文档进行签名

以下代码示例显示了如何使用 Java 使用证书对 DOCX 文件进行签名。

```
Signature signature = new Signature("sample.docx");

// 定义数字签名选项  
DigitalSignOptions options = new DigitalSignOptions("Signature.pfx");
options.setImageFilePath("signature.jpg");
options.setPassword("1234567890");
options.setReason("Approved");
options.setContact("John Smith");
options.setLocation("New York");
options.setAllPages(true);
options.setWidth(160);
options.setHeight(80);
options.setTop(400);
options.setLeft(100);

// 签署文件归档
signature.sign("output.docx", options);
```

{{< figure align=center src="images/Sign-DOCX-1024x582.jpg" alt="使用 Java 使用数字证书签署 Word 文档" caption="使用 Java 使用数字证书签署 Word 文档">}}
 
## 获得免费许可证

您可以通过请求 [免费的临时许可证][15] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 Java 使用数字签名对文档进行电子签名**。您可以使用 [文档][16] 了解有关 Java API 的 GroupDocs.Signature 的更多信息。如有任何歧义，请随时在 [论坛][17] 上与我们联系。

## 也可以看看

  * [使用 C# 使用数字证书签署文档][18]
  * [用Java生成二维码|签署文件和图像][19]
  * [在 Python 中使用 REST API 使用 QR 码签署 PDF 文档][20]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/Digitally-sign-PDF-using-Java-1.jpg
 [2]: #api-for-signing-documents
 [3]: #sign-pdf-documents
 [4]: #sign-word-documents
 [5]: https://products.groupdocs.com/signature/java
 [6]: https://docs.groupdocs.com/signature/java/supported-document-formats/
 [7]: https://downloads.groupdocs.com/signature/java
 [8]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature/Signature#Signature(java.lang.String)
 [9]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature.options.sign/DigitalSignOptions#DigitalSignOptions(java.lang.String)
 [10]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature/Signature#sign(java.lang.String,%20com.groupdocs.signature.options.sign.SignOptions)
 [11]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/Signed-PDF.jpg
 [12]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature/Signature
 [13]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature.options.sign/DigitalSignOptions
 [14]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/Sign-DOCX.jpg
 [15]: https://purchase.groupdocs.com/temporary-license
 [16]: https://docs.groupdocs.com/signature/java/
 [17]: https://forum.groupdocs.com/c/signature/
 [18]: https://blog.groupdocs.com/2021/03/11/sign-documents-with-digital-certificate-using-csharp/
 [19]: https://blog.groupdocs.com/2021/02/19/generate-qr-codes-in-java-to-sign-documents-and-images/
 [20]: https://blog.groupdocs.cloud/2021/03/06/sign-pdf-documents-with-qr-code-using-python/

