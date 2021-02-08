---
description: 'Дополнительные сведения о методе: ICorProfilerCallback4:: Режиткомпилатионфинишед'
title: Метод ICorProfilerCallback4::ReJITCompilationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
ms.openlocfilehash: 2d7270b5a8cf31fd81505c148429da5f7025319a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788726"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="fa4bf-103">Метод ICorProfilerCallback4::ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="fa4bf-103">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>

<span data-ttu-id="fa4bf-104">Уведомляет профилировщик о том, что JIT-компилятор завершил повторную компиляцию функции.</span><span class="sxs-lookup"><span data-stu-id="fa4bf-104">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa4bf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fa4bf-105">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa4bf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fa4bf-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="fa4bf-107">окне Идентификатор перекомпилированной функции.</span><span class="sxs-lookup"><span data-stu-id="fa4bf-107">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="fa4bf-108">[in] Идентификатор функции, перекомпилированной с помощью JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="fa4bf-108">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="fa4bf-109">окне Значение, указывающее, успешно ли выполнена повторная компиляция JIT.</span><span class="sxs-lookup"><span data-stu-id="fa4bf-109">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="fa4bf-110">[входные] `true` чтобы указать, что блокировка может привести к тому, что среда выполнения будет ожидать возврата вызывающим потоком из этого обратного вызова. `false` чтобы указать, что блокировка не повлияет на работу среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="fa4bf-110">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="fa4bf-111">Значение `true` не нанесет вред исполняющей среде, но может повлиять на результаты профилирования.</span><span class="sxs-lookup"><span data-stu-id="fa4bf-111">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa4bf-112">Требования</span><span class="sxs-lookup"><span data-stu-id="fa4bf-112">Requirements</span></span>  

 <span data-ttu-id="fa4bf-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa4bf-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa4bf-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fa4bf-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fa4bf-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa4bf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa4bf-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa4bf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa4bf-117">См. также</span><span class="sxs-lookup"><span data-stu-id="fa4bf-117">See also</span></span>

- [<span data-ttu-id="fa4bf-118">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="fa4bf-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="fa4bf-119">Интерфейс ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="fa4bf-119">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="fa4bf-120">Метод JITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="fa4bf-120">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="fa4bf-121">Метод ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="fa4bf-121">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
