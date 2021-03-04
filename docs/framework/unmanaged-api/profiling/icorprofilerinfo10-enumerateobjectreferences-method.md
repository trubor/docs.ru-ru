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
ms.openlocfilehash: c18532450e420f38413028a18630dbf3e308fa61
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106726"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="6de41-103">Метод ICorProfilerInfo10:: Енумератеобжектреференцес</span><span class="sxs-lookup"><span data-stu-id="6de41-103">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="6de41-104">При наличии ObjectID, callback и Клиентдата перечисляет ссылки на все объекты (если таковые имеются).</span><span class="sxs-lookup"><span data-stu-id="6de41-104">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="6de41-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6de41-105">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="6de41-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6de41-106">Parameters</span></span>

- `objectId`

  <span data-ttu-id="6de41-107">\[в] объект для перечисления ссылок.</span><span class="sxs-lookup"><span data-stu-id="6de41-107">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="6de41-108">\[in] функция, которая будет вызываться со ссылками на объект.</span><span class="sxs-lookup"><span data-stu-id="6de41-108">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="6de41-109">\[in] данные, предоставленные профилировщиком, передаются в `callback` функцию.</span><span class="sxs-lookup"><span data-stu-id="6de41-109">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="6de41-110">Комментарии</span><span class="sxs-lookup"><span data-stu-id="6de41-110">Remarks</span></span>

<span data-ttu-id="6de41-111">`EnumerateObjectReferences`Метод аналогичен [ObjectReferences](icorprofilercallback-objectreferences-method.md), за исключением того, что он просматривает ссылки по запросу для профилировщика вместо предварительного выделения массива для хранения ссылок.</span><span class="sxs-lookup"><span data-stu-id="6de41-111">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="6de41-112">Требования</span><span class="sxs-lookup"><span data-stu-id="6de41-112">Requirements</span></span>

<span data-ttu-id="6de41-113">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="6de41-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="6de41-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6de41-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="6de41-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6de41-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="6de41-116">**Версии .NET:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6de41-116">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6de41-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6de41-117">See also</span></span>

- [<span data-ttu-id="6de41-118">Интерфейс ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="6de41-118">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
