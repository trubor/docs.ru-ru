---
description: Дополнительные сведения см. в статье как расшифровать XML-элементы с помощью симметричных ключей.
title: Практическое руководство. Расшифровка XML-элементов с помощью симметричных ключей
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.Aes class
- XML encryption
- decryption
ms.assetid: 6038aff0-f92c-4e29-a618-d793410410d8
ms.openlocfilehash: 894b202143daf2af767fd9877266e2323e0057e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685183"
---
# <a name="how-to-decrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="d1621-103">Практическое руководство. Расшифровка XML-элементов с помощью симметричных ключей</span><span class="sxs-lookup"><span data-stu-id="d1621-103">How to: Decrypt XML Elements with Symmetric Keys</span></span>

<span data-ttu-id="d1621-104">Классы можно использовать в пространстве имен <xref:System.Security.Cryptography.Xml> для шифрования элемента XML-документа.</span><span class="sxs-lookup"><span data-stu-id="d1621-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="d1621-105">Шифрование XML-данных позволяет хранить или передавать важные XML-данные, не беспокоясь о том, что они могут быть прочитаны.</span><span class="sxs-lookup"><span data-stu-id="d1621-105">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="d1621-106">Этот пример кода расшифровывает XML-элемент с помощью алгоритма AES (AES).</span><span class="sxs-lookup"><span data-stu-id="d1621-106">This code example decrypts an XML element using the Advanced Encryption Standard (AES) algorithm.</span></span>
  
 <span data-ttu-id="d1621-107">Дополнительные сведения о шифровании XML-элемента с помощью этой процедуры см. [в разделе как шифровать XML-элементы с симметричными ключами](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="d1621-107">For information about how to encrypt an XML element using this procedure, see [How to: Encrypt XML Elements with Symmetric Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="d1621-108">При использовании симметричного алгоритма, такого как AES, для шифрования XML-данных необходимо использовать один и тот же ключ как для шифрования, так и для расшифровки XML-данных.</span><span class="sxs-lookup"><span data-stu-id="d1621-108">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="d1621-109">В этом примере предполагается, что зашифрованные XML-данные были зашифрованы при помощи того же ключа и что стороны, выполняющие шифрование и расшифровку, согласуют между собой используемый алгоритм и ключ.</span><span class="sxs-lookup"><span data-stu-id="d1621-109">The example in this procedure assumes that the encrypted XML was encrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="d1621-110">В этом примере ключ AES не сохраняется и не шифруется внутри зашифрованного XML-документа.</span><span class="sxs-lookup"><span data-stu-id="d1621-110">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="d1621-111">Этот пример подходит для ситуаций, где отдельному приложению требуется зашифровать данные на основе хранящегося в памяти сеансового ключа или на основе криптографически стойкого ключа, полученного из пароля.</span><span class="sxs-lookup"><span data-stu-id="d1621-111">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="d1621-112">В ситуациях, когда два приложения и более нуждаются в общем доступе к зашифрованным XML-данным, рекомендуется использовать схему шифрования, основанную на асимметричном алгоритме или сертификате X.509.</span><span class="sxs-lookup"><span data-stu-id="d1621-112">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="d1621-113">Расшифровка XML-элемента при помощи симметричного ключа</span><span class="sxs-lookup"><span data-stu-id="d1621-113">To decrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="d1621-114">Зашифруйте XML-элемент с помощью ранее созданного ключа, используя методы, описанные в разделе [как шифровать XML-элементы с симметричными ключами](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="d1621-114">Encrypt an XML element with the previously generated key using the techniques described in [How to: Encrypt XML Elements with Symmetric Keys](how-to-encrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
2. <span data-ttu-id="d1621-115">Найдите `EncryptedData` элемент> <(определяется стандартом шифрования XML) в <xref:System.Xml.XmlDocument> объекте, содержащем зашифрованный XML-код, и создайте новый <xref:System.Xml.XmlElement> объект для представления этого элемента.</span><span class="sxs-lookup"><span data-stu-id="d1621-115">Find the <`EncryptedData`> element (defined by the XML Encryption standard) in an <xref:System.Xml.XmlDocument> object that contains the encrypted XML and create a new <xref:System.Xml.XmlElement> object to represent that element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementSymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#10)]  
  
3. <span data-ttu-id="d1621-116">Создайте объект <xref:System.Security.Cryptography.Xml.EncryptedData>, загрузив необработанные XML-данные из ранее созданного объекта <xref:System.Xml.XmlElement>.</span><span class="sxs-lookup"><span data-stu-id="d1621-116">Create an <xref:System.Security.Cryptography.Xml.EncryptedData> object by loading the raw XML data from the previously created <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementSymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#11)]  
  
4. <span data-ttu-id="d1621-117">Создайте новый объект <xref:System.Security.Cryptography.Xml.EncryptedXml> и используйте его для расшифровки XML-данных при помощи того же ключа, который использовался для шифрования.</span><span class="sxs-lookup"><span data-stu-id="d1621-117">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object and use it to decrypt the XML data using the same key that was used for encryption.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementSymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#12)]  
  
5. <span data-ttu-id="d1621-118">Замените зашифрованный элемент на вновь расшифрованный элемент в формате открытого текста в XML-документе.</span><span class="sxs-lookup"><span data-stu-id="d1621-118">Replace the encrypted element with the newly decrypted plaintext element within the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementSymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="d1621-119">Пример</span><span class="sxs-lookup"><span data-stu-id="d1621-119">Example</span></span>  

 <span data-ttu-id="d1621-120">В этом примере предполагается, что файл с именем `"test.xml"` существует в том же каталоге, что и скомпилированная программа.</span><span class="sxs-lookup"><span data-stu-id="d1621-120">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="d1621-121">Кроме того, предполагается, что `"test.xml"` содержит элемент `"creditcard"`.</span><span class="sxs-lookup"><span data-stu-id="d1621-121">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="d1621-122">Можно поместить следующий XML-код в файл с именем `test.xml` и использовать его вместе с данным примером.</span><span class="sxs-lookup"><span data-stu-id="d1621-122">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d1621-123">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="d1621-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="d1621-124">В проекте, предназначенном для платформа .NET Framework, включите ссылку на `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="d1621-124">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="d1621-125">В проекте, ориентированном на .NET Core или .NET 5, установите пакет NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="d1621-125">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="d1621-126">Включите следующие пространства имен: <xref:System.Xml>, <xref:System.Security.Cryptography> и <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="d1621-126">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="d1621-127">Безопасность .NET</span><span class="sxs-lookup"><span data-stu-id="d1621-127">.NET Security</span></span>
  
<span data-ttu-id="d1621-128">Никогда не храните криптографический ключ в формате обычного текста и не передавайте этот ключ в таком формате между компьютерами.</span><span class="sxs-lookup"><span data-stu-id="d1621-128">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  
  
<span data-ttu-id="d1621-129">После завершения работы с симметричным криптографическим ключом очистите его из памяти, установив для каждого байта нулевое значение или вызвав метод <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> управляемого класса шифрования.</span><span class="sxs-lookup"><span data-stu-id="d1621-129">When you are done using a symmetric cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1621-130">См. также</span><span class="sxs-lookup"><span data-stu-id="d1621-130">See also</span></span>

- [<span data-ttu-id="d1621-131">Модель криптографии</span><span class="sxs-lookup"><span data-stu-id="d1621-131">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="d1621-132">службы шифрования</span><span class="sxs-lookup"><span data-stu-id="d1621-132">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="d1621-133">Кросс-платформенная криптография</span><span class="sxs-lookup"><span data-stu-id="d1621-133">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="d1621-134">Практическое руководство. Шифрование XML-элементов с помощью симметричного ключа</span><span class="sxs-lookup"><span data-stu-id="d1621-134">How to: Encrypt XML Elements with Symmetric Keys</span></span>](how-to-encrypt-xml-elements-with-symmetric-keys.md)
- [<span data-ttu-id="d1621-135">ASP.NET Core Защита данных</span><span class="sxs-lookup"><span data-stu-id="d1621-135">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
