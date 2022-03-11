---
title: "'使用 C# 在 Word 文档中创建图表'"
author: Muzammil Khan
date: 2021-10-31T11:50:18+00:00
summary: "作为 C# 开发人员，您可以以编程方式在 Word 文档中插入各种类型的图表。在本文中，您将学习**如何使用 C# 在 Word 文档中创建图表**。"
url: /zh/2021/10/31/create-charts-in-word-documents-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 CSharp 的 Word 中的图表"
  - "在 CSharp 中创建面积图"
  - "在 CSharp 中创建图表"
  - "创建柱形图 CSharp"
  - "在 CSharp 中创建散点图"

---


{{< figure align=center src="images/create-charts-in-word-documents-using-csharp.jpg" alt="创建图表-in-word-documents-using-csharp">}}
 

作为 C# 开发人员，您可以通过编程方式在 Word 文档中插入各种类型的图表。它有助于以图形方式呈现您的数据和信息。在本文中，您将学习**如何使用 C# 在 Word 文档中创建图表**。

本文讨论/涵盖了以下主题：

  * [在 Word 文档中插入图表的 C# API][2]
  * [在 Word 文档中创建柱形图][3]
  * [使用 C# 在 Word 文档中创建散点图][4]
  * [使用 C# 在 Word 文档中插入面积图][5]
  * [使用 C# 在 Word 文档中插入气泡图][6]

## 在 Word 文档中插入图表的 C# API {#CSharp-API-to-Insert-Charts-in-Word-Documents}

为了在 DOCX 文件中插入图表，我们将使用 [Aspose.Words for .NET API][7]。它允许您生成、修改、转换、渲染和打印文件，而无需直接在跨平台应用程序中使用 Microsoft Word。 API 使您能够以编程方式在 Word 文档中插入各种 [支持的图表类型][8]。

您可以 [下载][9] API 的 DLL 或使用 [NuGet][10] 安装它。

```
Install-Package Aspose.Words
```

## 在 Word 文档中创建柱形图 {#Create-Columns-Charts-in-Word-Documents-using-CSharp}

您可以按照以下步骤以编程方式在 Word 文档中创建柱形图：

  * 首先，使用 [Document][11] 类创建一个新文档。
  * 现在，使用 _Document_ 类对象创建 [DocumentBuilder][12] 类的实例。
  * 然后，调用 [DocumentBuilder.InsertChart()][13] 方法。将 [ChartType][8] 作为 _Column_ 传递，并以 _height_ 和 _width_ 作为输入参数。
  * 在 [Shape][14] 类对象中获取结果。
  * 现在，创建 [Chart][15] 类的实例并将 [Shape.Chart][16] 对象分配给它。如果此形状具有图表，则它提供对图表属性的访问。
  * 然后，在 [ChartSeriesCollection][17] 对象中获取图表系列集合。
  * 创建类别名称数组。
  * 现在，调用 [ChartSeriesCollection.Add()][18] 方法添加图表系列。传递名称、类别数组和值作为输入参数。重复此步骤以添加更多系列。
  * 最后，调用带有输出文件路径的[Document.Save()][19]方法来保存文件。

以下代码示例展示了**如何使用 C# 在 Word 文档中创建柱形图**。

```
// 创建文档
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 添加带有默认数据的图表。您可以指定不同的图表类型和大小。
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);

// Shape 的图表属性包含所有图表相关选项。
Chart chart = shape.Chart;

// 获取图表系列集合。
ChartSeriesCollection seriesColl = chart.Series;
// 检查系列计数。
Console.WriteLine(seriesColl.Count);

// 删除默认生成的系列。
seriesColl.Clear();

// 创建类别名称数组，在此示例中，我们有两个类别。
string[] categories = new string[] { "AW Category 1", "AW Category 2" };

// 添加新系列。请注意，数据数组不能为空，并且数组的大小必须相同。
seriesColl.Add("AW Series 1", categories, new double[] { 1, 2 });
seriesColl.Add("AW Series 2", categories, new double[] { 3, 4 });
seriesColl.Add("AW Series 3", categories, new double[] { 5, 6 });
seriesColl.Add("AW Series 4", categories, new double[] { 7, 8 });
seriesColl.Add("AW Series 5", categories, new double[] { 9, 10 });

// 保存文档
doc.Save(@"C:\Files\Words\ColumnsChart.docx");
```

{{< figure align=center src="images/Create-Columns-Charts-in-Word-Documents-using-CSharp-1024x1002.jpg" alt="使用 C# 在 Word 文档中创建柱形图。" caption="使用 C# 在 Word 文档中创建柱形图">}}
 

## 使用 C# 在 Word 文档中创建散点图 {#Create-Scatter-Charts-in-Word-Documents-using-CSharp}

您可以按照前面提到的步骤以编程方式在 Word 文档中插入散点图。但是，您需要在 [DocumentBuilder.InsertChart()][21] 方法中设置 ChartType.Scatter。

以下代码示例展示了**如何使用 C# 在 Word 文档中创建散点图**。

```
// 创建一个新文档
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入散点图。
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;

// 使用此重载将系列添加到任何类型的散点图。
chart.Series.Add("AW Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });

// 保存文档
doc.Save(@"C:\Files\Words\ScatterChart.docx");
```

{{< figure align=center src="images/Create-Scatter-Charts-in-Word-Documents-using-CSharp-1024x1000.jpg" alt="使用 C# 在 Word 文档中创建散点图。" caption="使用 C# 在 Word 文档中创建散点图">}}
 

## 使用 C# 在 Word 文档中插入面积图 {#Insert-Area-Charts-in-Word-Documents-using-CSharp}

您可以按照前面提到的步骤以编程方式在 Word 文档中插入面积图。但是，您需要在 [DocumentBuilder.InsertChart()][21] 方法中设置 ChartType.Area。

以下代码示例展示了**如何使用 C# 在 Word 文档中创建面积图**。

```
// 创建一个新文档
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入面积图。
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;

// 使用此重载将系列添加到任何类型的区域、雷达和股票图表。
chart.Series.Add("AW Series 1", new DateTime[] {
    new DateTime(2002, 05, 01),
    new DateTime(2002, 06, 01),
    new DateTime(2002, 07, 01),
    new DateTime(2002, 08, 01),
    new DateTime(2002, 09, 01)},
    new double[] { 32, 32, 28, 12, 15 });

// 保存文档
doc.Save(@"C:\Files\Words\AreaChart.docx");
```

{{< figure align=center src="images/Insert-Area-Charts-in-Word-Documents-using-CSharp-1024x998.jpg" alt="使用 C# 在 Word 文档中插入面积图。" caption="使用 C# 在 Word 文档中插入面积图">}}
 

## 使用 C# 在 Word 文档中插入气泡图 {#Insert-Bubble-Charts-in-Word-Documents-using-CSharp}

您可以按照前面提到的步骤以编程方式在 Word 文档中插入气泡图。但是，您需要在 [DocumentBuilder.InsertChart()][21] 方法中设置 ChartType.Bubble。

以下代码示例展示了**如何使用 C# 在 Word 文档中创建气泡图**。

```
// 创建一个新文档
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入气泡图。
Shape shape = builder.InsertChart(ChartType.Bubble, 432, 252);
Chart chart = shape.Chart;

// 使用此重载将系列添加到任何类型的气泡图。
chart.Series.Add("AW Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 }, new double[] { 10, 4, 8 });

// 保存文档
doc.Save(@"C:\Files\Words\BubbleChart.docx");
```

{{< figure align=center src="images/Insert-Bubble-Charts-in-Word-Documents-using-CSharp-1024x997.jpg" alt="使用 C# 在 Word 文档中插入气泡图。" caption="使用 C# 在 Word 文档中插入气泡图">}}
 

## 获得免费许可证

您可以通过请求 [免费的临时许可证][25] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C# 在 Word 文档中创建图表**。特别是，您学习了如何以编程方式在 Word 文档中创建柱形图、面积图、气泡图和散点图。同样，您可以创建其他类型的图表。您可以使用 [文档][26] 了解更多关于 Aspose.Words for .NET API 的信息。如有任何歧义，请随时在 [论坛][27] 上与我们联系。

## 也可以看看

  * [使用 Word 文档 C# 中的目录][28]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/create-charts-in-word-documents-using-csharp.jpg
 [2]: #CSharp-API-to-Insert-Charts-in-Word-Documents
 [3]: #Create-Columns-Charts-in-Word-Documents-using-CSharp
 [4]: #Create-Scatter-Charts-in-Word-Documents-using-CSharp
 [5]: #Insert-Area-Charts-in-Word-Documents-using-CSharp
 [6]: #Insert-Bubble-Charts-in-Word-Documents-using-CSharp
 [7]: https://products.aspose.com/words/net/
 [8]: https://apireference.aspose.com/words/net/aspose.words.drawing.charts/charttype
 [9]: https://downloads.aspose.com/words/net
 [10]: https://www.nuget.org/packages/aspose.words
 [11]: https://apireference.aspose.com/words/net/aspose.words/document
 [12]: https://apireference.aspose.com/words/net/aspose.words/documentbuilder
 [13]: https://apireference.aspose.com/words/net/aspose.words/documentbuilder/methods/insertchart
 [14]: https://apireference.aspose.com/words/net/aspose.words.drawing/shape
 [15]: https://apireference.aspose.com/words/net/aspose.words.drawing.charts/chart
 [16]: https://apireference.aspose.com/words/net/aspose.words.drawing/shape/properties/chart
 [17]: https://apireference.aspose.com/words/net/aspose.words.drawing.charts/chartseriescollection
 [18]: https://apireference.aspose.com/words/net/aspose.words.drawing.charts.chartseriescollection/add/methods/3
 [19]: https://apireference.aspose.com/words/net/aspose.words.document/save/methods/2
 [20]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Create-Columns-Charts-in-Word-Documents-using-CSharp.jpg
 [21]: https://apireference.aspose.com/words/net/aspose.words/documentbuilder/methods/write
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Create-Scatter-Charts-in-Word-Documents-using-CSharp.jpg
 [23]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Insert-Area-Charts-in-Word-Documents-using-CSharp.jpg
 [24]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Insert-Bubble-Charts-in-Word-Documents-using-CSharp.jpg
 [25]: https://purchase.groupdocs.com/temporary-license
 [26]: https://docs.aspose.com/words/net/
 [27]: https://forum.aspose.com/c/words/8
 [28]: https://blog.aspose.com/2021/03/02/work-with-table-of-contents-in-word-csharp/








