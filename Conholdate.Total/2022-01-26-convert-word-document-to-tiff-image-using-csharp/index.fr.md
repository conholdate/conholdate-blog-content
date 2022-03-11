---
title: "Convertir un document Word en image TIFF à l'aide de C#"
author: Muzammil Khan
date: 2022-01-26T07:56:46+00:00
summary: "En tant que développeur C#, vous pouvez facilement convertir vos documents Word en images TIFF multipages par programmation. Dans cet article, vous apprendrez **à convertir des documents Word en images TIFF à l'aide de C#** ."
url: /fr/2022/01/26/convert-word-document-to-tiff-image-using-csharp/
categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "Convertir Word en TIFF"
  - "Convertir Word en TIFF en C#"
  - "DOCX vers TIFF"
  - "DOCX vers TIFF en utilisant C#"
  - "Mot vers TIFF"
  - "Word en TIFF avec C#"

---

{{< figure align=center src="images/convert-word-document-to-tiff-image-using-csharp.jpg" alt="Convertir un document Word en image TIFF à l'aide de C #">}}
 
Nous pouvons facilement convertir des documents Word ([DOC][2] ou [DOCX][3]) en images raster. Les images raster sont capables de rendre des visuels complexes et multicolores. [TIFF][4] est un format populaire pour stocker des images raster. Il prend en charge l'enregistrement de plusieurs images sous forme de pages. Cette caractéristique distinctive du format TIFF en fait une option appropriée pour présenter les documents Word dans un format en lecture seule. Dans cet article, nous allons apprendre **comment convertir un document Word en image TIFF à l'aide de C#**.

Les sujets suivants seront traités dans cet article:

  * [API C# pour convertir Word en TIFF][5]
  * [Convertir un document Word en TIFF en C#][6]
  * [Personnaliser la conversion de Word en TIFF en C#][7]

## API C# pour convertir Word en TIFF {#CSharp-API-to-Convert-Word-to-TIFF}

Pour convertir **DOC en TIFF** ou **DOCX en TIFF**, nous utiliserons l'API [Aspose.Words pour .NET][8]. Il nous permet de générer, modifier, convertir, rendre et imprimer des fichiers sans utiliser Microsoft Word directement dans des applications multiplateformes. Veuillez soit [télécharger][9] la DLL de l'API ou l'installer à l'aide de [NuGet][10].

```
PM> Install-Package Aspose.Words
```

## Convertir un document Word en TIFF en C# {#Convert-Word-Document-to-TIFF-in-CSharp}

Nous pouvons convertir un document Word en un TIFF multipage en suivant les étapes ci-dessous:
  1. Chargez un document Word à l'aide de la classe _**[Document][11]**_.
  2. Enregistrez le document au format TIFF à l'aide de la méthode _**[Save()][12]**_. Il prend le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre comment convertir un document Word en TIFF à l'aide de C#.

```
// Cet exemple de code montre comment convertir DOCX en TIFF.
// Charger un document Word
Document doc = new Document("C:\\Files\\Document.docx");

// Convertir Word en TIFF
doc.Save("C:\\Files\\SaveWordAsTiff.tiff");
```

{{< figure align=center src="images/Convert-Word-Document-to-TIFF-in-CSharp-1024x611.jpg" alt="Convertir un document Word en TIFF en C#." caption="Convertir un document Word en TIFF en C#.">}}
 
## Personnaliser la conversion de Word en TIFF en C# {#Customize-Word-to-TIFF-Conversion-in-CSharp}

Nous pouvons utiliser différentes options pour personnaliser la conversion des documents Word en TIFF. A cet effet, l'API fournit la _classe _ImageSaveOptions. Il permet de régler la luminosité de l'image, la résolution, la plage de pages à convertir, le schéma de compression, etc. Veuillez suivre les étapes mentionnées ci-dessous pour définir des options supplémentaires lors de la conversion de Word en TIFF.

  1. Tout d'abord, chargez un document Word à l'aide de la classe [Document](https://apireference.aspose.com/words/net/aspose.words/Document">.
  2. Ensuite, créez une instance de la classe [ImageSaveOptions](https://apireference.aspose.com/words/net/aspose.words.saving/imagesaveoptions) avec le format d'image d'entrée comme argument.
  3. Après cela, définissez les options souhaitées telles que [TiffCompression](https://apireference.aspose.com/words/net/aspose.words.saving/imagesaveoptions/properties/tiffcompression), Résolution, etc.
  4. Enfin, appelez la méthode [Save(string, ImageSaveOptions)](https://apireference.aspose.com/words/net/aspose.words.document/save/methods/4) pour convertir Word en TIFF.

L'exemple de code suivant montre **comment convertir un document Word en image TIFF avec des options supplémentaires**.

```
// Cet exemple de code montre comment convertir DOCX en TIFF avec des options supplémentaires.
// Charger un document Word
Document doc = new Document("C:\\Files\\Document.docx");

// Créez un objet ImageSaveOptions à transmettre à la méthode Save
ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Tiff);

// Définir la ou les pages à afficher
options.PageSet = new PageSet(1);

// Appliquer la compression CCITT4
options.TiffCompression = TiffCompression.Ccitt4;

// Réglez la luminosité et le contraste de l'image.
// Les deux sont sur une échelle de 0 à 1 et sont à 0,5 par défaut.
options.ImageBrightness = 0.3f;
options.ImageContrast = 0.7f;

// Définissez à la fois la résolution horizontale et verticale pour 
// les images générées, en points par pouce.
// Définissez la propriété "Résolution" sur "72" pour rendre le document en 72dpi.
options.Resolution = 72;

// Convertir Word en TIFF
doc.Save("C:\\Files\\Convert_with_Options.tiff");
```

## Obtenez une licence gratuite
Veuillez essayer l'API sans limitation d'évaluation en demandant [une licence temporaire gratuite][14].

## Conclusion

Dans cet article, nous avons appris **comment convertir un document Word en une image TIFF à l'aide de C#**. Nous avons également vu comment appliquer des options supplémentaires telles que la compression et la résolution TIFF par programmation. En outre, vous pouvez en savoir plus sur l'API Aspose.Words pour .NET en utilisant la [documentation][15]. En cas d'ambiguïté, n'hésitez pas à nous contacter sur le [forum][16].

## Voir également

  * [Fusionner des documents Word à l'aide de C#][17]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/convert-word-document-to-tiff-image-using-csharp.jpg
 [2]: https://docs.fileformat.com/word-processing/doc/
 [3]: https://docs.fileformat.com/word-processing/docx/
 [4]: https://docs.fileformat.com/image/tiff/
 [5]: #CSharp-API-to-Convert-Word-to-TIFF
 [6]: #Convert-Word-Document-to-TIFF-in-CSharp
 [7]: #Customize-Word-to-TIFF-Conversion-in-CSharp
 [8]: https://products.aspose.com/words/net/
 [9]: https://downloads.aspose.com/words/net
 [10]: https://www.nuget.org/packages/aspose.words
 [11]: https://apireference.aspose.com/words/net/aspose.words/Document
 [12]: https://apireference.aspose.com/words/net/aspose.words.document/save/methods/2
 [13]: https://blog.conholdate.com/wp-content/uploads/sites/27/2022/01/Convert-Word-Document-to-TIFF-in-CSharp.jpg
 [14]: https://purchase.conholdate.com/temporary-license
 [15]: https://docs.aspose.com/words/net/
 [16]: https://forum.aspose.com/c/words
 [17]: https://blog.conholdate.com/2021/11/19/merge-word-documents-using-csharp/








