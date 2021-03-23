---
description: 'Дополнительные сведения о: интерфейс ICorProfilerCallback10'
title: Интерфейс ICorProfilerCallback10
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: d9091dc81307e2dcb83e74154a8217dffaa1e7a2
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805653"
---
# <a name="icorprofilercallback10-interface"></a>Интерфейс ICorProfilerCallback10

 Подкласс [ICorProfilerCallback9](icorprofilercallback9-interface.md) , предоставляющий методы обратного вызова для уведомления профилировщика о том, что события евентпипе были доставлены в текущий активный сеанс профилировщика.
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод Евентпипивентделиверед](icorprofilercallback10-eventpipeeventdelivered-method.md)|Уведомляет профилировщик о том, что событие Евентпипе было доставлено в сеанс, Открытый профилировщиком.|
|[Метод Евентпипепровидеркреатед](icorprofilercallback10-eventpipeprovidercreated-method.md)|Уведомляет профилировщик о том, что создан поставщик Евентпипе, что позволяет профилировщику добавить этот поставщик в сеанс.|  
  
## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).  
**Заголовок:** CorProf.idl, CorProf.h  
**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]  

## <a name="see-also"></a>См. также раздел

- [Общие сведения об EventPipe](../../../core/diagnostics/eventpipe.md)
- [Хорошо известные Евентпровидерс](../../../core/diagnostics/well-known-event-providers.md)
- [Профилирующие интерфейсы](profiling-interfaces.md)
- [Интерфейс ICorProfilerInfo12](ICorProfilerInfo12-interface.md)
- [ICorProfilerInfo12. Евентпипестартсессион, метод](ICorProfilerInfo12-eventpipestartsession-method.md)
- [ICorProfilerInfo12. Евентпипестопсессион, метод](ICorProfilerInfo12-eventpipestopsession-method.md)
