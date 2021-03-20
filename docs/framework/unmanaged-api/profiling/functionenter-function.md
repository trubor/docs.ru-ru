---
description: Дополнительные сведения о функции FunctionEnter
title: Функция FunctionEnter
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
ms.openlocfilehash: 0f5c9f0dde405aaadf50a7da476bbae664ef8ef7
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759382"
---
# <a name="functionenter-function"></a>Функция FunctionEnter

Уведомляет профилировщик о передаче управления в функцию.  
  
> [!NOTE]
> `FunctionEnter`Функция является устаревшей в платформа .NET Framework версии 2,0, и ее использование приведет к снижению производительности. Вместо этого используйте функцию [FunctionEnter2](functionenter2-function.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Параметры

`funcID` окне Идентификатор функции, которой передается элемент управления.

## <a name="remarks"></a>Remarks  

 `FunctionEnter`Функция является обратным вызовом. ее необходимо реализовать. Реализация должна использовать `__declspec` `naked` атрибут класса хранения ().  
  
 Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.  
  
- Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).  
  
- При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.  
  
 Реализация `FunctionEnter` не должна блокироваться, так как она приведет к задержке сборки мусора. Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, понятном для сборки мусора. Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionEnter` вернет.  
  
 Кроме того, `FunctionEnter` функция не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf. idl  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:** 1,1, 1,0  
  
## <a name="see-also"></a>См. также раздел

- [Функция FunctionEnter2](functionenter2-function.md)
- [Функция FunctionLeave2](functionleave2-function.md)
- [Функция FunctionTailcall2](functiontailcall2-function.md)
- [Метод SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Глобальные статические функции профилирования](profiling-global-static-functions.md)
