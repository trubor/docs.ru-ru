---
description: 'Дополнительные сведения о методе ICLRTask:: RudeAbort'
title: Метод ICLRTask::RudeAbort
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
ms.openlocfilehash: f152f11ce41018b458ed2cb4df255e486ad54da0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636888"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="72d92-103">Метод ICLRTask::RudeAbort</span><span class="sxs-lookup"><span data-stu-id="72d92-103">ICLRTask::RudeAbort Method</span></span>

<span data-ttu-id="72d92-104">Инструктирует среду CLR, чтобы немедленно и безусловно прерывать выполнение задачи, представленной текущим экземпляром [интерфейса ICLRTask](iclrtask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="72d92-104">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72d92-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="72d92-105">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="72d92-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="72d92-106">Return Value</span></span>  
  
|<span data-ttu-id="72d92-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72d92-107">HRESULT</span></span>|<span data-ttu-id="72d92-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="72d92-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72d92-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="72d92-109">S_OK</span></span>|<span data-ttu-id="72d92-110">`RudeAbort` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="72d92-110">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="72d92-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="72d92-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="72d92-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="72d92-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="72d92-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="72d92-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="72d92-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="72d92-114">The call timed out.</span></span>|  
|<span data-ttu-id="72d92-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="72d92-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="72d92-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="72d92-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="72d92-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="72d92-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="72d92-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="72d92-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="72d92-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72d92-119">E_FAIL</span></span>|<span data-ttu-id="72d92-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="72d92-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="72d92-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="72d92-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="72d92-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="72d92-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72d92-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="72d92-123">Remarks</span></span>  

 <span data-ttu-id="72d92-124">Вызовы узла `RudeAbort` для немедленного прерывания задачи.</span><span class="sxs-lookup"><span data-stu-id="72d92-124">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="72d92-125">Выполнение методов завершения и подпрограмм обработки исключений не гарантируется.</span><span class="sxs-lookup"><span data-stu-id="72d92-125">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72d92-126">Требования</span><span class="sxs-lookup"><span data-stu-id="72d92-126">Requirements</span></span>  

 <span data-ttu-id="72d92-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72d92-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72d92-128">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="72d92-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72d92-129">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="72d92-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72d92-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72d92-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d92-131">См. также</span><span class="sxs-lookup"><span data-stu-id="72d92-131">See also</span></span>

- [<span data-ttu-id="72d92-132">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="72d92-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="72d92-133">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="72d92-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="72d92-134">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="72d92-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="72d92-135">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="72d92-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
