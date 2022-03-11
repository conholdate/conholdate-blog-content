---
title: "'在 C# 中将数据导出到 Excel'"
author: Muhammad Sohail
date: 2020-08-10T08:43:31+00:00
url: /zh/2020/08/10/export-data-to-excel-in-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "CSV 到 Excel"
  - "将数组导出到 Excel CSharp"
  - "将数据表导出到 Excel"
  - "将行和列数据导出到 Excel"
  - "网格视图到 Excel"
  - "JSON 到 Excel"

---


{{< figure align=center src="images/ExportDataToAnExcelDocument.png" alt="导出数据到excel">}}
 

在本文中，我将向您展示如何使用 C# 和 VB.NET 从各种数据源（如数组、自定义对象集合、DataTable、DataView、DataGrid、GridView、HTML、JSON 和 CSV）将数据导出到 Excel。

  * [在 C# 中将数组导出到 Excel][1]
      * [将 ArrayList 导出到 Excel][2]
      * [将自定义对象的集合导出到 Excel][3]
  * [将行和列从一个 Excel 文件复制到另一个][4]
  * [在 C# 中将数据表导出到 Excel][5]
      * [将选择性数据列的数据导出到 Excel][6]
      * [将数据视图导出到 Excel][7]
  * [将数据从 DataGrid 和 GridView 导出到 Excel][8]
  * [将 HTML 格式的数据导出到 Excel][9]
      * [将 HTML 文件导出到 Excel][10]
  * [在 C# 中将 JSON 数据导出到 Excel][11]
  * [在 C# 中将 CSV 数据导出到 Excel][12]

## 使用 Aspose.Cells API 在 C# 中将数据导出到 Excel

[Aspose.Cells for .NET][13] 是一个强大的电子表格操作 API，可让您在 .NET 应用程序中创建、编辑或转换 Excel 文件。 API 易于使用的方法使您能够在几行代码中无缝地执行 Excel 自动化功能。 **NuGet** 是下载和安装 [Aspose.Cells API for .NET][14] 的最简单方法。打开 **Manage NuGet Packages** 窗口并在搜索文本框中键入“Aspose.Cells”以找到 **Aspose.Cells** .NET 包。最后，点击 **Install** 按钮安装最新版本的软件包。

## 在 C# 中将数组导出到 Excel {#Export-from-Array-to-Excel}

我们可以将引用类型或值类型的数组（一维或二维）导出到 Excel 文档。我们使用 [Cells][16] 集合的 [ImportArray][15] 方法将数据从数组导出到电子表格。 [ImportArray][15] 方法的重载版本如下。

|姓名 |说明 |
| ------------ | ------------ |
| [ImportArray(Double[], Int32, Int32, Boolean)](https://apireference.aspose.com/cells/net/aspose.cells.cells/importarray/methods/1) |将双精度数组导出到工作表中。 |
| [ImportArray(Int32[], Int32, Int32, Boolean)](https://apireference.aspose.com/cells/net/aspose.cells.cells/importarray/methods/3) |将整数数组导出到工作表中。 |
| [ImportArray(String[], Int32, Int32, Boolean)](https://apireference.aspose.com/cells/net/aspose.cells.cells/importarray/methods/5) |将字符串数组导出到工作表中。 |
| [ImportArray(Double[,], Int32, Int32)](https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/importarray/) |将 double 的二维数组导出到工作表中。 |
| [ImportArray(Int32[,], Int32, Int32)](https://apireference.aspose.com/cells/net/aspose.cells.cells/importarray/methods/2) |将整数的二维数组导出到工作表中。 |
| [ImportArray(String[,], Int32, Int32)](https://apireference.aspose.com/cells/net/aspose.cells.cells/importarray/methods/4) |将二维字符串数组导出到工作表中。 |

典型的重载采用以下参数：

  * **Array**，您从中导出内容的数组对象。
  * **行号**，数据将被导出到的第一个单元格（从零开始）的行号。
  * **列号**，数据将导出到的第一个单元格（从零开始）的列号。
  * **是垂直的**，一个布尔值，指定是垂直还是水平导出数据。

以下是在 C# 中将数组导出到 Excel 文件的步骤。

  * 创建一个 [Workbook][17] 对象。 [Workbook][17] 类表示 Microsoft Excel 文件。
  * 获取对所需工作表的引用。 [Workbook][17] 类包含一个 [Worksheets][18] 集合，允许访问 Excel 文件中的每个工作表。
  * 调用 [Cells][16] 集合的 [ImportArray][19] 方法将数组导出到指定行和列的工作表。 [Worksheet][20] 类提供了一个 [Cells][16] 集合。
  * 使用 [Workbook.Save(string)][21] 方法保存 Excel 文件。

以下代码示例演示如何将字符串数组导出到 C# 中的 Excel 文件。

```
// Instantiating a Workbook object
Workbook workbook = new Workbook();

// Obtaining the reference of the worksheet
Worksheet worksheet = workbook.Worksheets[0];

// Creating an array containing names as string values
string[] names = new string[] { "Laurence Chen", "Roman Korchagin", "Kyle Huang" };

// Exporting the array of names to first row and first column vertically
worksheet.Cells.ImportArray(names, 0, 0, true);

// Saving the Excel file
workbook.Save("StringsArray.xlsx");
```

{{< figure align=center src="images/Export-Array-to-Excel.jpg" alt="将字符串数组导出到 Excel" caption="将一组数据导出到 Excel">}}
 

同样，我们可以将**二维数组导出到 Excel 文件**。以下代码示例展示了如何在 C# 中将二维数组导出到 Excel 文件。

```
// Creating a two-dimensional array of integers
int[,] array2D = new int[4, 2] { { 1, 2 }, { 3, 4 }, { 5, 6 }, { 7, 8 } };

// Exporting a two-dimensional array at the first row and first column of the worksheet
worksheet.Cells.ImportArray(array2D, 0, 0);
```

### 在 C# 中将 ArrayList 导出到 Excel {#Export-from-ArrayList-to-Excel}

要将数据从 ArrayList 导出到工作表，请调用 [Cells][16] 集合的 [ImportArrayList][22] 方法。 [ImportArrayList][22] 方法采用以下参数：

  * **Array list** 表示您要导出的 ArrayList 对象。
  * **Row** **number** 表示数据将被导出到的第一个单元格的行号。
  * **列号**表示数据将被导出到的第一个单元格的列号。
  * **Is vertical** 一个布尔值，指定是垂直还是水平导出数据。

以下代码示例演示如何在 C# 中将 ArrayList 导出到 Excel 文件。

```
// Instantiating a Workbook object
Workbook workbook = new Workbook();

// Obtaining the reference of the worksheet
Worksheet worksheet = workbook.Worksheets[0];

// Instantiating an ArrayList object
ArrayList list = new ArrayList();

// Add few names to the list as string values
list.Add("Laurence Chen");
list.Add("Roman Korchagin");
list.Add("Kyle Huang");
list.Add("Tommy Wang");

// Exporting the contents of ArrayList vertically at the first row and first column of the worksheet. 
worksheet.Cells.ImportArrayList(list, 0, 0, true);

// Saving the Excel file
workbook.Save("ArrayListExport.xlsx");
```

### 在 C# 中将自定义对象的集合导出到 Excel {#Export-from-Collection-of-Custom-Objects}

要将数据从自定义对象集合导出到工作表，我们使用 [ImportCustomObjects][23] 方法。此方法有两个重载版本。

  1. [ImportCustomObjects(ICollection list, String[] propertyNames, Boolean isPropertyNameShown, Int32 firstRow, Int32 firstColumn, Int32 rowNumber, Boolean 插入, String dateFormatString, Boolean convertStringToNumber)][24]
  2. [ImportCustomObjects(ICollection list, Int32 firstRow, Int32 firstColumn, ImportTableOptions options)][25]

我们将一一探索每个重载的方法。下面给出第一个重载方法的参数说明：

  * **list** 自定义对象的集合。
  * **propertyNames** 要导出的对象的属性名称。如果为 null，则将导出所有属性。
  * **isPropertyNameShown** 指示是否将属性名称导出到第一行。
  * **firstRow** 要导出到的第一个单元格的行号。
  * **firstColumn** 要导出到的第一个单元格的列号。
  * **rowNumber** 要导出的对象数。
  * **insertRows** 指示是否添加额外的行以适应数据。
  * **dateFormatString** 单元格的日期格式字符串。
  * **convertStringToNumber** 指示此方法是否会尝试将字符串转换为数字。

在以下示例中，我们将 _Person_ 对象列表导出到 C# 中的 Excel 文档。请注意，我们只导出 _Person_ 对象的两个属性（_Name_ 和 _Age_）。

```
// Instantiate a new Workbook
Workbook book = new Workbook();
// Obtaining the reference of the worksheet
Worksheet sheet = book.Worksheets[0];

// Define List
List<Person> list = new List<Person>();

list.Add(new Person("Mike", 25, "Software Engineer"));
list.Add(new Person("Steve", 30, "Doctor"));
list.Add(new Person("Billy", 35, "Teacher"));

// We pick only Name and Age columns, not all, to export to the worksheet         
sheet.Cells.ImportCustomObjects((System.Collections.ICollection)list,
    new string[] { "Name", "Age" }, // propertyNames
    true, // isPropertyNameShown
    0, // firstRow
    0, // firstColumn
    list.Count, // Number of objects to be exported
    true, // insertRows
    null, // dateFormatString
    false); // convertStringToNumber

// Save the Excel file
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

{{< figure align=center src="images/Export-ArrayList-Object.jpg" alt="将对象列表导出到 Excel" caption="将人员对象列表导出到 Excel">}}
 

现在我们探索[ImportCustomObjects][23]的第二个重载方法。该方法的参数说明如下：

  * **list** 自定义对象的列表。
  * **firstRow** 要导出到的第一个单元格的行号。
  * **firstColumn** 要导出到的第一个单元格的列号。
  * **选项** [ImportTableOptions][26] 对象。

[ImportTableOptions][26] 参数提供了几个用于将数据导出到单元格的选项。其中一些如下：

  * **CheckMergedCells** Excel 文档是否包含合并单元格。
  * **ColumnIndexes** 要从数据源导出的列索引的整数数组（从 0 开始）。 _null_ 表示应导出所有列。
  * **ConvertGridStyle** 指示是否将网格视图的样式应用于单元格。
  * **ConvertNumericData** 一个布尔值，指示字符串值应转换为数字值还是日期值。
  * **DateFormat** 获取或设置具有导出 DateTime 值的单元格的日期格式字符串。
  * **DefaultValues** 表中单元格的默认值为空。
  * **InsertRows** 指示是否应添加新行以导出数据记录。
  * **IsFieldNameShown** 指示是否应导出字段名称。
  * **IsFormulas** 指示数据是否为公式。
  * **IsHtmlString** 指示数据是否包含 HTML 标记。如果我们将该值设置为 true，则在将数据导出到 Excel 文档时将保留 HTML 格式。
  * **NumberFormats** 获取或设置数字格式
  * **ShiftFirstRowDown** 指示插入行时是否应下移第一行。
  * **TotalColumns** 获取或设置要从数据源导出的总列数。 -1 表示给定数据源的所有列。
  * **TotalRows** 获取或设置要从数据源导出的总行数。 -1 表示给定数据源的所有行。

在以下示例中，我们将数据从对象集合导出到包含合并单元格的工作表。我们将 [ImportTableOptions.CheckMergedCells][27] 属性的值设置为 true，因为 Excel 文档包含合并的单元格。

```
// Opening an existing Workbook.
Workbook workbook = new Workbook("SampleMergedTemplate.xlsx");
List<Product> productList = new List<Product>();

// Creating a collection of Products
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
// Set CheckMergedCells property to true
tableOptions.CheckMergedCells = true;
tableOptions.IsFieldNameShown = false;

//Export data to excel template (in second row, first column) 
workbook.Worksheets[0].Cells.ImportCustomObjects((ICollection)productList, 1, 0, tableOptions);
workbook.Save("SampleMergedTemplate_out.xlsx", SaveFormat.Xlsx);

public class Product
{
    public int ProductId { get; set; }

    public string ProductName { get; set; }
}
```

{{< figure align=center src="images/MergedCells.jpg" alt="将数据从对象集合导出到包含合并单元格的工作表" caption="将数据导出到包含合并单元格的 Excel 文档">}}
 

## 在 C# 中将行和列从一个 Excel 文件复制到另一个文件 {#Copy-Rows-and-Columns}

我们可以通过编程将行和列从一个 Excel 文档复制到另一个文档。复制行（或列）时，其中包含的数据，包括公式（具有更新的引用）和值、注释、格式、隐藏单元格、图像和其他绘图对象也会被复制。我们还可以在同一个工作表内或在 Excel 文档中的不同工作表之间复制行和列。 Aspose.Cells 提供以下方法来复制行和列。

  * [CopyRow（单元格 sourceCells，int sourceRowIndex，int destinationRowIndex）][28] Copies data of a single row.
  * [CopyRows（单元格 sourceCells，int sourceRowIndex，int destinationRowIndex，int rowNumber）][29] Copies data of multiple rows.
  * [CopyColumn（单元格 sourceCells，int sourceColumnIndex，int destinationColumnIndex）][30] Copies data of a single column.
  * [CopyColumns（单元格 sourceCells，int sourceColumnIndex，int destinationColumnIndex，int columnNumber）][31] Copies data of multiple columns.

以下示例代码展示了如何在 C# 中将行从一个 Excel 文档复制到另一个文档。

```
// Open the source excel file.
Workbook srcWorkbook = new Workbook("Source_Workbook.xlsx");

// Instantiate the destination excel file.
Workbook destWorkbook = new Workbook();

// Get the first worksheet of the source workbook.
Worksheet srcWorksheet = srcWorkbook.Worksheets[0];

// Get the first worksheet of the destination workbook.
Worksheet desWorksheet = destWorkbook.Worksheets[0];

// Copy all the rows of the first worksheet of source Workbook to
// the first worksheet of destination Workbook.
desWorksheet.Cells.CopyRows(srcWorksheet.Cells, 0, 0, srcWorksheet.Cells.MaxDisplayRange.RowCount);

// Save the excel file.
destWorkbook.Save("Destination_Workbook.xlsx");
```

以下示例代码显示如何将一个 Excel 文档的特定行复制到另一个。

```
// Open the source excel file.
Workbook srcWorkbook = new Workbook("Source_Workbook.xlsx");

// Instantiate the destination excel file.
Workbook destWorkbook = new Workbook();

// Get the first worksheet of the source workbook.
Worksheet srcWorksheet = srcWorkbook.Worksheets[0];

// Get the first worksheet of the destination workbook.
Worksheet desWorksheet = destWorkbook.Worksheets[0];

// Copy the second row of the source Workbook to the first row of destination Workbook.
desWorksheet.Cells.CopyRow(srcWorksheet.Cells, 1, 0);

// Copy the fourth row of the source Workbook to the second row of destination Workbook.
desWorksheet.Cells.CopyRow(srcWorksheet.Cells, 3, 1);

// Save the excel file.
destWorkbook.Save("Destination_Workbook.xlsx");
```

{{< figure align=center src="images/CopyRowsData.jpg" alt="将行的数据从一个 Excel 文档复制到另一个">}}
 

我们可以类似地使用 [CopyColumn][30] 或 [CopyColumns][31] 方法将列的数据从一个 Microsoft Excel 文档复制到另一个文档。

## 在 C# 中将数据表导出到 Excel {#Export-from-DataTable-to-Excel}

[DataTable][32]、[DataColumn][33] 和 [DataView][34] 等 ADO.NET 对象中的数据可以导出到 Excel 工作表。要从 DataTable 中导出数据，我们调用 Cells 集合的 [ImportData][35] 方法。 [ImportData][36] 方法有许多重载版本，但我们使用以下方法：

```
public int ImportData(
	DataTable table,
	int firstRow,
	int firstColumn,
	ImportTableOptions options
)
```

参数说明如下：

  * **table** [DataTable](https://docs.microsoft.com/en-us/dotnet/api/system.data.datatable?view=netcore-3.1) 要导出的对象。
  * **firstRow** 要导出到的第一个单元格的行号。
  * **firstColumn** 要导出到的第一个单元格的列号。
  * **optionsType** [ImportTableOptions][26] 对象。

在以下代码示例中，我们将创建一个包含三列和两行的 DataTable 对象。并将其导出到 Excel 工作表。

```
// Instantiating a Workbook object            
Workbook workbook = new Workbook();

// Obtaining the reference of the worksheet
Worksheet worksheet = workbook.Worksheets[0];

// Instantiating a "Products" DataTable object
DataTable dataTable = new DataTable("Products");

// Adding columns to the DataTable object
dataTable.Columns.Add("Product ID", typeof(int));
dataTable.Columns.Add("Product Name", typeof(string));
dataTable.Columns.Add("Units In Stock", typeof(int));

// Creating an empty row in the DataTable object
DataRow dr = dataTable.NewRow();

// Adding data to the row
dr[0] = 1;
dr[1] = "Aniseed Syrup";
dr[2] = 15;

// Adding filled row to the DataTable object
dataTable.Rows.Add(dr);

// Creating another empty row in the DataTable object
dr = dataTable.NewRow();

// Adding data to the row
dr[0] = 2;
dr[1] = "Boston Crab Meat";
dr[2] = 123;

// Adding filled row to the DataTable object
dataTable.Rows.Add(dr);

// Setting IsFieldNameShown property to true will add column names // of the DataTable to the worksheet as a header row
ImportTableOptions tableOptions = new ImportTableOptions();
tableOptions.IsFieldNameShown = true;

// Exporting the contents of DataTable at the first row and first column.
worksheet.Cells.ImportData(dataTable, 0, 0, tableOptions);

// Saving the Excel file
workbook.Save("DataTable_Eport.xlsx");
```

{{< figure align=center src="images/Export-DataTable.jpg" alt="将数据表导出到 Excel" caption="将数据表导出到 Excel">}}
 

### 在 C# 中将选择性数据列的数据导出到 Excel {#Export-Data-of-Selective-DataColumns}

我们可以将 DataTable 或 DataView 的选择性 DataColumns 导出到 Excel 文档。如前所述，[ImportData][35] 方法接受 [ImportTableOptions][37] 类型的参数。 [ImportTableOptions][37] 类有一个 [ColumnIndexes][38] 属性，它接受我们要导出的列索引数组（从零开始）。在以下代码示例中，我们仅将 DataTable 的两个 DataColumn 导出到 Excel 工作表。

```
// Instantiating a "Products" DataTable object
DataTable dataTable = new DataTable("Products");

// Adding columns to the DataTable object
dataTable.Columns.Add("Product ID", typeof(int));
dataTable.Columns.Add("Product Name", typeof(string));
dataTable.Columns.Add("Units In Stock", typeof(int));

// Creating an empty row in the DataTable object
DataRow dr = dataTable.NewRow();

// Adding data to the row
dr[0] = 1;
dr[1] = "Aniseed Syrup";
dr[2] = 15;

// Adding filled row to the DataTable object
dataTable.Rows.Add(dr);

// Creating another empty row in the DataTable object
dr = dataTable.NewRow();

// Adding data to the row
dr[0] = 2;
dr[1] = "Boston Crab Meat";
dr[2] = 123;

// Adding filled row to the DataTable object
dataTable.Rows.Add(dr);

// Instantiate a new Workbook
Workbook book = new Workbook();

Worksheet sheet = book.Worksheets[0];

// Create export options
ImportTableOptions importOptions = new ImportTableOptions();
// Sets the columns (0-based) to export from data source.
// null means all columns should be exported.
importOptions.ColumnIndexes = new int[] { 0, 1 };
importOptions.IsFieldNameShown = true;

// Exporting the values of 1st and 2nd columns of the data table
sheet.Cells.ImportData(dataTable, 0, 0, importOptions);

book.Save("DataColumsExport.xlsx");
```

{{< figure align=center src="images/DataColumn-Export.jpg" alt="将选择性数据列的数据导出到 Excel" caption="_DataColumns 到 Excel 的输出_">}}
 

### 在 C# 中将数据从 DataView 导出到 Excel {#Export-Data-from-DataView-to-Excel}

[DataView][39] 是 DataTable 上的一个视图，可以对其进行定制以呈现来自 DataTable 的数据子集。我们使用以下重载版本的 [ImportData][36] 方法将数据从 DataView 导出到 Excel 文档。

```
public int ImportData(
	DataView dataView,
	int firstRow,
	int firstColumn,
	ImportTableOptions options
)
```

我们知道有两种方法可以创建 [DataView][40]。我们可以使用 **DataView** 构造函数，也可以创建对 [DataTable][42] 的 [DefaultView][41] 属性的引用。在下面的代码示例中，我们使用后一种方式来创建 DataView。

```
worksheet.Cells.ImportData(dataTable.DefaultView, 0, 0, options);
```

## 在 C# 中将数据从 DataGrid 和 GridView 导出到 Excel {#Export-Data-from-DataGrid-and-GridView}

[Aspose.Cells][43] 库允许我们将数据从 Microsoft Grid 控件（如 DataGrid 和 GridView）导出到 Excel 工作表。它提供 [ImportDataGrid][44] 方法从 DataGrid 导出数据和 [ImportGridView][45] 方法从 GridView 导出数据。

[ImportDataGrid][44] 方法有许多重载版本，但典型的重载采用以下参数：

  * **dataGrid**，我们从中导出内容的 _DataGrid_ 对象。
  * **firstRow**，数据将被导出到的第一个单元格的行号。
  * **firstColumn**，数据将被导出到的第一个单元格的列号。
  * **insertRows**，一个布尔属性，指示是否应将额外行添加到工作表以适应数据。
  * **importStyle**，一个布尔属性，指示是否应导出单元格样式。

下面的代码示例演示如何将数据从 DataGrid 导出到 C# 中的 Excel 文件。

```
// Create a DataTable object and set it as the DataSource of the DataGrid.
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

// Now take care of DataGrid
DataGrid dg = new DataGrid();
dg.DataSource = dataTable;
dg.DataBind();

// We have a DataGrid object with some data in it.
// Lets export it to an Excel worksheet.

// Creat a new workbook
Workbook workbook = new Workbook();
Worksheet worksheet = workbook.Worksheets[0];

// Exporting the contents of the DataGrid to the worksheet
worksheet.Cells.ImportDataGrid(dg, 0, 0, false);

// Save it as Excel file
workbook.Save("ExportDataGrid.xlsx");
```

## 在 C# 中将 HTML 格式的数据导出到 Excel {#Export-HTML-formatted-Data-to-Excel}

[Aspose.Cells][46] 允许您将 HTML 格式的数据导出到 Excel 工作表。 API 在导出数据时解析 HTML 格式的文本，并将 HTML 转换为格式化的单元格值。在以下示例代码中，DataTable 包含 HTML 格式的文本，我们使用 [ImportData][35] 方法将其导出到 Excel 文档。

```
// Prepare a DataTable with some HTML formatted values
DataTable dataTable = new DataTable("Products");

dataTable.Columns.Add("Product ID", typeof(int));
dataTable.Columns.Add("Product Name", typeof(string));
dataTable.Columns.Add("Units In Stock", typeof(int));

DataRow dr = dataTable.NewRow();
dr[0] = 1;
// Make text italicize
dr[1] = "<i>Aniseed</i> Syrup";
dr[2] = 15;
dataTable.Rows.Add(dr);

dr = dataTable.NewRow();
dr[0] = 2;
// Make text bold
dr[1] = "<b>Boston Crab Meat</b>";
dr[2] = 123;
dataTable.Rows.Add(dr);

// Create export options
ImportTableOptions exportOptions = new ImportTableOptions();
exportOptions.IsFieldNameShown = true;
// Set IsHtmlString property to true as the data contains HTML tags. 
exportOptions.IsHtmlString = true;

// Create workbook
Workbook workbook = new Workbook();
Worksheet worksheet = workbook.Worksheets[0];

worksheet.Cells.ImportData(dataTable, 0, 0, exportOptions);

workbook.Save("HTMLFormattedData_Out.xlsx");
```

{{< figure align=center src="images/Export-HTML-Formatted-Data.jpg" alt="HTML 格式的数据到电子表格" caption="将 HTML 导出的数据输出到 Excel 文档">}}
 

### 在 C# 中将 HTML 文件导出到 Excel {#Export-HTML-File-to-Excel}

Aspose.Cells 允许我们将 HTML 文件导出到 Excel。 HTML 文件应该是面向 Microsoft Excel 的，即 MS-Excel 应该能够打开它。

```
// An HTML file
string filePath = "Book1.html";

// Instantiate LoadOptions specified by the LoadFormat.
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.Html);

// Create a Workbook object and open the HTML file.
Workbook wb = new Workbook(filePath, loadOptions);

// Save the file as Excel Document
wb.Save("Book1_out.xlsx");
```

## 在 C# 中将 JSON 数据导出到 Excel {#Export-JSON-Data-to-Excel}

有时我们需要将 JSON 数据导出到 Excel 文档。使用 [Aspose.Cells][46]，我们只需几行代码就可以轻松做到这一点。 Aspose.Cells 提供了一个 [JsonUtility][47] 类，该类具有用于将 JSON 数据导出到 Excel 文档的 [ImportData][48] 方法。 [ImportData][48] 方法接受 [JsonLayoutOptions][49] 对象作为参数。 [JsonLayoutOptions][49] 类表示 JSON 布局的选项，具有以下属性。

  * [ArrayAsTable][50]: Indicates whether the array should be processed as a table.
  * [转换数字或日期][51]: Gets or sets a value that indicates whether the string in JSON is to be converted to numeric or date.
  * [日期格式][52]: Gets and sets the format of the date value.
  * [忽略数组标题][53]: Indicates whether to ignore the title if the property of the object is an array.
  * [忽略空][54]: Indicates whether the null value should be ignored.
  * [忽略对象标题][55]: Indicates whether to ignore the title if the property of the object is an object.
  * [数字格式][56]: Gets and sets the format of the numeric value.
  * [标题样式][57]: Gets and sets the style of the title.

在以下示例代码中，我们将 JSON 数据导出到 C# 中的 Excel 文件。

```
// Instantiating a Workbook object
Workbook workbook = new Workbook();
Worksheet worksheet = workbook.Worksheets[0];

// Read JSON file
string jsonInput = File.ReadAllText("Sample.json");

// Set Styles
CellsFactory factory = new CellsFactory();
Style style = factory.CreateStyle();
style.HorizontalAlignment = TextAlignmentType.Center;
style.Font.Color = System.Drawing.Color.BlueViolet;
style.Font.IsBold = true;

// Set JsonLayoutOptions
JsonLayoutOptions options = new JsonLayoutOptions();
options.TitleStyle = style;
options.ArrayAsTable = true;

// Export JSON Data
JsonUtility.ImportData(jsonInput, worksheet.Cells, 0, 0, options);

// Save Excel file
workbook.Save("ExportingJsonData.xlsx");
```

```
{
  "quiz": {
    "sport": {
      "q1": {
        "question": "Which one is correct team name in NBA?",
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

{{< figure align=center src="images/Exporting-JSON-To-Excel-1024x400.jpg" alt="JSON 数据到 Excel 文档" caption="将 JSON 数据导出到 Excel">}}
 

## 在 C# 中将 CSV 数据导出到 Excel {#Export-CSV-Data-to-Excel}

逗号分隔值 (CSV) 文件是使用逗号分隔值的分隔文本文件。 CSV 文件通常以纯文本形式存储表格数据（数字和文本），在这种情况下，每行将具有相同数量的字段。

以下代码示例显示了我们如何使用 Aspose.Cells 库打开 CSV 文件并将其保存为 Excel 文件。

```
// Instantiate LoadOptions with CSV LoadFormat.
LoadOptions loadOptions = new LoadOptions(LoadFormat.CSV);

// Open CSV file as a Workbook object
Workbook wb = new Workbook("Business-Price.csv", loadOptions);

// Save the file as an Excel Documnt
wb.Save("CSVAsAnExcelDocument.xlsx");
```

{{< figure align=center src="images/CSV-to-Excel.jpg" alt="在电子表格文档中打开 CSV 文件" caption="CSV 到 Excel 文档">}}
 

## 结论

在这篇文章中，您已经了解如何轻松地将数据从 Array、DataTable、DataView、DataGrid 和 GridView 导出到 C# 中的 Excel。您还了解了如何将 HTML、JSON、CSV 数据导出到 Excel 工作表。请查看 [文档][46] 以了解有关 Aspose.Cells API 提供的这些功能和其他几个功能的更多信息。如果您有任何问题，请随时通过我们的 [支持论坛][58] 与我们联系。

## 也可以看看

  * [在没有 MS Office 的 C# 中以编程方式创建 MS Excel 文件][59]
  * [在 C# .NET 中将数据从 JSON 导入 Excel 工作表][60]

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








