---
description: 'Дополнительные сведения о методе: ICorThreadpool:: CorGetAvailableThreads'
title: Метод ICorThreadpool::CorGetAvailableThreads
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type:
- apiref
ms.openlocfilehash: ca6b476a00ce781e10c0708f5132b398b4c85398
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760593"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="f93c4-103">Метод ICorThreadpool::CorGetAvailableThreads</span><span class="sxs-lookup"><span data-stu-id="f93c4-103">ICorThreadpool::CorGetAvailableThreads Method</span></span>

<span data-ttu-id="f93c4-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="f93c4-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f93c4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f93c4-105">Syntax</span></span>  
  
```cpp  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f93c4-106">Требования</span><span class="sxs-lookup"><span data-stu-id="f93c4-106">Requirements</span></span>  

 <span data-ttu-id="f93c4-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f93c4-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f93c4-108">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f93c4-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f93c4-109">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f93c4-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f93c4-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f93c4-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f93c4-111">См. также</span><span class="sxs-lookup"><span data-stu-id="f93c4-111">See also</span></span>

- [<span data-ttu-id="f93c4-112">Интерфейс ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="f93c4-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
