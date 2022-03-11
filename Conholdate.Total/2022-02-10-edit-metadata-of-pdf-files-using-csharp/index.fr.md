---
title: "Modifier les métadonnées des fichiers PDF à l'aide de C#"
author: Muzammil Khan
date: 2022-02-10T15:15:07+00:00
summary: "Vous pouvez ajouter/modifier des informations de document et des métadonnées XMP dans un document PDF par programmation. Dans cet article, vous apprendrez **à modifier les métadonnées des fichiers PDF à l'aide de C#** ."
url: /fr/2022/02/10/edit-metadata-of-pdf-files-using-csharp/
categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "Ajouter des métadonnées XMP personnalisées C#"
  - "Obtenir des informations sur le document en C#"
  - "Obtenir des métadonnées XMP à l'aide de C#"
  - "Lire les métadonnées XMP personnalisées"
  - "Lire les métadonnées XMP personnalisées C#"
  - "Définir les informations sur le document en C#"
  - "Définir les métadonnées XMP à l'aide de C#"

---


{{< figure align=center src="images/edit-metadata-of-pdf-files-using-csharp.jpg" alt="Modifier les métadonnées des fichiers PDF à l'aide de C#">}}
 

Les métadonnées sont une carte de visite d'un document numérique particulier qui se compose d'un ensemble de propriétés. Ces propriétés contiennent des informations de base sur le document telles que le titre, l'auteur, le sujet, les mots-clés, etc. Extensible Metadata Platform (XMP) est un format basé sur XML qui permet d'enregistrer les métadonnées du document dans une paire clé/valeur. Nous pouvons ajouter/modifier des informations de document et des métadonnées XMP dans un document PDF par programme. Dans cet article, nous allons apprendre **comment modifier les métadonnées des fichiers PDF à l'aide de C#**.

Les sujets suivants seront traités dans cet article:
  * [API C# pour modifier les métadonnées des fichiers PDF][2]
  * [Modifier les métadonnées d'un fichier PDF][3]
  * [Obtenir les métadonnées d'un fichier PDF][4]
  * [Obtenir des métadonnées XMP à partir d'un fichier PDF][5]
  * [Définir les métadonnées XMP dans un fichier PDF][6]
  * [Personnaliser l'espace de noms de métadonnées XMP dans un fichier PDF][7]

## API C# pour modifier les métadonnées des fichiers PDF {#CSharp-API-to-Edit-Metadata-of-PDF-Files}

Pour modifier les informations de métadonnées dans un document [PDF][8], nous utiliserons [Aspose.PDF pour .NET API][9]. Il nous permet de générer, modifier, convertir, restituer, sécuriser et imprimer [documents pris en charge][10] sans utiliser Adobe Acrobat. Veuillez soit [télécharger][11] la DLL de l'API ou l'installer à l'aide de [NuGet][12].

```
PM> Install-Package Aspose.Pdf
```

## Modifier les métadonnées d'un fichier PDF en C # {#Edit-Metadata-of-a-PDF-File-in-CSharp}

Nous pouvons modifier les informations d'un document PDF à l'aide de la classe **_[DocumentInfo][13]_** qui représente les méta-informations d'un document PDF. Nous pouvons définir diverses **[propriétés][14]** prédéfinies en suivant les étapes ci-dessous:
  1. Tout d'abord, chargez un document PDF à l'aide de la classe [**_Document_**][15].
  2. Ensuite, créez une instance de la classe **_[DocumentInfo][13]_** avec l'objet de classe _Document_ comme argument.
  3. Ensuite, définissez diverses propriétés telles que _Author_, _CreationDate_, _Keywords_, _Subject_, _Title_, etc.
  4. Enfin, enregistrez le fichier PDF à l'aide de la méthode **_[Document.Save()][16]_** avec le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment modifier les métadonnées d'un fichier PDF à l'aide de C#**.

```
// Cet exemple de code montre comment définir les informations de base d'un document PDF.
// Ouvrir le document
Document pdfDocument = new Document("C:\\Files\\PDF\\sample.pdf");

// Initialiser l'objet DocumentInfo
DocumentInfo docInfo = new DocumentInfo(pdfDocument);

// Spécifier les propriétés des informations sur le document
docInfo.Author = "Aspose";
docInfo.CreationDate = DateTime.Now;
docInfo.Keywords = "Aspose.Pdf, DOM, API";
docInfo.ModDate = DateTime.Now;
docInfo.Subject = "PDF Information";
docInfo.Title = "Setting PDF Document Information";

// Enregistrer le document
pdfDocument.Save("C:\\Files\\PDF\\sample_metadata.pdf");
```

{{< figure align=center src="images/Edit-Metadata-of-a-PDF-File-in-CSharp-1024x940.jpg" alt="Modifier les métadonnées d'un fichier PDF en C#." caption="Modifier les métadonnées d'un fichier PDF en C #.">}}
 

## Obtenir les métadonnées d'un fichier PDF à l'aide de C # {#Get-Metadata-of-a-PDF-File-using-CSharp}

Nous pouvons lire les informations de base d'un document PDF **** en suivant les étapes ci-dessous:
  1. Tout d'abord, chargez un document PDF à l'aide de la classe [**_Document_**][15].
  2. Ensuite, créez une instance de la classe **_[DocumentInfo][13]_** avec l'objet de classe _Document_ comme argument.
  3. Enfin, affichez les informations du document en lisant les valeurs des propriétés des métadonnées.

L'exemple de code suivant montre **comment obtenir les métadonnées d'un fichier PDF à l'aide de C#**.

```
// Cet exemple de code montre comment obtenir les informations de base d'un document PDF.
// Ouvrir le document
Document pdfDocument = new Document("C:\\Files\\PDF\\sample_metadata.pdf");

// Obtenir des informations sur les documents
DocumentInfo docInfo = pdfDocument.Info;

// Afficher les informations sur le document
Console.WriteLine("Author: {0}", docInfo.Author);
Console.WriteLine("Creation Date: {0}", docInfo.CreationDate);
Console.WriteLine("Keywords: {0}", docInfo.Keywords);
Console.WriteLine("Modify Date: {0}", docInfo.ModDate);
Console.WriteLine("Subject: {0}", docInfo.Subject);
Console.WriteLine("Title: {0}", docInfo.Title);
```

```
Author: Aspose
Creation Date: 2/9/2022 9:47:00 AM
Keywords: Aspose.Pdf, DOM, API
Modify Date: 2/9/2022 9:47:00 AM
Subject: PDF Information
Title: Setting PDF Document Information
```

## Obtenir les métadonnées XMP d'un fichier PDF à l'aide de C # {#Get-XMP-Metadata-of-a-PDF-File-using-CSharp}

Nous pouvons lire les métadonnées XMP d'un document PDF **** en suivant les étapes ci-dessous:
  1. Tout d'abord, chargez un document PDF à l'aide de la classe [**_Document_**][15].
  2. Enfin, lisez la propriété [**_Metadata_**][18] et extrayez les informations.

L'exemple de code suivant montre **comment obtenir les métadonnées XMP d'un fichier PDF à l'aide de C#**.

```
// Cet exemple de code montre comment obtenir les métadonnées XMP d'un document PDF.
// Ouvrir le document
Document pdfDocument = new Document("C:\\Files\\PDF\\sample_xmp.pdf");

// Afficher les informations XMP
Console.WriteLine("xmp:CreateDate: " + pdfDocument.Metadata["xmp:CreateDate"]);
Console.WriteLine("xmp:Nickname: " + pdfDocument.Metadata["xmp:Nickname"]);
Console.WriteLine("xmp:CustomProperty: " + pdfDocument.Metadata["xmp:CustomProperty"]);
```

```
xmp:CreateDate: 2022-02-09T08:57:00.7+05:00
xmp:Nickname: Nickname
xmp:CustomProperty: Custom Value
```

## Définir les métadonnées XMP dans un fichier PDF à l'aide de C# {#Set-XMP-Metadata-in-a-PDF-File-using-CSharp}

Nous pouvons définir les métadonnées XMP dans un fichier PDF à l'aide de la propriété **_[Metadata][18]_** de la classe **_[Document][19]_** en suivant les étapes ci-dessous:
  1. Tout d'abord, chargez un document PDF à l'aide de la classe [**_Document_**][15].
  2. Ensuite, définissez les valeurs des métadonnées à l'aide de la propriété [**_Metadata_**][18].
  3. Enfin, enregistrez le fichier PDF à l'aide de la méthode **_[Document.Save()][16]_** avec le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment définir les métadonnées XMP d'un fichier PDF à l'aide de C#**.

```
// Cet exemple de code montre comment définir les métadonnées XMP d'un document PDF.
// Ouvrir le document
Document pdfDocument = new Document("C:\\Files\\PDF\\sample.pdf");

// Définir les propriétés
pdfDocument.Metadata["xmp:CreateDate"] = DateTime.Now;
pdfDocument.Metadata["xmp:Nickname"] = "Nickname";
pdfDocument.Metadata["xmp:CustomProperty"] = "Custom Value";

// Enregistrer le document
pdfDocument.Save("C:\\Files\\PDF\\sample_xmp.pdf");
```

## Personnaliser l'espace de noms de métadonnées XMP dans un fichier PDF {#Customize-XMP-Metadata-Namespace-in-a-PDF-File}

La spécification Adobe XMP définit les quatre (4) espaces de noms principaux suivants que nous utilisons normalement:
  1. [Dublin Core][20] avec l'URI d'espace de noms comme "[http://purl.org/dc/elements/1.1/][21]" et son préfixe d'espace de noms préféré est 'dc'.
  2. Le [XMP][22] avec l'URI d'espace de noms comme http://ns.adobe.com/xap/1.0/ et son préfixe d'espace de noms préféré est 'xmp'.
  3. [Gestion des droits XMP][24] avec l'URI de l'espace de noms http://ns.adobe.com/xap/1.0/rights/ » et son préfixe d'espace de noms préféré est « xmpRights ».
  4. [XMP Media Management][26] avec l'URI de l'espace de noms « http://ns.adobe.com/xap/1.0/mm/ » et son préfixe d'espace de noms préféré est « xmpMM ».

Nous pouvons également définir l'URI de l'espace de noms personnalisé au lieu des spécifications XMP définies dans un fichier PDF. À cette fin, l'API fournit la méthode **_[RegisterNamespaceUri][28]_** dans la classe **_[Metadata][29]_**. Nous pouvons créer un nouvel espace de noms de métadonnées avec un préfixe en suivant les étapes ci-dessous:
  1. Tout d'abord, chargez un document PDF à l'aide de la classe [**_Document_**][15].
  2. Ensuite, appelez la méthode **_RegisterNamespaceUri_** avec un préfixe et un URI d'espace de noms comme arguments.
  3. Définissez ensuite les valeurs des métadonnées à l'aide de la propriété [**_Metadata_**][18].
  4. Enfin, enregistrez le fichier PDF à l'aide de la méthode **_[Document.Save()][16]_** avec le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment définir un espace de noms de métadonnées personnalisé dans un fichier PDF à l'aide de C#**.

```
// Cet exemple de code montre comment définir l'URI namepsace personnalisé dans un document PDF.
// Ouvrir le document
Document pdfDocument = new Document("C:\\Files\\PDF\\sample.pdf");

// Définir les propriétés
pdfDocument.Metadata.RegisterNamespaceUri("myown", "http:// myown.xyz.com/xap/1.0/");
pdfDocument.Metadata["myown:ModifyDate"] = DateTime.Now;
pdfDocument.Metadata["myown:CreateDate"] = DateTime.Now;
pdfDocument.Metadata["myown:DeveloperName"] = "Developer Name";
pdfDocument.Metadata["myown:MyProperty"] = "My Custom Value";


// Enregistrer le document
pdfDocument.Save("C:\\Files\\PDF\\sample_myown.pdf");
```

Nous pouvons lire les propriétés de métadonnées XMP personnalisées en suivant les étapes mentionnées précédemment.

```
myown:ModifyDate: 2022-02-09T10:38:26.8+05:00
myown:CreateDate: 2022-02-09T10:38:26.8+05:00
myown:DeveloperName: Developer Name
myown:MyProperty: My Custom Value
```

## Obtenez une licence API gratuite {#Get-a-Free-License}

Vous pouvez essayer l'API sans limitation d'évaluation en demandant [une licence temporaire gratuite][30].

## Conclusion

Dans cet article, nous avons appris à:
  * ajouter/modifier les informations de base d'un document PDF à l'aide de C# ;
  * définir/obtenir les métadonnées XMP dans un fichier PDF à l'aide de C# ;
  * définir l'URI de l'espace de noms de métadonnées personnalisées avec un préfixe.

En outre, vous pouvez en savoir plus sur Aspose.PDF pour l'API .NET en utilisant la [documentation][31]. En cas d'ambiguïté, n'hésitez pas à nous contacter sur le [forum][32].

## Voir également

  * [Ajouter des en-têtes et des pieds de page dans un PDF à l'aide de C #][33]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/edit-metadata-of-pdf-files-using-csharp.jpg
 [2]: #CSharp-API-to-Edit-Metadata-of-PDF-Files
 [3]: #Edit-Metadata-of-a-PDF-File-in-CSharp
 [4]: #Get-Metadata-of-a-PDF-File-using-CSharp
 [5]: #Get-XMP-Metadata-of-a-PDF-File-using-CSharp
 [6]: #Set-XMP-Metadata-in-a-PDF-File-using-CSharp
 [7]: #Customize-XMP-Metadata-Namespace-in-a-PDF-File
 [8]: https://docs.fileformat.com/pdf/
 [9]: https://products.aspose.com/pdf/net/
 [10]: https://docs.aspose.com/pdf/net/supported-file-formats/
 [11]: https://downloads.aspose.com/pdf/net
 [12]: https://www.nuget.org/packages/aspose.pdf
 [13]: https://apireference.aspose.com/pdf/net/aspose.pdf/documentinfo
 [14]: https://apireference.aspose.com/pdf/net/aspose.pdf/documentinfo/properties/index
 [15]: https://apireference.aspose.com/pdf/net/aspose.pdf/document
 [16]: https://apireference.aspose.com/pdf/net/aspose.pdf.document/save/methods/4
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Edit-Metadata-of-a-PDF-File-in-CSharp.jpg
 [18]: https://apireference.aspose.com/pdf/net/aspose.pdf/document/properties/metadata
 [19]: https://apireference.aspose.com/pdf/net/aspose.pdf/document/
 [20]: https://wwwimages2.adobe.com/content/dam/acom/en/devnet/xmp/pdfs/XMP%20SDK%20Release%20cc-2016-08/XMPSpecificationPart1.pdf#G5.785800
 [21]: http://purl.org/dc/elements/1.1/%22
 [22]: https://wwwimages2.adobe.com/content/dam/acom/en/devnet/xmp/pdfs/XMP%20SDK%20Release%20cc-2016-08/XMPSpecificationPart1.pdf#G5.810413
 [23]: http://ns.adobe.com/xap/1.0/%22
 [24]: https://wwwimages2.adobe.com/content/dam/acom/en/devnet/xmp/pdfs/XMP%20SDK%20Release%20cc-2016-08/XMPSpecificationPart1.pdf#G5.802526
 [25]: http://ns.adobe.com/xap/1.0/rights/%22
 [26]: https://wwwimages2.adobe.com/content/dam/acom/en/devnet/xmp/pdfs/XMP%20SDK%20Release%20cc-2016-08/XMPSpecificationPart1.pdf#G5.785832
 [27]: http://ns.adobe.com/xap/1.0/mm/%22
 [28]: https://apireference.aspose.com/pdf/net/aspose.pdf/metadata/methods/registernamespaceuri
 [29]: https://apireference.aspose.com/pdf/net/aspose.pdf/metadata
 [30]: https://purchase.conholdate.com/temporary-license
 [31]: https://docs.aspose.com/pdf/net
 [32]: https://forum.aspose.com/c/pdf/10
 [33]: https://blog.conholdate.com/2021/12/15/add-headers-and-footers-in-pdf-using-csharp/