---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: AppDomainCreationStarted'
title: Метод ICorProfilerCallback::AppDomainCreationStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
ms.openlocfilehash: b783bb652bed3b600c1e4524810620bab68f5f7a
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760708"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a>Метод ICorProfilerCallback::AppDomainCreationStarted

Уведомляет профилировщик о создании домена приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a>Параметры

`appDomainId` окне Определяет создаваемый домен.
  
## <a name="remarks"></a>Remarks  

 Идентификатор не является допустимым для запроса информации до вызова метода [ICorProfilerCallback:: аппдомаинкреатионфинишед](icorprofilercallback-appdomaincreationfinished-method.md) .  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
