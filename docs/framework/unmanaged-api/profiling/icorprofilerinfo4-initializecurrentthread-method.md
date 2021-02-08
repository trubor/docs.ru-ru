---
description: 'Дополнительные сведения о методе: метод icorprofilerinfo4:: Инитиализекуррентсреад'
title: Метод ICorProfilerInfo4::InitializeCurrentThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
ms.openlocfilehash: a78816c736507a4a59da3ea1c75b078b54c34125
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781408"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="86f93-103">Метод ICorProfilerInfo4::InitializeCurrentThread</span><span class="sxs-lookup"><span data-stu-id="86f93-103">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>

<span data-ttu-id="86f93-104">Инициализирует текущий поток перед последовательными вызовами API профилировщика в том же потоке, что позволяет избежать взаимоблокировки.</span><span class="sxs-lookup"><span data-stu-id="86f93-104">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f93-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="86f93-105">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="86f93-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="86f93-106">Remarks</span></span>  

 <span data-ttu-id="86f93-107">Рекомендуется вызывать `InitializeCurrentThread` в любом потоке, который будет вызывать API профилировщика при наличии приостановленных потоков.</span><span class="sxs-lookup"><span data-stu-id="86f93-107">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="86f93-108">Этот метод обычно используется выборочными профилировщиками, которые создают собственный поток для вызова метода [ICorProfilerInfo2::D остаккснапшот](icorprofilerinfo2-dostacksnapshot-method.md) для выполнения проверки стека, пока целевой поток приостанавливается.</span><span class="sxs-lookup"><span data-stu-id="86f93-108">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="86f93-109">Вызывая `InitializeCurrentThread` один раз, когда профилировщик сначала создает поток выборки, профилировщики могут гарантировать, что отложенная инициализация для каждого потока, которая в противном случае будет выполняться средой CLR во время первого вызова, `DoStackSnapshot` теперь может быть безопасно, когда никакие другие потоки не будут приостановлены.</span><span class="sxs-lookup"><span data-stu-id="86f93-109">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86f93-110">`InitializeCurrentThread` Выполняет инициализацию заранее для завершения задач, которые принимают блокировки и могут быть взаимоблокировками.</span><span class="sxs-lookup"><span data-stu-id="86f93-110">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="86f93-111">Вызывайте `InitializeCurrentThread` , только если нет приостановленных потоков.</span><span class="sxs-lookup"><span data-stu-id="86f93-111">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86f93-112">Требования</span><span class="sxs-lookup"><span data-stu-id="86f93-112">Requirements</span></span>  

 <span data-ttu-id="86f93-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86f93-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86f93-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="86f93-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="86f93-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86f93-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86f93-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86f93-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f93-117">См. также</span><span class="sxs-lookup"><span data-stu-id="86f93-117">See also</span></span>

- [<span data-ttu-id="86f93-118">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="86f93-118">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="86f93-119">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="86f93-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="86f93-120">Профилирование</span><span class="sxs-lookup"><span data-stu-id="86f93-120">Profiling</span></span>](index.md)
