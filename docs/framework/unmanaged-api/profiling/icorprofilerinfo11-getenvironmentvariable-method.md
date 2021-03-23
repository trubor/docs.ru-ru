---
description: 'Дополнительные сведения о методе: ICorProfilerInfo11:: GetEnvironmentVariable'
title: 'Метод ICorProfilerInfo11:: GetEnvironmentVariable'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo11.GetEnvironmentVariable
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 635c5fb67b880c39f15fbc194a51a706d9ef7fe4
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805835"
---
# <a name="icorprofilerinfo11getenvironmentvariable-method"></a>Метод ICorProfilerInfo11:: GetEnvironmentVariable

Возвращает переменную среды из процесса. На платформах, отличных от Windows, среда выполнения сохраняет внутренний кэш переменных среды для обеспечения безопасности потоков. Это означает, что вызов `getenv` не будет считывать новые или обновленные переменные среды, установленные управляемым кодом, который выполняется в процессе после запуска.
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
    HRESULT GetEnvironmentVariable(
                [in, string] const WCHAR *szName,
                [in]         ULONG cchValue,
                [out]        ULONG *pcchValue,
                [out, annotation("_Out_writes_to_(cchValue, *pcchValue)")]
                             WCHAR szValue[]);
```  
  
## <a name="parameters"></a>Параметры

`szName` окне Указатель на строку расширенных символов, заканчивающуюся нулем и содержащую имя переменной среды для получения.

`cchValue` окне Длина в символах `szValue` .

`pcchValue` заполняет Указатель на общую длину символов `szValue` .

`szValue` заполняет Вызывающий объект предоставил широкий буфер символов. Когда функция возвращает буфер, будет содержать значение переменной среды.

## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).  
**Заголовок:** CorProf.idl, CorProf.h  
**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Профилирующие интерфейсы](profiling-interfaces.md)
- [Интерфейс ICorProfilerInfo11](icorprofilerinfo11-interface.md)
