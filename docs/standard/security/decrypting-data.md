---
title: Расшифровка данных
description: Узнайте, как расшифровать данные в .NET с помощью симметричного алгоритма или асимметричного алгоритма.
ms.date: 04/19/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: 1b12e4250f3b2345afd05dbe3c257eb3e7277634
ms.sourcegitcommit: 8f71a6c655a9c39d5223401aed76c02ba00e03ee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2021
ms.locfileid: "107740348"
---
# <a name="decrypting-data"></a>Расшифровка данных

Расшифровка представляет собой операцию, обратную операции шифрования. Для шифрования с секретным ключом необходимо знать как ключ, так и вектор инициализации, которые использовались при шифровании данных. Для шифрования с открытым ключом необходимо знать либо открытый ключ (если данные были зашифрованы при помощи закрытого ключа), либо закрытый ключ (если данные были зашифрованы при помощи открытого ключа).

## <a name="symmetric-decryption"></a>Симметричная расшифровка

Расшифровка данных, зашифрованных при помощи симметричных алгоритмов, похожа на процесс, используемый для шифрования данных при помощи симметричных алгоритмов. <xref:System.Security.Cryptography.CryptoStream>Класс используется с симметричными криптографическими классами, предоставляемыми .NET для расшифровки данных, считанных из любого управляемого объекта потока.

В следующем примере показано, как создать новый экземпляр класса реализации по умолчанию для <xref:System.Security.Cryptography.Aes> алгоритма. Экземпляр используется для расшифровки <xref:System.Security.Cryptography.CryptoStream> объекта. В этом примере сначала создается новый экземпляр <xref:System.Security.Cryptography.Aes> класса реализации. Он считывает значение вектора инициализации (IV) из управляемой переменной потока, `fileStream` . Затем он создает экземпляр <xref:System.Security.Cryptography.CryptoStream> объекта и инициализирует его значением `fileStream` экземпляра. <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType>Методу из <xref:System.Security.Cryptography.Aes> экземпляра передается значение IV и тот же ключ, который использовался для шифрования.

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(
    fileStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(
    fileStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

В следующем примере показан весь процесс создания потока, расшифровки потока, чтения из потока и закрытия потока. Создается объект файлового потока, который считывает файл с именем *TestData.txt*. Затем файловый поток расшифровывается с помощью класса **CryptoStream** и класса **AES** . В этом примере указывается значение ключа, которое используется в примере симметричного шифрования для [шифрования данных](encrypting-data.md). Он не показывает код, необходимый для шифрования и передачи этих значений.

:::code language="csharp" source="snippets/decrypting-data/csharp/aes-decrypt.cs":::
:::code language="vb" source="snippets/decrypting-data/vb/aes-decrypt.vb":::

В предыдущем примере используется тот же ключ и алгоритм, который использовался в примере симметричного шифрования для [шифрования данных](encrypting-data.md). Он расшифровывает файл *TestData.txt* , созданный в этом примере, и отображает исходный текст в консоли.

## <a name="asymmetric-decryption"></a>Асимметричная расшифровка

Как правило, сторона (сторона А) создает как открытый, так и закрытый ключи и сохраняет их в памяти или в контейнере криптографических ключей. Затем сторона А пересылает открытый ключ другой стороне (сторона Б). С помощью открытого ключа сторона б шифрует данные и отправляет их обратно стороне A. После получения данных сторона A расшифровывает их с помощью закрытого ключа, который соответствует. Расшифровка будет успешной только в том случае, если сторона А использует закрытый ключ, соответствующий открытому ключу, использованному стороной Б для шифрования данных.

Дополнительные сведения о хранении асимметричных ключей в безопасном контейнере криптографических ключей и последующем извлечении асимметричного ключа см. в разделе [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).

Следующий пример иллюстрирует расшифровку двух массивов байтов, представляющих симметричный ключ и вектор инициализации. Дополнительные сведения о способе извлечения асимметричного открытого ключа из объекта <xref:System.Security.Cryptography.RSA> в формате, допускающем простую отправку третьей стороне, см. в разделе [Encrypting Data](encrypting-data.md).

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

## <a name="see-also"></a>См. также раздел

- [Создание ключей для шифрования и расшифровки](generating-keys-for-encryption-and-decryption.md)
- [Шифрование данных](encrypting-data.md)
- [Службы шифрования](cryptographic-services.md)
- [Модель шифрования](cryptography-model.md)
- [Кроссплатформенное шифрование](cross-platform-cryptography.md)
- [Уязвимости в учете времени при симметричной расшифровке в режиме CBC с использованием заполнения](vulnerabilities-cbc-mode.md)
- [ASP.NET Core Защита данных](/aspnet/core/security/data-protection/introduction)
