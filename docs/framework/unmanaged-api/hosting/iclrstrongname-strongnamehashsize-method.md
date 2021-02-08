---
description: 'Дополнительные сведения о методе: метод iclrstrongname:: StrongNameHashSize'
title: Метод ICLRStrongName::StrongNameHashSize
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameHashSize
helpviewer_keywords:
- ICLRStrongName::StrongNameHashSize method [.NET Framework hosting]
- StrongNameHashSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 4a05ee56-08e4-4f3a-86a9-9b52083d5c0f
topic_type:
- apiref
ms.openlocfilehash: 74781f0eaec720a84a242e6a9637036408652601
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799594"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="a9694-103">Метод ICLRStrongName::StrongNameHashSize</span><span class="sxs-lookup"><span data-stu-id="a9694-103">ICLRStrongName::StrongNameHashSize Method</span></span>

<span data-ttu-id="a9694-104">Получает размер буфера, необходимый для хэша, с помощью указанного хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="a9694-104">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9694-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a9694-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9694-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a9694-106">Parameters</span></span>  

 `ulHashAlg`  
 <span data-ttu-id="a9694-107">окне Хэш-алгоритм, используемый для вычисления размера буфера.</span><span class="sxs-lookup"><span data-stu-id="a9694-107">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="a9694-108">заполняет Размер возвращенного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="a9694-108">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9694-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a9694-109">Return Value</span></span>  

 <span data-ttu-id="a9694-110">`S_OK` значение, если метод успешно выполнен; в противном случае — значение HRESULT, указывающее на сбой (см. раздел [Общие значения HRESULT](/windows/win32/seccrypto/common-hresult-values) для списка).</span><span class="sxs-lookup"><span data-stu-id="a9694-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9694-111">Требования</span><span class="sxs-lookup"><span data-stu-id="a9694-111">Requirements</span></span>  

 <span data-ttu-id="a9694-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9694-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9694-113">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="a9694-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a9694-114">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9694-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9694-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9694-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9694-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a9694-116">See also</span></span>

- [<span data-ttu-id="a9694-117">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a9694-117">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
