---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameKeyGen'
title: Метод ICLRStrongName::StrongNameKeyGen
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
ms.openlocfilehash: c445e1f0290d907f7820c0000f602f2668f59103
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799564"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="de89d-103">Метод ICLRStrongName::StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="de89d-103">ICLRStrongName::StrongNameKeyGen Method</span></span>

<span data-ttu-id="de89d-104">Создает пару открытого и закрытого ключей для использования строгого имени.</span><span class="sxs-lookup"><span data-stu-id="de89d-104">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de89d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="de89d-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de89d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="de89d-106">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="de89d-107">окне Запрошенное имя контейнера ключей.</span><span class="sxs-lookup"><span data-stu-id="de89d-107">[in] The requested key container name.</span></span> <span data-ttu-id="de89d-108">`wszKeyContainer` значение должно быть непустой строкой или null для создания временного имени.</span><span class="sxs-lookup"><span data-stu-id="de89d-108">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="de89d-109">окне Значение типа, указывающее, следует ли оставлять зарегистрированный ключ.</span><span class="sxs-lookup"><span data-stu-id="de89d-109">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="de89d-110">Поддерживаются следующие значения.</span><span class="sxs-lookup"><span data-stu-id="de89d-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="de89d-111">0x00000000 — используется, если `wszKeyContainer` параметр имеет значение null, чтобы создать имя контейнера временного ключа.</span><span class="sxs-lookup"><span data-stu-id="de89d-111">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="de89d-112">0x00000001 ( `SN_LEAVE_KEY` ) — указывает, что ключ должен оставаться зарегистрированным.</span><span class="sxs-lookup"><span data-stu-id="de89d-112">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="de89d-113">заполняет Возвращаемая пара открытого и закрытого ключей.</span><span class="sxs-lookup"><span data-stu-id="de89d-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="de89d-114">заполняет Размер (в байтах) `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="de89d-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de89d-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="de89d-115">Return Value</span></span>  

 <span data-ttu-id="de89d-116">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="de89d-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de89d-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="de89d-117">Remarks</span></span>  

 <span data-ttu-id="de89d-118">Метод [метод iclrstrongname:: StrongNameKeyGen](iclrstrongname-strongnamekeygen-method.md) создает ключ 1024-bit.</span><span class="sxs-lookup"><span data-stu-id="de89d-118">The [ICLRStrongName::StrongNameKeyGen](iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="de89d-119">После извлечения ключа необходимо вызвать метод [метод iclrstrongname:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) , чтобы освободить выделенную память.</span><span class="sxs-lookup"><span data-stu-id="de89d-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de89d-120">Требования</span><span class="sxs-lookup"><span data-stu-id="de89d-120">Requirements</span></span>  

 <span data-ttu-id="de89d-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de89d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de89d-122">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="de89d-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="de89d-123">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="de89d-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de89d-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de89d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de89d-125">См. также</span><span class="sxs-lookup"><span data-stu-id="de89d-125">See also</span></span>

- [<span data-ttu-id="de89d-126">Метод StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="de89d-126">StrongNameKeyGenEx Method</span></span>](iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="de89d-127">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="de89d-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
