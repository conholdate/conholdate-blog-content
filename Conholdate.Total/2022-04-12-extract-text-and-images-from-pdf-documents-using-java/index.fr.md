---
title: "Extraire du texte et des images de documents PDF à l'aide de Java"
author: Muzammil Khan
date: 2022-04-12T03:52:00+00:00
summary: "En tant que développeur Java, vous pouvez facilement extraire du texte et des images de vos documents PDF par programmation. Dans cet article, vous apprendrez ** comment extraire du texte et des images de documents PDF à l'aide de Java **."
url: /fr/2022/04/12/extraire-texte-et-images-des-documents-pdf-en-utilisant-java/
categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "Extraction de texte de document"
  - "Extraction d'images de documents"
  - "Extraire le texte"
  - "Extraire des images"
  - "Extraire le texte" from PDF
  - "Extraire des images" from PDF
  - "Extraction de texte"
  - "Extraction de texte" API
  - "API d'extraction de texte pour Java"
  - "Extraction d'images"
  - "API d'extraction d'images"
  - "API d'extraction d'images pour Java"
---

{{< figure align=center src="images/extract-text-and-images-from-pdf-documents-using-java.jpg" alt="Extraire du texte et des images de documents PDF à l'aide de Java">}}

[PDF][1] est le format de document numérique le plus utilisé. Nous pouvons analyser des documents PDF et en extraire du texte et des images par programmation. Cela pourrait être utile dans plusieurs cas, tels que l'analyse de texte, la recherche d'informations, la conversion de documents, etc. Dans cet article, nous allons apprendre **comment extraire du texte et des images de documents PDF en utilisant Java**.

Les sujets suivants seront traités dans cet article :

  * [API Java pour extraire du texte et des images à partir de documents PDF][2]
  * [Extraire du texte de documents PDF à l'aide de Java][3]
  * [Extraire le texte de pages spécifiques d'un document PDF à l'aide de Java][4]
  * [Obtenir des images à partir de documents PDF à l'aide de Java][5]
  * [Extraire des images de pages spécifiques d'un document PDF à l'aide de Java][6]
  * [Extraire et enregistrer des images dans des fichiers à l'aide de Java][7]

## API Java pour extraire du texte et des images à partir de documents PDF {#Java-API-to-Extract-Text-and-Images-from-PDF-Documents}

Pour extraire du texte et des images à partir de documents PDF, nous utiliserons l'API [GroupDocs.Parser for Java][8]. Il permet l'extraction de texte, de métadonnées et d'images bruts, formatés et structurés à partir de fichiers aux [formats pris en charge] [9]. Veuillez soit [télécharger][10] le JAR de l'API ou ajouter la configuration _pom.xml_ suivante dans une application Java basée sur Maven.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
```

```
<dependency>
	<groupId>com.groupdocs</groupId>
	<artifactId>groupdocs-parser</artifactId>
	<version>22.3</version> 
</dependency>
```

## Extraire du texte de documents PDF à l'aide de Java {#Extract-Text-from-PDF-Documents-using-Java}

Nous pouvons analyser n'importe quel document PDF et extraire du texte en suivant les étapes ci-dessous :

  * Tout d'abord, chargez le fichier PDF à l'aide de la classe [Parser][11].
  * Ensuite, appelez la méthode _[Parser.getText()][12]_ pour extraire le texte du document chargé.
  * Ensuite, obtenez les résultats dans l'objet de classe _[TextReader][13]_.
  * Enfin, appelez la méthode _[TextReader.readToEnd()][14]_ pour lire tous les caractères de la position actuelle à la fin du lecteur de texte et les renvoyer sous la forme d'une chaîne.

L'exemple de code suivant montre comment extraire du texte d'un fichier PDF à l'aide de Java.

```
// Cet exemple de code montre comment analyser un PDF et extraire du texte.
// Créer une instance de la classe Parser
Parser parser = new Parser("D:\\Files\\Parser\\sample.pdf");

// Extraire un texte dans le lecteur
try (TextReader reader = parser.getText()) {
    // Print a text from the document
    // If text extraction isn't supported, a reader is null
    System.out.println(reader == null ? "Text extraction isn't supported" : reader.readToEnd());
}
```

{{< figure align=center src="images/Extract-Text-from-PDF-Documents-using-Java.jpg" alt="Extraire du texte de documents PDF à l'aide de Java" caption="Extraire du texte de documents PDF à l'aide de Java">}}
 
## Extraire le texte d'une page spécifique d'un document PDF à l'aide de Java {#Extract-Text-from-Specific-Page-of-a-PDF-Document-using-Java}

Vous pouvez analyser un document PDF et extraire le texte d'une page spécifique en suivant les étapes simples mentionnées ci-dessous :

  * Tout d'abord, chargez le fichier PDF à l'aide de la classe [Parser][11].
  * Ensuite, obtenez les informations sur le document à l'aide de la méthode _[Parser.getDocumentInfo()][15]_.
  * Ensuite, vérifiez si _[IDocumentInfo.getPageCount()][16]_ n'est pas nul.
  * Après cela, appelez la méthode [Parser.getText()][12] avec l'index de page pour extraire le texte de cette page spécifique et obtenir les résultats dans l'objet de classe [TextReader][13].
  * Enfin, affichez les résultats en appelant la méthode [TextReader.readToEnd()][14] pour lire le texte extrait.

L'exemple de code suivant montre comment extraire du texte d'une page spécifique à l'aide de Java.

```
// Cet exemple de code montre comment analyser un PDF et extraire du texte d'une page spécifique.
// Créer une instance de la classe Parser
Parser parser = new Parser("D:\\Files\\Parser\\sample.pdf");

// Obtenir les informations sur le document
IDocumentInfo documentInfo = parser.getDocumentInfo();

// Vérifiez si le document contient des pages
if (documentInfo == null || documentInfo.getRawPageCount() == 0) {
    System.out.println("Document hasn't pages.");
    return;
}

// Extraire un texte dans le lecteur
try (TextReader reader = parser.getText(1)) {
    // Print a text from the document
    // If text extraction isn't supported, a reader is null
    System.out.println(reader.readToEnd());
}
```

L'API permet également de vérifier si le document prend en charge la fonction d'extraction de texte. À cette fin, nous pouvons utiliser la propriété [Parser.getFeatures().isText()][17]. Veuillez en savoir plus sur les [fonctionnalités prises en charge][18].

## Obtenir des images à partir de documents PDF à l'aide de Java {#Get-Images-from-PDF-Documents-using-Java}

Nous pouvons analyser n'importe quel document PDF et extraire des images en suivant les étapes ci-dessous :

  * Tout d'abord, chargez le fichier PDF à l'aide de la classe [Parser][11].
  * Ensuite, appelez la méthode _[Parser.getImages()][19]_ et obtenez la collection d'objets _[PageImageArea][20]_ à partir du document chargé.
  * Ensuite, vérifiez si la collection n'est pas nulle.
  * Après cela, parcourez toutes les images trouvées.
  * Enfin, affichez les détails des images.

L'exemple de code suivant montre comment obtenir des détails d'images à partir d'un fichier PDF à l'aide de Java.

```
// Cet exemple de code montre comment analyser un PDF et obtenir des images.
// Créer une instance de la classe Parser
Parser parser = new Parser("D:\\Files\\Parser\\images.pdf");

// Extraire des images
Iterable<PageImageArea> images = parser.getImages();

// Vérifiez si l'extraction d'images est prise en charge
if (images == null) {
    System.out.println("Images extraction isn't supported");
    return;
}

// Itérer sur les images
for (PageImageArea image : images) {
    // Print a page index, rectangle and image type:
    System.out.println("Page: " + image.getPage().getIndex());
    System.out.println("Image Rectangle: " + image.getRectangle());
    System.out.println("Image Filetype: " + image.getFileType());
    System.out.println("----------------------------------------");
}
```

{{< figure align=center src="images/Get-Images-from-PDF-Documents-using-Java.jpg" alt="Obtenir des images à partir de documents PDF en utilisant Java" caption="Obtenir des images à partir de documents PDF à l'aide de Java">}}

## Extraire des images d'une page spécifique d'un document PDF à l'aide de Java {#Extract-Images-from-Specific-Page-of-a-PDF-Document-using-Java}

Nous pouvons extraire des images d'une page spécifique en suivant les étapes simples mentionnées ci-dessous :

  * Tout d'abord, chargez le fichier PDF à l'aide de la classe [Parser][11].
  * Ensuite, obtenez les informations sur le document à l'aide de la méthode _[Parser.getDocumentInfo()][15]_.
  * Ensuite, vérifiez si _[IDocumentInfo.getPageCount()][16]_ n'est pas nul.
  * Après cela, appelez la méthode [Parser.getImages()][21] avec l'index de la page pour extraire les images de cette page spécifique.
  * Enfin, parcourez toutes les images trouvées et affichez les détails.

L'exemple de code suivant montre comment extraire des images d'une page spécifique à l'aide de Java.

```
// Cet exemple de code montre comment analyser un PDF et obtenir des images à partir d'une page spécifique.
// Créer une instance de la classe Parser
Parser parser = new Parser("D:\\Files\\Parser\\images.pdf");

// Obtenir les informations sur le document
IDocumentInfo documentInfo = parser.getDocumentInfo();

// Vérifiez si le document contient des pages
if (documentInfo.getPageCount() == 0) {
    System.out.println("Document hasn't pages.");
    return;
}

int pageIndex = 1;

// Itérer sur les images
// Nous ignorons la vérification nulle car nous avons vérifié la prise en charge de la fonction d'extraction d'images plus tôt
for (PageImageArea image : parser.getImages(pageIndex)) {
  // Print a page index, rectangle and image type:
    System.out.println("Page: " + image.getPage().getIndex());
    System.out.println("Image Rectangle: " + image.getRectangle());
    System.out.println("Image Filetype: " + image.getFileType());
    System.out.println("----------------------------------------");
}
```

## Extraire et enregistrer des images dans des fichiers à l'aide de Java {#Extract-and-Save-Images-to-Files-using-Java}

Nous pouvons également enregistrer les images extraites en suivant les étapes ci-dessous :

  * Tout d'abord, chargez le fichier PDF à l'aide de la classe [Parser][11].
  * Ensuite, appelez la méthode _[Parser.getImages()][19]_ et obtenez la collection d'objets PageImageArea à partir du document chargé.
  * Ensuite, créez une instance de la classe _[ImageOptions][22]_ et définissez le format de l'image.
  * Après cela, parcourez toutes les images trouvées.
  * Enfin, enregistrez en utilisant la méthode _[save()][23]_. Il prend le chemin du fichier de sortie et ImageOptions comme arguments.

L'exemple de code suivant montre comment extraire et enregistrer des images dans des fichiers à l'aide de Java.

```
// Cet exemple de code montre comment extraire et images dans le répertoire.
// Créer une instance de la classe Parser
Parser parser = new Parser("D:\\Files\\Parser\\images.pdf");

// Extraire des images du document
Iterable<PageImageArea> images = parser.getImages();

// Vérifiez si l'extraction d'images est prise en charge
if (images == null) {
    System.out.println("Page images extraction isn't supported");
    return;
}

// Créer les options pour enregistrer les images au format PNG
ImageOptions options = new ImageOptions(ImageFormat.Png);

int imageNumber = 0;

// Itérer sur les images
for (PageImageArea image : images)
{
    // Save the image to the PNG file
    image.save(String.format("D:\\Files\\Parser\\Images\\%d.png", imageNumber), options);
    imageNumber++;
}
```

{{< figure align=center src="images/Extract-and-Save-Images-to-Files-using-Java.jpg" alt="Extraire et enregistrer des images dans des fichiers à l'aide de Java" caption="Extraire et enregistrer des images dans des fichiers à l'aide de Java">}}

## Obtenez une licence gratuite
Vous pouvez essayer l'API sans limites d'évaluation en demandant [une licence temporaire gratuite][24].

## Conclusion
Dans cet article, nous avons appris à :

  * extraire tout le texte d'un document PDF entier ou de pages spécifiques du document à l'aide de Java ;
  * extraire des images d'un fichier PDF par programmation ;
  * enregistrer les images extraites sur un disque local.

En outre, vous pouvez en savoir plus sur l'API GroupDocs.Parser pour Java en utilisant la [documentation][25]. En cas d'ambiguïté, n'hésitez pas à nous contacter sur le [forum][26].

## Voir également

  * [Extraire du texte de documents Word à l'aide de Java][27]

 [1]: https://docs.fileformat.com/pdf/
 [2]: #Java-API-to-Extract-Text-and-Images-from-PDF-Documents
 [3]: #Extract-Text-from-PDF-Documents-using-Java
 [4]: #Extract-Text-from-Specific-Page-of-a-PDF-Document-using-Java
 [5]: #Get-Images-from-PDF-Documents-using-Java
 [6]: #Extract-Images-from-Specific-Page-of-a-PDF-Document-using-Java
 [7]: #Extract-and-Save-Images-to-Files-using-Java
 [8]: https://products.groupdocs.com/parser/java/
 [9]: https://docs.groupdocs.com/parser/java/supported-document-formats/
 [10]: https://downloads.groupdocs.com/parser/java
 [11]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser
 [12]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getText()
 [13]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/TextReader
 [14]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/TextReader#readToEnd()
 [15]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getDocumentInfo()
 [16]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/IDocumentInfo#getPageCount()
 [17]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/Features#isText()
 [18]: https://docs.groupdocs.com/parser/java/get-supported-features/
 [19]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getImages()
 [20]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/PageImageArea
 [21]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getImages(int)
 [22]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.options/ImageOptions
 [23]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/PageImageArea#save(java.lang.String,%20com.groupdocs.parser.options.ImageOptions)
 [24]: https://purchase.groupdocs.com/temporary-license
 [25]: https://docs.groupdocs.com/parser/java/
 [26]: https://forum.groupdocs.com/c/parser/
 [27]: https://blog.conholdate.com/2021/10/13/extract-text-from-word-documents-using-java/








