---
description: 'Дополнительные сведения о методе: IHostSecurityManager:: SetSecurityContext'
title: Метод IHostSecurityManager::SetSecurityContext
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type:
- apiref
ms.openlocfilehash: ee2de40e043e626aba1d75540faab3cae4c8fb7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671481"
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="a5c14-103">Метод IHostSecurityManager::SetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="a5c14-103">IHostSecurityManager::SetSecurityContext Method</span></span>

<span data-ttu-id="a5c14-104">Задает контекст безопасности выполняемого в данный момент потока.</span><span class="sxs-lookup"><span data-stu-id="a5c14-104">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c14-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a5c14-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5c14-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a5c14-106">Parameters</span></span>  

 `eContextType`  
 <span data-ttu-id="a5c14-107">окне Одно из значений [еконтексттипе](econtexttype-enumeration.md) , указывающее, какой тип контекста используется средой CLR для размещения на узле.</span><span class="sxs-lookup"><span data-stu-id="a5c14-107">[in] One of the [EContextType](econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="a5c14-108">заполняет Указатель на адрес нового объекта [IHostSecurityContext](ihostsecuritycontext-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a5c14-108">[out] A pointer to the address of a new [IHostSecurityContext](ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5c14-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a5c14-109">Return Value</span></span>  
  
|<span data-ttu-id="a5c14-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5c14-110">HRESULT</span></span>|<span data-ttu-id="a5c14-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="a5c14-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5c14-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5c14-112">S_OK</span></span>|<span data-ttu-id="a5c14-113">`SetSecurityContext` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="a5c14-113">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="a5c14-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a5c14-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a5c14-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="a5c14-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a5c14-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a5c14-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a5c14-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="a5c14-117">The call timed out.</span></span>|  
|<span data-ttu-id="a5c14-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a5c14-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a5c14-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="a5c14-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a5c14-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a5c14-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a5c14-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="a5c14-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a5c14-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a5c14-122">E_FAIL</span></span>|<span data-ttu-id="a5c14-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="a5c14-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a5c14-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="a5c14-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a5c14-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a5c14-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5c14-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="a5c14-126">Remarks</span></span>  

 <span data-ttu-id="a5c14-127">Среда CLR вызывает `SetSecurityContext` в нескольких сценариях.</span><span class="sxs-lookup"><span data-stu-id="a5c14-127">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="a5c14-128">Перед выполнением конструкторов классов и модулей и методов завершения среда CLR вызывает `SetSecurityContext` для защиты узла от сбоев при выполнении.</span><span class="sxs-lookup"><span data-stu-id="a5c14-128">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="a5c14-129">Затем он сбрасывает контекст безопасности до исходного состояния после выполнения конструктора или метода завершения, используя другой вызов `SetSecurityContext` .</span><span class="sxs-lookup"><span data-stu-id="a5c14-129">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="a5c14-130">Аналогичный шаблон происходит при завершении ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="a5c14-130">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="a5c14-131">Если узел реализует [IHostIoCompletionManager](ihostiocompletionmanager-interface.md), среда CLR вызывает `SetSecurityContext` после того, как узел вызывает [ICLRIoCompletionManager:: OnComplete](iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="a5c14-131">If the host implements [IHostIoCompletionManager](ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="a5c14-132">В асинхронных точках рабочих потоков среда CLR вызывает `SetSecurityContext` в <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> или внутри [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md)в зависимости от того, РЕАЛИЗУЕТ ли узел или CLR пул потоков.</span><span class="sxs-lookup"><span data-stu-id="a5c14-132">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5c14-133">Требования</span><span class="sxs-lookup"><span data-stu-id="a5c14-133">Requirements</span></span>  

 <span data-ttu-id="a5c14-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5c14-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5c14-135">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a5c14-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5c14-136">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a5c14-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5c14-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5c14-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c14-138">См. также</span><span class="sxs-lookup"><span data-stu-id="a5c14-138">See also</span></span>

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- [<span data-ttu-id="a5c14-139">Перечисление EContextType</span><span class="sxs-lookup"><span data-stu-id="a5c14-139">EContextType Enumeration</span></span>](econtexttype-enumeration.md)
- [<span data-ttu-id="a5c14-140">Интерфейс ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="a5c14-140">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="a5c14-141">Интерфейс IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="a5c14-141">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="a5c14-142">Интерфейс IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="a5c14-142">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="a5c14-143">Интерфейс IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="a5c14-143">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="a5c14-144">Интерфейс IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="a5c14-144">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
