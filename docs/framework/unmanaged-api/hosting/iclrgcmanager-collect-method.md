---
description: 'Дополнительные сведения о методе: Иклргкманажер:: забрать'
title: Метод ICLRGCManager::Collect
ms.date: 03/30/2017
api_name:
- ICLRGCManager.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type:
- apiref
ms.openlocfilehash: 7c2649f7ce3472c504c1e48a203cf89d4b8508e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746065"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="dbbc9-103">Метод ICLRGCManager::Collect</span><span class="sxs-lookup"><span data-stu-id="dbbc9-103">ICLRGCManager::Collect Method</span></span>

<span data-ttu-id="dbbc9-104">Вызывает принудительную сборку мусора для указанного поколения.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-104">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbbc9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dbbc9-105">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbbc9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dbbc9-106">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="dbbc9-107">окне Поколение, которое необходимо получить.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-107">[in] The generation to collect.</span></span> <span data-ttu-id="dbbc9-108">Значение-1 вызывает сбор всех поколений.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-108">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbbc9-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dbbc9-109">Return Value</span></span>  
  
|<span data-ttu-id="dbbc9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dbbc9-110">HRESULT</span></span>|<span data-ttu-id="dbbc9-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="dbbc9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dbbc9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="dbbc9-112">S_OK</span></span>|<span data-ttu-id="dbbc9-113">`Collect` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-113">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="dbbc9-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dbbc9-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dbbc9-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dbbc9-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dbbc9-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dbbc9-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-117">The call timed out.</span></span>|  
|<span data-ttu-id="dbbc9-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dbbc9-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dbbc9-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dbbc9-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dbbc9-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dbbc9-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dbbc9-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dbbc9-122">E_FAIL</span></span>|<span data-ttu-id="dbbc9-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dbbc9-124">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dbbc9-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbbc9-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="dbbc9-126">Remarks</span></span>  

 <span data-ttu-id="dbbc9-127">`Collect`Метод заставляет сборщик мусора среды CLR выполнить сбор данных независимо от его текущего состояния.</span><span class="sxs-lookup"><span data-stu-id="dbbc9-127">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbbc9-128">Требования</span><span class="sxs-lookup"><span data-stu-id="dbbc9-128">Requirements</span></span>  

 <span data-ttu-id="dbbc9-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbbc9-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbbc9-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dbbc9-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbbc9-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbbc9-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbbc9-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbbc9-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbbc9-133">См. также</span><span class="sxs-lookup"><span data-stu-id="dbbc9-133">See also</span></span>

- [<span data-ttu-id="dbbc9-134">Автоматическое управление памятью</span><span class="sxs-lookup"><span data-stu-id="dbbc9-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="dbbc9-135">Сборка мусора</span><span class="sxs-lookup"><span data-stu-id="dbbc9-135">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="dbbc9-136">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="dbbc9-136">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="dbbc9-137">Интерфейс ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="dbbc9-137">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="dbbc9-138">Интерфейсы размещения CLR</span><span class="sxs-lookup"><span data-stu-id="dbbc9-138">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="dbbc9-139">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="dbbc9-139">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="dbbc9-140">Размещение</span><span class="sxs-lookup"><span data-stu-id="dbbc9-140">Hosting</span></span>](index.md)
