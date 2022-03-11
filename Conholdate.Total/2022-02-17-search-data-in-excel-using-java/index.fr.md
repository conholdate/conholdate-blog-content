---
title: Rechercher des données dans Excel à l'aide de Java
author: Muzammil Khan
date: 2022-02-17T07:34:30+00:00
summary: "Vous pouvez facilement rechercher par programmation des cellules contenant des valeurs de données ou des chaînes spécifiques dans des feuilles de calcul Excel dans des applications Java. Dans cet article, vous apprendrez **à rechercher des données dans Excel à l'aide de Java**."
url: /fr/2022/02/17/search-data-in-excel-using-java/
categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "API pour la recherche de texte"
  - "Recherche sensible à la casse"
  - "Trouver une formule dans Excel en utilisant Java"
  - "Rechercher du texte"
  - "Rechercher du texte in Excel using Java"
  - "Rechercher des cellules"
  - "Formule de recherche dans Excel"
  - "Rechercher du texte dans Excel"

---

{{< figure align=center src="images/search-data-in-excel-using-java.jpg" alt="Rechercher des données dans Excel à l'aide de Java">}}
 
Les feuilles de calcul Excel permettent de stocker une énorme quantité de données sous forme de tableau. Dans certains cas, nous pouvons avoir besoin de rechercher des cellules contenant des valeurs de données spécifiques ou des chaînes de données stockées. Bien qu'Excel fournisse une fonctionnalité intégrée pour rechercher dans toutes les feuilles de calcul, nous devrons peut-être effectuer l'opération de recherche par programme dans les applications Java. Dans cet article, nous allons apprendre **comment rechercher des données dans Excel à l'aide de Java**.

Les sujets suivants seront traités dans cet article:
  * [API Java pour rechercher des données dans Excel][2]
  * [Rechercher un texte spécifique dans Excel à l'aide de Java][3]
  * [Rechercher du texte commençant par des lettres spécifiques][4]
  * [Rechercher un texte se terminant par des lettres spécifiques][5]
  * [Rechercher du texte contenant des lettres spécifiques][6]
  * [Rechercher avec une expression régulière dans Excel à l'aide de Java][7]
  * [Recherche sensible à la casse dans Excel avec Java][8]
  * [Formule de recherche dans Excel à l'aide de Java][9]

## Java API to Search Data in Excel

Nous utiliserons l'API [Aspose.Cells for Java][10] pour effectuer une opération de recherche sur le fichier [XLSX][11]. Il permet d'exécuter des fonctionnalités d'automatisation Excel par programmation sans avoir besoin d'une application Microsoft Excel. Veuillez soit [télécharger][12] le JAR de l'API ou simplement ajouter la configuration **_pom.xml_** suivante dans une application Java basée sur Maven.

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
    <version>22.1</version>
</dependency>
```

## Rechercher un texte spécifique dans Excel à l'aide de Java {#Find-Specific-Text-in-Excel-using-Java}

Nous pouvons rechercher n'importe quelle valeur de texte, de nombre ou de date dans un fichier Excel en suivant les étapes ci-dessous:
  * Tout d'abord, chargez un fichier Excel à l'aide de la classe [**_Workbook_**][13].
  * Ensuite, accédez à la première [feuille de calcul][14] dans le fichier Excel.
  * Ensuite, obtenez [cellules][15] de la feuille consultée.
  * Ensuite, créez une instance de la classe **_[FindOptions][16]_**.
  * Après cela, définissez **_[LookAtType][17]_** sur "_ENTIRE_CONTENT_".
  * Enfin, recherchez le texte à l'aide de la méthode **_[Cells.find()][18]_**. Il prend la chaîne de recherche et **_FindOptions_** comme arguments.

L'exemple de code suivant montre **comment rechercher un texte spécifique dans un fichier Excel à l'aide de Java.**

```
// Charger un fichier Excel
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// Accéder à la première feuille de calcul du fichier Excel
Worksheet worksheet = workbook.getWorksheets().get(0);

// Obtenir toutes les cellules dans CellCollections
Cells cells = worksheet.getCells();

// Initialiser FindOptions
FindOptions findOptions = new FindOptions();

// Trouver la cellule contenant une valeur de chaîne
findOptions.setLookAtType(LookAtType.ENTIRE_CONTENT);
Cell cell = cells.find("A Company", null, findOptions);

// Afficher le nom de la cellule et sa valeur
System.out.println("Name of the cell containing String: " + cell.getName());
System.out.println("the cell value is: " + cell.getValue());
```

{{< figure align=center src="images/Find-Specific-Text-in-Excel-using-Java-1024x455.jpg" alt="Rechercher un texte spécifique dans Excel à l'aide de Java" caption="Rechercher un texte spécifique dans Excel à l'aide de Java.">}}
 

## Rechercher du texte commençant par des lettres spécifiques {#Find-Text-Starting-with-Specific-Letters}

Nous pouvons rechercher n'importe quelle valeur de texte commençant par des lettres spécifiques en suivant les étapes mentionnées ci-dessus. Cependant, nous devons simplement définir **_LookAtType_** sur "_START_WITH_".

L'exemple de code suivant montre comment rechercher un texte spécifique commençant par la lettre "H" dans un fichier Excel à l'aide de Java.

```
// Charger un fichier Excel
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// Accéder à la première feuille de calcul du fichier Excel
Worksheet worksheet = workbook.getWorksheets().get(0);

// Obtenir toutes les cellules dans CellCollections
Cells cells = worksheet.getCells();

// Initialiser FindOptions
FindOptions findOptions = new FindOptions();

// Trouver la cellule contenant une valeur de chaîne
findOptions.setLookAtType(LookAtType.START_WITH);
Cell cell = cells.find("H", null, findOptions);

// Afficher le nom de la cellule et sa valeur
System.out.println("Name of the cell containing String: " + cell.getName());
System.out.println("the cell value is: " + cell.getValue());
```

{{< figure align=center src="images/Find-Text-Starting-with-Specific-Letters-1024x463.jpg" alt="" légende="Find Text Starting with Specific Letters.">}}
 

## Rechercher un texte se terminant par des lettres spécifiques {#Search-Text-Ending-with-Specific-Letters}

Nous pouvons rechercher n'importe quelle valeur de texte qui se termine par des lettres spécifiques en suivant les étapes mentionnées ci-dessus. Cependant, nous devons simplement définir **_LookAtType_** sur "_END_WITH_".

L'exemple de code suivant montre comment rechercher un texte spécifique qui se termine par les lettres "any" dans un fichier Excel à l'aide de Java.

```
// Charger un fichier Excel
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// Accéder à la première feuille de calcul du fichier Excel
Worksheet worksheet = workbook.getWorksheets().get(0);

// Obtenir toutes les cellules dans CellCollections
Cells cells = worksheet.getCells();

// Initialiser FindOptions
FindOptions findOptions = new FindOptions();

// Trouver la cellule contenant une valeur de chaîne
findOptions.setLookAtType(LookAtType.ENDS_WITH);
Cell cell = cells.find("any", null, findOptions);

// Afficher le nom de la cellule et sa valeur
System.out.println("Name of the cell containing String: " + cell.getName());
System.out.println("the cell value is: " + cell.getValue());
```

## Rechercher du texte contenant des lettres spécifiques {#Find-Text-Containing-Specific-Letters}

Nous pouvons rechercher n'importe quelle valeur de texte contenant une sous-chaîne spécifique en suivant les étapes mentionnées ci-dessus. Cependant, nous avons juste besoin de définir **_LookAtType_** comme "_CONTAINS_".

L'exemple de code suivant montre comment rechercher un texte contenant "comp" dans un fichier Excel à l'aide de Java.

```
// Charger un fichier Excel
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// Accéder à la première feuille de calcul du fichier Excel
Worksheet worksheet = workbook.getWorksheets().get(0);

// Obtenir toutes les cellules dans CellCollections
Cells cells = worksheet.getCells();

// Initialiser FindOptions
FindOptions findOptions = new FindOptions();

// Trouver la cellule contenant une valeur de chaîne
findOptions.setLookAtType(LookAtType.CONTAINS);
Cell cell = cells.find("comp", null, findOptions);

// Afficher le nom de la cellule et sa valeur
System.out.println("Name of the cell containing String: " + cell.getName());
System.out.println("the cell value is: " + cell.getValue());
```

## Rechercher avec une expression régulière dans Excel à l'aide de Java {#Search-with-Regular-Expression-in-Excel-using-Java}

Nous pouvons également rechercher une valeur de cellule à l'aide d'expressions régulières en suivant les étapes mentionnées ci-dessus. Cependant, nous avons juste besoin de définir la **_Regex Key_** sur true et le **_LookAtType_** sur "_CONTAINS_".

L'exemple de code suivant montre **comment rechercher du texte à l'aide d'une expression régulière dans un fichier Excel à l'aide de Java**.

```
// Charger un fichier Excel
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// Accéder à la première feuille de calcul du fichier Excel
Worksheet worksheet = workbook.getWorksheets().get(0);

// Obtenir toutes les cellules dans CellCollections
Cells cells = worksheet.getCells();

// Initialiser FindOptions
FindOptions findOptions = new FindOptions();

// Définissez-le comme Regex
findOptions.setRegexKey(true);
findOptions.setLookAtType(LookAtType.ENTIRE_CONTENT);
findOptions.setLookInType(LookInType.VALUES);
Cell cell = cells.find("[a-z]{1}[\\s]&[\\s][a-z]{1}", null, opt);

// Afficher le nom de la cellule et sa valeur
System.out.println("Name of the cell containing String: " + cell.getName());
System.out.println("the cell value is: " + cell.getValue());
```

{{< figure align=center src="images/Search-with-Regular-Expression-in-Excel-using-Java-1024x465.jpg" alt="Rechercher avec une expression régulière dans Excel à l'aide de Java" caption="Rechercher avec une expression régulière dans Excel en utilisant Java.">}}
 
## Recherche sensible à la casse dans Excel avec Java {#Case-Sensitive-Search-in-Excel-using-Java}

Nous pouvons effectuer une opération de recherche et trouver toute chaîne de texte sensible à la casse en suivant les étapes mentionnées ci-dessus. Cependant, il nous suffit de définir la propriété **_CaseSensitive_** sur true.

L'exemple de code suivant montre **comment rechercher un texte sensible à la casse dans un fichier Excel à l'aide de Java**.

```
// Charger un fichier Excel
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// Accéder à la première feuille de calcul du fichier Excel
Worksheet worksheet = workbook.getWorksheets().get(0);

// Obtenir toutes les cellules dans CellCollections
Cells cells = worksheet.getCells();

// Initialiser FindOptions
FindOptions findOptions = new FindOptions();

// Trouver la cellule contenant une formule
findOptions.setCaseSensitive(true);
findOptions.setLookAtType(LookAtType.CONTAINS);
Cell cell = cells.find("Ltd", null, findOptions);

// Afficher le nom de la cellule et sa valeur
System.out.println("Name of the cell containing String: " + cell.getName());
System.out.println("the cell value is: " + cell.getValue());
```

## Formule de recherche dans Excel à l'aide de Java {#Search-Formula-in-Excel-using-Java}

Nous pouvons rechercher une cellule contenant une formule dans un fichier Excel en suivant les étapes ci-dessous:
  * Tout d'abord, chargez un fichier Excel à l'aide de la classe [**_Workbook_**][13].
  * Ensuite, accédez à la première feuille de calcul du fichier Excel.
  * Ensuite, récupérez les cellules de la feuille consultée.
  * Ensuite, créez une instance de la classe **_FindOptions_**.
  * Après cela, définissez **_[LookInType][22]_** sur "__FORMULAS__".
  * Enfin, recherchez le texte à l'aide de la méthode Cells.find(). Il prend la chaîne de recherche et **_FindOptions_** comme arguments.

L'exemple de code suivant montre **comment rechercher une cellule de formule dans un fichier Excel à l'aide de Java.**

```
// Charger un fichier Excel
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// Accéder à la première feuille de calcul du fichier Excel
Worksheet worksheet = workbook.getWorksheets().get(0);

// Obtenir toutes les cellules dans CellCollections
Cells cells = worksheet.getCells();

// Initialiser FindOptions
FindOptions findOptions = new FindOptions();

// Trouver la cellule contenant une formule
findOptions.setLookInType(LookInType.FORMULAS);
Cell cell = cells.find("=SUM(C2:C10)", null, findOptions);

// Afficher le nom de la cellule et sa valeur
System.out.println("Name of the cell containing String: " + cell.getName());
System.out.println("the cell value is: " + cell.getValue());
```

{{< figure align=center src="images/Search-Formula-in-Excel-using-Java-1024x453.jpg" alt="Formule de recherche dans Excel en utilisant Java." caption="Formule de recherche dans Excel en utilisant Java.">}}
 
## Obtenez une licence gratuite

Veuillez essayer l'API sans limitation d'évaluation en demandant [une licence temporaire gratuite][24].

## Conclusion

Dans cet article, nous avons appris **comment rechercher du texte ou des formules dans Excel à l'aide de Java**. Plus précisément, nous avons appris **comment rechercher n'importe quel texte dans Excel qui commence, se termine ou contient des lettres spécifiques** par programmation. Nous avons également vu **comment effectuer une recherche à l'aide d'expressions régulières** dans des fichiers Excel. En outre, vous pouvez en savoir plus sur l'API Aspose.Cells for Java en utilisant la [documentation][25]. En cas d'ambiguïté, n'hésitez pas à nous contacter sur le [forum][26].

## Voir également

  * [Rechercher et remplacer du texte dans Excel en Java][27]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/search-data-in-excel-using-java.jpg
 [2]: #
 [3]: #Find-Specific-Text-in-Excel-using-Java
 [4]: #Find-Text-Starting-with-Specific-Letters
 [5]: #Search-Text-Ending-with-Specific-Letters
 [6]: #Find-Text-Containing-Specific-Letters
 [7]: #Search-with-Regular-Expression-in-Excel-using-Java
 [8]: #Case-Sensitive-Search-in-Excel-using-Java
 [9]: #Search-Formula-in-Excel-using-Java
 [10]: https://products.aspose.com/cells/java/
 [11]: https://docs.fileformat.com/spreadsheet/xlsx/
 [12]: https://downloads.aspose.com/cells/java
 [13]: https://apireference.aspose.com/cells/java/com.aspose.cells/workbook
 [14]: https://apireference.aspose.com/cells/java/com.aspose.cells/Worksheet
 [15]: https://apireference.aspose.com/cells/java/com.aspose.cells/Cells
 [16]: https://apireference.aspose.com/cells/java/com.aspose.cells/FindOptions
 [17]: https://apireference.aspose.com/cells/java/com.aspose.cells/LookAtType
 [18]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#find(java.lang.Object,%20com.aspose.cells.Cell,%20com.aspose.cells.FindOptions)
 [19]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Find-Specific-Text-in-Excel-using-Java.jpg
 [20]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Find-Text-Starting-with-Specific-Letters.jpg
 [21]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Search-with-Regular-Expression-in-Excel-using-Java.jpg
 [22]: https://apireference.aspose.com/cells/java/com.aspose.cells/LookInType
 [23]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Search-Formula-in-Excel-using-Java.jpg
 [24]: https://purchase.conholdate.com/temporary-license
 [25]: https://docs.aspose.com/cells/java/
 [26]: https://forum.aspose.com/c/cells/9
 [27]: https://blog.aspose.com/2020/12/08/find-and-replace-text-in-spreadsheets-using-java/








