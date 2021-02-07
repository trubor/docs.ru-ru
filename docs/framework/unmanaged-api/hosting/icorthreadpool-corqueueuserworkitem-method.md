---
description: 'Дополнительные сведения о методе: ICorThreadpool:: Коркуеуеусерворкитем'
title: Метод ICorThreadpool::CorQueueUserWorkItem
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorQueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorQueueUserWorkItem method [.NET Framework hosting]
- CorQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 29ac7898-a7c7-433e-8f79-cd5237e0bab8
topic_type:
- apiref
ms.openlocfilehash: fc0fc1dc3aa33bf11735fddd2c034af03f269f3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737776"
---
# <a name="icorthreadpoolcorqueueuserworkitem-method"></a><span data-ttu-id="ab08c-103">Метод ICorThreadpool::CorQueueUserWorkItem</span><span class="sxs-lookup"><span data-stu-id="ab08c-103">ICorThreadpool::CorQueueUserWorkItem Method</span></span>

<span data-ttu-id="ab08c-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="ab08c-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab08c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ab08c-105">Syntax</span></span>  
  
```cpp  
HRESULT CorQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [in] BOOL                   executeOnlyOnce,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ab08c-106">Требования</span><span class="sxs-lookup"><span data-stu-id="ab08c-106">Requirements</span></span>  

 <span data-ttu-id="ab08c-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab08c-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab08c-108">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ab08c-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab08c-109">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab08c-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab08c-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab08c-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab08c-111">См. также</span><span class="sxs-lookup"><span data-stu-id="ab08c-111">See also</span></span>

- [<span data-ttu-id="ab08c-112">Интерфейс ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="ab08c-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
