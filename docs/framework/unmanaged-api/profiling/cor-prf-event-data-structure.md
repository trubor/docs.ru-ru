---
description: 'Дополнительные сведения: перечисление COR_PRF_EVENT_DATA'
title: Перечисление COR_PRF_EVENT_DATA
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENT_DATA
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 477f36476deb9c0d74e263703e36b134c91b5327
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805573"
---
# <a name="cor_prf_event_data-enumeration"></a>Перечисление COR_PRF_EVENT_DATA

Описывает данные события для записываемого события Евентпипе.
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct
{
    UINT64 ptr;
    UINT32 size;
    UINT32 reserved;
} COR_PRF_EVENT_DATA;
```  
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|`ptr`|Указатель на данные.|  
|`size`|Размер данных, на которые указывает `ptr` .|  
|`reserved`|Зарезервированное поле для конкретной реализации.|  
  
## <a name="remarks"></a>Remarks  

 `COR_PRF_EVENT_DATA`Структура используется методом [ICorProfilerInfo12:: евентпипевритивент](icorprofilerinfo12-eventpipewriteevent-method.md) , чтобы провидате полезные данные для записываемого события.
  
## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).
**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>См. также раздел

- [Перечисления профилирования](profiling-enumerations.md)
- [ICorProfilerInfo12:: Евентпипевритивент](icorprofilerinfo12-eventpipewriteevent-method.md)
