---
description: 'Дополнительные сведения о методе: ICorProfilerCallback5:: ConditionalWeakTableElementReferences'
title: Метод ICorProfilerCallback5::ConditionalWeakTableElementReferences
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5.ConditionalWeakTableReferences
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ConditionalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
ms.openlocfilehash: ded43da029fe0b4c2a645823e62ca66b480f095c
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760279"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="f7b4d-103">Метод ICorProfilerCallback5::ConditionalWeakTableElementReferences</span><span class="sxs-lookup"><span data-stu-id="f7b4d-103">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>

<span data-ttu-id="f7b4d-104">Идентифицирует транзитивное замыкание объектов, на которые ссылаются эти корневые элементы как через прямые ссылки на поля члена, так и через зависимости `ConditionalWeakTable`.</span><span class="sxs-lookup"><span data-stu-id="f7b4d-104">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>

## <a name="syntax"></a><span data-ttu-id="f7b4d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f7b4d-105">Syntax</span></span>

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a><span data-ttu-id="f7b4d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f7b4d-106">Parameters</span></span>

<span data-ttu-id="f7b4d-107">`cRootRefs` окне Число элементов в `keyRefIds` `valueRefIds` `rootIds` массивах, и.</span><span class="sxs-lookup"><span data-stu-id="f7b4d-107">`cRootRefs` [in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>

<span data-ttu-id="f7b4d-108">`keyRefIds` окне Массив идентификаторов объектов, каждый из которых содержит `ObjectID` для первичного элемента в паре зависимых маркеров.</span><span class="sxs-lookup"><span data-stu-id="f7b4d-108">`keyRefIds` [in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>

<span data-ttu-id="f7b4d-109">`valueRefIds` окне Массив идентификаторов объектов, каждый из которых содержит `ObjectID` для вторичного элемента в паре зависимых маркеров.</span><span class="sxs-lookup"><span data-stu-id="f7b4d-109">`valueRefIds` [in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="f7b4d-110">( `keyRefIds[i]` продолжает `valueRefIds[i]` существовать.)</span><span class="sxs-lookup"><span data-stu-id="f7b4d-110">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>

<span data-ttu-id="f7b4d-111">`rootIds` окне Массив `GCHandleID` значений, указывающий на целое число, которое содержит дополнительные сведения об корне сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="f7b4d-111">`rootIds` [in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>

<span data-ttu-id="f7b4d-112">Ни одно из значений `ObjectID`, возвращаемых методом `ConditionalWeakTableElementReferences` во время обратного вызова самого себя, не является допустимым, потому что сборка мусора может находиться в процессе перемещения объектов из старого в новое расположение.</span><span class="sxs-lookup"><span data-stu-id="f7b4d-112">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="f7b4d-113">В связи с этим профилировщикам не следует пытаться проверять объекты во время вызова `ConditionalWeakTableElementReferences`.</span><span class="sxs-lookup"><span data-stu-id="f7b4d-113">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="f7b4d-114">Вызов `GarbageCollectionFinished` означает, что все объекты перемещены в новые расположения и можно проводить проверку.</span><span class="sxs-lookup"><span data-stu-id="f7b4d-114">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>

## <a name="example"></a><span data-ttu-id="f7b4d-115">Пример</span><span class="sxs-lookup"><span data-stu-id="f7b4d-115">Example</span></span>

<span data-ttu-id="f7b4d-116">В следующем примере кода показано, как реализовать [ICorProfilerCallback5](icorprofilercallback5-interface.md) и использовать этот метод.</span><span class="sxs-lookup"><span data-stu-id="f7b4d-116">The following code example demonstrates how to implement [ICorProfilerCallback5](icorprofilercallback5-interface.md) and use this method.</span></span>

```cpp
HRESULT Callback5Impl::ConditionalWeakTableElementReferences(
    ULONG      cRootRefs,
    ObjectID   keyRefIds[],
    ObjectID   valueRefIds[],
    GCHandleID rootIds[])
{
    printf("Callback5Impl::ConditionalWeakTableElementReferences called\n");
    for (unsigned int i = 0; i < cRootRefs; ++i)
    {
        // Save dependency to XML for later retrieval
        PersistDependencyToXml(rootIds[i], keyRefIds[i], valueRefIds[i]);
        // or store dependency to an internal map
        m_cwt_deps->add_dep(rootIds[i], keyRefIds[i], valueRefIds[i]);
        // or add arc to object graph
        m_obj_graph->add_arc(keyRefIds[i], valueRefIds[i], rootIds[i]);
    }
    return S_OK;
}
```

## <a name="remarks"></a><span data-ttu-id="f7b4d-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="f7b4d-117">Remarks</span></span>

<span data-ttu-id="f7b4d-118">Профилировщик для платформа .NET Framework 4,5 или более поздних версий реализует интерфейс [ICorProfilerCallback5](icorprofilercallback5-interface.md) и записывает зависимости, заданные `ConditionalWeakTableElementReferences` методом.</span><span class="sxs-lookup"><span data-stu-id="f7b4d-118">A profiler for the .NET Framework 4.5 or later versions implements the [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="f7b4d-119">`ICorProfilerCallback5` предоставляет полный набор зависимостей между динамическими объектами, представленными `ConditionalWeakTable` записями.</span><span class="sxs-lookup"><span data-stu-id="f7b4d-119">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="f7b4d-120">Эти зависимости и ссылки на поля элементов, заданные методом [ICorProfilerCallback:: ObjectReferences](icorprofilercallback-objectreferences-method.md) , позволяют управляемому профилировщику создавать полный граф объектов для активных объектов.</span><span class="sxs-lookup"><span data-stu-id="f7b4d-120">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>

## <a name="requirements"></a><span data-ttu-id="f7b4d-121">Требования</span><span class="sxs-lookup"><span data-stu-id="f7b4d-121">Requirements</span></span>

<span data-ttu-id="f7b4d-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7b4d-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f7b4d-123">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f7b4d-123">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="f7b4d-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7b4d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f7b4d-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f7b4d-125">See also</span></span>

- [<span data-ttu-id="f7b4d-126">Интерфейс ICorProfilerCallback5</span><span class="sxs-lookup"><span data-stu-id="f7b4d-126">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)
