---
description: 'Дополнительные сведения о методе: IHostTaskManager:: Леаверунтиме'
title: Метод IHostTaskManager::LeaveRuntime
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
ms.openlocfilehash: 7b18bdc17b9cfd52b68309a07c6714fd1efa66cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707449"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="85249-103">Метод IHostTaskManager::LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="85249-103">IHostTaskManager::LeaveRuntime Method</span></span>

<span data-ttu-id="85249-104">Уведомляет основное приложение о том, что Текущая выполняемая задача собирается покинуть среду CLR, и введите неуправляемый код.</span><span class="sxs-lookup"><span data-stu-id="85249-104">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="85249-105">Соответствующий вызов [IHostTaskManager:: EnterRuntime](ihosttaskmanager-enterruntime-method.md) уведомляет основное приложение о том, что выполняемая в данный момент задача повторно вводит управляемый код.</span><span class="sxs-lookup"><span data-stu-id="85249-105">A corresponding call to [IHostTaskManager::EnterRuntime](ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85249-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="85249-106">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85249-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="85249-107">Parameters</span></span>  

 `target`  
 <span data-ttu-id="85249-108">окне Адрес в сопоставленном переносимом исполняемом файле неуправляемой функции для вызова.</span><span class="sxs-lookup"><span data-stu-id="85249-108">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85249-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="85249-109">Return Value</span></span>  
  
|<span data-ttu-id="85249-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85249-110">HRESULT</span></span>|<span data-ttu-id="85249-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="85249-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85249-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="85249-112">S_OK</span></span>|<span data-ttu-id="85249-113">`LeaveRuntime` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="85249-113">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="85249-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="85249-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="85249-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="85249-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="85249-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="85249-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="85249-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="85249-117">The call timed out.</span></span>|  
|<span data-ttu-id="85249-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="85249-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="85249-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="85249-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="85249-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="85249-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="85249-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="85249-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="85249-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="85249-122">E_FAIL</span></span>|<span data-ttu-id="85249-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="85249-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="85249-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="85249-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="85249-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="85249-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="85249-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="85249-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="85249-127">Недостаточно памяти для завершения запрошенного выделения.</span><span class="sxs-lookup"><span data-stu-id="85249-127">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85249-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="85249-128">Remarks</span></span>  

 <span data-ttu-id="85249-129">Последовательности вызовов для и из неуправляемого кода могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="85249-129">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="85249-130">Например, приведенный ниже список описывает гипотетическую ситуацию, в которой последовательность вызовов `LeaveRuntime` , [IHostTaskManager:: реверсинтеррунтиме](ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md), и узел, `IHostTaskManager::EnterRuntime` позволяющий находить вложенные слои.</span><span class="sxs-lookup"><span data-stu-id="85249-130">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="85249-131">Действие</span><span class="sxs-lookup"><span data-stu-id="85249-131">Action</span></span>|<span data-ttu-id="85249-132">Вызов соответствующего метода</span><span class="sxs-lookup"><span data-stu-id="85249-132">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="85249-133">Управляемый исполняемый файл Visual Basic вызывает неуправляемую функцию, написанную на языке C, с помощью вызова неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="85249-133">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="85249-134">Неуправляемая функция C вызывает метод в управляемой библиотеке DLL, написанной на языке C#.</span><span class="sxs-lookup"><span data-stu-id="85249-134">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="85249-135">Управляемая функция C# вызывает другую неуправляемую функцию, написанную на языке C, также используя вызов неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="85249-135">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="85249-136">Вторая неуправляемая функция возвращает выполнение функции C#.</span><span class="sxs-lookup"><span data-stu-id="85249-136">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="85249-137">Функция C# возвращает выполнение в первую неуправляемую функцию.</span><span class="sxs-lookup"><span data-stu-id="85249-137">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="85249-138">Первая неуправляемая функция возвращает выполнение в программу Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="85249-138">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="85249-139">Требования</span><span class="sxs-lookup"><span data-stu-id="85249-139">Requirements</span></span>  

 <span data-ttu-id="85249-140">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85249-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85249-141">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="85249-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85249-142">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85249-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85249-143">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85249-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85249-144">См. также</span><span class="sxs-lookup"><span data-stu-id="85249-144">See also</span></span>

- [<span data-ttu-id="85249-145">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="85249-145">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="85249-146">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="85249-146">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="85249-147">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="85249-147">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="85249-148">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="85249-148">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
