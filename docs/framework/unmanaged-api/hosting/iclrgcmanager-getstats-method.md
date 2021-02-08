---
description: 'Дополнительные сведения о методе: Иклргкманажер:: stats'
title: Метод ICLRGCManager::GetStats
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
ms.openlocfilehash: 94b20fb313f06d73f1e7fafd1f46fefb0da3fe95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790026"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="2237c-103">Метод ICLRGCManager::GetStats</span><span class="sxs-lookup"><span data-stu-id="2237c-103">ICLRGCManager::GetStats Method</span></span>

<span data-ttu-id="2237c-104">Возвращает набор текущих статистических данных о системе сборки мусора среды CLR.</span><span class="sxs-lookup"><span data-stu-id="2237c-104">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2237c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2237c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2237c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2237c-106">Parameters</span></span>  

 `pStats`  
 <span data-ttu-id="2237c-107">[вход, выход] Экземпляр [COR_GC_STATS](cor-gc-stats-structure.md) , содержащий запрошенную статистику.</span><span class="sxs-lookup"><span data-stu-id="2237c-107">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2237c-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2237c-108">Return Value</span></span>  
  
|<span data-ttu-id="2237c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2237c-109">HRESULT</span></span>|<span data-ttu-id="2237c-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="2237c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2237c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2237c-111">S_OK</span></span>|<span data-ttu-id="2237c-112">`GetStats` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="2237c-112">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="2237c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2237c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2237c-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="2237c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2237c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2237c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2237c-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="2237c-116">The call timed out.</span></span>|  
|<span data-ttu-id="2237c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2237c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2237c-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="2237c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2237c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2237c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2237c-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="2237c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2237c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2237c-121">E_FAIL</span></span>|<span data-ttu-id="2237c-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="2237c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2237c-123">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="2237c-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2237c-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2237c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2237c-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="2237c-125">Remarks</span></span>  

 <span data-ttu-id="2237c-126">Среда CLR вычисляет и возвращает только те статистические данные, которые указаны в `Flags` поле `pStats` .</span><span class="sxs-lookup"><span data-stu-id="2237c-126">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="2237c-127">Задайте в `Flags` поле одно или несколько значений перечисления [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) , чтобы указать, какие статистические данные должны быть заданы в структуре [COR_GC_STATS](cor-gc-stats-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="2237c-127">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="2237c-128">Пример использования таков:</span><span class="sxs-lookup"><span data-stu-id="2237c-128">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2237c-129">Требования</span><span class="sxs-lookup"><span data-stu-id="2237c-129">Requirements</span></span>  

 <span data-ttu-id="2237c-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2237c-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2237c-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2237c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2237c-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2237c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2237c-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2237c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2237c-134">См. также</span><span class="sxs-lookup"><span data-stu-id="2237c-134">See also</span></span>

- [<span data-ttu-id="2237c-135">Автоматическое управление памятью</span><span class="sxs-lookup"><span data-stu-id="2237c-135">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="2237c-136">Структура COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="2237c-136">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="2237c-137">Перечисление COR_GC_STAT_TYPES</span><span class="sxs-lookup"><span data-stu-id="2237c-137">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="2237c-138">Сборка мусора</span><span class="sxs-lookup"><span data-stu-id="2237c-138">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="2237c-139">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="2237c-139">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="2237c-140">Интерфейс ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="2237c-140">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="2237c-141">Интерфейсы размещения CLR</span><span class="sxs-lookup"><span data-stu-id="2237c-141">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="2237c-142">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="2237c-142">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="2237c-143">Размещение</span><span class="sxs-lookup"><span data-stu-id="2237c-143">Hosting</span></span>](index.md)
