---
description: 'Дополнительные сведения: перечисление COR_PRF_EVENTPIPE_LEVEL'
title: Перечисление COR_PRF_EVENTPIPE_LEVEL
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_LEVEL
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: da8211da1a9bb6262b078c5e56bee1d0c1f9342e
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805822"
---
# <a name="cor_prf_eventpipe_level-enumeration"></a>Перечисление COR_PRF_EVENTPIPE_LEVEL

Описывает уровень события Евентпипе.
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum
{
    COR_PRF_EVENTPIPE_LOGALWAYS = 0,
    COR_PRF_EVENTPIPE_CRITICAL = 1,
    COR_PRF_EVENTPIPE_ERROR = 2,
    COR_PRF_EVENTPIPE_WARNING = 3,
    COR_PRF_EVENTPIPE_INFORMATIONAL = 4,
    COR_PRF_EVENTPIPE_VERBOSE = 5
} COR_PRF_EVENTPIPE_LEVEL;
```  
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|`COR_PRF_EVENTPIPE_LOGALWAYS`|Событие всегда заносится в журнал.|
|`COR_PRF_EVENTPIPE_CRITICAL`|Событие представляет критическое сообщение.|
|`COR_PRF_EVENTPIPE_ERROR`|Событие представляет сообщение об ошибке.|
|`COR_PRF_EVENTPIPE_WARNING`|Событие представляет предупреждающее сообщение.|
|`COR_PRF_EVENTPIPE_INFORMATIONAL`|Событие представляет информационное сообщение.|
|`COR_PRF_EVENTPIPE_VERBOSE`|Событие представляет подробное сообщение.|
  
## <a name="remarks"></a>Remarks  

 `COR_PRF_EVENTPIPE_LEVEL`Перечисление используется методом [ICorProfilerInfo12:: евентпипедефинивент](icorprofilerinfo12-eventpipedefineevent-method.md) для указания уровня определяемого события.
  
## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).
**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>См. также раздел

- [Перечисления профилирования](profiling-enumerations.md)
- [ICorProfilerInfo12:: Евентпипедефинивент](icorprofilerinfo12-eventpipedefineevent-method.md)
