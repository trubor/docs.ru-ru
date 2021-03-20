---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: JITCompilationFinished'
title: Метод ICorProfilerCallback::JITCompilationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
ms.openlocfilehash: 32a47860ae2e973d32ef12b2bd9002bb1de45ee9
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760331"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a>Метод ICorProfilerCallback::JITCompilationFinished

Уведомляет профилировщик о том, что JIT-компилятор завершил компиляцию функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Параметры

`functionId` окне Идентификатор скомпилированной функции.

`hrStatus` окне Значение, указывающее, успешно ли выполнена компиляция.

`fIsSafeToBlock` окне Значение, указывающее профилировщику, будет ли блокировка влиять на работу среды выполнения. Значение равно `true` , если блокировка может привести к тому, что среда выполнения будет ожидать возврата вызывающим потоком из этого обратного вызова; в противном случае — `false` .

Хотя значение `true` не будет нанести вред среде выполнения, оно может наклонять результаты профилирования.

## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс ICorProfilerCallback](icorprofilercallback-interface.md)
- [Метод JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md)
