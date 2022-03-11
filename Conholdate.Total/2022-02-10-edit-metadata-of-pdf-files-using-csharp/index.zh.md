---
title: "'使用 C# 编辑 PDF 文件的元数据'"
author: Muzammil Khan
date: 2022-02-10T15:15:07+00:00
summary: "您可以通过编程方式在 PDF 文档中添加/编辑文档信息和 XMP 元数据。在本文中，您将学习**如何使用 C# 编辑 PDF 文件的元数据**。"
url: /zh/2022/02/10/edit-metadata-of-pdf-files-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "添加自定义 XMP 元数据 C#"
  - "在 C# 中获取文档信息"
  - "使用 C# 获取 XMP 元数据"
  - "读取自定义 XMP 元数据"
  - "读取自定义 XMP 元数据 C#"
  - "在 C# 中设置文档信息"
  - "使用 C# 设置 XMP 元数据"

---


{{< figure align=center src="images/edit-metadata-of-pdf-files-using-csharp.jpg" alt="使用 C# 编辑 PDF 文件的元数据">}}
 

元数据是由一组属性组成的特定数字文档的名片。这些属性包含有关文档的基本信息，例如标题、作者、主题、关键字等。可扩展元数据平台 (XMP) 是一种基于 XML 的格式，允许将文档元数据保存在键/值对中。我们可以通过编程方式在 PDF 文档中添加/编辑文档信息和 XMP 元数据。在本文中，我们将学习**如何使用 C# 编辑 PDF 文件的元数据**。

本文将涵盖以下主题：

  * [用于编辑 PDF 文件元数据的 C# API][2]
  * [编辑 PDF 文件的元数据][3]
  * [获取 PDF 文件的元数据][4]
  * [从 PDF 文件中获取 XMP 元数据][5]
  * [在 PDF 文件中设置 XMP 元数据][6]
  * [在 PDF 文件中自定义 XMP 元数据命名空间][7]

## 用于编辑 PDF 文件元数据的 C# API {#CSharp-API-to-Edit-Metadata-of-PDF-Files}

要编辑 [PDF][8] 文档中的元数据信息，我们将使用 [Aspose.PDF for .NET API][9]。它允许我们在不使用 Adobe Acrobat 的情况下生成、修改、转换、渲染、保护和打印 [支持的文档][10]。请[下载][11] API 的 DLL 或使用 [NuGet][12] 安装它。

```
PM> Install-Package Aspose.Pdf
```

## 在 C# 中编辑 PDF 文件的元数据 {#Edit-Metadata-of-a-PDF-File-in-CSharp}

我们可以使用表示 PDF 文档元信息的 **_[DocumentInfo][13]_** 类来编辑 PDF 文档信息。我们可以按照以下步骤设置各种预定义的**[properties][14]**：

  1. 首先，使用 [**_Document_**][15] 类加载 PDF 文档。
  2. 接下来，使用 _Document_ 类对象作为参数创建 **_[DocumentInfo][13]_** 类的实例。
  3. 然后，设置各种属性，例如_Author_、_CreationDate_、_Keywords_、_Subject_、_Title_ 等。
  4. 最后，使用 **_[Document.Save()][16]_** 方法保存 PDF 文件，并将输出文件路径作为参数。

以下代码示例展示了**如何使用 C# 编辑 PDF 文件的元数据**。

```
// 此代码示例演示了如何设置 PDF 文档的基本信息。
// 打开文档
Document pdfDocument = new Document("C:\\Files\\PDF\\sample.pdf");

// 初始化 DocumentInfo 对象
DocumentInfo docInfo = new DocumentInfo(pdfDocument);

// 指定文档信息属性
docInfo.Author = "Aspose";
docInfo.CreationDate = DateTime.Now;
docInfo.Keywords = "Aspose.Pdf, DOM, API";
docInfo.ModDate = DateTime.Now;
docInfo.Subject = "PDF Information";
docInfo.Title = "Setting PDF Document Information";

// 保存文档
pdfDocument.Save("C:\\Files\\PDF\\sample_metadata.pdf");
```

{{< figure align=center src="images/Edit-Metadata-of-a-PDF-File-in-CSharp-1024x940.jpg" alt="在 C# 中编辑 PDF 文件的元数据。" caption="在 C# 中编辑 PDF 文件的元数据。">}}
 

## 使用 C# 获取 PDF 文件的元数据 {#Get-Metadata-of-a-PDF-File-using-CSharp}

我们可以按照以下步骤阅读PDF文档的基本信息****：

  1. 首先，使用 [**_Document_**][15] 类加载 PDF 文档。
  2. 接下来，使用 _Document_ 类对象作为参数创建 **_[DocumentInfo][13]_** 类的实例。
  3. 最后，通过读取元数据属性的值来显示文档信息。

以下代码示例展示了**如何使用 C# 获取 PDF 文件的元数据**。

```
// 此代码示例演示如何获取 PDF 文档的基本信息。
// 打开文档
Document pdfDocument = new Document("C:\\Files\\PDF\\sample_metadata.pdf");

// 获取文档信息
DocumentInfo docInfo = pdfDocument.Info;

// 显示文档信息
Console.WriteLine("Author: {0}", docInfo.Author);
Console.WriteLine("Creation Date: {0}", docInfo.CreationDate);
Console.WriteLine("Keywords: {0}", docInfo.Keywords);
Console.WriteLine("Modify Date: {0}", docInfo.ModDate);
Console.WriteLine("Subject: {0}", docInfo.Subject);
Console.WriteLine("Title: {0}", docInfo.Title);
```

```
Author: Aspose
Creation Date: 2/9/2022 9:47:00 AM
Keywords: Aspose.Pdf, DOM, API
Modify Date: 2/9/2022 9:47:00 AM
Subject: PDF Information
Title: Setting PDF Document Information
```

## 使用 C# 获取 PDF 文件的 XMP 元数据 {#Get-XMP-Metadata-of-a-PDF-File-using-CSharp}

我们可以按照以下步骤读取 PDF 文档的 XMP 元数据****：

  1. 首先，使用 [**_Document_**][15] 类加载 PDF 文档。
  2. 最后，读取 [**_Metadata_**][18] 属性并提取信息。

以下代码示例显示**如何使用 C# 获取 PDF 文件的 XMP 元数据**。

```
// 此代码示例演示如何获取 PDF 文档的 XMP 元数据。
// 打开文档
Document pdfDocument = new Document("C:\\Files\\PDF\\sample_xmp.pdf");

// 显示 XMP 信息
Console.WriteLine("xmp:CreateDate : " + pdfDocument.Metadata["xmp:CreateDate"]);
Console.WriteLine("xmp:Nickname : " + pdfDocument.Metadata["xmp:Nickname"]);
Console.WriteLine("xmp:CustomProperty : " + pdfDocument.Metadata["xmp:CustomProperty"]);
```

```
xmp:CreateDate: 2022-02-09T08:57:00.7+05:00
xmp:Nickname: Nickname
xmp:CustomProperty: Custom Value
```

## 使用 C# 在 PDF 文件中设置 XMP 元数据 {#Set-XMP-Metadata-in-a-PDF-File-using-CSharp}

我们可以使用 **_[Document][19]_** 类的 **_[Metadata][18]_** 属性在 PDF 文件中设置 XMP 元数据，步骤如下：

  1. 首先，使用 [**_Document_**][15] 类加载 PDF 文档。
  2. 接下来，使用 [**_Metadata_**][18] 属性设置元数据值。
  3. 最后，使用 **_[Document.Save()][16]_** 方法保存 PDF 文件，并将输出文件路径作为参数。

以下代码示例展示了**如何使用 C# 设置 PDF 文件的 XMP 元数据**。

```
// 此代码示例演示如何设置 PDF 文档的 XMP 元数据。
// 打开文档
Document pdfDocument = new Document("C:\\Files\\PDF\\sample.pdf");

// 设置属性
pdfDocument.Metadata["xmp:CreateDate"] = DateTime.Now;
pdfDocument.Metadata["xmp:Nickname"] = "Nickname";
pdfDocument.Metadata["xmp:CustomProperty"] = "Custom Value";

// 保存文档
pdfDocument.Save("C:\\Files\\PDF\\sample_xmp.pdf");
```

## 在 PDF 文件中自定义 XMP 元数据命名空间 {#Customize-XMP-Metadata-Namespace-in-a-PDF-File}

Adobe XMP 规范定义了我们通常使用的以下四 (4) 个核心命名空间：

  1. [都柏林核心][20] 命名空间 URI 为“[http://purl.org/dc/elements/1.1/][21]”，其首选命名空间前缀为“dc”。
  2. [XMP][22] 的命名空间 URI 为 http://ns.adobe.com/xap/1.0/，其首选命名空间前缀为“xmp”。
  3. [XMP 权限管理][24]，命名空间 URI 为 http://ns.adobe.com/xap/1.0/rights/，其首选命名空间前缀为“xmpRights”。
  4. [XMP 媒体管理][26] 命名空间 URI 为 http://ns.adobe.com/xap/1.0/mm/，其首选命名空间前缀为“xmpMM”。

我们还可以在 PDF 文件中设置自定义命名空间 URI，而不是定义 XMP 规范。为此，API 在 **_[Metadata][29]_** 类中提供了 **_[RegisterNamespaceUri][28]_** 方法。我们可以按照以下步骤创建一个带有前缀的新元数据命名空间：

  1. 首先，使用 [**_Document_**][15] 类加载 PDF 文档。
  2. 接下来，使用前缀和命名空间 URI 作为参数调用 **_RegisterNamespaceUri_** 方法。
  3. 然后，使用 [**_Metadata_**][18] 属性设置元数据值。
  4. 最后，使用 **_[Document.Save()][16]_** 方法保存 PDF 文件，并将输出文件路径作为参数。

以下代码示例展示了**如何使用 C#** 在 PDF 文件中设置自定义元数据命名空间。

```
// 此代码示例演示如何在 PDF 文档中设置自定义命名空间 URI。
// 打开文档
Document pdfDocument = new Document("C:\\Files\\PDF\\sample.pdf");

// 设置属性
pdfDocument.Metadata.RegisterNamespaceUri("myown", "http:// myown.xyz.com/xap/1.0/");
pdfDocument.Metadata["myown:ModifyDate"] = DateTime.Now;
pdfDocument.Metadata["myown:CreateDate"] = DateTime.Now;
pdfDocument.Metadata["myown:DeveloperName"] = "Developer Name";
pdfDocument.Metadata["myown:MyProperty"] = "My Custom Value";


// 保存文档
pdfDocument.Save("C:\\Files\\PDF\\sample_myown.pdf");
```

我们可以按照前面提到的步骤来读取自定义的 XMP 元数据属性。

```
myown:ModifyDate: 2022-02-09T10:38:26.8+05:00
myown:CreateDate: 2022-02-09T10:38:26.8+05:00
myown:DeveloperName: Developer Name
myown:MyProperty: My Custom Value
```

## 获取免费 API 许可证 {#Get-a-Free-License}

您可以通过请求 [免费的临时许可证][30] 来试用该 API，而不受评估限制。

## 结论

在本文中，我们学习了如何：

  * 使用 C# 添加/编辑 PDF 文档的基本信息；
  * 使用 C# 设置/获取 PDF 文件中的 XMP 元数据；
  * 使用前缀设置自定义元数据命名空间 URI。

此外，您可以使用 [文档][31] 了解更多关于 Aspose.PDF for .NET API 的信息。如有任何歧义，请随时在 [论坛][32] 上与我们联系。

## 也可以看看

  * [使用 C# 在 PDF 中添加页眉和页脚][33]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/edit-metadata-of-pdf-files-using-csharp.jpg
 [2]: #CSharp-API-to-Edit-Metadata-of-PDF-Files
 [3]: #Edit-Metadata-of-a-PDF-File-in-CSharp
 [4]: #Get-Metadata-of-a-PDF-File-using-CSharp
 [5]: #Get-XMP-Metadata-of-a-PDF-File-using-CSharp
 [6]: #Set-XMP-Metadata-in-a-PDF-File-using-CSharp
 [7]: #Customize-XMP-Metadata-Namespace-in-a-PDF-File
 [8]: https://docs.fileformat.com/pdf/
 [9]: https://products.aspose.com/pdf/net/
 [10]: https://docs.aspose.com/pdf/net/supported-file-formats/
 [11]: https://downloads.aspose.com/pdf/net
 [12]: https://www.nuget.org/packages/aspose.pdf
 [13]: https://apireference.aspose.com/pdf/net/aspose.pdf/documentinfo
 [14]: https://apireference.aspose.com/pdf/net/aspose.pdf/documentinfo/properties/index
 [15]: https://apireference.aspose.com/pdf/net/aspose.pdf/document
 [16]: https://apireference.aspose.com/pdf/net/aspose.pdf.document/save/methods/4
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Edit-Metadata-of-a-PDF-File-in-CSharp.jpg
 [18]: https://apireference.aspose.com/pdf/net/aspose.pdf/document/properties/metadata
 [19]: https://apireference.aspose.com/pdf/net/aspose.pdf/document/
 [20]: https://wwwimages2.adobe.com/content/dam/acom/en/devnet/xmp/pdfs/XMP%20SDK%20Release%20cc-2016-08/XMPSpecificationPart1.pdf#G5.785800
 [21]: http://purl.org/dc/elements/1.1/%22
 [22]: https://wwwimages2.adobe.com/content/dam/acom/en/devnet/xmp/pdfs/XMP%20SDK%20Release%20cc-2016-08/XMPSpecificationPart1.pdf#G5.810413
 [23]: http://ns.adobe.com/xap/1.0/%22
 [24]: https://wwwimages2.adobe.com/content/dam/acom/en/devnet/xmp/pdfs/XMP%20SDK%20Release%20cc-2016-08/XMPSpecificationPart1.pdf#G5.802526
 [25]: http://ns.adobe.com/xap/1.0/rights/%22
 [26]: https://wwwimages2.adobe.com/content/dam/acom/en/devnet/xmp/pdfs/XMP%20SDK%20Release%20cc-2016-08/XMPSpecificationPart1.pdf#G5.785832
 [27]: http://ns.adobe.com/xap/1.0/mm/%22
 [28]: https://apireference.aspose.com/pdf/net/aspose.pdf/metadata/methods/registernamespaceuri
 [29]: https://apireference.aspose.com/pdf/net/aspose.pdf/metadata
 [30]: https://purchase.conholdate.com/temporary-license
 [31]: https://docs.aspose.com/pdf/net
 [32]: https://forum.aspose.com/c/pdf/10
 [33]: https://blog.conholdate.com/2021/12/15/add-headers-and-footers-in-pdf-using-csharp/







