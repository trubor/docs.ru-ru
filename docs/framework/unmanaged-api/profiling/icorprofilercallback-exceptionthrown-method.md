---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: ExceptionThrown'
title: Метод ICorProfilerCallback::ExceptionThrown
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
ms.openlocfilehash: aed3d6c4c3c45b546fa8af1db918a6f68eda9bde
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760409"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a>Метод ICorProfilerCallback::ExceptionThrown

Уведомляет профилировщик о том, что было создано исключение.  
  
> [!NOTE]
> Эта функция вызывается, только если исключение достигает управляемого кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a>Параметры

`thrownObjectId` окне Идентификатор объекта, который вызвал исключение.
  
## <a name="remarks"></a>Remarks  

 Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора. Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.  
  
 Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
