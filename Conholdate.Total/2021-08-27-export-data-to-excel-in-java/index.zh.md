---
title: "在 Java 中将数据导出到 Excel"
author: Muzammil Khan
date: 2021-08-27T03:06:50+00:00
summary: "作为 Java 开发人员，您可以通过编程轻松地将数据从数组、对象集合、JSON 或 CSV 导出到 Excel。在本文中，您将学习**如何使用 Java** 将数据导出到 Excel。"
url: /zh/2021/08/27/export-data-to-excel-in-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "用 Java 将数组导出到 Excel"
  - "用 Java 将 CSV 数据导出到 Excel"
  - "在 Java 中将 JSON 数据导出到 Excel"
  - "将行和列数据导出到 Excel"

---


{{< figure align=center src="images/export-data-to-excel-in-java.jpg" alt="在 Java 中将数据导出到 Excel">}}
 

您可以轻松地将数据从各种可用来源（例如 JSON 和 CSV）导出到 Microsoft Excel。作为 Java 开发人员，您可以通过编程方式将数据从数组、对象列表、JSON 和 CSV 导出到 Excel 文档。在本文中，您将学习**如何使用 Java 将数据导出到 Excel**。

本文讨论/涵盖了以下主题：

  * [用于导出数据的 Java API][2]
  * [用 Java 将数组导出到 Excel][3]
  * [将二维数组导出到 Excel][4]
  * [Java 中的 ArrayList 到 Excel][5]
  * [在 Java 中将自定义对象的集合导出到 Excel][6]
  * [使用 Java 中的合并单元格将数据导出到 Excel][7]
  * [在 Java 中将行和列从一个 Excel 文件复制到另一个文件][8]
  * [在 Java 中将 JSON 数据导出到 Excel][9]
  * [使用 Java 在 Excel 中获取 CSV 数据][10]

## 用于导出数据的 Java API {#Java-API-for-Exporting-Data}

为了将数据导出到 Excel，我将使用 [Aspose.Cells for Java API][11]。它是一个强大的电子表格操作 API，可让您在 Java 应用程序中创建、编辑或转换 Excel 文件。 API 使您能够以编程方式执行 Excel 自动化功能，而无需 Microsoft Excel 应用程序。

您可以 [下载][12] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置，以尝试以下代码示例。

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
    <version>21.8</version>
</dependency>
```

## 用 Java 将数组导出到 Excel {#Export-Array-to-Excel-in-Java}

您可以轻松地将数据从一维数组或二维数组导出到 Excel 文档。数组可以是引用类型或值类型。您可以按照下面提到的简单步骤将数据从数组导出到 Excel：

  * 创建 _[Workbook][13]_ 类的实例
  * 在 [_Worksheet_][14] 类的实例中获取工作表
  * 创建一个包含字符串值的数组
  * 使用数组调用 [_importArray()_][15] 方法
  * 通过调用_Workbook_类的_[save()][16]_方法保存输出文件

以下代码示例展示了**如何使用 Java 将字符串数组导出到 Excel**。

```
// 初始化工作簿对象
Workbook workbook = new Workbook();

// 获取工作表的引用
Worksheet worksheet = workbook.getWorksheets().get(0);

// 创建一个包含名称作为字符串值的数组
String[] names = new String[] { "Laurence Chen", "Roman Korchagin", "Kyle Huang" };

// 将名称数组垂直导出到第一行和第一列
worksheet.getCells().importArray(names, 0, 0, true);

// 保存 Excel 文件
workbook.save("C:\\Files\\output.xlsx");
```

{{< figure align=center src="images/Export-Array-to-Excel-in-Java.jpg" alt="用 Java 将数组导出到 Excel" caption="用 Java 将数组导出到 Excel">}}
 

API 的 **[Workbook][13]** 类是创建 Excel 电子表格的主要类。它提供了打开和保存本机 excel 文件的功能。该类的**[_save()_][16]**方法用于将输出文件保存到指定的文件路径。

**[Worksheet][14]** 类表示单个工作表并提供处理单元格和行的功能。

Cells 类的 [_importArray()_][15] 方法将字符串数组导出到工作表。它采用以下输入参数：

  * _**stringArray**_：字符串值的数组
  * _**firstRow**_：要导出到的第一个单元格的行号
  * _**firstColumn**_：要导出到的第一个单元格的列号
  * _**isVertical**_：指定数据是垂直导出还是水平导出

API 还提供了 _**importArray()**_ 方法的重载版本，用于将整数或双精度数组导出到工作表。

## 将二维数组导出到 Excel {#Export-Two-Dimensional-Array-to-Excel}

同样，您可以将**二维数组导出到 Excel 文件**。以下代码示例展示了**如何将二维数组导出到 Java 中的 Excel 文件**。

```
// 初始化工作簿对象
Workbook workbook = new Workbook();

// 获取工作表的引用
Worksheet worksheet = workbook.getWorksheets().get(0);

// 创建一个二维整数数组
int[][] array2D = { 
  { 1, 2 }, 
  { 3, 4 }, 
  { 5, 6 }, 
  { 7, 8 } 
};

// 将名称数组垂直导出到第一行和第一列
worksheet.getCells().importArray(array2D, 0, 0);

// 保存 Excel 文件
workbook.save("C:\\Files\\output.xlsx");
```

{{< figure align=center src="images/Export-Two-Dimensional-Array-to-Excel.jpg" alt="将二维数组导出到 Excel" caption="将二维数组导出到 Excel">}}
 

Cells 类提供了 **[importArray()][19]** 方法来将二维整数数组导出到工作表。 API 还提供了此方法的重载版本，用于将二维字符串数组或双精度数组导出到工作表中。

## 在 Java 中将 ArrayList 导出到 Excel {#Export-ArrayList-to-Excel-in-Java}

您可以按照以下步骤将数据从 ArrayList 导出到 Excel：

  * 创建 _[Workbook][13]_ 类的实例
  * 在 [_Worksheet_][14] 类的实例中获取工作表
  * 创建一个包含字符串值的数组列表
  * 使用数组列表调用 [_importArrayList()_][20] 方法
  * 通过调用_Workbook_类的_[save()][16]_方法保存输出文件

以下代码示例展示了**如何在**Java** 中将 ArrayList 导出到 Excel。

```
// 初始化工作簿对象
Workbook workbook = new Workbook();

// 获取工作表的引用
Worksheet worksheet = workbook.getWorksheets().get(0);

// 实例化 ArrayList 对象
ArrayList<String> list = new ArrayList<String>();

// 将几个名称作为字符串值添加到列表中
list.add("Laurence Chen");
list.add("Roman Korchagin");
list.add("Kyle Huang");
list.add("Tommy Wang");

// 在工作表的第一行和第一列垂直导出 ArrayList 的内容。 
worksheet.getCells().importArrayList(list, 0, 0, true);

// 保存 Excel 文件
workbook.save("C:\\Files\\Output.xlsx");
```

{{< figure align=center src="images/Export-ArrayList-to-Excel-in-Java.jpg" alt="用 Java 将数组列表导出到 Excel" caption="在 Java 中将 ArrayList 导出到 Excel">}}
 

Cells 类的 [**_importArrayList()_**][20] 方法将数据的 ArrayList 导出到工作表。它需要四个参数，包括数据的 ArrayList。其他参数是_firstRow_、_firstColumn_ 和_isVertical_。

## 在 Java 中将自定义对象的集合导出到 Excel {#Export-Collection-of-Custom-Objects-to-Excel-in-Java}

您可以按照以下步骤将数据从自定义对象集合导出到 Excel：

  * 创建 _[Workbook][13]_ 类的实例
  * 在 [_Worksheet_][14] 类的实例中获取工作表
  * 创建自定义对象的数组列表
  * 使用数组列表调用 [_importCustomObjects()_][22] 方法
  * 通过调用_Workbook_类的_[save()][16]_方法保存输出文件

以下代码示例展示了**如何将自定义对象的集合导出到 Java 中的 Excel**。

```
// 初始化一个新的工作簿
Workbook book = new Workbook();

// 获取工作表的引用
Worksheet sheet = book.getWorksheets().get(0);

// 定义人员的 ArrayList
List<Person> list = new ArrayList<Person>();

list.add(new Person("Mike", 25, "Software Engineer"));
list.add(new Person("Steve", 30, "Doctor"));
list.add(new Person("Billy", 35, "Teacher"));

// 我们只选择名称和年龄列，而不是全部，以导出到工作表         
sheet.getCells().importCustomObjects((Collection)list,
    new String[] { "Name", "Age" }, // propertyNames
    true, // isPropertyNameShown
    0, // firstRow
    0, // firstColumn
    list.size(), // Number of objects to be exported
    true, // insertRows
    null, // dateFormatString
    false); // convertStringToNumber

// 保存 Excel 文件
book.save("C:\\Files\\Output.xlsx");
```

{{< figure align=center src="images/Export-Collection-of-Custom-Objects-to-Excel-in-Java.jpg" alt="在 Java 中将自定义对象集合到 Excel" caption="在 Java 中将自定义对象集合到 Excel">}}
 

Cells 类的 [][22]**[_importCustomObjects_][22]()** 方法导出自定义对象列表并采用以下参数。 API 还提供了此方法的重载版本，它采用的参数更少。

  * _**list**_：自定义对象的集合
  * **_propertName_**：指定要导出的特定属性的名称。如果为null，则会导出对象的所有属性
  * **_isPropertyNameShown_**：表示是否将属性名称导出到第一行
  * **_firstRow_**：要导出的第一个单元格的行号
  * **_firstColumn_**：要导出的第一个单元格的列号
  * **_rowNumber_**：要导出的行数
  * **_insertRows_**：指示是否添加额外的行以适应数据
  * **_dataFormatString_**：单元格的日期格式字符串
  * **_convertStringToNumber_**：指示此方法是否会尝试将字符串转换为数字。

## 使用 Java 中的合并单元格将数据导出到 Excel {#Export-Data-to-Excel-with-Merged-Cells-in-Java}

您可以按照以下步骤将对象集合中的数据导出到包含合并单元格的工作表：

  * 创建 _[Workbook][13]_ 类的实例 with template file path
  * 在 [_Worksheet_][14] 类的实例中获取工作表
  * 创建对象的数组列表
  * 创建 _[ImportTableOptions][24]_ 类的实例
  * 使用数组列表调用 [_importCustomObjects()_][22] 方法
  * 通过调用_Workbook_类的_[save()][16]_方法保存输出文件

以下代码示例展示了如何将自定义对象的集合导出到 **Excel 工作表，其中包含 Java 中的合并单元格**。

```
// 打开现有工作簿。
Workbook workbook = new Workbook("C:\\Files\\SampleMergedTemplate.xlsx");

// 获取工作表的引用
Worksheet sheet = workbook.getWorksheets().get(0);

// 实例化 ArrayList 对象
List<Product> productList = new ArrayList<Product>();

// 创建产品集合
for (int i = 0; i < 3; i++)
{
  Product product = new Product(i, "Product - " + i);
    productList.add(product);
}

// 定义表导入选项
ImportTableOptions tableOptions = new ImportTableOptions();

// 将 CheckMergedCells 属性设置为 true
tableOptions.setCheckMergedCells(true);
tableOptions.setFieldNameShown(false);

// 将数据导出到 Excel 模板（第二行第一列）           
sheet.getCells().importCustomObjects((Collection)productList, 1, 0, tableOptions);

// 保存 Excel 文件
workbook.save("C:\\Files\\Output.xlsx", SaveFormat.XLSX);
```

{{< figure align=center src="images/Export-Data-to-Excel-with-Merged-Cells-in-Java-1024x434.jpg" alt="使用 Java 中的合并单元格将数据导出到 Excel" caption="使用 Java 中的合并单元格将数据导出到 Excel">}}
 

**[ImportTableOptions][24]** 类提供了几个用于将数据导出到单元格的选项。 **_setCheckMergedCells_** 表示是否检查合并单元格。 **_setFieldNameShown_** 属性指示是否应导出字段名称。

## 在 Java 中将行和列从一个 Excel 文件复制到另一个文件 {#Copy-Rows-and-Columns-from-one-Excel-file-to-Another-in-Java}

您可以按照以下提到的步骤以编程方式轻松地将行和列从一个 Excel 文件复制到另一个文件：

  * 创建 _[Workbook][13]_ 类的实例 with source workbook input file
  * 创建 _[Workbook][13]_ 类的实例 for destination workbook
  * 在 [_Worksheet_][14] 类的单独实例中获取源工作表和目标工作表
  * 使用源工作表单元格调用目标工作表的 _[copyRows()][26]_ 方法
  * 通过调用 _Workbook_ 类的 _[save()][16]_ 方法保存目标工作簿输出文件

以下代码示例展示了**如何使用 Java 将行和列从一个 Excel 文件复制到另一个文件**。

```
// 打开源excel文件。
Workbook srcWorkbook = new Workbook("C:\\Files\\Source_Workbook.xlsx");

// 实例化目标 excel 文件。
Workbook destWorkbook = new Workbook();

// 获取源工作簿的第一个工作表。
Worksheet srcWorksheet = srcWorkbook.getWorksheets().get(0);

// 获取目标工作簿的第一个工作表。
Worksheet desWorksheet = destWorkbook.getWorksheets().get(0);

// 将源工作簿第一个工作表的所有行复制到
// 目标工作簿的第一个工作表。
desWorksheet.getCells().copyRows(srcWorksheet.getCells(), 0, 0, srcWorksheet.getCells().getMaxDisplayRange().getRowCount());

// 保存excel文件。
destWorkbook.save("C:\\Files\\Destination_Workbook.xlsx");	
```

{{< figure align=center src="images/Copy-Rows-and-Columns-from-one-Excel-file-to-Another-in-Java-1024x430.jpg" alt="在 Java 中将行和列从一个 Excel 文件复制到另一个文件" caption="在 Java 中将行和列从一个 Excel 文件复制到另一个文件">}}
 

您可以将特定行从一个 Excel 文件复制到另一个文件。以下代码示例显示**如何使用 Java 将特定行从一个 Excel 文件复制到另一个文件**。

```
// 打开源excel文件。
Workbook srcWorkbook = new Workbook("C:\\Files\\Source_Workbook.xlsx");

// 实例化目标 excel 文件。
Workbook destWorkbook = new Workbook();

// 获取源工作簿的第一个工作表。
Worksheet srcWorksheet = srcWorkbook.getWorksheets().get(0);

// 获取目标工作簿的第一个工作表。
Worksheet desWorksheet = destWorkbook.getWorksheets().get(0);

// 将源工作簿的第二行复制到目标工作簿的第一行。
desWorksheet.getCells().copyRow(srcWorksheet.getCells(), 1, 0);

// 将源工作簿的第四行复制到目标工作簿的第二行。
desWorksheet.getCells().copyRow(srcWorksheet.getCells(), 3, 1);

// 保存excel文件。
destWorkbook.save("C:\\Files\\Destination_Workbook.xlsx");
```

{{< figure align=center src="images/Copy-Specific-Rows-and-Columns-from-one-Excel-file-to-Another-in-Java-1024x432.jpg" alt="在 Java 中将特定行和列从一个 Excel 文件复制到另一个文件" caption="在 Java 中将特定行和列从一个 Excel 文件复制到另一个文件">}}
 

**_[copyRows()][26]_** 方法复制整行的数据和格式。它将源工作表单元格与源行索引、目标行索引和复制的行号一起作为输入参数进行复制。 API 还提供了此方法的重载版本，以使用 [CopyOptions][29] 和 [PasteOptions][30] 复制行。

同样，您可以使用 [copyColumn()][31] 或 [copyColumns()][32] 方法将列数据从一个 Microsoft Excel 文档复制到另一个文档。

## 在 Java 中将 JSON 数据导出到 Excel {#Export-JSON-Data-to-Excel-in-Java}

您可以按照以下提到的步骤轻松地将数据从 JSON 文件导出到 Excel：

  * 创建 _[Workbook][13]_ 类的实例
  * 在 [_Worksheet_][14] 类的实例中获取工作表
  * 读取 JSON 文件
  * 创建 _[CellsFactory][33]_ 类的实例
  * 通过调用 _[createStyle()][34]_ 方法启动样式
  * 设置各种样式属性，如水平对齐、字体颜色等。
  * 创建 [JsonLayoutOptions][35] 类的实例
  * 使用样式对象设置标题样式
  * 将数组作为表属性设置为 true
  * 使用 JSON 输入和 _JsonLayoutOptions_ 调用 [_JsonUtility.importData()_][36] 方法
  * 通过调用_Workbook_类的_[save()][16]_方法保存输出文件

以下代码示例展示了**如何使用 Java 将数据从 JSON 文件导出到 Excel**。

```
// 实例化工作簿对象
Workbook workbook = new Workbook();
Worksheet worksheet = workbook.getWorksheets().get(0);

// 读取 JSON 文件
File file = new File("C:\\Files\\sample.json");
BufferedReader bufferedReader = new BufferedReader(new FileReader(file));
    String jsonInput = "";
    String tempString;
    while ((tempString = bufferedReader.readLine()) != null) {
      jsonInput = jsonInput + tempString; 
    }
    bufferedReader.close();

// 设置样式
CellsFactory factory = new CellsFactory();
Style style = factory.createStyle();
style.setHorizontalAlignment(TextAlignmentType.CENTER);
style.getFont().setColor(Color.getCyan());
style.getFont().setBold(true);

// 设置 JsonLayoutOptions
JsonLayoutOptions options = new JsonLayoutOptions();
options.setTitleStyle(style);
options.setArrayAsTable(true);

// 导出 JSON 数据
JsonUtility.importData(jsonInput, worksheet.getCells(), 0, 0, options);

// 保存 Excel 文件
workbook.save("C:\\Files\\Output.xlsx");
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

{{< figure align=center src="images/Export-JSON-Data-to-Excel-in-Java.jpg" alt="在 Java 中将 JSON 数据导出到 Excel" caption="在 Java 中将 JSON 数据导出到 Excel">}}
 

**[CellsFactory][33]** 类实例化 Cells 模型的类。这个类的 _[**createStyle()**][34]_ 方法创建了一个新的 **[Style][38]** 类的样式对象。 **Style** 类允许设置 Excel 文档的显示样式，如字体、颜色、对齐方式、边框等。

**[JsonLayoutOptions][35]** 类提供了 JSON 布局类型的选项。该类的**_setTitleStyle_** 方法用于设置标题的定义样式。 **_setArrayAsTable_** 方法允许将 Array 处理为表。

API 提供 **[JsonUtility][39]** 类来处理 JSON。该类的 [_**importData()**_][36] 方法导出 JSON 字符串，并采用以下参数：

  * **_json_**：JSON 字符串
  * **_cells_**：细胞
  * **_row_**：行索引
  * **_column_**：列索引
  * **_option_**：导出 JSON 字符串的选项

## 使用 Java 在 Excel 中获取 CSV 数据 {#Export-CSV-Data-to-Excel-in-Java}

您可以按照以下提到的简单步骤将数据从 CSV 文件导出到 Excel：

  * 使用 _[LoadFormat][41]_ 创建 _[LoadOptions][40]_ 类的实例
  * 创建 _[Workbook][13]_ 类的实例 with CSV file path and _LoadOptions_ object
  * 调用_Workbook_类的_[save()][16]_方法，保存输出文件

以下代码示例展示了**如何使用 Java 将数据从 CSV 文件导出到 Excel**。

```
// 使用 CSV LoadFormat 初始化 LoadOptions。
LoadOptions loadOptions = new LoadOptions(LoadFormat.CSV);

// 打开 CSV 文件作为工作簿对象
Workbook workbook = new Workbook("C:\\Files\\Sample.csv", loadOptions);

// 将文件另存为 Excel 文档
workbook.save("C:\\Files\\Output.xlsx");
```

```
id,language,edition,author,streetAddress,city,state,postalCode
01,Java,third,Herbert Schildt,126,San Jone,CA,394221
02,C++,second,EAAAA,126,San Jone,CA,394221
03,.Net,second,E.Balagurusamy,126,San Jone,CA,394221
```

{{< figure align=center src="images/Export-CSV-Data-to-Excel-in-Java-1024x662.jpg" alt="用 Java 将 CSV 数据导出到 Excel" caption="用 Java 将 CSV 数据导出到 Excel">}}
 

API 的 **[LoadOptions][40]** 类提供了加载文件的选项。 **[LoadFormat][41]** 类包含表示加载文件格式的常量。

## 获得免费许可证

您可以通过申请 [免费的临时许可证][43] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何在 Java 中将数据导出到 Excel**。您还学习了**如何以编程方式将数据从数组、JSON 或 CSV 文件导出到 Excel**。此外，您还学习了**如何使用 Java 将行和列从一个 Excel 文件复制到另一个文件**。您可以使用 [documentation][44] 了解有关 Aspose.Cells for Java API 的更多信息。如有任何歧义，请随时在 [论坛][45] 上与我们联系。

## 也可以看看

  * [使用 Java 在 Excel 中复制行和列][46]

## 经常问的问题

**如何在 Java 中将数据导出到 XLSX 文件？**
您可以在 Java 应用程序中使用易于集成的 Aspose.Cells for Java API 轻松地将数据从数组、对象集合、JSON 和 CSV 导出到 XLSX 文件。
    
**如何将数据从 JSON 导出到 Excel？**
Aspose.Cells API 提供 JsonUtility 以将数据从 JSON 文件导出到 Java 中的 Excel。您可以在 [Export JSON Data to Excel in Java](#Export-JSON-Data-to-Excel-in-Java) 部分下找到简单的步骤。
    
**如何在 Java 中将数据从 CSV 导出到 Excel？**
您可以使用 Aspose.Cells API 简单地加载 CSV 文件并将其保存为 XLSX。您可以在 [使用 Java 获取 Excel 中的 CSV 数据](#Export-CSV-Data-to-Excel-in-Java) 部分下找到简单的步骤。
    
 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/export-data-to-excel-in-java.jpg
 [2]: #Java-API-for-Exporting-Data
 [3]: #Export-Array-to-Excel-in-Java
 [4]: #Export-Two-Dimensional-Array-to-Excel
 [5]: #Export-ArrayList-to-Excel-in-Java
 [6]: #Export-Collection-of-Custom-Objects-to-Excel-in-Java
 [7]: #Export-Data-to-Excel-with-Merged-Cells-in-Java
 [8]: #Copy-Rows-and-Columns-from-one-Excel-file-to-Another-in-Java
 [9]: #Export-JSON-Data-to-Excel-in-Java
 [10]: #Export-CSV-Data-to-Excel-in-Java
 [11]: https://products.aspose.com/cells/java/
 [12]: https://downloads.aspose.com/cells/java
 [13]: https://apireference.aspose.com/cells/java/com.aspose.cells/Workbook
 [14]: https://apireference.aspose.com/cells/java/com.aspose.cells/Worksheet
 [15]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#importArray(java.lang.String[],%20int,%20int,%20boolean)
 [16]: https://apireference.aspose.com/cells/java/com.aspose.cells/workbook#save(java.lang.String)
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/Export-Array-to-Excel-in-Java.jpg
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/Export-Two-Dimensional-Array-to-Excel.jpg
 [19]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#importArray(int[][],%20int,%20int)
 [20]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#importArrayList(java.util.ArrayList,%20int,%20int,%20boolean)
 [21]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/Export-ArrayList-to-Excel-in-Java.jpg
 [22]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#importCustomObjects(java.util.Collection,%20java.lang.String[],%20boolean,%20int,%20int,%20int,%20boolean,%20java.lang.String,%20boolean)
 [23]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/Export-Collection-of-Custom-Objects-to-Excel-in-Java.jpg
 [24]: https://apireference.aspose.com/cells/java/com.aspose.cells/ImportTableOptions
 [25]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/Export-Data-to-Excel-with-Merged-Cells-in-Java.jpg
 [26]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#copyRows(com.aspose.cells.Cells,%20int,%20int,%20int)
 [27]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/Copy-Rows-and-Columns-from-one-Excel-file-to-Another-in-Java.jpg
 [28]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/Copy-Specific-Rows-and-Columns-from-one-Excel-file-to-Another-in-Java.jpg
 [29]: https://apireference.aspose.com/cells/java/com.aspose.cells/CopyOptions
 [30]: https://apireference.aspose.com/cells/java/com.aspose.cells/PasteOptions
 [31]: https://apireference.aspose.com/cells/java/com.aspose.cells/cells#copyColumn(com.aspose.cells.Cells,%20int,%20int)
 [32]: https://apireference.aspose.com/cells/net/aspose.cells/cells/methods/copycolumns
 [33]: https://apireference.aspose.com/cells/java/com.aspose.cells/CellsFactory
 [34]: https://apireference.aspose.com/cells/java/com.aspose.cells/cellsfactory#createStyle()
 [35]: https://apireference.aspose.com/cells/java/com.aspose.cells/JsonLayoutOptions
 [36]: https://apireference.aspose.com/cells/java/com.aspose.cells/jsonutility#importData(java.lang.String,%20com.aspose.cells.Cells,%20int,%20int,%20com.aspose.cells.JsonLayoutOptions)
 [37]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/Export-JSON-Data-to-Excel-in-Java.jpg
 [38]: https://apireference.aspose.com/cells/java/com.aspose.cells/Style
 [39]: https://apireference.aspose.com/cells/java/com.aspose.cells/jsonutility
 [40]: https://apireference.aspose.com/cells/java/com.aspose.cells/LoadOptions
 [41]: https://apireference.aspose.com/cells/java/com.aspose.cells/LoadFormat
 [42]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/Export-CSV-Data-to-Excel-in-Java.jpg
 [43]: https://purchase.aspose.com/temporary-license
 [44]: https://docs.aspose.com/cells/java/
 [45]: https://forum.aspose.com/c/cells/9
 [46]: https://blog.aspose.com/2021/06/15/copy-rows-and-columns-in-excel-using-java/








