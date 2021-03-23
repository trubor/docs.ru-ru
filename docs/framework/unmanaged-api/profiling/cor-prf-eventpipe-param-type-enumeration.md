---
description: 'Дополнительные сведения: перечисление COR_PRF_EVENTPIPE_PARAM_TYPE'
title: Перечисление COR_PRF_EVENTPIPE_PARAM_TYPE
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PARAM_TYPE
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 29aed86e4a991598d038a60ae086e77e25df24bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805783"
---
# <a name="cor_prf_eventpipe_param_type-enumeration"></a>Перечисление COR_PRF_EVENTPIPE_PARAM_TYPE

Описывает тип параметра для события Евентпипе.
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum
{
    COR_PRF_EVENTPIPE_OBJECT = 1,
    COR_PRF_EVENTPIPE_BOOLEAN = 3,
    COR_PRF_EVENTPIPE_CHAR = 4,
    COR_PRF_EVENTPIPE_SBYTE = 5,
    COR_PRF_EVENTPIPE_BYTE = 6,
    COR_PRF_EVENTPIPE_INT16 = 7,
    COR_PRF_EVENTPIPE_UINT16 = 8,
    COR_PRF_EVENTPIPE_INT32 = 9,
    COR_PRF_EVENTPIPE_UINT32 = 10,
    COR_PRF_EVENTPIPE_INT64 = 11,
    COR_PRF_EVENTPIPE_UINT64 = 12,
    COR_PRF_EVENTPIPE_SINGLE = 13,
    COR_PRF_EVENTPIPE_DOUBLE = 14,
    COR_PRF_EVENTPIPE_DECIMAL = 15,
    COR_PRF_EVENTPIPE_DATETIME = 16,
    COR_PRF_EVENTPIPE_GUID = 17,
    COR_PRF_EVENTPIPE_STRING = 18,
    COR_PRF_EVENTPIPE_ARRAY = 19,
} COR_PRF_EVENTPIPE_PARAM_TYPE;
```  
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|`COR_PRF_EVENTPIPE_OBJECT`|Тип параметра является самоописывающим объектом.|
|`COR_PRF_EVENTPIPE_BOOLEAN`|Тип параметра — логическое значение.|
|`COR_PRF_EVENTPIPE_CHAR`|Тип параметра является 16-разрядным расширенным символом.|
|`COR_PRF_EVENTPIPE_SBYTE`|Тип параметра — 8-разрядное целое число со знаком.|
|`COR_PRF_EVENTPIPE_BYTE`|Тип параметра — 8-разрядное целое число без знака.|
|`COR_PRF_EVENTPIPE_INT16`|Тип параметра представляет собой 16-разрядное целое число со знаком.|
|`COR_PRF_EVENTPIPE_UINT16`|Тип параметра представляет собой 16-разрядное целое число без знака.|
|`COR_PRF_EVENTPIPE_INT32`|Тип параметра — это 32-разрядное целое число со знаком.|
|`COR_PRF_EVENTPIPE_UINT32`|Тип параметра — это 32-разрядное целое число без знака.|
|`COR_PRF_EVENTPIPE_INT64`|Тип параметра — это 64-разрядное целое число со знаком.|
|`COR_PRF_EVENTPIPE_UINT64`|Тип параметра — это 64-разрядное целое число без знака.|
|`COR_PRF_EVENTPIPE_SINGLE`|Тип параметра — 32-разрядное число с плавающей запятой.|
|`COR_PRF_EVENTPIPE_DOUBLE`|Тип параметра — 64-разрядное число с плавающей запятой.|
|`COR_PRF_EVENTPIPE_DECIMAL`|Тип параметра — 128-разрядное число с плавающей запятой.|
|`COR_PRF_EVENTPIPE_DATETIME`|Тип параметра является сериализованной структурой времени.|
|`COR_PRF_EVENTPIPE_GUID`|Тип параметра — GUID.|
|`COR_PRF_EVENTPIPE_STRING`|Тип параметра — это 16-разрядная строка расширенных символов, заканчивающаяся нулем.|
|`COR_PRF_EVENTPIPE_ARRAY`|Тип параметра является массивом одного из перечисленных выше типов.|
  
## <a name="remarks"></a>Remarks  

 `COR_PRF_EVENTPIPE_PARAM_TYPE`Перечисление используется структурой [COR_PRF_EVENTPIPE_PARAM_DESC](cor-prf-eventpipe-param-desc-structure.md) для указания типа параметра.
  
## <a name="requirements"></a>Требования  

**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).
**Заголовок:** **Версии .NET** CorProf. idl, CorProf. h: [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>См. также раздел

- [Перечисления профилирования](profiling-enumerations.md)
