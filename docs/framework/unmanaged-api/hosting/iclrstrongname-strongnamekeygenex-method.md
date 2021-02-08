---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameKeyGenEx'
title: Метод ICLRStrongName::StrongNameKeyGenEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
ms.openlocfilehash: 3ea2bef5cc6a45066d010fc925f8866e8129faaa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799568"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="7cacf-103">Метод ICLRStrongName::StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="7cacf-103">ICLRStrongName::StrongNameKeyGenEx Method</span></span>

<span data-ttu-id="7cacf-104">Создает новую пару открытого и закрытого ключей с указанным размером ключа для использования строгого имени.</span><span class="sxs-lookup"><span data-stu-id="7cacf-104">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cacf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7cacf-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cacf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7cacf-106">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="7cacf-107">окне Запрошенное имя контейнера ключей.</span><span class="sxs-lookup"><span data-stu-id="7cacf-107">[in] The requested key container name.</span></span> <span data-ttu-id="7cacf-108">`wszKeyContainer` значение должно быть непустой строкой или null для создания временного имени.</span><span class="sxs-lookup"><span data-stu-id="7cacf-108">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7cacf-109">окне Значение типа, указывающее, следует ли оставлять зарегистрированный ключ.</span><span class="sxs-lookup"><span data-stu-id="7cacf-109">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="7cacf-110">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="7cacf-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="7cacf-111">0x00000000 — используется, если `wszKeyContainer` параметр имеет значение null, чтобы создать имя контейнера временного ключа.</span><span class="sxs-lookup"><span data-stu-id="7cacf-111">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="7cacf-112">0x00000001 ( `SN_LEAVE_KEY` ) — указывает, что ключ должен оставаться зарегистрированным.</span><span class="sxs-lookup"><span data-stu-id="7cacf-112">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="7cacf-113">окне Запрошенный размер ключа в битах.</span><span class="sxs-lookup"><span data-stu-id="7cacf-113">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="7cacf-114">заполняет Возвращаемая пара открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="7cacf-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="7cacf-115">заполняет Размер (в байтах) `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="7cacf-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cacf-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7cacf-116">Return Value</span></span>  

 <span data-ttu-id="7cacf-117">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="7cacf-117">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cacf-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="7cacf-118">Remarks</span></span>  

 <span data-ttu-id="7cacf-119">Для подписывания сборки строгим именем в платформа .NET Framework версиях 1,0 и 1,1 требуется a `dwKeySize` из 1024 бит. в версии 2,0 добавлена поддержка для 2048-разрядных ключей.</span><span class="sxs-lookup"><span data-stu-id="7cacf-119">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="7cacf-120">После извлечения ключа необходимо вызвать метод [метод iclrstrongname:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) , чтобы освободить выделенную память.</span><span class="sxs-lookup"><span data-stu-id="7cacf-120">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cacf-121">Требования</span><span class="sxs-lookup"><span data-stu-id="7cacf-121">Requirements</span></span>  

 <span data-ttu-id="7cacf-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cacf-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cacf-123">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="7cacf-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7cacf-124">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7cacf-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7cacf-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cacf-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cacf-126">См. также</span><span class="sxs-lookup"><span data-stu-id="7cacf-126">See also</span></span>

- [<span data-ttu-id="7cacf-127">Метод StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="7cacf-127">StrongNameKeyGen Method</span></span>](iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="7cacf-128">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="7cacf-128">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
