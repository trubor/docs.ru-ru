---
description: 'Дополнительные сведения о методе: ICorProfilerCallback3::P Рофилердетачсукцеедед'
title: Метод ICorProfilerCallback3::ProfilerDetachSucceeded
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
ms.openlocfilehash: bc80b5bd5301bb5b0278534cfba6ac23e5968620
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788778"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="b9dfe-103">Метод ICorProfilerCallback3::ProfilerDetachSucceeded</span><span class="sxs-lookup"><span data-stu-id="b9dfe-103">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>

<span data-ttu-id="b9dfe-104">Уведомляет профилировщик о том, что среда CLR намерена выгрузить библиотеку DLL профилировщика.</span><span class="sxs-lookup"><span data-stu-id="b9dfe-104">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9dfe-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b9dfe-105">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b9dfe-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b9dfe-106">Return Value</span></span>  

 <span data-ttu-id="b9dfe-107">Возвращаемое значение этого обратного вызова игнорируется.</span><span class="sxs-lookup"><span data-stu-id="b9dfe-107">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9dfe-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="b9dfe-108">Remarks</span></span>  

 <span data-ttu-id="b9dfe-109">Обратный вызов `ProfilerDetachSucceeded` производится после того, как все потоки вышли из кода профилировщика.</span><span class="sxs-lookup"><span data-stu-id="b9dfe-109">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="b9dfe-110">Когда вызывается этот метод, профилировщик должен выполнить все завершающие задачи, которые не может выполнить его деструктор, такие как уведомление интерфейса пользователя или компонента ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="b9dfe-110">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="b9dfe-111">Однако профилировщик не должен вызывать функции для интерфейсов, предоставляемых средой CLR во время этого обратного вызова (например, в [ICorProfilerInfo](icorprofilerinfo-interface.md) или `IMetaData*` интерфейсах).</span><span class="sxs-lookup"><span data-stu-id="b9dfe-111">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="b9dfe-112">Среда CLR создает запись в журнале событий приложений Windows о том, что операция отключения выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="b9dfe-112">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="b9dfe-113">После возврата профилировщика из этого обратного вызова среда CLR освобождает объект профилировщика и выгружает библиотеку DLL профилировщика.</span><span class="sxs-lookup"><span data-stu-id="b9dfe-113">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="b9dfe-114">Поэтому после возврата из обратного вызова профилировщик не должен выполнять никаких действий, которые вызовут выполнение кода в библиотеке DLL профилировщика.</span><span class="sxs-lookup"><span data-stu-id="b9dfe-114">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="b9dfe-115">Например, он не должен создавать потоки или регистрировать обратные вызовы таймера.</span><span class="sxs-lookup"><span data-stu-id="b9dfe-115">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9dfe-116">Требования</span><span class="sxs-lookup"><span data-stu-id="b9dfe-116">Requirements</span></span>  

 <span data-ttu-id="b9dfe-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9dfe-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9dfe-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b9dfe-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9dfe-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9dfe-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9dfe-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9dfe-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9dfe-121">См. также</span><span class="sxs-lookup"><span data-stu-id="b9dfe-121">See also</span></span>

- [<span data-ttu-id="b9dfe-122">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="b9dfe-122">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
- [<span data-ttu-id="b9dfe-123">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="b9dfe-123">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="b9dfe-124">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="b9dfe-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b9dfe-125">Профилирование</span><span class="sxs-lookup"><span data-stu-id="b9dfe-125">Profiling</span></span>](index.md)
