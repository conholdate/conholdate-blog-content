---
title: "创建具有条码功能的 ASP.NET PDF 编辑器"
author: Muhammad Sohail
date: 2020-07-10T23:31:48+00:00
url: /zh/2020/07/10/create-asp.net-pdf-editor-with-barcode-features/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "asp.net pdf编辑器"
  - "asp.net pdf编辑器 with barcode"
  - "在 asp.net 中创建带有条形码的 pdf"
  - "生成带有条形码的 pdf 发票"

---
[PDF][1]（便携式文档格式）已成为数字文档世界中广泛使用的格式之一。各个行业都在使用 PDF 格式来生成他们的报告、发票、账单和其他类型的业务文档。另一方面，条形码已成为包含机器可读形式信息的业务的重要组成部分。如今，您甚至可以在账单和发票上找到条形码。在本文中，我将介绍一个用例，您需要创建 PDF 文件并在其上嵌入条形码，例如在生成发票时。为了演示，我将创建一个 ASP.NET PDF 编辑器，您可以使用它在 ASP.NET Core Web 应用程序中使用 C# 生成 PDF 文件和条形码。

此 ASP.NET Web 应用程序将具有以下功能：

  * 一个所见即所得的编辑器，用于编写 PDF 文档的内容。
  * 根据提供的文本生成条形码的选项。
  * 用于设置所需条码符号系统的选项。

## 在 ASP.NET 中生成具有条形码的 PDF 的先决条件

以下是创建具有条形码功能的 ASP.NET PDF 编辑器所需的工具和 API。

  * Visual Studio 2017 或更高版本。
  * [Aspose.PDF for .NET][2] &#8211; A .NET PDF API.
  * [Aspose.BarCode for .NET][3] &#8211; .NET Barcode Generator and Scanner API.

## 创建具有条码功能的 ASP.NET PDF 编辑器

让我们开始我们的旅程，看看如何创建我们的 ASP.NET PDF 编辑器，只需单击一下即可生成 PDF 和嵌入条形码。

  * 在 Visual Studio 中创建一个新的 **ASP.NET Core Web 应用程序**。

{{< figure align=center src="images/ASP.NET-Core-MVC-Web-Application.jpg" alt="创建 ASP.NET Core Web 应用程序">}}
 

  * 从模板中选择**Web 应用程序（模型-视图-控制器）**。

{{< figure align=center src="images/MVC-Project-Template.jpg" alt="ASP.NET MVC">}}
 

  * 安装 **Aspose.PDF**、**Aspose.BarCode** 和 **CKEditor** 的软件包。

{{< figure align=center src="images/NPM-.jpg" alt="添加 Aspose .NET PDF 和条形码 API">}}
 

  * 下载CKEditor的[package][4]，解压，复制/粘贴文件夹到**wwwroot**目录。您还可以根据您的要求集成任何您喜欢的 WYSIWYG HTML 编辑器。

  * 在 **Views/Home/index.cshtml** 视图中添加以下脚本。

```
@{
    ViewData["Title"] = "PDF Creator";
}
<script src="~/ckeditor/ckeditor.js"></script>
<br />
<form method="post">
    <div class="row">
        <div class="col-md-12">
            <textarea name="editor1" id="editor1" rows="80" cols="80">
                Start creating your PDF document.
            </textarea>
            <br />
            <script>
                // Replace the <textarea id="editor1"> with a CKEditor
                // instance, using default configuration.
                CKEDITOR.replace('editor1');
            </script>
        </div>
        <hr />
    </div>
    <div class="row">
        <div class="col-md-12">
            <h3>Create a Barcode</h3>
        </div>
    </div>
    <hr />
    <div class="row">
        <div class="col-md-9 form-horizontal" align="center">
            <div class="form-group">
                <label class="control-label col-sm-2" for="CodeText">Code Text</label>
                <div class="col-sm-10">
                    <input class="form-control" type="text" name="codeText" id="codeText" placeholder="Code text" />
                </div>
            </div>
            <div class="form-group">
                <label class="control-label col-sm-2" for="barcodeType">Symbology</label>
                <div class="col-sm-10">
                    <select name="barcodeType" class="form-control">
                        <option value="Code128">Code128</option>
                        <option value="Code11">Code11</option>
                        <option value="QR">QR</option>
                        <option value="Pdf417">Pdf417</option>
                        <option value="Datamatrix">Datamatrix</option>
                    </select>
                </div>
            </div>
        </div>
    </div>
    <hr />
    <div class="row">
        <div class="col-md-12" align="center">
            <input type="submit" class="btn btn-lg btn-success" value="Generate PDF" />
        </div>
    </div>
</form>
```

  * 在 **Controllers/HomeController.cs** 中添加以下方法。

```
[HttpPost]
public FileResult Index(string editor1, string codeText, string barcodeType)
{
	// generate a barcode
	string barcodeImagePath = Path.Combine("wwwroot/barcodes/", Guid.NewGuid() + ".png");
	SymbologyEncodeType type = GetBarcodeSymbology(barcodeType);
	BarcodeGenerator generator = new BarcodeGenerator(type, codeText);
	generator.Parameters.BackColor = System.Drawing.Color.Transparent;
	// set resolution of the barcode image
	generator.Parameters.Resolution = 200;
	// generate barcode
	generator.Save(barcodeImagePath, BarCodeImageFormat.Png);

	// create a unique file name for PDF
	string fileName = Guid.NewGuid() + ".pdf";
	// convert HTML text to stream
	byte[] byteArray = Encoding.UTF8.GetBytes(editor1);
	// generate PDF from the HTML
	MemoryStream stream = new MemoryStream(byteArray);
	HtmlLoadOptions options = new HtmlLoadOptions();
	Document pdfDocument = new Document(stream, options);

	// add barcode image to the generated PDF 
	pdfDocument = InsertImage(pdfDocument, barcodeImagePath);

	// create memory stream for the PDF file
	Stream outputStream = new MemoryStream();
	// save PDF to output stream
	pdfDocument.Save(outputStream);

	// return generated PDF file
	return File(outputStream, System.Net.Mime.MediaTypeNames.Application.Pdf, fileName);
}
private SymbologyEncodeType GetBarcodeSymbology(string symbology)
{
	if (symbology.ToLower() == "qr")
		return EncodeTypes.QR;
	else if (symbology.ToLower() == "code128")
		return EncodeTypes.Code128;
	else if (symbology.ToLower() == "code11")
		return EncodeTypes.Code11;
	else if (symbology.ToLower() == "pdf417")
		return EncodeTypes.Pdf417;
	else if (symbology.ToLower() == "datamatrix")
		return EncodeTypes.DataMatrix;
	else
		return EncodeTypes.Code128; // default barcode type
}
private Document InsertImage(Document document, string barcodeImagePath)
{
	// get page from Pages collection of PDF file
	Aspose.Pdf.Page page = document.Pages[1];
	// create an image instance
	Aspose.Pdf.Image img = new Aspose.Pdf.Image();
	img.IsInLineParagraph = true;
	// set Image Width and Height in Points
	img.FixWidth = 100;
	img.FixHeight = 100;
	img.HorizontalAlignment = HorizontalAlignment.Right;
	img.VerticalAlignment = VerticalAlignment.Top;
	// set image type as SVG
	img.FileType = Aspose.Pdf.ImageFileType.Unknown;
	// path for source barcode image file
	img.File = barcodeImagePath;
	page.Paragraphs.Add(img);
	// return updated PDF document
	return document;
}
```

  * 构建应用程序并在您喜欢的浏览器中运行它。

{{< figure align=center src="images/Generate-PDF-with-Barcode-in-ASP.NET_.jpg" alt="具有条码功能的 ASP.NET PDF 编辑器">}}
 

## 使用 ASP.NET PDF 编辑器生成 PDF

以下是如何通过单击生成 PDF 文件和嵌入条形码的步骤和演示。

  * 在编辑器区域写入或复制/粘贴 PDF 文档的内容。
  * 设置代码文本以生成条形码。
  * 选择您想要的条码符号（查看所有[支持的条码符号][5]）。
  * 单击 **Generate PDF** 按钮以创建带有条形码的 PDF。 <figure class="wp-block-embed-youtube wp-block-embed is-type-video is-provider-youtube wp-embed-aspect-4-3 wp-has-aspect-ratio">

<div class="wp-block-embed__wrapper">
</div></figure>

## 下载源代码

您可以从 [此处][6] 下载此 ASP.NET PDF 编辑器的完整源代码。

## 免费试用 Aspose API

获取您的 [临时许可证][7] 并免费试用我们的 API 一个月。

## 也可以看看

  * [在 ASP.NET 中创建您自己的 Google Docs 类应用程序][8]

 [1]: https://docs.fileformat.com/pdf/
 [2]: https://products.aspose.com/pdf/net
 [3]: https://products.aspose.com/barcode/net
 [4]: https://ckeditor.com/ckeditor-4/download/
 [5]: https://docs.aspose.com/display/barcodenet/Barcode+Supported+Symbologies
 [6]: https://github.com/usman-aziz/ASP.NET-PDF-Editor-with-Barcode
 [7]: https://purchase.conholdate.com/temporary-license
 [8]: https://blog.conholdate.com/2020/06/22/build-your-own-google-docs-like-app/








