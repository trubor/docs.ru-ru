---
description: Дополнительные сведения о функции FunctionLeave3WithInfo
title: Функция FunctionLeave3WithInfo
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
ms.openlocfilehash: 617ca023f58a180c198751fea9752fe737249331
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760084"
---
# <a name="functionleave3withinfo-function"></a>Функция FunctionLeave3WithInfo

Уведомляет профилировщик о том, что управление возвращается из функции, и предоставляет маркер, который может быть передан [методу ICorProfilerInfo3:: GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) для получения кадра стека и возвращаемого значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Параметры

`functionIDOrClientID` окне Идентификатор функции, из которой возвращается элемент управления.

`eltInfo` окне Непрозрачный маркер, представляющий сведения об заданном кадре стека. Этот маркер действителен только во время обратного вызова, к которому он передается.

## <a name="remarks"></a>Remarks  

 `FunctionLeave3WithInfo`Метод обратного вызова уведомляет профилировщик о вызове функций и позволяет профилировщику использовать [метод ICorProfilerInfo3:: GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) для проверки возвращаемого значения. Чтобы получить доступ к сведениям о возвращаемом значении, необходимо `COR_PRF_ENABLE_FUNCTION_RETVAL` установить флаг. Профилировщик может использовать [метод ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) для установки флагов событий, а затем использовать [метод ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) для регистрации реализации этой функции.  
  
 `FunctionLeave3WithInfo`Функция является обратным вызовом. ее необходимо реализовать. Реализация должна использовать `__declspec(naked)` атрибут класса хранения.  
  
 Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.  
  
- Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).  
  
- При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.  
  
 Реализация `FunctionLeave3WithInfo` не должна блокироваться, так как она приведет к задержке сборки мусора. Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, удобном для сборки мусора. Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionLeave3WithInfo` вернет.  
  
 `FunctionLeave3WithInfo`Функция не должна вызывать управляемый код или вызывать управляемое выделение памяти каким-либо образом.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf. idl  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [SetFunctionIDMapper2](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Глобальные статические функции профилирования](profiling-global-static-functions.md)
