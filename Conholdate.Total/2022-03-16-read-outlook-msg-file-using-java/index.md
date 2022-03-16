---
title: 'Read Outlook MSG File using Java'
author: Muzammil Khan
date: 2022-03-16T06:43:17+00:00
summary: 'You can read Outlook MSG files in Java applications and extract properties such as subject, recipients, sender, body, etc. In this article, you will learn **how to read an Outlook MSG file using Java**.'
url: /2022/03/16/read-outlook-msg-file-using-java/

categories:
  - Conholdate.Total Product Family
tags:
  - 'Java API to Read Outlook MSG Files'
  - 'Read Outlook MSG File in Java'
  - 'Save MSG Attachments using Java'
  - 'Parse Outlook MSG in Java'
  - 'View MSG file using Java'
  - 'Aspose.Email for Java'
---

{{< figure align=center src="images/read-outlook-msg-file-using-java.jpg" alt="Read Outlook MSG File using Java">}}
 
The [MSG][1] is an email file format used by MS Outlook. It is an Outlook item that allows storing emails, contacts, messages, tasks, appointments, etc. In certain cases, we may need to read Outlook MSG files in Java applications and extract properties such as subject, recipients, sender, body, etc. In this article, we will learn **how to read an Outlook MSG file using Java**.

The following topics shall be covered in this article:

  * [Java API to Read Outlook MSG File][2]
  * [Parse and Read an Outlook MSG File][3]
  * [Get Attachments from MSG File][4]
  * [Read Embedded Message from Attachment][5]

## Java API to Read Outlook MSG File {#Java-API-to-Read-Outlook-MSG-File}

For reading the Outlook MSG file, we will be using [Aspose.Email for Java][6] API. It allows creating, sending, reading, and manipulating email messages seamlessly. It also supports the parsing of Outlook MSG files and provides their content in Java objects. Please either [download][7] the JAR of the API or just add the following pom.xml configuration in a Maven-based Java application.

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
## Parse and Read an Outlook MSG File using Java {#Parse-and-Read-an-Outlook-MSG-File-using-Java}

We can parse and read an Outlook MSG file by following the steps given below:

  1. Load an MSG file using the _**[MapiMessage.load()][8]**_ method.
  2. Read properties such as SenderName, Subject, Body, Recipients from the loaded MSG.

The following code sample shows **how to read an Outlook MSG file using Java**.

{{< gist conholdate-gists a1e600b31c9c1bdd10c3171922e06692 "ReadOutlookMSG_Java_Read.java" >}}

{{< figure align=center src="images/Parse-and-Read-an-Outlook-MSG-File-using-Java.jpg" alt="Parse and Read an Outlook MSG File using Java." caption="Parse and Read an Outlook MSG File using Java.">}}

## Get Attachments from MSG File using Java {#Get-Attachments-from-MSG-File-using-Java}

We can also save the attachments from an Outlook MSG file by following the steps given below:

  1. Load an MSG file using the _**[MapiMessage.load()][8]**_ method.
  2. Loop through the [attachments collection][9] associated with the MapiMessage object.
  3. Save each attachment to disk using the [save()][10] method.

The following code sample shows **how to save attachments from an Outlook MSG file using Java**.

{{< gist conholdate-gists a1e600b31c9c1bdd10c3171922e06692 "ReadOutlookMSG_Java_GetAttachments.java" >}}

{{< figure align=center src="images/Get-Attachments-from-MSG-File-using-Java.jpg" alt="Get Attachments from MSG File using Java." caption="Get Attachments from MSG File using Java.">}}

## Read Embedded Message from Attachment {#Read-Embedded-Message-from-Attachment}

We can read the email messages embedded within the Outlook MSG attachment as well by following the steps given below:

  1. Load an MSG file using the _**[MapiMessage.load()][8]**_ method.
  2. Get the attached message as a MapiMessage object.
  3. Show message properties.

The following code sample shows **how to read an embedded message as an attachment using Java**.

{{< gist conholdate-gists a1e600b31c9c1bdd10c3171922e06692 "ReadOutlookMSG_Java_ReadEmbeddedMessage.java" >}}

## Get a Free License

Please try the API without evaluation limitations by requesting [a free temporary license][11].

## Conclusion

In this article, we have learned how to read the content of the Outlook MSG file programmatically using Java. Moreover, we have seen how to read and extract attachments from an MSG file. Besides, you can learn more about Aspose.Email for Java API using the [documentation][12]. In case of any ambiguity, please feel free to contact us on the [forum][13].

## See Also

  * [Read Email Messages Programmatically using Java][14]

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