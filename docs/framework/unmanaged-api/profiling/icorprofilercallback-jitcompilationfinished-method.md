---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: JITCompilationFinished'
title: Метод ICorProfilerCallback::JITCompilationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
ms.openlocfilehash: 32a47860ae2e973d32ef12b2bd9002bb1de45ee9
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760331"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="0d6d6-103">Метод ICorProfilerCallback::JITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="0d6d6-103">ICorProfilerCallback::JITCompilationFinished Method</span></span>

<span data-ttu-id="0d6d6-104">Уведомляет профилировщик о том, что JIT-компилятор завершил компиляцию функции.</span><span class="sxs-lookup"><span data-stu-id="0d6d6-104">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d6d6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0d6d6-105">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d6d6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0d6d6-106">Parameters</span></span>

<span data-ttu-id="0d6d6-107">`functionId` окне Идентификатор скомпилированной функции.</span><span class="sxs-lookup"><span data-stu-id="0d6d6-107">`functionId` [in] The ID of the function that was compiled.</span></span>

<span data-ttu-id="0d6d6-108">`hrStatus` окне Значение, указывающее, успешно ли выполнена компиляция.</span><span class="sxs-lookup"><span data-stu-id="0d6d6-108">`hrStatus` [in] A value indicating whether compilation was successful.</span></span>

<span data-ttu-id="0d6d6-109">`fIsSafeToBlock` окне Значение, указывающее профилировщику, будет ли блокировка влиять на работу среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="0d6d6-109">`fIsSafeToBlock` [in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="0d6d6-110">Значение равно `true` , если блокировка может привести к тому, что среда выполнения будет ожидать возврата вызывающим потоком из этого обратного вызова; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="0d6d6-110">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>

<span data-ttu-id="0d6d6-111">Хотя значение `true` не будет нанести вред среде выполнения, оно может наклонять результаты профилирования.</span><span class="sxs-lookup"><span data-stu-id="0d6d6-111">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d6d6-112">Требования</span><span class="sxs-lookup"><span data-stu-id="0d6d6-112">Requirements</span></span>  

 <span data-ttu-id="0d6d6-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d6d6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d6d6-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0d6d6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d6d6-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d6d6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d6d6-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d6d6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d6d6-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0d6d6-117">See also</span></span>

- [<span data-ttu-id="0d6d6-118">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0d6d6-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0d6d6-119">Метод JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="0d6d6-119">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
