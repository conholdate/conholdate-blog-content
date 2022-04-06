---
title: "Modifier les propriétés et les métadonnées PDF à l'aide de Java"
author: "Muzammil Khan"
date: 2022-04-05T15:15:07+00:00
summary: "Vous pouvez ajouter/modifier et lire les informations sur le document et les métadonnées XMP d'un document PDF par programmation. Dans cet article, vous apprendrez **comment modifier les propriétés et les métadonnées d'un PDF à l'aide de Java**."
url: /fr/2022/04/05/edit-pdf-properties-and-metadata-using-java/
categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "Ajouter des métadonnées XMP personnalisées Java"
  - "Obtenir des informations sur les documents en Java"
  - "Obtenir des métadonnées XMP à l'aide de Java"
  - "Lire les métadonnées XMP personnalisées"
  - "Lire les métadonnées XMP personnalisées Java"
  - "Définir les informations du document en Java"
  - "Définir les métadonnées XMP à l'aide de Java"
  - "Propriétés PDF en Java"
---

{{< figure align=center src="images/edit-pdf-properties-and-metadata-using-java.jpg" alt="Modifier les métadonnées des fichiers PDF à l'aide de Java">}}

Les métadonnées d'un document contiennent des informations de base sur le document sous la forme de propriétés telles que le titre, l'auteur, le sujet, les mots-clés, etc. La plate-forme de métadonnées extensibles (XMP) est une norme basée sur XML pour stocker les métadonnées d'un document sous forme de clé/valeur. paire. Nous pouvons ajouter, modifier ou lire les informations sur le document et les métadonnées XMP d'un document PDF par programmation. Dans cet article, nous allons apprendre **comment modifier les propriétés et les métadonnées d'un PDF à l'aide de Java**.

Les sujets suivants seront traités dans cet article :

  * [API Java pour modifier les propriétés et les métadonnées PDF][1]
  * [Modifier les propriétés PDF à l'aide de Java][2]
  * [Lire les propriétés PDF à l'aide de Java][3]
  * [Obtenir des métadonnées XMP à partir d'un fichier PDF][4]
  * [Définir les métadonnées XMP dans un fichier PDF][5]
  * [Personnaliser l'espace de noms de métadonnées XMP dans un fichier PDF][6]

## API Java pour modifier les propriétés et les métadonnées PDF {#Java-API-to-Edit-PDF-Properties-and-Metadata}

Pour modifier les propriétés [PDF][7] et les informations de métadonnées, nous utiliserons [Aspose.PDF for Java API][8]. Il nous permet de générer, modifier, convertir, restituer, sécuriser et imprimer [documents pris en charge][9] sans utiliser Adobe Acrobat. Veuillez soit [télécharger][10] le JAR de l'API ou ajouter la configuration _pom.xml_ suivante dans une application Java basée sur Maven.

```
<repository>
    <id>AsposeJavaAPI</id>
    <name>Aspose Java API</name>
    <url>https://repository.aspose.com/repo/</url>
</repository>
```
```
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-pdf</artifactId>
    <version>22.3</version>
</dependency>
```

## Modifier les propriétés PDF à l'aide de Java {#Edit-PDF-Properties-using-Java}

Nous pouvons modifier les informations d'un document PDF à l'aide de la classe **_[PdfFileInfo][11]_** qui représente les méta-informations d'un document PDF. Nous pouvons définir diverses propriétés prédéfinies en suivant les étapes ci-dessous :

  1. Tout d'abord, chargez un document PDF en utilisant la classe _**[PdfFileInfo][11]**_.
  2. Définissez diverses propriétés telles que _Author_, _Creator_, _Keywords_, _Subject_, _Title_, etc.
  4. Enfin, enregistrez le fichier PDF à l'aide de la méthode **_[saveNewInfo()][12]_** avec le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment modifier les méta-propriétés d'un fichier PDF à l'aide de Java**.

```
// Cet exemple de code montre comment définir les informations de base d'un document PDF.
// Document open source
PdfFileInfo fileInfo = new PdfFileInfo("D:\\Files\\PDF\\sample.pdf");

// Définir les informations PDF
fileInfo.setAuthor("Aspose");
fileInfo.setTitle("Editing Metadata");
fileInfo.setKeywords("Aspose.Pdf, DOM, API");
fileInfo.setSubject("PDF Information");
fileInfo.setCreator("Aspose");

// Enregistrer le fichier mis à jour
fileInfo.saveNewInfo("D:\\Files\\PDF\\Updated_Info_output.pdf");
```

{{< figure align=center src="images/Edit-PDF-Properties-using-Java.jpg" alt="Modifier les propriétés méta d'un fichier PDF en Java." caption="Modifier les propriétés méta d'un fichier PDF en Java.">}}
 

## Lire les propriétés PDF à l'aide de Java {#Read-PDF-Properties-using-Java}

Nous pouvons lire les informations de base d'un document PDF en suivant les étapes ci-dessous :

  1. Tout d'abord, chargez un document PDF en utilisant la classe _**[PdfFileInfo][11]**_.
  2. Enfin, affichez les informations du document en lisant les valeurs des méta-propriétés.

L'exemple de code suivant montre **comment obtenir les méta-propriétés d'un fichier PDF à l'aide de Java**.

```
// Cet exemple de code montre comment obtenir les informations de base d'un document PDF.
// Ouvrir le document
PdfFileInfo fileInfo = new PdfFileInfo("D:\\Files\\PDF\\Updated_Info_output.pdf");

// Obtenir des informations PDF
System.out.println("Subject :" + fileInfo.getSubject());
System.out.println("Title :" + fileInfo.getTitle());
System.out.println("Keywords :" + fileInfo.getKeywords());
System.out.println("Creator :" + fileInfo.getCreator());
System.out.println("Creation Date :" + fileInfo.getCreationDate());
System.out.println("Modification Date :" + fileInfo.getModDate());

// Trouvez s'il s'agit d'un PDF valide et s'il est également crypté
System.out.println("Is Valid PDF :" + fileInfo.isPdfFile());
// si le fichier est crypté, vous devez fournir un mot de passe d'ouverture de fichier
// comme deuxième argument du constructeur PdfFileInfo
System.out.println("Is Encrypted :" + fileInfo.isEncrypted());
```

```
Subject :PDF Information
Title :Editing Metadata
Keywords :Aspose.Pdf, DOM, API
Creator :Aspose
Creation Date :D:20170612160123-04'00'
Modification Date :D:20220405214422+05'00'
Is Valid PDF :true
Is Encrypted :false
```

## Obtenir les métadonnées XMP d'un fichier PDF en Java {#Get-XMP-Metadata-of-a-PDF-File-in-Java}

Nous pouvons lire les métadonnées XMP d'un document PDF en suivant les étapes ci-dessous :

  1. Tout d'abord, chargez un document PDF en utilisant la classe _**[Document][13]**_.
  2. Enfin, lisez les métadonnées à l'aide de la méthode _**[get_Item()][14]**_ de la classe _**[Metadata][15]**_ et extrayez les informations.

L'exemple de code suivant montre **comment obtenir les métadonnées XMP d'un fichier PDF à l'aide de Java**.

```
// Cet exemple de code montre comment obtenir les métadonnées XMP d'un document PDF.
// Ouvrir le document
Document pdfDocument = new Document("D:\\Files\\PDF\\SetXMPMetadata.pdf");

// Obtenir des propriétés
System.out.println("xmp:CreateDate: " + pdfDocument.getMetadata().get_Item("xmp:CreateDate"));
System.out.println("xmp:Nickname: " + pdfDocument.getMetadata().get_Item("xmp:Nickname"));
System.out.println("xmp:CustomProperty: " + pdfDocument.getMetadata().get_Item("xmp:CustomProperty"));
```

```
xmp:CreateDate : 2022-04-05T10:05:24.4
xmp:Nickname : Nickname
xmp:CustomProperty : Custom Value
```

## Définir les métadonnées XMP dans un fichier PDF en Java {#Set-XMP-Metadata-in-a-PDF-File-in-Java}

Nous pouvons définir les métadonnées XMP dans un fichier PDF en suivant les étapes ci-dessous :

  1. Tout d'abord, chargez un document PDF en utilisant la classe _**[Document][13]**_.
  2. Ensuite, définissez les valeurs des métadonnées à l'aide de la méthode _**[set_Item()][16]**_ de la classe **_[Metadata][15]_**.
  3. Enfin, enregistrez le fichier PDF en utilisant la méthode _**[Document.save()][17]**_ avec le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment définir les métadonnées XMP d'un fichier PDF à l'aide de Java**.

```
// Cet exemple de code montre comment définir les métadonnées XMP d'un document PDF.
// Ouvrir le document
Document pdfDocument = new Document("D:\\Files\\PDF\\sample.pdf");

// Définir les propriétés
pdfDocument.getMetadata().set_Item("xmp:CreateDate", new XmpValue(new java.util.Date()));
pdfDocument.getMetadata().set_Item("xmp:Nickname", new XmpValue("Nickname"));
pdfDocument.getMetadata().set_Item("xmp:CustomProperty", new XmpValue("Custom Value"));

// Enregistrer le document
pdfDocument.save("D:\\Files\\PDF\\SetXMPMetadata.pdf");
```

## Personnaliser l'espace de noms de métadonnées XMP dans un fichier PDF {#Customize-XMP-Metadata-Namespace-in-a-PDF-File}

Nous pouvons définir l'URI de l'espace de noms personnalisé au lieu des spécifications XMP définies dans un fichier PDF. À cette fin, l'API fournit la méthode **_[registerNamespaceUri][18]_** dans la classe **_[Metadata][15]_**. Nous pouvons créer un nouvel espace de noms de métadonnées avec un préfixe en suivant les étapes ci-dessous :

  1. Tout d'abord, chargez un document PDF à l'aide de la classe [**_Document_**][13].
  2. Ensuite, appelez la méthode **_registerNamespaceUri()_** avec un préfixe et un URI d'espace de noms comme arguments.
  3. Ensuite, définissez les valeurs des métadonnées à l'aide de la méthode _**[set_Item()][16]**_.
  4. Enfin, enregistrez le fichier PDF en utilisant la méthode **_[Document.Save()][17]_** avec le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment définir un espace de noms de métadonnées personnalisé dans un fichier PDF à l'aide de Java**.

```
// Cet exemple de code montre comment définir les métadonnées XMP personnalisées d'un document PDF.
// Ouvrir le document
Document pdfDocument = new Document("D:\\Files\\PDF\\sample.pdf");

// Définir des propriétés personnalisées
pdfDocument.getMetadata().registerNamespaceUri("myown", "http:// myown.xyz.com/xap/1.0/");
pdfDocument.getMetadata().set_Item("myown:ModifyDate", new XmpValue(new java.util.Date()));
pdfDocument.getMetadata().set_Item("myown:CreateDate", new XmpValue(new java.util.Date()));
pdfDocument.getMetadata().set_Item("myown:DeveloperName", new XmpValue("Developer Name"));
pdfDocument.getMetadata().set_Item("myown:MyProperty", new XmpValue("My Custom Value"));

// Enregistrer le document
pdfDocument.save("D:\\Files\\PDF\\CustomizedXMPMetadata.pdf");
```

Nous pouvons lire les propriétés de métadonnées XMP personnalisées en suivant les étapes mentionnées précédemment.

```
NamespaceUri: http:// myown.xyz.com/xap/1.0/
myown:ModifyDate: 2022-04-05T10:18:45.9
myown:CreateDate: 2022-04-05T10:18:45.9
myown:DeveloperName: Developer Name
myown:MyProperty: My Custom Value
```

## Obtenez une licence API gratuite {#Get-a-Free-License}

Vous pouvez essayer l'API sans limitation d'évaluation en demandant [une licence temporaire gratuite][19].

## Conclusion

Dans cet article, nous avons appris à :

  * ajouter/modifier les informations de base d'un document PDF à l'aide de Java ;
  * définir/obtenir les métadonnées XMP dans un fichier PDF à l'aide de Java ;
  * définir l'URI de l'espace de noms de métadonnées personnalisées avec un préfixe.

En outre, vous pouvez en savoir plus sur Aspose.PDF pour l'API Java en utilisant la [documentation][20]. En cas d'ambiguïté, n'hésitez pas à nous contacter sur le [forum][21].

## Voir également

  * [Convertir PDF en HTML en utilisant Java][22]
  * [Ajouter des notes de bas de page et des notes de fin au format PDF à l'aide de Java][23]

 [1]: #Java-API-to-Edit-PDF-Properties-and-Metadata
 [2]: #Edit-PDF-Properties-using-Java
 [3]: #Read-PDF-Properties-using-Java
 [4]: #Get-XMP-Metadata-of-a-PDF-File-in-Java
 [5]: #Set-XMP-Metadata-in-a-PDF-File-in-Java
 [6]: #Customize-XMP-Metadata-Namespace-in-a-PDF-File
 [7]: https://docs.fileformat.com/pdf/
 [8]: https://products.aspose.com/pdf/java/
 [9]: https://docs.aspose.com/pdf/java/supported-file-formats/
 [10]: https://downloads.aspose.com/pdf/java
 [11]: https://apireference.aspose.com/pdf/java/com.aspose.pdf.facades/PdfFileInfo
 [12]: https://apireference.aspose.com/pdf/java/com.aspose.pdf.facades/PdfFileInfo#saveNewInfo-java.lang.String-
 [13]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Document
 [14]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Metadata#get_Item-java.lang.String-
 [15]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Metadata
 [16]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Metadata#set_Item-java.lang.String-com.aspose.pdf.XmpValue-
 [17]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Document#save-java.lang.String-
 [18]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Metadata#registerNamespaceUri-java.lang.String-java.lang.String-
 [19]: https://purchase.conholdate.com/temporary-license
 [20]: https://docs.aspose.com/pdf/java
 [21]: https://forum.aspose.com/c/pdf/10
 [22]: https://blog.conholdate.com/2022/02/19/convert-pdf-to-html-using-java/
 [23]: https://blog.conholdate.com/2022/02/07/add-footnotes-and-endnotes-in-pdf-using-java/
