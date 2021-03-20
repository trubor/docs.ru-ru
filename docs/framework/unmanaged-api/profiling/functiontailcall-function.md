---
description: Дополнительные сведения о функции Функтионтаилкалл
title: Функция FunctionTailcall
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
ms.openlocfilehash: aeb6e7dcbf52fc57ebb7b6dca22331c27cadc186
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760032"
---
# <a name="functiontailcall-function"></a>Функция FunctionTailcall

Уведомляет профилировщик о том, что выполняемая в данный момент функция собирается выполнить вызов другой функции с префиксом tail.  
  
> [!NOTE]
> `FunctionTailcall`Функция является устаревшей в платформа .NET Framework версии 2,0. Он будет продолжать работать, но будет приводить к снижению производительности. Вместо этого используйте функцию [FunctionTailcall2](functiontailcall2-function.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Параметры

`funcID` окне Идентификатор выполняемой в данный момент функции, которая собирается выполнить вызов с префиксом tail.

## <a name="remarks"></a>Remarks  

 Целевая функция вызова с префиксом tail будет использовать текущий кадр стека и будет возвращаться непосредственно вызывающему объекту функции, которая выполнила вызов с префиксом tail. Это означает, что обратный вызов [FunctionLeave](functionleave-function.md) не будет выдаваться для функции, которая является целевым объектом для вызова с префиксом tail.  
  
 `FunctionTailcall`Функция является обратным вызовом. ее необходимо реализовать. Реализация должна использовать `__declspec` `naked` атрибут класса хранения ().  
  
 Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.  
  
- Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).  
  
- При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.  
  
 Реализация `FunctionTailcall` не должна блокироваться, так как она приведет к задержке сборки мусора. Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, понятном для сборки мусора. Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionTailcall` вернет.  
  
 Кроме того, `FunctionTailcall` функция не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf. idl  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:** 1,1, 1,0  
  
## <a name="see-also"></a>См. также раздел

- [Функция FunctionEnter2](functionenter2-function.md)
- [Функция FunctionLeave2](functionleave2-function.md)
- [Метод SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Глобальные статические функции профилирования](profiling-global-static-functions.md)
