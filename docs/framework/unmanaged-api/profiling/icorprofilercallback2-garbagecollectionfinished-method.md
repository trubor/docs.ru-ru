---
description: 'Дополнительные сведения о методе: ICorProfilerCallback2:: GarbageCollectionFinished'
title: Метод ICorProfilerCallback2::GarbageCollectionFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type:
- apiref
ms.openlocfilehash: 9e41c5ced76af40866269fdff74fd302b937b70e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657117"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="b8c54-103">Метод ICorProfilerCallback2::GarbageCollectionFinished</span><span class="sxs-lookup"><span data-stu-id="b8c54-103">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>

<span data-ttu-id="b8c54-104">Уведомляет профилировщик о завершении сборки мусора и выдает для него все обратные вызовы сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="b8c54-104">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8c54-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b8c54-105">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b8c54-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="b8c54-106">Remarks</span></span>  

 <span data-ttu-id="b8c54-107">Профилировщик может быть защищен для проверки объектов в их конечном расположении при `GarbageCollectionFinished` вызове метода.</span><span class="sxs-lookup"><span data-stu-id="b8c54-107">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8c54-108">Требования</span><span class="sxs-lookup"><span data-stu-id="b8c54-108">Requirements</span></span>  

 <span data-ttu-id="b8c54-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8c54-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8c54-110">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b8c54-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b8c54-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8c54-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8c54-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8c54-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c54-113">См. также</span><span class="sxs-lookup"><span data-stu-id="b8c54-113">See also</span></span>

- [<span data-ttu-id="b8c54-114">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b8c54-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b8c54-115">Интерфейс ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="b8c54-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
