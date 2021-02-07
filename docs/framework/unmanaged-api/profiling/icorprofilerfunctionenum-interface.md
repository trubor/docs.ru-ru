---
description: 'Дополнительные сведения о: Интерфейс ICorProfilerFunctionEnum'
title: Интерфейс ICorProfilerFunctionEnum
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
ms.openlocfilehash: 0a9437ee1f5c481c2c2d1fd46361da6e938dd179
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737601"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="b695d-103">Интерфейс ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="b695d-103">ICorProfilerFunctionEnum Interface</span></span>

<span data-ttu-id="b695d-104">Предоставляет методы для последовательного перебора коллекции функций в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="b695d-104">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b695d-105">Методы</span><span class="sxs-lookup"><span data-stu-id="b695d-105">Methods</span></span>  
  
|<span data-ttu-id="b695d-106">Метод</span><span class="sxs-lookup"><span data-stu-id="b695d-106">Method</span></span>|<span data-ttu-id="b695d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="b695d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b695d-108">Метод Clone</span><span class="sxs-lookup"><span data-stu-id="b695d-108">Clone Method</span></span>](icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="b695d-109">Получает указатель на копию этого интерфейса `ICorProfilerFunctionEnum`.</span><span class="sxs-lookup"><span data-stu-id="b695d-109">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="b695d-110">Метод GetCount</span><span class="sxs-lookup"><span data-stu-id="b695d-110">GetCount Method</span></span>](icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="b695d-111">Возвращает количество функций, загруженных приложением или принудительно загруженных профилировщиком.</span><span class="sxs-lookup"><span data-stu-id="b695d-111">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="b695d-112">Следующий метод</span><span class="sxs-lookup"><span data-stu-id="b695d-112">Next Method</span></span>](icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="b695d-113">Возвращает заданное число смежных функций из последовательной коллекции функций начиная с текущей позиции перечислителя в последовательности.</span><span class="sxs-lookup"><span data-stu-id="b695d-113">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="b695d-114">Метод Reset</span><span class="sxs-lookup"><span data-stu-id="b695d-114">Reset Method</span></span>](icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="b695d-115">Перемещает курсор перечислителя в начальную позицию последовательности.</span><span class="sxs-lookup"><span data-stu-id="b695d-115">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="b695d-116">Метод Skip</span><span class="sxs-lookup"><span data-stu-id="b695d-116">Skip Method</span></span>](icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="b695d-117">Перемещает курсор перечислителя из текущей позиции, пропуская указанное число элементов.</span><span class="sxs-lookup"><span data-stu-id="b695d-117">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b695d-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="b695d-118">Remarks</span></span>  

 <span data-ttu-id="b695d-119">Интерфейс `ICorProfilerFunctionEnum` является перечислителем.</span><span class="sxs-lookup"><span data-stu-id="b695d-119">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="b695d-120">Он позволяет получающему массив объекту запрашивать элементы у отправляющего объекта с приемлемой для себя скоростью.</span><span class="sxs-lookup"><span data-stu-id="b695d-120">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="b695d-121">Иными словами, получающий объект может явным образом управлять потоком элементов массива, избегая тем самым проблем, связанных с передачей больших массивов в качестве параметров метода.</span><span class="sxs-lookup"><span data-stu-id="b695d-121">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="b695d-122">Интерфейс `ICorProfilerFunctionEnum` перечисляет функции, которые уже были скомпилированы для JIT-отладки, но не включает функции, загруженные из собственных образов, созданных с помощью программы Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="b695d-122">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b695d-123">Требования</span><span class="sxs-lookup"><span data-stu-id="b695d-123">Requirements</span></span>  

 <span data-ttu-id="b695d-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b695d-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b695d-125">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b695d-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b695d-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b695d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b695d-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b695d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b695d-128">См. также</span><span class="sxs-lookup"><span data-stu-id="b695d-128">See also</span></span>

- [<span data-ttu-id="b695d-129">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="b695d-129">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="b695d-130">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="b695d-130">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b695d-131">Метод EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="b695d-131">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
