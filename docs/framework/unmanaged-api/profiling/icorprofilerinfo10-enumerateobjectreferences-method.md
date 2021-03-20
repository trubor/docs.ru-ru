---
description: 'Дополнительные сведения о методе: ICorProfilerInfo10:: Енумератеобжектреференцес'
title: 'ICorProfilerInfo10:: Енумератеобжектреференцес'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: bcd374aec2944977a0745177995ba8adf0cce9b7
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759421"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="cdee4-103">Метод ICorProfilerInfo10:: Енумератеобжектреференцес</span><span class="sxs-lookup"><span data-stu-id="cdee4-103">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="cdee4-104">При наличии ObjectID, callback и Клиентдата перечисляет ссылки на все объекты (если таковые имеются).</span><span class="sxs-lookup"><span data-stu-id="cdee4-104">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="cdee4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cdee4-105">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="cdee4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cdee4-106">Parameters</span></span>

<span data-ttu-id="cdee4-107">`objectId` окне Объект для перечисления ссылок.</span><span class="sxs-lookup"><span data-stu-id="cdee4-107">`objectId` [in] The object to enumerate references on.</span></span>

<span data-ttu-id="cdee4-108">`callback` окне Функция, которая будет вызываться со ссылками для объекта.</span><span class="sxs-lookup"><span data-stu-id="cdee4-108">`callback` [in] The function that will be called with the references for the object.</span></span>

<span data-ttu-id="cdee4-109">`clientData` окне Данные, предоставленные профилировщиком, передаются в `callback` функцию.</span><span class="sxs-lookup"><span data-stu-id="cdee4-109">`clientData` [in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="cdee4-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="cdee4-110">Remarks</span></span>

<span data-ttu-id="cdee4-111">`EnumerateObjectReferences`Метод аналогичен [ObjectReferences](icorprofilercallback-objectreferences-method.md), за исключением того, что он просматривает ссылки по запросу для профилировщика вместо предварительного выделения массива для хранения ссылок.</span><span class="sxs-lookup"><span data-stu-id="cdee4-111">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="cdee4-112">Требования</span><span class="sxs-lookup"><span data-stu-id="cdee4-112">Requirements</span></span>

<span data-ttu-id="cdee4-113">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="cdee4-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="cdee4-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cdee4-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="cdee4-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdee4-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="cdee4-116">**Версии .NET:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdee4-116">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cdee4-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="cdee4-117">See also</span></span>

- [<span data-ttu-id="cdee4-118">Интерфейс ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="cdee4-118">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
