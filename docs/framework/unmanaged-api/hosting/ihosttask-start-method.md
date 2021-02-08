---
description: 'Дополнительные сведения о методе IHostTask:: Start.'
title: Метод IHostTask::Start
ms.date: 03/30/2017
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
ms.openlocfilehash: 48352a3df49ba2ef3e008ed211da19f54deb82f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784630"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="4a174-103">Метод IHostTask::Start</span><span class="sxs-lookup"><span data-stu-id="4a174-103">IHostTask::Start Method</span></span>

<span data-ttu-id="4a174-104">Запрашивает, что узел перемещает задачу, представленную текущим экземпляром [IHostTask](ihosttask-interface.md) , из приостановленного в активное состояние, в котором можно выполнить код.</span><span class="sxs-lookup"><span data-stu-id="4a174-104">Requests that the host move the task represented by the current [IHostTask](ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a174-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4a174-105">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4a174-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4a174-106">Return Value</span></span>  
  
|<span data-ttu-id="4a174-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a174-107">HRESULT</span></span>|<span data-ttu-id="4a174-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="4a174-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a174-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a174-109">S_OK</span></span>|<span data-ttu-id="4a174-110">Успешное начало возврата.</span><span class="sxs-lookup"><span data-stu-id="4a174-110">Start returned successfully.</span></span>|  
|<span data-ttu-id="4a174-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a174-111">E_FAIL</span></span>|<span data-ttu-id="4a174-112">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="4a174-112">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a174-113">Когда метод возвращает E_FAIL, общеязыковая среда выполнения (CLR) больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="4a174-113">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="4a174-114">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4a174-114">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a174-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="4a174-115">Remarks</span></span>  

 <span data-ttu-id="4a174-116">`Start` всегда возвращает значение HRESULT, равное S_OK, за исключением случаев, когда произошла разрушительная ошибка.</span><span class="sxs-lookup"><span data-stu-id="4a174-116">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a174-117">Требования</span><span class="sxs-lookup"><span data-stu-id="4a174-117">Requirements</span></span>  

 <span data-ttu-id="4a174-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a174-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a174-119">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4a174-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a174-120">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a174-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a174-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a174-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a174-122">См. также</span><span class="sxs-lookup"><span data-stu-id="4a174-122">See also</span></span>

- [<span data-ttu-id="4a174-123">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="4a174-123">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="4a174-124">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="4a174-124">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="4a174-125">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="4a174-125">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="4a174-126">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="4a174-126">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
