---
title: "'使用 Java 读取 Outlook MSG 文件'"
author: Muzammil Khan
date: 2022-03-16T06:43:17+00:00
summary: "您可以在 Java 应用程序中读取 Outlook MSG 文件并提取主题、收件人、发件人、正文等属性。在本文中，您将学习**如何使用 Java 读取 Outlook MSG 文件**。"
url: /zh/2022/03/16/read-outlook-msg-file-using-java/

categories:
  - "Conholdate.Total 产品系列"
tags:
  - "用于读取 Outlook MSG 文件的 Java API"
  - "在 Java 中读取 Outlook MSG 文件"
  - "使用 Java 保存 MSG 附件"
  - "在 Java 中解析 Outlook MSG"
  - "使用 Java 查看 MSG 文件"
  - "Aspose.Email 对于 Java"
---

{{< figure align=center src="images/read-outlook-msg-file-using-java.jpg" alt="使用 Java 读取 Outlook MSG 文件">}}
 
[MSG][1] 是 MS Outlook 使用的电子邮件文件格式。它是一个 Outlook 项目，允许存储电子邮件、联系人、消息、任务、约会等。在某些情况下，我们可能需要在 Java 应用程序中读取 Outlook MSG 文件并提取主题、收件人、发件人、正文等属性。在本文中，我们将学习**如何使用 Java 读取 Outlook MSG 文件**。

本文将涵盖以下主题：

  * [用于读取 Outlook MSG 文件的 Java API][2]
  * [解析和读取 Outlook MSG 文件][3]
  * [从 MSG 文件中获取附件][4]
  * [从附件中读取嵌入消息][5]

## 用于读取 Outlook MSG 文件的 Java API {#Java-API-to-Read-Outlook-MSG-File}

为了读取 Outlook MSG 文件，我们将使用 [Aspose.Email for Java][6] API。它允许无缝地创建、发送、阅读和操作电子邮件。它还支持 Outlook MSG 文件的解析并以 Java 对象的形式提供它们的内容。请[下载][7] API 的 JAR 或在基于 Maven 的 Java 应用程序中添加以下 pom.xml 配置。

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
## 使用 Java 解析和读取 Outlook MSG 文件 {#Parse-and-Read-an-Outlook-MSG-File-using-Java}

我们可以按照以下步骤解析和读取 Outlook MSG 文件：

  1. 使用 _**[MapiMessage.load()][8]**_ 方法加载一个 MSG 文件。
  2. 从加载的 MSG 中读取 SenderName、Subject、Body、Recipients 等属性。

以下代码示例展示了**如何使用 Java 读取 Outlook MSG 文件**。

```
// 此代码示例演示如何读取 MSG 文件。
// 从磁盘加载 MSG 文件
MapiMessage outlookMessageFile = MapiMessage.load("D:\\Files\\Email\\message.msg");

// 显示发件人姓名
System.out.println("Sender Name : " + outlookMessageFile.getSenderName());

// 显示主题
System.out.println("Subject : " + outlookMessageFile.getSubject());

// 显示体
System.out.println("Body : " + outlookMessageFile.getBody());

// 显示收件人信息
System.out.println("Recipients : \n");

// 遍历与 MapiMessage 对象关联的收件人集合
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

{{< figure align=center src="images/Parse-and-Read-an-Outlook-MSG-File-using-Java.jpg" alt="使用 Java 解析和读取 Outlook MSG 文件。" caption="使用 Java 解析和读取 Outlook MSG 文件。">}}

## 使用 Java 从 MSG 文件中获取附件 {#Get-Attachments-from-MSG-File-using-Java}

我们还可以按照以下步骤保存 Outlook MSG 文件中的附件：

  1. 使用 _**[MapiMessage.load()][8]**_ 方法加载一个 MSG 文件。
  2. 遍历与 MapiMessage 对象关联的 [附件集合][9]。
  3. 使用 [save()][10] 方法将每个附件保存到磁盘。

以下代码示例显示**如何使用 Java 保存 Outlook MSG 文件中的附件**。

```
// 此代码示例演示如何保存 MSG 文件中的附件。
// 从磁盘加载 MSG 文件
MapiMessage outlookMessageFile = MapiMessage.load("D:\\Files\\Email\\WithEmbeddedMsg.msg");

// 遍历与 MapiMessage 对象关联的附件集合
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

{{< figure align=center src="images/Get-Attachments-from-MSG-File-using-Java.jpg" alt="使用 Java 从 MSG 文件中获取附件。" caption="使用 Java 从 MSG 文件中获取附件。">}}

## 从附件中读取嵌入消息 {#Read-Embedded-Message-from-Attachment}

我们也可以按照以下步骤阅读嵌入在 Outlook MSG 附件中的电子邮件：

  1. 使用 _**[MapiMessage.load()][8]**_ 方法加载一个 MSG 文件。
  2. 获取作为 MapiMessage 对象的附加消息。
  3. 显示消息属性。

以下代码示例展示了**如何使用 Java 将嵌入式消息作为附件读取**。

```
// 此代码示例演示如何读取 MSG 中附加的嵌入消息。
// 加载一个味精文件
MapiMessage mapi = MapiMessage.load(dataDir + "EmbededMessageAsAttachment.msg");

// 显示总附件
System.out.println("Total attachments : " + mapi.getAttachments().size());

// 将附件读取为 MapiMessage
MapiMessage emb = mapi.getAttachments().get_Item(0).getObjectData().toMapiMessage();

// 显示发件人姓名
System.out.println("Sender Name : " + emb.getSenderName());

// 显示主题
System.out.println("Subject : " + emb.getSubject());

// 显示体
System.out.println("Body : " + emb.getBody());

// 显示收件人信息
System.out.println("Recipients :");

// 遍历与 MapiMessage 对象关联的收件人集合
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

## 获得免费许可证

请通过请求 [免费的临时许可证][11] 来尝试不受评估限制的 API。

## 结论

在本文中，我们学习了如何使用 Java 以编程方式读取 Outlook MSG 文件的内容。此外，我们还了解了如何从 MSG 文件中读取和提取附件。此外，您可以使用 [documentation][12] 了解有关 Aspose.Email for Java API 的更多信息。如有任何歧义，请随时在 [论坛][13] 上与我们联系。

## 也可以看看

  * [使用 Java 以编程方式阅读电子邮件][14]

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
