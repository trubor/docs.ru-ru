---
description: 'Дополнительные сведения о методе: ICorThreadpool:: Корунрегистерваит'
title: Метод ICorThreadpool::CorUnregisterWait
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorUnregisterWait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnregisterWait
helpviewer_keywords:
- CorUnregisterWait method [.NET Framework hosting]
- ICorThreadpool::CorUnregisterWait method [.NET Framework hosting]
ms.assetid: 42c933f1-30a8-4011-bdea-e117f3c3265e
topic_type:
- apiref
ms.openlocfilehash: 61b6c7a1fa8459ddd173d2857cff982f353afc31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789532"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="6c0d2-103">Метод ICorThreadpool::CorUnregisterWait</span><span class="sxs-lookup"><span data-stu-id="6c0d2-103">ICorThreadpool::CorUnregisterWait Method</span></span>

<span data-ttu-id="6c0d2-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="6c0d2-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c0d2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6c0d2-105">Syntax</span></span>  
  
```cpp  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="6c0d2-106">Требования</span><span class="sxs-lookup"><span data-stu-id="6c0d2-106">Requirements</span></span>  

 <span data-ttu-id="6c0d2-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c0d2-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c0d2-108">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6c0d2-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c0d2-109">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c0d2-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c0d2-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c0d2-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c0d2-111">См. также</span><span class="sxs-lookup"><span data-stu-id="6c0d2-111">See also</span></span>

- [<span data-ttu-id="6c0d2-112">Интерфейс ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="6c0d2-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
