---
description: 'Дополнительные сведения о методе: ICorProfilerCallback2:: Финализеаблеобжекткуеуед'
title: Метод ICorProfilerCallback2::FinalizeableObjectQueued
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.FinalizeableObjectQueued
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type:
- apiref
ms.openlocfilehash: 62424ea60f72cee2328a143e4e50acd7af33e221
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647925"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="0d616-103">Метод ICorProfilerCallback2::FinalizeableObjectQueued</span><span class="sxs-lookup"><span data-stu-id="0d616-103">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>

<span data-ttu-id="0d616-104">Уведомляет профилировщик кода о том, что объект с методом завершения был помещен в очередь в поток метода завершения для выполнения своего `Finalize` метода.</span><span class="sxs-lookup"><span data-stu-id="0d616-104">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d616-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0d616-105">Syntax</span></span>  
  
```cpp  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d616-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0d616-106">Parameters</span></span>  

 `finalizerFlags`  
 <span data-ttu-id="0d616-107">окне Значение перечисления [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) , описывающее аспекты метода завершения.</span><span class="sxs-lookup"><span data-stu-id="0d616-107">[in] A value of the [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="0d616-108">окне Идентификатор объекта, который был поставлен в очередь.</span><span class="sxs-lookup"><span data-stu-id="0d616-108">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d616-109">Требования</span><span class="sxs-lookup"><span data-stu-id="0d616-109">Requirements</span></span>  

 <span data-ttu-id="0d616-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d616-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d616-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0d616-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d616-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d616-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d616-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d616-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d616-114">См. также</span><span class="sxs-lookup"><span data-stu-id="0d616-114">See also</span></span>

- [<span data-ttu-id="0d616-115">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="0d616-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0d616-116">Интерфейс ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="0d616-116">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
