---
title: "'Rendre la présentation PowerPoint à l'aide de C#'"
author: Muzammil Khan
date: 2022-03-29T06:43:17+00:00
summary: "En tant que développeur C#, vous pouvez facilement restituer ou afficher par programmation des présentations PowerPoint (PPT/PPTX) dans des documents HTML ou PDF. Dans cet article, vous apprendrez **comment rendre une présentation PowerPoint à l'aide de C#**."
url: /fr/2022/03/29/rendre-présentation-powerpoint-en-utilisant-csharp/

categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "API C# pour afficher PPTX"
  - "Visionneuse PPTX"
  - "Lecteur PPTX C#"
  - "Visionneuse PowerPoint en C#"
  - "Convertir PPTX en PDF en C#"
  - "Convertir PPTX en HTML en utilisant C#"
  - "Rendu PowerPoint"
  - "PPTX en PDF"
  - "PPTX vers HTML"
  - "Convertir des diapositives PPTX en JPG"
  - "GroupDocs.Viewer pour .NET"
---

{{< figure align=center src="images/render-powerpoint-presentation-using-csharp.jpg" alt="Rendre une présentation PowerPoint en utilisant C#">}}
 
MS PowerPoint permet de présenter des informations ou des données sous forme de diapositives de présentation. Il fournit également une visionneuse PowerPoint pour afficher toutes les diapositives sous forme de diaporama. Dans certains cas, nous pouvons avoir besoin de rendre des diapositives de présentation PowerPoint dans d'autres formats tels que [PDF][1], [JPG][2] images ou [HTML][3]. Dans cet article, nous allons apprendre **comment rendre une présentation PowerPoint dans d'autres formats à l'aide de C#**.

Les sujets suivants seront traités dans cet article :

  * [API C # pour rendre la présentation PowerPoint][4]
  * [Rendre la présentation PowerPoint en PDF][5]
  * [Voir la présentation PowerPoint en HTML][6]
  * [Rendu des notes PowerPoint en HTML][28]
  * [Convertir des diapositives PowerPoint en images JPG][7]

## API C # pour rendre la présentation PowerPoint {#CSharp-API-to-Render-PowerPoint-Presentation}

Pour le rendu des fichiers [PPT][8] ou [PPTX][9] dans d'autres formats, nous utiliserons l'API [GroupDocs.Viewer for .NET][10]. Il permet le rendu et l'affichage des [formats de présentation PowerPoint pris en charge][11] par programmation. Veuillez soit [télécharger][12] la DLL pour l'API ou l'installer à l'aide de [NuGet][13].

```
PM> Install-Package GroupDocs.Viewer
```

## Rendre la présentation PowerPoint au format PDF à l'aide de C # {#Render-PowerPoint-Presentation-in-PDF-using-CSharp}

Nous pouvons rendre une présentation PowerPoint dans un document PDF en suivant les étapes ci-dessous :

  1. Chargez une présentation PowerPoint à l'aide de la classe _**[Viewer][14]**_.
  2. Créez une instance de la classe _**[PdfViewOptions][15]**_ avec le chemin du fichier PDF de sortie comme argument.
  3. Enfin, appelez la méthode _**[View()][16]**_ pour enregistrer le PPTX au format PDF. Il prend l'objet _**PdfViewOptions**_ comme argument.

L'exemple de code suivant montre **comment rendre un fichier PPTX au format PDF à l'aide de C#**.

```
// Cet exemple de code montre comment rendre PPTX en PDF.
// Charger le fichier PowerPoint PPTX
Voirer viewer = new Voirer(@"D:\Files\Voirer\sample.pptx");

// Définissez les options d'affichage PDF.
// La classe PdfVoirOptions fournit des options pour rendre les documents au format PDF.
PdfVoirOptions viewOptions = new PdfVoirOptions(@"D:\Files\Voirer\sample_output.pdf");

// Voir
viewer.Voir(viewOptions);
```

{{< figure align=center src="images/Render-PowerPoint-Presentation-in-PDF-using-CSharp.jpg" alt="Rendez la présentation PowerPoint au format PDF à l'aide de C #." caption="Rendez la présentation PowerPoint au format PDF à l'aide de C #.">}}

## Afficher la présentation PowerPoint en HTML à l'aide de C# {#View-PowerPoint-Presentation-in-HTML-using-CSharp}

Nous pouvons également rendre une présentation PowerPoint en HTML à afficher dans le navigateur en suivant les étapes ci-dessous :

  1. Chargez une présentation PowerPoint à l'aide de la classe _**[Viewer][14]**_.
  2. Créez une instance de la classe _**[HtmlViewOptions][17]**_ à l'aide de la méthode _**[ForEmbeddedResources][18]**_. Il prend le chemin du fichier HTML de sortie comme argument.
  3. Définissez diverses _**HtmlViewOptions**_ telles que RenderToSinglePage, etc.
  4. Enfin, appelez la méthode **_[View()][16]_** pour enregistrer le PPTX au format HTML. Il prend l'objet _**HtmlViewOptions**_ comme argument.

L'exemple de code suivant montre **comment rendre un PPTX au format HTML à l'aide de C#**.

```
// Cet exemple de code montre comment rendre PPTX en HTML.
// Charger le fichier PowerPoint PPTX
Voirer viewer = new Voirer(@"D:\Files\Voirer\sample.pptx");

// Définir les options d'affichage HTML
// La classe HtmlVoirOptions fournit des options pour rendre les documents au format HTML.
// Le rendu au format HTML avec des ressources intégrées intègre les ressources de la page au format HTML et rend chaque document 
// page autosuffisante. L'inconvénient est que la taille de la page et la vitesse de chargement peuvent diminuer.
HtmlVoirOptions viewOptions = HtmlVoirOptions.ForEmbeddedResources(@"D:\Files\Voirer\sample_output.html");

// Affichez toutes les diapositives dans une seule page HTML.
viewOptions.RenderToSinglePage = true;

// Voir
viewer.Voir(viewOptions);
```

{{< figure align=center src="images/View-PowerPoint-Presentation-in-HTML-using-CSharp.jpg" alt="Affichez la présentation PowerPoint en HTML à l'aide de C#." caption="Affichez la présentation PowerPoint en HTML à l'aide de C#.">}}

## Rendu des notes PowerPoint en HTML à l'aide de C# {#Render-PowerPoint-Notes-in-HTML-using-CSharp}

Nous pouvons rendre les notes de présentation PowerPoint en HTML en suivant les étapes mentionnées précédemment. Cependant, nous avons juste besoin d'activer le rendu des notes comme indiqué ci-dessous :

```
viewOptions.RenderNotes = true;
```

L'exemple de code suivant montre **comment rendre les notes de présentation PowerPoint en HTML à l'aide de C#**.

```
// Cet exemple de code montre comment rendre les notes de présentation PPTX en HTML.
// Charger le fichier PowerPoint PPTX
Voirer viewer = new Voirer(@"D:\Files\Voirer\sample.pptx");

// Définir les options d'affichage HTML
HtmlVoirOptions viewOptions = HtmlVoirOptions.ForEmbeddedResources(@"D:\Files\Voirer\sample_output.html");

// Affichez toutes les diapositives dans une seule page HTML.
viewOptions.RenderToSinglePage = true;

// Rendu des notes de présentation
viewOptions.RenderNotes = true;

// Voir
viewer.Voir(viewOptions);
```

{{< figure align=center src="images/Render-PowerPoint-Presentation-Notes-in-HTML-using-CSharp.jpg" alt="Rendez les notes de présentation PowerPoint en HTML à l'aide de C #." caption="Rendez les notes de présentation PowerPoint en HTML à l'aide de C #.">}}

## Convertir des diapositives PowerPoint en images JPG à l'aide de C# {#Convert-PowerPoint-Slides-into-JPG-images-using-CSharp}

Nous pouvons rendre une présentation PowerPoint et enregistrer toutes les diapositives sous forme d'images JPG en suivant les étapes ci-dessous :

  1. Chargez une présentation PowerPoint à l'aide de la classe _**[Viewer][14]**_.
  2. Créez une instance de la classe _**[ViewInfoOptions][19]**_ à l'aide de la méthode _**[ForJpgView][20]**_.
  3. Obtenez _**[ViewInfo][21]**_ à l'aide de la méthode _**[GetViewInfo][22]**_.
  4. Lisez la propriété _**ViewInfo.Pages.Count**_ et parcourez toutes les diapositives une par une.
  5. Créez une instance de la classe _**[JpgViewOptions][23]**_.
  6. Enfin, appelez la méthode _**[View()][16]**_ pour enregistrer la diapositive au format JPG. Il prend l'objet JpgViewOptions et le numéro de page comme arguments.

L'exemple de code suivant montre **comment convertir des diapositives PowerPoint en images JPG à l'aide de C#**.

```
// Cet exemple de code montre comment rendre PPTX en JPG.
// Charger le fichier PowerPoint PPTX
Viewer viewer = new Viewer(@"D:\Files\Viewer\sample.pptx");

// Obtenir des informations sur le document telles que le type de fichier et le nombre de pages
// La classe ViewInfoOptions fournit des options utilisées pour récupérer des informations sur la vue.
// La méthode ForJpgView() récupère les informations lors du rendu en JPG.
ViewInfoOptions viewInfoOptions = ViewInfoOptions.ForJpgView();
ViewInfo viewInfo = viewer.GetViewInfo(viewInfoOptions);

// Afficher les informations sur le document
Console.WriteLine("Document type is: " + viewInfo.FileType);
Console.WriteLine("Pages count: " + viewInfo.Pages.Count);

// Enregistrer chaque diapositive en tant qu'image JPG
for(int count=1;count<=viewInfo.Pages.Count;count++)
{
    // Define JPG view options
    // JpgViewOptions class provides options for rendering documents into JPG format.
    JpgViewOptions viewOptions = new JpgViewOptions(@"D:\Files\Viewer\Images\"+ "slide_" + count + ".jpg");
    
    // Render view
    viewer.View(viewOptions, count);
}
```

{{< figure align=center src="images/Convert-PowerPoint-Slides-into-JPG-images-using-CSharp.jpg" alt="Convertissez des diapositives PowerPoint en images JPG à l'aide de C#." caption="Convertissez des diapositives PowerPoint en images JPG à l'aide de C#.">}}

## Obtenez une licence gratuite

Veuillez essayer l'API sans limitation d'évaluation en demandant [une licence temporaire gratuite][24].

## Conclusion

Dans cet article, nous avons appris à :
  * rendre les diapositives PowerPoint de PPTX au format PDF en C# ;
  * afficher les diapositives PowerPoint dans le navigateur par programmation ;
  * convertir des diapositives PowerPoint en images JPG.
 
En outre, vous pouvez en savoir plus sur l'API GroupDocs.Viewer pour .NET à l'aide de la [documentation][25]. En cas d'ambiguïté, n'hésitez pas à nous contacter sur le [forum][26].

## Voir également

  * [Visionneuse de fichiers Excel - Afficher des données Excel à l'aide de C#][27]

  [1]: https://docs.fileformat.com/pdf/
  [2]: https://docs.fileformat.com/image/jpeg/
  [3]: https://docs.fileformat.com/web/html/
  [4]: #CSharp-API-to-Render-PowerPoint-Presentation
  [5]: #Render-PowerPoint-Presentation-in-PDF-using-CSharp
  [6]: #View-PowerPoint-Presentation-in-HTML-using-CSharp
  [7]: #Convert-PowerPoint-Slides-into-JPG-images-using-CSharp
  [8]: https://docs.fileformat.com/presentation/ppt/
  [9]: https://docs.fileformat.com/presentation/pptx/
  [10]: https://products.groupdocs.com/viewer/net/
  [11]: https://docs.groupdocs.com/viewer/net/view-powerpoint-presentations/#supported-presentation-formats
  [12]: https://downloads.groupdocs.com/viewer/net
  [13]: https://www.nuget.org/packages/GroupDocs.Viewer/
  [14]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
  [15]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
  [16]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
  [17]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
  [18]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options.htmlviewoptions/forembeddedresources/methods/4
  [19]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/viewinfooptions
  [20]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/viewinfooptions/methods/forjpgview
  [21]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.results/viewinfo
  [22]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/getviewinfo
  [23]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/jpgviewoptions
  [24]: https://purchase.conholdate.com/temporary-license
  [25]: https://docs.groupdocs.com/viewer/net/
  [26]: https://forum.groupdocs.com/c/viewer/
  [27]: https://blog.conholdate.com/2022/02/25/excel-file-viewer-display-excel-data-using-csharp/
  [28]: #Render-PowerPoint-Notes-in-HTML-using-CSharp
