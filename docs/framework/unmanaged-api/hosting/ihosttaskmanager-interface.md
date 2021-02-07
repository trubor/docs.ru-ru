---
description: 'Дополнительные сведения о: интерфейс IHostTaskManager'
title: Интерфейс IHostTaskManager
ms.date: 03/30/2017
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
ms.openlocfilehash: 67574550ba26970189ea53b8e6bdb867fea8549b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707488"
---
# <a name="ihosttaskmanager-interface"></a><span data-ttu-id="eb2c5-103">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="eb2c5-103">IHostTaskManager Interface</span></span>

<span data-ttu-id="eb2c5-104">Предоставляет методы, позволяющие среде CLR работать с задачами через основное приложение, а не использовать стандартные функции потоков или волоконно-оптической операционной системы.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-104">Provides methods that allow the common language runtime (CLR) to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb2c5-105">Методы</span><span class="sxs-lookup"><span data-stu-id="eb2c5-105">Methods</span></span>  
  
|<span data-ttu-id="eb2c5-106">Метод</span><span class="sxs-lookup"><span data-stu-id="eb2c5-106">Method</span></span>|<span data-ttu-id="eb2c5-107">Описание</span><span class="sxs-lookup"><span data-stu-id="eb2c5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb2c5-108">Метод BeginDelayAbort</span><span class="sxs-lookup"><span data-stu-id="eb2c5-108">BeginDelayAbort Method</span></span>](ihosttaskmanager-begindelayabort-method.md)|<span data-ttu-id="eb2c5-109">Уведомляет узел о том, что управляемый код вводит точку, в которой не нужно прерывать текущую задачу.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-109">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>|  
|[<span data-ttu-id="eb2c5-110">Метод BeginThreadAffinity</span><span class="sxs-lookup"><span data-stu-id="eb2c5-110">BeginThreadAffinity Method</span></span>](ihosttaskmanager-beginthreadaffinity-method.md)|<span data-ttu-id="eb2c5-111">Уведомляет узел о том, что управляемый код вводит точку, в которой текущая задача не должна быть перемещена в другой поток операционной системы.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-111">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>|  
|[<span data-ttu-id="eb2c5-112">Метод CallNeedsHostHook</span><span class="sxs-lookup"><span data-stu-id="eb2c5-112">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)|<span data-ttu-id="eb2c5-113">Позволяет узлу указать, может ли среда CLR подставляемый вызов к неуправляемой функции.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-113">Enables the host to specify whether the common language runtime can inline the specified call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="eb2c5-114">Метод CreateTask</span><span class="sxs-lookup"><span data-stu-id="eb2c5-114">CreateTask Method</span></span>](ihosttaskmanager-createtask-method.md)|<span data-ttu-id="eb2c5-115">Запрашивает создание новой задачи узлом.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-115">Requests that the host create a new task.</span></span>|  
|[<span data-ttu-id="eb2c5-116">Метод EndDelayAbort</span><span class="sxs-lookup"><span data-stu-id="eb2c5-116">EndDelayAbort Method</span></span>](ihosttaskmanager-enddelayabort-method.md)|<span data-ttu-id="eb2c5-117">Уведомляет узел о выходе управляемого кода за время, в течение которого текущая задача не должна прерываться, после предыдущего вызова `BeginDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="eb2c5-117">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to `BeginDelayAbort`.</span></span>|  
|[<span data-ttu-id="eb2c5-118">Метод EndThreadAffinity</span><span class="sxs-lookup"><span data-stu-id="eb2c5-118">EndThreadAffinity Method</span></span>](ihosttaskmanager-endthreadaffinity-method.md)|<span data-ttu-id="eb2c5-119">Уведомляет узел о выходе управляемого кода за время, в течение которого текущая задача не должна быть перемещена в другой поток операционной системы, после предыдущего вызова `BeginThreadAffinity` .</span><span class="sxs-lookup"><span data-stu-id="eb2c5-119">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to `BeginThreadAffinity`.</span></span>|  
|[<span data-ttu-id="eb2c5-120">Метод EnterRuntime</span><span class="sxs-lookup"><span data-stu-id="eb2c5-120">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)|<span data-ttu-id="eb2c5-121">Уведомляет узел о том, что вызов неуправляемого метода, например метода вызова платформы, возвращает управление выполнением в среду CLR.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-121">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the CLR.</span></span>|  
|[<span data-ttu-id="eb2c5-122">Метод GetCurrentTask</span><span class="sxs-lookup"><span data-stu-id="eb2c5-122">GetCurrentTask Method</span></span>](ihosttaskmanager-getcurrenttask-method.md)|<span data-ttu-id="eb2c5-123">Возвращает указатель интерфейса на задачу, которая выполняется в данный момент в потоке операционной системы, из которого выполняется этот вызов.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-123">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>|  
|[<span data-ttu-id="eb2c5-124">Метод GetStackGuarantee</span><span class="sxs-lookup"><span data-stu-id="eb2c5-124">GetStackGuarantee Method</span></span>](ihosttaskmanager-getstackguarantee-method.md)|<span data-ttu-id="eb2c5-125">Возвращает объем стекового пространства, который гарантированно будет доступен после завершения операции с стеком, но до закрытия процесса.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-125">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>|  
|[<span data-ttu-id="eb2c5-126">Метод LeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="eb2c5-126">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)|<span data-ttu-id="eb2c5-127">Уведомляет узел о том, что управляемый код собирается выполнить вызов неуправляемой функции.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-127">Notifies the host that managed code is about to make a call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="eb2c5-128">Метод ReverseEnterRuntime</span><span class="sxs-lookup"><span data-stu-id="eb2c5-128">ReverseEnterRuntime Method</span></span>](ihosttaskmanager-reverseenterruntime-method.md)|<span data-ttu-id="eb2c5-129">Уведомляет узел о том, что в среде CLR выполняется вызов из неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-129">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>|  
|[<span data-ttu-id="eb2c5-130">Метод ReverseLeaveRuntime</span><span class="sxs-lookup"><span data-stu-id="eb2c5-130">ReverseLeaveRuntime Method</span></span>](ihosttaskmanager-reverseleaveruntime-method.md)|<span data-ttu-id="eb2c5-131">Уведомляет узел, что элемент управления выходит из среды CLR и вводит неуправляемую функцию, которая, в свою очередь, вызывается из управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-131">Notifies the host that control is leaving the CLR and entering an unmanaged function that was, in turn, called from managed code.</span></span>|  
|[<span data-ttu-id="eb2c5-132">Метод SetCLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="eb2c5-132">SetCLRTaskManager Method</span></span>](ihosttaskmanager-setclrtaskmanager-method.md)|<span data-ttu-id="eb2c5-133">Предоставляет узлу указатель интерфейса на экземпляр [ICLRTaskManager](iclrtaskmanager-interface.md) , РЕАЛИЗУЕМый средой CLR.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-133">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="eb2c5-134">Метод SetLocale</span><span class="sxs-lookup"><span data-stu-id="eb2c5-134">SetLocale Method</span></span>](ihosttaskmanager-setlocale-method.md)|<span data-ttu-id="eb2c5-135">Уведомляет узел о том, что среда CLR изменила языковой стандарт текущей задачи.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-135">Notifies the host that the CLR has changed the locale on the current task.</span></span>|  
|[<span data-ttu-id="eb2c5-136">Метод SetStackGuarantee</span><span class="sxs-lookup"><span data-stu-id="eb2c5-136">SetStackGuarantee Method</span></span>](ihosttaskmanager-setstackguarantee-method.md)|<span data-ttu-id="eb2c5-137">Зарезервировано только для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-137">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="eb2c5-138">Метод SetUILocale</span><span class="sxs-lookup"><span data-stu-id="eb2c5-138">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)|<span data-ttu-id="eb2c5-139">Уведомляет узел о том, что языковой стандарт пользовательского интерфейса был изменен в текущей задаче.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-139">Notifies the host that the user interface locale has been changed on the current task.</span></span>|  
|[<span data-ttu-id="eb2c5-140">Метод Sleep</span><span class="sxs-lookup"><span data-stu-id="eb2c5-140">Sleep Method</span></span>](ihosttaskmanager-sleep-method.md)|<span data-ttu-id="eb2c5-141">Уведомляет узел о том, что текущая задача переходит в спящий режим.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-141">Notifies the host that the current task is going to sleep.</span></span>|  
|[<span data-ttu-id="eb2c5-142">Метод SwitchToTask</span><span class="sxs-lookup"><span data-stu-id="eb2c5-142">SwitchToTask Method</span></span>](ihosttaskmanager-switchtotask-method.md)|<span data-ttu-id="eb2c5-143">Уведомляет узел о том, что необходимо отключить текущую задачу.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-143">Notifies the host that it should switch out the current task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb2c5-144">Remarks</span><span class="sxs-lookup"><span data-stu-id="eb2c5-144">Remarks</span></span>  

 <span data-ttu-id="eb2c5-145">`IHostTaskManager` позволяет среде CLR создавать задачи и управлять ими, чтобы обеспечить обработчики для узла на выполнение действий при передаче управления из управляемого кода в неуправляемый и наоборот, а также для указания определенных действий, которые узел может и не может принимать во время выполнения кода.</span><span class="sxs-lookup"><span data-stu-id="eb2c5-145">`IHostTaskManager` allows the CLR to create and manage tasks, to provide hooks for the host to take action when control transfers from managed to unmanaged code and vice versa, and to specify certain actions the host can and cannot take during code execution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb2c5-146">Требования</span><span class="sxs-lookup"><span data-stu-id="eb2c5-146">Requirements</span></span>  

 <span data-ttu-id="eb2c5-147">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb2c5-147">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb2c5-148">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="eb2c5-148">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb2c5-149">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eb2c5-149">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb2c5-150">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb2c5-150">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2c5-151">См. также</span><span class="sxs-lookup"><span data-stu-id="eb2c5-151">See also</span></span>

- [<span data-ttu-id="eb2c5-152">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="eb2c5-152">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="eb2c5-153">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="eb2c5-153">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="eb2c5-154">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="eb2c5-154">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="eb2c5-155">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="eb2c5-155">Hosting Interfaces</span></span>](hosting-interfaces.md)
