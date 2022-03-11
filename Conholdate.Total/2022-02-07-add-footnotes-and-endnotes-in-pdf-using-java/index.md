---
title: Add Footnotes and Endnotes in PDF using Java
author: Muzammil Khan
date: 2022-02-07T07:18:39+00:00
summary: ' As a Java developer, you can add footnotes/endnotes to the PDF documents programmatically. In this article, you will learn **how to add footnotes and endnotes in PDF documents using Java**.'
url: /2022/02/07/add-footnotes-and-endnotes-in-pdf-using-java/
categories:
  - Conholdate.Total Product Family
tags:
  - Add Footnote to PDF in Java
  - Add Footnotes in PDF
  - Add Footnotes in PDF using Java
  - Add Image to Footnote using Java
  - Add Table to Footnote using Java

---


{{< figure align=center src="images/add-footnotes-and-endnotes-in-pdf-using-java.jpg" alt="Add Footnotes and Endnotes in PDF using Java.">}}
 
A footnote is a note or text given at the bottom of a specific page, whereas, the endnote is a note placed at the end of a document. We usually use footnotes or endnotes for references, explanations, or comments in the document. We can add footnotes/endnotes to the PDF document programmatically. In this article, we will learn **how to add footnotes and endnotes in PDF documents using Java**.

The following topics shall be covered in this article:

  - [Java API to Add Footnotes and Endnotes in PDF](#Java-API-to-Add-Footnotes-and-Endnotes-in-PDF")
  - [Add Footnotes to a PDF using Java](#Add-Footnotes-to-a-PDF-using-Java)
  - [Add an Image to Footnote in PDF](#Add-an-Image-to-Footnote-in-PDF)
  - [Insert a Table to Footnote in PDF](#Insert-a-Table-to-Footnote-in-PDF)
  - [Customize Footnote Label and Line Style using Java](#Customize-Footnote-Label-and-Line-Style-using-Java)
  - [Add Footnotes to Existing PDF using Java](#Add-Footnotes-to-Existing-PDF-using-Java)
  - [Add Endnotes to PDF using Java](#Add-Endnotes-to-PDF-using-Java)
 
## Java API to Add Footnotes and Endnotes in PDF {#Java-API-to-Add-Footnotes-and-Endnotes-in-PDF}

For adding footnotes and endnotes to a [PDF][2] document, we will be using [Aspose.PDF for Java API][3]. It allows us to generate, modify, convert, render, secure and print [supported documents][4] without using Adobe Acrobat. Please either [download][5] the JAR of the API or just add the following **_pom.xml_** configuration in a Maven-based Java application.

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
    <artifactId>aspose-pdf</artifactId>
    <version>22.1</version>
</dependency>
```

## Add Footnotes to a PDF using Java {#Add-Footnotes-to-a-PDF-using-Java}

We can add footnotes at the end of the page in a PDF document by following the steps given below:

  1. Firstly, create an instance of the [**_Document_**][6] class.
  2. Next, add a **_[Page][7]_** to the **_[PagesCollection][8]_** of the document.
  3. Then, create a **_[TextFragment][9]_**.
  4. Next, set the **_[Footnote][10]_** value for the _TextFragment_ object.
  5. Then, add _TextFragment_ to **[_Paragraphs_][11]** collection
  6. Optionally, repeat above steps to add more _TextFragments_ for multiple _Footnote_ values.
  7. Finally, save the PDF file using the **_[Document.Save()][12]_** method. It takes the path of the output file as an argument.

The following code sample shows **how to add footnotes to a PDF document using Java**.

{{< gist conholdate-gists a43bc0add392b88d80f53a8a96598da4 "FootnotesAndEndnotesInPDF_Java_AddFootnotes.java" >}}

{{< figure align=center src="images/Add-Footnotes-to-a-PDF-using-Java.jpg" alt="Add Footnotes to a PDF using Java." caption="Add Footnotes to a PDF using Java.">}}
 

## Add an Image to Footnote in PDF {#Add-an-Image-to-Footnote-in-PDF}

We can add an image in the footnotes of a PDF document by following the steps given below:

  1. Firstly, create an instance of the [**_Document_**][6] class.
  2. Next, add a **_[Page][7]_** to the **_[PagesCollection][8]_** of the document.
  3. Then, create a **_[TextFragment][9]_**.
  4. Next, set the **_[Footnote][10]_** value for the _TextFragment_ object.
  5. Then, add an image to the _TextFragment_ object.
  6. After that, add _TextFragment_ to **[_Paragraphs_][11]** collection
  7. Finally, save the PDF file using the **_[Document.Save()][12]_** method. It takes the path of the output file as an argument.

The following code sample shows **how to add an image in the footnotes of a PDF document using Java**.

{{< gist conholdate-gists a43bc0add392b88d80f53a8a96598da4 "FootnotesAndEndnotesInPDF_Java_ImageInFootnotes.java" >}}

{{< figure align=center src="images/Add-an-Image-to-Footnote-in-PDF-1024x972.jpg" alt="" caption="Add an Image to Footnote in PDF.">}}
 

## Insert a Table to Footnote in PDF {#Insert-a-Table-to-Footnote-in-PDF}

We can also add a table in the footnotes of a PDF document by following the steps given below:

  1. Firstly, create an instance of the [**_Document_**][6] class.
  2. Next, add a **_[Page][7]_** to the **_[PagesCollection][8]_** of the document.
  3. Then, create a **_[TextFragment][9]_**.
  4. Next, set the **_[Footnote][10]_** value for the _TextFragment_ object.
  5. Then, add a **_[table][15]_** to the _TextFragment_ object.
  6. After that, add _TextFragment_ to **[_Paragraphs_][11]** collection
  7. Finally, save the PDF file using the **_[Document.Save()][12]_** method. It takes the path of the output file as an argument.

The following code sample shows **how to add a table in the footnotes of a PDF document using Java**.

{{< gist conholdate-gists a43bc0add392b88d80f53a8a96598da4 "FootnotesAndEndnotesInPDF_Java_TableInFootnotes.java" >}}

{{< figure align=center src="images/Insert-a-Table-to-Footnote-in-PDF.jpg" alt="Insert a Table to Footnote in PDF." caption="Insert a Table to Footnote in PDF.">}}
 

## Customize Footnote Label and Line Style using Java {#Customize-Footnote-Label-and-Line-Style-using-Java}

We can customize the label of footnotes and footnote line style in a PDF document by following the steps given below:

  1. Firstly, create an instance of the [**_Document_**][6] class.
  2. Next, add a **_[Page][7]_** to the **_[PagesCollection][8]_** of the document.
  3. Then, initialize a **_[GraphInfo][17]_** object to customize the line style.
  4. Set GraphInfo object properties such as LineWidth, Color, DashArray, etc.
  5. Next, create a **_[TextFragment][9]_**.
  6. Then, set the **_[Footnote][10]_** value for the _TextFragment_ object.
  7. Next, initialize TextState object and set various properties e.g., ForegroundColor, FontStyle, etc.
  8. After that, add _TextFragment_ to **[_Paragraphs_][11]** collection
  9. Optionally, repeat above steps to add more _TextFragments_ for multiple _Footnote_ values.
 10. Finally, save the PDF file using the **_[Document.Save()][12]_** method. It takes the path of the output file as an argument.

The following code sample shows **how to add customize the footnotes label and line style using Java**.

{{< gist conholdate-gists a43bc0add392b88d80f53a8a96598da4 "FootnotesAndEndnotesInPDF_Java_CustomizeFootnotes.java" >}}

{{< figure align=center src="images/Customize-Footnote-Label-and-Line-Style-using-Java.jpg" alt="Customize Footnote Label and Line Style using Java." caption="Customize Footnote Label and Line Style using Java.">}}
 

## Add Footnotes to Existing PDF using Java {#Add-Footnotes-to-Existing-PDF-using-Java}

We can add footnotes to an existing PDF document by following the steps given below:

  1. Firstly, load a PDF file using the [**_Document_**][6] class.
  2. Next, get a particular **_[page][7]_** by its index.
  3. Then, create a **_[TextFragmentAbsorber][19]_** object with search phrase as input.
  4. After that, call the [_**accept()**_][20] method to search the input phrase from the page.
  5. Next, get the first occurrence of search phrase from _**[TextFragmentCollection][21]**_.
  6. Then, create an empty **_TextFragment_** and set its position on the page. 
  7. Also, set the **_[Footnote][10]_** value for the _TextFragment_ object.
  8. After that, add _TextFragment_ to **[_Paragraphs_][11]** collection
  9. Finally, save the PDF file using the **_[Document.Save()][12]_** method. It takes the path of the output file as an argument.

The following code sample shows **how to add footnotes to an existing PDF document using Java**.

{{< gist conholdate-gists a43bc0add392b88d80f53a8a96598da4 "FootnotesAndEndnotesInPDF_Java_AddFootnotesInExistingPDF.java" >}}

{{< figure align=center src="images/Add-Footnotes-to-Existing-PDF-using-Java-1024x970.jpg" alt="Add-Footnotes-to-Existing-PDF-using-Java" caption="Add Footnotes to Existing PDF using Java.">}}
 

## Add Endnotes to PDF using Java {#Add-Endnotes-to-PDF-using-Java}

We can also add endnotes at the end of a PDF document by following the steps given below:

  1. Firstly, create an instance of the [**_Document_**][6] class.
  2. Next, add a **_[Page][7]_** to the **_[PagesCollection][8]_** of the document.
  3. Then, create a **_[TextFragment][9]_**.
  4. Next, set the **_[Endnote][10]_** value for the _TextFragment_ object.
  5. Optionally, set a custom label for the Endnote.
  6. After that, add _TextFragment_ to **[_Paragraphs_][11]** collection.
  7. Finally, save the PDF file using the **_[Document.Save()][12]_** method. It takes the path of the output file as an argument.

The following code sample shows **how to add endnotes to a PDF document using Java**.

{{< gist conholdate-gists a43bc0add392b88d80f53a8a96598da4 "FootnotesAndEndnotesInPDF_Java_AddEndnotes.java" >}}

## Get a Free API License {#Get-a-Free-License}

You can try the API without evaluation limitations by requesting [a free temporary license][23].

## Conclusion

In this article, we have learned how to:

  * add footnotes and endnotes to a PDF document using Java;
  * add an image or a table to footnotes in PDF;
  * customize the label of footnote and line style using Java;
  * add footnotes to an existing PDF document using Java.

Besides, you can learn more about Aspose.PDF for Java API using the [documentation][24]. In case of any ambiguity, please feel free to contact us on the [forum][25].

## See Also

  * [Convert PDF to Word using Java][26]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/add-footnotes-and-endnotes-in-pdf-using-java.jpg
 [2]: https://docs.fileformat.com/pdf/
 [3]: https://products.aspose.com/pdf/java/
 [4]: https://docs.aspose.com/pdf/net/supported-file-formats/
 [5]: https://downloads.aspose.com/pdf/java
 [6]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/document
 [7]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Page
 [8]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/PageCollection
 [9]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/TextFragment
 [10]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Note
 [11]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Paragraphs
 [12]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Document#save-java.lang.String-
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Add-Footnotes-to-a-PDF-using-Java.jpg
 [14]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Add-an-Image-to-Footnote-in-PDF.jpg
 [15]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Table
 [16]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Insert-a-Table-to-Footnote-in-PDF.jpg
 [17]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/GraphInfo
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Customize-Footnote-Label-and-Line-Style-using-Java.jpg
 [19]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/TextFragmentAbsorber
 [20]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/Page#accept-com.aspose.pdf.TextFragmentAbsorber-
 [21]: https://apireference.aspose.com/pdf/java/com.aspose.pdf/TextFragmentCollection
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/Add-Footnotes-to-Existing-PDF-using-Java.jpg
 [23]: https://purchase.conholdate.com/temporary-license
 [24]: https://docs.aspose.com/pdf/java
 [25]: https://forum.aspose.com/c/pdf/10
 [26]: https://blog.conholdate.com/2021/07/26/convert-pdf-to-word-using-java/






