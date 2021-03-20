---
description: 'Дополнительные сведения о методе: ICorProfilerInfo10:: Исфрозенобжект'
title: 'ICorProfilerInfo10:: Исфрозенобжект'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: c4d31c96fd7470a153437ffb0125e81ca8ea77bd
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759759"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a>Метод ICorProfilerInfo10:: Исфрозенобжект

Определяет, находится ли объект в сегменте, доступном только для чтения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a>Параметры

`objectId` окне Объект для проверки.

`pbFrozen` заполняет Значение типа `BOOL` , указывающее, находится ли объект в сегменте, доступном только для чтения.

## <a name="requirements"></a>Требования

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).

**Заголовок:** CorProf.idl, CorProf.h

**Библиотека:** CorGuids.lib

**Версии .NET:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerInfo10](icorprofilerinfo10-interface.md)
