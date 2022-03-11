---
title: Créez votre propre Google Docs comme App
author: Muhammad Sohail
date: 2020-06-22T18:16:50+00:00
url: /fr/2020/06/22/créez-votre-propre-application-google-docs-like/
image_en vedette: /wp-content/uploads/sites/27/2020/06/Real-Time-Collaborative-Text-Editor-940x198.jpg
categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "Créer des documents Google"
  - "Google Docs"
  - "Éditeur collaboratif en temps réel"
  - "Texte riche"

---
Plusieurs clients nous ont contactés et nous ont demandé comment créer une application Web de type Google Docs à l'aide de nos API. [Google Docs][1] est un traitement de texte qui permet aux utilisateurs de créer et de modifier des fichiers en ligne tout en collaborant avec d'autres utilisateurs en temps réel.
Cet article de blog explique à quel point il est facile de créer une version allégée de Google Docs dotée des fonctionnalités suivantes:
  * Édition de texte enrichi (modifier la police du texte, sa taille, sa couleur, son style (gras, italique), l'alignement, etc.).
  * Édition collaborative en temps réel d'un même document. Plusieurs utilisateurs peuvent accéder au document en même temps et le modifier.
  * Téléchargez le contenu d'un document Word existant dans un éditeur.
  * Enregistrez le texte dans l'éditeur en tant que document MS Word, PDF, TXT ou HTML.

Notre produit final ressemblera à ceci:
{{< figure align=center src="images/Real-Time-Collaborative-Text-Editor-1-1024x505.jpg" alt="Google Docs comme App Interface">}} 

  * [Outils et technologies][2]
  * [Intégrer Firepad][3]
  * [Télécharger le contenu d'un document Word existant dans un éditeur][4]
  * [Intégrer GroupDocs.Editor][5]
  * [Traitement des données de formulaire][6]

## Outils et technologies - Créer Google Docs comme App {#Tools-and-Technologies}

Nous développerons l'application Web de type Google Docs dans ASP.NET Core et utiliserons les deux bibliothèques suivantes:

  * [Tapis de feu][7] is an open-source, collaborative text editor. It uses the [Firebase][8] Realtime Database as a backend so it requires no server-side code and can be added to any web app simply by including the JavaScript files.
  * [GroupDocs.Editor pour .NET][9] gives us an ability to edit most popular document formats using any [WYSIWYG][10] editor without any additional applications. We will load document via GroupDocs.Editor into Firepad, edit document in a way we want and save it back to original document format.

J'ai utilisé [Visual Studio pour Mac][11] comme [IDE][12]. Cependant, vous pouvez télécharger l'édition communautaire gratuite de Visual Studio, en fonction de votre plate-forme, à partir de [ici][13]. Commençons.
Créez un nouveau projet d'application Web ASP.NET Core et nommez le projet "GoogleDocsLite".
<div class="wp-block-image">  

{{< figure align=center src="images/ASP.NET-Core-New-Project-1024x318.jpg" alt="Créer une nouvelle application Web ASP.NET Core">}}</div>

Exécutez l'application pour vous assurer que tout est correctement configuré.

## Intégrer Firepad {#Integrate-Firepad}

Nous pouvons ajouter Firepad à notre application Web en incluant les fichiers JavaScript suivants dans le **_Layout.cshtml**.

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

<!-- liste d'utilisateurs -->
<script src="~/js/firepad-userlist.js"></script>
<link rel="stylesheet" href="~/css/firepad-userlist.css" />
```

Pour créer un Firepad, nous allons initialiser Firebase, CodeMirror puis Firepad. Ajoutez le script et le code HTML suivants dans **Index.cshtml**.

```
<script>
  function init() {
    // Initialise Firebase.
    // TODO: remplacer par la configuration de votre projet Firebase.
    var config = {
      apiAPI: '', 
      authDomain: "", 
      databaseURL: ""
    };
    firebase.initializeApp(config);

    // Récupère la référence de la base de données Firebase.
    var firepadRef = getExampleRef();

    // Créer CodeMirror (avec lineWrapping activé).
    var codeMirror = CodeMirror(document.getElementById('firepad'), { lineWrapping: true });

    // Créez un ID aléatoire à utiliser comme ID utilisateur (nous devons le donner à firepad et FirepadUserList).        
    var userId = Math.floor(Math.random() * 9999999999).toString();

    // Créer Firepad (avec des fonctionnalités de texte enrichi et notre userId souhaité).
    var firepad = Firepad.fromCodeMirror(firepadRef, codeMirror, { richTextToolbar: true, richTextShortcuts: true, userId: userId });

    // Créer FirepadUserList (avec notre userId souhaité).
    var firepadUserList = FirepadUserList.fromDiv(firepadRef.child('users'), document.getElementById('userlist'), userId);
  }

  // Aide pour obtenir le hachage à partir de la fin de l'URL ou en générer un aléatoire
  function getExampleRef() {
    var ref = firebase.database().ref();
    var hash = window.location.hash.replace(/#/g, '');
    if (hash) {
      ref = ref.child(hash);
    } else {
      ref = ref.push(); // génère un emplacement unique.
      window.location = window.location + '#' + ref.key; // ajoutez-le en tant que hachage à l'URL.
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

Veuillez remplacer le contenu de **config** par la configuration de votre propre projet Firebase.

Nous voulons que le script ci-dessus s'exécute une fois qu'une page Web a complètement chargé tout le contenu (fichiers de script, fichiers CSS, etc.). Appelez donc la fonction **init()** à partir de l'attribut d'événement **onLoad** de **<body>** élément dans **_Layout.cshtml**.

```
 <body onload="init()">
```

Ton `<body>` L'élément doit ressembler à ce qui suit. S'il contient des balises inutiles comme `<header>`, `<footer>`, veuillez les supprimer.

<div class="wp-block-image">  
{{< figure align=center src="images/Body-Element-1024x451.jpg" alt="Élément du corps">}}
</div>

Si vous exécutez le projet, vous remarquerez que **firepad** et **userlist** ne sont pas alignés correctement. Veuillez utiliser le code CSS suivant pour ajuster la taille/position du **firepad** et de la **userlist**. Vous pouvez ajouter le code suivant dans élément de **_Layout.cshtml**.

```
 <style>
   html {
     height: 100%;
   }

   body {
     margin: 0;
     height: 100%;
   }
   
   /* Nous faisons en sorte que la liste des utilisateurs fasse 175 pixels et que le firepad remplisse le reste de la page. */
   
   #userlist {
     position: absolute;
     left: 0;
     top:  50px;
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

Firepad a été configuré avec succès.

## Télécharger le contenu d'un document Word existant dans un éditeur {#Upload-Content-of-an-Existing-Word-Document-into-an-Editor}

Maintenant, nous voulons donner à nos utilisateurs un moyen de télécharger le contenu d'un document Word existant dans l'éditeur de texte. Sur le frontend, nous ajoutons un élément de type file qui permet à un utilisateur de sélectionner un document Word à partir de sa machine locale. Sur le backend, nous utilisons la bibliothèque [GroupDocs.Editor][9] pour récupérer le contenu d'un document Word sous forme de chaîne HTML. Enfin, nous utilisons la méthode setHtml() de Firepad pour afficher le contenu dans l'éditeur de texte.

Ajoutez l'élément suivant dans le fichier **Index.cshtml** avant la balise.

```
<form method="post" enctype="multipart/form-data" id="uploadForm">
  <input asp-for="UploadedDocument" />
  <input type="submit" value="Upload Document" class="btn btn-primary" asp-page-handler="UploadDocument" />
</form>
```

Dans le fichier **Index.cshtml.cs**, définissez une propriété correspondante.

```
[BindProperty]
public IFormFile UploadedDocument { get; set; }
```

Exécutez le projet et cliquez sur le bouton **Choisir un fichier**. Sélectionnez un document Word que vous souhaitez télécharger et cliquez sur le bouton **Télécharger le document**. Rien ne se passera car nous n'avons pas encore défini le gestionnaire dans **Index.cshtml.cs**. Avant de faire cela, ajoutons d'abord la bibliothèque GroupDocs.Editor dans notre projet.

## Intégrer GroupDocs.Editor {#Integrate-GroupDocs.Editor}

**GroupDocs.Editor** est disponible sous forme de package NuGet afin que nous puissions facilement l'ajouter à notre projet. Cliquez avec le bouton droit sur le projet et sélectionnez l'option **Gérer les packages NuGet**. La fenêtre **Gérer les packages NuGet** s'ouvre, sélectionnez l'onglet **Parcourir** et saisissez **GroupDocs.Editor** dans le champ de recherche. **GroupDocs.Editor** devrait apparaître comme premier résultat, sélectionnez-le puis cliquez sur le bouton **Ajouter un package**.

{{< figure align=center src="images/Manage-NuGet-Package-1024x645.jpg" alt="Ajouter GroupDocs.Editor via le gestionnaire de packages NuGet">}} 

Une fois le package ajouté avec succès, il apparaîtra dans le sous-dossier **NuGet** du dossier **Dependencies**.

## Traitement des données de formulaire {#Form-Data-Handling}

Nous écrivons maintenant un gestionnaire (méthode **OnPostUploadDocument()**) qui sera appelé lorsqu'un utilisateur cliquera sur le bouton **Télécharger le document**. L'objet **UploadedDocument** (de type **IFormFile**) contient le contenu du document téléchargé. Tout d'abord, nous enregistrons le document sur le serveur, puis utilisons la bibliothèque ** GroupDocs.Editor ** pour obtenir son contenu sous forme de chaîne HTML. Veuillez ajouter le code suivant dans le fichier **Index.cshtml.cs**.

```
private readonly IWebHostEnvironment _hostingEnvironment;

public string DocumentContent { get; set; }

public IndexModel(IWebHostEnvironment hostingEnvironment)
{
  _hostingEnvironment = hostingEnvironment;
}

public void OnPostUploadDocument() {
  var projectRootPath = Path.Combine(_hostingEnvironment.ContentRootPath, "UploadedDocuments");
  var filePath = Path.Combine(projectRootPath, UploadedDocument.FileName);UploadedDocument.CopyTo(new FileStream(filePath, FileMode.Create));ShowDocumentContentInTextEditor(filePath);
}

private void ShowDocumentContentInTextEditor(string filePath)
{
  WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
  Editor editor = new Editor(filePath, delegate { return loadOptions; }); //passage des options de chemin et de chargement (via un délégué) au constructeur
  EditableDocument document = editor.Edit(new WordProcessingEditOptions()); // ouverture du document pour modification avec des options d'édition spécifiques au format

  DocumentContent = document.GetContent();
}
```

Firepad fournit deux événements pour l'écoute. L'un d'eux est '**ready**' qui se déclenche une fois que Firepad a récupéré le contenu initial de l'éditeur. Nous attachons un rappel à ce type d'événement et dans le rappel, nous transmettons la chaîne **DocumentContent** comme argument à la méthode **setHtml()** de l'objet **firepad**. Veuillez ajouter le code suivant dans la fonction **init()** dans **Index.cshtml**.

```
firepad.on('ready', function () {
  if (firepad.isHistoryEmpty()) {
    var documentContent = '@Model.DocumentContent';
    if (documentContent.length != 0) {
      firepad.setHtml(htmlDecode(documentContent));
    } else {
      firepad.setText("Bienvenue sur votre propre pad privé ! Partagez l'URL ci-dessus et collaborez avec vos amis.");
    }
  }
});
```

Vous avez peut-être remarqué que nous avons d'abord passé la chaîne **documentContent** à la méthode **htmlDecode()** avant de passer à la méthode **setHtml()**. Il s'agit de remplacer les entités de caractères telles que **&lt**, **&gt** par des signes (**`<`** et **`>`**). La méthode **htmlDecode()** se présente comme suit.

```
function htmlDecode(input) {
  var e = document.createElement('div');
  e.innerHTML = input; 
  return e.childNodes[0].nodeValue;
}
```

Exécutez le projet, vous devriez maintenant pouvoir télécharger le contenu d'un document Word dans un éditeur.

Dans la [partie II][14] de cet article, j'ai expliqué comment nous pouvons étendre notre application pour inclure les fonctionnalités suivantes:
  * Téléchargez le contenu de l'éditeur sous forme de document MS Word, PDF, TXT ou HTML.
  * Partagez l'URL avec des amis afin qu'ils puissent modifier le document en même temps.

Veuillez [vérifier][14].
Le code source complet du projet est disponible sur [GitHub][15].
## Voir également

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












