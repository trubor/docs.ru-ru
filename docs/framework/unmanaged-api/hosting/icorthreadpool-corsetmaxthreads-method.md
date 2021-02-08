---
description: 'Дополнительные сведения о методе: ICorThreadpool:: CorSetMaxThreads'
title: Метод ICorThreadpool::CorSetMaxThreads
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorSetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetMaxThreads
helpviewer_keywords:
- ICorThreadpool::CorSetMaxThreads method [.NET Framework hosting]
- CorSetMaxThreads method [.NET Framework hosting]
ms.assetid: 4a846238-df4e-4060-ba3b-5173f6a51e85
topic_type:
- apiref
ms.openlocfilehash: 5eb55604b55da58ffb4b5b2806aa3e340274a6b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789545"
---
# <a name="icorthreadpoolcorsetmaxthreads-method"></a><span data-ttu-id="b0349-103">Метод ICorThreadpool::CorSetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="b0349-103">ICorThreadpool::CorSetMaxThreads Method</span></span>

<span data-ttu-id="b0349-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="b0349-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0349-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b0349-105">Syntax</span></span>  
  
```cpp  
HRESULT CorSetMaxThreads (  
    [in] DWORD MaxWorkerThreads,  
    [in] DWORD MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b0349-106">Требования</span><span class="sxs-lookup"><span data-stu-id="b0349-106">Requirements</span></span>  

 <span data-ttu-id="b0349-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0349-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0349-108">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b0349-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0349-109">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0349-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0349-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0349-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0349-111">См. также</span><span class="sxs-lookup"><span data-stu-id="b0349-111">See also</span></span>

- [<span data-ttu-id="b0349-112">Интерфейс ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="b0349-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
