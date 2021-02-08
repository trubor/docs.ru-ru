---
description: 'Дополнительные сведения о методе ICLRTask:: Жетмемстатс'
title: Метод ICLRTask::GetMemStats
ms.date: 03/30/2017
api_name:
- ICLRTask.GetMemStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::GetMemStats
helpviewer_keywords:
- ICLRTask::GetMemStats method [.NET Framework hosting]
- GetMemStats method [.NET Framework hosting]
ms.assetid: c9e07657-1682-4c30-a336-f8658ff1a125
topic_type:
- apiref
ms.openlocfilehash: ed81e9ced20a43528247d70012077ffd466f9ed1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784981"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="61739-103">Метод ICLRTask::GetMemStats</span><span class="sxs-lookup"><span data-stu-id="61739-103">ICLRTask::GetMemStats Method</span></span>

<span data-ttu-id="61739-104">Возвращает статистические сведения об использовании памяти, связанные с задачей, которую представляет текущий экземпляр [ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="61739-104">Gets statistical memory usage information related to the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61739-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="61739-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61739-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="61739-106">Parameters</span></span>  

 `pMemUsage`  
 <span data-ttu-id="61739-107">заполняет Указатель на экземпляр [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) , содержащий сведения об использовании памяти задачей, включая число выделенных байтов.</span><span class="sxs-lookup"><span data-stu-id="61739-107">[out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61739-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="61739-108">Return Value</span></span>  
  
|<span data-ttu-id="61739-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61739-109">HRESULT</span></span>|<span data-ttu-id="61739-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="61739-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61739-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="61739-111">S_OK</span></span>|<span data-ttu-id="61739-112">`GetMemStats` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="61739-112">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="61739-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="61739-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="61739-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="61739-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="61739-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="61739-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="61739-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="61739-116">The call timed out.</span></span>|  
|<span data-ttu-id="61739-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="61739-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="61739-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="61739-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="61739-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="61739-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="61739-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="61739-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="61739-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="61739-121">E_FAIL</span></span>|<span data-ttu-id="61739-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="61739-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="61739-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="61739-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="61739-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="61739-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61739-125">Требования</span><span class="sxs-lookup"><span data-stu-id="61739-125">Requirements</span></span>  

 <span data-ttu-id="61739-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61739-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61739-127">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="61739-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61739-128">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="61739-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61739-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61739-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61739-130">См. также</span><span class="sxs-lookup"><span data-stu-id="61739-130">See also</span></span>

- [<span data-ttu-id="61739-131">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="61739-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="61739-132">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="61739-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="61739-133">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="61739-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="61739-134">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="61739-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
