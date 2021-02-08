---
description: 'Дополнительные сведения о: интерфейс метод icorprofilerinfo4'
title: Интерфейс ICorProfilerInfo4
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
ms.openlocfilehash: 94e33be74ccffea3fa9a0e51e317a6888596606d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794511"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="3f1c6-103">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="3f1c6-103">ICorProfilerInfo4 Interface</span></span>

<span data-ttu-id="3f1c6-104">Предоставляет методы, используемые профилировщиками кода для взаимодействия со средой CLR для управления мониторингом событий и сведениями о запросах.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-104">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="3f1c6-105">.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-105">.</span></span> <span data-ttu-id="3f1c6-106">`ICorProfilerInfo4`Интерфейс является расширением других `ICorProfilerInfo` интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-106">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="3f1c6-107">Он предоставляет новые методы для поддержки повторной компиляции JIT, добавленной в платформа .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-107">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f1c6-108">Методы</span><span class="sxs-lookup"><span data-stu-id="3f1c6-108">Methods</span></span>  
  
|<span data-ttu-id="3f1c6-109">Метод</span><span class="sxs-lookup"><span data-stu-id="3f1c6-109">Method</span></span>|<span data-ttu-id="3f1c6-110">Описание</span><span class="sxs-lookup"><span data-stu-id="3f1c6-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f1c6-111">Метод EnumJITedFunctions2</span><span class="sxs-lookup"><span data-stu-id="3f1c6-111">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="3f1c6-112">Возвращает перечислитель для всех функций, которые были ранее скомпилированы JIT-компилятором и повторно скомпилированы.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-112">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="3f1c6-113">Метод EnumThreads</span><span class="sxs-lookup"><span data-stu-id="3f1c6-113">EnumThreads Method</span></span>](icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="3f1c6-114">Возвращает перечислитель, предоставляющий методы для последовательного прохода по коллекции всех управляемых потоков в процессе профилирования.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-114">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="3f1c6-115">Метод GetCodeInfo3</span><span class="sxs-lookup"><span data-stu-id="3f1c6-115">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="3f1c6-116">Получает экстенты машинного кода, связанного с перекомпилированной с помощью JIT-компилятора версией указанной функции.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-116">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="3f1c6-117">Метод GetFunctionFromIP2</span><span class="sxs-lookup"><span data-stu-id="3f1c6-117">GetFunctionFromIP2 Method</span></span>](icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="3f1c6-118">Сопоставляет указатель инструкции управляемого кода с JIT-повторно скомпилированной версией указанной функции.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-118">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="3f1c6-119">Метод GetILToNativeMapping2</span><span class="sxs-lookup"><span data-stu-id="3f1c6-119">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="3f1c6-120">Возвращает карту из смещений MSIL к собственным смещениям для кода, содержащегося в JIT-повторно скомпилированной версии указанной функции.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-120">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="3f1c6-121">Метод GetObjectSize2</span><span class="sxs-lookup"><span data-stu-id="3f1c6-121">GetObjectSize2 Method</span></span>](icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="3f1c6-122">Возвращает размер указанного объекта.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-122">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="3f1c6-123">Метод GetReJITIDs</span><span class="sxs-lookup"><span data-stu-id="3f1c6-123">GetReJITIDs Method</span></span>](icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="3f1c6-124">Возвращает массив идентификаторов, которые определяют все все повторно скомпилированные версии указанной функции, которые все еще выделены.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-124">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="3f1c6-125">Метод InitializeCurrentThread</span><span class="sxs-lookup"><span data-stu-id="3f1c6-125">InitializeCurrentThread Method</span></span>](icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="3f1c6-126">Инициализирует текущий поток перед последовательными вызовами API профилировщика в том же потоке, что позволяет избежать взаимоблокировки.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-126">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="3f1c6-127">Метод RequestReJIT</span><span class="sxs-lookup"><span data-stu-id="3f1c6-127">RequestReJIT Method</span></span>](icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="3f1c6-128">Запрашивает перекомпиляцию JIT всех экземпляров указанных функций.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-128">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="3f1c6-129">Метод RequestRevert</span><span class="sxs-lookup"><span data-stu-id="3f1c6-129">RequestRevert Method</span></span>](icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="3f1c6-130">Восстанавливает исходные версии всех экземпляров указанных функций.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-130">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f1c6-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="3f1c6-131">Remarks</span></span>  

 <span data-ttu-id="3f1c6-132">Среда CLR реализует методы интерфейса `ICorProfilerInfo4` с помощью модели свободных потоков.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-132">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="3f1c6-133">Каждый метод возвращает значение HRESULT, указывающее на успешное выполнение или сбой.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-133">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="3f1c6-134">Список возможных кодов возврата см. в файле CorError.h.</span><span class="sxs-lookup"><span data-stu-id="3f1c6-134">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f1c6-135">Требования</span><span class="sxs-lookup"><span data-stu-id="3f1c6-135">Requirements</span></span>  

 <span data-ttu-id="3f1c6-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f1c6-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f1c6-137">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3f1c6-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3f1c6-138">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f1c6-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f1c6-139">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f1c6-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f1c6-140">См. также</span><span class="sxs-lookup"><span data-stu-id="3f1c6-140">See also</span></span>

- [<span data-ttu-id="3f1c6-141">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="3f1c6-141">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3f1c6-142">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="3f1c6-142">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
