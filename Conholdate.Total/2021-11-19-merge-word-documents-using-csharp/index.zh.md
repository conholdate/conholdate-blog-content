---
title: "'使用 C# 合并 Word 文档'"
author: Muzammil Khan
date: 2021-11-19T03:48:57+00:00
summary: "作为 C# 开发人员，您可以通过编程轻松地将两个或多个 Word 文档合并到一个文档中。在本文中，您将学习**如何使用 C# 合并 Word 文档**。"
url: /zh/2021/11/19/merge-word-documents-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 CSharp 合并 Word 文件"
  - "使用 CSharp 合并 DOCX 文件"
  - "在 CSharp 中合并 Word 文档"
  - "将 Word 合并为 PDF"

---


{{< figure align=center src="images/Merge-Word-Documents-using-CSharp-1.jpg" alt="使用 C# 合并 Word 文档">}}
 

我们可以使用 C# 轻松地将两个或多个 Word 文档合并为一个文档。我们这样做是因为共享或打印单个文件比处理多个文件更容易。在本文中，我们将学习**如何使用 C# 合并 Word 文档**。

本文将涵盖以下主题：

  * [用于合并 Word 文档的 C# API][2]
  * [使用 C# 合并两个或多个 Word 文档][3]
  * [使用 C# 组合 Word 文档的特定页面][4]
  * [使用 C# 合并 DOCX 文件并使用密码保护][5]
  * [使用 C# 将 Word 文档合并为 PDF][6]

## 用于合并 Word 文档的 C# API {#CSharp-API-to-Merge-Word-Documents}

为了合并 [DOC][7] 或 [DOCX][8] 文件，我们将使用 [GroupDocs.Merger for .NET][9] API。请[下载][10] API 的 DLL 或使用 [NuGet][11] 安装它。

```
Install-Package GroupDocs.Merger
```

## 使用 C# 合并两个或多个 Word 文档 {#Merge-Two-or-More-Word-Documents-using-CSharp}

我们可以按照以下步骤轻松地以编程方式合并两个或多个 Word 文档：

  * 首先，使用 **_[Merger][12]_** 类加载 DOCX 文件。
  * 接下来，使用目标 DOCX 文件路径调用 **_[Merger.Join()][13]_** 方法与加载的文件合并。
  * 然后，重复上述步骤以合并更多文件。
  * 最后，使用输出文件路径调用**_[Merger.Save()][14]_**方法保存合并文件。

以下代码示例展示了如何使用 C# 合并两个或多个 DOCX 文件。

```
// 加载源 DOCX 文件
Merger merger = new Merger(@"C:\Files\sample.docx");

// 添加 DOCX 文件以与源 DOCX 合并
merger.Join(@"C:\Files\sample2.docx");

// 添加另一个 DOCX 文件以与源 DOCX 合并
merger.Join(@"C:\Files\sample3.docx");

// 合并 DOCX 文件并保存合并后的文件
merger.Save(@"C:\Files\merged.docx");
```

{{< figure align=center src="images/Merge-Word-Documents-using-CSharp-1024x365.jpg" alt="使用 C# 合并两个或多个 Word 文档" caption="使用 C# 合并两个或多个 Word 文档。">}}
 

## 使用 C# 组合 Word 文档的特定页面 {#Combine-Specific-Pages-of-Word-Documents-using-CSharp}

我们可以按照下面提到的简单步骤以编程方式组合 Word 文档的特定页面：

  * 首先，使用 **_[Merger][12]_** 类加载 DOCX 文件。
  * 接下来，使用起始页和结束页号创建 **_[JoinOptions][16]_ ** 类的实例。您还可以设置范围模式以从指定的页面范围加入奇数页或偶数页。
  * 然后，使用目标 DOCX 文件路径和 _JoinOptions_ 对象作为参数调用 _**[Merger.Join()][13]**_ 方法。 _JoinOptions_ 对象将目标文件的特定页面与源文件合并。
  * 最后，使用输出文件路径调用**_[Merger.Save()][14]_**方法保存合并文件。

以下代码示例显示了如何使用 C# 组合 Word 文档的选定页面。

```
// 加载源 DOCX 文件
Merger merger = new Merger(@"C:\Files\sample.docx");

// 定义连接选项
JoinOptions joinOptions = new JoinOptions(1, 4, RangeMode.OddPages);

// 添加 DOCX 文件以与源 DOCX 合并
merger.Join(@"C:\Files\sample2.docx", joinOptions);

// 合并 DOCX 文件并保存合并后的文件
merger.Save(@"C:\Files\merged.docx");
```

## 使用 C# 合并 DOCX 文件并使用密码保护 {#Merge-and-Secure-with-Password-using-CSharp}

我们可以合并两个或多个 DOCX 文件，然后按照下面给出的简单步骤以编程方式使用密码保护合并的文件：

  * 首先，使用 **_[Merger][12]_** 类加载 DOCX 文件。
  * 接下来，使用目标 DOCX 文件路径调用 **_[Merger.Join()][13]_** 方法与加载的文件合并。
  * 或者，重复上述步骤以合并更多文件。
  * 然后，使用 **_[AddPasswordOptions][17]_** 设置密码
  * 之后，使用 _AddPasswordOptions_ 调用 **_[Merger.AddPassword()][18]_** 方法。
  * 最后调用**_[Merger.Save()][14]_**方法保存密码保护的合并文件。

以下代码示例展示了如何合并多个 Word 文档，然后**使用 C# 使用密码保护合并的文件**。

```
// 加载源 DOCX 文件
Merger merger = new Merger(@"C:\Files\sample.docx");

// 添加 DOCX 文件以与源 DOCX 合并
merger.Join(@"C:\Files\sample2.docx");

// 设置密码
AddPasswordOptions addOptions = new AddPasswordOptions("password");
merger.AddPassword(addOptions);

// 合并 DOCX 文件并保存合并后的文件
merger.Save(@"C:\Files\merged.docx");
```

## 使用 C# 将 Word 文档合并为 PDF {#Merge-Word-Document-into-PDF-using-CSharp}

我们可以按照下面给出的简单步骤，以编程方式将 Word 文档合并为 PDF 文档：

  * 首先，使用 **_[Merger][12]_** 类加载 PDF 文件。
  * 接下来，使用目标 DOCX 文件路径调用 **_[Merger.Join()][13]_** 方法与加载的文件合并。
  * 或者，重复上述步骤以合并更多文件。
  * 最后，使用输出PDF文件路径调用**_[Merger.Save()][14]_**方法保存合并文件。

以下代码示例展示了**如何使用 C# 将 DOCX 文件合并到 PDF 文件中**。

```
// 加载源 PDF 文件
Merger merger = new Merger(@"C:\Files\sample.pdf");

// 添加 DOCX 文件以与源 PDF 合并
merger.Join(@"C:\Files\sample.docx");

// 合并 DOCX 文件并保存合并的 PDF
merger.Save(@"C:\Files\merged.pdf");
```

## 获得免费许可证

请通过请求 [免费的临时许可证][19] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了**如何使用 C# 合并两个或多个 Word 文档**。我们还看到了**如何以编程方式组合 Word 文档的特定页面**。本文还介绍了如何使用 C# 将 DOCX 文件合并为 PDF 文件。此外，您可以使用 [documentation][20] 了解更多关于 GroupDocs.Merger for .NET API 的信息。如有任何歧义，请随时在 [论坛][21] 上与我们联系。

## 也可以看看

  * [使用 C# 将多种文件类型合并为一个文件][22]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/Merge-Word-Documents-using-CSharp-1.jpg
 [2]: #CSharp-API-to-Merge-Word-Documents
 [3]: #Merge-Two-or-More-Word-Documents-using-CSharp
 [4]: #Combine-Specific-Pages-of-Word-Documents-using-CSharp
 [5]: #Merge-and-Secure-with-Password-using-CSharp
 [6]: #Merge-Word-Document-into-PDF-using-CSharp
 [7]: https://docs.fileformat.com/word-processing/doc/
 [8]: https://docs.fileformat.com/word-processing/docx/
 [9]: https://products.groupdocs.com/merger/net
 [10]: https://downloads.groupdocs.com/merger/net
 [11]: https://www.nuget.org/packages/groupdocs.merger
 [12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/Merger
 [13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.merger/join/methods/2
 [14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.merger/save/methods/1
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/Merge-Word-Documents-using-CSharp.jpg
 [16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/JoinOptions
 [17]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/AddPasswordOptions
 [18]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/addpassword
 [19]: https://purchase.groupdocs.com/temporary-license
 [20]: https://docs.groupdocs.com/merger/net/
 [21]: https://forum.groupdocs.com/c/merger/
 [22]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/








