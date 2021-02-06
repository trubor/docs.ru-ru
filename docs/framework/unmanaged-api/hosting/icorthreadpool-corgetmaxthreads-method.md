---
description: 'Дополнительные сведения о методе: ICorThreadpool:: Коржетмакссреадс'
title: Метод ICorThreadpool::CorGetMaxThreads
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetMaxThreads
helpviewer_keywords:
- CorGetMaxThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetMaxThreads method [.NET Framework hosting]
ms.assetid: 2861533a-cda0-47b3-b716-0d363505289b
topic_type:
- apiref
ms.openlocfilehash: 44de36a7ff3e086ab9389049137c66697af11af3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636485"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="25031-103">Метод ICorThreadpool::CorGetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="25031-103">ICorThreadpool::CorGetMaxThreads Method</span></span>

<span data-ttu-id="25031-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="25031-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25031-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="25031-105">Syntax</span></span>  
  
```cpp  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="25031-106">Требования</span><span class="sxs-lookup"><span data-stu-id="25031-106">Requirements</span></span>  

 <span data-ttu-id="25031-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25031-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25031-108">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="25031-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25031-109">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25031-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25031-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25031-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25031-111">См. также</span><span class="sxs-lookup"><span data-stu-id="25031-111">See also</span></span>

- [<span data-ttu-id="25031-112">Интерфейс ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="25031-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
