---
description: Дополнительные сведения о функции FunctionLeave2
title: Функция FunctionLeave2
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
ms.openlocfilehash: a9a97b84c70fd50044e8340b6f59fdbefe1d1a60
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760149"
---
# <a name="functionleave2-function"></a>Функция FunctionLeave2

Уведомляет профилировщик о том, что функция собирается вернуться к вызывающему объекту, и предоставляет сведения о кадре стека и возвращаемом значении функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a>Параметры

`funcId` окне Идентификатор возвращаемой функции.

`clientData` окне Идентификатор повторно сопоставленной функции, который профилировщик ранее указал с помощью функции [FunctionIDMapper](functionidmapper-function.md) .

`func` окне `COR_PRF_FRAME_INFO` Значение, указывающее на сведения о кадре стека.

Профилировщик должен рассматривать это как непрозрачный маркер, который можно передать обратно в подсистему выполнения метода [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
`retvalRange` окне Указатель на структуру [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) , указывающую расположение в памяти возвращаемого значения функции.

Чтобы получить доступ к сведениям о возвращаемом значении, `COR_PRF_ENABLE_FUNCTION_RETVAL` необходимо установить флаг. Профилировщик может использовать метод [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) для установки флагов событий.

## <a name="remarks"></a>Remarks  

 Значения `func` `retvalRange` параметров и недопустимы после `FunctionLeave2` возврата функции, так как значения могут измениться или быть уничтожены.  
  
 `FunctionLeave2`Функция является обратным вызовом. ее необходимо реализовать. Реализация должна использовать `__declspec` `naked` атрибут класса хранения ().  
  
 Подсистема выполнения не сохраняет никакие регистры перед вызовом этой функции.  
  
- Во время записи необходимо сохранить все используемые регистры, включая те, которые находятся в блоке с плавающей запятой (FPU).  
  
- При выходе необходимо восстановить стек, выключив все параметры, которые были переданы его вызывающим.  
  
 Реализация `FunctionLeave2` не должна блокироваться, так как она приведет к задержке сборки мусора. Реализация не должна пытаться выполнить сборку мусора, так как стек может не находиться в состоянии, понятном для сборки мусора. Если выполняется сборка мусора, среда выполнения будет блокироваться до тех пор, пока не `FunctionLeave2` вернет.  
  
 Кроме того, `FunctionLeave2` функция не должна вызывать управляемый код или каким-либо образом приводит к выделению управляемой памяти.  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf. idl  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Функция FunctionEnter2](functionenter2-function.md)
- [Функция FunctionTailcall2](functiontailcall2-function.md)
- [Метод SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Глобальные статические функции профилирования](profiling-global-static-functions.md)
