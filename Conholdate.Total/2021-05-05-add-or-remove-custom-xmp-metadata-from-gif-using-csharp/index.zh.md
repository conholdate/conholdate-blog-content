---
title: "'使用 C# 从 GIF 添加或删除自定义 XMP 元数据'"
author: Muzammil Khan
date: 2021-05-05T10:37:17+00:00
summary: "您可以以编程方式将自定义 XMP 元数据包添加到图像中。在本文中，您将学习**如何使用 C# 在 GIF 中添加或删除自定义 XMP 元数据**。"
url: /zh/2021/05/05/add-or-remove-custom-xmp-metadata-from-gif-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "添加自定义 XMP 元数据 CSharp"
  - "自定义 XMP 元数据到 GIF"
  - "读取自定义 XMP 元数据 CSharp"
  - "删除自定义 XMP 元数据 CSharp"

---


{{< figure align=center src="images/GIF-SMP.png" alt="使用 C# 从 GIF 添加或删除自定义 XMP 元数据">}}
 

可扩展元数据平台 (XMP) 元数据被编码为 XML 格式的文本。定义的 XMP 数据模型可用于以名称/值对的形式存储任何一组元数据属性。您可以以编程方式将自定义 XMP 元数据包添加到图像中。在本文中，您将学习**如何使用 C# 在 GIF 中添加或删除自定义 XMP 元数据**。

本文讨论/涵盖了以下主题：

  * [用于添加或删除 XMP 元数据的 C# API][2]
  * [使用 C# 将自定义 XMP 元数据包添加到 GIF][3]
  * [使用 C# 读取自定义 XMP 元数据包属性][4]
  * [使用 C# 删除自定义 XMP 元数据包][5]

## 用于添加或删除 XMP 元数据的 C# API {#api-for-XMP-metadata}

我将使用 [GroupDocs.Metadata for .NET][6] API 添加或删除自定义 XMP 元数据包。它允许您从文档和图像文件格式中添加、编辑、检索和删除元数据属性。该 API 可与最著名的元数据标准配合使用，例如内置、XMP、EXIF、IPTC、图像资源块、ID3 和自定义元数据属性。它可用于在任何面向 .NET 平台的开发环境中开发应用程序。

您可以 [下载][7] API 的 DLL 或使用 [NuGet][8] 安装它。

```
Install-Package GroupDocs.Metadata
```

## 使用 C# 将自定义 XMP 元数据包添加到 GIF {#Add-Custom-XMP-Package}

您可以按照下面提到的简单步骤轻松创建和添加包含用户定义属性的完全自定义 XMP 包：

  * 创建 _[元数据][9]_ 类的实例
  * 提供 GIF 图片的路径
  * [获取根包][10] as [IXmp][11] standard
  * 创建 [XmpPackage][12] 类的实例
  * 提供包 Prefix 和 NamespaceUri
  * 使用 [Set][13] 方法在名称/值对中设置属性
  * 创建 [XmpPacketWrapper][14] 类的实例
  * 调用 [AddPackage][15] 方法并传递创建的 XmpPackage
  * 将创建的 XmpPacketWrapper 分配给 IXMp.[XmpPackage][16]
  * 使用 [Metadata.Save][17] 方法保存输出文件

以下代码示例展示了如何使用 C# 创建自定义 XMP 元数据包并将其添加到 GIF 图像。

```
using (Metadata metadata = new Metadata(@"C:\Files\xmp.gif")) {

  IXmp root = (IXmp)metadata.GetRootPackage();
  XmpPacketWrapper packet = new XmpPacketWrapper();

  XmpPackage custom = new XmpPackage("gd", "https://groupdocs.com");
  custom.Set("gd:Copyright", "Copyright (C) 2021 GroupDocs. All Rights Reserved.");
  custom.Set("gd:CreationDate", DateTime.Now.ToString());
  custom.Set("gd:Company", XmpArray.From(new String[] { "Aspose", "GroupDocs" }, XmpArrayType.Ordered));

  packet.AddPackage(custom);
  root.XmpPackage = packet;
  metadata.Save(@"C:\Files\xmp_output.gif");
}
```

上述代码示例应将 XMP 元数据包添加到输入图像。<mark> ExifTool 从生成的输出 GIF 图像中读取以下元数据。</mark>

{{< figure align=center src="images/Add_XMP_Metadata_csharp-1024x594.jpg" alt="使用 C# 将 XMP 元数据包添加到 GIF" caption="使用 C# 将 XMP 元数据包添加到 GIF">}}
 

[IXMP][11] 接口公开 [XmpPackage][19]{.broken_link} 属性以获取或设置 XMP 元数据包。

Metadata 类提供 [GetRootPackage][10] 方法来获取根包，该根包提供对从文件中提取的所有元数据属性的访问。

[XmpPackage][12] 类提供了各种属性来定义包，例如 [Prefix][20]、[NamespaceUri][21] 和 [Keys][22]。此类还提供 [Set][13] 方法来设置用户定义的元数据属性的名称/值。

[XmpPacketWrapper][14] 类包含序列化的 XMP 包。此类的 [AddPackage][15] 方法允许添加已定义的自定义包。

您可以在文档中找到有关“[使用 XMP 元数据][23]”的更多详细信息。

## 使用 C# 读取自定义 XMP 包元数据属性 {#Read-Custom-XMP-Package}

您可以按照下面提到的简单步骤轻松读取所有自定义 XMP 包用户定义的属性：

  * 创建 _[元数据][9]_ 类的实例
  * 提供 GIF 图片的路径
  * [获取根包][10] as [IXmp][11] standard
  * 从[IXmp.XmpPackage.Packages][24]中一一获取所有包
  * 获取每个包的 NamespaceUri 和 Prefix
  * 为每个包 Key 调用 [FindProperties][25] 以获取属性名称和值

以下代码示例展示了如何使用 C# 读取自定义 XMP 包中定义的所有属性。

```
string file = @"C:\Files\xmp_output.gif";
using (Metadata metadata = new Metadata(file)) 
{
  IXmp root = (IXmp)metadata.GetRootPackage();

  if (root.XmpPackage != null)
  {
    foreach (var package in root.XmpPackage.Packages)
    {
      Console.WriteLine(package.NamespaceUri);
      Console.WriteLine(package.Prefix);

      foreach(var keys in package.Keys)
      {
        var property = package.FindProperties(p => p.Name == keys).FirstOrDefault();
        Console.WriteLine(property.Name + " : " + property.Value);
      }
    }
  }
}
```

上述代码示例应产生以下输出：

```
https://groupdocs.com
gd
gd:Copyright: Copyright (C) 2021 GroupDocs. All Rights Reserved.
gd:CreationDate: 04/05/2021 2:26:17 am
gd:Company: <rdf:Seq><rdf:li>Aspose</rdf:li><rdf:li>GroupDocs</rdf:li></rdf:Seq>
```

[XmpPackage][12] 类的 [FindProperties][25] 方法递归搜索并找到满足指定谓词的元数据属性。

## 使用 C# 删除自定义 XMP 包 {#Remove-Custom-XMP-Package}

您可以按照下面提到的简单步骤从 GIF 图像中删除 XMP 包：

  * 创建 _[元数据][9]_ 类的实例
  * 提供 GIF 图片的路径
  * [获取根包][10] as [IXmp][11] standard
  * 将 IXMp.[XmpPackage][16] 设置为 null
  * 使用 [Metadata.Save][17] 方法保存输出文件

以下代码示例展示了如何使用 C# 从 GIF 图像中删除 XMP 元数据包。

```
using (Metadata metadata = new Metadata(@"C:\Files\xmp_output.gif"))
{
  IXmp root = (IXmp)metadata.GetRootPackage();
  root.XmpPackage = null;
  metadata.Save(@"C:\Files\xmp_output_Removed.gif");
}
```

上述代码示例应从输入图像中删除 XMP 元数据包。 ExifTool 从生成的输出 GIF 图像中读取以下元数据。

{{< figure align=center src="images/Remove_XMP_Metadata_csharp-1024x488.jpg" alt="使用 C# 从 GIF 中删除 XMP 元数据包" caption="使用 C# 从 GIF 中删除 XMP 元数据包">}}
 

## 获得免费许可证

您可以通过申请 [免费的临时许可证][27] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C#** 从 GIF 图像中添加或删除自定义 XMP 包元数据。您还学习了如何使用 C# 读取 XMP 包属性。此外，您可以使用 [文档][28] 了解用于 .NET API 的 GroupDocs.Metadata。如有任何歧义，请随时在 [论坛][29] 上与我们联系。

## 也可以看看

  * [使用 C# 提取和操作图像的元数据][30]
  * [在 C# 中管理 JPEG、PNG、TIFF 和 WebP 图像的 EXIF 数据][31]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/05/GIF-SMP.png
 [2]: #api-for-XMP-metadata
 [3]: #Add-Custom-XMP-Package
 [4]: #Read-Custom-XMP-Package
 [5]: #Remove-Custom-XMP-Package
 [6]: https://products.groupdocs.com/metadata/net
 [7]: https://downloads.groupdocs.com/metadata/net
 [8]: https://www.nuget.org/packages/GroupDocs.Metadata
 [9]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
 [10]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/getrootpackage
 [11]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.xmp/ixmp
 [12]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.xmp/xmppackage
 [13]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.xmp.xmppackage/set/methods/7
 [14]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.xmp/xmppacketwrapper
 [15]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.xmp/xmppacketwrapper/methods/addpackage
 [16]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.xmp/ixmp/properties/xmppackage
 [17]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.metadata/save/methods/2
 [18]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/05/Add_XMP_Metadata_csharp.jpg
 [19]: http://XmpPackage
 [20]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.xmp/xmppackage/properties/prefix
 [21]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.xmp/xmppackage/properties/namespaceuri
 [22]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.common/metadatapackage/properties/keys
 [23]: https://docs.groupdocs.com/metadata/net/working-with-xmp-metadata/
 [24]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.xmp/xmppacketwrapper/properties/packages
 [25]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.common/metadatapackage/methods/findproperties
 [26]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/05/Remove_XMP_Metadata_csharp.jpg
 [27]: https://purchase.groupdocs.com/temporary-license
 [28]: https://docs.groupdocs.com/metadata/net/
 [29]: https://forum.groupdocs.com/c/metadata/
 [30]: https://blog.groupdocs.cloud/2021/04/20/extract-and-manipulate-metadata-of-images-using-csharp/
 [31]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/








