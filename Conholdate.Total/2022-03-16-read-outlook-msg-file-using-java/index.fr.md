---
title: ""Lire le fichier Outlook MSG à l'aide de Java""
author: Muzammil Khan
date: 2022-03-16T06:43:17+00:00
summary: "Vous pouvez lire les fichiers Outlook MSG dans les applications Java et extraire des propriétés telles que l'objet, les destinataires, l'expéditeur, le corps, etc. Dans cet article, vous apprendrez ** comment lire un fichier Outlook MSG à l'aide de Java **."
url: /fr/2022/03/16/read-outlook-msg-file-using-java/

categories:
  - "Conholdate.Total Famille de produits"
tags:
  - "API Java pour lire les fichiers Outlook MSG"
  - "Lire le fichier Outlook MSG en Java"
  - "Enregistrer les pièces jointes MSG à l'aide de Java"
  - "Analyser Outlook MSG en Java"
  - "Afficher le fichier MSG à l'aide de Java"
  - "Aspose.Email pour Java"
---

{{< figure align=center src="images/read-outlook-msg-file-using-java.jpg" alt="Lire le fichier Outlook MSG à l'aide de Java">}}
 
Le [MSG][1] est un format de fichier de courrier électronique utilisé par MS Outlook. Il s'agit d'un élément Outlook qui permet de stocker des e-mails, des contacts, des messages, des tâches, des rendez-vous, etc. Dans certains cas, nous pouvons avoir besoin de lire des fichiers Outlook MSG dans des applications Java et d'extraire des propriétés telles que le sujet, les destinataires, l'expéditeur, le corps, etc. Dans cet article, nous allons apprendre **comment lire un fichier Outlook MSG en utilisant Java**.

Les sujets suivants seront traités dans cet article :

  * [API Java pour lire le fichier Outlook MSG][2]
  * [Analyser et lire un fichier Outlook MSG][3]
  * [Obtenir des pièces jointes à partir du fichier MSG][4]
  * [Lire le message intégré à partir de la pièce jointe][5]

## API Java pour lire le fichier Outlook MSG {#Java-API-to-Read-Outlook-MSG-File}

Pour lire le fichier Outlook MSG, nous utiliserons l'API [Aspose.Email for Java][6]. Il permet de créer, d'envoyer, de lire et de manipuler des e-mails de manière transparente. Il prend également en charge l'analyse des fichiers Outlook MSG et fournit leur contenu dans des objets Java. Veuillez soit [télécharger][7] le JAR de l'API ou simplement ajouter la configuration pom.xml suivante dans une application Java basée sur Maven.

```
<repository>
    <id>AsposeJavaAPI</id>
    <name>Aspose Java API</name>
    <url>http://repository.aspose.com/repo/</url>
</repository>
```

```
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-email</artifactId>
    <version>22.2</version>
    <classifier>jdk16</classifier>
</dependency>
```
## Analyser et lire un fichier Outlook MSG à l'aide de Java {#Parse-and-Read-an-Outlook-MSG-File-using-Java}

Nous pouvons analyser et lire un fichier Outlook MSG en suivant les étapes ci-dessous :

  1. Chargez un fichier MSG à l'aide de la méthode _**[MapiMessage.load()][8]**_.
  2. Lire les propriétés telles que SenderName, Subject, Body, Recipients à partir du MSG chargé.

L'exemple de code suivant montre **comment lire un fichier Outlook MSG à l'aide de Java**.

```
// Cet exemple de code montre comment lire le fichier MSG.
// Charger un fichier MSG à partir du disque
MapiMessage outlookMessageFile = MapiMessage.load("D:\\Files\\Email\\message.msg");

// Afficher le nom de l'expéditeur
System.out.println("Sender Name : " + outlookMessageFile.getSenderName());

// Afficher le sujet
System.out.println("Subject : " + outlookMessageFile.getSubject());

// Corps d'affichage
System.out.println("Body : " + outlookMessageFile.getBody());

// Afficher les informations du destinataire
System.out.println("Recipients : \n");

// Boucle dans la collection de destinataires associée à l'objet MapiMessage
for (int i = 0; i < outlookMessageFile.getRecipients().size(); i++) {
  
  // Set a reference to the MapiRecipient object
  MapiRecipient rcp = (MapiRecipient) outlookMessageFile.getRecipients().get_Item(i);
  
  // Display recipient email address
  System.out.println("Email : " + rcp.getEmailAddress());
  
  // Display recipient name
  System.out.println("Name : " + rcp.getDisplayName());
  
  // Display recipient type
  System.out.println("Recipient Type : " + rcp.getRecipientType());
}
```

{{< figure align=center src="images/Parse-and-Read-an-Outlook-MSG-File-using-Java.jpg" alt="Analyser et lire un fichier Outlook MSG à l'aide de Java." caption="Analyser et lire un fichier Outlook MSG à l'aide de Java.">}}

## Obtenir des pièces jointes à partir d'un fichier MSG à l'aide de Java {#Get-Attachments-from-MSG-File-using-Java}

Nous pouvons également enregistrer les pièces jointes à partir d'un fichier Outlook MSG en suivant les étapes ci-dessous :

  1. Chargez un fichier MSG à l'aide de la méthode _**[MapiMessage.load()][8]**_.
  2. Parcourez la [collection de pièces jointes][9] associée à l'objet MapiMessage.
  3. Enregistrez chaque pièce jointe sur le disque à l'aide de la méthode [save()][10].

L'exemple de code suivant montre **comment enregistrer des pièces jointes à partir d'un fichier Outlook MSG à l'aide de Java**.

```
// Cet exemple de code montre comment enregistrer des pièces jointes à partir d'un fichier MSG.
// Charger un fichier MSG à partir du disque
MapiMessage outlookMessageFile = MapiMessage.load("D:\\Files\\Email\\WithEmbeddedMsg.msg");

// Boucle dans la collection de pièces jointes associée à l'objet MapiMessage
for (int i = 0; i < outlookMessageFile.getAttachments().size(); i++) {
  
  // Set a reference to the MapiAttachment object
  MapiAttachment outlookMessageAttachment = (MapiAttachment) outlookMessageFile.getAttachments().get_Item(i);
  
  // Display attachment type
  System.out.println("Att Type : " + outlookMessageAttachment.getMimeTag());
  
  // Display attached file name
  System.out.println("File Name : " + outlookMessageAttachment.getLongFileName());
  
  // Save attachment to the disk
  outlookMessageAttachment.save("D:\\Files\\Email\\" + outlookMessageAttachment.getDisplayName());
}
```

{{< figure align=center src="images/Get-Attachments-from-MSG-File-using-Java.jpg" alt="Obtenez les pièces jointes du fichier MSG à l'aide de Java." caption="Obtenez les pièces jointes du fichier MSG à l'aide de Java.">}}

## Lire le message intégré à partir de la pièce jointe {#Read-Embedded-Message-from-Attachment}

Nous pouvons également lire les e-mails intégrés dans la pièce jointe Outlook MSG en suivant les étapes ci-dessous :

  1. Chargez un fichier MSG à l'aide de la méthode _**[MapiMessage.load()][8]**_.
  2. Obtenez le message joint en tant qu'objet MapiMessage.
  3. Afficher les propriétés du message.

L'exemple de code suivant montre **comment lire un message intégré en tant que pièce jointe à l'aide de Java**.

```
// Cet exemple de code montre comment lire un message intégré joint dans MSG.
// Charger un fichier MSG
MapiMessage mapi = MapiMessage.load(dataDir + "EmbededMessageAsAttachment.msg");

// Afficher le nombre total de pièces jointes
System.out.println("Total attachments : " + mapi.getAttachments().size());

// Lire la pièce jointe en tant que MapiMessage
MapiMessage emb = mapi.getAttachments().get_Item(0).getObjectData().toMapiMessage();

// Afficher le nom de l'expéditeur
System.out.println("Sender Name : " + emb.getSenderName());

// Afficher le sujet
System.out.println("Subject : " + emb.getSubject());

// Corps d'affichage
System.out.println("Body : " + emb.getBody());

// Afficher les informations du destinataire
System.out.println("Recipients :");

// Boucle dans la collection de destinataires associée à l'objet MapiMessage
for (int i = 0; i < emb.getRecipients().size(); i++) {
  
  // Set a reference to the MapiRecipient object
  MapiRecipient rcp = (MapiRecipient) emb.getRecipients().get_Item(i);
  
  // Display recipient email address
  System.out.println("\t Email : " + rcp.getEmailAddress());
  
  // Display recipient name
  System.out.println("\t Name : " + rcp.getDisplayName());
  
  // Display recipient type
  System.out.println("\t Recipient Type : " + rcp.getRecipientType());
}
```

## Obtenez une licence gratuite

Veuillez essayer l'API sans limitation d'évaluation en demandant [une licence temporaire gratuite][11].

## Conclusion

Dans cet article, nous avons appris à lire le contenu du fichier Outlook MSG par programmation à l'aide de Java. De plus, nous avons vu comment lire et extraire les pièces jointes d'un fichier MSG. En outre, vous pouvez en savoir plus sur l'API Aspose.Email pour Java en utilisant la [documentation][12]. En cas d'ambiguïté, n'hésitez pas à nous contacter sur le [forum][13].

## Voir également

  * [Lire les e-mails par programmation à l'aide de Java][14]

  [1]: https://docs.fileformat.com/email/msg/
  [2]: #Java-API-to-Read-Outlook-MSG-File
  [3]: #Parse-and-Read-an-Outlook-MSG-File-using-Java
  [4]: #Get-Attachments-from-MSG-File-using-Java
  [5]: #Read-Embedded-Message-from-Attachment
  [6]: https://products.aspose.com/email/java/
  [7]: https://downloads.aspose.com/email/java
  [8]: https://apireference.aspose.com/email/java/com.aspose.email/MapiMessage#load(java.lang.String)
  [9]: https://apireference.aspose.com/email//java/com.aspose.email/mapiattachmentCollection
  [10]: https://apireference.aspose.com/email/java/com.aspose.email/MapiAttachment#save(java.lang.String)
  [11]: https://purchase.conholdate.com/temporary-license
  [12]: https://docs.aspose.com/email/java/
  [13]: https://forum.aspose.com/c/email/12
  [14]: https://blog.aspose.com/2021/04/12/read-email-messages-programmatically-using-java/
