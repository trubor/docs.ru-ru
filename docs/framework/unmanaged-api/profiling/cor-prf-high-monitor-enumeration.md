---
description: 'Дополнительные сведения: перечисление COR_PRF_HIGH_MONITOR'
title: Перечисление COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 800bad21af96d8bbdf73f2af799f474f11294705
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648770"
---
# <a name="cor_prf_high_monitor-enumeration"></a><span data-ttu-id="36934-103">Перечисление COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="36934-103">COR_PRF_HIGH_MONITOR Enumeration</span></span>

<span data-ttu-id="36934-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="36934-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
<span data-ttu-id="36934-105">Предоставляет флаги в дополнение к тем, которые находятся в перечислении [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) , которые профилировщик может указать в методе [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) при загрузке.</span><span class="sxs-lookup"><span data-stu-id="36934-105">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36934-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="36934-106">Syntax</span></span>  
  
```cpp
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,
    COR_PRF_HIGH_DISABLE_TIERED_COMPILATION       = 0x00000008,
    COR_PRF_HIGH_BASIC_GC                         = 0x00000010,
    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS         = 0x00000020,
    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED    = 0x00000040,
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED |
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS |
                                                    COR_PRF_HIGH_BASIC_GC |
                                                    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS |
                                                    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = COR_PRF_HIGH_DISABLE_TIERED_COMPILATION  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="36934-107">Члены</span><span class="sxs-lookup"><span data-stu-id="36934-107">Members</span></span>  
  
|<span data-ttu-id="36934-108">Член</span><span class="sxs-lookup"><span data-stu-id="36934-108">Member</span></span>|<span data-ttu-id="36934-109">Описание</span><span class="sxs-lookup"><span data-stu-id="36934-109">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="36934-110">Флаги не установлены.</span><span class="sxs-lookup"><span data-stu-id="36934-110">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="36934-111">Управляет обратным вызовом [ICorProfilerCallback6:: жетассемблиреференце](icorprofilercallback6-getassemblyreferences-method.md) для добавления ссылок на сборки во время анализа закрытия ссылок на сборки CLR.</span><span class="sxs-lookup"><span data-stu-id="36934-111">Controls the [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="36934-112">Управляет обратным вызовом [ICorProfilerCallback7:: модулеинмеморисимболсупдатед](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) для обновлений потока символов, связанного с модулем в памяти.</span><span class="sxs-lookup"><span data-stu-id="36934-112">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="36934-113">Управляет обратным вызовом [ICorProfilerCallback9::D инамикмесодунлоадед](icorprofilercallback9-dynamicmethodunloaded-method.md) для указания, когда динамический метод был собран и выгружен.</span><span class="sxs-lookup"><span data-stu-id="36934-113">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="36934-114">Только .NET Core 3,0 и более поздние версии: отключает [многоуровневую компиляцию](../../../core/whats-new/dotnet-core-3-0.md) для профилировщиков.</span><span class="sxs-lookup"><span data-stu-id="36934-114">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="36934-115">Только .NET Core 3,0 и более поздние версии: предоставляет параметр профилирования с упрощенной сборкой мусора по сравнению с [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="36934-115">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="36934-116">Управляет только обратными вызовами  [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)и [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) .</span><span class="sxs-lookup"><span data-stu-id="36934-116">Controls only the  [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="36934-117">В отличие от `COR_PRF_MONITOR_GC` флага, не `COR_PRF_HIGH_BASIC_GC` отключает параллельную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="36934-117">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="36934-118">Только для .NET Core 3,0 и более поздних версий: включает обратные вызовы [MovedReferences](icorprofilercallback-movedreferences-method.md) и [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) для сжатия GC.</span><span class="sxs-lookup"><span data-stu-id="36934-118">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="36934-119">.NET Core 3,0 и более поздние версии: аналогично [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md) , но предоставляет сведения о выделении объектов для кучи больших объектов (LOH).</span><span class="sxs-lookup"><span data-stu-id="36934-119">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the large object heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="36934-120">Представляет все флаги `COR_PRF_HIGH_MONITOR`, для которых необходимы улучшенные профилировщиком изображения.</span><span class="sxs-lookup"><span data-stu-id="36934-120">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="36934-121">Он соответствует `COR_PRF_REQUIRE_PROFILE_IMAGE` флагу в перечислении [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="36934-121">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="36934-122">Представляет все флаги `COR_PRF_HIGH_MONITOR`, которые могут быть установлены после присоединения профилировщика к выполняющемуся приложению.</span><span class="sxs-lookup"><span data-stu-id="36934-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="36934-123">Представляет все флаги `COR_PRF_HIGH_MONITOR`, которые могут быть установлены только во время инициализации.</span><span class="sxs-lookup"><span data-stu-id="36934-123">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="36934-124">Попытка изменить какой-нибудь из этих флагов в другом месте вызовет значение `HRESULT`, указывающее на сбой.</span><span class="sxs-lookup"><span data-stu-id="36934-124">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36934-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="36934-125">Remarks</span></span>

<span data-ttu-id="36934-126">`COR_PRF_HIGH_MONITOR`Флаги используются с `pdwEventsHigh` параметром методов [ICorProfilerInfo5:: GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) и [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="36934-126">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="36934-127">Начиная с платформа .NET Framework 4.6.1 значение `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` изменено с 0 на `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="36934-127">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="36934-128">Начиная с платформа .NET Framework 4.7.2, его значение изменилось с `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` на `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS` .</span><span class="sxs-lookup"><span data-stu-id="36934-128">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>

<span data-ttu-id="36934-129">`COR_PRF_HIGH_MONITOR_IMMUTABLE` должна быть битовой маской, представляющей все флаги, которые могут быть установлены только во время инициализации.</span><span class="sxs-lookup"><span data-stu-id="36934-129">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="36934-130">Попытка изменить любой из этих флагов в других случаях приведет к неудаче `HRESULT` .</span><span class="sxs-lookup"><span data-stu-id="36934-130">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="36934-131">Требования</span><span class="sxs-lookup"><span data-stu-id="36934-131">Requirements</span></span>

<span data-ttu-id="36934-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36934-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="36934-133">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36934-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="36934-134">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36934-134">**Library:** CorGuids.lib</span></span>  
  
<span data-ttu-id="36934-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36934-135">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36934-136">См. также</span><span class="sxs-lookup"><span data-stu-id="36934-136">See also</span></span>

- [<span data-ttu-id="36934-137">Перечисления профилирования</span><span class="sxs-lookup"><span data-stu-id="36934-137">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="36934-138">Перечисление COR_PRF_MONITOR</span><span class="sxs-lookup"><span data-stu-id="36934-138">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="36934-139">Интерфейс ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="36934-139">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
