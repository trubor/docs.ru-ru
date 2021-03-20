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
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>Метод ICorProfilerCallback5::ConditionalWeakTableElementReferences

Идентифицирует транзитивное замыкание объектов, на которые ссылаются эти корневые элементы как через прямые ссылки на поля члена, так и через зависимости `ConditionalWeakTable`.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a>Параметры

`cRootRefs` окне Число элементов в `keyRefIds` `valueRefIds` `rootIds` массивах, и.

`keyRefIds` окне Массив идентификаторов объектов, каждый из которых содержит `ObjectID` для первичного элемента в паре зависимых маркеров.

`valueRefIds` окне Массив идентификаторов объектов, каждый из которых содержит `ObjectID` для вторичного элемента в паре зависимых маркеров. ( `keyRefIds[i]` продолжает `valueRefIds[i]` существовать.)

`rootIds` окне Массив `GCHandleID` значений, указывающий на целое число, которое содержит дополнительные сведения об корне сборки мусора.

Ни одно из значений `ObjectID`, возвращаемых методом `ConditionalWeakTableElementReferences` во время обратного вызова самого себя, не является допустимым, потому что сборка мусора может находиться в процессе перемещения объектов из старого в новое расположение. В связи с этим профилировщикам не следует пытаться проверять объекты во время вызова `ConditionalWeakTableElementReferences`. Вызов `GarbageCollectionFinished` означает, что все объекты перемещены в новые расположения и можно проводить проверку.

## <a name="example"></a>Пример

В следующем примере кода показано, как реализовать [ICorProfilerCallback5](icorprofilercallback5-interface.md) и использовать этот метод.

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

## <a name="remarks"></a>Remarks

Профилировщик для платформа .NET Framework 4,5 или более поздних версий реализует интерфейс [ICorProfilerCallback5](icorprofilercallback5-interface.md) и записывает зависимости, заданные `ConditionalWeakTableElementReferences` методом. `ICorProfilerCallback5` предоставляет полный набор зависимостей между динамическими объектами, представленными `ConditionalWeakTable` записями. Эти зависимости и ссылки на поля элементов, заданные методом [ICorProfilerCallback:: ObjectReferences](icorprofilercallback-objectreferences-method.md) , позволяют управляемому профилировщику создавать полный граф объектов для активных объектов.

## <a name="requirements"></a>Требования

**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).

**Заголовок:** CorProf.idl, CorProf.h

**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]

## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback5](icorprofilercallback5-interface.md)
