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
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a>Метод ICorProfilerInfo10:: Енумератеобжектреференцес

При наличии ObjectID, callback и Клиентдата перечисляет ссылки на все объекты (если таковые имеются).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a>Параметры

`objectId` окне Объект для перечисления ссылок.

`callback` окне Функция, которая будет вызываться со ссылками для объекта.

`clientData` окне Данные, предоставленные профилировщиком, передаются в `callback` функцию.

## <a name="remarks"></a>Remarks

`EnumerateObjectReferences`Метод аналогичен [ObjectReferences](icorprofilercallback-objectreferences-method.md), за исключением того, что он просматривает ссылки по запросу для профилировщика вместо предварительного выделения массива для хранения ссылок.

## <a name="requirements"></a>Требования

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).

**Заголовок:** CorProf.idl, CorProf.h

**Библиотека:** CorGuids.lib

**Версии .NET:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerInfo10](icorprofilerinfo10-interface.md)
