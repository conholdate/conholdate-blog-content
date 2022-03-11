---
title: "构建您自己的 Google Docs like App"
author: Muhammad Sohail
date: 2020-06-22T18:16:50+00:00
url: /zh/2020/06/22/build-your-own-google-docs-like-app/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "创建 Google 文档"
  - "谷歌文档"
  - "实时协同编辑"
  - "富文本"

---
一些客户找到了我们，询问他们如何使用我们的 API 创建类似 Google Docs 的网络应用程序。 [Google Docs][1] 是一个文字处理器，允许用户在线创建和编辑文件，同时与其他用户实时协作。

这篇博文解释了创建具有以下功能的精简版 Google 文档是多么容易：

  * 富文本编辑（更改文本字体、大小、颜色、样式（粗体、斜体）、对齐方式等）。
  * 同一文档的实时协作编辑。多个用户可以同时访问文档并对其进行修改。
  * 将现有 Word 文档的内容上传到编辑器中。
  * 将编辑器中的文本保存为 MS Word、PDF、TXT 或 HTML 文档。

我们的最终产品如下所示：

{{< figure align=center src="images/Real-Time-Collaborative-Text-Editor-1-1024x505.jpg" alt="类似应用界面的 Google Docs">}}
 

  * [工具和技术][2]
  * [集成 Firepad][3]
  * [将现有 Word 文档的内容上传到编辑器][4]
  * [集成 GroupDocs.Editor][5]
  * [表单数据处理][6]

## 工具和技术 – 创建 Google Docs like App {#Tools-and-Technologies}

我们将在 ASP.NET Core 中开发 Google Docs like web 应用程序，并使用以下两个库：

  * [火垫][7] is an open-source, collaborative text editor. It uses the [Firebase][8] Realtime Database as a backend so it requires no server-side code and can be added to any web app simply by including the JavaScript files.
  * [GroupDocs.Editor for .NET][9] gives us an ability to edit most popular document formats using any [WYSIWYG][10] editor without any additional applications. We will load document via GroupDocs.Editor into Firepad, edit document in a way we want and save it back to original document format.

我使用 [Visual Studio for Mac][11] 作为 [IDE][12]。但是，您可以根据您的平台从 [此处][13] 下载免费的 Visual Studio 社区版。开始吧。

创建一个新的 ASP.NET Core Web 应用程序项目并将项目命名为“GoogleDocsLite”。

<div class="wp-block-image">
  

{{< figure align=center src="images/ASP.NET-Core-New-Project-1024x318.jpg" alt="创建一个新的 ASP.NET Core Web 应用">}}

</div>

运行应用程序以确保一切设置正确。

## 集成 Firepad {#Integrate-Firepad}

我们可以通过在 ** 中包含以下 JavaScript 文件来将 Firepad 添加到我们的 Web 应用程序中<head>** **_Layout.cshtml** 的部分。

```
<!-- Firebase -->
<script src="https://www.gstatic.com/firebasejs/7.13.2/firebase-app.js"></script>
<script src="https://www.gstatic.com/firebasejs/7.13.2/firebase-auth.js"></script>
<script src="https://www.gstatic.com/firebasejs/7.13.2/firebase-database.js"></script>

<!-- CodeMirror -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.17.0/codemirror.js"></script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.17.0/codemirror.css" />

<!-- Firepad -->
<link rel="stylesheet" href="https://firepad.io/releases/v1.5.9/firepad.css" />
<script src="https://firepad.io/releases/v1.5.9/firepad.min.js"></script>

<!-- userlist -->
<script src="~/js/firepad-userlist.js"></script>
<link rel="stylesheet" href="~/css/firepad-userlist.css" />
```

要创建 Firepad，我们将初始化 Firebase、CodeMirror 和 Firepad。在 **Index.cshtml** 中添加以下脚本和 HTML 代码。

```
<script>
    function init() {
        // Initialize Firebase.
        // TODO: replace with your Firebase project configuration.
        var config = {
            apiKey: '',
            authDomain: "",
            databaseURL: ""
        };
        firebase.initializeApp(config);
        
        // Get Firebase Database reference.
        var firepadRef = getExampleRef();
        
        // Create CodeMirror (with lineWrapping on).
        var codeMirror = CodeMirror(document.getElementById('firepad'), { lineWrapping: true });

        // Create a random ID to use as our user ID (we must give this to firepad and FirepadUserList).
        var userId = Math.floor(Math.random() * 9999999999).toString();

        // Create Firepad (with rich text features and our desired userId).
        var firepad = Firepad.fromCodeMirror(firepadRef, codeMirror,
                    { richTextToolbar: true, richTextShortcuts: true, userId: userId });

        // Create FirepadUserList (with our desired userId).
        var firepadUserList = FirepadUserList.fromDiv(firepadRef.child('users'),
        document.getElementById('userlist'), userId);
    }
    
    // Helper to get hash from end of URL or generate a random one.
    function getExampleRef() {
        var ref = firebase.database().ref();
        var hash = window.location.hash.replace(/#/g, '');
        if (hash) {
            ref = ref.child(hash);
        } else {
            ref = ref.push(); // generate unique location.
            window.location = window.location + '#' + ref.key; // add it as a hash to the URL.
        }
        if (typeof console !== 'undefined') {
            console.log('Firebase data: ', ref.toString());
        }
        return ref;
    }
</script>

<div id="userlist"></div>
<div id="firepad"></div>
```

请将 **config** 的内容替换为您自己的 Firebase 项目的配置。

我们希望在网页完全加载所有内容（脚本文件、CSS 文件等）后执行上述脚本。因此，从 ** 的 **onLoad** 事件属性调用 **init()** 函数<body>** **_Layout.cshtml** 中的元素。

```
<body onload="init()">
```

你的`<body> ` 元素应如下所示。如果它包含不必要的标签，如`<header> `, `<footer> `，请删除它们。

<div class="wp-block-image">

{{< figure align=center src="images/Body-Element-1024x451.jpg" alt="身体元素">}}

</div>

如果您运行该项目，您会注意到 **firepad** 和 **userlist** 没有正确对齐。请使用以下 CSS 代码调整 **firepad** 和 **userlist** 的大小/位置。您可以在**中添加以下代码<head>** **_Layout.cshtml** 的元素。

```
<style>
    html {
        height: 100%;
    }

    body {
        margin: 0;
        height: 100%;
    }

    /* We make the user list 175px and firepad fill the rest of the page. */
    #userlist {
        position: absolute;
        left: 0;
        top: 50px;
        bottom: 0;
        height: auto;
        width: 175px;
    }

    #firepad {
        position: absolute;
        left: 175px;
        top: 50px;
        bottom: 0;
        right: 0;
        height: auto;
    }
</style>
```

Firepad 已成功设置。

## 将现有 Word 文档的内容上传到编辑器 {#Upload-Content-of-an-Existing-Word-Document-into-an-Editor}

现在我们想为我们的用户提供一种在文本编辑器中上传现有 Word 文档内容的方法。在前端，我们添加一个**<input> ** **file** 类型的元素，允许用户从本地计算机中选择 Word 文档。在后端，我们使用 [GroupDocs.Editor][9] 库来检索 Word 文档的内容作为 HTML 字符串。最后，我们使用 Firepad 的 **setHtml()** 方法在文本编辑器中显示内容。

添加以下**<form> ** **Index.cshtml** 文件中的元素**<div id=”userlist”> ** 标签。

```
<form method="post" enctype="multipart/form-data" id="uploadForm">
    <input asp-for="UploadedDocument" />
    <input type="submit" value="Upload Document" class="btn btn-primary" asp-page-handler="UploadDocument" />
</form>
```

在 **Index.cshtml.cs** 文件中，定义相应的属性。

```
[BindProperty]
public IFormFile UploadedDocument { get;  set; }
```

运行项目并单击 **Choose file** 按钮。选择您要上传的 Word 文档，然后单击 **Upload Document** 按钮。什么都不会发生，因为我们还没有在 **Index.cshtml.cs** 中定义处理程序。在我们这样做之前，让我们首先在我们的项目中添加 GroupDocs.Editor 库。

## 集成 GroupDocs.Editor {#Integrate-GroupDocs.Editor}

**GroupDocs.Editor** 以 NuGet 包的形式提供，因此我们可以轻松地将其添加到我们的项目中。右键单击项目并选择 **Manage NuGet Packages** 选项。 **Manage NuGet Packages** 窗口将打开，选择 **Browse** 选项卡，然后在搜索字段中输入 **GroupDocs.Editor**。 **GroupDocs.Editor** 应该作为第一个结果出现，选择它，然后单击 **Add Package** 按钮。

{{< figure align=center src="images/Manage-NuGet-Package-1024x645.jpg" alt="通过 NuGet 包管理器添加 GroupDocs.Editor">}}

包添加成功后，会出现在**Dependencies**文件夹下的**NuGet**子文件夹下。

## 表单数据处理 {#Form-Data-Handling}

现在我们编写一个处理程序（**OnPostUploadDocument()** 方法），当用户单击**Upload Document** 按钮时将调用它。 **UploadedDocument** 对象（类型为 **IFormFile**）包含上载文档的内容。首先，我们将文档保存在服务器上，然后使用 **GroupDocs.Editor** 库将其内容获取为 HTML 字符串。请在 **Index.cshtml.cs** 文件中添加以下代码。

```
private readonly IWebHostEnvironment _hostingEnvironment;

public string DocumentContent { get; set; }

public IndexModel(IWebHostEnvironment hostingEnvironment)
{
    _hostingEnvironment = hostingEnvironment;
}

public void OnPostUploadDocument()
{
    var projectRootPath = Path.Combine(_hostingEnvironment.ContentRootPath, "UploadedDocuments");
    var filePath = Path.Combine(projectRootPath, UploadedDocument.FileName);
    UploadedDocument.CopyTo(new FileStream(filePath, FileMode.Create));
    ShowDocumentContentInTextEditor(filePath);
}

private void ShowDocumentContentInTextEditor(string filePath)
{
    WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
    Editor editor = new Editor(filePath, delegate { return loadOptions; }); //passing path and load options (via delegate) to the constructor
    EditableDocument document = editor.Edit(new WordProcessingEditOptions()); //opening document for editing with format-specific edit options

    DocumentContent = document.GetContent();
}
```

Firepad 提供了两个监听事件。其中之一是“**ready**”，一旦 Firepad 检索到初始编辑器内容就会触发。我们将回调附加到此事件类型，并在回调中将 **DocumentContent** 字符串作为参数传递给 **firepad** 对象的 **setHtml()** 方法。请在 **Index.cshtml** 的 **init()** 函数中添加以下代码。

```
firepad.on('ready', function () {
    if (firepad.isHistoryEmpty()) {
        var documentContent = '@Model.DocumentContent';
        if (documentContent.length != 0) {   
            firepad.setHtml(htmlDecode(documentContent));
        } else {
            firepad.setText("Welcome to your own private pad! Share the URL above and collaborate with your friends.");
        }
    }
});
```

您可能已经注意到，我们首先将 **documentContent** 字符串传递给 **htmlDecode()** 方法，然后再传递给 **setHtml()** 方法。就是用符号（**`<`** and **`>`**）来代替**<**、**>**等字符实体。 **htmlDecode()** 方法如下所示。

```
function htmlDecode(input) {
    var e = document.createElement('div');
    e.innerHTML = input;
    return e.childNodes[0].nodeValue;
}
```

运行项目，现在您应该能够将 Word 文档的内容上传到编辑器中。

在这篇文章的 [part II][14] 中，我解释了如何扩展我们的应用程序以包含以下功能：

  * 将编辑器的内容下载为 MS Word、PDF、TXT 或 HTML 文档。
  * 与朋友共享 URL，以便他们可以同时编辑文档。

请[检查一下][14]。

该项目的完整源代码可在 [GitHub][15] 上获得。

## 也可以看看

  * <https://blog.conholdate.com/2020/06/29/build-your-own-google-docs-like-app-part-two/>

 [1]: https://www.google.com/docs/about/
 [2]: #Tools-and-Technologies
 [3]: #Integrate-Firepad
 [4]: #Upload-Content-of-an-Existing-Word-Document-into-an-Editor
 [5]: #Integrate-GroupDocs.Editor
 [6]: #Form-Data-Handling
 [7]: https://firepad.io/
 [8]: https://firebase.google.com/
 [9]: https://products.groupdocs.com/editor
 [10]: https://en.wikipedia.org/wiki/WYSIWYG
 [11]: https://visualstudio.microsoft.com/vs/mac/
 [12]: https://en.wikipedia.org/wiki/Integrated_development_environment
 [13]: https://visualstudio.microsoft.com/
 [14]: https://blog.conholdate.com/2020/06/29/build-your-own-google-docs-like-app-part-two/
 [15]: https://github.com/sohail-aspose/GoogleDocsLite









