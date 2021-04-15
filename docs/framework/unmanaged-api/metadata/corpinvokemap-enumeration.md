---
description: Дополнительные сведения о перечислении CorPinvokeMap
title: Перечисление CorPinvokeMap
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: e054b7e9c5a8baf0e59fc3c9ce9bc57a4d7ea4d0
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494588"
---
# <a name="corpinvokemap-enumeration"></a>Перечисление CorPinvokeMap

Задает параметры для вызова PInvoke.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|`pmNoMangle`|Используйте каждое имя элемента, как указано.|  
|`pmCharSetMask`|Зарезервировано.|  
|`pmCharSetNotSpec`|Зарезервировано.|  
|`pmCharSetAnsi`|Маршалирует строки в виде строк многобайтовых символов.|  
|`pmCharSetUnicode`|Маршалирует строки в виде 2-байтных символов Юникода.|  
|`pmCharSetAuto`|Выполняет автоматический маршалинг строк способом, соответствующим целевой операционной системе. По умолчанию используется Юникод в Windows.|  
|`pmBestFitUseAssem`|Зарезервировано.|  
|`pmBestFitEnabled`|Выполните наилучшее сопоставление символов Юникода, не имея точного соответствия в кодировке ANSI.|  
|`pmBestFitDisabled`|Не выполняйте наилучшее соответствие символов Юникода. В этом случае все несопоставимые символы будут заменены символом "?".|  
|`pmBestFitMask`|Зарезервировано.|  
|`pmThrowOnUnmappableCharUseAssem`|Зарезервировано.|  
|`pmThrowOnUnmappableCharEnabled`|Создавать исключение, когда модуль маршалинга взаимодействия встречает несопоставимый символ.|  
|`pmThrowOnUnmappableCharDisabled`|Не вызывайте исключение, если модуль маршалинга взаимодействия встречает несопоставимый символ.|  
|`pmThrowOnUnmappableCharMask`|Зарезервировано|  
|`pmSupportsLastError`|Разрешить вызываемому `SetLastError` методу вызывать функцию Win32 перед возвратом из метода с атрибутом.|  
|`pmCallConvMask`|Зарезервировано|  
|`pmCallConvWinapi`|Используйте соглашение о вызовах платформы по умолчанию. Например, в Windows значение по умолчанию — `StdCall` и на Windows CE .NET — `Cdecl` .|  
|`pmCallConvCdecl`|Используйте `Cdecl` соглашение о вызовах. В этом случае вызывающий объект очищает стек. Это позволяет вызывать функции с `varargs` (то есть функциями, принимающими переменное количество параметров).|  
|`pmCallConvStdcall`|Используйте `StdCall` соглашение о вызовах. В этом случае вызываемый объект очищает стек. Это соглашение, используемое по умолчанию для вызова неуправляемых функций с вызовом неуправляемого кода.|  
|`pmCallConvThiscall`|Используйте `ThisCall` соглашение о вызовах. В этом случае первый параметр является `this` указателем и хранится в регистре ECX. Другие параметры помещаются в стек. `ThisCall`Соглашение о вызовах используется для вызова методов для классов, экспортируемых из неуправляемой библиотеки DLL.|  
|`pmCallConvFastcall`|Зарезервировано.|  
|`pmMaxValue`|Зарезервировано.|  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** Корхдр. h  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Перечисления метаданных](metadata-enumerations.md)
