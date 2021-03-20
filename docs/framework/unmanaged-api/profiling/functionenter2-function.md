---
description: Дополнительные сведения о функции FunctionEnter2
title: Функция FunctionEnter2
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: f68aeffdd63222cd78d7dc361f09e0b4c3e5af51
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759395"
---
# <a name="functionenter2-function"></a>Функция FunctionEnter2

Уведомляет профилировщик о передаче управления в функцию и предоставляет сведения о кадре стека и аргументах функции. Эта функция заменяет функцию [FunctionEnter](functionenter-function.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>Параметры

`funcId` окне Идентификатор функции, которой передается элемент управления.

`clientData` окне Идентификатор повторно сопоставленной функции, заданный ранее профилировщиком с помощью функции [FunctionIDMapper](functionidmapper-function.md) .
  
`func` окне `COR_PRF_FRAME_INFO` Значение, указывающее на сведения о кадре стека.
  
Профилировщик должен рассматривать это как непрозрачный маркер, который можно передать обратно в подсистему выполнения метода [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
`argumentInfo` окне Указатель на структуру [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) , указывающую расположения в памяти аргументов функции.

Чтобы получить доступ к сведениям об аргументах, `COR_PRF_ENABLE_FUNCTION_ARGS` необходимо установить флаг. Профилировщик может использовать метод [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) для установки флагов событий.

## <a name="remarks"></a>Remarks  

 Значения `func` `argumentInfo` параметров и недопустимы после `FunctionEnter2` возврата функции, так как значения могут измениться или быть уничтожены.  
  
 `FunctionEnter2`Функция является обратным вызовом. ее необходимо реализовать. Реализация должна использовать `__declspec` `naked` атрибут класса хранения ().  
  
 Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.  
  
- Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).  
  
- При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.  
  
 Реализация `FunctionEnter2` не должна блокироваться, так как она приведет к задержке сборки мусора. Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, понятном для сборки мусора. Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionEnter2` вернет.  
  
 Кроме того, `FunctionEnter2` функция не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf. idl  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Функция FunctionLeave2](functionleave2-function.md)
- [Функция FunctionTailcall2](functiontailcall2-function.md)
- [Метод SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Глобальные статические функции профилирования](profiling-global-static-functions.md)
