---
description: Дополнительные сведения о функции FunctionIDMapper
title: Функция FunctionIDMapper
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: 2db616509bf5dcb5b8aee9cea76a9841369ec49d
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759257"
---
# <a name="functionidmapper-function"></a>Функция FunctionIDMapper

Уведомляет профилировщик о том, что заданный идентификатор функции может быть повторно сопоставлен с альтернативным ИДЕНТИФИКАТОРом для использования в обратных вызовах [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)и [FunctionTailcall2](functiontailcall2-function.md) для этой функции. `FunctionIDMapper` также позволяет профилировщику указать, желает ли он получать обратные вызовы для этой функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Параметры

`funcId` окне Идентификатор функции для повторного сопоставления.

`pbHookFunction` заполняет Указатель на значение, которое задает профилировщик `true` , если он хочет получать `FunctionEnter2` `FunctionLeave2` `FunctionTailcall2` обратные вызовы, и, в противном случае присваивает этому параметру значение `false` .

## <a name="return-value"></a>Возвращаемое значение  

 Профилировщик возвращает значение, которое использует подсистема выполнения в качестве альтернативного идентификатора функции. Это возвращаемое значение не может быть значением null, если указатель `pbHookFunction` возвращает значение `false`. В противном случае возвращаемое значение null приведет к непредсказуемым результатам, включая, возможно, остановку процесса.  
  
## <a name="remarks"></a>Remarks  

 `FunctionIDMapper`Функция является обратным вызовом. Он реализуется профилировщиком для повторного сопоставления идентификатора функции с другим идентификатором, который более удобен для профилировщика. `FunctionIDMapper`Возвращает альтернативный идентификатор, используемый для любой заданной функции. Затем подсистема выполнения обрабатывает запрос профилировщика, передавая этот альтернативный идентификатор, помимо традиционного идентификатора функции, обратно в профилировщик в `clientData` параметре `FunctionEnter2` `FunctionLeave2` `FunctionTailcall2` обработчиков, и, чтобы найти функцию, для которой вызывается обработчик.  
  
 Для указания реализации функции можно использовать метод [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) `FunctionIDMapper` . Метод можно вызвать `ICorProfilerInfo::SetFunctionIDMapper` только один раз, и это рекомендуется сделать в обратном вызове [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .  
  
 По умолчанию предполагается, что профилировщик, устанавливающий флаг COR_PRF_MONITOR_ENTERLEAVE с помощью [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)и устанавливающий перехватчики через [ICorProfilerInfo:: сетентерлеавефунктионхукс](icorprofilerinfo-setenterleavefunctionhooks-method.md) или [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), должен получить `FunctionEnter2` `FunctionLeave2` `FunctionTailcall2` обратные вызовы, и для каждой функции. Однако профилировщики могут реализовать, `FunctionIDMapper` чтобы выборочно избежать получения этих обратных вызовов для определенных функций, задав `pbHookFunction` для значение `false` .  
  
 Профилировщики должны быть нечувствительными к случаям, когда несколько потоков профилированного приложения вызывают один и тот же метод или функцию одновременно. В таких случаях профилировщик может получить несколько `FunctionIDMapper` обратных вызовов для одного и того же `FunctionID` . Профилировщик должен быть уверенным в том, чтобы возвращать те же значения из этого обратного вызова, когда он вызывается несколько раз с одним и тем же `FunctionID` .  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** CorProf. idl  
  
 **Библиотека:** CorGuids.lib  
  
 **Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Метод SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [Функция FunctionIDMapper2](functionidmapper2-function.md)
- [Функция FunctionEnter2](functionenter2-function.md)
- [Функция FunctionLeave2](functionleave2-function.md)
- [Функция FunctionTailcall2](functiontailcall2-function.md)
- [Глобальные статические функции профилирования](profiling-global-static-functions.md)
