---
description: 'Дополнительные сведения о методе: ICorProfilerInfo9:: Жетнативекодестартаддрессес'
title: 'ICorProfilerInfo9:: Жетнативекодестартаддрессес'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 062aebf6d5bed208ea71b215bd9f857b82483673
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759054"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>Метод ICorProfilerInfo9:: Жетнативекодестартаддрессес

При наличии кода functionId и Режитид перечисляются начальные адреса всех откомпилированных версий этого кода, которые в настоящее время существуют.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a>Параметры

`functionId` окне Идентификатор функции, для которой должны возвращаться начальные адреса машинного кода.

`reJitId` окне Удостоверение JIT-повторно скомпилированной функции.

`cCodeStartAddresses` окне Максимальный размер `codeStartAddresses` массива.

`pcCodeStartAddresses` заполняет Количество доступных адресов.

`codeStartAddresses` заполняет Массив `UINT_PTR` , каждый из которых является начальным адресом для заданной функции в машинном тексте.

## <a name="remarks"></a>Remarks

Если включена многоуровневая компиляция, функция может иметь более одного тела машинного кода.

## <a name="requirements"></a>Требования

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).

**Заголовок:** CorProf.idl, CorProf.h

**Библиотека:** CorGuids.lib

**Версии .NET:**[!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]

## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerInfo9](icorprofilerinfo9-interface.md)
