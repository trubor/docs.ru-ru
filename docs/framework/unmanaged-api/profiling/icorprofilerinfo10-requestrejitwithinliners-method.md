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
ms.openlocfilehash: 3d85537030e042d53bb4ff859eb1d2c3a24a45a5
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760786"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="0f4fe-103">Метод ICorProfilerInfo10:: Рекуестрежитвисинлинерс</span><span class="sxs-lookup"><span data-stu-id="0f4fe-103">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="0f4fe-104">Режитс запрошенные методы, а также любые запрашиваются методы.</span><span class="sxs-lookup"><span data-stu-id="0f4fe-104">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f4fe-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0f4fe-105">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a><span data-ttu-id="0f4fe-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0f4fe-106">Parameters</span></span>

<span data-ttu-id="0f4fe-107">`dwRejitFlags` окне Битовая маска [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="0f4fe-107">`dwRejitFlags` [in] A bitmask of [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span></span>

<span data-ttu-id="0f4fe-108">`cFunctions` окне Число функций для повторной компиляции.</span><span class="sxs-lookup"><span data-stu-id="0f4fe-108">`cFunctions` [in] The number of functions to recompile.</span></span>

<span data-ttu-id="0f4fe-109">`moduleIds` окне Задает `moduleId` часть `module` пар (, `methodDef` ), определяющих функции для повторной компиляции.</span><span class="sxs-lookup"><span data-stu-id="0f4fe-109">`moduleIds` [in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

<span data-ttu-id="0f4fe-110">`methodIds` окне Задает `methodId` часть `module` пар (, `methodDef` ), определяющих функции для повторной компиляции.</span><span class="sxs-lookup"><span data-stu-id="0f4fe-110">`methodIds` [in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f4fe-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="0f4fe-111">Remarks</span></span>

<span data-ttu-id="0f4fe-112">[Рекуестрежит](icorprofilerinfo4-requestrejit-method.md) не выполняет отслеживание встроенных методов.</span><span class="sxs-lookup"><span data-stu-id="0f4fe-112">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="0f4fe-113">Профилировщик ожидал блокировать встраивание или отслеживание встраивания, а также вызов `RequestReJIT` всех строк, чтобы гарантировать, что каждый экземпляр встроенного метода был режиттед.</span><span class="sxs-lookup"><span data-stu-id="0f4fe-113">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="0f4fe-114">Это создает проблему с ReJIT при присоединении, так как профилировщик отсутствует для мониторинга встраивания.</span><span class="sxs-lookup"><span data-stu-id="0f4fe-114">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="0f4fe-115">Этот метод может быть вызван, чтобы гарантировать, что полный набор Режиттед также будет недоступен.</span><span class="sxs-lookup"><span data-stu-id="0f4fe-115">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f4fe-116">Требования</span><span class="sxs-lookup"><span data-stu-id="0f4fe-116">Requirements</span></span>

<span data-ttu-id="0f4fe-117">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="0f4fe-117">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="0f4fe-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0f4fe-118">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="0f4fe-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f4fe-119">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="0f4fe-120">**Версии .NET:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f4fe-120">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0f4fe-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0f4fe-121">See also</span></span>

- [<span data-ttu-id="0f4fe-122">Интерфейс ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="0f4fe-122">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
