---
description: 'Дополнительные сведения о методе: IHostTaskManager:: EnterRuntime'
title: Метод IHostTaskManager::EnterRuntime
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
ms.openlocfilehash: 924fa18c9acbf02d8c614ffd9bf95657fd73ed14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753839"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="7ab7f-103">Метод IHostTaskManager::EnterRuntime</span><span class="sxs-lookup"><span data-stu-id="7ab7f-103">IHostTaskManager::EnterRuntime Method</span></span>

<span data-ttu-id="7ab7f-104">Уведомляет узел о том, что вызов неуправляемого метода, например метода вызова платформы, возвращает управление выполнением среде CLR.</span><span class="sxs-lookup"><span data-stu-id="7ab7f-104">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ab7f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7ab7f-105">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7ab7f-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7ab7f-106">Return Value</span></span>  
  
|<span data-ttu-id="7ab7f-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7ab7f-107">HRESULT</span></span>|<span data-ttu-id="7ab7f-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="7ab7f-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ab7f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="7ab7f-109">S_OK</span></span>|<span data-ttu-id="7ab7f-110">`EnterRuntime` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="7ab7f-110">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="7ab7f-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7ab7f-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7ab7f-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="7ab7f-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7ab7f-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7ab7f-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7ab7f-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="7ab7f-114">The call timed out.</span></span>|  
|<span data-ttu-id="7ab7f-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7ab7f-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7ab7f-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="7ab7f-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7ab7f-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7ab7f-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7ab7f-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="7ab7f-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7ab7f-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7ab7f-119">E_FAIL</span></span>|<span data-ttu-id="7ab7f-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="7ab7f-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7ab7f-121">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="7ab7f-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7ab7f-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7ab7f-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7ab7f-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7ab7f-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7ab7f-124">Недостаточно памяти для завершения запрошенного выделения.</span><span class="sxs-lookup"><span data-stu-id="7ab7f-124">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ab7f-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="7ab7f-125">Remarks</span></span>  

 <span data-ttu-id="7ab7f-126">`EnterRuntime` вызывается для уведомления узла о том, что неуправляемая функция, для которой был выполнен предыдущий вызов метода [леаверунтиме](ihosttaskmanager-leaveruntime-method.md) , завершила выполнение, и возвращает управление выполнением среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="7ab7f-126">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ab7f-127">[Реверсинтеррунтиме](ihosttaskmanager-reverseenterruntime-method.md) вызывается для уведомления узла о том, что неуправляемая функция, для которой `LeaveRuntime` был выполнен предыдущий вызов, делает вызов управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="7ab7f-127">[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ab7f-128">Требования</span><span class="sxs-lookup"><span data-stu-id="7ab7f-128">Requirements</span></span>  

 <span data-ttu-id="7ab7f-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ab7f-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ab7f-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7ab7f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ab7f-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ab7f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ab7f-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ab7f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ab7f-133">См. также</span><span class="sxs-lookup"><span data-stu-id="7ab7f-133">See also</span></span>

- <span data-ttu-id="7ab7f-134">[Расширенное COM-взаимодействие](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7ab7f-134">[Advanced COM Interoperability](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="7ab7f-135">Инструкции. вызов собственных библиотек DLL из управляемого кода с помощью PInvoke</span><span class="sxs-lookup"><span data-stu-id="7ab7f-135">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="7ab7f-136">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="7ab7f-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="7ab7f-137">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="7ab7f-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="7ab7f-138">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="7ab7f-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="7ab7f-139">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="7ab7f-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="7ab7f-140">Метод LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="7ab7f-140">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
