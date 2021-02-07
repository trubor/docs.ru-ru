---
description: Дополнительные сведения о функции StrongNameKeyGenEx
title: Функция StrongNameKeyGenEx
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
ms.openlocfilehash: b6c103d16cac1b4668e4b478a0947970b5b44a0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686831"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="7ce71-103">Функция StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="7ce71-103">StrongNameKeyGenEx Function</span></span>

<span data-ttu-id="7ce71-104">Создает новую пару открытого и закрытого ключей с указанным размером ключа для использования строгого имени.</span><span class="sxs-lookup"><span data-stu-id="7ce71-104">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="7ce71-105">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="7ce71-105">This function has been deprecated.</span></span> <span data-ttu-id="7ce71-106">Используйте вместо этого метод [метод iclrstrongname:: StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7ce71-106">Use the [ICLRStrongName::StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ce71-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7ce71-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ce71-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="7ce71-108">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="7ce71-109">окне Запрошенное имя контейнера ключей.</span><span class="sxs-lookup"><span data-stu-id="7ce71-109">[in] The requested key container name.</span></span> <span data-ttu-id="7ce71-110">`wszKeyContainer` должен быть непустой строкой или иметь значение NULL для создания временного имени.</span><span class="sxs-lookup"><span data-stu-id="7ce71-110">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7ce71-111">окне Указывает, следует ли оставить зарегистрированный ключ.</span><span class="sxs-lookup"><span data-stu-id="7ce71-111">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="7ce71-112">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="7ce71-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="7ce71-113">0x00000000 — используется, если `wszKeyContainer` параметр имеет значение null, чтобы создать имя контейнера временного ключа.</span><span class="sxs-lookup"><span data-stu-id="7ce71-113">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="7ce71-114">0x00000001 ( `SN_LEAVE_KEY` ) — указывает, что ключ должен оставаться зарегистрированным.</span><span class="sxs-lookup"><span data-stu-id="7ce71-114">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="7ce71-115">окне Запрошенный размер ключа в битах.</span><span class="sxs-lookup"><span data-stu-id="7ce71-115">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="7ce71-116">заполняет Возвращаемая пара открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="7ce71-116">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="7ce71-117">заполняет Размер (в байтах) `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="7ce71-117">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ce71-118">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7ce71-118">Return Value</span></span>  

 <span data-ttu-id="7ce71-119">`true` При успешном завершении; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="7ce71-119">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ce71-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="7ce71-120">Remarks</span></span>  

 <span data-ttu-id="7ce71-121">Для подписывания сборки строгим именем в платформа .NET Framework версиях 1,0 и 1,1 требуется a `dwKeySize` из 1024 бит. в версии 2,0 добавлена поддержка для 2048-разрядных ключей.</span><span class="sxs-lookup"><span data-stu-id="7ce71-121">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="7ce71-122">После извлечения ключа необходимо вызвать функцию [StrongNameFreeBuffer](strongnamefreebuffer-function.md) , чтобы освободить выделенную память.</span><span class="sxs-lookup"><span data-stu-id="7ce71-122">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="7ce71-123">Если `StrongNameKeyGenEx` функция не завершается успешно, вызовите функцию [стронгнамирроринфо](strongnameerrorinfo-function.md) , чтобы получить последнюю созданную ошибку.</span><span class="sxs-lookup"><span data-stu-id="7ce71-123">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ce71-124">Требования</span><span class="sxs-lookup"><span data-stu-id="7ce71-124">Requirements</span></span>  

 <span data-ttu-id="7ce71-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ce71-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ce71-126">**Заголовок:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="7ce71-126">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="7ce71-127">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ce71-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ce71-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ce71-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ce71-129">См. также</span><span class="sxs-lookup"><span data-stu-id="7ce71-129">See also</span></span>

- [<span data-ttu-id="7ce71-130">Метод StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="7ce71-130">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="7ce71-131">Метод StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="7ce71-131">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="7ce71-132">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="7ce71-132">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
