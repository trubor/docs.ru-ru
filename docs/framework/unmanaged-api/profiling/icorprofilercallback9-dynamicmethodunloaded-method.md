---
description: 'Дополнительные сведения о методе: ICorProfilerCallback9::D Инамикмесодунлоадед'
title: 'ICorProfilerCallback9: метод:D Инамикмесодунлоадед'
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: bc7f95b5101658c93eeb9fcef51e9c0f1bd2f2bd
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760201"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a>ICorProfilerCallback9: метод:D Инамикмесодунлоадед

[Поддерживается в платформа .NET Framework 4.7.2 и более поздних версиях]  
  
Уведомляет профилировщик каждый раз, когда динамический метод уничтожается сборщиком мусора и затем выгружается.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a>Параметры  

`functionId` окне Идентификатор функции в памяти, которая была собрана и выгружена сборщиком мусора.

## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>См. также раздел

- [ICorProfilerCallback8. Динамикмесоджиткомпилатионстартед, метод](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8. Динамикмесоджиткомпилатионфинишед, метод](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [Интерфейс ICorProfilerCallback9](icorprofilercallback9-interface.md)
- [COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS](cor-prf-high-monitor-enumeration.md)
