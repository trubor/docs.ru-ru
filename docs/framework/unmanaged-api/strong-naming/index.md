---
description: 'Узнайте подробнее о: Строгое именование (справочник по управляемым API)'
title: Строгое именование (справочник по управляемым API)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 058cc51d8e9eb2ef4a2d0670811aefcd32dafb6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646365"
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="55d1c-103">Строгое именование (справочник по управляемым API)</span><span class="sxs-lookup"><span data-stu-id="55d1c-103">Strong Naming (Unmanaged API Reference)</span></span>

<span data-ttu-id="55d1c-104">API строгого именования позволяет клиенту администрировать подписание сборок строгим именем.</span><span class="sxs-lookup"><span data-stu-id="55d1c-104">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="55d1c-105">При подписи сборки строгим именем в файл, содержащий манифест сборки, добавляется зашифрованный открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="55d1c-105">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="55d1c-106">Подпись строгим именем гарантирует уникальность имени, предотвращает подмену имени и после разрешения ссылки предоставляет уникальный идентификатор вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="55d1c-106">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="55d1c-107">Однако со строгим именем не связано никакого уровня доверия.</span><span class="sxs-lookup"><span data-stu-id="55d1c-107">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55d1c-108">в этом разделе</span><span class="sxs-lookup"><span data-stu-id="55d1c-108">In This Section</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55d1c-109">Все эти функции являются нерекомендуемыми начиная с .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-109">All of these functions have been deprecated starting with the .NET Framework 4.</span></span> <span data-ttu-id="55d1c-110">Рекомендуемые альтернативы см. в интерфейсе [ICLRStrongName](../hosting/iclrstrongname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="55d1c-110">For suggested alternatives, see the [ICLRStrongName](../hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="55d1c-111">Функция GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="55d1c-111">GetHashFromAssemblyFile Function</span></span>](gethashfromassemblyfile-function.md)  
 <span data-ttu-id="55d1c-112">Получает хэш указанного файла сборки с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="55d1c-112">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="55d1c-113">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-113">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-114">Функция GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="55d1c-114">GetHashFromAssemblyFileW Function</span></span>](gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="55d1c-115">Получает хэш файла сборки, указанного строкой Юникода, с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="55d1c-115">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="55d1c-116">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-116">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-117">Функция GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="55d1c-117">GetHashFromBlob Function</span></span>](gethashfromblob-function.md)  
 <span data-ttu-id="55d1c-118">Получает хэш сборки по указанному адресу памяти с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="55d1c-118">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="55d1c-119">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-119">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-120">Функция GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="55d1c-120">GetHashFromFile Function</span></span>](gethashfromfile-function.md)  
 <span data-ttu-id="55d1c-121">Создает хэш содержимого указанного файла.</span><span class="sxs-lookup"><span data-stu-id="55d1c-121">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="55d1c-122">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-122">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-123">Функция GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="55d1c-123">GetHashFromFileW Function</span></span>](gethashfromfilew-function.md)  
 <span data-ttu-id="55d1c-124">Создает хэш содержимого файла, указанного строкой Юникода.</span><span class="sxs-lookup"><span data-stu-id="55d1c-124">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="55d1c-125">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-125">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-126">Функция GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="55d1c-126">GetHashFromHandle Function</span></span>](gethashfromhandle-function.md)  
 <span data-ttu-id="55d1c-127">Создает хэш содержимого файла с заданным дескриптором файла с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="55d1c-127">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="55d1c-128">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-128">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-129">Функция StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="55d1c-129">StrongNameCompareAssemblies Function</span></span>](strongnamecompareassemblies-function.md)  
 <span data-ttu-id="55d1c-130">Определяет, отличаются ли две сборки только подписями строгого имени.</span><span class="sxs-lookup"><span data-stu-id="55d1c-130">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="55d1c-131">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-131">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-132">Функция StrongNameErrorInfo</span><span class="sxs-lookup"><span data-stu-id="55d1c-132">StrongNameErrorInfo Function</span></span>](strongnameerrorinfo-function.md)  
 <span data-ttu-id="55d1c-133">Получает код последней ошибки, вызванной одной из функций строгого имени.</span><span class="sxs-lookup"><span data-stu-id="55d1c-133">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="55d1c-134">Функция StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="55d1c-134">StrongNameFreeBuffer Function</span></span>](strongnamefreebuffer-function.md)  
 <span data-ttu-id="55d1c-135">Освобождает память, выделенную предыдущим вызовом функции строгого имени, такой как [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md) или [StrongNameSignatureGeneration ](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="55d1c-135">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="55d1c-136">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-136">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-137">Функция StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="55d1c-137">StrongNameGetBlob Function</span></span>](strongnamegetblob-function.md)  
 <span data-ttu-id="55d1c-138">Заполняет указанный буфер двоичным представлением исполняемого файла по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="55d1c-138">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="55d1c-139">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-139">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-140">Функция StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="55d1c-140">StrongNameGetBlobFromImage Function</span></span>](strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="55d1c-141">Получает двоичное представление образа сборки по указанному адресу памяти.</span><span class="sxs-lookup"><span data-stu-id="55d1c-141">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="55d1c-142">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-142">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-143">Функция StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="55d1c-143">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)  
 <span data-ttu-id="55d1c-144">Получает открытый ключ из пары закрытого и открытого ключей.</span><span class="sxs-lookup"><span data-stu-id="55d1c-144">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="55d1c-145">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-145">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-146">Функция StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="55d1c-146">StrongNameHashSize Function</span></span>](strongnamehashsize-function.md)  
 <span data-ttu-id="55d1c-147">Получает размер буфера, необходимый для хэша, с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="55d1c-147">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="55d1c-148">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-148">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-149">Функция StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="55d1c-149">StrongNameKeyDelete Function</span></span>](strongnamekeydelete-function.md)  
 <span data-ttu-id="55d1c-150">Удаляет указанный контейнер ключей.</span><span class="sxs-lookup"><span data-stu-id="55d1c-150">Deletes the specified key container.</span></span> <span data-ttu-id="55d1c-151">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-151">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-152">Функция StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="55d1c-152">StrongNameKeyGen Function</span></span>](strongnamekeygen-function.md)  
 <span data-ttu-id="55d1c-153">Создает пару открытого и закрытого ключей для использования строгого имени.</span><span class="sxs-lookup"><span data-stu-id="55d1c-153">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="55d1c-154">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-154">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-155">Функция StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="55d1c-155">StrongNameKeyGenEx Function</span></span>](strongnamekeygenex-function.md)  
 <span data-ttu-id="55d1c-156">Создает пару открытого и закрытого ключей с заданным размером для использования строгого имени.</span><span class="sxs-lookup"><span data-stu-id="55d1c-156">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="55d1c-157">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-157">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-158">Функция StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="55d1c-158">StrongNameKeyInstall Function</span></span>](strongnamekeyinstall-function.md)  
 <span data-ttu-id="55d1c-159">Импортирует пару открытого и закрытого ключей в контейнер.</span><span class="sxs-lookup"><span data-stu-id="55d1c-159">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="55d1c-160">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-160">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-161">Функция StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="55d1c-161">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="55d1c-162">Создает подпись строгого имени для указанной сборки.</span><span class="sxs-lookup"><span data-stu-id="55d1c-162">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="55d1c-163">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-163">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-164">Функция StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="55d1c-164">StrongNameSignatureGenerationEx Function</span></span>](strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="55d1c-165">Создает подпись строгого имени для указанной сборки в зависимости от указанных флагов.</span><span class="sxs-lookup"><span data-stu-id="55d1c-165">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="55d1c-166">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-166">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-167">Функция StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="55d1c-167">StrongNameSignatureSize Function</span></span>](strongnamesignaturesize-function.md)  
 <span data-ttu-id="55d1c-168">Возвращает размер подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="55d1c-168">Returns the size of the strong name signature.</span></span> <span data-ttu-id="55d1c-169">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-169">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-170">Функция StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="55d1c-170">StrongNameSignatureVerification Function</span></span>](strongnamesignatureverification-function.md)  
 <span data-ttu-id="55d1c-171">Получает значение, указывающее, содержит ли находящийся по указанному пути манифест сборки подпись строгого имени, которая проверяется в соответствии с заданными флагами.</span><span class="sxs-lookup"><span data-stu-id="55d1c-171">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="55d1c-172">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-172">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-173">Функция StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="55d1c-173">StrongNameSignatureVerificationEx Function</span></span>](strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="55d1c-174">Получает значение, указывающее, содержит ли находящийся по указанному пути манифест сборки подпись строгого имени.</span><span class="sxs-lookup"><span data-stu-id="55d1c-174">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="55d1c-175">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-175">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-176">Функция StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="55d1c-176">StrongNameSignatureVerificationFromImage Function</span></span>](strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="55d1c-177">Проверяет допустимость сборки, которая уже была сопоставлена с памятью, для связанного открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="55d1c-177">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="55d1c-178">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-178">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-179">Функция StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="55d1c-179">StrongNameTokenFromAssembly Function</span></span>](strongnametokenfromassembly-function.md)  
 <span data-ttu-id="55d1c-180">Создает маркер строгого имени из указанного файла сборки.</span><span class="sxs-lookup"><span data-stu-id="55d1c-180">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="55d1c-181">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-181">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-182">Функция StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="55d1c-182">StrongNameTokenFromAssemblyEx Function</span></span>](strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="55d1c-183">Создает маркер строгого имени из указанного файла сборки и возвращает открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="55d1c-183">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="55d1c-184">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-184">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-185">Функция StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="55d1c-185">StrongNameTokenFromPublicKey Function</span></span>](strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="55d1c-186">Получает маркер, представляющий открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="55d1c-186">Gets a token representing a public key.</span></span> <span data-ttu-id="55d1c-187">Является нерекомендуемым начиная с версии .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="55d1c-187">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="55d1c-188">Структура PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="55d1c-188">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)  
 <span data-ttu-id="55d1c-189">Представляет открытый ключ из пары открытого и закрытого ключей в двоичном формате.</span><span class="sxs-lookup"><span data-stu-id="55d1c-189">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55d1c-190">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="55d1c-190">See also</span></span>

- [<span data-ttu-id="55d1c-191">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="55d1c-191">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="55d1c-192">Справочник по неуправляемым API</span><span class="sxs-lookup"><span data-stu-id="55d1c-192">Unmanaged API Reference</span></span>](../index.md)
