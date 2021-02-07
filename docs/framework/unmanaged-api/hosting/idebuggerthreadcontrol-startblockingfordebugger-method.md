---
description: 'Дополнительные сведения о методе: Идебугжерсреадконтрол:: StartBlockingForDebugger'
title: Метод IDebuggerThreadControl::StartBlockingForDebugger
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.StartBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type:
- apiref
ms.openlocfilehash: 3e19817c4adbefd1dd70be047656b3fea261c389
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709683"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="cf2cb-103">Метод IDebuggerThreadControl::StartBlockingForDebugger</span><span class="sxs-lookup"><span data-stu-id="cf2cb-103">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>

<span data-ttu-id="cf2cb-104">Уведомляет узел о том, что служба отладки собирается начать блокирование всех потоков.</span><span class="sxs-lookup"><span data-stu-id="cf2cb-104">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf2cb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cf2cb-105">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf2cb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cf2cb-106">Parameters</span></span>  

 `dwUnused`  
 <span data-ttu-id="cf2cb-107">[in] Зарезервирован для будущего использования.</span><span class="sxs-lookup"><span data-stu-id="cf2cb-107">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf2cb-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="cf2cb-108">Remarks</span></span>  

 <span data-ttu-id="cf2cb-109">`StartBlockingForDebugger`Метод может быть вызван в потоке среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="cf2cb-109">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf2cb-110">Требования</span><span class="sxs-lookup"><span data-stu-id="cf2cb-110">Requirements</span></span>  

 <span data-ttu-id="cf2cb-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf2cb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf2cb-112">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cf2cb-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf2cb-113">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf2cb-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf2cb-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf2cb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf2cb-115">См. также</span><span class="sxs-lookup"><span data-stu-id="cf2cb-115">See also</span></span>

- [<span data-ttu-id="cf2cb-116">Интерфейс IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="cf2cb-116">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
