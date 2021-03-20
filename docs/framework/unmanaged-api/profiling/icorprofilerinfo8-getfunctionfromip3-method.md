---
description: 'Дополнительные сведения о методе: ICorProfilerInfo8:: GetFunctionFromIP3'
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 1b753350f45f722d60099b17cfdd48bfd06e411a
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759108"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a>Метод ICorProfilerInfo8:: GetFunctionFromIP3

Сопоставляет указатель инструкции управляемого кода с FunctionID. Этот метод работает как с динамическими, так и с нединамическими методами.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a>Параметры

`ip` окне Указатель инструкции в управляемом коде.

`pFunctionId` заполняет Идентификатор функции.

`pReJitId` заполняет Удостоверение JIT-повторно скомпилированной версии функции.

## <a name="remarks"></a>Remarks

Этот метод работает как с динамическими, так и с нединамическими методами. Это надмножество [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), который работает только для функций с метаданными.

## <a name="requirements"></a>Требования

**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).

**Заголовок:** CorProf.idl, CorProf.h

**Библиотека:** CorGuids.lib

**Платформа .NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerInfo8](icorprofilerinfo8-interface.md)
