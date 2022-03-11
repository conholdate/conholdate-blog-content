---
title: "Convertir PDF en HTML en utilisant Java"
author: Muzammil Khan
date: 2022-02-19T17:14:51+00:00
summary: "Vous pouvez facilement convertir vos documents PDF en pages Web HTML pour les afficher dans n'importe quel navigateur. Dans cet article, **vous apprendrez à convertir des documents PDF en pages Web HTML à l'aide de Java** ."
url: /fr/2022/02/19/convert-pdf-to-html-using-java/
categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "Convertir PDF en HTML"
  - "Convertir PDF en HTML Java API"
  - "GroupDocs.Conversion pour Java"
  - "Convertisseur Java PDF"
  - "PDF vers HTML"
  - "PDF vers HTML in Java"

---


{{< figure align=center src="images/convert-pdf-to-html-using-java.jpg" alt="Convertir PDF en HTML en utilisant Java">}}
 

[PDF][2] propose de partager et d'imprimer des documents en lecture seule sans perdre la mise en forme des documents. Nous pouvons facilement convertir des documents PDF en pages Web [HTML][3] et les afficher dans n'importe quel navigateur. Dans cet article, nous allons apprendre **comment convertir des documents PDF en pages Web HTML à l'aide de Java**.
Les sujets suivants seront traités dans cet article:
  * [API Java pour convertir PDF en HTML — Téléchargement gratuit][4]
  * [Conversion PDF en HTML avec Java][5]
  * [Convertir une plage de pages de PDF en HTML][6]
  * [Convertir des pages spécifiques de PDF en HTML][7]
  * [Conversion PDF en HTML protégée par mot de passe en Java][8]
  * [Conversion PDF en HTML avec filigrane en Java][9]

## API Java pour convertir PDF en HTML — Téléchargement gratuit {#Java-API-to-Convert-PDF-to-HTML—Free-Download}

Pour convertir le PDF en HTML, nous utiliserons l'API [GroupDocs.Conversion for Java][10]. Il fournit des solutions de conversion de fichiers rapides, efficaces et fiables aux utilisateurs finaux. Veuillez soit [télécharger][11] le JAR de l'API ou simplement ajouter la configuration **_pom.xml_** suivante dans une application Java basée sur Maven.
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
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.10.1</version> 
</dependency>
```

## Conversion PDF en HTML avec Java {#PDF-to-HTML-Conversion-using-Java}

Nous pouvons facilement convertir des documents PDF en pages Web HTML par programmation en suivant les étapes simples indiquées ci-dessous:
  1. Tout d'abord, chargez un document PDF à l'aide de la classe **_[Converter][12]_**.
  2. Ensuite, créez une instance de la classe [**_MarkupConvertOptions_**][13].
  3. Ensuite, définissez éventuellement diverses options de conversion telles que _FixedLayout_, _FixedLayoutShowBorders_, etc.
  4. Enfin, convertissez PDF en HTML en utilisant la _**[Converter.Convert()][14]**_ method. Il prend le chemin du fichier de sortie et convertit les options en arguments.

L'exemple de code suivant montre **comment convertir un document PDF en une page Web HTML à l'aide de Java**.

```
// Cet exemple de code montre comment convertir un document PDF en fichier HTML.
// Initialiser l'objet de classe Convertir
Convertirer converter = new Convertirer("C:\\Files\\Conversion\\sample.pdf");

// Définir les options de conversion
MarkupConvertirOptions options = new MarkupConvertirOptions();
options.setFixedLayout(true);

// Convertir
String outputFile =  "C:\\Files\\Conversion\\sample.html";
converter.convert(outputFile, options);
```

{{< figure align=center src="images/PDF-to-HTML-Conversion-using-Java-1024x512.jpg" alt="Conversion PDF en HTML avec Java" caption="Conversion PDF en HTML en utilisant Java.">}}
 

## Convertir une plage de pages de PDF en HTML {#Convert-Range-of-Pages-from-PDF-to-HTML}

Nous pouvons convertir une plage de pages d'un document PDF en HTML en suivant les étapes ci-dessous:
  1. Tout d'abord, chargez un document PDF à l'aide de la classe **_[Converter][12]_**.
  2. Ensuite, créez une instance de la classe [**_MarkupConvertOptions_**][13].
  3. Ensuite, définissez le numéro de page à partir duquel commencer la conversion.
  4. Après cela, définissez le nombre de pages pour convertir le nombre total de pages.
  5. Enfin, convertissez PDF en HTML en utilisant la _**[Converter.Convert()][14]**_ method.

L'exemple de code suivant montre ****comment convertir **une plage de pages d'un document PDF** en un fichier HTML** à l'aide de Java**.

```
// Cet exemple de code montre comment convertir une plage de pages PDF en fichier HTML.
// Initialiser l'objet de classe Convertir
Convertirer converter = new Convertirer("C:\\Files\\Conversion\\sample.pdf");

// Définir les options de conversion
MarkupConvertirOptions options = new MarkupConvertirOptions();
options.setPageNumber(1);	// Starting page number
options.setPagesCount(2);	// Total number of pages to convert

// Convertir
String outputFile =  "C:\\Files\\Conversion\\sample_N_pages.html";
converter.convert(outputFile, options);
```

## Convertir des pages spécifiques de PDF en HTML {#Convert-Specific-Pages-of-PDF-to-HTML}

Nous pouvons convertir des pages spécifiques d'un document PDF en HTML en suivant les étapes ci-dessous:
  1. Tout d'abord, chargez un document PDF à l'aide de la classe **_[Converter][12]_**.
  2. Ensuite, créez une instance de la classe [**_MarkupConvertOptions_**][13].
  3. Ensuite, fournissez des numéros de page spécifiques dans une liste séparée par des virgules à convertir.
  4. Enfin, convertissez PDF en HTML en utilisant la _**[Converter.Convert()][14]**_ method.

L'exemple de code suivant montre ****comment convertir **des pages spécifiques d'un document PDF** en un fichier HTML** à l'aide de Java**.

```
// Cet exemple de code montre comment convertir des pages spécifiques d'un document PDF en fichier HTML.
// Initialiser l'objet de classe Convertir
Convertirer converter = new Convertirer("C:\\Files\\Conversion\\sample.pdf");

// Définir les options de conversion
MarkupConvertirOptions options = new MarkupConvertirOptions();
options.setPages(Arrays.asList( 1, 3)); // Page numbers to convert

// Convertir
String outputFile =  "C:\\Files\\Conversion\\sample_pages.html";
converter.convert(outputFile, options);
```

## Convertir un PDF protégé par mot de passe en HTML en Java {#Convert-Password-Protected-PDF-to-HTML-in-Java}

Nous pouvons également convertir des documents PDF protégés par mot de passe en pages Web HTML en suivant les étapes ci-dessous:

  1. Tout d'abord, fournissez un mot de passe à l'aide de l'objet _**[PdfLoadOptions ][16]**_ class.
  2. Ensuite, chargez un document PDF en utilisant la classe **_[Converter][12]_** avec _**PdfLoadOptions**_.
  3. Créez ensuite une instance de la classe [**_MarkupConvertOptions_**][13].
  4. Enfin, convertissez PDF en HTML en utilisant la _**[Converter.Convert()][14]**_ method.

L'exemple de code suivant montre **comment convertir un document PDF protégé par mot de passe en document HTML à l'aide de Java**.

```
// Cet exemple de code montre comment convertir un PDF protégé par mot de passe en HTML.
// Définir les options de chargement
PdfLoadOptions loadOptions = new PdfLoadOptions();
loadOptions.setPassword("12345");

// Initialiser l'objet de classe Convertir
Convertirer converter = new Convertirer("C:\\Files\\Conversion\\sample.pdf", loadOptions);

// Définir les options de conversion
MarkupConvertirOptions options = new MarkupConvertirOptions();

// Convertir
String outputFile =  "C:\\Files\\Conversion\\sample.html";
converter.convert(outputFile, options);
```

## Conversion PDF en HTML avec filigrane en Java {#PDF-to-HTML-Conversion-with-Watermark-in-Java}

Nous pouvons convertir des documents PDF en pages Web HTML et ajouter des filigranes aux fichiers HTML convertis en suivant les étapes ci-dessous:

  1. Tout d'abord, chargez un document PDF à l'aide de la classe **_[Converter][12]_**.
  2. Ensuite, créez une instance de la classe _**[WatermarkOptions][17]**_.
  3. Ensuite, définissez diverses options telles que _Text_, _Color_, _Width_, _Height_, _Font_, etc.
  4. Ensuite, créez une instance de la classe [**_MarkupConvertOptions_**][13].
  5. Après cela, attribuez _**WatermarkOptions**_ à **_MarkupConvertOptions_**.
  6. Enfin, convertissez PDF en HTML en utilisant la _**[Converter.Convert()][14]**_ method.

L'exemple de code suivant montre **comment convertir un document PDF en un document HTML avec un filigrane**.

```
// Cet exemple de code montre comment convertir un PDF en HTML avec filigrane.
// Initialiser l'objet de classe Convertir
Convertirer converter = new Convertirer("C:\\Files\\Conversion\\sample.pdf");

// Définir le filigrane 
WatermarkOptions watermark = new WatermarkOptions();
watermark.setText("This is a Sample watermark");
watermark.setColor(Color.red);
watermark.setWidth(500);
watermark.setHeight(100);
watermark.setTop(0);
watermark.setLeft(300);
watermark.setBackground(true);

// Définir les options de conversion
MarkupConvertirOptions options = new MarkupConvertirOptions();
options.setWatermark(watermark);

// Chemin du fichier de sortie
String outputFile =  "C:\\Files\\Conversion\\sampleWithWatermark.html";

// Convertir
converter.convert(outputFile, options);
```

{{< figure align=center src="images/PDF-to-HTML-Conversion-with-Watermark-in-Java-1024x512.jpg" alt="Conversion PDF en HTML avec filigrane en Java" caption="Conversion PDF en HTML avec filigrane en Java.">}}
 

## Obtenez une licence gratuite

Veuillez essayer l'API sans limitation d'évaluation en demandant [une licence temporaire gratuite][19].

## Conclusion

Dans cet article, nous avons appris **comment convertir des documents PDF en pages Web HTML en Java**. Nous avons également vu **comment convertir un fichier PDF protégé par mot de passe en HTML et ajouter un filigrane au fichier converti** par programmation. En outre, vous pouvez en savoir plus sur l'API GroupDocs.Conversion pour Java en utilisant la [documentation][20]. En cas d'ambiguïté, n'hésitez pas à nous contacter sur le [forum][21].

## Voir également

  * [Convertir HTML en PDF en utilisant Java][22]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/convert-pdf-to-html-using-java.jpg
 [2]: https://docs.fileformat.com/pdf/
 [3]: https://docs.fileformat.com/web/html/
 [4]: #Java-API-to-Convert-PDF-to-HTML—Free-Download
 [5]: #PDF-to-HTML-Conversion-using-Java
 [6]: #Convert-Range-of-Pages-from-PDF-to-HTML
 [7]: #Convert-Specific-Pages-of-PDF-to-HTML
 [8]: #Convert-Password-Protected-PDF-to-HTML-in-Java
 [9]: #PDF-to-HTML-Conversion-with-Watermark-in-Java
 [10]: https://products.groupdocs.com/conversion/java
 [11]: https://downloads.groupdocs.com/conversion/java
 [12]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
 [13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/markupconvertoptions
 [14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
 [15]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/PDF-to-HTML-Conversion-using-Java.jpg
 [16]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.load/PdfLoadOptions
 [17]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/WatermarkOptions
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/02/PDF-to-HTML-Conversion-with-Watermark-in-Java.jpg
 [19]: https://purchase.conholdate.com/temporary-license
 [20]: https://docs.groupdocs.com/conversion/java/
 [21]: https://forum.groupdocs.com/c/conversion/11
 [22]: https://blog.conholdate.com/2021/09/10/convert-html-to-pdf-using-java/