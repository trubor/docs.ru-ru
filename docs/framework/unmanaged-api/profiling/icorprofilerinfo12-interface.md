---
description: 'Дополнительные сведения о: интерфейс ICorProfilerInfo12'
title: Интерфейс ICorProfilerInfo12
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: a8b91eba686478c3e825ae15d6ae95bd0ffad944
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805731"
---
# <a name="icorprofilerinfo12-interface"></a>Интерфейс ICorProfilerInfo12

 Подкласс [ICorProfilerInfo11](icorprofilerinfo11-interface.md) , предоставляющий методы для создания евентпипе сеансов, событий и поставщиков.
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод Евентпипестартсессион](icorprofilerinfo12-eventpipestartsession-method.md)|Запускает сеанс Евентпипе профилировщика.|
|[Метод Евентпипеаддпровидертосессион](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)|Добавляет поставщик в существующий сеанс Евентпипе.|
|[Метод Евентпипестопсессион](icorprofilerinfo12-eventpipestopsession-method.md)|Останавливает сеанс Евентпипе.|
|[Метод Евентпипекреатепровидер](icorprofilerinfo12-eventpipecreateprovider-method.md)|Создает поставщик Евентпипе.|  
|[Метод Евентпипежетпровидеринфо](icorprofilerinfo12-eventpipegetproviderinfo-method.md)|Возвращает имя поставщика Евентпипе из его идентификатора.|
|[Метод Евентпипедефинивент](icorprofilerinfo12-eventpipedefineevent-method.md)|Определяет событие для существующего поставщика Евентпипе.|  
|[Метод Евентпипевритивент](icorprofilerinfo12-eventpipewriteevent-method.md)|Записывает событие Евентпипе.|
  
## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).  
**Заголовок:** CorProf.idl, CorProf.h  
**Версии .NET:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]  

## <a name="see-also"></a>См. также раздел

- [Общие сведения об EventPipe](../../../core/diagnostics/eventpipe.md)
- [Хорошо известные Евентпровидерс](../../../core/diagnostics/well-known-event-providers.md)
- [Профилирующие интерфейсы](profiling-interfaces.md)
- [Интерфейс ICorProfilerCallback10](icorprofilercallback10-interface.md)
