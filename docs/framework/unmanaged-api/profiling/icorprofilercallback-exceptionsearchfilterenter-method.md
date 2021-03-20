---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ексцептионсеарчфилтерентер'
title: Метод ICorProfilerCallback::ExceptionSearchFilterEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type:
- apiref
ms.openlocfilehash: 29a9eed75e5d8a954dfb23dedf3d2080e0d139d2
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760224"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a>Метод ICorProfilerCallback::ExceptionSearchFilterEnter

Уведомляет профилировщик о том, что фаза поиска обработки исключений начала выполнять пользовательский фильтр исключений.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a>Параметры

`functionId` окне Идентификатор функции, которая содержит фильтр.

## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
- [Метод ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md)
