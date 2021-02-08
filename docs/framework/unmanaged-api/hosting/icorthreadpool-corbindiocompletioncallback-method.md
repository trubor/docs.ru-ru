---
description: 'Дополнительные сведения о методе: ICorThreadpool:: Корбиндиокомплетионкаллбакк'
title: Метод ICorThreadpool::CorBindIoCompletionCallback
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorBindIoCompletionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorBindIoCompletionCallback
helpviewer_keywords:
- CorBindIoCompletionCallback method [.NET Framework hosting]
- ICorThreadpool::CorBindIoCompletionCallback method [.NET Framework hosting]
ms.assetid: 2b159225-f09c-42f1-aa7c-44087e121249
topic_type:
- apiref
ms.openlocfilehash: 9f9e62fd8947c3ab80c4434814ee7e95b5327a24
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799438"
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="62ee4-103">Метод ICorThreadpool::CorBindIoCompletionCallback</span><span class="sxs-lookup"><span data-stu-id="62ee4-103">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>

<span data-ttu-id="62ee4-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="62ee4-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ee4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="62ee4-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="62ee4-106">Требования</span><span class="sxs-lookup"><span data-stu-id="62ee4-106">Requirements</span></span>  

 <span data-ttu-id="62ee4-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62ee4-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62ee4-108">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="62ee4-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62ee4-109">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62ee4-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62ee4-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62ee4-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ee4-111">См. также</span><span class="sxs-lookup"><span data-stu-id="62ee4-111">See also</span></span>

- [<span data-ttu-id="62ee4-112">Интерфейс ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="62ee4-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
