---
description: 'Дополнительные сведения о методе: IHostControl:: Жесостманажер'
title: Метод IHostControl::GetHostManager
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
ms.openlocfilehash: 7cc118808c8788504da2cc07a8c61c419d3c588f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708913"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="6ea94-103">Метод IHostControl::GetHostManager</span><span class="sxs-lookup"><span data-stu-id="6ea94-103">IHostControl::GetHostManager Method</span></span>

<span data-ttu-id="6ea94-104">Возвращает указатель интерфейса на реализацию интерфейса узла с указанным `IID` .</span><span class="sxs-lookup"><span data-stu-id="6ea94-104">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ea94-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6ea94-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ea94-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6ea94-106">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="6ea94-107">окне `IID` Интерфейс, для которого запрашиваются общеязыковая среда выполнения (CLR).</span><span class="sxs-lookup"><span data-stu-id="6ea94-107">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="6ea94-108">заполняет Указатель на интерфейс, реализуемый узлом, или значение null, если узел не поддерживает этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="6ea94-108">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ea94-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6ea94-109">Return Value</span></span>  
  
|<span data-ttu-id="6ea94-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ea94-110">HRESULT</span></span>|<span data-ttu-id="6ea94-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="6ea94-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ea94-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ea94-112">S_OK</span></span>|<span data-ttu-id="6ea94-113">`GetHostManager` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="6ea94-113">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="6ea94-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6ea94-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6ea94-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="6ea94-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6ea94-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6ea94-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6ea94-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="6ea94-117">The call timed out.</span></span>|  
|<span data-ttu-id="6ea94-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6ea94-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6ea94-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="6ea94-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6ea94-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6ea94-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6ea94-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="6ea94-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6ea94-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6ea94-122">E_FAIL</span></span>|<span data-ttu-id="6ea94-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="6ea94-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6ea94-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="6ea94-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6ea94-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6ea94-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6ea94-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6ea94-126">E_INVALIDARG</span></span>|<span data-ttu-id="6ea94-127">Запрошен `IID` недопустимый.</span><span class="sxs-lookup"><span data-stu-id="6ea94-127">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="6ea94-128">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="6ea94-128">E_NOINTERFACE</span></span>|<span data-ttu-id="6ea94-129">Запрошенный интерфейс не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="6ea94-129">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ea94-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="6ea94-130">Remarks</span></span>  

 <span data-ttu-id="6ea94-131">Среда CLR опрашивает узел, чтобы определить, поддерживает ли он один или несколько следующих интерфейсов:</span><span class="sxs-lookup"><span data-stu-id="6ea94-131">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="6ea94-132">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="6ea94-132">IHostMemoryManager</span></span>](ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="6ea94-133">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="6ea94-133">IHostTaskManager</span></span>](ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="6ea94-134">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="6ea94-134">IHostThreadPoolManager</span></span>](ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="6ea94-135">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="6ea94-135">IHostIoCompletionManager</span></span>](ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="6ea94-136">Метод ihostsyncmanager</span><span class="sxs-lookup"><span data-stu-id="6ea94-136">IHostSyncManager</span></span>](ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="6ea94-137">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="6ea94-137">IHostAssemblyManager</span></span>](ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="6ea94-138">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="6ea94-138">IHostGCManager</span></span>](ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="6ea94-139">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="6ea94-139">IHostPolicyManager</span></span>](ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="6ea94-140">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="6ea94-140">IHostSecurityManager</span></span>](ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="6ea94-141">Если узел поддерживает указанный интерфейс, он задает `ppObject` его реализацию этого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="6ea94-141">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="6ea94-142">В противном случае устанавливается `ppObject` значение null.</span><span class="sxs-lookup"><span data-stu-id="6ea94-142">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="6ea94-143">Среда CLR не вызывает `Release` диспетчеры узлов даже при завершении работы.</span><span class="sxs-lookup"><span data-stu-id="6ea94-143">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ea94-144">Требования</span><span class="sxs-lookup"><span data-stu-id="6ea94-144">Requirements</span></span>  

 <span data-ttu-id="6ea94-145">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ea94-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ea94-146">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6ea94-146">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ea94-147">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ea94-147">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ea94-148">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ea94-148">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ea94-149">См. также</span><span class="sxs-lookup"><span data-stu-id="6ea94-149">See also</span></span>

- [<span data-ttu-id="6ea94-150">Интерфейс IHostControl</span><span class="sxs-lookup"><span data-stu-id="6ea94-150">IHostControl Interface</span></span>](ihostcontrol-interface.md)
