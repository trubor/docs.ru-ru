---
description: 'Дополнительные сведения о методе: ICLRGCManager2:: SetGCStartupLimitsEx'
title: Метод ICLRGCManager2::SetGCStartupLimitsEx
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
ms.openlocfilehash: 2a4801d2f6255f5f84e0a4bae7a1886689ee8dc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689242"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="83422-103">Метод ICLRGCManager2::SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="83422-103">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>

<span data-ttu-id="83422-104">Задает размер сегмента сборки мусора и максимальный размер поколения 0 для системы сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="83422-104">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83422-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="83422-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83422-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="83422-106">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="83422-107">окне Указанный размер сегмента сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="83422-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="83422-108">Минимальный размер сегмента — 4 МБ.</span><span class="sxs-lookup"><span data-stu-id="83422-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="83422-109">Размер сегментов можно увеличить с шагом в 1 МБ или больше.</span><span class="sxs-lookup"><span data-stu-id="83422-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="83422-110">окне Указанный максимальный размер для поколения 0.</span><span class="sxs-lookup"><span data-stu-id="83422-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="83422-111">Минимальный размер поколения 0 — 64 КБ.</span><span class="sxs-lookup"><span data-stu-id="83422-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83422-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="83422-112">Return Value</span></span>  
  
|<span data-ttu-id="83422-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83422-113">HRESULT</span></span>|<span data-ttu-id="83422-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="83422-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83422-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="83422-115">S_OK</span></span>|<span data-ttu-id="83422-116">`SetGCStartupLimitsEx` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="83422-116">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="83422-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83422-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83422-118">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="83422-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="83422-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="83422-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="83422-120">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="83422-120">The call timed out.</span></span>|  
|<span data-ttu-id="83422-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="83422-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="83422-122">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="83422-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="83422-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="83422-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="83422-124">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="83422-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="83422-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83422-125">E_FAIL</span></span>|<span data-ttu-id="83422-126">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="83422-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="83422-127">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="83422-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="83422-128">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="83422-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83422-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="83422-129">Remarks</span></span>  

 <span data-ttu-id="83422-130">Значения, которые `SetGCStartupLimitsEx` задаются, можно указать только перед запуском узла.</span><span class="sxs-lookup"><span data-stu-id="83422-130">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="83422-131">Последующие вызовы метода `SetGCStartupLimitsEx` игнорируются.</span><span class="sxs-lookup"><span data-stu-id="83422-131">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="83422-132">Чтобы задать любой параметр, не влияя на другой, укажите 0 (нуль) для параметра, который не нужно изменять.</span><span class="sxs-lookup"><span data-stu-id="83422-132">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83422-133">Требования</span><span class="sxs-lookup"><span data-stu-id="83422-133">Requirements</span></span>  

 <span data-ttu-id="83422-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83422-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83422-135">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="83422-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83422-136">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83422-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83422-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83422-137">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83422-138">См. также</span><span class="sxs-lookup"><span data-stu-id="83422-138">See also</span></span>

- [<span data-ttu-id="83422-139">Автоматическое управление памятью</span><span class="sxs-lookup"><span data-stu-id="83422-139">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="83422-140">Сборка мусора</span><span class="sxs-lookup"><span data-stu-id="83422-140">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="83422-141">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="83422-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="83422-142">Интерфейс ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="83422-142">ICLRGCManager2 Interface</span></span>](iclrgcmanager2-interface.md)
