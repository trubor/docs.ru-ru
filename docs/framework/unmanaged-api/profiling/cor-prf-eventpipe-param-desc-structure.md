---
description: 'Дополнительные сведения: перечисление COR_PRF_EVENTPIPE_PARAM_DESC'
title: Перечисление COR_PRF_EVENTPIPE_PARAM_DESC
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PARAM_DESC
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: b23897580092cc9f3f887a21e86f7111fecd9f19
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805796"
---
# <a name="cor_prf_eventpipe_param_desc-enumeration"></a>Перечисление COR_PRF_EVENTPIPE_PARAM_DESC

Описывает имя и тип параметра для события Евентпипе.
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct
{
    UINT32       type;
    UINT32       elementType;
    const WCHAR *name;
} COR_PRF_EVENTPIPE_PARAM_DESC;
```  
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|`type`|Тип параметра.|  
|`elementType`|Тип элемента, если этот параметр имеет тип массива.|  
|`name`|Строка расширенных символов, содержащая имя параметра.|  
  
## <a name="remarks"></a>Remarks  

 `COR_PRF_EVENTPIPE_PARAM_DESC`Структура используется методом [ICorProfilerInfo12:: евентпипедефинивент](icorprofilerinfo12-eventpipedefineevent-method.md) для определения типов параметров определяемого события.
  
## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).
**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>См. также раздел

- [Перечисления профилирования](profiling-enumerations.md)
- [ICorProfilerInfo12:: Евентпипедефинивент](icorprofilerinfo12-eventpipedefineevent-method.md)
