---
title: Encrypting data (Шифрование данных)
description: Узнайте, как шифровать данные в .NET с помощью симметричного алгоритма или асимметричного алгоритма.
ms.date: 03/22/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], symmetric
- symmetric encryption
- cryptography [.NET], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: 5105bf6763f89b5867ccb8908aaf6136ded29dcb
ms.sourcegitcommit: 26721a2260deabb3318cc98af8619306711153cd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2021
ms.locfileid: "105027894"
---
# <a name="encrypting-data"></a>Encrypting data (Шифрование данных)

Симметричное и асимметричное шифрования выполняются с использованием различных процессов. Симметричное шифрование выполняется в рамках потоков, поэтому его удобно применять для шифрования больших объемов данных. Асимметричное шифрование выполняется в рамках небольшого числа байтов, поэтому его удобно применять для шифрования только небольших объемов данных.

## <a name="symmetric-encryption"></a>Симметричное шифрование

Управляемые классы симметричного шифрования используются со специальным классом потока <xref:System.Security.Cryptography.CryptoStream> , который шифрует данные, считанные в поток. Класс **CryptoStream** инициализируется классом управляемого потока, классом, реализующим <xref:System.Security.Cryptography.ICryptoTransform> интерфейс (созданным из класса, реализующего криптографический алгоритм), и <xref:System.Security.Cryptography.CryptoStreamMode> перечислением, описывающим тип доступа, разрешенный для **CryptoStream**. Класс **CryptoStream** можно инициализировать с помощью любого класса, производного от <xref:System.IO.Stream> класса, включая <xref:System.IO.FileStream> , <xref:System.IO.MemoryStream> и <xref:System.Net.Sockets.NetworkStream> . При помощи этих классов можно осуществлять симметричное шифрование для различных объектов потока.

В следующем примере показано, как создать новый экземпляр класса реализации по умолчанию для <xref:System.Security.Cryptography.Aes> алгоритма. Экземпляр используется для выполнения шифрования класса **CryptoStream** . В этом примере **CryptoStream** инициализируется при помощи объекта потока `myStream` , который может быть любым типом управляемого потока. Методу **креатинкриптор** из класса **AES** передается ключ и вектор инициализации, используемые для шифрования. В этом случае используется ключ и вектор инициализации по умолчанию, созданные из `aes` .

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(
    myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(
    myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write);
```

После выполнения этого кода все данные, записанные в объект **CryptoStream** , шифруются с помощью алгоритма AES.

В следующем примере показан весь процесс создания потока, шифрования потока, чтения из потока и закрытия потока. В этом примере создается файловый поток, зашифрованный с помощью класса **CryptoStream** и класса **AES** . Созданный IV записывается в начало <xref:System.IO.FileStream> , поэтому его можно считать и использовать для расшифровки. Затем сообщение записывается в зашифрованный поток с помощью <xref:System.IO.StreamWriter> класса. Хотя один и тот же ключ можно использовать несколько раз для шифрования и расшифровки данных, рекомендуется создавать новый случайный вектор инициализации каждый раз. Таким образом зашифрованные данные всегда отличаются, даже если обычный текст одинаков.

:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb":::

Код шифрует поток с помощью симметричного алгоритма AES и записывает IV, а затем шифрует "Hello World!" в этот поток. Если код выполнен успешно, создается зашифрованный файл с именем *TestData.txt* и на консоль выводится следующий текст:

```console
The text was encrypted.
```

Файл можно расшифровать с помощью примера симметричного расшифровки при [расшифровке данных](decrypting-data.md). Этот пример и этот пример указывают тот же ключ.

Однако при возникновении исключения код выводит на консоль следующий текст:

```console
The encryption failed.
```

## <a name="asymmetric-encryption"></a>Асимметричное шифрование

Асимметричные алгоритмы обычно используются для шифрования малых объемов данных, например для шифрования симметричного ключа и вектора инициализации. Как правило, сторона, осуществляющая асимметричное шифрование, использует открытый ключ, созданный другой стороной. <xref:System.Security.Cryptography.RSA>Для этой цели класс предоставляется .NET.

В следующем примере сведения об открытом ключе используются для шифрования симметричного ключа и вектора инициализации. Инициализируются два массива байтов, представляющих открытый ключ третьей стороны. Объект <xref:System.Security.Cryptography.RSAParameters> инициализируется с этими значениями. Затем объект **RSAParameters** (вместе с открытым ключом, который он представляет) импортируется в экземпляр **RSA** с помощью <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> метода. Наконец, закрытый ключ и вектор инициализации, созданные <xref:System.Security.Cryptography.Aes> классом, шифруются. В этом примере требуется, чтобы в системе было установлено 128-битное шифрование.

```vb
Imports System
Imports System.Security.Cryptography

Module Module1

    Sub Main()
        'Initialize the byte arrays to the public key information.
        Dim modulus As Byte() = {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19, 202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}

        Dim exponent As Byte() = {1, 0, 1}

        'Create values to store encrypted symmetric keys.
        Dim encryptedSymmetricKey() As Byte
        Dim encryptedSymmetricIV() As Byte

        'Create a new instance of the default RSA implementation class.
        Dim rsa As RSA = RSA.Create()

        'Create a new instance of the RSAParameters structure.
        Dim rsaKeyInfo As New RSAParameters()

        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus
        rsaKeyInfo.Exponent = exponent

        'Import key parameters into rsa
        rsa.ImportParameters(rsaKeyInfo)

        'Create a new instance of the default Aes implementation class.
        Dim aes As Aes = Aes.Create()

        'Encrypt the symmetric key and IV.
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1)
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1)
    End Sub

End Module
```

```csharp
using System;
using System.Security.Cryptography;

class Class1
{
    static void Main()
    {
        //Initialize the byte arrays to the public key information.
        byte[] modulus =
        {
            214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,
            106,99,179,68,175,211,164,116,64,148,226,254,172,147
        };

        byte[] exponent = { 1, 0, 1 };

        //Create values to store encrypted symmetric keys.
        byte[] encryptedSymmetricKey;
        byte[] encryptedSymmetricIV;

        //Create a new instance of the RSA class.
        RSA rsa = RSA.Create();

        //Create a new instance of the RSAParameters structure.
        RSAParameters rsaKeyInfo = new RSAParameters();

        //Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus;
        rsaKeyInfo.Exponent = exponent;

        //Import key parameters into rsa.
        rsa.ImportParameters(rsaKeyInfo);

        //Create a new instance of the default Aes implementation class.
        Aes aes = Aes.Create();

        //Encrypt the symmetric key and IV.
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1);
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1);
    }
}
```

## <a name="see-also"></a>См. также раздел

- [Создание ключей для шифрования и расшифровки](generating-keys-for-encryption-and-decryption.md)
- [Расшифровка данных](decrypting-data.md)
- [Службы шифрования](cryptographic-services.md)
- [Кроссплатформенное шифрование](cross-platform-cryptography.md)
- [Уязвимости в учете времени при симметричной расшифровке в режиме CBC с использованием заполнения](vulnerabilities-cbc-mode.md)
- [ASP.NET Core Защита данных](/aspnet/core/security/data-protection/introduction)
