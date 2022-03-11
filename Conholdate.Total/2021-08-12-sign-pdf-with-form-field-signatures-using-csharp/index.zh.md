---
title: "'使用 C# 使用表单字段签名签署 PDF'"
author: Muzammil Khan
date: 2021-08-12T06:03:00+00:00
summary: "作为 C# 开发人员，您可以轻松创建 PDF 文档以供用户以电子方式填写和签名。在本文中，您将学习**如何使用 C# 对带有表单字段签名的 PDF 文档进行电子签名**。"
url: /zh/2021/08/12/sign-pdf-with-form-field-signatures-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "GroupDocs.Signature .NET"
  - "PDF 表单字段签名"
  - "签署 PDF 文件"
  - "使用表单字段签名签署 PDF"

---


{{< figure align=center src="images/sign-pdf-with-form-field-signatures-using-csharp.jpg" alt="使用 C# 使用表单字段签名签署 PDF">}}
 

表单字段是用于从用户那里收集信息的各种类型的数据字段。作为 C# 开发人员，您可以轻松创建 PDF 文档以供用户以电子方式填写和签名。这有助于收集客户反馈、合作伙伴的同意等。在本文中，您将学习**如何使用 C# 对带有表单字段签名的 PDF 文档进行电子签名**。

本文讨论/涵盖了以下主题：

  * [用于签署 PDF 文档的 C# API][2]
  * [使用 C# 使用表单字段签名签署 PDF 文档][3]
  * [使用 C# 签署具有多个表单字段签名的 PDF 文档][4]

## 用于签署 PDF 文档的 C# API {#api-for-signing-documents}

我将使用 [GroupDocs.Signature for .NET][5] API 对启用表单字段签名的 [PDF][6] 文档进行签名。 API 允许您将数字签名添加到 [支持的文档格式][7] 并在您的 .NET 应用程序中实现流行的电子签名类型。它还使您能够使用简单和高级的搜索选项在文档上找到所需的签名。

## 使用 C# 使用表单字段签名签署 PDF 文档 {#Sign-PDF-Documents-with-Form-Field-Signatures-using-CSharp}

您可以使用以下类型的表单域签名以编程方式对 PDF 文档进行电子签名：

  * [文本表单字段签名][8]
  * [单选按钮表单字段签名][9]
  * [组合框表单字段签名][10]
  * [复选框表单字段签名][11]
  * [数字表单字段签名][12]

### 使用文本表单字段签名为 PDF 文档签名 {#Sign-PDF-Documents-with-Text-Form-Field-Signatures}

您可以按照以下提到的简单步骤使用文本表单字段签名签署 PDF 文档：

  * 创建 _[Signature][13]_ 类的实例
  * 提供输入 PDF 文档的路径
  * 创建 _TextFormFieldSignature_ 类的实例
  * 使用 _TextFormFieldSignature_ 对象创建 _[FormFieldSignOptions][14]_ 类的实例
  * 设置所需的符号选项，例如边距、高度、宽度等。
  * 使用 _FormFieldSignOptions_ 和输出文件路径调用 [_Sign()_][15] 方法

以下代码示例显示**如何使用 C# 对带有文本表单字段签名的 PDF 文档进行电子签名**。

```
// 创建一个签名实例
Signature signature = new Signature(@"C:\Files\sample.pdf");

// 实例化文本表单字段签名
TextFormFieldSignature textSignature = new TextFormFieldSignature("textBoxData1", "Enter Your Name");
// 基于文本表单字段签名实例化选项
FormFieldSignOptions optionsTextFF = new FormFieldSignOptions(textSignature);
optionsTextFF.HorizontalAlignment = HorizontalAlignment.Center;
optionsTextFF.VerticalAlignment = VerticalAlignment.Top;
optionsTextFF.Margin = new Padding(20, 0, 170, 0);
optionsTextFF.Height = 50;
optionsTextFF.Width = 200;

// 签署文件归档
signature.Sign(@"C:\Files\TextFormFieldSignature.pdf", optionsTextFF);
```

[Signature][13] 类是控制文档签名过程的主要类。它提供了多种方法来签名、搜索、删除或验证文档中的签名。此类的 [Sign()][15] 方法用于使用已定义的 SignOptions 对文档进行签名。

[TextFormFieldSignature][16] 类为 PDF 文档提供文本输入表单字段签名属性。

### 使用单选按钮表单字段签名为 PDF 文档签名 {#Sign-PDF-Documents-with-Radio-Button-Form-Field-Signatures}

您可以按照前面提到的步骤使用单选按钮表单字段签名对 PDF 文档进行签名。但是，您需要创建 _RadioButtonFormFieldSignature_ 类的实例而不是 _TextFormFieldSignature_。

以下代码示例显示**如何使用 C# 对带有单选按钮表单字段签名的 PDF 文档进行电子签名**。

```
// 创建一个签名实例
Signature signature = new Signature(@"C:\Files\sample.pdf");

// 实例化单选按钮表单字段签名
List<string> radioOptions = new List<string>() { "Male", "Female" };
RadioButtonFormFieldSignature rbSignature = new RadioButtonFormFieldSignature("radioData1", radioOptions, "Male");
// 基于文本表单字段签名实例化选项
FormFieldSignOptions optionsTextRB = new FormFieldSignOptions(rbSignature);
optionsTextRB.HorizontalAlignment = HorizontalAlignment.Center;
optionsTextRB.VerticalAlignment = VerticalAlignment.Top;
optionsTextRB.Margin = new Padding(20, 0, 170, 0);
optionsTextRB.Height = 50;
optionsTextRB.Width = 200;

// 签署文件归档
signature.Sign(@"C:\Files\RadioButtonFormFieldSignature.pdf", optionsTextRB);
```

[RadioButtonFormFieldSignature][17] 类为 PDF 文档提供单选按钮输入表单字段签名属性。

### 使用组合框表单字段签名为 PDF 文档签名 {#Sign-PDF-Documents-with-Combobox-Form-Field-Signatures}

您可以按照前面提到的步骤使用 Combobox 表单字段签名对 PDF 文档进行签名。但是，您需要创建 _ComboboxFormFieldSignature_ 而不是 _TextFormFieldSignature_ 的实例。

以下代码示例显示**如何使用 C# 对带有 Combobox 表单字段签名的 PDF 文档进行电子签名**。

```
// 创建一个签名实例
Signature signature = new Signature(@"C:\Files\sample.pdf");

// 实例化组合框表单字段签名
List<string> items = new List<string>() { "Australia", "United Kingdom", "United States" };
ComboboxFormFieldSignature cmbSignature = new ComboboxFormFieldSignature("combo1", items, "Australia");
// 基于文本表单字段签名实例化选项
FormFieldSignOptions optionsTextCMB = new FormFieldSignOptions(cmbSignature);
optionsTextCMB.HorizontalAlignment = HorizontalAlignment.Center;
optionsTextCMB.VerticalAlignment = VerticalAlignment.Top;
optionsTextCMB.Margin = new Padding(20, 0, 238, 0);
optionsTextCMB.Height = 20;
optionsTextCMB.Width = 200;

// 签署文件归档
signature.Sign(@"C:\Files\ComboboxFormFieldSignature.pdf", optionsTextCMB);
```

[ComboboxFormFieldSignature][18] 类为 PDF 文档提供组合框输入表单字段签名属性。

### 使用复选框表单字段签名为 PDF 文档签名 {#Sign-PDF-Documents-with-Checkbox-Form-Field-Signatures}

您可以按照前面提到的相同步骤使用复选框表单字段签名来签署 PDF 文档。但是，您需要创建 _CheckboxFormFieldSignature_ 而不是 _TextFormFieldSignature_ 的实例。

以下代码示例显示**如何使用复选框表单字段签名对 PDF 文档进行电子签名**。

```
// 创建一个签名实例
Signature signature = new Signature(@"C:\Files\sample.pdf");

List<SignOptions> listOptions = new List<SignOptions>();

// 实例化文本表单字段签名
CheckboxFormFieldSignature chbSignature = new CheckboxFormFieldSignature("chbData1", true);
// 基于文本表单字段签名实例化选项
FormFieldSignOptions optionsTextCHB = new FormFieldSignOptions(chbSignature);
optionsTextCHB.HorizontalAlignment = HorizontalAlignment.Center;
optionsTextCHB.VerticalAlignment = VerticalAlignment.Top;
optionsTextCHB.Margin = new Padding(20, 0, 270, 0);
optionsTextCHB.Height = 20;
optionsTextCHB.Width = 20;

// 签署文件归档
signature.Sign(@"C:\Files\CheckboxFormFieldSignature.pdf", optionsTextCHB);
```

[CheckboxFormFieldSignature][19] 类为 PDF 文档提供复选框输入表单字段签名属性。

### 使用数字表单字段签名为 PDF 文档签名 {#Sign-PDF-Documents-with-Digital-Form-Field-Signatures}

您可以按照前面提到的相同步骤，使用数字表单字段签名签署 PDF 文档。但是，您需要创建 _DigitalFormFieldSignature_ 而不是 _TextFormFieldSignature_ 的实例。

以下代码示例显示**如何使用数字表单字段签名对 PDF 文档进行电子签名**。

```
// 创建一个签名实例
Signature signature = new Signature(@"C:\Files\sample.pdf");

// 实例化文本表单字段签名
DigitalFormFieldSignature digSignature = new DigitalFormFieldSignature("dgData1");
// 基于文本表单字段签名实例化选项
FormFieldSignOptions optionsTextDIG = new FormFieldSignOptions(digSignature);
optionsTextDIG.HorizontalAlignment = HorizontalAlignment.Center;
optionsTextDIG.VerticalAlignment = VerticalAlignment.Top;
optionsTextDIG.Margin = new Padding(20, 0, 300, 0);
optionsTextDIG.Height = 50;
optionsTextDIG.Width = 200;
optionsTextDIG.ForeColor = System.Drawing.Color.Yellow;

// 签署文件归档
signature.Sign(@"C:\Files\DigitalFormFieldSignature.pdf", optionsTextDIG);
```

[DigitalFormFieldSignature][20] 类为 PDF 文档提供数字签名输入表单字段属性。用户应能够在此字段中使用自己的数字签名签署文件。

## 使用 C# 签署具有多个表单字段签名的 PDF 文档 {#Sign-PDF-Documents-with-Multiple-Form-Field-Signatures-using-CSharp}

您可以按照以下提到的简单步骤以编程方式使用多个表单域签名对您的 PDF 文档进行电子签名：

  * 创建 _[Signature][13]_ 类的实例
  * 提供输入 PDF 文档的路径
  * 定义 _[SignOptions][21]_ 的列表
  * 创建 _FormFieldSignature_ 对象
  * 为创建的 _FormFieldSignature_ 对象创建 _[FormFieldSignOptions][14]_ 的实例
  * 为每个对象设置所需的符号选项，例如位置（边距、高度、宽度等）
  * 将 _FormFieldSignOptions_ 对象添加到 _SignOptions_ 列表
  * 使用 _SignOptions_ 和输出文件路径调用 [_Sign()_][22] 方法

以下代码示例显示**如何使用 C# 对具有多个表单域签名的 PDF 文档进行电子签名**。

```
// 创建一个签名实例
Signature signature = new Signature(@"C:\Files\sample.pdf");

List<SignOptions> listOptions = new List<SignOptions>();

// 实例化文本表单字段签名
TextFormFieldSignature textSignature = new TextFormFieldSignature("tbData1", "Enter Your Name");
// 基于文本表单字段签名实例化选项
FormFieldSignOptions optionsTextFF = new FormFieldSignOptions(textSignature)
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Top,
    Margin = new Padding(20, 0, 138, 0),
    Height = 20,
    Width = 200
};

// 实例化单选按钮表单字段签名
List<string> radioOptions = new List<string>() { "Male", "Female" };
RadioButtonFormFieldSignature rbSignature = new RadioButtonFormFieldSignature("radioData1", radioOptions, "Male");
// 基于文本表单字段签名实例化选项
FormFieldSignOptions optionsTextRB = new FormFieldSignOptions(rbSignature)
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Top,
    Margin = new Padding(20, 0, 170, 0),
    Height = 50,
    Width = 200,
};

// 实例化组合框表单字段签名
List<string> items = new List<string>() { "Australia", "United Kingdom", "United States" };
ComboboxFormFieldSignature cmbSignature = new ComboboxFormFieldSignature("combo1", items, "Australia");
// 基于文本表单字段签名实例化选项
FormFieldSignOptions optionsTextCMB = new FormFieldSignOptions(cmbSignature)
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Top,
    Margin = new Padding(20, 0, 238, 0),
    Height = 20,
    Width = 200,
};

// 实例化文本表单字段签名
CheckboxFormFieldSignature chbSignature = new CheckboxFormFieldSignature("chbData1", true);
// 基于文本表单字段签名实例化选项
FormFieldSignOptions optionsTextCHB = new FormFieldSignOptions(chbSignature)
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Top,
    Margin = new Padding(20, 0, 270, 0),
    Height = 20,
    Width = 20,
};


// 实例化数字表单域签名
DigitalFormFieldSignature digSignature = new DigitalFormFieldSignature("dgData1");
// 基于文本表单字段签名实例化选项
FormFieldSignOptions optionsTextDIG = new FormFieldSignOptions(digSignature)
{
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Top,
    Margin = new Padding(20, 0, 300, 0),
    Height = 50,
    Width = 200,
};

// 将表单字段添加到签名选项列表
listOptions.Add(optionsTextFF);
listOptions.Add(optionsTextCHB);
listOptions.Add(optionsTextRB);
listOptions.Add(optionsTextCMB);
listOptions.Add(optionsTextDIG);

// 签署文件归档
signature.Sign(@"C:\Files\Signature\sample_output.pdf", listOptions);
```

{{< figure align=center src="images/Sign-PDF-Documents-with-Form-Field-Signatures-using-CSharp-1024x987.jpg" alt="使用 C# 签署具有多个表单字段签名的 PDF 文档" caption="使用 C# 签署具有多个表单字段签名的 PDF 文档">}}
 

_**Signature**_ 类的 [Sign()][22] 方法用于使用 SignOptions 列表对文档进行签名。 [SignOptions][21] 类允许设置签名选项，例如外观、签名类型等。

[FormFieldSignOptions][14] 类为 PDF 文档提供表单域签名选项。您可以定义表单域选项，例如 HorizontalAlignment、VerticalAlignment、Margin、Height 和 Width。在创建 FormFieldSignOptions 类的实例时，您需要提供 FormFieldSignature 类之一的已定义对象。

## 获得免费许可证

您可以通过请求 [免费的临时许可证][24] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C# 创建带有表单字段签名的 PDF**。您还学习了**如何以编程方式对具有各种表单字段签名类型的 PDF 文档进行电子签名**。您可以使用 [文档][25] 了解有关 .NET API 的 GroupDocs.Signature 的更多信息。如有任何歧义，请随时在 [论坛][26] 上与我们联系。

## 也可以看看

  * [在 C# 中生成条形码][27]
  * [使用 C# 使用数字证书签署文档][28]
  * [在 C# 中生成二维码][29]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/sign-pdf-with-form-field-signatures-using-csharp.jpg
 [2]: #api-for-signing-documents
 [3]: #Sign-PDF-Documents-with-Form-Field-Signatures-using-CSharp
 [4]: #Sign-PDF-Documents-with-Multiple-Form-Field-Signatures-using-CSharp
 [5]: https://products.groupdocs.com/signature/net
 [6]: https://docs.fileformat.com/pdf/
 [7]: https://docs.groupdocs.com/signature/net/supported-document-formats/
 [8]: #Sign-PDF-Documents-with-Text-Form-Field-Signatures
 [9]: #Sign-PDF-Documents-with-Radio-Button-Form-Field-Signatures
 [10]: #Sign-PDF-Documents-with-Combobox-Form-Field-Signatures
 [11]: #Sign-PDF-Documents-with-Checkbox-Form-Field-Signatures
 [12]: #Sign-PDF-Documents-with-Digital-Form-Field-Signatures
 [13]: https://apireference.groupdocs.com/signature/net/groupdocs.signature/signature
 [14]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.options/formfieldsignoptions
 [15]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.signature/sign/methods/4
 [16]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.domain/textformfieldsignature
 [17]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.domain/radiobuttonformfieldsignature
 [18]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.domain/comboboxformfieldsignature
 [19]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.domain/checkboxformfieldsignature
 [20]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.domain/digitalformfieldsignature
 [21]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.options/signoptions
 [22]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.signature/sign/methods/6
 [23]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/Sign-PDF-Documents-with-Form-Field-Signatures-using-CSharp.jpg
 [24]: https://purchase.groupdocs.com/temporary-license
 [25]: https://docs.groupdocs.com/signature/net/
 [26]: https://forum.groupdocs.com/c/signature/
 [27]: https://blog.groupdocs.com/2021/07/14/generate-barcode-in-csharp-to-sign-documents-and-images/
 [28]: https://blog.groupdocs.com/2021/03/11/sign-documents-with-digital-certificate-using-csharp/
 [29]: https://blog.groupdocs.com/2021/01/27/generate-qr-codes-in-csharp-to-sign-documents-and-images/








