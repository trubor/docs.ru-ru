---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: AppDomainShutdownFinished'
title: Метод ICorProfilerCallback::AppDomainShutdownFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
ms.openlocfilehash: 8cd45f73741bd26cb54fa85d7d6a186ebaeab5d8
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760695"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a>Метод ICorProfilerCallback::AppDomainShutdownFinished

Уведомляет профилировщик о том, что домен приложения был выгружен из процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Параметры

`appDomainId` окне Определяет домен, в котором хранятся сборки приложения.

`hrStatus` окне Значение HRESULT, указывающее, успешно ли выгружен домен приложения.

## <a name="remarks"></a>Remarks  

 Значение недопустимо `appDomainId` для информационного запроса после возврата метода [ICorProfilerCallback:: AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) .  
  
 Некоторые части выгрузки домена приложения могут продолжаться после `AppDomainCreationFinished` обратного вызова. Ошибка HRESULT в `hrStatus` указывает на сбой. Однако значение HRESULT в случае успеха в `hrStatus` указывает, что первая часть выгрузки домена приложения успешно выполнена.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
