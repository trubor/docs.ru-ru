---
description: 'Дополнительные сведения о методе: ICorProfilerCallback8::D Инамикмесоджиткомпилатионфинишед'
title: 'ICorProfilerCallback8: метод:D Инамикмесоджиткомпилатионфинишед'
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: d610024af9959790b37a724c2bdbf4dabc89dd20
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759824"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8: метод:D Инамикмесоджиткомпилатионфинишед

[Поддерживается в платформа .NET Framework 4,7 и более поздних версиях]  
  
Уведомляет профилировщик о завершении JIT-компиляции динамического метода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a>Параметры  

`functionId`  
окне Идентификатор функции в памяти, для которой запускается JIT-компиляция.

`hrStatus` окне Значение, указывающее, была ли JIT-компиляция успешной.

`fIsSafeToBlock` [входные] `true` чтобы указать, что блокировка может привести к тому, что среда выполнения будет ожидать возврата вызывающим потоком из этого обратного вызова. `false` чтобы указать, что блокировка не повлияет на работу среды выполнения.  

## <a name="remarks"></a>Remarks  

Этот обратный вызов активируется каждый раз, когда JIT-компиляция динамического метода завершается. Сюда входят различные суррогаты IL и методы LCG. Его цель — предоставить средствам записи профилировщика достаточно информации для распознавания скомпилированного метода для пользователей.

> [!NOTE]
> `functionId` нельзя использовать значения для разрешения их маркеров метаданных, так как динамические методы не имеют метаданных.

## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Метод DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [Интерфейс ICorProfilerCallback8](icorprofilercallback8-interface.md)
