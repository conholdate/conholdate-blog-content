---
title: "使用 Java 在 GIF 中添加或删除自定义 XMP 元数据"
author: Muzammil Khan
date: 2021-10-21T04:53:36+00:00
summary: "作为 Java 开发人员，您可以通过编程轻松地将自定义 XMP 元数据包添加到您的图像中。在本文中，您将学习**如何使用 Java 在 GIF 中添加或删除自定义 XMP 元数据**。"
url: /zh/2021/10/21/add-or-remove-custom-xmp-metadata-from-gif-using-java/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "添加自定义 XMP 元数据"
  - "Java 元数据 API"
  - "读取自定义 XMP 元数据"
  - "删除自定义 XMP 元数据"

---


{{< figure align=center src="images/add-or-remove-custom-xmp-metadata-from-gif-using-java.jpg" alt="使用 Java 在 GIF 中添加或删除自定义 XMP 元数据">}}
 

可扩展元数据平台 (XMP) 数据模型可用于以编码为 [XML][2] 格式文本的名称/值对形式存储任何元数据属性集。作为 Java 开发人员，您可以通过编程轻松地将自定义 XMP 元数据包添加到您的图像中。在本文中，您将学习**如何使用 Java 在 GIF 中添加或删除自定义 XMP 元数据**。

本文讨论/涵盖了以下主题：

  * [用于添加或删除自定义 XMP 元数据的 Java API][3]
  * [使用 Java 将自定义 XMP 元数据包添加到 GIF][4]
  * [使用 Java 读取自定义 XMP 元数据包属性][5]
  * [使用 Java 删除自定义 XMP 元数据包][6]

## 用于添加或删除自定义 XMP 元数据的 Java API {#Java-API-to-Add-or-Remove-Custom-XMP-Metadata}

为了在 [GIF][8] 图像中添加或删除自定义 [XMP][7] 元数据包，我们将使用 [GroupDocs.Metadata for Java][9] API。它允许您从 [支持的文档和图像文件格式][10] 添加、编辑、检索和删除元数据属性。 API 与最显着的元数据标准配合使用，例如内置元数据属性，例如作者、创建日期、特定格式的元数据属性，例如 XMP、[EXIF][11]、[IPTC][12]、图像资源块、 ID3 和自定义元数据属性。

您可以 [下载][13] API 的 JAR 或在您的基于 Maven 的 Java 应用程序中添加以下 **_pom.xml_** 配置来尝试下面提到的代码示例。

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
        <artifactId>groupdocs-metadata</artifactId>
        <version>21.8</version> 
</dependency>
```

## 使用 Java 将自定义 XMP 元数据包添加到 GIF {#Add-Custom-XMP-Metadata-Package-to-GIF-using-Java}

您可以按照以下简单步骤创建和添加具有用户定义属性的完全自定义 XMP 包：

  * 首先，使用 _[Metadata][14]_ 类加载 GIF 图像。
  * 然后，调用 [Metadata.getRootPackage()][15] 作为 [IXmp][16] 标准来获取根包。
  * 创建 [XmpPackage][17] 类的实例以创建新包。
  * 现在，设置各种属性来定义包，例如 [Prefix][18] 和 [NamespaceUri][19]。
  * 然后，调用 [Set()][20] 方法在名称/值对中设置用户定义的元数据属性。
  * 创建一个包含序列化 XMP 包的 [XmpPacketWrapper][21] 类的实例。
  * 现在，调用 [XmpPacketWrapper.AddPackage()][22] 方法来添加创建的自定义 XmpPackage。
  * 使用 [IXmp.setXmpPackage()][23] 方法设置 XMP 元数据包。
  * 最后，使用 [Metadata.save()][24] 方法保存输出文件。

以下代码示例展示了如何使用 Java 创建自定义 XMP 元数据包并将其添加到 GIF 图像。

```
// 此代码示例演示如何创建自定义 XMP 元数据包并将其添加到 GIF 图像。
// 创建元数据类的实例
Metadata metadata = new Metadata("C:\\Files\\xmp.gif");

// 获取根包
IXmp root = (IXmp)metadata.getRootPackage();

// 创建 Xmp 数据包包装器
XmpPacketWrapper packet = new XmpPacketWrapper();

// 定义自定义包
XmpPackage custom = new XmpPackage("gd", "https://groupdocs.com");
custom.set("gd:Copyright", "Copyright (C) 2021 GroupDocs. All Rights Reserved.");
custom.set("gd:CreationDate", new Date().toString());
custom.set("gd:Company", XmpArray.from(new String[] { "Aspose", "GroupDocs" }, XmpArrayType.Ordered));

// 将自定义包添加到 Xmp Packet Wrapper
packet.addPackage(custom);

// 更新 XmpPackage
root.setXmpPackage(packet);

// 保存文件
metadata.save("C:\\Files\\xmp_output.gif");
```

上述代码示例应将 XMP 元数据包添加到输入图像。请在下面找到 [ExifTool][25] 生成的输出。

{{< figure align=center src="images/Add-Custom-XMP-Metadata-Package-to-GIF-using-Java-1024x597.jpg" alt="使用 Java 将自定义 XMP 元数据包添加到 GIF" caption="使用 Java 将自定义 XMP 元数据包添加到 GIF">}}
 

## 使用 Java 读取自定义 XMP 包元数据属性 {#Read-Custom-XMP-Package-Metadata-Properties-using-Java}

您可以按照以下步骤读取自定义 XMP 包的所有用户定义属性：

  * 首先，使用 _[Metadata][14]_ 类加载 GIF 图像。
  * 然后，调用 [Metadata.getRootPackage()][15] 作为 [IXmp][16] 标准来获取根包。 It provides access to all metadata properties extracted from the file.
  * 调用 [IXmp.getXmpPackage()][27] 方法检查 [XmpPackage][17] 是否存在。
  * 现在，通过调用 [IXmp.getXmpPackage().getPackages()][28] 方法获取 XmpPackage 数组
  * 遍历所有包并调用 [XmpPackage.getNamespaceUri()][19] 和 [XmpPackage.getPrefix()][18] 方法来显示包命名空间 URI 和每个包的前缀
  * 循环遍历 [XmpPackage.getKeys()][29] 方法返回的所有键以打印元数据值
  * 最后，对每个包Key调用[XmpPackage.findProperties()][30]方法，递归查找匹配包key的元数据属性。

以下代码示例展示了如何使用 Java 读取自定义 XMP 包中定义的所有属性。

```
// 此代码示例演示如何读取自定义 XMP 包中定义的所有属性
// 创建元数据类的实例
Metadata metadata = new Metadata("C:\\Files\\xmp_output.gif");

// 获取根包
IXmp root = (IXmp)metadata.getRootPackage();
if (root.getXmpPackage() != null)
{
  // Get Xmp pakages
  XmpPackage[] packages = root.getXmpPackage().getPackages();
  
  // Show Package details
  for (XmpPackage pkg : packages )
  {
    System.out.println(pkg.getNamespaceUri());
    System.out.println(pkg.getPrefix());

    for(String keys : pkg.getKeys())
    {
      MetadataProperty property = pkg.findProperties(new WithNameSpecification(keys)).get_Item(0);
      System.out.println(property.getName() + " : " + property.getValue());
    }
  }
}
```

上述代码示例应产生以下输出：

```
https://groupdocs.com
gd
gd:Copyright: Copyright (C) 2021 GroupDocs. All Rights Reserved.
gd:CreationDate: Sat Oct 16 00:13:15 PKT 2021
gd:Company: <rdf:Seq><rdf:li>Aspose</rdf:li><rdf:li>GroupDocs</rdf:li></rdf:Seq>
```

## 使用 Java 删除自定义 XMP 包 {#Remove-Custom-XMP-Package-using-Java}

您可以按照以下步骤从 GIF 图像中删除 XMP 包：

  * 首先，使用 _[Metadata][14]_ 类加载 GIF 图像。
  * 然后，调用 [Metadata.getRootPackage()][15] 作为 [IXmp][16] 标准来获取根包。
  * 现在，使用 [IXmp.setXmpPackage()][23] 将 XmpPackege 设置为 null
  * 最后，使用 [Metadata.save()][24] 方法保存输出文件

以下代码示例展示了如何使用 Java 从 GIF 图像中删除 XMP 元数据包。

```
// 此代码示例演示如何从 GIF 图像中删除 XMP 元数据包。
// 创建元数据类的实例
Metadata metadata = new Metadata("C:\\Files\\xmp_output.gif");

// 获取根包
IXmp root = (IXmp)metadata.getRootPackage();

// 将包设置为空
root.setXmpPackage(null);

// 保存图片
metadata.save("C:\\Files\\xmp_output_Removed.gif");
```

上述代码示例应从输入图像中删除 XMP 元数据包。 ExifTool 从生成的输出 GIF 图像中读取以下元数据。

{{< figure align=center src="images/Remove-Custom-XMP-Package-using-Java-1024x595.jpg" alt="使用 Java 删除自定义 XMP 包。" caption="使用 Java 删除自定义 XMP 包。">}}
 

## 获得免费许可证

您可以通过申请 [免费的临时许可证][32] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 Java 将自定义 XMP 包元数据添加到 GIF 图像**。此外，您还了解了**如何以编程方式读取 XMP 包属性并从 GIF 图像中删除它们**。您可以使用 [文档][33] 了解有关 Java API 的 GroupDocs.Metadata 的更多信息。如有任何歧义，请随时在 [论坛][34] 上与我们联系。

## 也可以看看

  * [在 Java 中处理 HEIF HEIC 图像的 XMP 和 EXIF 数据][35]
  * [在 Java 中提取 WAV 文件的 RIFF INFO 和元数据][36]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/add-or-remove-custom-xmp-metadata-from-gif-using-java.jpg
 [2]: https://docs.fileformat.com/web/xml/
 [3]: #Java-API-to-Add-or-Remove-Custom-XMP-Metadata
 [4]: #Add-Custom-XMP-Metadata-Package-to-GIF-using-Java
 [5]: #Read-Custom-XMP-Package-Metadata-Properties-using-Java
 [6]: #Remove-Custom-XMP-Package-using-Java
 [7]: https://en.wikipedia.org/wiki/Extensible_Metadata_Platform
 [8]: https://docs.fileformat.com/image/gif/
 [9]: https://products.groupdocs.com/metadata/java
 [10]: https://docs.groupdocs.com/metadata/java/supported-document-formats/
 [11]: https://docs.fileformat.com/image/exif/
 [12]: https://iptc.org/standards/photo-metadata/
 [13]: https://downloads.groupdocs.com/metadata/java
 [14]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
 [15]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#getRootPackage()
 [16]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/IXmp
 [17]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/XmpPackage
 [18]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/XmpPackage#getPrefix()
 [19]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/XmpPackage#getNamespaceUri()
 [20]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/XmpPackage#set(java.lang.String,%20java.lang.String)
 [21]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/XmpPacketWrapper
 [22]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/XmpPacketWrapper#addPackage(com.groupdocs.metadata.core.XmpPackage)
 [23]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/IXmp#setXmpPackage(com.groupdocs.metadata.core.XmpPacketWrapper)
 [24]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#save(java.lang.String)
 [25]: https://exiftool.org/
 [26]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Add-Custom-XMP-Metadata-Package-to-GIF-using-Java.jpg
 [27]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/IXmp#getXmpPackage()
 [28]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/XmpPacketWrapper#getPackages()
 [29]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MetadataPackage#getKeys()
 [30]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#findProperties(com.groupdocs.metadata.search.Specification)
 [31]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/10/Remove-Custom-XMP-Package-using-Java.jpg
 [32]: https://purchase.groupdocs.com/temporary-license
 [33]: https://docs.groupdocs.com/metadata/java
 [34]: https://forum.groupdocs.com/c/metadata/
 [35]: https://blog.groupdocs.com/2021/05/10/xmp-and-exif-data-of-heif-heic-images-using-java/
 [36]: https://blog.groupdocs.com/2021/03/22/extract-riff-info-and-metadata-of-wav-files-in-java/








