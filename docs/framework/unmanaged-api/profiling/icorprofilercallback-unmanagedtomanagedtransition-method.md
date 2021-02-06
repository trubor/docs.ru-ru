---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Унманажедтоманажедтранситион'
title: Метод ICorProfilerCallback::UnmanagedToManagedTransition
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
ms.openlocfilehash: 2b2bd86798df8b8c46506c924ee201c191e6cb82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657155"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a><span data-ttu-id="1bd68-103">Метод ICorProfilerCallback::UnmanagedToManagedTransition</span><span class="sxs-lookup"><span data-stu-id="1bd68-103">ICorProfilerCallback::UnmanagedToManagedTransition Method</span></span>

<span data-ttu-id="1bd68-104">Уведомляет профилировщик о том, что произошел переход из неуправляемого кода в управляемый код.</span><span class="sxs-lookup"><span data-stu-id="1bd68-104">Notifies the profiler that a transition from unmanaged code to managed code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd68-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1bd68-105">Syntax</span></span>  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bd68-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1bd68-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="1bd68-107">окне Идентификатор вызываемой функции.</span><span class="sxs-lookup"><span data-stu-id="1bd68-107">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="1bd68-108">окне Значение перечисления [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) , указывающее, произошло ли переход из-за вызова управляемого кода из неуправляемого кода или из-за возврата из неуправляемой функции, вызванной управляемой.</span><span class="sxs-lookup"><span data-stu-id="1bd68-108">[in] A value of the [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into managed code from unmanaged code, or because of a return from an unmanaged function called by a managed one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bd68-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="1bd68-109">Remarks</span></span>  

 <span data-ttu-id="1bd68-110">Если значение `reason` равно COR_PRF_TRANSITION_RETURN и `functionId` не равно null, идентификатор функции является неуправляемой функцией и никогда не будет компилироваться с помощью JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="1bd68-110">If the value of `reason` is COR_PRF_TRANSITION_RETURN and `functionId` is not null, the function ID is that of the unmanaged function, and will never have been compiled using the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="1bd68-111">С неуправляемыми функциями связаны некоторые основные сведения, такие как имя и некоторые метаданные.</span><span class="sxs-lookup"><span data-stu-id="1bd68-111">Unmanaged functions have some basic information associated with them, such as a name and some metadata.</span></span>  
  
 <span data-ttu-id="1bd68-112">Если значение `reason` равно COR_PRF_TRANSITION_CALL, возможно, что вызванная функция (то есть управляемая функция) еще не скомпилирована с помощью JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="1bd68-112">If the value of `reason` is COR_PRF_TRANSITION_CALL, it may be possible that the called function (that is, the managed function) has not yet been JIT-compiled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bd68-113">Требования</span><span class="sxs-lookup"><span data-stu-id="1bd68-113">Requirements</span></span>  

 <span data-ttu-id="1bd68-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bd68-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bd68-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1bd68-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1bd68-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bd68-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bd68-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bd68-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd68-118">См. также</span><span class="sxs-lookup"><span data-stu-id="1bd68-118">See also</span></span>

- [<span data-ttu-id="1bd68-119">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="1bd68-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1bd68-120">Метод ManagedToUnmanagedTransition</span><span class="sxs-lookup"><span data-stu-id="1bd68-120">ManagedToUnmanagedTransition Method</span></span>](icorprofilercallback-managedtounmanagedtransition-method.md)
- [<span data-ttu-id="1bd68-121">Использование явного вызова PInvoke в C++ (атрибут DllImport)</span><span class="sxs-lookup"><span data-stu-id="1bd68-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [<span data-ttu-id="1bd68-122">Использование взаимодействия C++ (неявный PInvoke)</span><span class="sxs-lookup"><span data-stu-id="1bd68-122">Using C++ Interop (Implicit PInvoke)</span></span>](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
