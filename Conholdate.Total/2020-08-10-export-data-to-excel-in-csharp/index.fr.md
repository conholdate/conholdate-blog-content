---
title: "Exporter des données vers Excel en C#"
author: Muhammad Sohail
date: 2020-08-10T08:43:31+00:00
url: /fr/2020/08/10/export-data-to-excel-in-csharp/
categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "CSV vers Excel"
  - "Exporter un tableau vers Excel CSharp"
  - "Exporter le tableau de données vers Excel"
  - "Exporter les données des lignes et des colonnes vers Excel"
  - "GridView vers Excel"
  - "JSON vers Excel"

---


{{< figure align=center src="images/ExportDataToAnExcelDocument.png" alt="Exporter des données vers Excel">}} 

Dans cet article, je vais vous montrer comment exporter des données vers Excel en C# et VB.NET à partir de diverses sources de données telles qu'un tableau, une collection d'objets personnalisés, DataTable, DataView, DataGrid, GridView, HTML, JSON et CSV.
  * [Exporter un tableau vers Excel en C#][1]
      * [Exporter ArrayList vers Excel][2]
      * [Exporter la collection d'objets personnalisés vers Excel][3]
  * [Copier des lignes et des colonnes d'un fichier Excel à un autre][4]
  * [Exporter DataTable vers Excel en C#][5]
      * [Exporter les données de colonnes de données sélectives vers Excel][6]
      * [Exporter DataView vers Excel][7]
  * [Exporter des données de DataGrid et GridView vers Excel][8]
  * [Exporter des données au format HTML vers Excel][9]
      * [Exporter le fichier HTML vers Excel][10]
  * [Exporter des données JSON vers Excel en C#][11]
  * [Exporter des données CSV vers Excel en C#][12]

## Exporter des données vers Excel en C# avec l'API Aspose.Cells
[Aspose.Cells pour .NET][13] est une puissante API de manipulation de feuilles de calcul qui vous permet de créer, de modifier ou de convertir des fichiers Excel dans des applications .NET. Les méthodes faciles à utiliser de l'API vous permettent d'exécuter les fonctionnalités d'automatisation d'Excel de manière transparente en quelques lignes de code. **NuGet** est le moyen le plus simple de télécharger et d'installer [l'API Aspose.Cells pour .NET][14]. Ouvrez la fenêtre **Gérer les packages NuGet** et saisissez "Aspose.Cells" dans la zone de texte de recherche pour trouver le package .NET **Aspose.Cells**. Enfin, cliquez sur le bouton **Installer** pour installer la dernière version du package.

## Exporter un tableau vers Excel en C# {#Export-from-Array-to-Excel}
Nous pouvons exporter un tableau (unidimensionnel ou bidimensionnel) d'un type référence ou d'un type valeur vers un document Excel. Nous utilisons la méthode [ImportArray][15] de la collection [Cells][16] pour exporter des données vers une feuille de calcul à partir d'un tableau. Les versions surchargées de la méthode [ImportArray][15] sont les suivantes.

| Name        | Description |
| ----------- | ----------- |
| [ImportArray(Double[], Int32, Int32, Boolean)](https://apireference.aspose.com/cells/net/aspose.cells.cells/importarray/methods/1)    | Exporte un tableau de double dans une feuille de calcul. |
| [ImportArray(Int32[], Int32, Int32, Boolean)](https://apireference.aspose.com/cells/net/aspose.cells.cells/importarray/methods/3)    | Exporte un tableau d'entiers dans une feuille de calcul. |
| [ImportArray(String[], Int32, Int32, Boolean)](https://apireference.aspose.com/cells/net/aspose.cells.cells/importarray/methods/5)    | Exporte un tableau de chaînes dans une feuille de calcul. |
| [ImportArray(Double[,], Int32, Int32)](https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/importarray/) | Exporte un tableau à deux dimensions de double dans une feuille de calcul. |
| [ImportArray(Int32[,], Int32, Int32)](https://apireference.aspose.com/cells/net/aspose.cells.cells/importarray/methods/2) | Exporte un tableau à deux dimensions d'un entier dans une feuille de calcul. |
| [ImportArray(String[,], Int32, Int32)](https://apireference.aspose.com/cells/net/aspose.cells.cells/importarray/methods/4) | Exporte un tableau de chaînes à deux dimensions dans une feuille de calcul. |

Une surcharge typique prend les paramètres suivants:
  * **Array**, l'objet tableau à partir duquel vous exportez le contenu.
  * **Numéro de ligne**, le numéro de ligne de la première cellule (base zéro) vers laquelle les données seront exportées.
  * **Numéro de colonne**, le numéro de colonne de la première cellule (base zéro) vers laquelle les données seront exportées.
  * **Est vertical**, une valeur booléenne qui spécifie s'il faut exporter les données verticalement ou horizontalement.

Voici les étapes pour exporter un tableau vers un fichier Excel en C#.
  * Créez un objet [Classeur][17]. Une classe [Workbook][17] représente un fichier Microsoft Excel.
  * Obtenez une référence à la feuille de calcul souhaitée. La classe [Workbook][17] contient une collection [Worksheets][18] qui permet d'accéder à chaque feuille de calcul dans un fichier Excel.
  * Appelez la méthode [ImportArray][19] d'une collection [Cells][16] pour exporter un tableau vers la feuille de calcul à la ligne et à la colonne spécifiées. La classe [Worksheet][20] fournit une collection [Cells][16].
  * Enregistrez le fichier Excel à l'aide de la méthode [Workbook.Save(string)][21].

L'exemple de code suivant montre comment exporter un tableau de String vers un fichier Excel en C#.

```
// Instanciation d'un objet Workbook
Workbook workbook = new Workbook();

// Obtenir la référence de la feuille de travail
Worksheet worksheet = workbook.Worksheets[0];

// Création d'un tableau contenant des noms sous forme de valeurs de chaîne
string[] names = new string[] { "Laurence Chen", "Roman Korchagin", "Kyle Huang" };

// Exportation verticale du tableau de noms vers la première ligne et la première colonne
worksheet.Cells.ImportArray(names, 0, 0, true);

// Enregistrement du fichier Excel
workbook.Save("StringsArray.xlsx");
```

{{< figure align=center src="images/Export-Array-to-Excel.jpg" alt="Exporter un tableau de chaînes vers Excel" caption="Exporter un tableau de données vers Excel">}} 

De même, nous pouvons exporter un **tableau bidimensionnel vers un fichier Excel**. L'exemple de code suivant montre comment exporter un tableau à deux dimensions vers un fichier Excel en C#.

```
// Création d'un tableau d'entiers à deux dimensions
int[,] array2D = new int[4, 2] { { 1, 2 }, { 3, 4 }, { 5, 6 }, { 7, 8 } };

// Exportation d'un tableau à deux dimensions sur la première ligne et la première colonne de la feuille de calcul
worksheet.Cells.ImportArray(array2D, 0, 0);
```

### Exporter ArrayList vers Excel en C# {#Export-from-ArrayList-to-Excel}
Pour exporter des données d'une feuille de calcul ArrayList_ _to, appelez la méthode [ImportArrayList][22] de la collection [Cells][16]. La méthode [ImportArrayList][22] prend les paramètres suivants:
  * **Array list** représente l'objet ArrayList que vous exportez.
  * **Row number** représente le numéro de ligne de la première cellule vers laquelle les données seront exportées.
  * **Numéro de colonne** représente le numéro de colonne de la première cellule vers laquelle les données seront exportées.
  * **Est vertical** une valeur booléenne qui spécifie s'il faut exporter les données verticalement ou horizontalement.

L'exemple de code suivant montre comment exporter une ArrayList vers un fichier Excel en C#.

```
// Instanciation d'un objet Workbook
Workbook workbook = new Workbook();

// Obtenir la référence de la feuille de travail
Worksheet worksheet = workbook.Worksheets[0];

// Instanciation d'un objet ArrayList
ArrayList list = new ArrayList();

// Ajouter quelques noms à la liste en tant que valeurs de chaîne
list.Add("Laurence Chen");
list.Add("Roman Korchagin");
list.Add("Kyle Huang");
list.Add("Tommy Wang");

// Exporter le contenu de ArrayList verticalement au niveau de la première ligne et de la première colonne de la feuille de calcul. 
worksheet.Cells.ImportArrayList(list, 0, 0, true);

// Enregistrement du fichier Excel
workbook.Save("ArrayListExport.xlsx");
```

### Exporter une collection d'objets personnalisés vers Excel en C# {#Export-from-Collection-of-Custom-Objects}
Pour exporter des données d'une collection d'objets personnalisés vers une feuille de calcul, nous utilisons la méthode [ImportCustomObjects][23]. Il existe deux versions surchargées de cette méthode.

  1. [ImportCustomObjects(ICollection list, String[] propertyNames, Boolean isPropertyNameShown, Int32 firstRow, Int32 firstColumn, Int32 rowNumber, Boolean insertions, String dateFormatString, Boolean convertStringToNumber)][24]
  2. [ImportCustomObjects(ICollection list, Int32 firstRow, Int32 firstColumn, ImportTableOptions options)][25]

Nous allons explorer chaque méthode surchargée une par une. La description des paramètres de la première méthode surchargée est donnée ci-dessous:
  * **list** La collection des objets personnalisés.
  * **propertyNames** Noms des propriétés de l'objet à exporter. S'il est nul, toutes les propriétés seront exportées.
  * **isPropertyNameShown** Indique si les noms de propriété seront exportés vers la première ligne.
  * **firstRow** Le numéro de ligne de la première cellule vers laquelle exporter.
  * **firstColumn** Le numéro de colonne de la première cellule vers laquelle exporter.
  * **rowNumber** Nombre d'objets à exporter.
  * **insertRows** Indique si des lignes supplémentaires sont ajoutées pour ajuster les données.
  * **dateFormatString** Chaîne de format de date pour les cellules.
  * **convertStringToNumber** Indique si cette méthode tentera de convertir une chaîne en nombre.

Dans l'exemple suivant, nous exportons une liste d'objets _Person_ vers un document Excel en C#. Veuillez noter que nous n'exportons que deux propriétés (_Name_ et _Age_) d'un objet _Person_.

```
// Instancier un nouveau classeur
Workbook book = new Workbook();
// Obtenir la référence de la feuille de travail
Worksheet sheet = book.Worksheets[0];

// Définir la liste
List<Person> list = new List<Person>();

list.Add(new Person("Mike", 25, "Software Engineer"));
list.Add(new Person("Steve", 30, "Doctor"));
list.Add(new Person("Billy", 35, "Teacher"));

// Nous sélectionnons uniquement les colonnes Nom et Âge, pas toutes, à exporter vers la feuille de calcul
sheet.Cells.ImportCustomObjects((System.Collections.ICollection)list,
    new string[] { "Name", "Age" }, // propertyNames
    true, // isPropertyNameShown
    0, // firstRow
    0, // firstColumn
    list.Count, // Nombre d'objets à exporter
    true, // insertRows
    null, // dateFormatString
    false); // convertStringToNumber

// Enregistrez le fichier Excel
book.Save("ExportedCustomObjects.xlsx");
       
public class Person
{
    public string Name { get; set; }

    public int Age { get; set; }

    public string Occupation { get; set; }

    public Person(string name, int age, string occupation)
    {
        Age = age;
        Name = name;
        Occupation = occupation;
    }
}
```

{{< figure align=center src="images/Export-ArrayList-Object.jpg" alt="Exporter la liste des objets vers Excel" caption="Exporter une liste d'objets Personne vers Excel">}} 

Nous explorons maintenant la deuxième méthode surchargée de [ImportCustomObjects][23]. La description des paramètres de la méthode est donnée ci-dessous:
  * **list** La liste des objets personnalisés.
  * **firstRow** Le numéro de ligne de la première cellule vers laquelle exporter.
  * **firstColumn** Le numéro de colonne de la première cellule vers laquelle exporter.
  * **options** [ImportTableOptions][26] objet.

Le paramètre [ImportTableOptions][26] fournit plusieurs options pour exporter des données dans des cellules. Certains d'entre eux sont donnés ci-dessous:
  * **CheckMergedCells** Un document Excel contient-il des cellules fusionnées.
  * **ColumnIndexes** Tableau d'entiers d'index de colonnes (de base 0) à exporter depuis la source de données. _null_ signifie que toutes les colonnes doivent être exportées.
  * **ConvertGridStyle** Indique s'il faut appliquer le style de la vue de grille aux cellules.
  * **ConvertNumericData** Une valeur booléenne qui indique si la valeur de chaîne doit être convertie en valeur numérique ou de date.
  * **DateFormat** Obtient ou définit la chaîne de format de date pour les cellules avec des valeurs DateTime exportées.
  * **DefaultValues** La valeur par défaut de la cellule du tableau est nulle.
  * **InsertRows** Indique si de nouvelles lignes doivent être ajoutées pour exporter des enregistrements de données.
  * **IsFieldNameShown** Indique si les noms de champ doivent être exportés.
  * **IsFormulas** Indique si les données sont des formules.
  * **IsHtmlString** Indique si les données contiennent des balises HTML. Si nous définissons la valeur sur true, le formatage HTML restera conservé lors de l'exportation des données vers un document Excel.
  * **NumberFormats** Obtient ou définit les formats de nombre
  * **ShiftFirstRowDown** Indique si la première ligne doit être décalée vers le bas lors de l'insertion de lignes.
  * **TotalColumns** Obtient ou définit le nombre total de colonnes à exporter à partir d'une source de données. -1 signifie toutes les colonnes de la source de données donnée.
  * **TotalRows** Obtient ou définit le nombre total de lignes à exporter à partir de la source de données. -1 signifie toutes les lignes de la source de données donnée.

Dans l'exemple suivant, nous exportons des données d'une collection d'objets vers une feuille de calcul contenant des cellules fusionnées. Nous définissons la valeur de la propriété [ImportTableOptions.CheckMergedCells][27] sur true car le document Excel contient des cellules fusionnées.

```
// Ouverture d'un classeur existant.
Workbook workbook = new Workbook("SampleMergedTemplate.xlsx");
List<Product> productList = new List<Product>();

// Création d'une collection de produits
for (int i = 0; i < 3; i++)
{
    Product product = new Product
    {
        ProductId = i,
        ProductName = "Test Product - " + i
    };
    productList.Add(product);
}

ImportTableOptions tableOptions = new ImportTableOptions();
// Définissez la propriété CheckMergedCells sur true
tableOptions.CheckMergedCells = true;
tableOptions.IsFieldNameShown = false;

// Exporter les données vers un modèle Excel (dans la deuxième ligne, première colonne) 
workbook.Worksheets[0].Cells.ImportCustomObjects((ICollection)productList, 1, 0, tableOptions);
workbook.Save("SampleMergedTemplate_out.xlsx", SaveFormat.Xlsx);

public class Product
{
    public int ProductId { get; set; }

    public string ProductName { get; set; }
}
```

{{< figure align=center src="images/MergedCells.jpg" alt="Exporter des données d'une collection d'objets vers une feuille de calcul contenant des cellules fusionnées" caption="Exporter des données vers un document Excel contenant des cellules fusionnées">}} 

## Copie les lignes et les colonnes d'un fichier Excel à un autre en C# {#Copy-Rows-and-Columns}
Nous pouvons copier par programmation des lignes et des colonnes d'un document Excel à un autre. Lorsqu'une ligne (ou une colonne) est copiée, les données qu'elle contient, y compris les formules - avec des références mises à jour - et les valeurs, les commentaires, le formatage, les cellules masquées, les images et d'autres objets de dessin sont également copiés. Nous pouvons également copier des lignes et des colonnes dans la même feuille de calcul ou sur différentes feuilles de calcul dans un document Excel. Aspose.Cells fournit les méthodes suivantes pour copier des lignes et des colonnes.
  * [CopyRow(Cellules sourceCells, int sourceRowIndex, int destinationRowIndex)][28] Copies data of a single row.
  * [CopyRows (Cellules sourceCells, int sourceRowIndex, int destinationRowIndex, int rowNumber)][29] Copies data of multiple rows.
  * [CopyColumn(Cells sourceCells, int sourceColumnIndex, int destinationColumnIndex)][30] Copies data of a single column.
  * [CopyColumns(Cells sourceCells, int sourceColumnIndex, int destinationColumnIndex, int columnNumber)][31] Copies data of multiple columns.

L'exemple de code suivant montre comment copier des lignes d'un document Excel à un autre en C#.

```
// Ouvrir le fichier Excel source.
Workbook srcWorkbook = new Workbook("Source_Workbook.xlsx");

// Instancier le fichier excel de destination.
Workbook destWorkbook = new Workbook();

// Obtenir la première feuille de calcul du classeur source.
Worksheet srcWorksheet = srcWorkbook.Worksheets[0];

// Obtenir la première feuille de calcul du classeur de destination.
Worksheet desWorksheet = destWorkbook.Worksheets[0];

// Copiez toutes les lignes de la première feuille de calcul du classeur source dans la première feuille de calcul du classeur de destination.
desWorksheet.Cells.CopyRows(srcWorksheet.Cells, 0, 0, srcWorksheet.Cells.MaxDisplayRange.RowCount);

// Enregistrez le fichier excel.
destWorkbook.Save("Destination_Workbook.xlsx");
```

L'exemple de code suivant montre comment copier des lignes spécifiques d'un document Excel dans un autre.

```
// Ouvrez le fichier Excel source.
Workbook srcWorkbook = new Workbook("Source_Workbook.xlsx");

// Instanciez le fichier Excel de destination.
Workbook destWorkbook = new Workbook();

// Obtenez la première feuille de calcul du classeur source.
Worksheet srcWorksheet = srcWorkbook.Worksheets[0];

// Obtenez la première feuille de calcul du classeur de destination.
Worksheet desWorksheet = destWorkbook.Worksheets[0];

// Copiez la deuxième ligne du classeur source dans la première ligne du classeur de destination.
desWorksheet.Cells.CopyRow(srcWorksheet.Cells, 1, 0);

// Copiez la quatrième ligne du classeur source dans la deuxième ligne du classeur de destination.
desWorksheet.Cells.CopyRow(srcWorksheet.Cells, 3, 1);

// Enregistrez le fichier excel.
destWorkbook.Save("Destination_Workbook.xlsx");
```

{{< figure align=center src="images/CopyRowsData.jpg" alt="Copie les données des lignes d'un document Excel à un autre">}} 

Nous pouvons également copier les données des colonnes d'un document Microsoft Excel à un autre en utilisant la méthode [CopyColumn][30] ou [CopyColumns][31].

## Exporter DataTable vers Excel en C# {#Export-from-DataTable-to-Excel}
Les données des objets ADO.NET tels que [DataTable][32], [DataColumn][33] et [DataView][34] peuvent être exportées vers des feuilles de calcul Excel. Pour exporter des données à partir d'un DataTable, nous appelons la méthode [ImportData][35] de la collection Cells. Il existe de nombreuses versions surchargées de la méthode [ImportData][36] mais nous utilisons ce qui suit:

```
public int ImportData(
	DataTable table,
	int firstRow,
	int firstColumn,
	ImportTableOptions options
)
```

La description des paramètres est donnée ci-dessous:
  * **table** L' [objet DataTable](https://docs.microsoft.com/en-us/dotnet/api/system.data.datatable?view=netcore-3.1) à exporter.
  * **firstRow** Le numéro de ligne de la première cellule vers laquelle exporter.
  * **firstColumn** Le numéro de colonne de la première cellule vers laquelle exporter.
  * **optionsType** [ImportTableOptions][26] objet.

Dans l'exemple de code suivant, nous créons un objet DataTable qui comporte trois colonnes et deux lignes. Et l'exporter vers une feuille de calcul Excel.

```
// Instanciation d'un objet Workbook            
Workbook workbook = new Workbook();

// Obtenir la référence de la feuille de travail
Worksheet worksheet = workbook.Worksheets[0];

// Instanciation d'un objet DataTable "Products"
DataTable dataTable = new DataTable("Products");

// Ajout de colonnes à l'objet DataTable
dataTable.Columns.Add("Product ID", typeof(int));
dataTable.Columns.Add("Product Name", typeof(string));
dataTable.Columns.Add("Units In Stock", typeof(int));

// Création d'une ligne vide dans l'objet DataTable
DataRow dr = dataTable.NewRow();

// Ajout de données à la ligne
dr[0] = 1;
dr[1] = "Aniseed Syrup";
dr[2] = 15;

// Ajout d'une ligne remplie à l'objet DataTable
dataTable.Rows.Add(dr);

// Création d'une autre ligne vide dans l'objet DataTable
dr = dataTable.NewRow();

// Ajout de données à la ligne
dr[0] = 2;
dr[1] = "Boston Crab Meat";
dr[2] = 123;

// Ajout d'une ligne remplie à l'objet DataTable
dataTable.Rows.Add(dr);

// La définition de la propriété IsFieldNameShown sur true ajoutera les noms de colonne du DataTable à la feuille de calcul en tant que ligne d'en-tête
ImportTableOptions tableOptions = new ImportTableOptions();
tableOptions.IsFieldNameShown = true;

// Exportation du contenu de DataTable à la première ligne et à la première colonne.
worksheet.Cells.ImportData(dataTable, 0, 0, tableOptions);

// Enregistrement du fichier Excel
workbook.Save("DataTable_Eport.xlsx");
```

{{< figure align=center src="images/Export-DataTable.jpg" alt="Exporter le tableau de données vers Excel" caption="Exporter le tableau de données vers Excel">}} 

### Exporter les données de Selective DataColumns vers Excel en C# {#Export-Data-of-Selective-DataColumns}
Nous pouvons exporter des DataColumns sélectives d'un DataTable ou d'un DataView vers un document Excel. Comme indiqué précédemment, la méthode [ImportData][35] accepte un argument de type [ImportTableOptions][37]. La classe [ImportTableOptions][37] a une propriété [ColumnIndexes][38] qui accepte un tableau d'index de colonnes (basé sur zéro) que nous voulons exporter. Dans l'exemple de code suivant, nous exportons uniquement deux DataColumns d'un DataTable vers une feuille de calcul Excel.

```
// Instanciation d'un objet DataTable "Products"
DataTable dataTable = new DataTable("Products");

// Ajout de colonnes à l'objet DataTable
dataTable.Columns.Add("Product ID", typeof(int));
dataTable.Columns.Add("Product Name", typeof(string));
dataTable.Columns.Add("Units In Stock", typeof(int));

// Création d'une ligne vide dans l'objet DataTable
DataRow dr = dataTable.NewRow();

// Ajout de données à la ligne
dr[0] = 1;
dr[1] = "Aniseed Syrup";
dr[2] = 15;

// Ajout d'une ligne remplie à l'objet DataTable
dataTable.Rows.Add(dr);

// Création d'une autre ligne vide dans l'objet DataTable
dr = dataTable.NewRow();

// Ajout de données à la ligne
dr[0] = 2;
dr[1] = "Boston Crab Meat";
dr[2] = 123;

// Ajout d'une ligne remplie à l'objet DataTable
dataTable.Rows.Add(dr);

// Instancier un nouveau classeur
Workbook book = new Workbook();

Worksheet sheet = book.Worksheets[0];

// Créer des options d'exportation
ImportTableOptions importOptions = new ImportTableOptions();
// Définit les colonnes (base 0) à exporter depuis la source de données.
// null signifie que toutes les colonnes doivent être exportées.
importOptions.ColumnIndexes = new int[] { 0, 1 };
importOptions.IsFieldNameShown = true;

// Exportation des valeurs des 1ère et 2ème colonnes du tableau de données
sheet.Cells.ImportData(dataTable, 0, 0, importOptions);

book.Save("DataColumsExport.xlsx");
```

{{< figure align=center src="images/DataColumn-Export.jpg" alt="Exporter les données de colonnes de données sélectives vers Excel" caption="_La sortie de DataColumns vers Excel_">}} 

### Exporter des données de DataView vers Excel en C# {#Export-Data-from-DataView-to-Excel}
Un [DataView][39] est une vue sur un DataTable qui peut être personnalisée pour présenter un sous-ensemble de données du DataTable. Nous utilisons la version surchargée suivante de la méthode [ImportData][36] pour exporter des données de DataView vers un document Excel.

```
public int ImportData(
	DataView dataView,
	int firstRow,
	int firstColumn,
	ImportTableOptions options
)
```

Nous savons qu'il existe deux façons de créer un [DataView][40]. Nous pouvons utiliser le constructeur **DataView**, ou nous pouvons créer une référence à la propriété [DefaultView][41] du [DataTable][42]. Dans l'exemple de code suivant, nous utilisons la méthode la plus récente pour créer un DataView.

```
worksheet.Cells.ImportData(dataTable.DefaultView, 0, 0, options);
```

## Exporter des données de DataGrid et GridView vers Excel en C# {#Export-Data-from-DataGrid-and-GridView}
La bibliothèque [Aspose.Cells][43] nous permet d'exporter des données à partir de contrôles Microsoft Grid tels que DataGrid et GridView vers une feuille de calcul Excel. Il fournit la méthode [ImportDataGrid][44] pour exporter les données d'un DataGrid et la méthode [ImportGridView][45] pour exporter les données d'un GridView.
Il existe de nombreuses versions surchargées de la méthode [ImportDataGrid][44] mais une surcharge typique prend les paramètres suivants:

  * **dataGrid**, l'objet _DataGrid_ à partir duquel nous exportons le contenu.
  * **firstRow**, le numéro de ligne de la première cellule vers laquelle les données seront exportées.
  * **firstColumn**, le numéro de colonne de la première cellule vers laquelle les données seront exportées.
  * **insertRows**, une propriété booléenne qui indique si des lignes supplémentaires doivent être ajoutées à la feuille de calcul pour ajuster les données.
  * **importStyle**, une propriété booléenne qui indique si le style de cellule doit être exporté.

L'exemple de code suivant montre comment exporter des données de DataGrid vers un fichier Excel en C#.

```
// Créez un objet DataTable et définissez-le comme DataSource du DataGrid.
DataTable dataTable = new DataTable("Products");
dataTable.Columns.Add("Product ID", typeof(int));
dataTable.Columns.Add("Product Name", typeof(string));
dataTable.Columns.Add("Units In Stock", typeof(int));

DataRow dr = dataTable.NewRow();
dr[0] = 1;
dr[1] = "Aniseed Syrup";
dr[2] = 15;
dataTable.Rows.Add(dr);

dr = dataTable.NewRow();
dr[0] = 2;
dr[1] = "Boston Crab Meat";
dr[2] = 123;
dataTable.Rows.Add(dr);

// Occupez-vous maintenant de DataGrid
DataGrid dg = new DataGrid();
dg.DataSource = dataTable;
dg.DataBind();

// Nous avons un objet DataGrid contenant des données.
// Exportons-le dans une feuille de calcul Excel.

// Créer un nouveau classeur
Workbook workbook = new Workbook();
Worksheet worksheet = workbook.Worksheets[0];

// Exportation du contenu du DataGrid vers la feuille de calcul
worksheet.Cells.ImportDataGrid(dg, 0, 0, false);

// Enregistrez-le en tant que fichier Excel
workbook.Save("ExportDataGrid.xlsx");
```

## Exporter des données au format HTML vers Excel en C# {#Export-HTML-formatted-Data-to-Excel}
[Aspose.Cells][46] vous permet d'exporter des données au format HTML vers une feuille de calcul Excel. L'API analyse le texte au format HTML lors de l'exportation des données et convertit le HTML en valeurs de cellule formatées. Dans l'exemple de code suivant, DataTable contient du texte au format HTML et nous l'exportons vers un document Excel à l'aide de la méthode [ImportData][35].

```
// Préparer un DataTable avec des valeurs au format HTML
DataTable dataTable = new DataTable("Products");

dataTable.Columns.Add("Product ID", typeof(int));
dataTable.Columns.Add("Product Name", typeof(string));
dataTable.Columns.Add("Units In Stock", typeof(int));

DataRow dr = dataTable.NewRow();
dr[0] = 1;
// Mettre le texte en italique
dr[1] = "<i>Aniseed</i> Syrup";
dr[2] = 15;
dataTable.Rows.Add(dr);

dr = dataTable.NewRow();
dr[0] = 2;
// Mettre le texte en gras
dr[1] = "<b>Boston Crab Meat</b>";
dr[2] = 123;
dataTable.Rows.Add(dr);

// Créer des options d'exportation
ImportTableOptions exportOptions = new ImportTableOptions();
exportOptions.IsFieldNameShown = true;
// Définissez la propriété IsHtmlString sur true car les données contiennent des balises HTML. 
exportOptions.IsHtmlString = true;

// Créer un classeur
Workbook workbook = new Workbook();
Worksheet worksheet = workbook.Worksheets[0];

worksheet.Cells.ImportData(dataTable, 0, 0, exportOptions);

workbook.Save("HTMLFormattedData_Out.xlsx");
```

{{< figure align=center src="images/Export-HTML-Formatted-Data.jpg" alt="Données au format HTML dans une feuille de calcul" caption="La sortie des données HTML exportées vers un document Excel">}} 

### Exporter un fichier HTML vers Excel en C# {#Export-HTML-File-to-Excel}
Aspose.Cells nous permet d'exporter un fichier HTML vers Excel. Le fichier HTML doit être orienté Microsoft Excel, c'est-à-dire que MS-Excel doit pouvoir l'ouvrir.

```
// Un fichier HTML
string filePath = "Book1.html";

// Instanciez LoadOptions spécifié par LoadFormat.
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.Html);

// Créez un objet Workbook et ouvrez le fichier HTML.
Workbook wb = new Workbook(filePath, loadOptions);

// Enregistrez le fichier en tant que document Excel.
wb.Save("Book1_out.xlsx");
```

## Exporter des données JSON vers Excel en C# {#Export-JSON-Data-to-Excel}
Parfois, nous avons besoin d'exporter des données JSON vers un document Excel. Avec [Aspose.Cells][46], nous pouvons facilement le faire avec quelques lignes de code. Aspose.Cells fournit une classe [JsonUtility][47] qui a une méthode [ImportData][48] pour exporter des données JSON vers un document Excel. La méthode [ImportData][48] accepte l'objet [JsonLayoutOptions][49] comme paramètre. La classe [JsonLayoutOptions][49] représente les options de mise en page JSON et possède les propriétés suivantes.

  * [ArrayAsTable][50]: Indique si le tableau doit être traité comme une table.
  * [ConvertNumericOrDate][51]: Obtient ou définit une valeur qui indique si la chaîne dans JSON doit être convertie en numérique ou en date.
  * [DateFormat][52]: Obtient et définit le format de la valeur de date.
  * [IgnoreArrayTitle][53]: Indique s'il faut ignorer le titre si la propriété de l'objet est un tableau.
  * [IgnoreNull][54]: Indique si la valeur nulle doit être ignorée.
  * [IgnoreObjectTitle][55]: Indique s'il faut ignorer le titre si la propriété de l'objet est un objet.
  * [NumberFormat][56]: Obtient et définit le format de la valeur numérique.
  * [TitleStyle][57]: Obtient et définit le style du titre.

Dans l'exemple de code suivant, nous exportons des données JSON vers un fichier Excel en C#.

```
// Instanciation d'un objet Workbook
Workbook workbook = new Workbook();
Worksheet worksheet = workbook.Worksheets[0];

// Lire le fichier JSON
string jsonInput = File.ReadAllText("Sample.json");

// Définir des styles
CellsFactory factory = new CellsFactory();
Style style = factory.CreateStyle();
style.HorizontalAlignment = TextAlignmentType.Center;
style.Font.Color = System.Drawing.Color.BlueViolet;
style.Font.IsBold = true;

// Définir JsonLayoutOptions
JsonLayoutOptions options = new JsonLayoutOptions();
options.TitleStyle = style;
options.ArrayAsTable = true;

// Exporter les données JSON
JsonUtility.ImportData(jsonInput, worksheet.Cells, 0, 0, options);

// Enregistrer le fichier Excel
workbook.Save("ExportingJsonData.xlsx");
```

```
{
  "quiz": {
    "sport": {
      "q1": {
        "question": "Lequel est le bon nom d'équipe en NBA ?",
        "answer": "Huston Rocket"
      }
    },
    "maths": {
      "q1": {
        "question": "5 + 7 = ?",
        "answer": "12"
      },
      "q2": {
        "question": "12 - 8 = ?",
        "answer": "4"
      }
    }
  }
}
```

{{< figure align=center src="images/Exporting-JSON-To-Excel-1024x400.jpg" alt="Données JSON dans un document Excel" caption="Exporter des données JSON vers Excel">}} 

## Exporter des données CSV vers Excel en C# {#Export-CSV-Data-to-Excel}
Un fichier de valeurs séparées par des virgules (CSV) est un fichier texte délimité qui utilise une virgule pour séparer les valeurs. Un fichier CSV stocke généralement des données tabulaires (chiffres et texte) en texte brut, auquel cas chaque ligne aura le même nombre de champs.
L'exemple de code suivant montre comment nous pouvons ouvrir un fichier CSV et l'enregistrer en tant que fichier Excel à l'aide de la bibliothèque Aspose.Cells.

```
// Instanciez LoadOptions avec CSV LoadFormat.
LoadOptions loadOptions = new LoadOptions(LoadFormat.CSV);

// Ouvrir le fichier CSV en tant qu'objet Workbook.
Workbook wb = new Workbook("Business-Price.csv", loadOptions);

// Enregistrez le fichier en tant que document Excel
wb.Save("CSVAsAnExcelDocument.xlsx");
```

{{< figure align=center src="images/CSV-to-Excel.jpg" alt="Ouvrir un fichier CSV dans un document de feuille de calcul" caption="CSV vers un document Excel">}} 

## Conclusion

Dans cet article, vous avez vu avec quelle facilité vous pouvez exporter des données vers Excel en C # à partir de Array, DataTable, DataView, DataGrid et GridView. Vous avez également vu comment exporter des données HTML, JSON, CSV vers une feuille de calcul Excel. Veuillez consulter la [documentation][46] pour en savoir plus sur ces fonctionnalités et sur plusieurs autres fonctionnalités proposées par l'API Aspose.Cells. Si vous avez des questions, n'hésitez pas à nous contacter via notre [Forum d'assistance][58].

## Voir également

  * [Créer des fichiers MS Excel par programmation en C # sans MS Office][59]
  * [Importer des données de JSON vers une feuille de calcul Excel en C # .NET][60]

 [1]: #Export-from-Array-to-Excel
 [2]: #Export-from-ArrayList-to-Excel
 [3]: #Export-from-Collection-of-Custom-Objects
 [4]: #Copy-Rows-and-Columns
 [5]: #Export-from-DataTable-to-Excel
 [6]: #Export-Data-of-Selective-DataColumns
 [7]: #Export-Data-from-DataView-to-Excel
 [8]: #Export-Data-from-DataGrid-and-GridView
 [9]: #Export-HTML-formatted-Data-to-Excel
 [10]: #Export-HTML-File-to-Excel
 [11]: #Export-JSON-Data-to-Excel
 [12]: #Export-CSV-Data-to-Excel
 [13]: https://products.aspose.com/cells/net
 [14]: https://www.nuget.org/packages/Aspose.Cells/
 [15]: https://apireference.aspose.com/net/cells/aspose.cells/cells/methods/importarray/index
 [16]: https://apireference.aspose.com/net/cells/aspose.cells/worksheet/properties/cells
 [17]: https://apireference.aspose.com/net/cells/aspose.cells/workbook
 [18]: https://apireference.aspose.com/net/cells/aspose.cells/workbook/properties/worksheets
 [19]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/importarray/index
 [20]: https://apireference.aspose.com/net/cells/aspose.cells/worksheet
 [21]: https://apireference.aspose.com/net/cells/aspose.cells.workbook/save/methods/2
 [22]: https://apireference.aspose.com/net/cells/aspose.cells/cells/methods/importarraylist
 [23]: https://apireference.aspose.com/net/cells/aspose.cells/cells/methods/importcustomobjects/index
 [24]: https://apireference.aspose.com/cells/net/aspose.cells.cells/importcustomobjects/methods/1
 [25]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/importcustomobjects
 [26]: https://apireference.aspose.com/cells/net/aspose.cells/importtableoptions
 [27]: https://apireference.aspose.com/net/cells/aspose.cells/importtableoptions/properties/checkmergedcells
 [28]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/copyrow
 [29]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/copyrows
 [30]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/copycolumn
 [31]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/copycolumns
 [32]: https://docs.microsoft.com/en-us/dotnet/framework/data/adonet/dataset-datatable-dataview/datatables
 [33]: https://docs.microsoft.com/en-us/dotnet/api/system.data.datacolumn?view=netcore-3.1
 [34]: https://docs.microsoft.com/en-us/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews
 [35]: https://apireference.aspose.com/cells/net/aspose.cells.cells/importdata/methods/1
 [36]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/importdata/index
 [37]: https://apireference.aspose.com/net/cells/aspose.cells/importtableoptions
 [38]: https://apireference.aspose.com/net/cells/aspose.cells/importtableoptions/properties/columnindexes
 [39]: https://docs.microsoft.com/en-us/dotnet/api/system.data.dataview?view=netcore-3.1
 [40]: https://docs.microsoft.com/en-us/dotnet/api/system.data.dataview
 [41]: https://docs.microsoft.com/en-us/dotnet/api/system.data.datatable.defaultview
 [42]: https://docs.microsoft.com/en-us/dotnet/api/system.data.datatable
 [43]: https://products.aspose.com/cells
 [44]: https://apireference.aspose.com/net/cells/aspose.cells/cells/methods/importdatagrid/index
 [45]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/importgridview
 [46]: https://docs.aspose.com/cells/net/
 [47]: https://apireference.aspose.com/net/cells/aspose.cells.utility/jsonutility
 [48]: https://apireference.aspose.com/net/cells/aspose.cells.utility/jsonutility/methods/importdata
 [49]: https://apireference.aspose.com/net/cells/aspose.cells.utility/jsonlayoutoptions
 [50]: https://apireference.aspose.com/net/cells/aspose.cells.utility/jsonlayoutoptions/properties/arrayastable
 [51]: https://apireference.aspose.com/net/cells/aspose.cells.utility/jsonlayoutoptions/properties/convertnumericordate
 [52]: https://apireference.aspose.com/net/cells/aspose.cells.utility/jsonlayoutoptions/properties/dateformat
 [53]: https://apireference.aspose.com/net/cells/aspose.cells.utility/jsonlayoutoptions/properties/ignorearraytitle
 [54]: https://apireference.aspose.com/net/cells/aspose.cells.utility/jsonlayoutoptions/properties/ignorenull
 [55]: https://apireference.aspose.com/net/cells/aspose.cells.utility/jsonlayoutoptions/properties/ignoreobjecttitle
 [56]: https://apireference.aspose.com/net/cells/aspose.cells.utility/jsonlayoutoptions/properties/numberformat
 [57]: https://apireference.aspose.com/net/cells/aspose.cells.utility/jsonlayoutoptions/properties/titlestyle
 [58]: https://forum.aspose.com/
 [59]: https://blog.aspose.com/2020/01/21/create-excel-xls-xlsx-programmatically-in-csharp-net/
 [60]: https://blog.aspose.com/2020/04/03/import-data-from-json-to-excel-in-csharp-asp.net/

