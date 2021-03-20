---
description: Дополнительные сведения о функции FunctionTailcall3WithInfo
title: Функция FunctionTailcall3WithInfo
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
ms.openlocfilehash: d84cac19acb8a1d696030fe372d29c655c5f97a6
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760799"
---
# <a name="functiontailcall3withinfo-function"></a>Функция FunctionTailcall3WithInfo

Уведомляет профилировщик о том, что выполняемая в данный момент функция собирается выполнить вызов другой функции с префиксом tail, и предоставляет маркер, который может быть передан [методу ICorProfilerInfo3:: GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) для получения кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Параметры  

`functionIDOrClientID` окне Идентификатор выполняемой в данный момент функции, которая собирается выполнить вызов с префиксом tail.

`eltInfo` окне Непрозрачный маркер, представляющий сведения об заданном кадре стека. Этот маркер действителен только во время обратного вызова, к которому он передается.

## <a name="remarks"></a>Remarks  

 `FunctionTailcall3WithInfo`Метод обратного вызова уведомляет профилировщик о вызове функций и позволяет профилировщику использовать [метод ICorProfilerInfo3:: GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) для проверки кадра стека. Чтобы получить доступ к сведениям о кадрах стека, необходимо `COR_PRF_ENABLE_FRAME_INFO` установить флаг. Профилировщик может использовать [метод ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) для установки флагов событий, а затем использовать [метод ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) для регистрации реализации этой функции.  
  
 `FunctionTailcall3WithInfo`Функция является обратным вызовом. ее необходимо реализовать. Реализация должна использовать `__declspec(naked)` атрибут класса хранения.  
  
 Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.  
  
- Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).  
  
- При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.  
  
 Реализация `FunctionTailcall3WithInfo` не должна блокироваться, так как она приведет к задержке сборки мусора. Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, удобном для сборки мусора. Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionTailcall3WithInfo` вернет.  
  
 Кроме того, функция FunctionTailcall3WithInfo не должна вызывать управляемый код или каким-либо образом вызывать управляемое выделение памяти.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf. idl  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functiontailcall3-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [SetFunctionIDMapper2](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Глобальные статические функции профилирования](profiling-global-static-functions.md)
