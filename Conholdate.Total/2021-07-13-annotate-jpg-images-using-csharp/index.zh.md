---
title: "'使用 C# 注释 JPG 图像'"
author: Muzammil Khan
date: 2021-07-13T18:03:57+00:00
summary: ".您可以轻松地为 JPG 图像添加注释，并在 .NET 应用程序中添加各种图形、文本和水印注释。在本文中，您将学习**如何使用 C# 注释 JPG 图像**。"
url: /zh/2021/07/13/annotate-jpg-images-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "使用 CSharp 添加区域注释"
  - "使用 CSharp 添加 TextFiled 注释"
  - "使用 CSharp 添加水印注释"
  - "注释 JPG 图像"
  - "用于注释图像的 CSharp API"

---


{{< figure align=center src="images/annotate-jpg-images-using-csharp.jpg" alt="使用 C# 注释 jpg 图像">}}
 

您可以以编程方式注释流行图像格式的图像，例如 JPEG、PNG、TIFF。图像上的注释提供了有关现有数据的附加信息。您可以向 .NET 应用程序中的图像添加范围广泛的图形、文本和水印注释。在本文中，您将学习**如何使用 C# 注释 JPG 图像**。

本文讨论/涵盖了以下主题：

  * [用于注释图像的 C# API][2]
  * [使用 C# 注释 JPG 图像][3]
  * [使用 C# 将区域注释添加到 JPG][4]
  * [使用 C# 将文本字段注释添加到 JPG][5]
  * [使用 C# 使用水印注释 JPG 图像][6]

## 用于注释图像的 C# API {#CSharp-API-to-Annotate-Images}

为了注释 [JPG][7] 图像，我将使用 [GroupDocs.Annotation for .NET][8] API。它允许以编程方式在 C#、ASP.NET 和其他相关 .NET 技术中构建文档注释应用程序。您可以在所有流行格式的文档中添加流行的注释类型，例如区域、点、文本、椭圆、链接、下划线、折线、箭头、距离、水印、图像等。该 API 还允许您在将注释、评论或突出显示的注释添加回其原始格式后导出文档。

您可以[下载][9] API 的 DLL 或使用 [NuGet][10] 安装它。

```
Install-Package GroupDocs.Annotation
```

## 使用 C# 注释 JPG 图像 {#Annotate-JPG-Images}

您可以按照以下步骤添加多个注释来注释您的 JPG 图像：

  * 创建 _**[Annotator][11]**_ 类的实例
  * 提供输入文件路径
  * 创建 [_**ArrowAnnotation**_][12] 类的实例
  * 为 _ArrowAnnotation_ 设置各种属性，例如颜色、不透明度、样式等。
  * 将 _ArrowAnnotation_ 添加到注释列表
  * 创建 [_**DistanceAnnotation**_][13] 类的实例
  * 为 _DistanceAnnotation_ 设置各种属性，例如颜色、不透明度、样式等。
  * 将 _DistanceAnnotation_ 添加到注释列表
  * 创建 [_**EllipseAnnotation**_][14] 类的实例
  * 为 _EllipseAnnotation_ 设置各种属性，例如颜色、不透明度、样式等。
  * 将 _EllipseAnnotation_ 添加到注释列表
  * 创建 [_**PointAnnotation**_][15] 类的实例
  * 为 _PointAnnotation_ 设置各种属性，例如框大小和位置
  * 将 _PointAnnotation_ 添加到注释列表
  * 调用[_Add()_][16]方法给Annotator添加注解
  * 调用 _[Save()][17]_ 方法并保存结果文件

以下代码示例展示了**如何使用 C#** 注释 JPG 图像。

```
// 初始化注释器
Annotator annotator = new Annotator("C:\\Files\\sample.jpg");

List<AnnotationBase> annotations = new List<AnnotationBase>();

// 定义和添加箭头注释
ArrowAnnotation arrow = new ArrowAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PenColor = 16777215,
    PenStyle = PenStyle.DashDotDot,
    PenWidth = 5
};
annotations.Add(arrow);

// 定义和添加距离注释
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(75, 545, 315, 0),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PenColor = 65535,
    PenStyle = PenStyle.Solid,
    PenWidth = 9
};
annotations.Add(distance);

// 定义和添加椭圆注释
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(150, 300, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.3,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3
};
annotations.Add(ellipse);

// 定义和添加点注释
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(75, 605, 10, 10),
    CreatedOn = DateTime.Now,
};
annotations.Add(point);

// 向注释器添加注释
annotator.Add(annotations);

// 保存输出文件
annotator.Save("C:\\Files\\result.jpg");
```

{{< figure align=center src="images/Add-Multiple-Annotations-to-JPG-Images-1024x572.jpg" alt="使用 C# 注释 JPG 图像" caption="使用 C# 注释 JPG 图像">}}
 

[Annotator][11] 类是控制文档注释过程的主要类。它提供了各种方法来添加、更新或删除注释。此类的 [Save()][17] 方法将带注释的文件保存在给定路径。

API 提供了各种特定的类来定义各种类型的注解，例如：

  * ArrowAnnotation 类提供了定义箭头注释的属性
  * 用于定义距离注释的 DistanceAnnotation 类工具
  * EllipseAnnotation 类可用于定义 Ellipse 注释
  * PointAnnotation 类提供定义点注释的属性

## 使用 C# 将区域注释添加到 JPG {#Add-Area-Annotation-to-JPG-using-CSharp}

您可以按照以下步骤以编程方式将区域注释添加到 JPG 图像：

  * 创建 _**[Annotator][11]**_ 类的实例
  * 提供输入文件路径
  * 创建 [_**AreaAnnotation**_][19] 类的实例
  * 为 _AreaAnnotation_ 设置各种属性，例如位置、颜色、消息、不透明度、样式等。
  * 调用 [_Add()_][20] 方法将 _AreaAnnotation_ 添加到 Annotator
  * 调用 _[Save()][17]_ 方法并保存结果文件

以下代码示例展示了**如何使用 C# 向 JPG 图像添加区域注释**。

```
// 初始化注释器
Annotator annotator = new Annotator("C:\\Files\\sample.jpg");

// 定义区域注释
AreaAnnotation area = new AreaAnnotation();
area.BackgroundColor = 65535;
area.Box = new Rectangle(80, 575, 310, 50);
area.CreatedOn = DateTime.Now;
area.Opacity = 0.7;
area.PageNumber = 0;
area.PenColor = 65535;
area.PenStyle = PenStyle.Dot;
area.PenWidth = 3;

// 添加区域注释
annotator.Add(area);

// 保存输出文件
annotator.Save("C:\\Files\\result.jpg");
```

{{< figure align=center src="images/Add-Area-Annotation-to-JPG-1024x653.jpg" alt="使用 C# 将区域注释添加到 JPG" caption="使用 C# 将区域注释添加到 JPG">}}
 

## 使用 C# 将文本字段注释添加到 JPG {#Add-Text-Field-Annotation-to-JPG-using-CSharp}

您可以按照以下步骤为您的 JPG 图像添加文本字段注释：

  * 创建 _**[Annotator][11]**_ 类的实例
  * 提供输入文件路径
  * 创建 [_**TextFieldAnnotation**_][22] 类的实例
  * 为 _TextFieldAnnotation_ 设置各种属性，例如文本、颜色、不透明度、样式、字体等。
  * 调用 [_Add()_][20] 方法将 _TextFieldAnnotation_ 添加到 Annotator
  * 调用 _[Save()][17]_ 方法并保存结果文件

以下代码示例展示了**如何使用 C# 向 JPG 图像添加文本字段注释**。

```
// 初始化注释器
Annotator annotator = new Annotator("C:\\Files\\sample.jpg");

// 定义文本字段注释
TextFieldAnnotation textField = new TextFieldAnnotation();
textField.Box = new Rectangle(130, 120, 270, 30);
textField.CreatedOn = DateTime.Now;
textField.Text = "Document Automation APIs";
textField.FontColor = 16777215;
textField.FontSize = 12;
textField.Opacity = 1;
textField.PenStyle = PenStyle.Dot;
textField.PenWidth = 3;
textField.FontFamily = "Arial";
textField.TextHorizontalAlignment = HorizontalAlignment.Center;

// 添加文本字段注释
annotator.Add(textField);

// 保存输出文件
annotator.Save("C:\\Files\\result.jpg");
```

{{< figure align=center src="images/Add-Text-Field-Annotation-to-JPG-1024x653.jpg" alt="使用 C# 将文本字段注释添加到 JPG" caption="使用 C# 将文本字段注释添加到 JPG">}}
 

## 使用 C# 注释带有水印的 JPG 图像 {#Annotation-JPG-Images-with-Watermark-using-CSharp}

您可以按照以下步骤为您的 JPG 图像添加水印文本：。

  * 创建 _**[Annotator][11]**_ 类的实例
  * 提供输入文件路径
  * 创建 [_**WatermarkAnnotation**_][24] 类的实例
  * 为 _WatermarkAnnotation_ 设置各种属性，例如文本、颜色、字体大小、对齐方式等。
  * 调用 [_Add()_][20] 方法将 WatermarkAnnotation 添加到 Annotator
  * 调用 _[Save()][17]_ 方法并保存结果文件

以下代码示例显示了**如何使用 C#** 使用水印文本注释 JPG 图像。

```
// 初始化注释器
Annotator annotator = new Annotator("C:\\Files\\sample.jpg");

// 定义水印注释
WatermarkAnnotation watermark = new WatermarkAnnotation();
watermark.Text = "This is a sample Watermark";
watermark.FontColor = 16777215;
watermark.FontSize = 22;
watermark.Opacity = 0.7;
watermark.HorizontalAlignment = HorizontalAlignment.Center;
watermark.VerticalAlignment = VerticalAlignment.Center;

// 添加水印注释
annotator.Add(watermark);

// 保存输出文件
annotator.Save("C:\\Files\\result.jpg");
```

{{< figure align=center src="images/Annotation-JPG-Images-with-Watermark-1024x648.jpg" alt="带水印的注释图像" caption="使用 C# 注释带有水印的 JPG 图像">}}
 

## 获得免费许可证

您可以通过请求 [免费的临时许可证][26] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C# 注释 JPG 图像**。您还学习了**如何为 JPG 图像添加多个注释**。此外，您还学习了**如何在 C# 中以编程方式向 JPG 图像添加区域、文本字段和水印注释**。您可以使用 [documentation][27] 了解有关 .NET API 的 GroupDocs.Annotation 的更多信息。如有任何歧义，请随时在 [论坛][28] 上与我们联系。

## 也可以看看

  * [使用 C# 添加或删除注释或标记 Word 文件][29]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/07/annotate-jpg-images-using-csharp.jpg
 [2]: #CSharp-API-to-Annotate-Images
 [3]: #Annotate-JPG-Images
 [4]: #Add-Area-Annotation-to-JPG-using-CSharp
 [5]: #Add-Text-Field-Annotation-to-JPG-using-CSharp
 [6]: #Annotation-JPG-Images-with-Watermark-using-CSharp
 [7]: https://docs.fileformat.com/image/jpeg/
 [8]: https://products.groupdocs.com/annotation/net/
 [9]: https://downloads.groupdocs.com/annotation/net
 [10]: https://www.nuget.org/packages/GroupDocs.Annotation
 [11]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
 [12]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/arrowannotation
 [13]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/distanceannotation
 [14]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/ellipseannotation
 [15]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/pointannotation
 [16]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.annotator/add/methods/1
 [17]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.annotator/save/methods/4
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/07/Add-Multiple-Annotations-to-JPG-Images.jpg
 [19]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation
 [20]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add
 [21]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/07/Add-Area-Annotation-to-JPG.jpg
 [22]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation
 [23]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/07/Add-Text-Field-Annotation-to-JPG.jpg
 [24]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation
 [25]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/07/Annotation-JPG-Images-with-Watermark.jpg
 [26]: https://purchase.groupdocs.com/temporary-license
 [27]: https://docs.groupdocs.com/annotation/net/
 [28]: https://forum.groupdocs.com/c/annotation/
 [29]: https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/








