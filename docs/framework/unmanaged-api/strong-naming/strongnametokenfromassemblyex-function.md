---
description: Дополнительные сведения о функции StrongNameTokenFromAssemblyEx
title: Функция StrongNameTokenFromAssemblyEx
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
ms.openlocfilehash: 4ca08c8cfa90415723fc2632e32aa8f45c334db3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636287"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="e76b0-103">Функция StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="e76b0-103">StrongNameTokenFromAssemblyEx Function</span></span>

<span data-ttu-id="e76b0-104">Создает маркер строгого имени из указанного файла сборки и возвращает открытый ключ, который представляет маркер.</span><span class="sxs-lookup"><span data-stu-id="e76b0-104">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="e76b0-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="e76b0-105">This function has been deprecated.</span></span> <span data-ttu-id="e76b0-106">Используйте вместо этого метод [метод iclrstrongname:: StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e76b0-106">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e76b0-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e76b0-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e76b0-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="e76b0-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="e76b0-109">окне Путь к переносимому исполняемому файлу (PE) для сборки.</span><span class="sxs-lookup"><span data-stu-id="e76b0-109">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="e76b0-110">заполняет Возвращенный маркер строгого имени.</span><span class="sxs-lookup"><span data-stu-id="e76b0-110">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="e76b0-111">заполняет Размер (в байтах) маркера строгого имени.</span><span class="sxs-lookup"><span data-stu-id="e76b0-111">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="e76b0-112">заполняет Возвращаемый открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="e76b0-112">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="e76b0-113">заполняет Размер открытого ключа в байтах.</span><span class="sxs-lookup"><span data-stu-id="e76b0-113">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e76b0-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e76b0-114">Return Value</span></span>  

 <span data-ttu-id="e76b0-115">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="e76b0-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e76b0-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="e76b0-116">Remarks</span></span>  

 <span data-ttu-id="e76b0-117">Маркер строгого имени — это сокращенная форма открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="e76b0-117">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="e76b0-118">Маркер представляет собой 64-разрядный хэш, созданный из открытого ключа, используемого для подписания сборки.</span><span class="sxs-lookup"><span data-stu-id="e76b0-118">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="e76b0-119">Токен является частью строгого имени сборки и может быть считан из метаданных сборки.</span><span class="sxs-lookup"><span data-stu-id="e76b0-119">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="e76b0-120">После извлечения ключа и создания маркера следует вызвать функцию [StrongNameFreeBuffer](strongnamefreebuffer-function.md) , чтобы освободить выделенную память.</span><span class="sxs-lookup"><span data-stu-id="e76b0-120">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="e76b0-121">Если `StrongNameTokenFromAssemblyEx` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="e76b0-121">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e76b0-122">Требования</span><span class="sxs-lookup"><span data-stu-id="e76b0-122">Requirements</span></span>  

 <span data-ttu-id="e76b0-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e76b0-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e76b0-124">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="e76b0-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e76b0-125">**Библиотека:** Включается в качестве ресурса в mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e76b0-125">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="e76b0-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e76b0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e76b0-127">См. также</span><span class="sxs-lookup"><span data-stu-id="e76b0-127">See also</span></span>

- [<span data-ttu-id="e76b0-128">Метод StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="e76b0-128">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="e76b0-129">Метод StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="e76b0-129">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="e76b0-130">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="e76b0-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
