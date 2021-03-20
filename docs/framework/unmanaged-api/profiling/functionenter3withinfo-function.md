---
description: Дополнительные сведения о функции FunctionEnter3WithInfo
title: Функция FunctionEnter3WithInfo
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
ms.openlocfilehash: 9bcebba724f7ebb405bb3d404f028e3ebca3e0d7
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759316"
---
# <a name="functionenter3withinfo-function"></a>Функция FunctionEnter3WithInfo

Уведомляет профилировщик о передаче управления в функцию и предоставляет маркер, который может быть передан [методу ICorProfilerInfo3:: GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) для получения кадра стека и аргументов функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Параметры

`functionIDOrClientID` окне Идентификатор функции, которой передается элемент управления.

`eltInfo` окне Непрозрачный маркер, представляющий сведения об заданном кадре стека. Этот маркер действителен только во время обратного вызова, к которому он передается.

## <a name="remarks"></a>Remarks  

 `FunctionEnter3WithInfo`Метод обратного вызова уведомляет профилировщик о вызове функций и позволяет профилировщику использовать [метод ICorProfilerInfo3:: GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) для проверки значений аргументов. Чтобы получить доступ к сведениям об аргументах, необходимо `COR_PRF_ENABLE_FUNCTION_ARGS` установить флаг. Профилировщик может использовать [метод ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) для установки флагов событий, а затем использовать [метод ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) для регистрации реализации этой функции.  
  
 `FunctionEnter3WithInfo`Функция является обратным вызовом. ее необходимо реализовать. Реализация должна использовать `__declspec(naked)` атрибут класса хранения.  
  
 Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.  
  
- Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).  
  
- При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.  
  
 Реализация `FunctionEnter3WithInfo` не должна блокироваться, так как она приведет к задержке сборки мусора. Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, удобном для сборки мусора. Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionEnter3WithInfo` вернет.  
  
 `FunctionEnter3WithInfo`Функция не должна вызывать управляемый код или вызывать управляемое выделение памяти каким-либо образом.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf. idl  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [Глобальные статические функции профилирования](profiling-global-static-functions.md)
