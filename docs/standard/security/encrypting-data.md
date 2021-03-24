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
# <a name="encrypting-data"></a><span data-ttu-id="2f978-103">Encrypting data (Шифрование данных)</span><span class="sxs-lookup"><span data-stu-id="2f978-103">Encrypting data</span></span>

<span data-ttu-id="2f978-104">Симметричное и асимметричное шифрования выполняются с использованием различных процессов.</span><span class="sxs-lookup"><span data-stu-id="2f978-104">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="2f978-105">Симметричное шифрование выполняется в рамках потоков, поэтому его удобно применять для шифрования больших объемов данных.</span><span class="sxs-lookup"><span data-stu-id="2f978-105">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="2f978-106">Асимметричное шифрование выполняется в рамках небольшого числа байтов, поэтому его удобно применять для шифрования только небольших объемов данных.</span><span class="sxs-lookup"><span data-stu-id="2f978-106">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>

## <a name="symmetric-encryption"></a><span data-ttu-id="2f978-107">Симметричное шифрование</span><span class="sxs-lookup"><span data-stu-id="2f978-107">Symmetric encryption</span></span>

<span data-ttu-id="2f978-108">Управляемые классы симметричного шифрования используются со специальным классом потока <xref:System.Security.Cryptography.CryptoStream> , который шифрует данные, считанные в поток.</span><span class="sxs-lookup"><span data-stu-id="2f978-108">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="2f978-109">Класс **CryptoStream** инициализируется классом управляемого потока, классом, реализующим <xref:System.Security.Cryptography.ICryptoTransform> интерфейс (созданным из класса, реализующего криптографический алгоритм), и <xref:System.Security.Cryptography.CryptoStreamMode> перечислением, описывающим тип доступа, разрешенный для **CryptoStream**.</span><span class="sxs-lookup"><span data-stu-id="2f978-109">The **CryptoStream** class is initialized with a managed stream class, a class that implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="2f978-110">Класс **CryptoStream** можно инициализировать с помощью любого класса, производного от <xref:System.IO.Stream> класса, включая <xref:System.IO.FileStream> , <xref:System.IO.MemoryStream> и <xref:System.Net.Sockets.NetworkStream> .</span><span class="sxs-lookup"><span data-stu-id="2f978-110">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="2f978-111">При помощи этих классов можно осуществлять симметричное шифрование для различных объектов потока.</span><span class="sxs-lookup"><span data-stu-id="2f978-111">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>

<span data-ttu-id="2f978-112">В следующем примере показано, как создать новый экземпляр класса реализации по умолчанию для <xref:System.Security.Cryptography.Aes> алгоритма.</span><span class="sxs-lookup"><span data-stu-id="2f978-112">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="2f978-113">Экземпляр используется для выполнения шифрования класса **CryptoStream** .</span><span class="sxs-lookup"><span data-stu-id="2f978-113">The instance is used to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="2f978-114">В этом примере **CryptoStream** инициализируется при помощи объекта потока `myStream` , который может быть любым типом управляемого потока.</span><span class="sxs-lookup"><span data-stu-id="2f978-114">In this example, the **CryptoStream** is initialized with a stream object called `myStream` that can be any type of managed stream.</span></span> <span data-ttu-id="2f978-115">Методу **креатинкриптор** из класса **AES** передается ключ и вектор инициализации, используемые для шифрования.</span><span class="sxs-lookup"><span data-stu-id="2f978-115">The **CreateEncryptor** method from the **Aes** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="2f978-116">В этом случае используется ключ и вектор инициализации по умолчанию, созданные из `aes` .</span><span class="sxs-lookup"><span data-stu-id="2f978-116">In this case, the default key and IV generated from `aes` are used.</span></span>

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

<span data-ttu-id="2f978-117">После выполнения этого кода все данные, записанные в объект **CryptoStream** , шифруются с помощью алгоритма AES.</span><span class="sxs-lookup"><span data-stu-id="2f978-117">After this code is executed, any data written to the **CryptoStream** object is encrypted using the AES algorithm.</span></span>

<span data-ttu-id="2f978-118">В следующем примере показан весь процесс создания потока, шифрования потока, чтения из потока и закрытия потока.</span><span class="sxs-lookup"><span data-stu-id="2f978-118">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="2f978-119">В этом примере создается файловый поток, зашифрованный с помощью класса **CryptoStream** и класса **AES** .</span><span class="sxs-lookup"><span data-stu-id="2f978-119">This example creates a file stream that is encrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="2f978-120">Созданный IV записывается в начало <xref:System.IO.FileStream> , поэтому его можно считать и использовать для расшифровки.</span><span class="sxs-lookup"><span data-stu-id="2f978-120">Generated IV is written to beginning of <xref:System.IO.FileStream>, so it can be read and used for decryption.</span></span> <span data-ttu-id="2f978-121">Затем сообщение записывается в зашифрованный поток с помощью <xref:System.IO.StreamWriter> класса.</span><span class="sxs-lookup"><span data-stu-id="2f978-121">Then a message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="2f978-122">Хотя один и тот же ключ можно использовать несколько раз для шифрования и расшифровки данных, рекомендуется создавать новый случайный вектор инициализации каждый раз.</span><span class="sxs-lookup"><span data-stu-id="2f978-122">While the same key can be used multiple times to encrypt and decrypt data, it is recommended to generate a new random IV each time.</span></span> <span data-ttu-id="2f978-123">Таким образом зашифрованные данные всегда отличаются, даже если обычный текст одинаков.</span><span class="sxs-lookup"><span data-stu-id="2f978-123">This way the encrypted data is always different, even when plain text is the same.</span></span>

:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb":::

<span data-ttu-id="2f978-124">Код шифрует поток с помощью симметричного алгоритма AES и записывает IV, а затем шифрует "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="2f978-124">The code encrypts the stream using the AES symmetric algorithm, and writes IV and then encrypted "Hello World!"</span></span> <span data-ttu-id="2f978-125">в этот поток.</span><span class="sxs-lookup"><span data-stu-id="2f978-125">to the stream.</span></span> <span data-ttu-id="2f978-126">Если код выполнен успешно, создается зашифрованный файл с именем *TestData.txt* и на консоль выводится следующий текст:</span><span class="sxs-lookup"><span data-stu-id="2f978-126">If the code is successful, it creates an encrypted file named *TestData.txt* and displays the following text to the console:</span></span>

```console
The text was encrypted.
```

<span data-ttu-id="2f978-127">Файл можно расшифровать с помощью примера симметричного расшифровки при [расшифровке данных](decrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="2f978-127">You can decrypt the file by using the symmetric decryption example in [Decrypting Data](decrypting-data.md).</span></span> <span data-ttu-id="2f978-128">Этот пример и этот пример указывают тот же ключ.</span><span class="sxs-lookup"><span data-stu-id="2f978-128">That example and this example specify the same key.</span></span>

<span data-ttu-id="2f978-129">Однако при возникновении исключения код выводит на консоль следующий текст:</span><span class="sxs-lookup"><span data-stu-id="2f978-129">However, if an exception is raised, the code displays the following text to the console:</span></span>

```console
The encryption failed.
```

## <a name="asymmetric-encryption"></a><span data-ttu-id="2f978-130">Асимметричное шифрование</span><span class="sxs-lookup"><span data-stu-id="2f978-130">Asymmetric encryption</span></span>

<span data-ttu-id="2f978-131">Асимметричные алгоритмы обычно используются для шифрования малых объемов данных, например для шифрования симметричного ключа и вектора инициализации.</span><span class="sxs-lookup"><span data-stu-id="2f978-131">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="2f978-132">Как правило, сторона, осуществляющая асимметричное шифрование, использует открытый ключ, созданный другой стороной.</span><span class="sxs-lookup"><span data-stu-id="2f978-132">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="2f978-133"><xref:System.Security.Cryptography.RSA>Для этой цели класс предоставляется .NET.</span><span class="sxs-lookup"><span data-stu-id="2f978-133">The <xref:System.Security.Cryptography.RSA> class is provided by .NET for this purpose.</span></span>

<span data-ttu-id="2f978-134">В следующем примере сведения об открытом ключе используются для шифрования симметричного ключа и вектора инициализации.</span><span class="sxs-lookup"><span data-stu-id="2f978-134">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="2f978-135">Инициализируются два массива байтов, представляющих открытый ключ третьей стороны.</span><span class="sxs-lookup"><span data-stu-id="2f978-135">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="2f978-136">Объект <xref:System.Security.Cryptography.RSAParameters> инициализируется с этими значениями.</span><span class="sxs-lookup"><span data-stu-id="2f978-136">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="2f978-137">Затем объект **RSAParameters** (вместе с открытым ключом, который он представляет) импортируется в экземпляр **RSA** с помощью <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> метода.</span><span class="sxs-lookup"><span data-stu-id="2f978-137">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSA** instance using the <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2f978-138">Наконец, закрытый ключ и вектор инициализации, созданные <xref:System.Security.Cryptography.Aes> классом, шифруются.</span><span class="sxs-lookup"><span data-stu-id="2f978-138">Finally, the private key and IV created by an <xref:System.Security.Cryptography.Aes> class are encrypted.</span></span> <span data-ttu-id="2f978-139">В этом примере требуется, чтобы в системе было установлено 128-битное шифрование.</span><span class="sxs-lookup"><span data-stu-id="2f978-139">This example requires systems to have 128-bit encryption installed.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2f978-140">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2f978-140">See also</span></span>

- [<span data-ttu-id="2f978-141">Создание ключей для шифрования и расшифровки</span><span class="sxs-lookup"><span data-stu-id="2f978-141">Generating keys for encryption and decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="2f978-142">Расшифровка данных</span><span class="sxs-lookup"><span data-stu-id="2f978-142">Decrypting data</span></span>](decrypting-data.md)
- [<span data-ttu-id="2f978-143">Службы шифрования</span><span class="sxs-lookup"><span data-stu-id="2f978-143">Cryptographic services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="2f978-144">Кроссплатформенное шифрование</span><span class="sxs-lookup"><span data-stu-id="2f978-144">Cross-platform cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="2f978-145">Уязвимости в учете времени при симметричной расшифровке в режиме CBC с использованием заполнения</span><span class="sxs-lookup"><span data-stu-id="2f978-145">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="2f978-146">ASP.NET Core Защита данных</span><span class="sxs-lookup"><span data-stu-id="2f978-146">ASP.NET Core data protection</span></span>](/aspnet/core/security/data-protection/introduction)
