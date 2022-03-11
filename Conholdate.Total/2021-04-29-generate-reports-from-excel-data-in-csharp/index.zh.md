---
title: "'在 C# 中从 Excel 数据生成报告'"
author: Muzammil Khan
date: 2021-04-29T06:18:58+00:00
summary: "您可以使用 Excel 电子表格作为数据表，以编程方式轻松生成自定义报告。本文将重点介绍**如何使用 C# 从 Excel 数据生成报告**。"
url: /zh/2021/04/29/generate-reports-from-excel-data-in-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "在 CSharp 中将 Excel 转换为 Word"
  - "使用 CSharp 将 Excel 数据转换为 Word"
  - "生成报告"
  - "生成报告 from Excel"
---

{{< figure align=center src="images/Generate-Reports-from-Excel-Data.jpg" alt="在 C# 中从 Excel 数据生成报告">}}
 
您可以从 Microsoft Excel 数据表轻松创建自定义报告。此类报告可以通过使用 Excel 电子表格作为数据表以编程方式生成。本文将重点介绍**如何使用 C# 从 Excel 数据生成报告**。

本文讨论/涵盖了以下主题：

  * [用于生成报告的 C# API][2]
  * [使用 C# 从 Excel 数据生成报告][3]

## 用于生成报告的 C# API {#api-for-generating-reports}

我将使用 [GroupDocs.Assembly for .NET][4] API 从 Excel 数据生成报告。它使您能够构建强大的文档自动化和报告生成应用程序。该 API 支持从 XML、JSON 和 CSV 等各种数据源获取数据。您可以轻松地生成所有常用文件格式的报告，例如 PDF、HTML 和 Microsoft Word。它可用于在任何面向 .NET 平台的开发环境中开发应用程序。

您可以[下载][5] API 的 DLL 或使用 [NuGet][6] 安装它。

```
Install-Package GroupDocs.Assembly
```

## 使用 C# 从 Excel 数据生成报告 {#generate-reports-from-excel}

您可以按照以下提到的简单步骤从 Excel 数据生成报告：

  1. 获取 [Excel 数据](#get-excel-data) 源。
  2. 根据 Excel 数据定义 [模板](#template)。
  3. 为[用于报告生成的简单C#代码]提供数据源和模板(#generate-excel-to-word-report)

### Excel 数据 {#get-excel-data}

Excel 电子表格中可用的表格数据可用作生成报告的数据源。我将使用以下示例 Excel 数据生成报告。这是客户与其各自经理的合同数据和约定的合同价格。

{{< figure align=center src="images/Excel_data_source.png" alt="Excel 数据源" caption="Excel 数据源">}}
 
### 模板 {#template}

现在，在 DOCX 文件中定义以下模板。这允许使用合约价格迭代合约的数据及其各自的管理者。之后，您可以跳转到生成报告的代码。

{{< figure align=center src="images/Template.jpg" alt="报告模板" caption="报告模板">}}
 
### 在 C# 中将 Excel 转换为 Word 报告 {#generate-excel-to-word-report}

请按照下面提到的步骤，自动将 Excel 数据转换为基于模板的 DOCX 报告。

  * 定义 Excel 数据文件、模板文件和 DOCX 输出报告文件路径
  * 定义_**[DocumentTableOptions][9]**_
  * 使用定义的 Excel 数据文件和 _DocumentTableOptions_ 创建 _**[DocumentTable][10]**_
  * 调用 [DocumentAssembler][12] 类的 _**[AssembleDocument][11]**_ 方法，根据提供的 Excel 数据和定义的模板生成报表

以下代码示例展示了如何使用 C# 根据定义的模板从 Excel 数据源生成报告。

```
string ExcelDataFile = "Contracts_Data.xlsx";
string strDocumentTemplate = "Template.docx";
string strDocumentReport = "Output.docx";

// 从 Excel 文件定义数据表
DocumentTableOptions options = new DocumentTableOptions 
{ 
    FirstRowContainsColumnNames = true 
};
DocumentTable table = new DocumentTable(ExcelDataFile, 0, options);

// 使用外部文档表作为数据源来组装文档。
DocumentAssembler assembler = new DocumentAssembler();
assembler.AssembleDocument(strDocumentTemplate, strDocumentReport,
    new DataSourceInfo(table, "contracts"));
```

上面的代码示例将生成以下报告。

{{< figure align=center src="images/output.jpg" alt="生成的报告" caption="生成的报告">}}
 
_**DocumentTableOptions**_ 类提供了一组选项来控制从文档表中提取数据。在这里，_FirstRowContainsColumnNames_ 属性设置为 _true_。

_**DocumentTable**_ 类提供对位于外部文档中的单个表（或电子表格）的数据的访问，以在组装文档时使用。

**_DocumentAssembler_** 类提供了基于带有数据的模板文档生成报告的方法。

## 获得免费许可证

您可以通过请求 [免费的临时许可证][14] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C# 从 Excel 数据生成报告**。您可以使用 [文档][15] 了解有关 .NET API 的 GroupDocs.Assembly 的更多信息。如有任何歧义，请随时在 [论坛][16] 上与我们联系。

## 也可以看看

  * [在 C# 中从 JSON 数据生成 PDF 和 Word 报告][17]
  * [使用 C# 从 CSV 或 XML 数据生成报告][18]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/Generate-Reports-from-Excel-Data.jpg
 [2]: #api-for-generating-reports
 [3]: #generate-reports-from-excel
 [4]: https://products.groupdocs.com/assembly/net
 [5]: https://downloads.groupdocs.com/assembly/net
 [6]: https://www.nuget.org/packages/GroupDocs.Assembly
 [7]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/Excel_data_source.png
 [8]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/Template.jpg
 [9]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly.data/documenttableoptions
 [10]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly.data/documenttable
 [11]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly.documentassembler/assembledocument/methods/2
 [12]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/documentassembler
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/04/output.jpg
 [14]: https://purchase.groupdocs.com/temporary-license
 [15]: https://docs.groupdocs.com/assembly/net/
 [16]: https://forum.groupdocs.com/c/assembly/
 [17]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/
 [18]: https://blog.groupdocs.com/2019/10/21/generate-reports-from-csv-xml-in-csharp/








