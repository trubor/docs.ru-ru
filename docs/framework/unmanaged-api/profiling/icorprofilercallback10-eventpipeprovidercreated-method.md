---
description: 'Дополнительные сведения о методе: ICorProfilerCallback10:: Евентпипепровидеркреатед'
title: 'Метод ICorProfilerCallback10:: Евентпипепровидеркреатед'
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10.EventPipeProviderCreated
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 6ce96bf301f1c559923df64edd9dd214c28db918
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231314"
---
# <a name="icorprofilercallback10eventpipeprovidercreated-method"></a>Метод ICorProfilerCallback10:: Евентпипепровидеркреатед

Уведомляет профилировщик каждый раз, когда создается поставщик Евентпипе.
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
    HRESULT EventPipeProviderCreated([in] EVENTPIPE_PROVIDER provider);
```  
  
## <a name="parameters"></a>Параметры

`provider` окне Созданный поставщик.

## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).  
**Заголовок:** CorProf.idl, CorProf.h  
**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Профилирующие интерфейсы](profiling-interfaces.md)
- [Интерфейс ICorProfilerCallback10](icorprofilercallback10-interface.md)
- [Интерфейс ICorProfilerInfo12](icorprofilerinfo12-interface.md)
- [ICorProfilerInfo12. Евентпипеаддпровидертосессион, метод](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)
