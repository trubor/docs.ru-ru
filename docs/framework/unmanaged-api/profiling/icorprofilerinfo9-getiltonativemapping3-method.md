---
description: 'Дополнительные сведения о методе: ICorProfilerInfo9:: GetILToNativeMapping3'
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 865545e2352209447b3942da3a62f3733c165b35
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759330"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a>Метод ICorProfilerInfo9:: GetILToNativeMapping3

С учетом начального адреса машинного кода возвращает сведения о сопоставлении IL для этой откомпилированной версии кода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a>Параметры

`pNativeCodeStartAddress` окне Указатель на начало собственной функции.

`cMap` окне Максимальный размер `map` массива.

`pcMap` заполняет Общее число доступных структур COR_DEBUG_IL_TO_NATIVE_MAP.

`map` заполняет Массив структур [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , каждый из которых задает смещения. После возврата метода `GetILToNativeMapping3` параметр `map` будет содержать все или некоторые из структур `COR_DEBUG_IL_TO_NATIVE_MAP`.

## <a name="remarks"></a>Remarks

Если включена многоуровневая компиляция, метод может иметь более одного тела машинного кода. [ICorProfilerInfo9:: жетнативекодестартаддрессес](icorprofilerinfo9-getnativecodestartaddresses-method.md) будет возвращать начальные адреса для всех частей машинного кода.

## <a name="requirements"></a>Требования

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).

**Заголовок:** CorProf.idl, CorProf.h

**Библиотека:** CorGuids.lib

**Платформа .NET Framework версии:**[!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]

## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerInfo9](icorprofilerinfo9-interface.md)
