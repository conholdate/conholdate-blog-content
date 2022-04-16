---
title: "'Fusionner les images JPG en PDF en utilisant C#'"
author: Muzammil Khan
date: 2022-03-21T06:43:17+00:00
summary: "Nous pouvons facilement convertir et combiner plusieurs images JPG en un seul document PDF par programmation en C#. Dans cet article, vous apprendrez **comment fusionner des images JPG dans un PDF à l'aide de C#**."
url: /fr/2022/03/21/merge-jpg-images-into-pdf-using-csharp/

categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "API C# pour fusionner JPG en PDF"
  - "Convertir JPG en PDF en C#"
  - "Fusionner JPG en PDF en utilisant C#"
  - "Combinez des images JPG en PDF à l'aide de C #"
  - "JPG en PDF"
  - "Fusionner JPG en PDF"
  - "Fusionner des images en PDF"
  - "Aspose.Imaging pour C#"
  - "GroupDocs.Merger pour .NET"
---

{{< figure align=center src="images/merge-jpg-images-into-pdf-using-csharp.jpg" alt="Fusionner JPG en PDF en utilisant C#">}}
 
[JPG][1] est le format de fichier image le plus largement utilisé pour stocker des images compressées. [PDF][2], d'autre part, permet de partager des documents dans un format en lecture seule sans compromettre leur style ou leur mise en page. Nous pouvons parfois avoir besoin de combiner de nombreuses photos JPG dans un document PDF. Dans cet article, nous allons apprendre **comment fusionner des images JPG dans un document PDF à l'aide de C#**.

Les sujets suivants seront traités dans cet article :

  * [API C# pour fusionner des images JPG en PDF][3]
  * [Convertir JPG en PDF en C#][4]
  * [Ajouter une image JPG au PDF en utilisant C #][5]
  * [Fusionner plusieurs images JPG en PDF à l'aide de C #][6]

## API C# pour fusionner des images JPG en PDF {#CSharp-API-to-Merge-JPG-Images-into-PDF}

Pour fusionner deux images JPG ou plus dans un document PDF, nous suivrons une procédure en deux étapes. Tout d'abord, nous utiliserons [Aspose.Imaging pour .NET][7] pour convertir JPG en PDF, puis nous les fusionnerons dans un document PDF à l'aide de l'API [GroupDocs.Merger pour .NET][8]. Veuillez soit [télécharger][9] les DLL pour les API ou les installer à l'aide de [NuGet][10].

```
PM> Install-Package Aspose.Imaging
PM> Install-Package GroupDocs.Merger
```

## Convertir JPG en PDF en C# {#Convert-JPG-to-PDF-in-CSharp}

Nous pouvons convertir n'importe quelle image JPG en un document PDF en suivant les étapes ci-dessous :

  1. Chargez une image JPG en utilisant la méthode _**[Image.Load()][11]**_.
  2. Enfin, appelez la méthode _**[Image.Save()][12]**_ pour enregistrer l'image au format PDF. Il prend le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment convertir un JPG en PDF à l'aide de C#**.

```
// Cet exemple de code montre comment convertir une image JPG en un document PDF.
// Charger l'image JPG
Image image = Image.Load(@"sample1.jpg");

// Enregistrer au format PDF
image.Save(@"converted.pdf");
```

{{< figure align=center src="images/Convert-JPG-to-PDF-in-CSharp.jpg" alt="Convertir JPG en PDF en C#." caption="Convertir JPG en PDF en C#.">}}

## Ajouter une image JPG au PDF en utilisant C# {#Append-JPG-Image-in-PDF-using-CSharp}

Nous pouvons ajouter une image JPG dans un document PDF existant en suivant les étapes ci-dessous :

  1. Chargez une image JPG en utilisant la méthode _**[Image.Load()][11]**_.
  2. Convertissez l'image chargée en PDF et enregistrez-la dans FileStream à l'aide de la méthode _**[Image.Save()][13]**_.
  3. Chargez un PDF existant à l'aide de la classe _**[Merger][14]**_.
  4. Appelez la méthode _**[Merger.Join()][15]**_ pour joindre le PDF converti en JPG avec le PDF chargé.
  5. Enfin, appelez la méthode _**[Merger.Save()][16]**_ pour enregistrer le PDF fusionné. Il prend le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment ajouter une image JPG dans un document PDF existant à l'aide de C#**.

```
// Cet exemple de code montre comment ajouter JPG dans un PDF existant.
// Charger l'image JPG
Image image = Image.Load(@"sample1.jpg");

// Convertir en PDF et enregistrer dans FileStream
FileStream fs = new FileStream("image.pdf", FileMode.Create);
image.Save(fs);

// Charger un PDF existant
Merger merger = new Merger(@"sample.pdf");

// Joindre le PDF converti en JPG avec le PDF chargé
merger.Join(fs);

// Enregistrer le PDF fusionné
merger.Save(@"Merged.pdf");
```

{{< figure align=center src="images/Append-JPG-Image-in-PDF-using-CSharp.jpg" alt="Ajouter une image JPG au PDF en utilisant C #." caption="Ajouter une image JPG au PDF en utilisant C #.">}}

## Fusionner plusieurs images JPG en PDF à l'aide de C # {#Merge-Multiple-JPG-Images-into-PDF-using-CSharp}

Nous pouvons fusionner plusieurs images JPG dans un document PDF en suivant les étapes ci-dessous :

  1. Lire tous les fichiers image JPG d'un répertoire un par un.
  2. Chargez une image JPG en utilisant la méthode _**[Image.Load()][11]**_.
  2. Convertissez la première image en PDF et enregistrez le fichier sur un disque local. Sinon, convertissez et enregistrez dans FileStream.
  3. Chargez le PDF précédemment enregistré à l'aide de la classe _**[Merger][14]**_.
  4. Appelez la méthode _**[Merger.Join()][15]**_ pour joindre le PDF converti en JPG avec le PDF chargé.
  5. Enfin, appelez la méthode _**[Merger.Save()][16]**_ pour enregistrer le PDF fusionné. Il prend le chemin du fichier de sortie comme argument.

L'exemple de code suivant montre **comment fusionner plusieurs images JPG dans un document PDF à l'aide de C#**.

```
// Cet exemple de code montre comment fusionner des images JPG dans un PDF.
int count = 0;
foreach (string fileName in Directory.GetFiles(@"D:\Files\Images\", "*.jpg"))
{
    // Load JPG image
    Image image = Image.Load(fileName);

    if (count == 0)
    {
        // Save PDF file
        image.Save(@"D:\Files\Images\converted.pdf");
        count = 1;   
    }
    else
    {
        // Convert to PDF and save in FileStream
        FileStream fs = new FileStream(fileName + ".pdf", FileMode.Create);
        image.Save(fs);

        // Merge
        using (Merger merger = new Merger(@"D:\Files\images\converted.pdf"))
        {
            merger.Join(fs);
            merger.Save(@"D:\Files\images\converted.pdf");
        }
    }
}
```

{{< figure align=center src="images/Merge-Multiple-JPG-Images-into-PDF-using-CSharp.jpg" alt="Fusionnez plusieurs images JPG en PDF à l'aide de C#." caption="Fusionnez plusieurs images JPG en PDF à l'aide de C#.">}}

## Obtenez une licence gratuite

Veuillez essayer l'API sans limitation d'évaluation en demandant [une licence temporaire gratuite][17].

## Conclusion

Dans cet article, nous avons appris à :
  * enregistrer l'image JPG en tant que document PDF en C# ;
  * insérer une image dans un document PDF par programmation ;
  * combiner plusieurs images dans un document PDF.
 
En outre, vous pouvez en savoir plus sur l'API Aspose.Imaging pour .NET en utilisant la [documentation][18]. En cas d'ambiguïté, n'hésitez pas à nous contacter sur le [forum][19].

## Voir également

  * [Recadrer et redimensionner les images JPEG à l'aide de C #][20]
  * [Fusionner des documents Word à l'aide de C#][21]

  [1]: https://docs.fileformat.com/image/jpeg/
  [2]: https://docs.fileformat.com/pdf/
  [3]: #CSharp-API-to-Merge-JPG-Images-into-PDF
  [4]: #Convert-JPG-to-PDF-in-CSharp
  [5]: #Append-JPG-Image-in-PDF-using-CSharp
  [6]: #Merge-Multiple-JPG-Images-into-PDF-using-CSharp
  [7]: https://products.aspose.com/imaging/net/
  [8]: https://products.groupdocs.com/merger/net/
  [9]: https://downloads.aspose.com/imaging/net
  [10]: https://www.nuget.org/packages/Aspose.Imaging/
  [11]: https://apireference.aspose.com/imaging/net/aspose.imaging.image/load/methods/2
  [12]: https://apireference.aspose.com/imaging/net/aspose.imaging.image/save/methods/3
  [13]: https://apireference.aspose.com/imaging/net/aspose.imaging.datastreamsupporter/save/methods/1
  [14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
  [15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/join
  [16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.merger/save/methods/1
  [17]: https://purchase.conholdate.com/temporary-license
  [18]: https://docs.aspose.com/imaging/net/
  [19]: https://forum.aspose.com/c/imaging/14
  [20]: https://blog.conholdate.com/2022/01/05/crop-and-resize-jpeg-images-using-csharp/
  [21]: https://blog.conholdate.com/2021/11/19/merge-word-documents-using-csharp/
