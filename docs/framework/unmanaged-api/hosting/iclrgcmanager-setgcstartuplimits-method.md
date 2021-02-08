---
description: 'Дополнительные сведения о методе: Иклргкманажер:: Сетгкстартуплимитс'
title: Метод ICLRGCManager::SetGCStartupLimits
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
ms.openlocfilehash: 5614b41cfd7a7938cdb653d879119ddbd9560b9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789987"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="7f744-103">Метод ICLRGCManager::SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="7f744-103">ICLRGCManager::SetGCStartupLimits Method</span></span>

<span data-ttu-id="7f744-104">Задает размер сегмента сборки мусора и максимальный размер поколения 0 для системы сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="7f744-104">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7f744-105">Начиная с платформа .NET Framework 4,5 можно задать размер сегмента и максимальный размер поколения 0 в значениях, превышающих `DWORD` использование метода [ICLRGCManager2:: SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7f744-105">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f744-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7f744-106">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f744-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="7f744-107">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="7f744-108">окне Указанный размер сегмента сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="7f744-108">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="7f744-109">Минимальный размер сегмента — 4 МБ.</span><span class="sxs-lookup"><span data-stu-id="7f744-109">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="7f744-110">Размер сегментов можно увеличить с шагом в 1 МБ или больше.</span><span class="sxs-lookup"><span data-stu-id="7f744-110">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="7f744-111">окне Указанный максимальный размер для поколения 0.</span><span class="sxs-lookup"><span data-stu-id="7f744-111">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="7f744-112">Минимальный размер поколения 0 — 64 КБ.</span><span class="sxs-lookup"><span data-stu-id="7f744-112">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f744-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7f744-113">Return Value</span></span>  
  
|<span data-ttu-id="7f744-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f744-114">HRESULT</span></span>|<span data-ttu-id="7f744-115">Описание:</span><span class="sxs-lookup"><span data-stu-id="7f744-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f744-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f744-116">S_OK</span></span>|<span data-ttu-id="7f744-117">`SetGCStartupLimits` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="7f744-117">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="7f744-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7f744-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7f744-119">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="7f744-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7f744-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7f744-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7f744-121">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="7f744-121">The call timed out.</span></span>|  
|<span data-ttu-id="7f744-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7f744-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7f744-123">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="7f744-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7f744-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7f744-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7f744-125">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="7f744-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7f744-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7f744-126">E_FAIL</span></span>|<span data-ttu-id="7f744-127">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="7f744-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7f744-128">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="7f744-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7f744-129">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7f744-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f744-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="7f744-130">Remarks</span></span>  

 <span data-ttu-id="7f744-131">Значения, которые `SetGCStartupLimits` задаются, можно указать только один раз.</span><span class="sxs-lookup"><span data-stu-id="7f744-131">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="7f744-132">Последующие вызовы метода `SetGCStartupLimits` игнорируются.</span><span class="sxs-lookup"><span data-stu-id="7f744-132">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f744-133">Требования</span><span class="sxs-lookup"><span data-stu-id="7f744-133">Requirements</span></span>  

 <span data-ttu-id="7f744-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f744-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f744-135">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7f744-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f744-136">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f744-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f744-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f744-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f744-138">См. также</span><span class="sxs-lookup"><span data-stu-id="7f744-138">See also</span></span>

- [<span data-ttu-id="7f744-139">Автоматическое управление памятью</span><span class="sxs-lookup"><span data-stu-id="7f744-139">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="7f744-140">Сборка мусора</span><span class="sxs-lookup"><span data-stu-id="7f744-140">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="7f744-141">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="7f744-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="7f744-142">Интерфейс ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="7f744-142">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
