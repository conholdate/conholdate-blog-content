---
title: "在 Java 中从 Excel 数据生成报告"
author: Muzammil Khan
date: 2021-08-18T17:20:07+00:00
summary: "作为 Java 开发人员，您可以轻松地以编程方式从 Excel 数据生成自定义报告。在本文中，您将学习**如何使用 Java 从 Excel 数据生成报告**。"
url: /zh/2021/08/18/generate-reports-from-excel-data-in-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "生成报告"
  - "生成报告 from Excel"
  - "GroupDocs.Assembly 对于 Java"
  - "使用 Java 从 Excel 生成 Word 报告"

---


{{< figure align=center src="images/generate-reports-from-excel-data-in-java.jpg" alt="在 Java 中从 Excel 数据生成报告">}}
 

您可以将 Microsoft Excel 数据以自定义报告的形式呈现给您的用户，例如客户、利益相关者等。作为 Java 开发人员，您可以使用 Excel 电子表格作为数据表以编程方式生成此类报告。在本文中，您将学习**如何使用 Java 从 Excel 数据生成报告**。

本文讨论/涵盖了以下主题：

  * [用于生成报告的 Java API][2]
  * [使用 Java 从 Excel 数据生成报告][3]

## 用于生成报告的 Java API {#java-api-for-generating-reports}

为了从 Excel 数据生成报告，我将使用 [GroupDocs.Assembly for Java][4] API。它使您能够构建强大的文档自动化和报告生成应用程序。它根据定义的模板文档从数据源中获取数据，组装它，并以指定的输出格式生成报告。该 API 支持从 XML、Excel、JSON 和 CSV 等各种数据源获取数据。您可以轻松地生成所有常用文件格式的报告，例如 PDF、HTML 和 Microsoft Word。

您可以 [下载][5] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置，以尝试以下代码示例。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```

```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-assembly</artifactId>
        <version>21.7</version> 
</dependency>
```

## 使用 Java 从 Excel 数据生成报告 {#generate-reports-from-excel-in-java}

按照下面提到的简单步骤，您可以轻松地在 Word 中从 Excel 数据生成报告：

1. 获取[Excel数据源](#get-excel-data)
2. 根据Excel数据定义一个[模板](#template)
3. [Java 中将 Excel 数据转换为 Word 报告](#generate-excel-to-word-report)

### Excel 数据源 {#get-excel-data}

您可以使用表格数据作为 Excel 电子表格中提供的数据源来生成报告。我将使用以下示例 Excel 数据来生成报告。这是客户与其各自经理的合同数据和约定的合同价格。


{{< figure align=center src="images/Excel-Data-Source.jpg" alt="Excel 数据源" caption="Excel 数据源">}}
 

### 模板 {#template}

您可以使用基于 Linq 的模板语法来创建模板。模板由描述模板结构和数据绑定的通用文档内容和标签组成。您可以在 DOCX 或 XLSX 文件中定义以下模板。此模板使您能够使用合同价格迭代合同的数据及其各自的经理。模板中的每个组都有一个由输入选择器定义的唯一键，并包含与该键关联的源枚举项。您可以使用 Key 属性访问组实例的密钥。创建模板后，您可以跳转到生成报告的代码。您可以在文档中阅读有关 [模板语法][7] 的更多信息。

{{< figure align=center src="images/Report-Template.jpg" alt="报告模板" caption="报告模板">}}
 

### 在 Java 中将 Excel 数据转换为 Word 报告 {#generate-excel-to-word-report}

您可以按照以下步骤自动将 Excel 数据转换为基于模板的 DOCX 报告：

  * 定义 Excel 数据文件、模板文件和 DOCX 输出报告文件路径
  * 创建 _**[DocumentTableOptions][9]**_ 类的实例
  * 将 _**[setFirstRowContainsColumnNames][10]**_ 设置为 _true_
  * 使用定义的 Excel 数据文件和 _DocumentTableOptions_ 创建 _**[DocumentTable][11]**_
  * 创建 **[DocumentAssembler][12]** 类的实例
  * 使用提供的 Excel 数据和定义的模板调用 _**[assembleDocument()][13]**_ 方法

以下代码示例展示了如何使用 Java 根据定义的模板从 Excel 数据源生成报告。

```
String srcDocument = "C:\\Files\\template.docx";
String docReport = "C:\\Files\\Output.docx";
String dataFilePath = "C:\\Files\\Contracts_Data.xlsx";

// 设置从第一行提取列名。
DocumentTableOptions options = new DocumentTableOptions();
options.setFirstRowContainsColumnNames(true);

// 创建文档表
DocumentTable table = new DocumentTable(dataFilePath, 0, options);

// 创建文档汇编器
DocumentAssembler assembler = new DocumentAssembler();

// 收集数据并生成报告
assembler.assembleDocument(srcDocument,docReport, 
  new DataSourceInfo(new DataStorage(), null),
  new DataSourceInfo(table,"ds"));
```

{{< figure align=center src="images/output_report.jpg" alt="生成的报告" caption="生成的报告">}}
 

_**DocumentTableOptions**_ 类提供了一组选项来控制从文档表中提取数据。我将 _FirstRowContainsColumnNames _property 设置为 _true_，以便列标题不应该成为报告数据的一部分。

_**DocumentTable **_ 类提供对位于外部文档中的单个表（或电子表格）的数据的访问，以在组装文档时使用。

**_DocumentAssembler_** 类提供了各种方法来使用已定义的模板文档和数据生成报告。该类的 _assembleDocument**()**_ 方法接受三个输入参数，定义的模板作为源文档、输出文件路径和数据源。它根据提供的模板文档从数据源填充数据，并将生成的文档存储到目标路径。您可以将生成的文档保存为各种受支持的文件格式，例如 Word、Excel 或 HTML。

## 获得免费许可证

您可以通过请求 [免费的临时许可证][15] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 Java 从 Excel 数据生成报告**。您还学习了**如何创建报告模板以生成报告**。您可以使用 [文档][16] 了解有关 Java API 的 GroupDocs.Assembly 的更多信息。如有任何歧义，请随时在 [论坛][17] 上与我们联系。

## 也可以看看

  * [Java 中 CSV 的 PDF 和 Word 报告][18]
  * [在 Java 中从 XML 数据生成报告][19]
  * [从 Java 中的 JSON 数据生成 PDF 报告][20]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/generate-reports-from-excel-data-in-java.jpg
 [2]: #java-api-for-generating-reports
 [3]: #generate-reports-from-excel-in-java
 [4]: https://products.groupdocs.com/assembly/java
 [5]: https://downloads.groupdocs.com/assembly/java
 [6]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/Excel-Data-Source.jpg
 [7]: https://docs.groupdocs.com/assembly/java/template-syntax-part-1-of-2/
 [8]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/Report-Template.jpg
 [9]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DocumentTableOptions
 [10]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DocumentTableOptions#setFirstRowContainsColumnNames-boolean-
 [11]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DocumentTable
 [12]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DocumentAssembler
 [13]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DocumentAssembler#assembleDocument-java.lang.String-java.lang.String-com.groupdocs.assembly.DataSourceInfo...-
 [14]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/08/output_report.jpg
 [15]: https://purchase.groupdocs.com/temporary-license
 [16]: https://docs.groupdocs.com/assembly/java/
 [17]: https://forum.groupdocs.com/c/assembly/
 [18]: https://blog.groupdocs.com/2021/07/07/generate-reports-from-csv-data-in-java/
 [19]: https://blog.groupdocs.com/2021/07/10/generate-reports-from-xml-data-in-java/
 [20]: https://blog.groupdocs.com/2021/02/10/generate-pdf-report-from-json-data-in-java/








