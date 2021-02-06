---
description: Дополнительные сведения о функции StrongNameTokenFromPublicKey
title: Функция StrongNameTokenFromPublicKey
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
ms.openlocfilehash: f978c9b2727db4b293b9c92a8789fbf9ba749d41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636288"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="4ce17-103">Функция StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="4ce17-103">StrongNameTokenFromPublicKey Function</span></span>

<span data-ttu-id="4ce17-104">Получает маркер, представляющий открытый ключ.</span><span class="sxs-lookup"><span data-stu-id="4ce17-104">Gets a token representing a public key.</span></span> <span data-ttu-id="4ce17-105">Маркер строгого имени — это сокращенная форма открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="4ce17-105">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="4ce17-106">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="4ce17-106">This function has been deprecated.</span></span> <span data-ttu-id="4ce17-107">Используйте вместо этого метод [метод iclrstrongname:: StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4ce17-107">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ce17-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4ce17-108">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ce17-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="4ce17-109">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="4ce17-110">окне Структура типа [публиккэйблоб](publickeyblob-structure.md) , содержащая открытую часть пары ключей, используемую для создания подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="4ce17-110">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="4ce17-111">окне Размер (в байтах) `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="4ce17-111">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="4ce17-112">заполняет Маркер строгого имени, соответствующий переданному ключу `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="4ce17-112">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="4ce17-113">Среда CLR выделяет память, в которую возвращается маркер.</span><span class="sxs-lookup"><span data-stu-id="4ce17-113">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="4ce17-114">Вызывающий объект должен освободить эту память с помощью функции [StrongNameFreeBuffer](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="4ce17-114">The caller must free this memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="4ce17-115">заполняет Размер возвращенного маркера строгого имени в байтах.</span><span class="sxs-lookup"><span data-stu-id="4ce17-115">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ce17-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4ce17-116">Return Value</span></span>  

 <span data-ttu-id="4ce17-117">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="4ce17-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ce17-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="4ce17-118">Remarks</span></span>  

 <span data-ttu-id="4ce17-119">Маркер строгого имени — это сокращенная форма открытого ключа, используемая для экономии места при хранении ключевых сведений в метаданных.</span><span class="sxs-lookup"><span data-stu-id="4ce17-119">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="4ce17-120">В частности, маркеры строгого имени используются в ссылках на сборки для ссылки на зависимую сборку.</span><span class="sxs-lookup"><span data-stu-id="4ce17-120">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="4ce17-121">Если `StrongNameTokenFromPublicKey` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="4ce17-121">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ce17-122">Требования</span><span class="sxs-lookup"><span data-stu-id="4ce17-122">Requirements</span></span>  

 <span data-ttu-id="4ce17-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ce17-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ce17-124">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="4ce17-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="4ce17-125">**Библиотека:** Включается в качестве ресурса в mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4ce17-125">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="4ce17-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ce17-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ce17-127">См. также</span><span class="sxs-lookup"><span data-stu-id="4ce17-127">See also</span></span>

- [<span data-ttu-id="4ce17-128">Метод StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="4ce17-128">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="4ce17-129">Метод StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="4ce17-129">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="4ce17-130">Структура PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="4ce17-130">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
