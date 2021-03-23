---
description: 'Дополнительные сведения: перечисление COR_PRF_EVENTPIPE_PROVIDER_CONFIG'
title: Перечисление COR_PRF_EVENTPIPE_PROVIDER_CONFIG
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PROVIDER_CONFIG
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 2a7a5e720e9468b44e6504d24a3b9ad836e13693
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805848"
---
# <a name="cor_prf_eventpipe_provider_config-enumeration"></a>Перечисление COR_PRF_EVENTPIPE_PROVIDER_CONFIG

Описание полей, необходимых для настройки поставщика Евентпипе.
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct
{
    const WCHAR* providerName;
    UINT64       keywords;
    UINT32       loggingLevel;
    const WCHAR* filterData;
} COR_PRF_EVENTPIPE_PROVIDER_CONFIG;
```  
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|`providerName`|Имя поставщика, который необходимо включить.|  
|`keywords`|Ключевые слова, которые должны быть включены для поставщика.|  
|`loggingLevel`|Уровень, который должен быть включен для поставщика.|  
|`filterData`|Строка расширенных символов, содержащая FilterData, используемый при включении поставщика.|  
  
## <a name="remarks"></a>Remarks  

 `COR_PRF_EVENTPIPE_PROVIDER_CONFIG`Структура используется методом [ICorProfilerInfo12:: евентпипеаддпровидертосессион](icorprofilerinfo12-eventpipeaddprovidertosession-method.md) для указания конфигурации поставщика, добавляемого в сеанс.
  
## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).
**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>См. также раздел

- [Перечисления профилирования](profiling-enumerations.md)
- [ICorProfilerInfo12:: Евентпипеаддпровидертосессион](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)
