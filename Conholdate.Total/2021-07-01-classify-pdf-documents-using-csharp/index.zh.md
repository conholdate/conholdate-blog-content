---
title: "'使用 C# 对 PDF 文档进行分类'"
author: Muzammil Khan
date: 2021-07-01T05:17:59+00:00
summary: "您可以在 .NET 应用程序中以编程方式轻松地对 PDF 文档进行分类。本文将重点介绍**如何使用 C# 对 PDF 文档进行分类**。"
url: /zh/2021/07/01/classify-pdf-documents-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "分类文档分类"
  - "分类 PDF 文档"
  - "使用 CSharp 对 PDF 进行分类"
  - "文件分类"

---


{{< figure align=center src="images/classify-pdf-documents-using-csharp.jpg" alt="使用 C# 对 PDF 文档进行分类">}}
 

您可以使用 IAB-2、文档和情感分类法中的预定义标签或类别以编程方式对文档进行分类。文件的分类使在正确的时间更容易找到相关信息。它还有助于管理和排序文档以搜索和检索重要信息。在本文中，您将学习**如何使用 C# 对 PDF 文档进行分类**。

本文讨论/涵盖了以下主题：

  * [用于 PDF 分类的 C# API][2]
  * [使用 C# 使用 IAB-2 分类法对 PDF 文档进行分类][3]
  * [使用 C# 使用文档分类法进行 PDF 分类][4]
  * [使用 C# 从 Stream 中的 PDF 文档分类][5]
  * [使用 C# 对受密码保护的 PDF 文件进行分类][6]

## 用于 PDF 分类的 C# API {#api-for-pdf-classification}

我将使用 [GroupDocs.Classification for .NET][7] API 对 [PDF][8] 文件进行分类。它提供了预定义类别中的高级文档和文本分类。 API 支持不同类型的分类法，例如 IAB-2、文档和情感分类法。它分析文本并显示分类信息，包括带有概率分数的最佳类别。您可以对各种行业标准文档格式进行分类，例如 PDF、Word、OpenDocument、RTF 和 TXT。该 API 还提供带有自动检测语言的情感分析，并支持英语、中文、西班牙语和德语。它可用于在任何面向 .NET 平台的开发环境中开发应用程序。

您可以 [下载][9] API 的 DLL 或使用 [NuGet][10] 安装它。

```
Install-Package GroupDocs.Classification
```

## 使用 C# 使用 IAB-2 分类法对 PDF 文档进行分类 {#Classify-PDF-Documents-with-IAB-2-Taxonomy}

您可以按照下面给出的简单步骤，以编程方式轻松地使用 IAB-2 分类法对 PDF 文档进行分类：

  * 创建 _[**Classifier**][11]_ 类的实例
  * 使用文件路径调用_[**Classifier.Classify()**][12]_方法
  * 将 _bestClassesCount_ 和 _Taxonomy_ 设置为输入
  * 在 _**[ClassificationResponse][13]**_ 类对象中获取结果

以下代码示例展示了**如何使用 C# 使用 IAB-2 分类法对 PDF 进行分类**。

```
// 创建分类器
var classifier = new Classifier();

// 使用 IAB-2 对文档进行分类
var response = classifier.Classify("sample.pdf", @"C:\Files\", 3, Taxonomy.Iab2);

// 显示分类信息
foreach (var r in response.BestResults)
{
    Console.WriteLine("ClassName: " + r.Name);
    Console.WriteLine("ClassProbability: " + r.Probability);
    Console.WriteLine("--------------------------------");
}
```

{{< figure align=center src="images/Classify-PDF-Documents-with-IAB-2-Taxonomy-1024x698.jpg" alt="使用 C# 使用 IAB-2 分类法对 PDF 文档进行分类" caption="使用 C# 使用 IAB-2 分类法对 PDF 文档进行分类">}}
 

**[Classifier][11]** 类是提供各种[方法][15] 对文档进行分类的主要类。此类的 _Classify()_ 方法按文件名和目录名对文档进行分类。 _bestClassesCount_ 参数定义要返回的最佳匹配类的计数。在上面的代码示例中，我使用 [Taxonomy.IAB2][16] 分类法进行分类。

_**[ClassificationResponse][13]**_ 类提供属性和方法来显示检索到的分类信息。

## 使用 C# 使用文档分类法进行 PDF 分类 {#PDF-Classification-with-Documents-Taxonomy}

您可以按照以下简单步骤以编程方式使用文档分类法对 PDF 文档进行分类：

  * 创建 _[**Classifier**][11]_ 类的实例
  * 使用文件路径调用_[**Classifier.Classify()**][12]_方法
  * 将 bestClassesCount、Taxonomy 和 _PrecisionRecallBalance_ 设置为输入
  * 在 _**[ClassificationResponse][13]**_ 类对象中获取结果

以下代码示例展示了**如何使用 C# 对带有文档分类的 PDF 进行分类**。

```
// 创建分类器
var classifier = new Classifier();

// 使用文档分类对文档进行分类
var response = classifier.Classify("sample.pdf", @"C:\Files\", 4, Taxonomy.Documents, PrecisionRecallBalance.Precision);
                
// 显示分类信息
foreach (var r in response.BestResults)
{
    Console.WriteLine("ClassName: " + r.Name);
    Console.WriteLine("ClassProbability: " + r.Probability);
    Console.WriteLine("--------------------------------");
}
```

{{< figure align=center src="images/Classify-PDF-Documents-with-Document-Taxonomy-1024x683.jpg" alt="使用 C# 使用文档分类法对 PDF 进行分类" caption="使用 C# 使用文档分类法对 PDF 进行分类">}}
 

## 使用 C# 从 Stream 中的 PDF 文档分类 {#PDF-Document-Classification-from-Stream}

您可以按照以下给出的几个步骤，以编程方式从文件流中对 PDF 文档进行分类：

  * 读取 FileStream 实例中的文件
  * 创建 _[**Classifier**][11]_ 类的实例
  * 使用 FileStream 实例调用 _[**Classifier.Classify()**][18]_ 方法
  * 将 _bestClassesCount_ 和 _Taxonomy_ 设置为输入
  * 在 _**[ClassificationResponse][13]**_ 类对象中获取结果

以下代码示例展示了**如何使用 C# 对来自文档流的 PDF 进行分类**。

```
using (var fs = File.OpenRead(Path.Combine(@"C:\Files\", "sample.pdf")))
{
    // create classifier
    var classifier = new Classifier();
    
    // classify document
    var response = classifier.Classify(fs, "sample.pdf", 2, Taxonomy.Documents);
    
    // show classification information
    Console.WriteLine($"{"sample.pdf"}: {response.BestClassName}, {response.BestClassProbability}");
}
```

## 使用 C# 对受密码保护的 PDF 文件进行分类 {#Classify-Password-Protected-PDF-using-CSharp}

您可以按照下面给出的简单步骤，以编程方式轻松地对受密码保护的 PDF 文档进行分类：

  * 创建 _[**Classifier**][11]_ 类的实例
  * 使用文件路径调用_[**Classifier.Classify()**][12]_方法
  * 将文件的_bestClassesCount_和_Password_设置为输入
  * 在 _**[ClassificationResponse][13]**_ 类对象中获取结果

以下代码示例展示了**如何使用 C# 对受密码保护的 PDF 文件进行分类**。

```
// 创建分类器
var classifier = new Classifier();

// 对受密码保护的文档进行分类
var response = classifier.Classify("password-protected.pdf", @"C:\Files\", password: "password");

// 显示分类信息
Console.WriteLine(response.BestClassName, response.BestClassProbability);
```

## 获得免费许可证

您可以通过请求 [免费的临时许可证][19] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C# 对 PDF 文档进行分类**。您还学习了如何使用 IAB-2 分类法和文档分类法对文档进行分类。此外，您还学习了如何在使用文件流而不是 C# 中的文件路径加载文档时对文档进行分类。您可以使用 [文档][20] 了解有关 .NET API 的 GroupDocs.Classification 的更多信息。如有任何歧义，请随时在 [论坛][21] 上与我们联系。

## 也可以看看

  * [C# 中的客户反馈情绪分析][22]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/06/classify-pdf-documents-using-csharp.jpg
 [2]: #api-for-pdf-classification
 [3]: #Classify-PDF-Documents-with-IAB-2-Taxonomy
 [4]: #PDF-Classification-with-Documents-Taxonomy
 [5]: #PDF-Document-Classification-from-Stream
 [6]: #Classify-Password-Protected-PDF-using-CSharp
 [7]: https://products.groupdocs.com/classification/net
 [8]: https://docs.fileformat.com/pdf
 [9]: https://downloads.groupdocs.com/classification/net
 [10]: https://www.nuget.org/packages/GroupDocs.Classification
 [11]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier
 [12]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.classifier/classify/methods/2
 [13]: https://apireference.groupdocs.com/classification/net/groupdocs.classification.dto/classificationresponse
 [14]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/06/Classify-PDF-Documents-with-IAB-2-Taxonomy.jpg
 [15]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier/methods/index
 [16]: https://docs.groupdocs.com/classification/net/taxonomies/#iab-2-taxonomy
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/06/Classify-PDF-Documents-with-Document-Taxonomy.jpg
 [18]: https://apireference.groupdocs.com/classification/net/groupdocs.classification/classifier/methods/classify
 [19]: https://purchase.groupdocs.com/temporary-license
 [20]: https://docs.groupdocs.com/classification/net/
 [21]: https://forum.groupdocs.com/c/classification/
 [22]: https://blog.groupdocs.com/2020/06/17/classify-customers-feedback-using-sentiment-analysis-in-csharp/








