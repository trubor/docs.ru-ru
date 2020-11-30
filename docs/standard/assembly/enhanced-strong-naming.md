---
title: Усовершенствованное строгое именование
description: Подписи обычных строгих имен для сборок в .NET Framework имеют ограничения. Узнайте об усовершенствованном строгом именовании.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
ms.openlocfilehash: b9c690c77dafc247f7282c3f56384481efe53399
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731531"
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="d8ef3-104">Усовершенствованное строгое именование</span><span class="sxs-lookup"><span data-stu-id="d8ef3-104">Enhanced strong naming</span></span>

<span data-ttu-id="d8ef3-105">Подпись строгого имени — это механизм идентификации сборок в .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-105">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="d8ef3-106">Это цифровая подпись с открытым ключом, которая обычно используется для проверки целостности данных, передаваемых от инициатора (подписывающего) к получателю (проверяющему).</span><span class="sxs-lookup"><span data-stu-id="d8ef3-106">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="d8ef3-107">Эта подпись используется в виде уникального идентификатора сборки и гарантирует, что ссылки на сборку не являются неоднозначными.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-107">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="d8ef3-108">Подписывание сборки является частью процесса сборки, что затем проверяется при ее загрузке.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-108">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="d8ef3-109">Подписи строгого имени помогают предотвратить подделку сборки на стороне злоумышленника с последующей повторной подписью сборки оригинальным ключом подписавшего.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-109">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="d8ef3-110">Но ключи строгого имени не содержат никаких сведений об издателе, а также не содержат иерархию сертификатов.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-110">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="d8ef3-111">Подпись строгого имени не гарантирует, что подписавшему сборку человеку можно доверять, и не указывает на то, что человек является правомерным владельцем ключа; она означает только то, что владелец ключа подписал сборку.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-111">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="d8ef3-112">Поэтому не рекомендуется использовать подпись строгого имени как средство проверки безопасности на доверие к коду сторонних разработчиков.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-112">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="d8ef3-113">Рекомендуемым способом проверки подлинности кода является Microsoft Authenticode.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-113">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="d8ef3-114">Ограничения обычных строгих имен</span><span class="sxs-lookup"><span data-stu-id="d8ef3-114">Limitations of conventional strong names</span></span>  

 <span data-ttu-id="d8ef3-115">Технология строгого именования, используемая в версиях до .NET Framework 4.5, имеет указанные ниже недостатки:</span><span class="sxs-lookup"><span data-stu-id="d8ef3-115">The strong naming technology used in versions before the .NET Framework 4.5 has the following shortcomings:</span></span>  
  
- <span data-ttu-id="d8ef3-116">Ключи постоянно подвержены атакам, а улучшенные методы и оборудование облегчают поиск закрытого ключа по открытому.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-116">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="d8ef3-117">Для защиты от атак необходимы более длинные ключи.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-117">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="d8ef3-118">Версии .NET Framework до .NET Framework 4.5 предоставляют возможность подписывания с помощью ключа любого размера (размер по умолчанию — 1024 бита), но подпись сборки новым ключом испортит все двоичные файлы, ссылающиеся на старый идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-118">.NET Framework versions before the .NET Framework 4.5 provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="d8ef3-119">Поэтому изменение размера ключа подписи является крайне сложным, если необходимо обеспечить совместимость.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-119">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
- <span data-ttu-id="d8ef3-120">Подпись строгого имени поддерживает только алгоритм SHA-1.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-120">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="d8ef3-121">Недавно было показано, что алгоритма SHA-1 недостаточно для обеспечения безопасности хэширования.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-121">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="d8ef3-122">Поэтому необходим более надежный алгоритм (SHA-256 или выше).</span><span class="sxs-lookup"><span data-stu-id="d8ef3-122">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="d8ef3-123">Возможно, алгоритм SHA-1 утратит статус совместимого с FIPS, что станет проблемой для тех, кто предпочитает использовать только FIPS-совместимое программное обеспечение и алгоритмы.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-123">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="d8ef3-124">Преимущества улучшенных строгих имен</span><span class="sxs-lookup"><span data-stu-id="d8ef3-124">Advantages of enhanced strong names</span></span>  

 <span data-ttu-id="d8ef3-125">Основными преимуществами улучшенных строгих имен являются совместимость с уже существующими строгими именами и возможность утверждения эквивалентности одного идентификатора другому.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-125">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
- <span data-ttu-id="d8ef3-126">Разработчики, которые имеют уже существующие подписанные сборки, могут перенести формирование их идентификаторов на алгоритм SHA-2, сохранив при этом совместимость со сборками, которые ссылаются на старые идентификаторы.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-126">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
- <span data-ttu-id="d8ef3-127">Разработчики, которые создают новые сборки и не имеют существующих подписей строгого имени, могут использовать более безопасные алгоритмы SHA-2 и подписывать сборки так, как они делали всегда.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-127">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="use-enhanced-strong-names"></a><span data-ttu-id="d8ef3-128">Использование улучшенных строгих имен</span><span class="sxs-lookup"><span data-stu-id="d8ef3-128">Use enhanced strong names</span></span>  

 <span data-ttu-id="d8ef3-129">Ключи строгого имени состоят из ключа подписи и ключа удостоверения.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-129">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="d8ef3-130">Сборка подписывается с помощью ключа подписи и не зависит от ключа удостоверения.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-130">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="d8ef3-131">До выхода версии .NET Framework 4.5 эти ключи были идентичными.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-131">Prior to the .NET Framework 4.5, these two keys were identical.</span></span> <span data-ttu-id="d8ef3-132">Начиная с .NET Framework 4.5 ключ удостоверения остается таким же, как и в более ранних версиях платформы .NET Framework, а ключ подписи улучшается с использованием более надежного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-132">Starting with the .NET Framework 4.5, the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="d8ef3-133">Кроме того, ключ подписи подписывается ключом удостоверения для создания подписи другой стороны.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-133">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="d8ef3-134">Атрибут <xref:System.Reflection.AssemblySignatureKeyAttribute> позволяет метаданным сборки использовать уже существующий открытый ключ для идентификации сборки, что позволяет старым ссылкам на сборки продолжать работать.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-134">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="d8ef3-135">Атрибут <xref:System.Reflection.AssemblySignatureKeyAttribute> использует подпись другой стороны для проверки того, является ли владелец нового ключа подписи также владельцем старого ключа удостоверения.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-135">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="sign-with-sha-2-without-key-migration"></a><span data-ttu-id="d8ef3-136">Подписывание с использованием SHA-2 без переноса ключа</span><span class="sxs-lookup"><span data-stu-id="d8ef3-136">Sign with SHA-2, without key migration</span></span>  

 <span data-ttu-id="d8ef3-137">Чтобы подписать сборку без переноса подписи строгого имени, выполните следующие команды в командной строке:</span><span class="sxs-lookup"><span data-stu-id="d8ef3-137">Run the following commands from a command prompt to sign an assembly without migrating a strong name signature:</span></span>  
  
1. <span data-ttu-id="d8ef3-138">Создайте ключ удостоверения (если необходимо).</span><span class="sxs-lookup"><span data-stu-id="d8ef3-138">Generate the new identity key (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. <span data-ttu-id="d8ef3-139">Извлеките открытый ключ удостоверения и укажите, что при подписывании этим ключом необходимо использовать алгоритм SHA-2.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-139">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="d8ef3-140">Используйте отложенную подпись сборки с помощью файла с открытым ключом удостоверения.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-140">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. <span data-ttu-id="d8ef3-141">Повторно подпишите сборку с помощью полной пары ключей удостоверения.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-141">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a><span data-ttu-id="d8ef3-142">Подписывание с использованием SHA-2 с переносом ключа</span><span class="sxs-lookup"><span data-stu-id="d8ef3-142">Sign with SHA-2, with key migration</span></span>  

 <span data-ttu-id="d8ef3-143">Чтобы подписать сборку с переносом подписи строгого имени, выполните следующие команды в командной строке:</span><span class="sxs-lookup"><span data-stu-id="d8ef3-143">Run the following commands from a command prompt to sign an assembly with a migrated strong name signature.</span></span>  
  
1. <span data-ttu-id="d8ef3-144">Создайте пару ключей удостоверения и подписи (если необходимо).</span><span class="sxs-lookup"><span data-stu-id="d8ef3-144">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. <span data-ttu-id="d8ef3-145">Извлеките открытый ключ подписи и укажите, что при подписывании этим ключом необходимо использовать алгоритм SHA-2.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-145">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="d8ef3-146">Извлеките открытый ключ удостоверения, определяющий хэш-алгоритм, с помощью которого создается подпись другой стороны.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-146">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. <span data-ttu-id="d8ef3-147">Создайте параметры для атрибута <xref:System.Reflection.AssemblySignatureKeyAttribute> и прикрепите атрибут к сборке.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-147">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    <span data-ttu-id="d8ef3-148">Вы увидите приблизительно следующее.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-148">This produces output similar to the following.</span></span>

    ```output
    Information for key migration attribute.
    (System.Reflection.AssemblySignatureKeyAttribute):
    publicKey=
    002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519
    d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936
    e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b4
    3893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a3
    4d153cdd

    counterSignature=
    e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91eb
    e1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8
    ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3
    ae5fec2c682e57b7442738
    ```

    <span data-ttu-id="d8ef3-149">Эти выходные данные затем могут быть преобразованы в AssemblySignatureKeyAttribute.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-149">This output can then be transformed into an AssemblySignatureKeyAttribute.</span></span>

    ```csharp
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. <span data-ttu-id="d8ef3-150">Используйте отложенную подпись сборки с помощью открытого ключа удостоверения.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-150">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. <span data-ttu-id="d8ef3-151">Подпишите сборку с помощью полной пары ключей удостоверения.</span><span class="sxs-lookup"><span data-stu-id="d8ef3-151">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d8ef3-152">См. также</span><span class="sxs-lookup"><span data-stu-id="d8ef3-152">See also</span></span>

- [<span data-ttu-id="d8ef3-153">Создание и использование сборок со строгими именами</span><span class="sxs-lookup"><span data-stu-id="d8ef3-153">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
