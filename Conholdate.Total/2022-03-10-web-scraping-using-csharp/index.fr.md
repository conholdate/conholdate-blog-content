---
title: "'Grattage Web en utilisant C#'"
author: Muzammil Khan
date: 2022-03-10T06:43:17+00:00
summary: "Le Web Scraping est une technique utilisée pour extraire des données de sites Web. Dans cet article, vous apprendrez **comment effectuer du scraping Web avec analyse HTML à l'aide de C#**."
url: /fr/2022/03/10/web-scraping-using-csharp/

categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "API de grattage Web C#"
  - "Exploration Web avec C#"
  - "Extraire des données de sites Web"
  - "Extraire des données de sites Web à l'aide de C#"
---

{{< figure align=center src="images/web-scraping-using-csharp.jpg" alt="Web Scraping avec C#">}}
 
Le Web Scraping est une technique utilisée pour extraire des données de sites Web. Il permet d'automatiser le processus d'extraction des données des sites Web et des fichiers [HTML][16]. En tant que développeur C #, nous pouvons facilement inspecter, capturer et extraire des données, telles que des images, des vidéos, du son, etc., à partir des pages Web. Dans cet article, nous allons apprendre **comment effectuer du scraping Web avec analyse HTML en utilisant C#**.

Les sujets suivants seront traités dans cet article :

  * [API de grattage Web C#][1]
  * [Lire et extraire le HTML en utilisant C#][2]
  * [Inspecter les éléments de document à l'aide de C#][3]
  * [Rechercher un élément spécifique à l'aide de filtres en C #][4]
  * [Interroger des données à partir de HTML à l'aide de C #][5]
  * [Extraire à l'aide du sélecteur CSS en C#][6]

## API de grattage Web C# {#CSharp-Web-Scraping-API}

Pour le grattage Web à partir de fichiers HTML ou d'URL, nous utiliserons l'API [Aspose.HTML pour .NET][7]. Il s'agit d'une API de traitement HTML avancée qui permet de générer, modifier, extraire des données, convertir et restituer des documents HTML sans aucun logiciel externe. Veuillez [télécharger][8] la DLL de l'API ou l'installer à l'aide de [NuGet][9].

```
PM> Install-Package Aspose.Html
```

## Lire et extraire le HTML en utilisant C# {#Read-and-Extract-HTML-using-CSharp}

Nous pouvons lire et extraire le HTML de n'importe quel document HTML en suivant les étapes ci-dessous :

  1. Chargez un document HTML à l'aide de la classe _**[HTMLDocument][10]**_.
  2. Affichez le code HTML interne du fichier sur la console.

L'exemple de code suivant montre **comment lire et extraire du contenu HTML à l'aide de C#**.

```
// Cet exemple de code montre comment afficher le contenu d'un document HTML
// Charger le document HTML
var document = new HTMLDocument(@"D:\Files\html\input.html");

// Afficher le code HTML interne du document
Console.WriteLine(document.Body.InnerHTML);
```

{{< figure align=center src="images/Read-and-Extract-HTML-using-CSharp.jpg" alt="Lire et extraire le HTML à l'aide de C#." caption="Lire et extraire le HTML à l'aide de C #.">}}

De même, nous pouvons lire et extraire le code HTML des sites Web en direct, comme indiqué ci-dessous :

```
// Cet exemple de code montre comment afficher le contenu de l'URL du site Web en direct.
// Initialiser l'URL
Url url = new Url("https://en.wikipedia.org/wiki/HTML");

// Charger le fichier HTML à l'aide de l'instance Url
HTMLDocument document = new HTMLDocument(url);

// Afficher le code HTML interne du fichier sur la console
Console.WriteLine(document.Body.InnerHTML);
```
 

## Inspecter les éléments de document à l'aide de C# {#Inspect-Document-Elements-using-CSharp}

Nous pouvons inspecter le document et ses éléments en suivant les étapes ci-dessous :

  1. Chargez un document HTML à l'aide de la classe _**[HTMLDocument][10]**_.
  2. Obtenez l'élément HTML du document.
  3. Récupère les premiers/derniers éléments de l'élément HTML.
  4. Afficher les détails des éléments tels que TagName, TextContent.

L'exemple de code suivant montre **comment inspecter les éléments du document à l'aide de C#**.

```
// Cet exemple de code montre comment inspecter des éléments HTML.
// Charger un document à partir d'un fichier
string documentPath = @"D:\Files\html\input.html";
HTMLDocument document = new HTMLDocument(documentPath);

// Obtenir l'élément html du document
var element = document.DocumentElement;
Console.WriteLine(element.TagName); // HTML

// Obtenir le dernier élément de l'élément html
element = element.LastElementChild;
Console.WriteLine(element.TagName); // BODY

// Obtenir le premier élément de l'élément body
element = element.FirstElementChild;
Console.WriteLine(element.TagName); // H1
Console.WriteLine(element.TextContent); // Header 1
```


## Rechercher des éléments spécifiques à l'aide de filtres en C# {#Find-Specific-Element-using-Filters-in-CSharp}

Nous pouvons utiliser des filtres personnalisés pour trouver des éléments spécifiques tels que récupérer toutes les images, les liens, etc. À cette fin, l'API fournit l'interface TreeWalker. Il permet de naviguer dans une arborescence ou une sous-arborescence de documents en utilisant la vue du document définie par leurs drapeaux et leur filtre whatToShow (le cas échéant). Nous pouvons trouver des éléments spécifiques à l'aide de filtres en suivant les étapes ci-dessous :

  1. Définissez des filtres à l'aide de la classe NodeFilter et remplacez la méthode AcceptNode().
  2. Chargez un document HTML à l'aide de la classe _**[HTMLDocument][10]**_.
  3. Appelez la méthode CreateTreeWalker(). Il prend le nœud racine, ce qu'il faut afficher et NodeFilter comme arguments.

L'exemple de code suivant montre **comment lire et extraire du contenu HTML à l'aide de C#**.

```
// Cet exemple de code montre comment interroger des données à l'aide de filtres.
// Charger un document HTML
HTMLDocument document = new HTMLDocument(@"D:\Files\html\input.html");

// Pour démarrer la navigation HTML, nous devons créer une instance de TreeWalker.
// Les paramètres spécifiés signifient qu'il commence à marcher à partir de la racine du document,
// itérer tous les nœuds et utiliser notre implémentation personnalisée du filtre
using (var iterator = document.CreateTreeWalker(document, Dom.Traversal.Filters.NodeFilter.SHOW_ALL, new OnlyImageFilter()))
{
    while (iterator.NextNode() != null)
    {
        // Since we are using our own filter, the current node will always be an instance of the HTMLImageElement.
        // So, we don't need the additional validations here.
        var image = (HTMLImageElement)iterator.CurrentNode;

        System.Console.WriteLine(image.Src);
        // output: image1.png
        // output: image2.png
    }
}
```

```
// Cet exemple de code montre comment définir le filtre Node.
class OnlyImageFilter : Aspose.Html.Dom.Traversal.Filters.NodeFilter
{
    public override short AcceptNode(Aspose.Html.Dom.Node n)
    {
        // The current filter skips all elements, except IMG elements.
        return string.Equals("img", n.LocalName)
            ? FILTER_ACCEPT
            : FILTER_SKIP;
    }
}
```

## Interroger des données à partir de HTML à l'aide de C# {#Query-Data-from-HTML-using-CSharp}

Nous pouvons également utiliser XPath Query pour interroger les données d'un document HTML en suivant les étapes ci-dessous :

  1. Chargez un document HTML à l'aide de la classe _**[HTMLDocument][10]**_.
  2. Appelez la méthode Evaluate(). Il prend la chaîne d'expression XPath, le document et le type comme arguments.
  3. Enfin, parcourez les nœuds résultants et affichez le texte

L'exemple de code suivant montre **comment interroger des données avec des requêtes XPath à l'aide de C#**.

```
// Cet exemple de code montre comment interroger des données à l'aide d'une requête XPath.
// Préparer un code HTML
var code = @"
    <div class='happy'>
        <div>
            <span>Hello!</span>
        </div>
    </div>
    <p class='happy'>
        <span>World</span>
    </p>
";

// Initialiser un document basé sur le code préparé
HTMLDocument document = new HTMLDocument(code, ".");

// Ici, nous évaluons l'expression XPath où nous sélectionnons tous les éléments SPAN enfants 
// à partir d'éléments dont l'attribut 'class' est égal à 'happy' :
var result = document.Evaluate("//*[@class='happy']//span",
    document,
    null,
    Aspose.Html.Dom.XPath.XPathResultType.Any,
    null);

// Itérer sur les nœuds résultants
for (Aspose.Html.Dom.Node node; (node = result.IterateNext()) != null;)
{
    System.Console.WriteLine(node.TextContent);
    // output: Hello
    // output: World!
}
```
 
## Extraire à l'aide du sélecteur CSS en C # {#Extract-using-CSS-Selector-in-CSharp}

Nous pouvons également extraire du contenu HTML à l'aide de sélecteurs CSS. À cette fin, l'API fournit la méthode [QuerySelectorAll()][11] qui permet de naviguer dans un document HTML et de rechercher les éléments nécessaires. Il prend le sélecteur de requête comme paramètre et renvoie une NodeList correspondante de tous les éléments. Nous pouvons interroger à l'aide de sélecteurs CSS en suivant les étapes ci-dessous :

  1. Chargez un document HTML à l'aide de la classe _**[HTMLDocument][10]**_.
  2. Appelez la méthode QuerySelectorAll(). Il prend le sélecteur de requête comme argument.
  3. Enfin, parcourez la liste d'éléments résultante.

L'exemple de code suivant montre **comment extraire du contenu HTML à l'aide de sélecteurs CSS en C#**.

```
// Initialiser un document basé sur le code préparé
HTMLDocument document = new HTMLDocument(@"D:\Files\html\input.html");

// Ici, nous créons un sélecteur CSS qui extrait tous les éléments div
var elements = document.QuerySelectorAll("div");

// Itérer sur la liste d'éléments résultante
foreach (Aspose.Html.HTMLElement element in elements)
{
    System.Console.WriteLine(element.InnerHTML);
}
```
 
## Obtenez une licence gratuite

Veuillez essayer l'API sans limitation d'évaluation en demandant [une licence temporaire gratuite][12].

## Conclusion

Dans cet article, nous avons appris à :
  * lire et extraire le contenu d'un document HTML à l'aide de C# ;
  * inspecter les éléments de document et trouver un élément spécifique à partir de HTML ;
  * interroger des données spécifiques et extraire des données à l'aide de CSS Selector ;

En outre, vous pouvez en savoir plus sur l'API Aspose.HTML pour .NET en utilisant la [documentation][13]. En cas d'ambiguïté, n'hésitez pas à nous contacter sur le [forum][14].

## Voir également

  * [C# Convertir HTML en JPG, PNG, BMP et image GIF avec .NET][15]

  [1]: #CSharp-Web-Scraping-API
  [2]: #Read-and-Extract-HTML-using-CSharp
  [3]: #Inspect-Document-Elements-using-CSharp
  [4]: #Find-Specific-Element-using-Filters-in-CSharp
  [5]: #Query-Data-from-HTML-using-CSharp
  [6]: #Extract-using-CSS-Selector-in-CSharp
  [7]: https://products.aspose.com/html/net/
  [8]: https://downloads.aspose.com/html/net/
  [9]: https://www.nuget.org/packages/aspose.html
  [10]: https://apireference.aspose.com/html/net/aspose.html/htmldocument
  [11]: https://apireference.aspose.com/html/net/aspose.html.dom/document/methods/queryselectorall
  [12]: https://purchase.conholdate.com/temporary-license
  [13]: https://docs.aspose.com/html/net/
  [14]: https://forum.aspose.com/c/html/
  [15]: https://blog.aspose.com/2020/05/30/html-to-jpg-png-bmp-and-gif-images-csharp/
  [16]: https://docs.fileformat.com/web/html/
