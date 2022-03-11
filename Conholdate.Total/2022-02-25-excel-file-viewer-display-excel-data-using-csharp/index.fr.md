---
title: "Excel File Viewer - Afficher les données Excel à l'aide de C#"
author: Muzammil Khan
date: 2022-02-25T06:43:17+00:00
summary: "En tant que développeur C#, vous pouvez restituer et afficher des fichiers Excel au format HTML, PDF ou sous forme d'image par programme dans des applications .NET. Dans cet article, vous apprendrez **comment créer une visionneuse de fichiers Excel et afficher des données Excel à l'aide de C#**."
url: /fr/2022/02/25/excel-file-viewer-display-excel-data-using-csharp/
categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "Visionneuse de fichiers Excel C#"
  - "Afficher des données Excel à l'aide de C#"
  - "Excel vers HTML"
  - "Excel vers image"
  - "Excel en PDF"
  - "GroupDocs.Viewer pour .NET"
  - "Rendre Excel en tant qu'image en C #"
  - "Rendre Excel au format PDF en C#"
  - "Rendre des fichiers Excel en C#"
  - "Rendre Excel en HTML en C#"

---


{{< figure align=center src="images/excel-file-viewer-display-excel-data-using-csharp.jpg" alt="Visionneuse de fichiers Excel - Afficher des données Excel à l'aide de C #">}}
 
Nous pouvons afficher les données des fichiers Excel au format HTML, PDF ou sous forme d'image par programmation dans les applications .NET. Il permet de montrer des données à d'autres sans partager les fichiers Excel réels. Dans cet article, nous allons apprendre à créer une **visionneuse de fichiers Excel** et à **afficher des données Excel** à l'aide de **C#**.

Les sujets suivants seront traités dans cet article :

  * [API de visualisation de fichiers C# Excel — Téléchargement gratuit][2]
  * [Afficher des données Excel en HTML à l'aide de C#][3]
  * [Rendu des données Excel au format PDF à l'aide de C#][4]
  * [Afficher le fichier Excel en tant qu'image JPG à l'aide de C #][5]
  * [Ajuster le débordement de texte dans les cellules à l'aide de C #][6]
  * [Rendu des lignes et des colonnes masquées d'Excel][7] 
  * [Ignorer les lignes et les colonnes vides dans Excel][8]
  * [Diviser la feuille de calcul Excel par lignes et colonnes][9]

## API de visualisation de fichiers C# Excel — Téléchargement gratuit {#CSharp-Excel-File-Viewer-API-Free-Download}

Pour afficher les données des feuilles de calcul [XLS][10] ou [XLSX][11], nous utiliserons l'API [GroupDocs.Viewer for .NET][12]. Il permet le rendu et l'affichage des [formats de feuille de calcul pris en charge] [13] par programmation. Veuillez soit [télécharger][14] la DLL de l'API ou l'installer à l'aide de [NuGet][15].

```
PM> Install-Package GroupDocs.Viewer
```

## Afficher des données Excel en HTML à l'aide de C # {#Display-Excel-Data-in-HTML-using-CSharp}

Nous pouvons rendre le fichier Excel et afficher les données en HTML en suivant les étapes simples indiquées ci-dessous :

  1. Tout d'abord, chargez un fichier Excel à l'aide de la _**[Viewer][16]** _class.
  2. Créez une instance de la classe [_**HtmlViewOptions**_ ][17]pour [**_EmbeddedResources_**][18].
  3. Fournissez le chemin du fichier de sortie comme argument.
  4. Définissez éventuellement diverses options d'affichage, telles que _[RenderToSinglePage][19]_.
  5. Enfin, appelez la méthode _**[View()][20]**_ et passez _HtmlViewOptions_ comme argument.

L'exemple de code suivant montre **comment rendre un fichier Excel au format HTML à l'aide de C#**.

```
// Cet exemple de code montre comment afficher un fichier Excel en HTML.
// Charger le fichier Excel
Viewer viewer = new Viewer(@"C:\Files\Viewer\sample.xlsx");

// Définir les options d'affichage HTML
HtmlViewOptions viewOptions = HtmlViewOptions.ForEmbeddedResources(@"C:\Files\Viewer\sample_output.html");
viewOptions.RenderToSinglePage = true;

// Vue de rendu
viewer.View(viewOptions);
```

{{< figure align=center src="images/Display-Excel-Data-in-HTML-using-CSharp-1024x512.jpg" alt="Affichez les données Excel en HTML à l'aide de C#." caption="Affichez les données Excel en HTML à l'aide de C#.">}}
 

## Rendu des données Excel au format PDF à l'aide de C# {#Render-Excel-Data-in-PDF-using-CSharp}

Nous pouvons rendre le fichier Excel et afficher les données au format PDF en suivant les étapes ci-dessous:

  1. Tout d'abord, chargez un fichier Excel en utilisant la classe [Viewer](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer).
  2. Créez une instance de la classe [PdfViewOptions](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions).
  3. Fournissez le chemin du fichier de sortie comme argument.
  4. Enfin, appelez la méthode [View()](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view) et passez **PdfViewOptions** comme argument.

L'exemple de code suivant montre **comment rendre un fichier Excel au format PDF à l'aide de C#**.

```
// Cet exemple de code montre comment rendre un fichier Excel au format PDF.
// Charger le fichier Excel
Voirer viewer = new Voirer(@"C:\Files\Voirer\sample.xlsx");

// Définir les options d'affichage PDF
PdfVoirOptions viewOptions = new PdfVoirOptions(@"C:\Files\Voirer\sample_output.pdf");

// Voir
viewer.Voir(viewOptions);
```

{{< figure align=center src="images/Render-Excel-Data-in-PDF-using-CSharp-1024x512.jpg" alt="Rendu des données Excel au format PDF à l'aide de C#." caption="Rendu des données Excel au format PDF à l'aide de C#.">}}
 

## Afficher le fichier Excel en tant qu'image JPG à l'aide de C# {#View-Excel-File-as-JPG-Image-using-CSharp}

Nous pouvons rendre le fichier Excel et afficher les données sous forme d'images JPG en suivant les étapes ci-dessous :

  1. Tout d'abord, chargez un fichier Excel en utilisant la classe [Viewer](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer).
  2. Créez une instance de la classe [JpgViewOptions](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/jpgviewoptions).
  3. Indiquez le chemin du fichier de sortie.
  4. Enfin, appelez la méthode [View()](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view) et passez **JpgViewOptions** comme argument.

L'exemple de code suivant montre **comment rendre un fichier Excel au format JPG à l'aide de C#**.

```
// Cet exemple de code montre comment rendre un fichier Excel en image JPG.
// Charger le fichier Excel
Voirer viewer = new Voirer(@"C:\Files\Voirer\sample.xlsx");

// Définir les options d'affichage JPG
JpgVoirOptions viewOptions = new JpgVoirOptions(@"C:\Files\Voirer\sample_output.jpg");

// Voir
viewer.Voir(viewOptions);
```

{{< figure align=center src="images/View-Excel-File-as-JPG-Image-using-CSharp-1024x582.jpg" alt="Afficher le fichier Excel en tant qu'image JPG à l'aide de C#." caption="Afficher le fichier Excel en tant qu'image JPG à l'aide de C #.">}}
 

De même, nous pouvons également convertir un fichier Excel en images PNG comme indiqué ci-dessous :

```
// Cet exemple de code montre comment rendre un fichier Excel en image PNG.
// Charger le fichier Excel
Voirer viewer = new Voirer(@"C:\Files\Voirer\sample.xlsx");

// Définir les options d'affichage PNG
PngVoirOptions viewOptions = new PngVoirOptions(@"C:\Files\Voirer\sample_output.png");

// Voir
viewer.Voir(viewOptions);
```

## Ajuster le débordement de texte dans les cellules à l'aide de C# {#Adjust-Text-Overflow-in-Cells-using-CSharp}

Nous pouvons ajuster le débordement de texte dans les cellules lors du rendu d'une feuille de calcul Excel. L'API fournit les types d'ajustements de dépassement de capacité suivants :

  * _Overlay_ - Superposer les cellules suivantes même si elles ne sont pas vides.
  * _OverlayIfNextIsEmpty_ – Superposer les cellules suivantes uniquement si elles sont vides.
  * _AutoFitColumn_ – Développez les colonnes pour ajuster le texte.
  * _HideText_ – Masque le texte de débordement.

Veuillez suivre les étapes ci-dessous pour ajuster le dépassement de texte :

  1. Tout d'abord, chargez un fichier Excel à l'aide de la _**[Viewer][16]** _class.
  2. Créer une instance de [_**PdfViewOptions**_ ][24]classe
  3. Indiquez le chemin du fichier de sortie.
  4. Définissez la propriété TextOverflowMode de SpreadsheetOptions sur _HideText_.
  5. Définissez éventuellement RenderHeadings et RenderGridLines sur true.
  6. Enfin, appelez la méthode _**[View()][20]**_ et passez _PdfViewOptions_ comme argument.

L'exemple de code suivant montre **comment ajuster le dépassement de texte lors du rendu d'un fichier Excel à l'aide de C#**.

```
// Cet exemple de code montre comment ajuster le débordement de texte dans une cellule, rendre les en-têtes et les lignes de grille .
// Charger le fichier Excel
Voirer viewer = new Voirer(@"C:\Files\Voirer\sample.xlsx");

// Définir les options d'affichage PDF
PdfVoirOptions viewOptions = new PdfVoirOptions(@"C:\Files\Voirer\sample_overflow.pdf");

// Ajuster le débordement de texte
viewOptions.SpreadsheetOptions.TextOverflowMode = TextOverflowMode.HideText;

// Rendre les en-têtes Excel
viewOptions.SpreadsheetOptions.RenderHeadings = true;

// Rendre les lignes de la grille
viewOptions.SpreadsheetOptions.RenderGridLines = true;

// Voir
viewer.Voir(viewOptions);
```

{{< figure align=center src="images/Adjust-Text-Overflow-in-Cells-using-CSharp-1024x512.jpg" alt="Ajustez le débordement de texte dans les cellules à l'aide de C#." caption="Ajustez le débordement de texte dans les cellules à l'aide de C#.">}}
 

## Rendu des lignes et des colonnes masquées d'Excel {#Render-Hidden-Rows-and-Columns-of-Excel}

Nous pouvons rendre les lignes et les colonnes masquées d'une feuille de calcul Excel en suivant les étapes mentionnées précédemment. Cependant, il nous suffit de définir les propriétés suivantes sur true à l'étape 4 :

```
viewOptions.SpreadsheetOptions.RenderHiddenColumns = true;
viewOptions.SpreadsheetOptions.RenderHiddenRows = true;
```

L'exemple de code suivant montre **comment afficher les lignes et les colonnes masquées d'un fichier Excel au format PDF à l'aide de C#**.

```
// Cet exemple de code montre comment afficher les lignes et les colonnes masquées d'une feuille Excel.
// Charger le fichier Excel
Voirer viewer = new Voirer(@"C:\Files\Voirer\sample.xlsx");

// Définir les options d'affichage PDF
PdfVoirOptions viewOptions = new PdfVoirOptions(@"C:\Files\Voirer\hidden_rows_columns.pdf");
viewOptions.SpreadsheetOptions.RenderHiddenColumns = true;
viewOptions.SpreadsheetOptions.RenderHiddenRows = true;

// Voir
viewer.Voir(viewOptions);
```

{{< figure align=center src="images/Render-Hidden-Rows-and-Columns-of-Excel-1024x512.jpg" alt="Rendu des lignes et des colonnes masquées d'Excel." caption="Rendu des lignes et des colonnes masquées d'Excel.">}}
 

## Ignorer les lignes et les colonnes vides dans Excel à l'aide de C # {#Skip-Empty-Rows-and-Columns-in-Excel-using-CSharp}

Nous pouvons ignorer le rendu des lignes et des colonnes vides lors de l'affichage de la feuille de calcul Excel en suivant les étapes mentionnées précédemment. Cependant, il nous suffit de définir les propriétés suivantes sur true à l'étape 4 :

```
viewOptions.SpreadsheetOptions.SkipEmptyColumns = true;
viewOptions.SpreadsheetOptions.SkipEmptyRows = true;
```

L'exemple de code suivant montre **comment ignorer le rendu des lignes et des colonnes vides d'un fichier Excel à l'aide de C#**.

```
// Cet exemple de code montre comment ignorer le rendu des lignes et des colonnes masquées de la feuille Excel.
// Charger le fichier Excel
Voirer viewer = new Voirer(@"C:\Files\Voirer\sample.xlsx");

// Définir les options d'affichage PDF
PdfVoirOptions viewOptions = new PdfVoirOptions(@"C:\Files\Voirer\skip_empty.pdf");
viewOptions.SpreadsheetOptions.SkipEmptyColumns = true;
viewOptions.SpreadsheetOptions.SkipEmptyRows = true;

// Voir
viewer.Voir(viewOptions);
```

{{< figure align=center src="images/Skip-Empty-Rows-and-Columns-in-Excel-using-CSharp-1024x512.jpg" alt="Ignorer les lignes et les colonnes vides dans Excel à l'aide de C #" caption="Ignorer les lignes et les colonnes vides dans Excel à l'aide de C#.">}}
 

## Diviser la feuille de calcul Excel par lignes et colonnes {#Split-Excel-Worksheet-by-Rows-and-Columns}

Nous pouvons rendre de grandes feuilles de calcul Excel et les diviser par le nombre de lignes et de colonnes sur une page. Nous pouvons diviser la feuille de calcul en suivant les étapes ci-dessous :

  1. Tout d'abord, chargez un fichier Excel à l'aide de la _**[Viewer][16]** _class.
  2. Créer une instance de [_**PdfViewOptions**_ ][24]classe
  3. Indiquez le chemin du fichier de sortie.
  4. Initialisez _SpreadsheetOptions_ à l'aide de la méthode _ForSplitSheetIntoPages_. Il prend le nombre de lignes et de colonnes par page comme arguments.
  5. Enfin, appelez la méthode _**[View()][20]**_ et passez _PdfViewOptions_ comme argument.

L'exemple de code suivant montre **comment diviser une feuille de calcul Excel en lignes et en colonnes à l'aide de C#**.

```
// Cet exemple de code montre comment diviser une feuille Excel en lignes et en colonnes.
// Charger le fichier Excel
Viewer viewer = new Viewer(@"C:\Files\Viewer\sample.xlsx");

int countRowsPerPage = 25;
int countColumnsPerPage = 5;

PdfViewOptions viewOptions = new PdfViewOptions(@"C:\Files\Viewer\sample_split.pdf");
viewOptions.SpreadsheetOptions = SpreadsheetOptions.ForSplitSheetIntoPages(countRowsPerPage, countColumnsPerPage);

viewer.View(viewOptions);
```

{{< figure align=center src="images/Split-Excel-Worksheet-by-Rows-and-Columns-1024x603.jpg" alt="Diviser la feuille de calcul Excel par lignes et colonnes" caption="Fractionner la feuille de calcul Excel par lignes et colonnes.">}}
 

## Obtenez une licence gratuite

Veuillez essayer l'API sans limitation d'évaluation en demandant [une licence temporaire gratuite][29].

## Conclusion

Dans cet article, nous avons appris à :

  * rendre ou afficher des feuilles de calcul Excel au format HTML, PDF, PNG et JPG à l'aide de C# ;
  * ajuster le débordement de texte dans les cellules d'Excel et rendre les lignes de grille ;
  * afficher les en-têtes des colonnes et des lignes Excel ;
  * ignorer les lignes/colonnes vides et afficher les lignes et colonnes masquées ;
  * limiter l'affichage des feuilles de calcul par lignes et colonnes.

En outre, vous pouvez en savoir plus sur l'API GroupDocs.Viewer pour .NET à l'aide de la [documentation][30]. En cas d'ambiguïté, n'hésitez pas à nous contacter sur le [forum][31].

## Voir également

  * [Insérer ou supprimer des lignes et des colonnes dans Excel à l'aide de C #][32]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/excel-file-viewer-display-excel-data-using-csharp.jpg
 [2]: #CSharp-Excel-File-Viewer-API-Free-Download
 [3]: #Display-Excel-Data-in-HTML-using-CSharp
 [4]: #Render-Excel-Data-in-PDF-using-CSharp
 [5]: #View-Excel-File-as-JPG-Image-using-CSharp
 [6]: #Adjust-Text-Overflow-in-Cells-using-CSharp
 [7]: #Render-Hidden-Rows-and-Columns-of-Excel
 [8]: #Skip-Empty-Rows-and-Columns-in-Excel-using-CSharp
 [9]: #Split-Excel-Worksheet-by-Rows-and-Columns
 [10]: https://docs.fileformat.com/spreadsheet/xls/
 [11]: https://docs.fileformat.com/spreadsheet/xlsx/
 [12]: https://products.groupdocs.com/viewer/net
 [13]: https://docs.groupdocs.com/viewer/net/view-excel-spreadsheets/#supported-spreadsheets-formats
 [14]: https://downloads.groupdocs.com/viewer/net
 [15]: https://www.nuget.org/packages/groupdocs.viewer
 [16]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
 [17]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
 [18]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options.htmlviewoptions/forembeddedresources/methods/4
 [19]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions/properties/rendertosinglepage
 [20]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
 [21]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Display-Excel-Data-in-HTML-using-CSharp.jpg
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Render-Excel-Data-in-PDF-using-CSharp.jpg
 [23]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/View-Excel-File-as-JPG-Image-using-CSharp.jpg
 [24]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
 [25]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Adjust-Text-Overflow-in-Cells-using-CSharp.jpg
 [26]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Render-Hidden-Rows-and-Columns-of-Excel.jpg
 [27]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Skip-Empty-Rows-and-Columns-in-Excel-using-CSharp.jpg
 [28]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Split-Excel-Worksheet-by-Rows-and-Columns.jpg
 [29]: https://purchase.conholdate.com/temporary-license
 [30]: https://docs.groupdocs.com/viewer/net/
 [31]: https://forum.groupdocs.com/c/viewer/9
 [32]: https://blog.conholdate.com/2021/10/06/insert-or-delete-rows-and-columns-in-excel-using-csharp/



