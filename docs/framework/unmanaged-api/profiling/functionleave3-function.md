---
description: Дополнительные сведения о функции FunctionLeave3
title: Функция FunctionLeave3
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
ms.openlocfilehash: 0409a9969fddbbbcb8fcb5d870acccf1ae3a809b
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760110"
---
# <a name="functionleave3-function"></a>Функция FunctionLeave3

Уведомляет профилировщик о том, что управление возвращается из функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a>Параметры  

`functionOrRemappedID` окне Идентификатор функции, из которой возвращается элемент управления.
  
## <a name="remarks"></a>Remarks  

 `FunctionLeave3`Функция обратного вызова уведомляет профилировщик о вызове функций, но не поддерживает проверку возвращаемого значения. Чтобы зарегистрировать реализацию этой функции, используйте [метод ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) .  
  
 `FunctionLeave3`Функция является обратным вызовом. ее необходимо реализовать. Реализация должна использовать `__declspec(naked)` атрибут класса хранения.  
  
 Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.  
  
- Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).  
  
- При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.  
  
 Реализация `FunctionLeave3` не должна блокироваться, так как она приведет к задержке сборки мусора. Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, удобном для сборки мусора. Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionLeave3` вернет.  
  
 `FunctionLeave3`Функция не должна вызывать управляемый код или вызывать управляемое выделение памяти каким-либо образом.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf. idl  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [FunctionEnter3](functionenter3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functiontailcall3-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [SetFunctionIDMapper2](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Глобальные статические функции профилирования](profiling-global-static-functions.md)
