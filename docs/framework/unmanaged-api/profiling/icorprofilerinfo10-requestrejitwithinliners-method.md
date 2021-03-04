---
description: 'Дополнительные сведения о методе: ICorProfilerInfo10:: Рекуестрежитвисинлинерс'
title: 'ICorProfilerInfo10:: Рекуестрежитвисинлинерс'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 925a61bf2521950cad7fb0dce8f1484198f3f806
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106518"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="ef644-103">Метод ICorProfilerInfo10:: Рекуестрежитвисинлинерс</span><span class="sxs-lookup"><span data-stu-id="ef644-103">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="ef644-104">Режитс запрошенные методы, а также любые запрашиваются методы.</span><span class="sxs-lookup"><span data-stu-id="ef644-104">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef644-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ef644-105">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a><span data-ttu-id="ef644-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ef644-106">Parameters</span></span>

- `dwRejitFlags`

  <span data-ttu-id="ef644-107">\[in] битовая маска [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="ef644-107">\[in] A bitmask of [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span></span>

- `cFunctions`

  <span data-ttu-id="ef644-108">\[в] число функций для повторной компиляции.</span><span class="sxs-lookup"><span data-stu-id="ef644-108">\[in] The number of functions to recompile.</span></span>

- `moduleIds`

  <span data-ttu-id="ef644-109">\[в] задает `moduleId` часть `module` пар (, `methodDef` ), определяющих функции для повторной компиляции.</span><span class="sxs-lookup"><span data-stu-id="ef644-109">\[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

- `methodIds`

  <span data-ttu-id="ef644-110">\[в] задает `methodId` часть `module` пар (, `methodDef` ), определяющих функции для повторной компиляции.</span><span class="sxs-lookup"><span data-stu-id="ef644-110">\[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef644-111">Комментарии</span><span class="sxs-lookup"><span data-stu-id="ef644-111">Remarks</span></span>

<span data-ttu-id="ef644-112">[Рекуестрежит](icorprofilerinfo4-requestrejit-method.md) не выполняет отслеживание встроенных методов.</span><span class="sxs-lookup"><span data-stu-id="ef644-112">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="ef644-113">Профилировщик ожидал блокировать встраивание или отслеживание встраивания, а также вызов `RequestReJIT` всех строк, чтобы гарантировать, что каждый экземпляр встроенного метода был режиттед.</span><span class="sxs-lookup"><span data-stu-id="ef644-113">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="ef644-114">Это создает проблему с ReJIT при присоединении, так как профилировщик отсутствует для мониторинга встраивания.</span><span class="sxs-lookup"><span data-stu-id="ef644-114">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="ef644-115">Этот метод может быть вызван, чтобы гарантировать, что полный набор Режиттед также будет недоступен.</span><span class="sxs-lookup"><span data-stu-id="ef644-115">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="ef644-116">Требования</span><span class="sxs-lookup"><span data-stu-id="ef644-116">Requirements</span></span>

<span data-ttu-id="ef644-117">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="ef644-117">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="ef644-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ef644-118">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="ef644-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef644-119">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ef644-120">**Версии .NET:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef644-120">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ef644-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ef644-121">See also</span></span>

- [<span data-ttu-id="ef644-122">Интерфейс ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="ef644-122">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
