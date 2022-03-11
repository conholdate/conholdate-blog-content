---
title: "'使用 C# 创建加密的 ZIP 文件'"
author: Muzammil Khan
date: 2021-09-18T17:42:25+00:00
summary: "作为 C# 开发人员，您可以在 .NET 应用程序中使用 C# 以编程方式轻松创建加密或受密码保护的 ZIP 存档。在本文中，您将学习**如何使用 C# 创建加密的 ZIP 档案**。"
url: /zh/2021/09/18/create-encrypted-zip-files-using-csharp/
categories:
  - "Conholdate.Total 产品系列"
tags:
  - "CSharp API 创建 ZIP 档案"
  - "创建受密码保护的 ZIP 文件"
  - "使用 CSharp 创建 ZIP 档案"
  - "加密 ZIP 中的文件和文件夹"
  - "使用 CSharp 加密 ZIP 档案"

---


{{< figure align=center src="images/add-files-or-folders-to-zip-archives-using-csharp.jpg" alt="使用 csharp 添加文件或文件夹到 zip 存档">}}
 

ZIP 文件是最常见的存档文件类型，用于将压缩文件和文件夹保存在单个容器中。作为 C# 开发人员，您可以在 .NET 应用程序中使用 C# 以编程方式轻松创建加密或受密码保护的 ZIP 存档。在本文中，您将学习**如何使用 C# 创建加密的 ZIP 文件**。

本文讨论/涵盖了以下主题：

  * [用于创建加密 ZIP 文件的 C# API][2]
  * [创建受密码保护的 ZIP 文件][3]
  * [使用 AES 加密创建加密的 ZIP 文件][4]
  * [加密 ZIP 文件中的文件夹][5]
  * [加密 ZIP 档案中的特定文件][6]
  * [使用混合加密创建加密 ZIP 文件][7]

## 用于创建加密 ZIP 文件的 C# API {#CSharp-API-to-Create-Encrypted-ZIP-Files}

为了创建加密的 [ZIP][8] 档案，我将使用 [Aspose.ZIP for .NET API][9]。它使您能够压缩文件和文件夹并将它们添加到 ZIP 存档中。它还允许您解压缩支持类型的档案，例如 ZIP、TAR、GZIP、BZ2、7Zip、RAR 等。API 通过用户定义的密码和使用 AES 加密的传统加密技术（例如 AES128、AES192 和 AES256）提供保护.

您可以 [下载][10] API 的 DLL 或使用 [NuGet][11] 安装它。

```
Install-Package Aspose.ZIP
```

## 创建受密码保护的 ZIP 文件 {#Create-Password-Protected-ZIP-Files}

您可以按照以下步骤以编程方式轻松创建受密码保护的 ZIP 存档：

  1. 使用 _**[ArchiveEntrySettings][13]**_ 对象创建 **_[Archive][12]_** 类的实例。
  2. 使用 [_**TraditionalEncryptionSettings**_][14] 对象设置密码。
  3. 使用输入文件路径调用 **_[CreatEntry()][15]_** 方法以添加到存档。
  4. 重复上述步骤以添加多个文件。
  5. 使用输出文件路径调用 _**[Save()][16]**_ 方法来保存输出文件。

以下代码示例展示了**如何使用 C# 创建受密码保护的 ZIP 文件**。

```
// 创建档案
Archive archive = new Archive(new ArchiveEntrySettings(encryptionSettings: new TraditionalEncryptionSettings("12345")));

// 将文件添加到存档
archive.CreateEntry("sample1.txt", "C:\\Files\\sample1.txt");
archive.CreateEntry("sample2.txt", "C:\\Files\\sample2.txt");

// 保存存档
archive.Save("C:\\Files\\password_protcted.zip");
```

{{< figure align=center src="images/Create-Password-Protected-ZIP-Archives.jpg" alt="创建受密码保护的 ZIP 档案" caption="创建受密码保护的 ZIP 档案">}}
 

**Archive** 类代表一个 ZIP 归档文件。它提供了多种方法来创建、编写、提取或更新 ZIP 档案。此类的 **CreatEntry()** 方法在存档中创建文件的单个条目。它将文件名和完全限定的文件路径作为输入参数。此类还提供重载的 _**[CreatEntry()][18]**_ 方法来从流或 _FileInfo_ 添加文件。此类的 **Save()** 方法将 ZIP 存档保存在指定的文件路径中。

**ArchiveEntrySettings** 类提供压缩或解压缩条目的设置。 **TraditionalEncryptionSetings** 类为传统的 **ZipCrypto** 算法提供设置。它是一种 ZIP 密码保护算法。此类的 **_Password_** 属性允许获取或设置密码以加密或解密 ZIP 存档中的文件和文件夹。

## 使用 AES 加密创建加密的 ZIP 文件 {#Create-Encrypted-ZIP-Files-with-AES-Encryption}

您可以按照以下步骤以编程方式使用 AES 加密来加密 ZIP 存档：

  1. 使用 _**[ArchiveEntrySettings][13]**_ 对象创建 **_[Archive][12]_** 类的实例。
  2. 使用 [_**AesEcryptionSettings**_][19] 类设置密码。将密码字符串和 [**_EncryptionMethod_**][20] 作为参数传递给构造函数。
  3. 使用输入文件路径调用 **_[CreatEntry()][15]_** 方法以添加到存档。
  4. 重复上述步骤以添加多个文件。
  5. 使用输出文件路径调用 _**[Save()][16]**_ 方法来保存输出文件。

以下代码示例显示**如何使用 C# 创建使用 AES 加密的 ZIP 文件**。

```
// 创建档案
Archive archive = new Archive(new ArchiveEntrySettings(null, new AesEcryptionSettings("p@s$", EncryptionMethod.AES128)));

// 将文件添加到存档
archive.CreateEntry("abc.txt", "C:\\Files\\sample1.txt");

// 保存存档
archive.Save("C:\\Files\\aes.zip");
```

**AesEncryptionSettings** 类提供 AES 加密或解密算法的设置。高级加密标准 (AES) 是一种对称加密或解密分组密码算法。

您可以使用以下类型的加密方法：

  * 传统的——传统的 PKWARE 加密
  * AES128 — 密钥长度为 128 位的高级加密标准
  * AES192 — 密钥长度为 192 位的高级加密标准
  * AES256 — 密钥长度为 256 位的高级加密标准

## 加密 ZIP 文件中的文件夹 {#Encrypt-Folders-in-ZIP-Files}

您可以按照以下步骤以编程方式将受密码保护的文件夹添加到 ZIP 文件中：

  1. 使用 _**[ArchiveEntrySettings][13]**_ 对象创建 **_[Archive][12]_** 类的实例。
  2. 使用 [_**TraditionalEncryptionSettings**_][14] 对象设置密码。
  3. 使用要添加到存档的文件夹路径调用 **_[CreatEntries()][21]_** 方法。
  4. 重复上述步骤以添加多个文件夹。
  5. 使用输出文件路径调用 _**[Save()][16]**_ 方法来保存输出文件。

以下代码示例展示了**如何使用 C#** 将 **encrypted** 文件夹添加到 ZIP 文件中。

```
// 创建档案
Archive archive = new Archive(new ArchiveEntrySettings(null, new TraditionalEncryptionSettings("123@45")));

// 将文件夹添加到存档
archive.CreateEntries("C:\\Files\\MyFolder");

// 保存存档
archive.Save("C:\\Files\\password_protcted_folder.zip");
```

## 加密 ZIP 档案中的特定文件 {#Encrypt-Specific-Files-in-ZIP-Archives}

您可以按照以下步骤以编程方式加密 ZIP 存档中的特定文件：

  1. 创建 **_[Archive][12]_** 类的实例。
  2. 使用输入文件路径调用 **_[CreatEntry()][15]_** 方法以添加到存档。
  3. 使用 _**ArchiveEntrySettings**_ 和 _**_**TraditionalEncryptionSettings**_**_ 为文件设置密码。
  4. 使用输入文件路径调用 **_[CreatEntry()][15]_** 方法以将另一个文件添加到存档中。
  5. 重复上述步骤以添加更多文件。
  6. 使用输出文件路径调用 _**[Save()][16]**_ 方法来保存输出文件。

以下代码示例显示**如何使用 C# 加密 ZIP 存档中的特定文件**。

```
// 创建档案
Archive archive = new Archive();

// 将文件添加到存档
archive.CreateEntry("sample1.txt", "C:\\Files\\sample1.txt");
archive.CreateEntry("sample2.txt", "C:\\Files\\sample2.txt", false, new ArchiveEntrySettings(encryptionSettings: new TraditionalEncryptionSettings("123@abc")));

// 保存存档
archive.Save("C:\\Files\\password_protcted.zip");
```

{{< figure align=center src="images/Encrypt-Specific-Files-in-ZIP-Archives.jpg" alt="加密 ZIP 档案中的特定文件" caption="加密 ZIP 档案中的特定文件">}}
 

## 使用混合加密创建加密 ZIP 文件 {#Create-Encrypted-ZIP-Files-with-Mixed-Encryption}

您可以按照以下给出的步骤以编程方式创建包含使用混合加密技术保护的文件和文件夹的 ZIP 存档，这些加密技术因每个文件和文件夹而异：

  1. 创建 **_[Archive][12]_** 类的实例。
  2. 使用输入文件路径调用 **_[CreatEntry()][15]_** 方法以添加到存档。
  3. 使用 _**ArchiveEntrySettings**_ 和 _**AesEcryptionSettings**_ 为文件设置密码。
  4. 使用输入文件路径调用 **_[CreatEntry()][15]_** 方法以将另一个文件添加到存档中。
  5. 使用 _**ArchiveEntrySettings**_ 和 _**TraditionalEncryptionSettings**_ 设置文件的密码。
  6. 使用输入文件路径调用 **_[CreatEntry()][15]_** 方法以将另一个文件添加到存档中。
  7. 使用要添加到存档的文件夹路径调用 **_[CreateEntries()][21]_** 方法。
  8. 使用带有输出文件路径的 _**[Save()][16]**_ 方法保存输出文件。

以下代码示例展示了**如何使用 C# 创建具有混合加密技术的 ZIP 文件**。

```
// 创建档案
Archive archive = new Archive();

// 将使用 AES 加密的文件添加到存档
archive.CreateEntry("sample1.txt", "C:\\Files\\sample1.txt", false, new ArchiveEntrySettings(null, new AesEcryptionSettings("p@s$", EncryptionMethod.AES128)));

// 将具有传统加密的文件添加到存档
archive.CreateEntry("sample2.txt", "C:\\Files\\sample2.txt", false, new ArchiveEntrySettings(encryptionSettings: new TraditionalEncryptionSettings("321")));

// 将未加密的文件添加到存档
archive.CreateEntry("sample3.txt", "C:\\Files\\sample2.txt");

// 将未加密的文件夹添加到存档
archive.CreateEntries("C:\\Files\\MyFolder");

// 保存存档
archive.Save("C:\\Files\\Mixed.zip");
```

{{< figure align=center src="images/Create-Encrypted-ZIP-Archives-with-Mixed-Encryption.jpg" alt="使用混合加密创建加密 ZIP 档案" caption="使用混合加密创建加密 ZIP 文件">}}
 

## 获得免费许可证

您可以通过请求 [免费的临时许可证][24] 来试用该 API，而不受评估限制。

## 结论

在本文中，您学习了**如何使用 C# 创建加密的 ZIP 文件**。您还学习了**如何以编程方式创建受密码保护的 ZIP 文件**。此外，您还学习了**如何加密 ZIP 档案中的特定文件**。此外，您还学习了**如何将受密码保护的文件夹添加到 ZIP 文件**。本文还解释了**如何使用 C# 创建使用混合加密技术加密的 ZIP 文件**。您可以使用 [文档][25] 了解更多关于 Aspose.ZIP for .NET API 的信息。如有任何歧义，请随时在 [论坛][26] 上与我们联系。

## 也可以看看

  * [使用 C# 渲染 ZIP 档案][27]

 [1]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/add-files-or-folders-to-zip-archives-using-csharp.jpg
 [2]: #CSharp-API-to-Create-Encrypted-ZIP-Files
 [3]: #Create-Password-Protected-ZIP-Files
 [4]: #Create-Encrypted-ZIP-Files-with-AES-Encryption
 [5]: #Encrypt-Folders-in-ZIP-Files
 [6]: #Encrypt-Specific-Files-in-ZIP-Archives
 [7]: #Create-Encrypted-ZIP-Files-with-Mixed-Encryption
 [8]: https://docs.fileformat.com/compression/zip/
 [9]: https://products.aspose.com/zip/net
 [10]: https://downloads.aspose.com/zip/net
 [11]: https://www.nuget.org/packages/Aspose.Zip/
 [12]: https://apireference.aspose.com/zip/net/aspose.zip/archive
 [13]: https://apireference.aspose.com/zip/net/aspose.zip.saving/archiveentrysettings
 [14]: https://apireference.aspose.com/zip/net/aspose.zip.saving/traditionalencryptionsettings
 [15]: https://apireference.aspose.com/zip/net/aspose.zip.archive/createentry/methods/3
 [16]: https://apireference.aspose.com/zip/net/aspose.zip.archive/save/methods/1
 [17]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Create-Password-Protected-ZIP-Archives.jpg
 [18]: https://apireference.aspose.com/zip/net/aspose.zip/archive/methods/createentry/index
 [19]: https://apireference.aspose.com/zip/net/aspose.zip.saving/aesecryptionsettings
 [20]: https://apireference.aspose.com/zip/net/aspose.zip.saving/encryptionmethod
 [21]: https://apireference.aspose.com/zip/net/aspose.zip.archive/createentries/methods/1
 [22]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Encrypt-Specific-Files-in-ZIP-Archives.jpg
 [23]: https://blog.conholdate.com/wp-content/uploads/sites/27/2021/09/Create-Encrypted-ZIP-Archives-with-Mixed-Encryption.jpg
 [24]: https://purchase.aspose.com/temporary-license
 [25]: https://docs.aspose.com/zip/net/
 [26]: https://forum.aspose.com/c/zip/37
 [27]: https://blog.conholdate.com/2021/07/06/render-zip-archives-using-csharp/








