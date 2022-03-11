---
title: "'使用 C# 比较两个或多个 Word 文档'"
author: Muzammil Khan
date: 2021-10-01T10:14:16+00:00
summary: "作为 C# 开发人员，您可以在 .NET 应用程序中以编程方式轻松比较两个或多个 Word 文档或比较同一 Word 文件的多个版本，以了解它们的异同。在本文中，您将学习**如何使用 C# 比较两个或多个 Word 文档并突出显示差异**。"
url: /zh/2021/10/01/compare-two-or-more-word-documents-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "比较 Word 文件的 API"
  - "比较多个 DOCX 文件"
  - "比较两个或多个文档"
  - "比较 Word 文档"

---


{{< figure align=center src="images/compare-two-or-more-word-documents-using-csharp.jpg" alt="使用 C# 比较两个或多个 Word 文档" caption="使用 C# 比较两个或多个 Word 文档">}}
 

您可以在 .NET 应用程序中以编程方式轻松比较两个或多个 Word 文档或比较同一个 Word 文件的多个版本的异同。在本文中，您将学习**如何使用 C# 比较两个或多个 Word 文档并突出显示差异**。

本文讨论/涵盖了以下主题：

  * [用于比较 DOCX 文件的 C# API][2]
  * [使用 C# 比较两个或多个 Word 文档][3]
  * [在 C# 中使用 Stream 比较 Word 文档][4]
  * [使用 C# 获取更改的文本][5]
  * [使用 C# 比较文档属性][6]
  * [使用 C# 比较受密码保护的 Word 文档][7]
  * [使用 C# 比较 Word 文档中的书签][8]

## 用于比较 DOCX 文件的 C# API {#CSharp-API-to-Compare-DOCX-Files}

为了比较两个或多个 [DOCX][9] 文件，我将使用 [GroupDocs.Comparison for .NET API][10]。它比较两个或多个文档，找出文档内容中单词、段落和字符的变化。因此，它会生成一个比较文档，突出显示差异并列出差异摘要。它还使您能够检测相似文档格式之间文本样式的变化和差异。 API 支持比较所有行业标准文档格式，例如 PDF、HTML、Word、Excel、PowerPoint、Outlook 电子邮件、Visio 图表、OpenDocument、AutoCAD 和图像。

您可以[下载][11] API 的 DLL 或使用 [NuGet][12] 安装它。

```
Install-Package GroupDocs.Comparison
```

## 使用 C# 比较两个或多个 Word 文档 {#Compare-Word-Documents-using-CSharp}

您可以按照下面给出的简单步骤以编程方式比较两个或多个 Word 文档：

  1. 使用源 DOCX 文件路径创建 _**[Comparer][13]**_ 类的实例
  2. 使用目标 DOCX 文件调用 **_[Add()][14]_** 方法以添加到比较中
  3. 重复上述步骤添加更多文件进行比较
  4. 使用输出文件路径调用 _**[Compare()][15]**_ 方法

以下代码示例展示了**如何比较两个或多个 Word 文档并使用 C# 突出显示差异**。

```
// 初始化比较器
Comparer comparer = new Comparer("C:\\Files\\source.docx");

// 添加目标文件进行比较
comparer.Add("C:\\Files\\target.docx");

// 比较并保存差异
comparer.Compare("C:\\Files\\result.docx");
```

{{< figure align=center src="images/source_and_target_docx_files-1024x657.jpg" alt="源和目标 DOCX 文件" caption="源和目标 DOCX 文件">}}
 

{{< figure align=center src="images/Compare-Word-Documents-using-CSharp-1024x794.jpg" alt="使用 C# 比较两个或多个 Word 文档" caption="使用 C# 比较两个或多个 Word 文档">}}
 

生成的文档还在文档末尾包含一个摘要页面，该页面显示比较中发现的所有更改的摘要。

[Comparer][13] 类是使您能够控制和执行比较过程的主类。它提供了几种方法来比较两个或多个文档。此类的 [Add()][14] 方法，将文件添加到比较过程中。您可以使用 Add() 方法轻松地将多个文件添加到比较中，如下所示：

```
comparer.Add("target1.docx");
comparer.Add("target2.docx");
comparer.Add("target3.docx");
```

[Comparer][13] 类的 [Compare()][15] 方法比较源文档和目标文档。此方法突出显示差异并将结果保存到作为输入参数提供的文件路径中。

## 在 C# 中使用 Stream 比较 Word 文档 {#Compare-Word-Documents-using-Stream-in-CSharp}

您可以按照以下步骤使用 FileStream 比较两个或多个 Word 文档：

  1. 读取 Stream 对象中的源文件
  2. 在另一个 Stream 对象中读取目标文件
  3. 使用源 Stream 对象创建 _**[Comparer][13]**_ 类的实例
  4. 使用目标 Stream 对象调用 **_[Add()][14]_** 方法以添加到比较中
  5. 使用输出文件路径调用 _**[Compare()][15]**_ 方法

以下代码示例展示了**如何在 C# 中使用 FileStream 比较 Word 文档**。

```
// 读取源文件和目标文件
using (Stream sourceStream = File.OpenRead("C:\\Files\\source.docx"))
using (Stream targetStream = File.OpenRead("C:\\Files\\target.docx"))
{
    // initialize comparer
    using (Comparer comparer = new Comparer(sourceStream))
    {
        // add target filestream to compare
        comparer.Add(targetStream);

        // compare and save differences
        comparer.Compare(File.Create("C:\\Files\\result.docx"));
    }
}
```

## 使用 C# 获取更改的文本 {#Get-Text-of-the-Changes-using-CSharp}

您可以按照下面给出的简单步骤以编程方式获取在比较 Word 文档中发现的更改的文本：

  1. 使用源 DOCX 文件路径创建 _**[Comparer][13]**_ 类的实例
  2. 使用目标 DOCX 文件调用 **_[Add()][14]_** 方法以添加到比较中
  3. 重复上述步骤添加更多文件进行比较
  4. 调用 _**[Compare()][15]**_ 方法
  5. 调用**_[GetChanges()][18]_**方法获取变更详情
  6. 显示更改

以下代码示例显示**如何使用 C# 获取更改的文本**。

```
// 初始化比较器
Comparer 比较r = new Comparer("C:\\Files\\source.docx");

// 添加目标文件进行比较
比较r.Add("C:\\Files\\target.docx");

// 比较
比较r.Compare();

// 获取更改
ChangeInfo[] changes = 比较r.GetChanges();

Console.WriteLine("Count of changes: " + changes.Length);

// 显示更改
foreach (ChangeInfo change in changes)
{
    Console.WriteLine("Change Type: " + change.Type + ", Text: " + change.Text);
}
```

```
Count of changes: 10
Change Type: Inserted, Text:
Change Type: Inserted, Text:  Company ‼ HYPERLINK "http://www.aspose.com/" ¶Aspose Pty Ltd§ Division GroupDocs
Change Type: Inserted, Text:
Change Type: Inserted, Text: Cool
Change Type: Deleted, Text: test
Change Type: Inserted, Text:
Change Type: Inserted, Text: signatures
Change Type: Inserted, Text:
Change Type: Deleted, Text: Customers
Change Type: Deleted, Text: GroupDocs is used by companies of all sizes across the globe, from large multinational firms to small freelance businesses. They come to us because they have a need for a simple, one-stop-shop, document management solution.
```

您可以通过调用 [Comparer][13] 类的 [GetChanges()][18] 方法来获取源文件和目标文件之间的更改列表。它返回 [ChangeInfo][19] 对象的列表。 [ChangeInfo][19] 类表示有关更改的信息，并提供各种属性来获取更改的详细信息，例如 [Text][20]、[Type][21] 等。

## 使用 C# 比较文档属性 {#Documents-Properties-Comparison-using-CSharp}

您可以按照以下步骤以编程方式比较 Word 文档的内置、自定义属性和可变属性：

  1. 使用源 DOCX 文件路径创建 _**[Comparer][13]**_ 类的实例
  2. 使用目标 DOCX 文件调用 **_[Add()][14]_** 方法以添加到比较中
  3. 重复上述步骤添加更多文件进行比较
  4. 创建 **_[CompareOptions][22]_** 的实例
  5. 将 [CompareVariableProperty][23] 设置为 true
  6. 将 [CompareDocumentProperty][24] 设置为 true
  7. 使用输出文件路径和 **_CompareOptions_** 调用 _**[Compare()][25]**_ 方法

以下代码示例展示了**如何使用 C# 比较文档属性**。

```
// 初始化比较器
Comparer 比较r = new Comparer("C:\\Files\\source.docx");

// 添加目标文件进行比较
比较r.Add("C:\\Files\\target.docx");

// 定义比较选项
CompareOptions options = new CompareOptions();
options.CompareVariableProperty = true; // activate the comparison of variable properties
options.CompareDocumentProperty = true; // activate the comparison of built and custom properties

// 比较
比较r.Compare("C:\\Files\\result.docx", options);
```

{{< figure align=center src="images/Documents-Properties-Comparison-using-CSharp-957x1024.jpg" alt="使用 C# 比较文档属性" caption="使用 C# 比较文档属性">}}
 

您可以通过应用各种比较选项来增强比较过程。为此，[**CompareOptions**][22] 类允许设置各种比较选项以实现特定结果。该类的 [CompareDocumentProperty][24] 使您可以打开 Word 格式的内置和自定义属性的比较。 [CompareVariableProperty][23] 允许打开 Word 格式的变量属性的比较。

## 使用 C# 比较受密码保护的 Word 文档 {#Compare-Password-Protected-Word-Documents-using-CSharp}

您可以按照以下步骤以编程方式比较两个或多个受密码保护的 Word 文档：

  1. 创建 [_**LoadOptions**_][27] 类的实例
  2. 提供源文件的密码
  3. 使用源 DOCX 文件路径和 **_LoadOptions_** 创建 _**[Comparer][13]**_ 类的实例
  4. 使用目标 DOCX 文件路径和带有密码的 **_LoadOptions_** 实例调用 **_[Add()][14]_** 方法
  5. 重复上述步骤添加更多文件进行比较
  6. 使用输出文件路径调用 _**[Compare()][15]**_ 方法

以下代码示例显示**如何使用 C# 比较受密码保护的 Word 文档**。

```
// 定义源文件的加载选项
LoadOptions sourceLoadOptions = new LoadOptions() { Password = "1234" };

// 初始化比较器
Comparer 比较r = new Comparer("C:\\Files\\source.docx", sourceLoadOptions);

// 添加目标文件进行比较
比较r.Add("C:\\Files\\target.docx", new LoadOptions() { Password = "5678" });

// 比较
比较r.Compare("C:\\Files\\result.docx");
```

[**LoadOptions**][27] 类使您能够在加载文档时指定其他选项。它提供了以下属性来指定：

  * FontDirectories — 要加载的字体目录列表。
  * LoadText — 表示传递的字符串是比较文本，而不是文件路径（仅用于文本比较）。
  * 密码 — 文档的密码。

## 使用 C# 比较 Word 文档中的书签 {#Compare-Bookmarks-in-Word-Documents-using-CSharp}

您可以按照以下步骤以编程方式比较 Word 文档中可用的书签：

  1. 使用源 DOCX 文件路径创建 _**[Comparer][13]**_ 类的实例
  2. 使用目标 DOCX 文件调用 **_[Add()][14]_** 方法以添加到比较中
  3. 重复上述步骤添加更多文件进行比较
  4. 创建 **_[CompareOptions][22]_** 的实例
  5. 将 [CompareBookmarks][28] 设置为 true
  6. 使用输出文件路径和 **_CompareOptions_** 调用 _**[Compare()][25]**_ 方法

以下代码示例展示了**如何使用 C# 比较 Word 文档中的书签**。

```
// 初始化比较器
Comparer 比较r = new Comparer("C:\\Files\\source.docx");

// 添加目标文件进行比较
比较r.Add("C:\\Files\\target.docx");

// 定义比较选项
CompareOptions 比较Options = new CompareOptions();
比较Options.CompareBookmarks = true; // 比较 bookmarks

// 比较
比较r.Compare("C:\\Files\\result.docx", 比较Options);
```

{{< figure align=center src="images/Compare-Bookmarks-in-Word-Documents-using-CSharp-1.jpg" alt="使用 C# 比较 Word 文档中的书签" caption="使用 C# 比较 Word 文档中的书签">}}
 

[CompareBookmarks][28] 属性允许您比较源文档和目标文档中可用的书签。

## 获得免费许可证

您可以通过请求 [免费的临时许可证][30] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C# 比较两个或多个 Word 文档并突出显示** **差异**。您还学习了**如何获取突出显示的更改列表。** 此外，您还学习了**如何以编程方式比较 Word 文档中的书签**。此外，您还学习了**如何使用 C# 比较受密码保护的 Word 文档**。您可以使用 [文档][31] 了解有关 .NET API 的 GroupDocs.Comparison 的更多信息。如有任何歧义，请随时在 [论坛][32] 上与我们联系。

## 也可以看看

  * [使用 C# 比较 PDF 文件并突出显示差异][33]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/compare-two-or-more-word-documents-using-csharp.jpg
 [2]: #CSharp-API-to-Compare-DOCX-Files
 [3]: #Compare-Word-Documents-using-CSharp
 [4]: #Compare-Word-Documents-using-Stream-in-CSharp
 [5]: #Get-Text-of-the-Changes-using-CSharp
 [6]: #Documents-Properties-Comparison-using-CSharp
 [7]: #Compare-Password-Protected-Word-Documents-using-CSharp
 [8]: #Compare-Bookmarks-in-Word-Documents-using-CSharp
 [9]: https://docs.fileformat.com/word-processing/docx/
 [10]: https://products.groupdocs.com/comparison/net
 [11]: https://downloads.groupdocs.com/comparison/net
 [12]: https://www.nuget.org/packages/groupdocs.comparison
 [13]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
 [14]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.comparer/add/methods/2
 [15]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.comparer/compare/methods/7
 [16]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/source_and_target_docx_files.jpg
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Compare-Word-Documents-using-CSharp.jpg
 [18]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/getchanges
 [19]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.result/changeinfo
 [20]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.result/changeinfo/properties/text
 [21]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.result/changeinfo/properties/type
 [22]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.options/compareoptions
 [23]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.options/compareoptions/properties/comparevariableproperty
 [24]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.options/compareoptions/properties/comparedocumentproperty
 [25]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.comparer/compare/methods/8
 [26]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Documents-Properties-Comparison-using-CSharp.jpg
 [27]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.options/loadoptions
 [28]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.options/compareoptions/properties/comparebookmarks
 [29]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Compare-Bookmarks-in-Word-Documents-using-CSharp-1.jpg
 [30]: https://purchase.groupdocs.com/temporary-license
 [31]: https://docs.groupdocs.com/comparison/net/
 [32]: https://forum.groupdocs.com/c/comparison/
 [33]: https://blog.conholdate.com/2021/04/14/compare-pdf-files-and-highlight-differences-using-csharp/








