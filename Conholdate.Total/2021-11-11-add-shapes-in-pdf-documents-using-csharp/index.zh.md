---
title: "'使用 C# 在 PDF 文档中添加形状'"
author: Muzammil Khan
date: 2021-11-11T05:04:14+00:00
summary: "作为 C# 开发人员，您可以通过编程方式在 PDF 文档中添加绘图形状。在本文中，您将学习**如何使用 C# 在 PDF 文档中添加形状**。"
url: /zh/2021/11/11/add-shapes-in-pdf-documents-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 CSharp 在 PDF 中添加圆"
  - "使用 CSharp 在 PDF 中添加矩形"
  - "使用 CSharp 在 PDF 中添加形状"
  - "在 PDF 中绘制形状"
  - "绘制形状"

---


{{< figure align=center src="images/add-shapes-in-pdf-documents-using-csharp.jpg" alt="使用 C# 在 PDF 文档中添加形状">}}
 

您可能需要在 PDF 文件中添加各种类型的图形或形状，以交互方式呈现数据或信息。作为 C# 开发人员，您可以通过编程方式在 PDF 文档中添加绘图形状。在本文中，您将学习**如何使用 C# 在 PDF 文档中添加形状**。

本文讨论/涵盖了以下主题：

  1. [在 PDF 文档中绘制形状的 C# API](#CSharp-API-to-Draw-Shapes-in-PDF-Documents)
  2. [使用 C# 在 PDF 文档中创建填充矩形](#Create-Filled-Rectangle-in-PDF-Documents-using-CSharp)
  3. [使用 C# 在 PDF 文档中添加圆圈](#Add-Circle-in-PDF-Documents-using-CSharp)
  4. [使用 C# 在 PDF 文档中跨页面画线](#Draw-Lines-Across-the-Page-in-PDF-Documents-using-CSharp)
  5. [使用 C# 在 PDF 文档中添加椭圆](#Add-Ellipse-in-PDF-Documents-using-CSharp)

## 在 PDF 文档中绘制形状的 C# API {#CSharp-API-to-Draw-Shapes-in-PDF-Documents}

为了在 [PDF][2] 文件中添加形状，我们将使用 [Aspose.PDF for .NET API][3]。它允许您在不使用 Adobe Acrobat 的情况下生成、修改、转换、渲染、保护和打印 [支持的文档][4]。它还提供压缩选项、表格创建和操作、图形和图像功能、印章和水印任务、扩展的安全控制和自定义字体处理。

您可以[下载][5] API 的 DLL 或使用 [NuGet][6] 安装它。

```
Install-Package Aspose.PDF
```

## 使用 C# 在 PDF 文档中创建填充矩形 {#Create-Filled-Rectangle-in-PDF-Documents-using-CSharp}

您可以按照以下步骤以编程方式在 PDF 文档中创建填充矩形：

  * 首先，使用 [Document][7] 类创建一个新文档。
  * 现在，调用 [Document.Pages.Add()][8] 方法将一个空页面添加到 PDF 文件的页面集合中。
  * 为图表创建一个具有高度和宽度的 [Graph][9] 类的实例。
  * 然后，调用 [Page.Paragraphs.Add()][10] 方法将图形对象添加到页面实例的段落集合中。
  * 现在，创建一个 [Rectangle][11] 类的实例并设置它的左侧和底部位置，以及它的宽度和高度。
  * （可选）指定 [Graph 对象][12] 的填充颜色。
  * 然后，将矩形对象添加到 Graph 对象的 [形状集合][13] 中。
  * 最后，调用带有输出文件路径的[Document.Save()][14]方法来保存文件。

以下代码示例展示了**如何使用 C#** 在 PDF 文档中创建填充矩形。

```
// 创建文档实例
Document doc = new Document();

// 将页面添加到 PDF 文件的页面集合
Page page = doc.Pages.Add();

// 创建 Graph 实例
Graph graph = new Graph(100, 400);

// 将图形对象添加到页面实例的段落集合
page.Paragraphs.Add(graph);

// 创建矩形实例
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);

// 为 Graph 对象指定填充颜色
rect.GraphInfo.FillColor = Color.Gray;

// 将矩形对象添加到 Graph 对象的形状集合中
graph.Shapes.Add(rect);

// 保存 PDF 文件
doc.Save(@"C:\Files\PDF\FilledRectangle_out.pdf");
```

{{< figure align=center src="images/Create-Filled-Rectangle-in-PDF-Documents-using-CSharp.jpg" alt="使用 C# 在 PDF 文档中创建填充矩形。" caption="使用 C# 在 PDF 文档中创建填充矩形。">}}
 

## 使用 C# 在 PDF 文档中添加圆圈 {#Add-Circle-in-PDF-Documents-using-CSharp}

您可以按照以下步骤以编程方式在 PDF 文档中添加圆圈：

  * 首先，使用 [Document][7] 类创建一个新文档。
  * 现在，调用 [Document.Pages.Add()][8] 方法将一个空页面添加到 PDF 文件的页面集合中。
  * 为图表创建一个具有高度和宽度的 [Graph][9] 类的实例。
  * 然后，调用 [Page.Paragraphs.Add()][10] 方法将图形对象添加到页面实例的段落集合中。
  * 现在，创建一个 [Circle][16] 类的实例并设置它的 X 和 Y 位置以及它的半径。
  * 然后，设置圆圈的颜色和填充颜色。
  * 将圆形对象添加到 Graph 对象的 [形状集合][13]。
  * 最后，调用带有输出文件路径的[Document.Save()][14]方法来保存文件。

以下代码示例展示了**如何使用 C# 在 PDF 文档中添加圆圈**。

```
// 创建文档实例
Document doc = new Document();

// 将页面添加到 PDF 文件的页面集合
Page page = doc.Pages.Add();

// 创建具有特定尺寸的绘图对象
Graph graph = new Graph(400, 200);

// 创建圈子
Circle circle = new Circle(100, 100, 40);
circle.GraphInfo.Color = Color.Green;
circle.GraphInfo.FillColor = Color.GreenYellow;

graph.Shapes.Add(circle);

// 将 Graph 对象添加到页面的段落集合
page.Paragraphs.Add(graph);

// 保存 PDF 文件
doc.Save(@"C:\Files\PDF\FilledCircle_out.pdf");
```

{{< figure align=center src="images/Add-Circle-in-PDF-Documents-using-CSharp.jpg" alt="使用 C# 在 PDF 文档中添加圆圈。" caption="使用 C# 在 PDF 文档中添加圆圈。">}}
 

## 使用 C# 在 PDF 文档中的页面上画线 {#Draw-Lines-Across-the-Page-in-PDF-Documents-using-CSharp}

您可以按照以下步骤以编程方式在 PDF 文档的页面上画线：

  * 首先，使用 [Document][7] 类创建一个新文档。
  * 现在，调用 [Document.Pages.Add()][8] 方法将一个空页面添加到 PDF 文件的页面集合中。
  * 然后，将所有边的页边距设置为 0。
  * 创建具有页面宽度和页面高度的 [Graph][9] 类的实例。
  * 现在，使用线条位置数组创建 [Line][18] 类的实例，以创建从页面左下角到右上角的线条。
  * 然后，将线对象添加到 Graph 对象的 [形状集合][13] 中。
  * 现在，使用线位置数组创建 [Line][18] 类的另一个实例，以从页面的左上角到页面的右下角绘制一条线。
  * 然后，将线对象的第二个实例添加到 Graph 对象的 [形状集合][13]。
  * 调用 [Page.Paragraphs.Add()][10] 方法将图形对象添加到页面实例的段落集合中。
  * 最后，调用带有输出文件路径的[Document.Save()][14]方法来保存文件。

以下代码示例展示了**如何使用 C#** 在 PDF 文档的页面上绘制线条。

```
// 创建文档实例
Document doc = new Document();

// 将页面添加到 PDF 文件的页面集合
Page page = doc.Pages.Add();

// 将所有边的页边距设置为 0
page.PageInfo.Margin.Left = 0;
page.PageInfo.Margin.Right = 0;
page.PageInfo.Margin.Bottom = 0;
page.PageInfo.Margin.Top = 0;

// 创建宽度和高度等于页面尺寸的 Graph 对象
Graph graph = new Graph((float)page.PageInfo.Width, (float)page.PageInfo.Height);

// 从页面的左下角到右上角创建第一行对象
Line line = new Line(new float[] { (float) page.Rect.LLX, 0, (float) page.PageInfo.Width,
    (float) page.Rect.URY });

// 将线条添加到 Graph 对象的形状集合
graph.Shapes.Add(line);

// 从页面左上角到页面右下角画线
Line line2 = new Line(new float[] { 0, (float) page.Rect.URY, (float) page.PageInfo.Width,
    (float) page.Rect.LLX });

// 将线条添加到 Graph 对象的形状集合
graph.Shapes.Add(line2);

// 将 Graph 对象添加到页面的段落集合
page.Paragraphs.Add(graph);

// 保存 PDF 文件
doc.Save(@"C:\Files\PDF\DrawLineAcrossPage_out.pdf");
```

{{< figure align=center src="images/Draw-Line-Across-the-Page-in-PDF-Documents-using-CSharp.png" alt="使用 C# 在 PDF 文档中的页面上画一条线。" caption="使用 C# 在 PDF 文档中的页面上画一条线。">}}
 

## 使用 C# 在 PDF 文档中添加椭圆 {#Add-Ellipse-in-PDF-Documents-using-CSharp}

您可以按照以下步骤以编程方式在 PDF 文档中添加带有文本的椭圆：

  * 首先，使用 [Document][7] 类创建一个新文档。
  * 现在，调用 [Document.Pages.Add()][8] 方法将一个空页面添加到 PDF 文件的页面集合中。
  * 为图表创建一个具有高度和宽度的 [Graph][9] 类的实例。
  * 创建一个 [TextFragment][20] 类的实例，其中包含要在图形对象中显示的文本值。
  * 然后，设置文本的字体和大小。
  * 现在，创建一个 [Ellipse][21] 类的实例并设置它的左下方位置，以及它的宽度和高度。
  * 然后，设置颜色、填充颜色并将 TextFragment 对象分配给它的文本属性。
  * 现在，将椭圆对象添加到 Graph 对象的 [形状集合][13]。
  * 然后，调用 [Page.Paragraphs.Add()][10] 方法将图形对象添加到页面实例的段落集合中。
  * 最后，调用带有输出文件路径的[Document.Save()][14]方法来保存文件。

以下代码示例展示了**如何使用 C#** 在 PDF 文档中创建带有文本的椭圆。

```
// 创建文档实例
Document doc = new Document();

// 将页面添加到 PDF 文件的页面集合
Page page = doc.Pages.Add();

// 创建具有特定尺寸的绘图对象
Graph graph = new Graph(400, 400);

// 定义文本
TextFragment textFragment = new TextFragment("Ellipse");
textFragment.TextState.Font = FontRepository.FindFont("Helvetica");
textFragment.TextState.FontSize = 24;

// 画椭圆
Ellipse ellipse = new Ellipse(100, 100, 120, 180);
ellipse.GraphInfo.FillColor = Color.GreenYellow;
ellipse.GraphInfo.Color = Color.Red;
ellipse.Text = textFragment;

// 将椭圆添加到 Graph 对象的形状集合中
graph.Shapes.Add(ellipse);

// 将 Graph 对象添加到页面的段落集合
page.Paragraphs.Add(graph);

// 保存 PDF 文件
doc.Save(@"C:\Files\PDF\EclipseWithText_out.pdf");
```

{{< figure align=center src="images/Add-Ellipse-in-PDF-Documents-using-CSharp.jpg" alt="使用 C# 在 PDF 文档中添加椭圆。" caption="使用 C# 在 PDF 文档中添加椭圆。">}}
 

## 获得免费许可证

您可以通过请求 [免费的临时许可证][23] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C# 在 PDF 文档中添加形状**。特别是，您已经了解了如何以编程方式在 PDF 文档中添加填充的矩形、圆形、直线和椭圆。同样，您可以在 PDF 文件中创建圆弧和曲线。您可以使用 [文档][24] 了解更多关于 Aspose.PDF for .NET API 的信息。如有任何歧义，请随时在 [论坛][25] 上与我们联系。

## 也可以看看

  * [使用 C# 将 PDF 转换为图像][26]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/add-shapes-in-pdf-documents-using-csharp.jpg
 [2]: https://docs.fileformat.com/pdf/
 [3]: https://products.aspose.com/pdf/net/
 [4]: https://docs.aspose.com/pdf/net/supported-file-formats/
 [5]: https://downloads.aspose.com/pdf/net
 [6]: https://www.nuget.org/packages/aspose.pdf
 [7]: https://apireference.aspose.com/pdf/net/aspose.pdf/document
 [8]: https://apireference.aspose.com/pdf/net/aspose.pdf/pagecollection/methods/add
 [9]: https://apireference.aspose.com/pdf/net/aspose.pdf.drawing/graph
 [10]: https://apireference.aspose.com/pdf/net/aspose.pdf/paragraphs/methods/add
 [11]: https://apireference.aspose.com/pdf/net/aspose.pdf.drawing/rectangle
 [12]: https://apireference.aspose.com/pdf/net/aspose.pdf/graphinfo
 [13]: https://apireference.aspose.com/pdf/net/aspose.pdf.drawing/graph/properties/shapes
 [14]: https://apireference.aspose.com/pdf/net/aspose.pdf.document/save/methods/4
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/Create-Filled-Rectangle-in-PDF-Documents-using-CSharp.jpg
 [16]: https://apireference.aspose.com/pdf/net/aspose.pdf.drawing/circle
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/Add-Circle-in-PDF-Documents-using-CSharp.jpg
 [18]: https://apireference.aspose.com/pdf/net/aspose.pdf.drawing/line
 [19]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/Draw-Line-Across-the-Page-in-PDF-Documents-using-CSharp.png
 [20]: https://apireference.aspose.com/pdf/net/aspose.pdf.text/textfragment
 [21]: https://apireference.aspose.com/pdf/net/aspose.pdf.drawing/ellipse
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/11/Add-Ellipse-in-PDF-Documents-using-CSharp.jpg
 [23]: https://purchase.groupdocs.com/temporary-license
 [24]: https://docs.aspose.com/pdf/net/
 [25]: https://forum.aspose.com/c/pdf
 [26]: https://blog.conholdate.com/2021/09/23/convert-pdf-to-images-using-csharp/








