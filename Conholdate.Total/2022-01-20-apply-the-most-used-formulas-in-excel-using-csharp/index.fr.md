---
title: "Appliquer les formules les plus utilisées dans Excel à l'aide de C#"
author: Muzammil Khan
date: 2022-01-20T10:41:26+00:00
summary: "En tant que développeur C#, vous pouvez facilement exécuter par programme des formules prises en charge par Excel dans des feuilles Excel. Dans cet article, vous apprendrez **à appliquer les formules les plus utilisées dans Excel à l'aide de C#** ."
url: /fr/2022/01/20/appliquer-les-formules-les-plus-utilisees-dans-excel-en-utilisant-csharp/
categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "Calculer des formules Excel"
  - "Formules Excel"
  - "Formules Excel en C#"
  - "Calcul de formule"
  - "Formules dans Excel en C#"
  - "Formules les plus utilisées dans Excel"
  - "Formule de pourcentage en C #"

---

{{< figure align=center src="images/most-used-formulas-in-excel-using-csharp.jpg" alt="Formules les plus utilisées dans Excel avec C#">}}
 
Excel est l'une des applications de tableur les plus populaires et les plus utilisées. Il fournit une fonctionnalité intégrée pour appliquer diverses formules/fonctions pour traiter les données. Ces formules permettent d'effectuer différents types de calculs ou calculs. Une formule est une expression qui calcule la valeur d'une cellule. Excel fournit également des fonctions qui sont des formules prédéfinies, qui sont facilement utilisables. Dans cet article, nous allons apprendre **comment appliquer les formules les plus utilisées dans Excel en utilisant C#**.

Les sujets suivants seront traités dans cet article:
  * [API C# pour exécuter les formules les plus utilisées dans Excel][2]
  * [Compter les cellules dans Excel à l'aide de C #][3]
  * [Fonction SUM dans Excel avec C#][4]
  * [Calculer la moyenne dans Excel en utilisant C#][5]
  * [Fonction SI dans Excel avec C#][6]
  * [Formule de pourcentage dans Excel en utilisant C#][7]

## API C # pour exécuter les formules les plus utilisées dans Excel {#CSharp-API-to-Execute-Most-Used-Formulas-in-Excel}

Nous utiliserons l'API [Aspose.Cells for .NET][8] pour utiliser les formules dans les fichiers [XLSX][9]. Il prend en charge un vaste ensemble de [formules] mathématiques, de chaîne, booléennes, de date/heure, statistiques, de base de données, de recherche et de référence [10]. Veuillez soit [télécharger][11] la DLL de l'API ou l'installer à l'aide de [NuGet][12].

```
PM> Install-Package Aspose.Cells
```

## Compter les cellules dans Excel à l'aide de C # {#Count-Cells-in-Excel-using-CSharp}

La fonction COUNT compte le nombre de cellules dans une plage fournie qui contient des nombres. Nous pouvons utiliser la formule de comptage par programmation en suivant les étapes ci-dessous:
  1. Tout d'abord, chargez un fichier Excel à l'aide de la classe [Workbook][13].
  2. Ensuite, accédez à la [feuille de calcul][14], soit par son index (basé sur zéro), soit par son nom.
  3. Ensuite, définissez la [formule][15] pour une [cellule][16] accessible par son nom.
  4. Après cela, appelez la fonction [CalculateFormula()][17] pour calculer les résultats de la formule.
  5. Enfin, enregistrez le fichier Excel en utilisant la méthode [Save()][18]. Il prend le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment exécuter la formule COUNT** **dans Excel à l'aide de C#**.

```
// Cet exemple de code montre comment utiliser la fonction COUNT dans Excel.
// Charger un fichier Excel existant
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// Accéder à la feuille de calcul en passant son index de feuille
Worksheet worksheet = workbook.Worksheets[0];

// Ajouter une formule à la cellule
worksheet.Cells["B12"].Formula = "=COUNT(B1:B11)";

// Calcul des résultats de formules
workbook.CalculateFormula();

// Enregistrez le fichier Excel
workbook.Save("C:\\Files\\Cells\\output_Count.xlsx");
```

{{< figure align=center src="images/Count-Cells-in-Excel-using-CSharp-1024x618.jpg" alt="Comptez les cellules dans Excel en utilisant C #." caption="Comptez les cellules dans Excel en utilisant C#.">}}
 
De même, nous pouvons utiliser la fonction NBVAL pour compter toutes les cellules qui ne sont pas vides. Dans ce cas, la fonction NBVAL renvoie 10.

## Fonction SUM dans Excel avec C# {#SUM-Function-in-Excel-using-CSharp}

La fonction SUM dans Excel additionne toutes les valeurs dans une plage donnée. Veuillez suivre les étapes mentionnées précédemment pour calculer la sum des valeurs. Cependant, nous avons juste besoin de définir la formule sum à l'étape 3.
L'exemple de code suivant montre **comment appliquer la formule SUM dans Excel à l'aide de C#**.

```
// Cet exemple de code montre comment utiliser la fonction SUM dans Excel.
// Charger un fichier Excel existant
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// Accéder à la feuille de calcul en passant son index de feuille
Worksheet worksheet = workbook.Worksheets[0];

// Ajouter une formule à la cellule
worksheet.Cells["B12"].Formula = "=SUM(B2:B11)";

// Calcul des résultats de formules
workbook.CalculateFormula();

// Enregistrez le fichier Excel
workbook.Save("C:\\Files\\Cells\\output_sum.xlsx");
```

{{< figure align=center src="images/SUM-Function-in-Excel-using-CSharp-1024x674.jpg" alt="Fonction SUM dans Excel en utilisant C #." caption="Fonction SUM dans Excel en utilisant C#.">}}
 
## Calculer la moyenne dans Excel en utilisant C# {#Calculate-Average-in-Excel-using-CSharp}

Nous pouvons calculer la moyenne de la plage de valeurs fournie dans Excel à l'aide de la fonction MOYENNE. Veuillez suivre les étapes mentionnées précédemment pour calculer la moyenne des valeurs données. Cependant, nous avons juste besoin de définir la formule MOYENNE à l'étape 3.
L'exemple de code suivant montre **comment calculer la moyenne dans Excel à l'aide de C#**.

```
// Cet exemple de code montre comment utiliser la fonction MOYENNE dans Excel.
// Charger un fichier Excel existant
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// Accéder à la feuille de calcul en passant son index de feuille
Worksheet worksheet = workbook.Worksheets[0];

// Ajouter une formule à la cellule
worksheet.Cells["B12"].Formula = "=AVERAGE(B2:B11)";

// Calcul des résultats de formules
workbook.CalculateFormula();

// Enregistrez le fichier Excel
workbook.Save("C:\\Files\\Cells\\output_average.xlsx");
```

{{< figure align=center src="images/Calculate-Average-in-Excel-using-CSharp-1024x654.jpg" alt="Calculez la moyenne dans Excel en utilisant C#." caption="Calculez la moyenne dans Excel à l'aide de C#.">}}
 
## Fonction SI dans Excel avec C# {#IF-Function-in-Excel-using-CSharp}

Nous pouvons appliquer la fonction SI dans Excel par programmation pour vérifier si une condition est remplie ou non. Il renvoie une valeur si vrai et une autre valeur si faux. Veuillez suivre les étapes mentionnées précédemment pour utiliser la fonction SI. Cependant, nous avons juste besoin de définir la condition IF à l'étape 3.
L'exemple de code suivant montre **comment appliquer la fonction SI dans Excel à l'aide de C#**.

```
// Cet exemple de code montre comment utiliser la fonction SI dans Excel.
// Charger un fichier Excel existant
Workbook workbook = new Workbook("C:\\Files\\Cells\\sample.xlsx");

// Accéder à la feuille de calcul en passant son index de feuille
Worksheet worksheet = workbook.Worksheets[0];

// Ajout d'une formule SUM à la cellule "A4"
worksheet.Cells["C2"].Formula = "=IF(B2>=A2,\"Target Acheived\",\"Not Acheived\")";

// Calcul des résultats de formules
workbook.CalculateFormula();

// Enregistrez le fichier Excel
workbook.Save("C:\\Files\\Cells\\output_if.xlsx");
```

{{< figure align=center src="images/IF-Function-in-Excel-using-CSharp.jpg" alt="Fonction SI dans Excel avec C#." caption="Fonction SI dans Excel avec C#.">}}

## Formule de pourcentage dans Excel en utilisant C# {#Percentage-Formula-in-Excel-using-CSharp}

Nous pouvons également appliquer la formule de pourcentage dans Excel en utilisant la formule de pourcentage de base, par exemple **"(partie/total) * 100"**. Veuillez suivre les étapes mentionnées ci-dessous pour calculer le pourcentage dans Excel.
  1. Tout d'abord, créez une instance de la classe [Workbook][13].
  2. Ensuite, ajoutez une nouvelle [Feuille de travail][14] au nouveau classeur créé.
  3. Ensuite, accédez à la feuille de travail ajoutée soit par son index (basé sur zéro), soit par son nom.
  4. Ensuite, ajoutez des valeurs aux [Cellules][23] requises à l'aide de la fonction [PutValue][24].
  5. Ensuite, définissez le pourcentage [formule][15] pour une cellule accessible par son nom.
  6. Après cela, appelez la fonction [CalculateFormula()][17] pour calculer les résultats de la formule.
  7. Enfin, enregistrez le fichier Excel en utilisant la méthode [Save()][18]. Il prend le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment appliquer la formule de pourcentage** **dans Excel à l'aide de C#**.

```
// Cet exemple de code montre comment calculer le pourcentage dans Excel.
// Instanciation d'un objet Workbook
Workbook workbook = new Workbook();

// Ajout d'une nouvelle feuille de calcul à l'objet Excel
int sheetIndex = workbook.Worksheets.Add();

// Obtenir la référence de la feuille de calcul nouvellement ajoutée en passant son index de feuille
Worksheet worksheet = workbook.Worksheets[0];

// Ajouter une valeur à la cellule "A1"
worksheet.Cells["A1"].PutValue(35000);

// Ajouter une valeur à la cellule "B1"
worksheet.Cells["B1"].PutValue(39000);

// Ajout d'une formule de pourcentage à la cellule "C1"
worksheet.Cells["C1"].Formula = "=((B1-A1)/A1)*100";

// Calcul des résultats de formules
workbook.CalculateFormula();

// Enregistrement du fichier Excel
workbook.Save("C:\\Files\\Cells\\output_percentage.xlsx");
```

{{< figure align=center src="images/Percentage-Formula-in-Excel-using-CSharp.jpg" alt="Formule de pourcentage dans Excel en utilisant C#" caption="Formule de pourcentage dans Excel en utilisant C #.">}}
 
## Obtenez une licence gratuite

Veuillez essayer l'API sans limitation d'évaluation en demandant [une licence temporaire gratuite][26].

## Conclusion

Dans cet article, nous avons appris **comment appliquer les formules les plus utilisées dans Excel à l'aide de C#**. Plus précisément, nous avons appris **comment calculer SUM, Count et Average dans Excel** par programmation. Nous avons également vu **comment appliquer la formule de pourcentage dans Excel.** De plus, vous pouvez en savoir plus sur Aspose.Cells pour l'API .NET en utilisant la [documentation][27]. En cas d'ambiguïté, n'hésitez pas à nous contacter sur le [forum][28].

## Voir également

  * [Insérer ou supprimer des lignes et des colonnes dans Excel à l'aide de C #][29]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/most-used-formulas-in-excel-using-csharp.jpg
 [2]: #CSharp-API-to-Execute-Most-Used-Formulas-in-Excel
 [3]: #Count-Cells-in-Excel-using-CSharp
 [4]: #SUM-Function-in-Excel-using-CSharp
 [5]: #Calculate-Average-in-Excel-using-CSharp
 [6]: #IF-Function-in-Excel-using-CSharp
 [7]: #Percentage-Formula-in-Excel-using-CSharp
 [8]: https://products.aspose.com/cells/net/
 [9]: https://docs.fileformat.com/spreadsheet/xlsx/
 [10]: https://docs.aspose.com/cells/net/supported-formula-functions/
 [11]: https://downloads.aspose.com/cells/net
 [12]: https://www.nuget.org/packages/aspose.cells
 [13]: https://apireference.aspose.com/cells/net/aspose.cells/workbook
 [14]: https://apireference.aspose.com/cells/net/aspose.cells/worksheet
 [15]: https://apireference.aspose.com/cells/net/aspose.cells/cell/properties/formula
 [16]: https://apireference.aspose.com/cells/net/aspose.cells/cells
 [17]: https://apireference.aspose.com/cells/net/aspose.cells/workbook/methods/calculateformula
 [18]: https://apireference.aspose.com/cells/net/aspose.cells.workbook/save/methods/2
 [19]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/Count-Cells-in-Excel-using-CSharp.jpg
 [20]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/SUM-Function-in-Excel-using-CSharp.jpg
 [21]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/Calculate-Average-in-Excel-using-CSharp.jpg
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/IF-Function-in-Excel-using-CSharp.jpg
 [23]: https://apireference.aspose.com/cells/net/aspose.cells/cell
 [24]: https://apireference.aspose.com/cells/net/aspose.cells.cell/putvalue/methods/3
 [25]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/Percentage-Formula-in-Excel-using-CSharp.jpg
 [26]: https://purchase.conholdate.com/temporary-license
 [27]: https://docs.aspose.com/cells/net/
 [28]: https://forum.aspose.com/c/cells/9
 [29]: https://blog.conholdate.com/2021/10/06/insert-or-delete-rows-and-columns-in-excel-using-csharp/








