---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameFreeBuffer'
title: Метод ICLRStrongName::StrongNameFreeBuffer
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
ms.openlocfilehash: 8b65b75b92dd259c6919cfac9bc097066f552aba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799656"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="a84b5-103">Метод ICLRStrongName::StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="a84b5-103">ICLRStrongName::StrongNameFreeBuffer Method</span></span>

<span data-ttu-id="a84b5-104">Освобождает память, выделенную с помощью предыдущего вызова метода строгого имени, такого как [метод iclrstrongname:: StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [метод iclrstrongname:: StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md)или [метод iclrstrongname:: StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).</span><span class="sxs-lookup"><span data-stu-id="a84b5-104">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a84b5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a84b5-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a84b5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a84b5-106">Parameters</span></span>  

 `pbMemory`  
 <span data-ttu-id="a84b5-107">окне Указатель на память для освобождения.</span><span class="sxs-lookup"><span data-stu-id="a84b5-107">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a84b5-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a84b5-108">Return Value</span></span>  

 <span data-ttu-id="a84b5-109">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="a84b5-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a84b5-110">Требования</span><span class="sxs-lookup"><span data-stu-id="a84b5-110">Requirements</span></span>  

 <span data-ttu-id="a84b5-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a84b5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a84b5-112">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="a84b5-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a84b5-113">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a84b5-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a84b5-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a84b5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a84b5-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a84b5-115">See also</span></span>

- [<span data-ttu-id="a84b5-116">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a84b5-116">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
