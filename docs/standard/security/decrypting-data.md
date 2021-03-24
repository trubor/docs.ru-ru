---
title: Расшифровка данных
description: Узнайте, как расшифровать данные в .NET с помощью симметричного алгоритма или асимметричного алгоритма.
ms.date: 03/22/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: 14d8b6185c1c5b3aaee4f2041f98c500f2d3c313
ms.sourcegitcommit: 26721a2260deabb3318cc98af8619306711153cd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2021
ms.locfileid: "105027913"
---
# <a name="decrypting-data"></a><span data-ttu-id="6ac42-103">Расшифровка данных</span><span class="sxs-lookup"><span data-stu-id="6ac42-103">Decrypting data</span></span>

<span data-ttu-id="6ac42-104">Расшифровка представляет собой операцию, обратную операции шифрования.</span><span class="sxs-lookup"><span data-stu-id="6ac42-104">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="6ac42-105">Для шифрования с секретным ключом необходимо знать как ключ, так и вектор инициализации, которые использовались при шифровании данных.</span><span class="sxs-lookup"><span data-stu-id="6ac42-105">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="6ac42-106">Для шифрования с открытым ключом необходимо знать либо открытый ключ (если данные были зашифрованы при помощи закрытого ключа), либо закрытый ключ (если данные были зашифрованы при помощи открытого ключа).</span><span class="sxs-lookup"><span data-stu-id="6ac42-106">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="6ac42-107">Симметричная расшифровка</span><span class="sxs-lookup"><span data-stu-id="6ac42-107">Symmetric decryption</span></span>

<span data-ttu-id="6ac42-108">Расшифровка данных, зашифрованных при помощи симметричных алгоритмов, похожа на процесс, используемый для шифрования данных при помощи симметричных алгоритмов.</span><span class="sxs-lookup"><span data-stu-id="6ac42-108">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="6ac42-109"><xref:System.Security.Cryptography.CryptoStream>Класс используется с симметричными криптографическими классами, предоставляемыми .NET для расшифровки данных, считанных из любого управляемого объекта потока.</span><span class="sxs-lookup"><span data-stu-id="6ac42-109">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by .NET to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="6ac42-110">В следующем примере показано, как создать новый экземпляр класса реализации по умолчанию для <xref:System.Security.Cryptography.Aes> алгоритма.</span><span class="sxs-lookup"><span data-stu-id="6ac42-110">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="6ac42-111">Экземпляр используется для расшифровки <xref:System.Security.Cryptography.CryptoStream> объекта.</span><span class="sxs-lookup"><span data-stu-id="6ac42-111">The instance is used to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="6ac42-112">В этом примере сначала создается новый экземпляр <xref:System.Security.Cryptography.Aes> класса реализации.</span><span class="sxs-lookup"><span data-stu-id="6ac42-112">This example first creates a new instance of the <xref:System.Security.Cryptography.Aes> implementation class.</span></span> <span data-ttu-id="6ac42-113">Он считывает значение вектора инициализации (IV) из управляемой переменной потока, `myStream` .</span><span class="sxs-lookup"><span data-stu-id="6ac42-113">It reads the initialization vector (IV) value from a managed stream variable, `myStream`.</span></span> <span data-ttu-id="6ac42-114">Затем он создает экземпляр <xref:System.Security.Cryptography.CryptoStream> объекта и инициализирует его значением `myStream` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="6ac42-114">Next it instantiates a <xref:System.Security.Cryptography.CryptoStream> object and initializes it to the value of the `myStream` instance.</span></span> <span data-ttu-id="6ac42-115"><xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType>Методу из <xref:System.Security.Cryptography.Aes> экземпляра передается значение IV и тот же ключ, который использовался для шифрования.</span><span class="sxs-lookup"><span data-stu-id="6ac42-115">The <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType> method from the <xref:System.Security.Cryptography.Aes> instance is passed the IV value and the same key that was used for encryption.</span></span>

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(
    myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(
    myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

<span data-ttu-id="6ac42-116">В следующем примере показан весь процесс создания потока, расшифровки потока, чтения из потока и закрытия потока.</span><span class="sxs-lookup"><span data-stu-id="6ac42-116">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="6ac42-117">Создается объект файлового потока, который считывает файл с именем *TestData.txt*.</span><span class="sxs-lookup"><span data-stu-id="6ac42-117">A file stream object is created that reads a file named *TestData.txt*.</span></span> <span data-ttu-id="6ac42-118">Затем файловый поток расшифровывается с помощью класса **CryptoStream** и класса **AES** .</span><span class="sxs-lookup"><span data-stu-id="6ac42-118">The file stream is then decrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="6ac42-119">В этом примере указывается значение ключа, которое используется в примере симметричного шифрования для [шифрования данных](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="6ac42-119">This example specifies key value that is used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="6ac42-120">Он не показывает код, необходимый для шифрования и передачи этих значений.</span><span class="sxs-lookup"><span data-stu-id="6ac42-120">It does not show the code needed to encrypt and transfer these values.</span></span>

:::code language="csharp" source="snippets/decrypting-data/csharp/aes-decrypt.cs":::
:::code language="vb" source="snippets/decrypting-data/vb/aes-decrypt.vb":::

<span data-ttu-id="6ac42-121">В предыдущем примере используется тот же ключ и алгоритм, который использовался в примере симметричного шифрования для [шифрования данных](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="6ac42-121">The preceding example uses the same key, and algorithm used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="6ac42-122">Он расшифровывает файл *TestData.txt* , созданный в этом примере, и отображает исходный текст в консоли.</span><span class="sxs-lookup"><span data-stu-id="6ac42-122">It decrypts the *TestData.txt* file that is created by that example and displays the original text on the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="6ac42-123">Асимметричная расшифровка</span><span class="sxs-lookup"><span data-stu-id="6ac42-123">Asymmetric decryption</span></span>

<span data-ttu-id="6ac42-124">Как правило, сторона (сторона А) создает как открытый, так и закрытый ключи и сохраняет их в памяти или в контейнере криптографических ключей.</span><span class="sxs-lookup"><span data-stu-id="6ac42-124">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="6ac42-125">Затем сторона А пересылает открытый ключ другой стороне (сторона Б).</span><span class="sxs-lookup"><span data-stu-id="6ac42-125">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="6ac42-126">С помощью открытого ключа сторона б шифрует данные и отправляет их обратно стороне A. После получения данных сторона A расшифровывает их с помощью закрытого ключа, который соответствует.</span><span class="sxs-lookup"><span data-stu-id="6ac42-126">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="6ac42-127">Расшифровка будет успешной только в том случае, если сторона А использует закрытый ключ, соответствующий открытому ключу, использованному стороной Б для шифрования данных.</span><span class="sxs-lookup"><span data-stu-id="6ac42-127">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="6ac42-128">Дополнительные сведения о хранении асимметричных ключей в безопасном контейнере криптографических ключей и последующем извлечении асимметричного ключа см. в разделе [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="6ac42-128">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="6ac42-129">Следующий пример иллюстрирует расшифровку двух массивов байтов, представляющих симметричный ключ и вектор инициализации.</span><span class="sxs-lookup"><span data-stu-id="6ac42-129">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="6ac42-130">Дополнительные сведения о способе извлечения асимметричного открытого ключа из объекта <xref:System.Security.Cryptography.RSA> в формате, допускающем простую отправку третьей стороне, см. в разделе [Encrypting Data](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="6ac42-130">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSA> object in a format that you can easily send to a third party, see [Encrypting Data](encrypting-data.md).</span></span>

```vb
'Create a new instance of the RSA class.
Dim rsa As RSA = RSA.Create()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, RSAEncryptionPadding.Pkcs1)
```

```csharp
//Create a new instance of the RSA class.
RSA rsa = RSA.Create();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , RSAEncryptionPadding.Pkcs1);
```

## <a name="see-also"></a><span data-ttu-id="6ac42-131">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6ac42-131">See also</span></span>

- [<span data-ttu-id="6ac42-132">Создание ключей для шифрования и расшифровки</span><span class="sxs-lookup"><span data-stu-id="6ac42-132">Generating keys for encryption and decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="6ac42-133">Шифрование данных</span><span class="sxs-lookup"><span data-stu-id="6ac42-133">Encrypting data</span></span>](encrypting-data.md)
- [<span data-ttu-id="6ac42-134">Службы шифрования</span><span class="sxs-lookup"><span data-stu-id="6ac42-134">Cryptographic services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="6ac42-135">Модель шифрования</span><span class="sxs-lookup"><span data-stu-id="6ac42-135">Cryptography model</span></span>](cryptography-model.md)
- [<span data-ttu-id="6ac42-136">Кроссплатформенное шифрование</span><span class="sxs-lookup"><span data-stu-id="6ac42-136">Cross-platform cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="6ac42-137">Уязвимости в учете времени при симметричной расшифровке в режиме CBC с использованием заполнения</span><span class="sxs-lookup"><span data-stu-id="6ac42-137">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="6ac42-138">ASP.NET Core Защита данных</span><span class="sxs-lookup"><span data-stu-id="6ac42-138">ASP.NET Core data protection</span></span>](/aspnet/core/security/data-protection/introduction)
