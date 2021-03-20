---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Класслоадфинишед'
title: Метод ICorProfilerCallback::ClassLoadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: 52fd26c1efaf9b85caeb5af7184ae70e1d29b9ff
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760225"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a>Метод ICorProfilerCallback::ClassLoadFinished

Уведомляет профилировщик о том, что загрузка класса завершена.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a>Параметры

`classId` окне Идентифицирует загруженный класс.

`hrStatus` окне Значение HRESULT, указывающее, успешно ли загружен класс.

## <a name="remarks"></a>Remarks  

 Значение недопустимо `classId` для информационного запроса до `ClassLoadFinished` вызова метода.  
  
 Некоторые части загрузки класса могут продолжаться после `ClassLoadFinished` обратного вызова. Ошибка HRESULT в `hrStatus` указывает на сбой. Однако значение HRESULT в случае успеха в `hrStatus` указывает только на то, что первая часть загрузки класса завершилась успешно.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
- [Метод ClassLoadStarted](icorprofilercallback-classloadstarted-method.md)
