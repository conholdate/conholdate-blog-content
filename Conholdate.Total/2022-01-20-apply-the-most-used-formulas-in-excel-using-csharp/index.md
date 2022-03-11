---
title: 'Apply the Most Used Formulas in Excel using C#'
author: Muzammil Khan
date: 2022-01-20T10:41:26+00:00
summary: 'As a C# developer, you can easily execute Excel supported formulas in Excel sheets programmatically. In this article, you will learn **how to apply the most used formulas in Excel using C#**.'
url: /2022/01/20/apply-the-most-used-formulas-in-excel-using-csharp/
categories:
  - Conholdate.Total Product Family
tags:
  - Calculate Excel Formulas
  - Excel Formulas
  - 'Excel Formulas in C#'
  - Formula Calculation
  - 'Formulas in Excel using C#'
  - Most Used Formulas in Excel
  - 'Percentage Formula in C#'
---


{{< figure align=center src="images/most-used-formulas-in-excel-using-csharp.jpg" alt="Most Used Formulas in Excel using C#">}}
 
Excel is one of the most popular and widely used spreadsheet applications. It provides a built-in feature to apply various formulas/functions to process data. These formulae help to perform different types of calculations or computations. A formula is an expression that calculates the value of a cell. Excel also provides functions that are predefined formulas, which are readily available to use. In this article, we will learn **how to apply the most used formulas in Excel using C#**.

The following topics shall be covered in this article:

  * [C# API to Execute Most Used Formulas in Excel][2]
  * [Count Cells in Excel using C#][3]
  * [SUM Function in Excel using C#][4]
  * [Calculate Average in Excel using C#][5]
  * [IF Function in Excel using C#][6]
  * [Percentage Formula in Excel using C#][7]

## C# API to Execute Most Used Formulas in Excel {#CSharp-API-to-Execute-Most-Used-Formulas-in-Excel}

We will be using [Aspose.Cells for .NET][8] API for using the formulas in [XLSX][9] files. It supports a huge set of mathematical, string, boolean, date/time, statistical, database, lookup, and reference [formulas][10]. Please either [download][11] the DLL of the API or install it using [NuGet][12].

```
PM> Install-Package Aspose.Cells
```

## Count Cells in Excel using C# {#Count-Cells-in-Excel-using-CSharp}

The COUNT function counts the number of cells in a provided range that contains numbers. We can use the count formula programmatically by following the steps given below:

  1. Firstly, load an Excel file using the [Workbook][13] class.
  2. Next, access the [worksheet][14], either by its index (zero-based) or by name.
  3. Then, set the [formula][15] for a [cell][16] accessed by its name.
  4. After that, call the function [CalculateFormula()][17] to calculate formula results.
  5. Finally, save the Excel file using the [Save()][18] method. It takes output file path as an argument.

The following code sample shows **how to execute the COUNT** **formula in Excel using C#**.

{{< gist conholdate-gists 5371544c329f66b6868fcd29ff744782 "FormulasInExcel_CSharp_Count.cs" >}}

{{< figure align=center src="images/Count-Cells-in-Excel-using-CSharp-1024x618.jpg" alt="Count Cells in Excel using C#." caption="Count Cells in Excel using C#.">}}
 
Similarly, we can use the COUNTA function to count all the cells that are not empty. In this case, the COUNTA function shall return 10.

## SUM Function in Excel using C# {#SUM-Function-in-Excel-using-CSharp}

The SUM function in Excel sums all the values in a given range. Please follow the steps mentioned earlier to calculate the sum of values. However, we just need to set the SUM formula at step 3.

The following code sample shows **how to apply the SUM formula in Excel using C#**.

{{< gist conholdate-gists 5371544c329f66b6868fcd29ff744782 "FormulasInExcel_CSharp_Sum.cs" >}}

{{< figure align=center src="images/SUM-Function-in-Excel-using-CSharp-1024x674.jpg" alt="SUM Function in Excel using C#." caption="SUM Function in Excel using C#.">}}
 
## Calculate Average in Excel using C# {#Calculate-Average-in-Excel-using-CSharp}

We can calculate the average of the provided range of values in Excel using the AVERAGE function. Please follow the steps mentioned earlier to calculate the average of given values. However, we just need to set the AVERAGE formula at step 3.

The following code sample shows **how to calculate the average in Excel using C#**.

{{< gist conholdate-gists 5371544c329f66b6868fcd29ff744782 "FormulasInExcel_CSharp_Average.cs" >}}

{{< figure align=center src="images/Calculate-Average-in-Excel-using-CSharp-1024x654.jpg" alt="Calculate Average in Excel using C#." caption="Calculate the Average in Excel using C#.">}}
 

## IF Function in Excel using C# {#IF-Function-in-Excel-using-CSharp}

We can apply the IF function in Excel programmatically to check whether a condition is met or not. It returns one value if true and another value if false. Please follow the steps mentioned earlier to use the IF function. However, we just need to set the IF condition at step 3.

The following code sample shows **how to apply the IF function in Excel using C#**.

{{< gist conholdate-gists 5371544c329f66b6868fcd29ff744782 "FormulasInExcel_CSharp_IF.cs" >}}

{{< figure align=center src="images/IF-Function-in-Excel-using-CSharp.jpg" alt="IF Function in Excel using C#." caption="IF Function in Excel using C#.">}}
 

## Percentage Formula in Excel using C# {#Percentage-Formula-in-Excel-using-CSharp}

We can also apply the percentage formula in Excel using the basic percentage formula, e.g., **“(part/total)*100”**. Please follow the steps mentioned below to calculate the percentage in Excel.

  1. Firstly, create an instance of the [Workbook][13] class.
  2. Next, add a new [Worksheet][14] to the newly created Workbook.
  3. Then, access the added Worksheet either by its index (zero-based) or by name.
  4. Next, add values to the required [Cells][23] using the [PutValue][24] function.
  5. Then, set the percentage [formula][15] for a cell accessed by its name.
  6. After that, call the function [CalculateFormula()][17] to calculate formula results.
  7. Finally, save the Excel file using the [Save()][18] method. It takes output file path as an argument.

The following code sample shows **how to apply the percentage formula in Excel using C#**.

{{< gist conholdate-gists 5371544c329f66b6868fcd29ff744782 "FormulasInExcel_CSharp_Percentage.cs" >}}

{{< figure align=center src="images/Percentage-Formula-in-Excel-using-CSharp.jpg" alt="Percentage Formula in Excel using C#" caption="Percentage Formula in Excel using C#.">}}
 

## Get a Free License

Please try the API without evaluation limitations by requesting [a free temporary license][26].

## Conclusion

In this article, we have learned **how to apply the most used formulas in Excel using C#**. Specifically, we have learned **how to calculate SUM, Count, and Average in Excel** programmatically. We have also seen **how to apply the percentage formula in Excel**. Besides, you can learn more about Aspose.Cells for .NET API using the [documentation][27]. In case of any ambiguity, please feel free to contact us on the [forum][28].

## See Also

  * [Insert or Delete Rows and Columns in Excel using C#][29]

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






