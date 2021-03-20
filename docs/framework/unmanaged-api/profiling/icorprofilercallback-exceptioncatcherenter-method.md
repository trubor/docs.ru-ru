---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Ексцептионкатчерентер'
title: Метод ICorProfilerCallback::ExceptionCatcherEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
ms.openlocfilehash: f9ea2b44e7a783f9b21f4aa385585dfebc48b1d4
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760526"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a>Метод ICorProfilerCallback::ExceptionCatcherEnter

Уведомляет профилировщик о том, что управление передается соответствующему `catch` блоку.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a>Параметры

`functionId` окне Идентификатор функции, содержащей `catch` блок.
  
`objectId` окне Идентификатор обрабатываемого исключения.

## <a name="remarks"></a>Remarks  

 `ExceptionCatcherEnter`Метод вызывается только в том случае, если точка перехвата находится в коде, скомпилированном с JIT-компилятором. Исключение, перехваченное в неуправляемом коде или во внутреннем коде среды выполнения, не будет вызывать это уведомление. `objectId`Значение передается снова, так как сборка мусора могла переместить объект с момента получения `ExceptionThrown` уведомления.  
  
 Профилировщик не должен блокировать реализацию этого метода, так как стек может не находиться в состоянии, допускающем сборку мусора, поэтому невозможно включить вытесненную сборку мусора. Если профилировщик блокируется здесь и выполняется сборка мусора, среда выполнения блокируется до тех пор, пока этот обратный вызов не вернет значение.  
  
 Реализация этого метода профилировщиком не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
- [Метод ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md)
