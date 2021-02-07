---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Манажедтаунманажедтранситион'
title: Метод ICorProfilerCallback::ManagedToUnmanagedTransition
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: bf7f45ae576f9812dee24cd3799a3a87678f7c61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705602"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="b00bb-103">Метод ICorProfilerCallback::ManagedToUnmanagedTransition</span><span class="sxs-lookup"><span data-stu-id="b00bb-103">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>

<span data-ttu-id="b00bb-104">Уведомляет профилировщик о том, что произошел переход из управляемого кода в неуправляемый код.</span><span class="sxs-lookup"><span data-stu-id="b00bb-104">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b00bb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b00bb-105">Syntax</span></span>  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b00bb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b00bb-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="b00bb-107">окне Идентификатор вызываемой функции.</span><span class="sxs-lookup"><span data-stu-id="b00bb-107">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="b00bb-108">окне Значение перечисления [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) , указывающее, произошло ли переход из-за вызова неуправляемого кода из управляемого кода или из-за возврата из управляемой функции, вызываемой неуправляемой функцией.</span><span class="sxs-lookup"><span data-stu-id="b00bb-108">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b00bb-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="b00bb-109">Remarks</span></span>  

 <span data-ttu-id="b00bb-110">Если значение `reason` равно COR_PRF_TRANSITION_CALL, идентификатором функции является неуправляемая функция, которая никогда не будет компилироваться с помощью JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="b00bb-110">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="b00bb-111">С неуправляемыми функциями связаны основные сведения, такие как имя и некоторые метаданные.</span><span class="sxs-lookup"><span data-stu-id="b00bb-111">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="b00bb-112">Если неуправляемая функция была вызвана с помощью неявного вызова платформы (PInvoke), среда выполнения не может определить назначение вызова, а значение `functionId` будет равно null.</span><span class="sxs-lookup"><span data-stu-id="b00bb-112">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="b00bb-113">Дополнительные сведения о неявном вызове PInvoke см. в разделе [использование взаимодействия C++ (неявный PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span><span class="sxs-lookup"><span data-stu-id="b00bb-113">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b00bb-114">Требования</span><span class="sxs-lookup"><span data-stu-id="b00bb-114">Requirements</span></span>  

 <span data-ttu-id="b00bb-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b00bb-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b00bb-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b00bb-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b00bb-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b00bb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b00bb-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b00bb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b00bb-119">См. также</span><span class="sxs-lookup"><span data-stu-id="b00bb-119">See also</span></span>

- [<span data-ttu-id="b00bb-120">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b00bb-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b00bb-121">Метод UnmanagedToManagedTransition</span><span class="sxs-lookup"><span data-stu-id="b00bb-121">UnmanagedToManagedTransition Method</span></span>](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [<span data-ttu-id="b00bb-122">Использование явного вызова PInvoke в C++ (атрибут DllImport)</span><span class="sxs-lookup"><span data-stu-id="b00bb-122">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
