---
description: 'Дополнительные сведения о методе: ICorProfilerInfo10:: Жетлохобжектсизесрешолд'
title: 'ICorProfilerInfo10:: Жетлохобжектсизесрешолд'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7dca887f6d0ff5f9360b0edaa1568bc4b1bb42ac
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759772"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>Метод ICorProfilerInfo10:: Жетлохобжектсизесрешолд

Возвращает значение заданного порога кучи больших объектов (LOH).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a>Параметры

`pThreshold` заполняет Пороговое значение кучи больших объектов в байтах.

## <a name="remarks"></a>Remarks

Объекты, превышающие пороговое значение кучи больших объектов, будут выделены в куче больших объектов. Начиная с .NET Core 3,0, порог кучи больших объектов можно настроить, он `pThreshold` будет содержать пороговое значение активной кучи больших объектов в байтах.

## <a name="requirements"></a>Требования

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).

**Заголовок:** CorProf.idl, CorProf.h

**Библиотека:** CorGuids.lib

**Версии .NET:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerInfo10](icorprofilerinfo10-interface.md)
