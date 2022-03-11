---
title: "使用 Java 在 XML 中生成条形码"
author: Muzammil Khan
date: 2021-12-29T10:45:20+00:00
summary: "作为 Java 开发人员，您可以轻松地以编程方式生成不同类型的条形码并保存为 XML。在本文中，您将学习**如何使用 Java 在 XML 中生成条形码**。"
url: /zh/2021/12/29/generate-barcode-in-xml-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "在 Java 中将条码导出为 XML"
  - "在 Java 中从 XML 生成条形码"
  - "在 Java 中生成条形码"
  - "用Java生成二维码"

---

{{< figure align=center src="images/Generate-Barcode-in-XML-using-Java.jpg" alt="使用 Java 在 XML 中生成条形码">}}
 
条形码是机器可读代码中数据的可视化表示。条形码以数字和/或平行线图案的形式包含有关产品或公司的编码信息。条码扫描仪翻译条形图案并将编码信息提取为简单文本。我们可以通过编程方式生成各种类型的条形码。在本文中，我们将学习**如何使用 Java 生成 XML 中的条形码**。

本文将涵盖以下主题：

  * [Java 条码生成器 API][2]
  * [如何在 XML 中生成条形码][3]
  * [以 XML 格式导出条码属性][4]
  * [如何将二维码导出为 XML][5]
  * [如何从 XML 导入条形码][6]

## Java 条码生成器 API – 免费下载 {#Java-Barcode-Generator-API-Free-Download}

为了在 XML 中生成条形码，我们将使用 [Aspose.BarCode for Java][7] API。它有助于生成和读取[广泛的条形码类型][8]。请[下载][9] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置。

```
<repository>
    <id>AsposeJavaAPI</id>
    <name>Aspose Java API</name>
    <url>http://repository.aspose.com/repo/</url>
</repository>
```

```
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-barcode</artifactId>
    <version>21.12</version>
</dependency>
```

## 如何使用 Java 在 XML 中生成条形码 {#How-to-Generate-a-Barcode-in-XML-using-Java}

API 的 [BarcodeGenerator][10] 类允许生成条形码。我们可以使用以下步骤轻松生成条形码并将其保存在 XML 文件中：

  1. 首先，创建 _**[BarcodeGenerator][10]**_ 类的实例，并指定条形码的类型和文本作为参数。
  2. 最后，使用 [_**BarcodeGenerator.exportToXml(String)**_][11] 方法以 XML 格式生成条形码。它将输出文件的路径作为参数。

以下代码示例展示了**如何使用 Java 生成条形码并将其保存在 XML 中**。

```
// 使用 CodeText 和 Barcode Symbology 实例化条形码生成器实例
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.PDF_417,
    "this is some test code text. \n Second line \n third line.");

// 保存为 XML
generator.exportToXml("C:\\Files\\barcode\\barcode_xml_out.xml");
```

{{< figure align=center src="images/How-to-Generate-a-Barcode-in-XML-using-Java.jpg" alt="如何使用 Java 在 XML 中生成条形码。" caption="如何使用 Java 在 XML 中生成条形码。">}}
 
## 使用 Java 以 XML 格式导出条码属性 {#Export-Barcode-Properties-in-XML-using-Java}

我们可以使用以下步骤生成自定义条形码并将所有属性保存在 XML 中：

  1. 首先，创建 _**[BarcodeGenerator][10]**_ 类的实例，并指定条形码的类型和文本作为参数。
  2. 设置各种条码属性，如文本、对齐方式、下方标题和上方标题设置等。
  3. 最后，使用 **_[BarcodeGenerator.exportToXml(String)][11]_** 方法将条形码保存在 XML 中。它将输出文件的路径作为参数。

以下代码示例展示了**如何使用 Java 以 XML 格式导出条形码属性**。

```
// 初始化 BarcodeGenerator 对象
// 将条形码文本和条形码符号系统作为参数传递。
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.DATA_MATRIX, "abcdefghijklmnopqrstuvwxyzabcdef");

// 设置条码的各种不同属性/变量。
generator.getParameters().getBorder().setVisible(true);
generator.getParameters().getBarcode().getCodeTextParameters().setLocation(CodeLocation.ABOVE);

// 指定标题以上设置。
generator.getParameters().getCaptionAbove().setText("Caption ABOVE");
generator.getParameters().getCaptionAbove().setAlignment(TextAlignment.CENTER);
generator.getParameters().getCaptionAbove().setVisible(true);
generator.getParameters().getCaptionAbove().setTextColor(Color.GREEN);

// 指定标题下面的设置。
generator.getParameters().getCaptionBelow().setText("Caption BELOW");
generator.getParameters().getCaptionBelow().setAlignment(TextAlignment.CENTER);
generator.getParameters().getCaptionBelow().setVisible(true);
generator.getParameters().getCaptionBelow().setTextColor(Color.YELLOW);

// 指定文本字体设置。
generator.getParameters().getBarcode().getCodeTextParameters().getFont().setFamilyName("Courier New");
generator.getParameters().getBarcode().getCodeTextParameters().getFont().getSize().setPoint(24);
generator.getParameters().getBarcode().getCodeTextParameters().getFont().setStyle(FontStyle.BOLD);

// 调用 export to XML 方法将属性导出到 XML 文件。
generator.exportToXml("C:\\Files\\barcode\\DataMatrix_out.xml");
```

## 如何使用 Java 将 QR 码导出为 XML {#How-to-Export-a-QR-Code-to-XML-using-Java}

我们还可以使用以下步骤生成二维码并将其保存在 XML 文件中：

  1. 首先，创建 **_[BarcodeGenerator][10]_** 类的实例，并将条形码的类型指定为 QR，将文本指定为参数。
  2. 可选地，设置条形码的特征，例如高度、宽度和分辨率等。
  3. 最后，使用 **_[BarcodeGenerator.exportToXml(String)][11]_** 方法以 XML 格式生成二维码。它将输出文件的路径作为参数。

以下代码示例展示了**如何使用 Java 生成 QR 码并以 XML 格式保存**。

```
// 初始化 BarcodeGenerator 对象
// 将条码符号系统作为 QR 和条码文本作为参数传递。
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "Aspose.BarCode");

// 设置分辨率
generator.getParameters().setResolution(400);

// 以 XML 格式保存二维码
generator.exportToXml("C:\\Files\\barcode\\QR_out.xml");
```

## 如何使用 Java 从 XML 导入条形码 {#How-to-Import-a-Barcode-from-XML-using-Java}

我们可以从 XML 文件中读取条形码属性并使用以下步骤保存条形码图像：

  1. 使用输入 XML 文件路径作为参数调用 **_[BarcodeGenerator.importFromXml()][13]_** 方法。它返回 **_[BarcodeGenerator][10]_** 类对象。
  2. 最后，使用 **_[BarcodeGenerator.save(String)][14]_** 方法保存条形码图像。它将输出文件的路径作为参数。

以下代码示例展示了**如何从 XML 文件中读取条形码并使用 Java 将其保存为图像**。

```
// 从 XML 读取条形码并实例化 BarcodeGenerator 对象
BarcodeGenerator generator = BarcodeGenerator.importFromXml("C:\\Files\\barcode\\barcode_xml_out.xml");

// 将条形码另存为 Jpeg
generator.save("C:\\Files\\barcode\\barcode_xml_out.jpg", BarCodeImageFormat.JPEG);
```

{{< figure align=center src="images/barcode_xml_out.jpg" alt="如何使用 Java 从 XML 生成条形码" caption="如何使用 Java 从 XML 生成条形码">}}
 

## 获得免费许可证

请通过申请 [免费的临时许可证][16] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了**如何使用 Java 生成条形码并以 XML 格式导出**。我们还看到了**如何以 XML 格式生成 QR 码**和 **以编程方式从 XML 文件中导入条形码**。此外，您可以使用 [documentation][17] 了解有关 Aspose.BarCode for Java API 的更多信息。如有任何歧义，请随时在 [论坛][18] 上与我们联系。

## 也可以看看

  * [使用 Java 生成条形码][19]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/12/Generate-Barcode-in-XML-using-Java.jpg
 [2]: #Java-Barcode-Generator-API-Free-Download
 [3]: #How-to-Generate-a-Barcode-in-XML-using-Java
 [4]: #Export-Barcode-Properties-in-XML-using-Java
 [5]: #How-to-Export-a-QR-Code-to-XML-using-Java
 [6]: #How-to-Import-a-Barcode-from-XML-using-Java
 [7]: https://products.aspose.com/barcode/java
 [8]: https://docs.aspose.com/barcode/java/barcode-supported-symbologies/
 [9]: https://downloads.aspose.com/barcode/java
 [10]: https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/barcodegenerator
 [11]: https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeGenerator#exportToXml-java.lang.String-
 [12]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/12/How-to-Generate-a-Barcode-in-XML-using-Java.jpg
 [13]: https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeGenerator#importFromXml-java.lang.String-
 [14]: https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeGenerator#save-java.lang.String-
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/12/barcode_xml_out.jpg
 [16]: https://purchase.conholdate.com/temporary-license
 [17]: https://docs.aspose.com/barcode/java
 [18]: https://forum.aspose.com/c/barcode
 [19]: https://blog.aspose.com/2020/04/07/generate-or-scan-barcodes-qr-codes-in-java-using-java-barcode-library/








