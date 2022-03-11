---
title: "构建您自己的 Google Docs like App（第二部分）"
author: Muhammad Sohail
date: 2020-06-29T13:25:59+00:00
url: /zh/2020/06/29/build-your-own-google-docs-like-app-part-two/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "协作编辑"
  - "以 PDF 格式下载内容"
  - "将内容下载为 Word 文档"
  - "实时编辑"

---
在 [第一篇博文][1] 中，我们创建了一个类似 Google Docs 的网络应用程序，它具有以下功能：

  * 富文本编辑（更改文本字体、大小、颜色、样式（粗体、斜体）、对齐方式等）。
  * 同一文档的实时协作编辑。多个用户可以同时访问文档并对其进行修改。
  * 将现有 Word 文档的内容上传到编辑器中。

在这篇博文中，我们将扩展我们的 Web 应用程序以包含以下功能：

  * 将编辑器的内容下载为 MS Word、PDF、TXT 或 HTML 文档。
  * 与朋友共享 URL，以便他们可以同时编辑文档。

最终产品如下所示：

{{< figure align=center src="images/Real-Time-Collaborative-Text-Editor-1-1024x505.jpg" alt="类似应用界面的 Google Docs">}}
 

  * 将编辑器的内容下载为
      * [微软 Word 文档][2]
      * [PDF文件][3]
      * [纯文本文档][4]
  * [与朋友分享编辑器的 URL][5]

## 将编辑器的内容下载为 Microsoft Word 文档 {#Download-Content-As-MS-Word}

首先，我们添加一个**`<input> `** **submit** 类型的元素到我们的 **form** 以在前端显示“**Download Document**”按钮。我们使用 **asp-page-handler** 属性来指定按钮的处理程序。我们的表单元素现在如下所示：

```
<form method="post" enctype="multipart/form-data" id="uploadForm">
    <input asp-for="UploadedDocument" />
    
    <input type="submit" value="Upload Document" class="btn btn-primary" asp-page-handler="UploadDocument" />
    <input type="submit" value="Download Document" class="btn btn-primary" asp-page-handler="DownloadDocument" />

    <input asp-for="DocumentContent" type="hidden" />
</form>
```

您可能已经注意到我们添加了另一个**`<input> `** **隐藏**类型的元素。此元素绑定到 **Index.cshtml.cs** 中的 **DocumentContent** 属性。我们将使用此属性将编辑器的内容存储为 HTML 字符串。

```
[BindProperty]
public string DocumentContent { get; set; }
```

[Firepad][6] 提供另一个事件 **synced** 用于监听。当我们的本地客户端编辑文档并且这些编辑已成功写入 Firebase 时，它会被触发。我们将回调附加到此事件类型，以便将 **DocumentContent** 属性的值设置为 **firepad.getHtml()**。请在 **Index.cshtml** 中的 **init()** 函数中添加以下代码。

```
firepad.on('synced', function (isSynced) {
    // isSynced will be false immediately after the user edits 
    // the pad, and true when their edit has been saved to Firebase.
    if (isSynced) {
        document.getElementById("DocumentContent").value = firepad.getHtml();
    }
});
```

现在我们实现 **OnPostDownloadDocument()** 处理程序的功能。我们使用 [GroupDocs.Editor][7] 库将编辑器的内容保存为 Microsoft Word 文档，存储在 **DocumentContent** 属性中。处理程序返回 Word 文档作为对用户的响应。

```
public FileResult OnPostDownloadDocument()
{
    // Editor object is referencing to the document initially uploaded for editing.
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Editor editor = new Editor(UploadedDocumentPath, delegate { return loadOptions; });
    
    // <html>, <head> and <body> tags are missing in the HTML string stored in DocumentContent, so we are adding them manually.
    string completeHTML = "<!DOCTYPE html><html><head><title></title></head><body>" + DocumentContent + "</body></html>";
    EditableDocument document = EditableDocument.FromMarkup(completeHTML, null);
    
    // Path to the output document        
    var projectRootPath = Path.Combine(_hostingEnvironment.ContentRootPath, "DownloadedDocuments");
    var outputPath = Path.Combine(projectRootPath, Path.GetFileName(UploadedDocumentPath));
    
    // Save the Word Document at the outputPath 
    WordProcessingSaveOptions saveOptions = new WordProcessingSaveOptions(WordProcessingFormats.Docx);
    editor.Save(document, outputPath, saveOptions);
    
    // Return the Word Document as response to the User
    var bytes = System.IO.File.ReadAllBytes(outputPath);        
    return new FileContentResult(bytes, new MediaTypeHeaderValue("application/vnd.openxmlformats-officedocument.wordprocessingml.document"))
    {
        FileDownloadName = Path.GetFileName(UploadedDocumentPath)
    };
}
```

**UploadedDocumentPath** 变量定义为 **volatile** **string** 以保持会话之间上传文档路径的值。

```
static volatile string UploadedDocumentPath;

public void OnPostUploadDocument()
{
    var projectRootPath = Path.Combine(_hostingEnvironment.ContentRootPath, "UploadedDocuments");
    var filePath = Path.Combine(projectRootPath, UploadedDocument.FileName);
    UploadedDocument.CopyTo(new FileStream(filePath, FileMode.Create));

    // Retain the path of uploaded document between sessions.
    UploadedDocumentPath = filePath;

    ShowDocumentContentInTextEditor();
}
```

请查看 [保存文档][8] 和 [从文件或标记创建可编辑文档][9] 文章以了解有关 GroupDocs.Editor 类的更多信息。

运行项目并测试以下用例：

  1. 通过单击 **Upload Document** 按钮将现有 Word 文档的内容上传到编辑器。
  2. 对内容进行所需的更改。
  3. 单击**下载文档**按钮以将更新的内容下载为 Word 文档。

## 将编辑器的内容下载为 PDF 文档 {#Download-Content-As-PDF}

我们需要在 **OnPostDownloadDocument()** 处理程序中进行一些修改，以返回 PDF 文档作为响应。我们使用 [PdfSaveOptions][10] 而不是 [WordProcessingSaveOptions][11] 并使用 **application/pdf** 作为 MIME 类型。

```
public FileResult OnPostDownloadDocument()
{
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Editor editor = new Editor(UploadedDocumentPath, delegate { return loadOptions; });

    string completeHTML = "<!DOCTYPE html><html><head><title></title></head><body>" + DocumentContent + "</body></html>";
    EditableDocument document = EditableDocument.FromMarkup(completeHTML, null);

    var projectRootPath = Path.Combine(_hostingEnvironment.ContentRootPath, "DownloadedDocuments");
    var outputPath = Path.Combine(projectRootPath, Path.GetFileNameWithoutExtension(UploadedDocumentPath) + ".pdf");

    PdfSaveOptions saveOptions = new PdfSaveOptions();
    editor.Save(document, outputPath, saveOptions);

    var bytes = System.IO.File.ReadAllBytes(outputPath);
    return new FileContentResult(bytes, new MediaTypeHeaderValue("application/pdf"))
    {
        FileDownloadName = Path.GetFileNameWithoutExtension(UploadedDocumentPath) + ".pdf"
    };
}
```

## 将编辑器的内容下载为纯文本文档 {#Download-Content-As-Plain-Text-Document}

为了返回纯文本文档 (.txt) 作为响应，我们使用 [TextSaveOptions][12] 类并使用 **text/plain** 作为 MIME 类型。

```
public FileResult OnPostDownloadDocument()
{
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Editor editor = new Editor(UploadedDocumentPath, delegate { return loadOptions; });

    string completeHTML = "<!DOCTYPE html><html><head><title></title></head><body>" + DocumentContent + "</body></html>";
    EditableDocument document = EditableDocument.FromMarkup(completeHTML, null);

    var projectRootPath = Path.Combine(_hostingEnvironment.ContentRootPath, "DownloadedDocuments");
    var outputPath = Path.Combine(projectRootPath, Path.GetFileNameWithoutExtension(UploadedDocumentPath) + ".txt");

    TextSaveOptions saveOptions = new TextSaveOptions();
    editor.Save(document, outputPath, saveOptions);

    var bytes = System.IO.File.ReadAllBytes(outputPath);
    return new FileContentResult(bytes, new MediaTypeHeaderValue("text/plain"))
    {
        FileDownloadName = Path.GetFileNameWithoutExtension(UploadedDocumentPath) + ".txt"
    };
}
```

## 与朋友分享编辑器的 URL {#Share-URL-With-Friends}

我们应该为用户提供一种方便的方式来复制编辑器的 URL 并与朋友分享。为此，请添加一个 **`<input> `** **Index.cshtml** 中**text** 类型的元素。

```
<div>
    <strong>
        <label for="shareURL">Edit with Friends: </label>
    </strong>
    <input type="text" name="shareURL" id="shareURL" size="50">
</div>
```

添加上面的**`<div> `** **之前的元素`<div id="userlist"> `** 标签。我们使用以下代码行将此文本输入字段的值设置为编辑器的 URL。在 **Index.cshtml** 中的 **init()** 函数中添加此代码。

```
document.getElementById("shareURL").value = window.location.origin + window.location.pathname + window.location.hash;
```

我们将对 CSS 进行微小的更改，以确保正确显示文本输入字段。将 **firepad** 和 **userlist** 的顶部位置设置为 **100px**，并为文本输入字段添加左边距。

```
#userlist {
    position: absolute;
    left: 0;
    top: 100px;
    bottom: 0;
    height: auto;
    width: 175px;
}

#firepad {
    position: absolute;
    left: 175px;
    top: 100px;
    bottom: 0;
    right: 0;
    height: auto;
}

#uploadForm {
    margin: 16px 2px;
}

#shareURL {
    margin-left: 123px;
}
```

运行项目，您应该会看到一个文本字段，可以让您复制编辑器的 URL。与您的朋友分享并与他们同时编辑文档。

该项目的完整源代码可在 [GitHub][13] 上获得。

## 也可以看看

  * <https://blog.conholdate.com/2020/06/22/build-your-own-google-docs-like-app/>

 [1]: https://blog.conholdate.com/2020/06/22/build-your-own-google-docs-like-app/
 [2]: #Download-Content-As-MS-Word
 [3]: #Download-Content-As-PDF
 [4]: #Download-Content-As-Plain-Text-Document
 [5]: #Share-URL-With-Friends
 [6]: https://firepad.io/docs/
 [7]: https://products.groupdocs.com/editor/net
 [8]: https://docs.groupdocs.com/display/editornet/Save+document
 [9]: https://docs.groupdocs.com/display/editornet/Create+EditableDocument+from+file+or+markup
 [10]: https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/pdfsaveoptions
 [11]: https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/wordprocessingsaveoptions
 [12]: https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/textsaveoptions
 [13]: https://github.com/sohail-aspose/GoogleDocsLite








