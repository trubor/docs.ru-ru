---
description: 'Дополнительные сведения о методе ICLRTask:: Нидсприоритисчедулинг'
title: Метод ICLRTask::NeedsPriorityScheduling
ms.date: 03/30/2017
api_name:
- ICLRTask.NeedsPriorityScheduling
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::NeedsPriorityScheduling
helpviewer_keywords:
- ICLRTask::NeedsPriorityScheduling method [.NET Framework hosting]
- NeedsPriorityScheduling method [.NET Framework hosting]
ms.assetid: 9c9db3f3-26bf-4317-88de-5eb926a22a1d
topic_type:
- apiref
ms.openlocfilehash: e6e1b93b38d86259dc2f405f8512ec1063fe7b3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781770"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="b5062-103">Метод ICLRTask::NeedsPriorityScheduling</span><span class="sxs-lookup"><span data-stu-id="b5062-103">ICLRTask::NeedsPriorityScheduling Method</span></span>

<span data-ttu-id="b5062-104">Возвращает значение, указывающее, нужно ли пометить текущую задачу, для которой выполняется переключение, в качестве высокого приоритета для повторного планирования.</span><span class="sxs-lookup"><span data-stu-id="b5062-104">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5062-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b5062-105">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5062-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b5062-106">Parameters</span></span>  

 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="b5062-107">[out] `true` , если узел должен попытаться повторно запланировать текущий экземпляр задачи как можно скорее. в противном случае — значение `false` .</span><span class="sxs-lookup"><span data-stu-id="b5062-107">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5062-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b5062-108">Return Value</span></span>  
  
|<span data-ttu-id="b5062-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b5062-109">HRESULT</span></span>|<span data-ttu-id="b5062-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="b5062-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5062-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5062-111">S_OK</span></span>|<span data-ttu-id="b5062-112">`NeedsPriorityRescheduling` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="b5062-112">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="b5062-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b5062-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b5062-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="b5062-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b5062-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b5062-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b5062-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="b5062-116">The call timed out.</span></span>|  
|<span data-ttu-id="b5062-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5062-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b5062-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="b5062-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b5062-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b5062-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b5062-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="b5062-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b5062-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b5062-121">E_FAIL</span></span>|<span data-ttu-id="b5062-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="b5062-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b5062-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="b5062-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b5062-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b5062-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5062-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="b5062-125">Remarks</span></span>  

 <span data-ttu-id="b5062-126">В ситуациях, когда задача находится в близком к сбору сборщиком мусора, среда CLR устанавливает значение `pbNeedsPriorityScheduling` равным `true` , что указывает на перепланирование с высоким приоритетом.</span><span class="sxs-lookup"><span data-stu-id="b5062-126">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="b5062-127">Это позволяет основному приложению быстро планировать задачу, уменьшая вероятность задержек при сборке мусора и позволяя основному приложению и среде выполнения взаимодействовать для экономии ресурсов памяти.</span><span class="sxs-lookup"><span data-stu-id="b5062-127">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5062-128">Требования</span><span class="sxs-lookup"><span data-stu-id="b5062-128">Requirements</span></span>  

 <span data-ttu-id="b5062-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5062-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5062-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b5062-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b5062-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5062-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5062-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5062-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5062-133">См. также</span><span class="sxs-lookup"><span data-stu-id="b5062-133">See also</span></span>

- [<span data-ttu-id="b5062-134">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="b5062-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b5062-135">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="b5062-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b5062-136">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="b5062-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b5062-137">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="b5062-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
