---
title: Convertir des graphiques Excel en SVG à l'aide de Java
author: Muzammil Khan
date: 2022-01-11T05:11:47+00:00
summary: "En tant que développeur Java, vous pouvez facilement convertir par programme des tableaux de données de classeurs Excel en fichiers SVG. Dans cet article, vous apprendrez **à convertir des graphiques Excel en SVG à l'aide de Java**."
url: /fr/2022/01/11/convert-excel-charts-to-svg-using-java/
categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "Aspose.Cells pour Java"
  - "Convertir des graphiques en SVG en Java"
  - "Convertir des graphiques Excel en SVG"
  - "Convertir des graphiques Excel en SVG in Java"
  - "Exporter des graphiques vers SVG en Java"
  - "API Java pour convertir des graphiques Excel"

---


{{< figure align=center src="images/convert-excel-charts-to-svg-using-java.jpg" alt="Convertir des graphiques Excel en SVG à l'aide de Java">}}
 
[SVG (_Scalable Vector Graphics_)][2] est un format d'image vectorielle basé sur XML qui stocke une image dans un format graphique vectoriel bidimensionnel. Les images SVG peuvent également être modifiées avec n'importe quel éditeur de texte. Nous pouvons convertir par programme des tableaux de données de classeurs Excel en fichiers SVG. Dans cet article, nous allons apprendre **comment convertir des graphiques Excel en SVG en utilisant Java**.

Les sujets suivants seront traités dans cet article:
  * [API Java pour convertir des graphiques Excel en SVG][3]
  * [Convertir des graphiques Excel en SVG en Java][4]
  * [Exporter le graphique et l'échelle SVG pour ajuster la fenêtre][5] 

## API Java pour convertir des graphiques Excel en SVG {#Java-API-to-Convert-Excel-Charts-to-SVG}

Pour convertir les graphiques des fichiers [XLSX][6] en SVG, nous utiliserons l'API [Aspose.Cells for Java][7]. Il permet d'exécuter des fonctionnalités d'automatisation Excel par programmation sans avoir besoin d'une application Microsoft Excel. Veuillez soit [télécharger][8] le JAR de l'API ou simplement ajouter la configuration **_pom.xml_** suivante dans une application Java basée sur Maven.

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
    <artifactId>aspose-cells</artifactId>
    <version>21.12</version>
</dependency>
```

## Convertir des graphiques Excel en SVG en Java {#Convert-Excel-Charts-to-SVG-in-Java}

Nous pouvons convertir des graphiques de feuilles de calcul Excel en SVG en suivant les étapes ci-dessous:
  1. Tout d'abord, chargez un fichier Excel à l'aide de la classe [**_Workbook_**][9].
  2. Ensuite, accédez à la feuille de calcul contenant un graphique à convertir à partir de la collection de feuilles de calcul, soit par son index (basé sur zéro), soit par son nom.
  3. Ensuite, accédez au graphique à convertir par son index (basé sur zéro) à partir de la collection de graphiques.
  4. Après cela, définissez **_ImageOrPrintOptions.setSaveFormat_** sur SVG.
  5. Enfin, convertissez le graphique en SVG à l'aide de la méthode [**_Chart.toImage()_**][10] et enregistrez le fichier de sortie.

L'exemple de code suivant montre **comment convertir un graphique d'Excel en SVG à l'aide de Java**.

```
// Cet exemple de code montre comment convertir un graphique d'Excel en SVG
// Charger le fichier Excel dans l'objet classeur
Workbook workbook = new Workbook("C:\\Files\\Cells\\Sample_Chart.xlsx");

// Accéder à la première feuille de calcul
Worksheet worksheet = workbook.getWorksheets().get(0);

// Accéder au premier graphique à l'intérieur de la feuille de calcul
Chart chart = worksheet.getCharts().get(0);

// Enregistrez le graphique dans l'image au format SVG
ImageOrPrintOptions options = new ImageOrPrintOptions();
options.setSaveFormat(SaveFormat.SVG);

chart.toImage("C:\\Files\\Cells\\Sample_Chart_out.svg", options);
```

{{< figure align=center src="images/Convert-Excel-Charts-to-SVG-in-Java-1024x576.jpg" alt="Convertir des graphiques Excel en SVG en Java" caption="Convertissez des graphiques Excel en SVG en Java.">}}
 
## Exporter le graphique et l'échelle SVG pour ajuster la fenêtre en Java {#Export-Chart-and-Scale-SVG-to-Fit-Viewport-in-Java}

En XML, l'attribut **viewBox** définit la position et la dimension du contenu de la fenêtre SVG. Nous pouvons exporter n'importe quel graphique à partir de feuilles de calcul Excel vers SVG et le configurer pour qu'il tienne dans la fenêtre d'affichage en suivant les étapes ci-dessous:
  1. Tout d'abord, chargez un fichier Excel à l'aide de la classe [**_Workbook_**][9].
  2. Ensuite, accédez à la feuille de calcul contenant un graphique à convertir à partir de la collection de feuilles de calcul, soit par son index (basé sur zéro), soit par son nom.
  3. Ensuite, accédez au graphique à exporter par son index (basé sur zéro) à partir de la collection de graphiques.
  4. Définissez **_ImageOrPrintOptions.setSaveFormat_** sur SVG.
  5. Après cela, définissez **_ImageOrPrintOptions.setSVGFitToViewPort_** sur true.
  6. Enfin, appelez la méthode [**_Chart.toImage()_**][10] pour enregistrer le fichier de sortie.

L'exemple de code suivant montre **comment exporter un graphique d'Excel vers SVG pour tenir dans la fenêtre d'affichage à l'aide de Java**.

```
// Cet exemple de code montre comment convertir un graphique d'Excel en SVG et le configurer pour qu'il tienne dans la fenêtre d'affichage
// Charger le fichier Excel dans l'objet classeur
Workbook workbook = new Workbook("C:\\Files\\Cells\\Sample_Chart.xlsx");

// Accéder à la première feuille de calcul
Worksheet worksheet = workbook.getWorksheets().get(0);

// Accéder au premier graphique à l'intérieur de la feuille de calcul
Chart chart = worksheet.getCharts().get(0);

// Définir les options d'image ou d'impression
// avec SVGFitToViewPort vrai
ImageOrPrintOptions options = new ImageOrPrintOptions();
options.setSaveFormat(SaveFormat.SVG);
options.setSVGFitToViewPort(true);

chart.toImage("C:\\Files\\Cells\\Sample_Chart_ViewPort_out.svg", options);
```

{{< figure align=center src="images/Export-Chart-and-Scale-SVG-to-Fit-Viewport-in-Java-1024x512.jpg" alt="Exporter le graphique et l'échelle SVG pour ajuster la fenêtre en Java" caption="Exportez le graphique et l'échelle SVG pour adapter la fenêtre d'affichage en Java.">}}
 
## Obtenez une licence gratuite

Veuillez essayer l'API sans limitation d'évaluation en demandant [une licence temporaire gratuite][13].

## Conclusion

Dans cet article, nous avons appris **comment convertir un graphique d'Excel en SVG en Java**. Nous avons également vu **comment exporter un graphique Excel vers SVG pour tenir dans la fenêtre d'affichage** par programmation. En outre, vous pouvez en savoir plus sur l'API Aspose.Cells for Java en utilisant la [documentation][14]. En cas d'ambiguïté, n'hésitez pas à nous contacter sur le [forum][15].

## Voir également

  * [Exporter des données vers Excel en Java][16]
  * [Supprimer les lignes et les colonnes vides dans Excel à l'aide de Java][17]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/convert-excel-charts-to-svg-using-java.jpg
 [2]: https://docs.fileformat.com/page-description-language/svg/
 [3]: #Java-API-to-Convert-Excel-Charts-to-SVG
 [4]: #Convert-Excel-Charts-to-SVG-in-Java
 [5]: #Export-Chart-and-Scale-SVG-to-Fit-Viewport-in-Java
 [6]: https://docs.fileformat.com/spreadsheet/xlsx/
 [7]: https://products.aspose.com/cells/java/
 [8]: https://downloads.aspose.com/cells/java
 [9]: https://apireference.aspose.com/cells/java/com.aspose.cells/workbook
 [10]: https://apireference.aspose.com/cells/java/com.aspose.cells/chart#toImage(java.lang.String,%20com.aspose.cells.ImageOrPrintOptions)
 [11]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/Convert-Excel-Charts-to-SVG-in-Java.jpg
 [12]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/Export-Chart-and-Scale-SVG-to-Fit-Viewport-in-Java.jpg
 [13]: https://purchase.conholdate.com/temporary-license
 [14]: https://docs.aspose.com/cells/java/
 [15]: https://forum.aspose.com/c/cells/9
 [16]: https://blog.conholdate.com/2021/08/27/export-data-to-excel-in-java/
 [17]: https://blog.conholdate.com/2021/11/23/delete-blank-rows-and-columns-in-excel-using-java/








