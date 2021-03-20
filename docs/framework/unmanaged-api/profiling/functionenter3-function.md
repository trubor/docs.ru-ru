---
description: Дополнительные сведения о функции FunctionEnter3
title: Функция FunctionEnter3
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
ms.openlocfilehash: 4726a080157b99c7538fe8a66cf8b26403564ad2
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759303"
---
# <a name="functionenter3-function"></a>Функция FunctionEnter3

Уведомляет профилировщик о передаче управления в функцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a>Параметры

`functionOrRemappedID` окне Идентификатор функции, которой передается элемент управления.

## <a name="remarks"></a>Remarks  

 `FunctionEnter3`Функция обратного вызова уведомляет профилировщик о вызове функций, но не поддерживает проверку аргументов. Чтобы зарегистрировать реализацию этой функции, используйте [метод ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) .  
  
 `FunctionEnter3`Функция является обратным вызовом. ее необходимо реализовать. Реализация должна использовать `__declspec(naked)` атрибут класса хранения.  
  
 Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.  
  
- Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).  
  
- При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf. idl  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [SetFunctionIDMapper2](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Глобальные статические функции профилирования](profiling-global-static-functions.md)
