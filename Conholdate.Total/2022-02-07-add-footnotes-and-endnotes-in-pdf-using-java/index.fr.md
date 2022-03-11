---
title: Ajouter des notes de bas de page et des notes de fin au format PDF à l'aide de Java
author: Muzammil Khan
date: 2022-02-07T07:18:39+00:00
summary: "En tant que développeur Java, vous pouvez ajouter des notes de bas de page/notes de fin aux documents PDF par programme. Dans cet article, vous apprendrez **à ajouter des notes de bas de page et des notes de fin dans des documents PDF à l'aide de Java** ."
url: /fr/2022/02/07/add-footnotes-and-endnotes-in-pdf-using-java/
categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "Ajouter une note de bas de page au PDF en Java"
  - "Ajouter des notes de bas de page en PDF"
  - "Ajouter des notes de bas de page en PDF using Java"
  - "Ajouter une image à la note de bas de page à l'aide de Java"
  - "Ajouter un tableau à la note de bas de page à l'aide de Java"

---

{{< figure align=center src="images/add-footnotes-and-endnotes-in-pdf-using-java.jpg" alt="Ajoutez des notes de bas de page et des notes de fin au format PDF à l'aide de Java.">}}
 
Une note de bas de page est une note ou un texte donné au bas d'une page spécifique, tandis que la note de fin est une note placée à la fin d'un document. Nous utilisons généralement des notes de bas de page ou des notes de fin pour les références, les explications ou les commentaires dans le document. Nous pouvons ajouter des notes de bas de page/notes de fin au document PDF par programme. Dans cet article, nous allons apprendre **comment ajouter des notes de bas de page et des notes de fin dans des documents PDF à l'aide de Java**.

Les sujets suivants seront traités dans cet article:

  - [API Java pour ajouter des notes de bas de page et des notes de fin en PDF](#Java-API-to-Add-Footnotes-and-Endnotes-in-PDF) 
  - [Ajouter des notes de bas de page à un PDF à l'aide de Java](#Add-Footnotes-to-a-PDF-using-Java)
  - [Ajouter une image à la note de bas de page en PDF](#Add-an-Image-to-Footnote-in-PDF)
  - [Insérer un tableau dans une note de bas de page en PDF](#Insert-a-Table-to-Footnote-in-PDF)
  - [Personnaliser l'étiquette de la note de bas de page et le style de ligne à l'aide de Java](#Customize-Footnote-Label-and-Line-Style-using-Java)
  - [Ajouter des notes de bas de page à un PDF existant à l'aide de Java](#Add-Footnotes-to-Existing-PDF-using-Java)
  - [Ajouter des notes de fin au PDF en utilisant Java](#Add-Endnotes-to-PDF-using-Java)

## API Java pour ajouter des notes de bas de page et des notes de fin en PDF {#Java-API-to-Add-Footnotes-and-Endnotes-in-PDF}

Pour ajouter des notes de bas de page et des notes de fin à un document [PDF][2], nous utiliserons [Aspose.PDF for Java API][3]. Il nous permet de générer, modifier, convertir, restituer, sécuriser et imprimer [documents pris en charge][4] sans utiliser Adobe Acrobat. Veuillez soit [télécharger][5] le JAR de l'API ou simplement ajouter la configuration **_pom.xml_** suivante dans une application Java basée sur Maven.

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
    <version>22.1</version>
</dependency>
```

## Ajouter des notes de bas de page à un PDF à l'aide de Java {#Add-Footnotes-to-a-PDF-using-Java}

Nous pouvons ajouter des notes de bas de page à la fin de la page dans un document PDF en suivant les étapes ci-dessous:
  1. Tout d'abord, créez une instance de la classe [**_Document_**][6].
  2. Ensuite, ajoutez une **_[Page][7]_** à la **_[PagesCollection][8]_** du document.
  3. Ensuite, créez un **_[TextFragment][9]_**.
  4. Ensuite, définissez la valeur **_[Footnote][10]_** pour l'objet _TextFragment_.
  5. Ensuite, ajoutez _TextFragment_ à la collection **[_Paragraphs_][11]**
  6. Si vous le souhaitez, répétez les étapes ci-dessus pour ajouter plus de _TextFragments_ pour plusieurs valeurs _Footnote_.
  7. Enfin, enregistrez le fichier PDF en utilisant la méthode **_[Document.Save()][12]_**. Il prend le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment ajouter des notes de bas de page à un document PDF à l'aide de Java**.

```
// Cet exemple de code montre comment ajouter des notes de bas de page à un document PDF.
// Créer une instance de Document
Document document = new Document();

// Ajouter une page à la collection de pages de PDF
Page page = document.getPages().add();

// Créer un fragment de texte
TextFragment text = new TextFragment("Hello World");

// Définir la valeur de la note de bas de page pour TextFragment
text.setFootNote(new Note("foot note for Hello World!"));

// Ajouter TextFragment à la collection de paragraphes de la première page du document
page.getParagraphs().add(text);

// Créer un autre TextFragment
text = new TextFragment("Aspose.Pdf for Java");

// Définir la note de bas de page pour le deuxième TextFragment
text.setFootNote(new Note("foot note for second text fragment!"));

// Ajouter un deuxième fragment de texte à la collection de paragraphes du fichier PDF
page.getParagraphs().add(text);

// Enregistrer le document
document.save("C:\\Files\\PDF\\sample_footnote.pdf");
```

{{< figure align=center src="images/Add-Footnotes-to-a-PDF-using-Java.jpg" alt="Ajoutez des notes de bas de page à un PDF à l'aide de Java." caption="Ajoutez des notes de bas de page à un PDF à l'aide de Java.">}}
 

## Ajouter une image à la note de bas de page en PDF {#Add-an-Image-to-Footnote-in-PDF}

Nous pouvons ajouter une image dans les notes de bas de page d'un document PDF en suivant les étapes ci-dessous:
  1. Tout d'abord, créez une instance de la classe [**_Document_**][6].
  2. Ensuite, ajoutez une **_[Page][7]_** à la **_[PagesCollection][8]_** du document.
  3. Ensuite, créez un **_[TextFragment][9]_**.
  4. Ensuite, définissez la valeur **_[Footnote][10]_** pour l'objet _TextFragment_.
  5. Ensuite, ajoutez une image à l'objet _TextFragment_.
  6. Après cela, ajoutez _TextFragment_ à la collection **[_Paragraphs_][11]**
  7. Enfin, enregistrez le fichier PDF en utilisant la méthode **_[Document.Save()][12]_**. Il prend le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment ajouter une image dans les notes de bas de page d'un document PDF à l'aide de Java**.

```
// Cet exemple de code montre comment insérer une image dans les notes de bas de page.
// Créer une instance de Document
Document document = new Document();

// Ajouter une page à la collection de pages de PDF
Page page = document.getPages().add();

// Créer un fragment de texte
TextFragment text = new TextFragment("Hello World");

// Définir la valeur de la note de bas de page pour TextFragment
text.setFootNote(new Note());

// Ajouter une image
Image image = new Image();
image.setFile("C:\\Files\\PDF\\aspose_logo.jpg");
image.setFixHeight(20);
text.getFootNote().getParagraphs().add(image);

// Créer un fragment de texte
TextFragment footNote = new TextFragment(" foot note for Hello World!");
footNote.getTextState().setFontSize(20);
footNote.setInLineParagraph(true);
text.getFootNote().getParagraphs().add(footNote);

// Ajouter TextFragment à la collection de paragraphes de la première page du document
page.getParagraphs().add(text);

// Enregistrer le document
document.save("C:\\Files\\PDF\\image_footnote.pdf");
```

{{< figure align=center src="images/Add-an-Image-to-Footnote-in-PDF-1024x972.jpg" alt="" légende="Add an Image to Footnote in PDF.">}}
 

## Insérer un tableau dans une note de bas de page en PDF {#Insert-a-Table-to-Footnote-in-PDF}

Nous pouvons également ajouter un tableau dans les notes de bas de page d'un document PDF en suivant les étapes ci-dessous:
  1. Tout d'abord, créez une instance de la classe [**_Document_**][6].
  2. Ensuite, ajoutez une **_[Page][7]_** à la **_[PagesCollection][8]_** du document.
  3. Ensuite, créez un **_[TextFragment][9]_**.
  4. Ensuite, définissez la valeur **_[Footnote][10]_** pour l'objet _TextFragment_.
  5. Ensuite, ajoutez un **_[table][15]_** à l'objet _TextFragment_.
  6. Après cela, ajoutez _TextFragment_ à la collection **[_Paragraphs_][11]**
  7. Enfin, enregistrez le fichier PDF en utilisant la méthode **_[Document.Save()][12]_**. Il prend le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment ajouter un tableau dans les notes de bas de page d'un document PDF à l'aide de Java**.

```
// Cet exemple de code montre comment ajouter un tableau aux notes de bas de page.
// Créer une instance de document
Document document = new Document();

// Ajouter une page à la collection de pages de PDF
Page page = document.getPages().add();

// Créer une instance TextFragment
TextFragment text = new TextFragment("Hello World");

// Définir la valeur de la note de bas de page pour TextFragment
text.setFootNote(new Note());

// Insérer un tableau
Table table = new Table();
table.getRows().add().getCells().add().getParagraphs().add(new TextFragment("Row 1 Cell 1"));
table.getRows().get_Item(0).getCells().add().getParagraphs().add(new TextFragment("Row 1 Cell 2"));
table.getRows().add().getCells().add().getParagraphs().add(new TextFragment("Row 2 Cell 1"));
table.getRows().get_Item(1).getCells().add().getParagraphs().add(new TextFragment("Row 2 Cell 2"));
text.getFootNote().getParagraphs().add(table);

// Ajouter TextFragment à la collection de paragraphes de la première page du document
page.getParagraphs().add(text);

// Enregistrer le document
document.save("C:\\Files\\PDF\\Table_footnote.pdf");
```

{{< figure align=center src="images/Insert-a-Table-to-Footnote-in-PDF.jpg" alt="Insérer un tableau dans la note de bas de page au format PDF." caption="Insérer un tableau dans la note de bas de page au format PDF.">}}
 

## Personnaliser l'étiquette de la note de bas de page et le style de ligne à l'aide de Java {#Customize-Footnote-Label-and-Line-Style-using-Java}

Nous pouvons personnaliser l'étiquette des notes de bas de page et le style de ligne des notes de bas de page dans un document PDF en suivant les étapes ci-dessous:
  1. Tout d'abord, créez une instance de la classe [**_Document_**][6].
  2. Ensuite, ajoutez une **_[Page][7]_** à la **_[PagesCollection][8]_** du document.
  3. Ensuite, initialisez un objet **_[GraphInfo][17]_** pour personnaliser le style de ligne.
  4. Définissez les propriétés de l'objet GraphInfo telles que LineWidth, Color, DashArray, etc.
  5. Ensuite, créez un **_[TextFragment][9]_**.
  6. Ensuite, définissez la valeur **_[Footnote][10]_** pour l'objet _TextFragment_.
  7. Ensuite, initialisez l'objet TextState et définissez diverses propriétés, par exemple ForegroundColor, FontStyle, etc.
  8. Après cela, ajoutez _TextFragment_ à la collection **[_Paragraphs_][11]**
  9. Si vous le souhaitez, répétez les étapes ci-dessus pour ajouter plus de _TextFragments_ pour plusieurs valeurs _Footnote_.
 10. Enfin, enregistrez le fichier PDF en utilisant la méthode **_[Document.Save()][12]_**. Il prend le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment personnaliser l'étiquette et le style de ligne des notes de bas de page à l'aide de Java**.

```
// Cet exemple de code montre comment personnaliser l'étiquette et le style de ligne des notes de bas de page.
// Créer une instance de document
Document document = new Document();

// Ajouter une page à la collection de pages de PDF
Page page = document.getPages().add();

// Personnaliser le style de ligne
// créer un objet GraphInfo
GraphInfo graph = new GraphInfo();

// définir la largeur de ligne sur 2
graph.setLineWidth(2);

// définir la couleur de l'objet graphique
graph.setColor(Color.getRed());

// définir la valeur du tableau de tirets sur 3
graph.setDashArray(new int[] { 3 });

// définir la valeur de la phase du tiret sur 1
graph.setDashPhase(1);

// définir le style de ligne de note de bas de page pour la page en tant que graphique
page.setNoteLineStyle(graph);

// Créer une instance TextFragment
TextFragment text = new TextFragment("Hello World");

// Définir la valeur de la note de bas de page pour TextFragment
text.setFootNote(new Note("foot note for Hello World!"));

// Personnaliser l'étiquette
text.getFootNote().setText("FOOTNOTE-1");
TextState ts = new TextState();
ts.setForegroundColor(Color.getBlue());
ts.setFontStyle(FontStyles.Italic);
text.getFootNote().setTextState(ts);

// Ajouter TextFragment à la collection de paragraphes de la première page du document
page.getParagraphs().add(text);

// Créer un autre TextFragment
text = new TextFragment("Aspose.Pdf for Java");

// Définir la note de bas de page pour le deuxième fragment de texte
text.setFootNote(new Note("foot note for second text fragment!"));

// Ajouter un deuxième fragment de texte à la collection de paragraphes du fichier PDF
page.getParagraphs().add(text);

// Enregistrer le document
document.save("C:\\Files\\PDF\\customize_footnote.pdf");
```

{{< figure align=center src="images/Customize-Footnote-Label-and-Line-Style-using-Java.jpg" alt="Personnalisez l'étiquette de la note de bas de page et le style de ligne à l'aide de Java." caption="Personnalisez l'étiquette de la note de bas de page et le style de ligne à l'aide de Java.">}}
 

## Ajouter des notes de bas de page à un PDF existant à l'aide de Java {#Add-Footnotes-to-Existing-PDF-using-Java}

Nous pouvons ajouter des notes de bas de page à un document PDF existant en suivant les étapes ci-dessous:
  1. Tout d'abord, chargez un fichier PDF à l'aide de la classe [**_Document_**][6].
  2. Ensuite, obtenez une **_[page][7]_** particulière par son index.
  3. Ensuite, créez un objet **_[TextFragmentAbsorber][19]_** avec une phrase de recherche en entrée.
  4. Après cela, appelez la méthode [_**accept()**_][20] pour rechercher la phrase d'entrée à partir de la page.
  5. Ensuite, récupérez la première occurrence de la phrase de recherche à partir de _**[TextFragmentCollection][21]**_.
  6. Ensuite, créez un **_TextFragment_** vide et définissez sa position sur la page.
  7. Définissez également la valeur **_[Footnote][10]_** pour l'objet _TextFragment_.
  8. Après cela, ajoutez _TextFragment_ à la collection **[_Paragraphs_][11]**
  9. Enfin, enregistrez le fichier PDF en utilisant la méthode **_[Document.Save()][12]_**. Il prend le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment ajouter des notes de bas de page à un document PDF existant à l'aide de Java**.

```
// Cet exemple de code montre comment ajouter des notes de bas de page à un document PDF existant.
// Charger un document PDF existant
Document document = new Document("C:\\Files\\PDF\\sample.pdf");

// Créez un objet TextAbsorber pour trouver toutes les instances de la phrase de texte
TextFragmentAbsorber textFragmentAbsorber = new TextFragmentAbsorber("Class");

// Obtenir une page particulière
Page page = document.getPages().get_Item(2);

// Accepter l'absorbeur pour la deuxième page du document
page.accept(textFragmentAbsorber);

// Obtenez les fragments de texte extraits dans la collection
TextFragmentCollection textFragmentCollection = textFragmentAbsorber.getTextFragments();

// Obtenir la première occurrence du texte
TextFragment textFragment = textFragmentCollection.get_Item(1);

// Créer un TextFragment vide
TextFragment text = new TextFragment("");

// Définir la position
Position position = textFragment.getPosition();
position = new Position(position.getXIndent() + 26, position.getYIndent());
text.setPosition(position);

// Définir la valeur de la note de bas de page pour TextFragment
text.setFootNote(new Note("This is example footnote added in an existing PDF!"));

// Ajouter un deuxième fragment de texte à la collection de paragraphes du fichier PDF
page.getParagraphs().add(text);

// Enregistrer le document
document.save("C:\\Files\\PDF\\Text_Added.pdf");
```

{{< figure align=center src="images/Add-Footnotes-to-Existing-PDF-using-Java-1024x970.jpg" alt="Ajouter des notes de bas de page à un PDF existant à l'aide de Java" caption="Ajoutez des notes de bas de page au PDF existant à l'aide de Java.">}}
 
## Ajouter des notes de fin au PDF en utilisant Java {#Add-Endnotes-to-PDF-using-Java}

Nous pouvons également ajouter des notes de fin à la fin d'un document PDF en suivant les étapes ci-dessous:
  1. Tout d'abord, créez une instance de la classe [**_Document_**][6].
  2. Ensuite, ajoutez une **_[Page][7]_** à la **_[PagesCollection][8]_** du document.
  3. Ensuite, créez un **_[TextFragment][9]_**.
  4. Ensuite, définissez la valeur **_[Endnote][10]_** pour l'objet _TextFragment_.
  5. Définissez éventuellement une étiquette personnalisée pour la note de fin.
  6. Après cela, ajoutez _TextFragment_ à la collection **[_Paragraphs_][11]**.
  7. Enfin, enregistrez le fichier PDF en utilisant la méthode **_[Document.Save()][12]_**. Il prend le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment ajouter des notes de fin à un document PDF à l'aide de Java**.

```
// Cet exemple de code montre comment ajouter des notes de fin à un document PDF.
// Créer une instance de document
Document doc = new Document();

// Ajouter une page à la collection de pages de PDF
Page page = doc.getPages().add();

// Créer une instance TextFragment
TextFragment text = new TextFragment("Hello World");

// Définir la valeur FootNote pour TextFragment
text.setEndNote(new Note("sample End note"));

// Spécifier une étiquette personnalisée pour la note de bas de page
text.getEndNote().setText(" Aspose(2015)");

// Ajouter TextFragment à la collection de paragraphes de la première page du document
page.getParagraphs().add(text);

// Enregistrez le fichier PDF
doc.save("C:\\Files\\PDF\\EndNote.pdf");
```

## Obtenez une licence API gratuite {#Get-a-Free-License}

Vous pouvez essayer l'API sans limitation d'évaluation en demandant [une licence temporaire gratuite][23].

## Conclusion

Dans cet article, nous avons appris à:
  * ajouter des notes de bas de page et des notes de fin à un document PDF à l'aide de Java ;
  * ajouter une image ou un tableau aux notes de bas de page en PDF ;
  * personnaliser l'étiquette de la note de bas de page et le style de ligne à l'aide de Java ;
  * ajouter des notes de bas de page à un document PDF existant à l'aide de Java.

En outre, vous pouvez en savoir plus sur Aspose.PDF pour l'API Java en utilisant la [documentation][24]. En cas d'ambiguïté, n'hésitez pas à nous contacter sur le [forum][25].

## Voir également

  * [Convertir PDF en Word en utilisant Java][26]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/add-footnotes-and-endnotes-in-pdf-using-java.jpg
 [2]: https://docs.fileformat.com/pdf/
 [3]: https://products.aspose.com/pdf/java/
 [4]: https://docs.aspose.com/pdf/net/supported-file-formats/
 [5]: https://downloads.aspose.com/pdf/java
 [6]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/document
 [7]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Page
 [8]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/PageCollection
 [9]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/TextFragment
 [10]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Note
 [11]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Paragraphs
 [12]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Document#save-java.lang.String-
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Add-Footnotes-to-a-PDF-using-Java.jpg
 [14]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Add-an-Image-to-Footnote-in-PDF.jpg
 [15]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Table
 [16]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Insert-a-Table-to-Footnote-in-PDF.jpg
 [17]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/GraphInfo
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Customize-Footnote-Label-and-Line-Style-using-Java.jpg
 [19]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/TextFragmentAbsorber
 [20]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Page#accept-com.aspose.pdf.TextFragmentAbsorber-
 [21]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/TextFragmentCollection
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Add-Footnotes-to-Existing-PDF-using-Java.jpg
 [23]: https://purchase.conholdate.com/temporary-license
 [24]: https://docs.aspose.com/pdf/java
 [25]: https://forum.aspose.com/c/pdf/10
 [26]: https://blog.conholdate.com/2021/07/26/convert-pdf-to-word-using-java/