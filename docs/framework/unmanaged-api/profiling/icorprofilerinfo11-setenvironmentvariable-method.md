---
description: 'Дополнительные сведения о методе: ICorProfilerInfo11:: SetEnvironmentVariable'
title: 'Метод ICorProfilerInfo11:: SetEnvironmentVariable'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo11.SetEnvironmentVariable
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 77dc3fc992dec037881573323822dc11481a56be
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805612"
---
# <a name="icorprofilerinfo11setenvironmentvariable-method"></a>Метод ICorProfilerInfo11:: SetEnvironmentVariable

Задает переменную среды в процессе. На платформах, отличных от Windows, среда выполнения сохраняет внутренний кэш переменных среды для обеспечения безопасности потоков. Это означает, что если профилировщик вызывает `setenv` новую переменную среды, управляемый код, выполняющийся в процессе, не будет выбран.
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
    HRESULT SetEnvironmentVariable(
                [in, string] const WCHAR *szName,
                [in, string] const WCHAR *szValue);
```  
  
## <a name="parameters"></a>Параметры

`szName` окне Указатель на строку расширенных символов, заканчивающуюся нулем и содержащую имя заданной переменной среды.

`szValue` окне Указатель на строку расширенных символов, заканчивающуюся нулем и содержащую значение заданной переменной среды.

## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).  
**Заголовок:** CorProf.idl, CorProf.h  
**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Профилирующие интерфейсы](profiling-interfaces.md)
- [Интерфейс ICorProfilerInfo11](icorprofilerinfo11-interface.md)
