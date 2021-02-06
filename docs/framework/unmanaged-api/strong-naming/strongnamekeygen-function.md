---
description: Дополнительные сведения о функции StrongNameKeyGen
title: Функция StrongNameKeyGen
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
ms.openlocfilehash: c5f4cfcfa9030ae856acf5fd59ab34a2b8338670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636271"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="a8f16-103">Функция StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="a8f16-103">StrongNameKeyGen Function</span></span>

<span data-ttu-id="a8f16-104">Создает пару открытого и закрытого ключей для использования строгого имени.</span><span class="sxs-lookup"><span data-stu-id="a8f16-104">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="a8f16-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="a8f16-105">This function has been deprecated.</span></span> <span data-ttu-id="a8f16-106">Используйте вместо этого метод [метод iclrstrongname:: StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a8f16-106">Use the [ICLRStrongName::StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8f16-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a8f16-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8f16-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="a8f16-108">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="a8f16-109">окне Запрошенное имя контейнера ключей.</span><span class="sxs-lookup"><span data-stu-id="a8f16-109">[in] The requested key container name.</span></span> <span data-ttu-id="a8f16-110">`wszKeyContainer` должен быть непустой строкой или иметь значение NULL для создания временного имени.</span><span class="sxs-lookup"><span data-stu-id="a8f16-110">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a8f16-111">окне Указывает, следует ли оставить зарегистрированный ключ.</span><span class="sxs-lookup"><span data-stu-id="a8f16-111">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="a8f16-112">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="a8f16-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="a8f16-113">0x00000000 — используется, если `wszKeyContainer` параметр имеет значение null, чтобы создать имя контейнера временного ключа.</span><span class="sxs-lookup"><span data-stu-id="a8f16-113">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="a8f16-114">0x00000001 ( `SN_LEAVE_KEY` ) — указывает, что ключ должен оставаться зарегистрированным.</span><span class="sxs-lookup"><span data-stu-id="a8f16-114">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="a8f16-115">заполняет Возвращаемая пара открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="a8f16-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="a8f16-116">заполняет Размер (в байтах) `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="a8f16-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8f16-117">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a8f16-117">Return Value</span></span>  

 <span data-ttu-id="a8f16-118">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="a8f16-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8f16-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="a8f16-119">Remarks</span></span>  

 <span data-ttu-id="a8f16-120">`StrongNameKeyGen`Функция создает 1024-разрядный ключ.</span><span class="sxs-lookup"><span data-stu-id="a8f16-120">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="a8f16-121">После извлечения ключа необходимо вызвать функцию [StrongNameFreeBuffer](strongnamefreebuffer-function.md) , чтобы освободить выделенную память.</span><span class="sxs-lookup"><span data-stu-id="a8f16-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="a8f16-122">Если `StrongNameKeyGen` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="a8f16-122">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8f16-123">Требования</span><span class="sxs-lookup"><span data-stu-id="a8f16-123">Requirements</span></span>  

 <span data-ttu-id="a8f16-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8f16-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8f16-125">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="a8f16-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a8f16-126">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8f16-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a8f16-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8f16-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f16-128">См. также</span><span class="sxs-lookup"><span data-stu-id="a8f16-128">See also</span></span>

- [<span data-ttu-id="a8f16-129">Метод StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="a8f16-129">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="a8f16-130">Метод StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="a8f16-130">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="a8f16-131">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a8f16-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
