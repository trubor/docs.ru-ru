---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: JITFunctionPitched'
title: Метод ICorProfilerCallback::JITFunctionPitched
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
ms.openlocfilehash: 11729de2188fe2f2cec7ec16ff7a5d1928cbd75d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705724"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="c29b8-103">Метод ICorProfilerCallback::JITFunctionPitched</span><span class="sxs-lookup"><span data-stu-id="c29b8-103">ICorProfilerCallback::JITFunctionPitched Method</span></span>

<span data-ttu-id="c29b8-104">Оповещает профилировщик о том, что JIT-скомпилированная функция была удалена из памяти.</span><span class="sxs-lookup"><span data-stu-id="c29b8-104">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c29b8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c29b8-105">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c29b8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c29b8-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="c29b8-107">окне Идентификатор удаленной функции.</span><span class="sxs-lookup"><span data-stu-id="c29b8-107">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c29b8-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="c29b8-108">Remarks</span></span>  

 <span data-ttu-id="c29b8-109">Если вызывается Удаленная функция, профилировщик получит новые события JIT-компиляции при повторной компиляции функции.</span><span class="sxs-lookup"><span data-stu-id="c29b8-109">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="c29b8-110">В настоящее время JIT-компилятор среды CLR не удаляет функции из памяти, поэтому этот обратный вызов сейчас не используется и не будет получен профилировщиком.</span><span class="sxs-lookup"><span data-stu-id="c29b8-110">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="c29b8-111">Значение недопустимо `functionId` до повторной компиляции функции.</span><span class="sxs-lookup"><span data-stu-id="c29b8-111">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="c29b8-112">При повторной компиляции функции `functionId` будет использоваться то же значение.</span><span class="sxs-lookup"><span data-stu-id="c29b8-112">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c29b8-113">Требования</span><span class="sxs-lookup"><span data-stu-id="c29b8-113">Requirements</span></span>  

 <span data-ttu-id="c29b8-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c29b8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c29b8-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c29b8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c29b8-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c29b8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c29b8-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c29b8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c29b8-118">См. также</span><span class="sxs-lookup"><span data-stu-id="c29b8-118">See also</span></span>

- [<span data-ttu-id="c29b8-119">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="c29b8-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
