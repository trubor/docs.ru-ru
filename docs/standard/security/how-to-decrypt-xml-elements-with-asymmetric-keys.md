---
description: Дополнительные сведения см. в статье как расшифровать XML-элементы с помощью асимметричных ключей.
title: Практическое руководство. Расшифровка XML-элементов с помощью асимметричных ключей
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSA class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
ms.openlocfilehash: bd3bd142aa5800efa83bc20a4b1af6d5bc61eba2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675576"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="fc07e-103">Практическое руководство. Расшифровка XML-элементов с помощью асимметричных ключей</span><span class="sxs-lookup"><span data-stu-id="fc07e-103">How to: Decrypt XML Elements with Asymmetric Keys</span></span>

<span data-ttu-id="fc07e-104">Классы можно использовать в пространстве имен <xref:System.Security.Cryptography.Xml> для шифрования и расшифровки элемента XML-документа.</span><span class="sxs-lookup"><span data-stu-id="fc07e-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="fc07e-105">Шифрование XML-данных — это стандартный способ обмена зашифрованными XML-данными и их хранения, позволяющий не беспокоиться о том, что эти данные могут быть прочитаны.</span><span class="sxs-lookup"><span data-stu-id="fc07e-105">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="fc07e-106">Дополнительные сведения о стандарте шифрования XML см. в разделе рекомендации по [синтаксису XML-подписи](https://www.w3.org/TR/xmldsig-core/)консорциум W3C (W3C) и обработке.</span><span class="sxs-lookup"><span data-stu-id="fc07e-106">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  

> [!NOTE]
> <span data-ttu-id="fc07e-107">Код, приведенный в этой статье, относится к Windows.</span><span class="sxs-lookup"><span data-stu-id="fc07e-107">The code in this article applies to Windows.</span></span>

<span data-ttu-id="fc07e-108">В примере в этой процедуре выполняется расшифровка XML-элемента, который был зашифрован с помощью методов, описанных в разделе [инструкции. Шифрование XML-элементов с помощью асимметричных ключей](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="fc07e-108">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="fc07e-109">Он находит `EncryptedData` элемент> <, расшифровывает элемент, а затем заменяет элемент исходным XML-элементом с открытым текстом.</span><span class="sxs-lookup"><span data-stu-id="fc07e-109">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
<span data-ttu-id="fc07e-110">Этот пример выполняет расшифровку XML-элемента с использованием двух ключей.</span><span class="sxs-lookup"><span data-stu-id="fc07e-110">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="fc07e-111">Он извлекает ранее созданный закрытый ключ RSA из контейнера ключей, а затем использует ключ RSA для расшифровки ключа сеанса, хранящегося в `EncryptedKey` элементе <> элемента <`EncryptedData`>.</span><span class="sxs-lookup"><span data-stu-id="fc07e-111">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="fc07e-112">После этого пример использует сеансовый ключ для расшифровки XML-элемента.</span><span class="sxs-lookup"><span data-stu-id="fc07e-112">The example then uses the session key to decrypt the XML element.</span></span>  
  
<span data-ttu-id="fc07e-113">Этот пример подходит в ситуациях, когда нескольким приложениям нужен общий доступ к зашифрованным данным или когда приложению требуется сохранять зашифрованные данные между запусками.</span><span class="sxs-lookup"><span data-stu-id="fc07e-113">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="fc07e-114">Расшифровка XML-элемента с использованием асимметричного ключа</span><span class="sxs-lookup"><span data-stu-id="fc07e-114">To decrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="fc07e-115">Создайте объект <xref:System.Security.Cryptography.CspParameters> и укажите имя контейнера ключей.</span><span class="sxs-lookup"><span data-stu-id="fc07e-115">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="fc07e-116">Извлеките ранее созданный асимметричный ключ из контейнера при помощи объекта <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="fc07e-116">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="fc07e-117">Этот ключ автоматически извлекается из контейнера ключей по имени при передаче объекта <xref:System.Security.Cryptography.CspParameters> в конструктор <xref:System.Security.Cryptography.RSACryptoServiceProvider>.</span><span class="sxs-lookup"><span data-stu-id="fc07e-117">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="fc07e-118">Создайте новый объект <xref:System.Security.Cryptography.Xml.EncryptedXml> для расшифровки документа.</span><span class="sxs-lookup"><span data-stu-id="fc07e-118">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. <span data-ttu-id="fc07e-119">Добавьте сопоставление ключа и имени, чтобы связать ключ RSA с элементом в документе, который следует расшифровать.</span><span class="sxs-lookup"><span data-stu-id="fc07e-119">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="fc07e-120">Для ключа необходимо использовать то же имя, которое использовалось при шифровании документа.</span><span class="sxs-lookup"><span data-stu-id="fc07e-120">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="fc07e-121">Обратите внимание, что это имя отличается от имени, используемого для определения ключа в контейнере ключей, заданном на шаге 1.</span><span class="sxs-lookup"><span data-stu-id="fc07e-121">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. <span data-ttu-id="fc07e-122">Вызовите <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> метод, чтобы расшифровать `EncryptedData` элемент> <.</span><span class="sxs-lookup"><span data-stu-id="fc07e-122">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="fc07e-123">Этот метод использует ключ RSA для расшифровки сеансового ключа и автоматически использует этот сеансовый ключ для расшифровки XML-элемента.</span><span class="sxs-lookup"><span data-stu-id="fc07e-123">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="fc07e-124">Он также автоматически заменяет элемент <`EncryptedData`> исходным текстом.</span><span class="sxs-lookup"><span data-stu-id="fc07e-124">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. <span data-ttu-id="fc07e-125">Сохраните XML-документ.</span><span class="sxs-lookup"><span data-stu-id="fc07e-125">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="fc07e-126">Пример</span><span class="sxs-lookup"><span data-stu-id="fc07e-126">Example</span></span>

<span data-ttu-id="fc07e-127">В этом примере предполагается, что файл с именем `test.xml` существует в том же каталоге, что и скомпилированная программа.</span><span class="sxs-lookup"><span data-stu-id="fc07e-127">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="fc07e-128">Также предполагается, что `test.xml` содержит XML-элемент, который был зашифрован с помощью методов, описанных в разделе [как шифровать XML-элементы с помощью асимметричных ключей](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span><span class="sxs-lookup"><span data-stu-id="fc07e-128">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
[!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
[!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fc07e-129">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="fc07e-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="fc07e-130">В проекте, предназначенном для платформа .NET Framework, включите ссылку на `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="fc07e-130">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="fc07e-131">В проекте, ориентированном на .NET Core или .NET 5, установите пакет NuGet [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span><span class="sxs-lookup"><span data-stu-id="fc07e-131">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="fc07e-132">Включите следующие пространства имен: <xref:System.Xml>, <xref:System.Security.Cryptography> и <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="fc07e-132">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="fc07e-133">Безопасность .NET</span><span class="sxs-lookup"><span data-stu-id="fc07e-133">.NET Security</span></span>  

<span data-ttu-id="fc07e-134">Никогда не храните симметричный криптографический ключ в формате обычного текста и не передавайте этот симметричный ключ в таком формате между компьютерами.</span><span class="sxs-lookup"><span data-stu-id="fc07e-134">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="fc07e-135">Кроме того, не следует хранить или передавать закрытый ключ из пары асимметричных ключей в виде обычного текста.</span><span class="sxs-lookup"><span data-stu-id="fc07e-135">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="fc07e-136">Дополнительные сведения о симметричных и асимметричных криптографических ключах см. в разделе [Создание ключей для шифрования и расшифровки](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="fc07e-136">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="fc07e-137">Не следует внедрять ключ непосредственно в исходный код.</span><span class="sxs-lookup"><span data-stu-id="fc07e-137">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="fc07e-138">Внедренные ключи можно легко считывать из сборки с помощью [Ildasm.exe (IL)](../../framework/tools/ildasm-exe-il-disassembler.md) или путем открытия сборки в текстовом редакторе, например в блокноте.</span><span class="sxs-lookup"><span data-stu-id="fc07e-138">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="fc07e-139">После завершения работы с криптографическим ключом очистите его из памяти, установив для каждого байта нулевое значение или вызвав метод <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> управляемого класса шифрования.</span><span class="sxs-lookup"><span data-stu-id="fc07e-139">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="fc07e-140">Иногда криптографические ключи можно считывать из памяти отладчиком или с жесткого диска, если область памяти выгружается на диск.</span><span class="sxs-lookup"><span data-stu-id="fc07e-140">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc07e-141">См. также</span><span class="sxs-lookup"><span data-stu-id="fc07e-141">See also</span></span>

- [<span data-ttu-id="fc07e-142">Модель криптографии</span><span class="sxs-lookup"><span data-stu-id="fc07e-142">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="fc07e-143">службы шифрования</span><span class="sxs-lookup"><span data-stu-id="fc07e-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="fc07e-144">Кросс-платформенная криптография</span><span class="sxs-lookup"><span data-stu-id="fc07e-144">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="fc07e-145">Практическое руководство. Шифрование XML-элементов с помощью асимметричных ключей</span><span class="sxs-lookup"><span data-stu-id="fc07e-145">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](how-to-encrypt-xml-elements-with-asymmetric-keys.md)
- [<span data-ttu-id="fc07e-146">ASP.NET Core Защита данных</span><span class="sxs-lookup"><span data-stu-id="fc07e-146">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
