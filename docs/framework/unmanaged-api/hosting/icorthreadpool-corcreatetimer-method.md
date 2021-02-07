---
description: 'Дополнительные сведения о методе: ICorThreadpool:: Коркреатетимер'
title: Метод ICorThreadpool::CorCreateTimer
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorCreateTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCreateTimer
helpviewer_keywords:
- CorCreateTimer method [.NET Framework hosting]
- ICorThreadpool::CorCreateTimer method [.NET Framework hosting]
ms.assetid: 0d56ef25-30f1-4499-8a1f-76e7654ec614
topic_type:
- apiref
ms.openlocfilehash: dc4258493181430a7e803f3b995e6b32ed2cd8b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737783"
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="5b457-103">Метод ICorThreadpool::CorCreateTimer</span><span class="sxs-lookup"><span data-stu-id="5b457-103">ICorThreadpool::CorCreateTimer Method</span></span>

<span data-ttu-id="5b457-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="5b457-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b457-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5b457-105">Syntax</span></span>  
  
```cpp  
HRESULT CorCreateTimer (  
    [in]  HANDLE*             phNewTimer,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Parameter,  
    [in]  DWORD               DueTime,  
    [in]  DWORD               Period,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5b457-106">Требования</span><span class="sxs-lookup"><span data-stu-id="5b457-106">Requirements</span></span>  

 <span data-ttu-id="5b457-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b457-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b457-108">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5b457-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b457-109">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b457-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b457-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b457-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b457-111">См. также</span><span class="sxs-lookup"><span data-stu-id="5b457-111">See also</span></span>

- [<span data-ttu-id="5b457-112">Интерфейс ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="5b457-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
