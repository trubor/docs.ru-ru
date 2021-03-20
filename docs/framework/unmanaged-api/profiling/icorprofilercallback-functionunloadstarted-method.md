---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: FunctionUnloadStarted'
title: Метод ICorProfilerCallback::FunctionUnloadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: ce3cf406b8d2f91613bce878db8a4f9e0838c052
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760435"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a>Метод ICorProfilerCallback::FunctionUnloadStarted

Уведомляет профилировщик о запуске среды выполнения для выгрузки функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a>Параметры

`functionId` окне Идентификатор выгрузки функции.

## <a name="remarks"></a>Remarks  

 Значение `functionId` параметра больше не является допустимым после возврата этим методом вызывающему объекту.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
