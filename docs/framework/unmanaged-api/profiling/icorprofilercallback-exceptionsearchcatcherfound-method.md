---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ексцептионсеарчкатчерфаунд'
title: Метод ICorProfilerCallback::ExceptionSearchCatcherFound
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
ms.openlocfilehash: 080e9be61e4f10cbfb60696a5089aca0c3f2843f
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759993"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a>Метод ICorProfilerCallback::ExceptionSearchCatcherFound

Уведомляет профилировщик о том, что на фазе поиска исключений обнаружен обработчик для созданного исключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a>Параметры

`functionId` окне Идентификатор функции, которая содержит обработчик исключений.

## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
