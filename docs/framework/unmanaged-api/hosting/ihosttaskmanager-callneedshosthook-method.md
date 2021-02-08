---
description: 'Дополнительные сведения о методе: IHostTaskManager:: CallNeedsHostHook'
title: Метод IHostTaskManager::CallNeedsHostHook
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
ms.openlocfilehash: 777e1e6c4ac094a7af077c481415167f57eed14d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784591"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="449b9-103">Метод IHostTaskManager::CallNeedsHostHook</span><span class="sxs-lookup"><span data-stu-id="449b9-103">IHostTaskManager::CallNeedsHostHook Method</span></span>

<span data-ttu-id="449b9-104">Позволяет узлу указать, может ли среда CLR подставляема указанный вызов к неуправляемой функции.</span><span class="sxs-lookup"><span data-stu-id="449b9-104">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="449b9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="449b9-105">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="449b9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="449b9-106">Parameters</span></span>  

 `target`  
 <span data-ttu-id="449b9-107">окне Адрес в сопоставленном переносимом исполняемом файле (PE) неуправляемой функции, которая должна быть вызвана.</span><span class="sxs-lookup"><span data-stu-id="449b9-107">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="449b9-108">заполняет Указатель на логическое значение, указывающее, требует ли узел вызова метода.</span><span class="sxs-lookup"><span data-stu-id="449b9-108">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="449b9-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="449b9-109">Return Value</span></span>  
  
|<span data-ttu-id="449b9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="449b9-110">HRESULT</span></span>|<span data-ttu-id="449b9-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="449b9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="449b9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="449b9-112">S_OK</span></span>|<span data-ttu-id="449b9-113">`CallNeedsHostHook` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="449b9-113">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="449b9-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="449b9-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="449b9-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="449b9-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="449b9-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="449b9-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="449b9-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="449b9-117">The call timed out.</span></span>|  
|<span data-ttu-id="449b9-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="449b9-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="449b9-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="449b9-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="449b9-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="449b9-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="449b9-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="449b9-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="449b9-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="449b9-122">E_FAIL</span></span>|<span data-ttu-id="449b9-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="449b9-123">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="449b9-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="449b9-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="449b9-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="449b9-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="449b9-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="449b9-126">Remarks</span></span>  

 <span data-ttu-id="449b9-127">Чтобы помочь оптимизировать выполнение кода, среда CLR выполняет анализ каждого вызова неиспользуемой платформы во время компиляции, чтобы определить, можно ли выполнить встраивание вызова.</span><span class="sxs-lookup"><span data-stu-id="449b9-127">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="449b9-128">`CallNeedsHostHook` позволяет узлу переопределить это решение, запрашивая вызов неуправляемой функции.</span><span class="sxs-lookup"><span data-stu-id="449b9-128">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="449b9-129">Если узлу требуется обработчик, среда выполнения не выполняет встраивание вызова.</span><span class="sxs-lookup"><span data-stu-id="449b9-129">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="449b9-130">Обычно хосту требуется обработчик, в котором необходимо настроить состояние с плавающей запятой, или при получении уведомления о том, что вызов переходит в состояние, в котором узел не может отрегулировать запросы среды выполнения для памяти или какие-либо блокировки.</span><span class="sxs-lookup"><span data-stu-id="449b9-130">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="449b9-131">Когда узел требует, чтобы вызов был подключен, среда выполнения уведомляет узел о переходах к управляемому коду и из него с помощью вызовов [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [леаверунтиме](ihosttaskmanager-leaveruntime-method.md), [реверсинтеррунтиме](ihosttaskmanager-reverseenterruntime-method.md)и [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="449b9-131">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="449b9-132">Требования</span><span class="sxs-lookup"><span data-stu-id="449b9-132">Requirements</span></span>  

 <span data-ttu-id="449b9-133">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="449b9-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="449b9-134">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="449b9-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="449b9-135">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="449b9-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="449b9-136">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="449b9-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="449b9-137">См. также</span><span class="sxs-lookup"><span data-stu-id="449b9-137">See also</span></span>

- [<span data-ttu-id="449b9-138">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="449b9-138">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="449b9-139">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="449b9-139">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="449b9-140">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="449b9-140">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="449b9-141">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="449b9-141">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
