---
description: 'Дополнительные сведения о: интерфейс Икорпрофилерсреаденум'
title: Интерфейс ICorProfilerThreadEnum
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
ms.openlocfilehash: 035296412aabf20503588a558c8e8ccc1338210e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636396"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="f0558-103">Интерфейс ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="f0558-103">ICorProfilerThreadEnum Interface</span></span>

<span data-ttu-id="f0558-104">Предоставляет методы для последовательного перебора коллекции потоков в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="f0558-104">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0558-105">Методы</span><span class="sxs-lookup"><span data-stu-id="f0558-105">Methods</span></span>  
  
|<span data-ttu-id="f0558-106">Метод</span><span class="sxs-lookup"><span data-stu-id="f0558-106">Method</span></span>|<span data-ttu-id="f0558-107">Описание</span><span class="sxs-lookup"><span data-stu-id="f0558-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0558-108">Метод Clone</span><span class="sxs-lookup"><span data-stu-id="f0558-108">Clone Method</span></span>](icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="f0558-109">Получает указатель на копию этого интерфейса `ICorProfilerThreadEnum`.</span><span class="sxs-lookup"><span data-stu-id="f0558-109">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="f0558-110">Метод GetCount</span><span class="sxs-lookup"><span data-stu-id="f0558-110">GetCount Method</span></span>](icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="f0558-111">Возвращает число потоков, используемых приложением.</span><span class="sxs-lookup"><span data-stu-id="f0558-111">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="f0558-112">Следующий метод</span><span class="sxs-lookup"><span data-stu-id="f0558-112">Next Method</span></span>](icorprofilerthreadenum-next-method.md)|<span data-ttu-id="f0558-113">Возвращает заданное число смежных потоков из упорядоченной коллекции потоков начиная с текущей позиции перечислителя в последовательности.</span><span class="sxs-lookup"><span data-stu-id="f0558-113">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="f0558-114">Метод Reset</span><span class="sxs-lookup"><span data-stu-id="f0558-114">Reset Method</span></span>](icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="f0558-115">Перемещает курсор перечислителя в начальную позицию последовательности.</span><span class="sxs-lookup"><span data-stu-id="f0558-115">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="f0558-116">Метод Skip</span><span class="sxs-lookup"><span data-stu-id="f0558-116">Skip Method</span></span>](icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="f0558-117">Перемещает курсор перечислителя из текущей позиции, пропуская указанное число элементов.</span><span class="sxs-lookup"><span data-stu-id="f0558-117">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0558-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="f0558-118">Remarks</span></span>  

 <span data-ttu-id="f0558-119">Интерфейс `ICorProfilerThreadEnum` является перечислителем.</span><span class="sxs-lookup"><span data-stu-id="f0558-119">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="f0558-120">Он позволяет получающему массив объекту запрашивать элементы у отправляющего объекта с приемлемой для себя скоростью.</span><span class="sxs-lookup"><span data-stu-id="f0558-120">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="f0558-121">Иными словами, получающий объект может явным образом управлять потоком элементов массива, избегая тем самым проблем, связанных с передачей больших массивов в качестве параметров метода.</span><span class="sxs-lookup"><span data-stu-id="f0558-121">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0558-122">Требования</span><span class="sxs-lookup"><span data-stu-id="f0558-122">Requirements</span></span>  

 <span data-ttu-id="f0558-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0558-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0558-124">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0558-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f0558-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0558-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0558-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0558-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0558-127">См. также</span><span class="sxs-lookup"><span data-stu-id="f0558-127">See also</span></span>

- [<span data-ttu-id="f0558-128">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f0558-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f0558-129">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="f0558-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
