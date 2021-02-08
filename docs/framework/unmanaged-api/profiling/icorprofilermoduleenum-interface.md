---
description: 'Дополнительные сведения о: интерфейс ICorProfilerModuleEnum'
title: Интерфейс ICorProfilerModuleEnum
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
ms.openlocfilehash: 195379e9ad6bce94fc93465fe5e1418c5d8c076d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783824"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="89ca8-103">Интерфейс ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="89ca8-103">ICorProfilerModuleEnum Interface</span></span>

<span data-ttu-id="89ca8-104">Предоставляет методы для последовательного перебора коллекции модулей, загруженных приложением или профилировщиком.</span><span class="sxs-lookup"><span data-stu-id="89ca8-104">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89ca8-105">Методы</span><span class="sxs-lookup"><span data-stu-id="89ca8-105">Methods</span></span>  
  
|<span data-ttu-id="89ca8-106">Метод</span><span class="sxs-lookup"><span data-stu-id="89ca8-106">Method</span></span>|<span data-ttu-id="89ca8-107">Описание</span><span class="sxs-lookup"><span data-stu-id="89ca8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89ca8-108">Метод Clone</span><span class="sxs-lookup"><span data-stu-id="89ca8-108">Clone Method</span></span>](icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="89ca8-109">Получает указатель на копию этого интерфейса `ICorProfilerModuleEnum`.</span><span class="sxs-lookup"><span data-stu-id="89ca8-109">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="89ca8-110">Метод GetCount</span><span class="sxs-lookup"><span data-stu-id="89ca8-110">GetCount Method</span></span>](icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="89ca8-111">Возвращает число управляемых модулей, загруженных в приложение.</span><span class="sxs-lookup"><span data-stu-id="89ca8-111">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="89ca8-112">Следующий метод</span><span class="sxs-lookup"><span data-stu-id="89ca8-112">Next Method</span></span>](icorprofilermoduleenum-next-method.md)|<span data-ttu-id="89ca8-113">Возвращает заданное число смежных модулей из последовательной коллекции объектов начиная с текущей позиции перечислителя в последовательности.</span><span class="sxs-lookup"><span data-stu-id="89ca8-113">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="89ca8-114">Метод Reset</span><span class="sxs-lookup"><span data-stu-id="89ca8-114">Reset Method</span></span>](icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="89ca8-115">Перемещает курсор перечислителя в начальную позицию последовательности.</span><span class="sxs-lookup"><span data-stu-id="89ca8-115">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="89ca8-116">Метод Skip</span><span class="sxs-lookup"><span data-stu-id="89ca8-116">Skip Method</span></span>](icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="89ca8-117">Перемещает курсор перечислителя из текущей позиции, пропуская указанное число элементов.</span><span class="sxs-lookup"><span data-stu-id="89ca8-117">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89ca8-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="89ca8-118">Remarks</span></span>  

 <span data-ttu-id="89ca8-119">Интерфейс `ICorProfilerModuleEnum` является перечислителем.</span><span class="sxs-lookup"><span data-stu-id="89ca8-119">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="89ca8-120">Он позволяет получающему массив объекту запрашивать элементы у отправляющего объекта с приемлемой для себя скоростью.</span><span class="sxs-lookup"><span data-stu-id="89ca8-120">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="89ca8-121">Иными словами, получающий объект может явным образом управлять потоком элементов массива, избегая тем самым проблем, связанных с передачей больших массивов в качестве параметров метода.</span><span class="sxs-lookup"><span data-stu-id="89ca8-121">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89ca8-122">Требования</span><span class="sxs-lookup"><span data-stu-id="89ca8-122">Requirements</span></span>  

 <span data-ttu-id="89ca8-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89ca8-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89ca8-124">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="89ca8-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="89ca8-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89ca8-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89ca8-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89ca8-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ca8-127">См. также</span><span class="sxs-lookup"><span data-stu-id="89ca8-127">See also</span></span>

- [<span data-ttu-id="89ca8-128">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="89ca8-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="89ca8-129">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="89ca8-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="89ca8-130">Метод EnumModules</span><span class="sxs-lookup"><span data-stu-id="89ca8-130">EnumModules Method</span></span>](icorprofilerinfo3-enummodules-method.md)
