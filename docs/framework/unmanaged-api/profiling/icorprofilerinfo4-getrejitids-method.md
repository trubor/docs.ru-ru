---
description: 'Дополнительные сведения о методе: метод icorprofilerinfo4:: GetReJITIDs'
title: Метод ICorProfilerInfo4::GetReJITIDs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
ms.openlocfilehash: 60df4cb6023bbee68d2909e1cc0e9de5595ac0b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636407"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="9006d-103">Метод ICorProfilerInfo4::GetReJITIDs</span><span class="sxs-lookup"><span data-stu-id="9006d-103">ICorProfilerInfo4::GetReJITIDs Method</span></span>

<span data-ttu-id="9006d-104">Возвращает массив идентификаторов, которые определяют все все повторно скомпилированные версии указанной функции, которые все еще выделены.</span><span class="sxs-lookup"><span data-stu-id="9006d-104">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="9006d-105">Сюда входят JIT-повторно скомпилированные версии функций, которые впоследствии были отменены, но еще не освобождены (например, если домен приложения, содержащий функцию, которая содержит возвращенные функции, все еще используется).</span><span class="sxs-lookup"><span data-stu-id="9006d-105">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9006d-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9006d-106">Syntax</span></span>  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9006d-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="9006d-107">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="9006d-108">окне Объект `FunctionID` экземпляра функции, для которого требуется перечислить версии.</span><span class="sxs-lookup"><span data-stu-id="9006d-108">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="9006d-109">окне Число идентификаторов, перекомпилированных с помощью JIT-компилятора, выделенных в `reJitIds` массиве.</span><span class="sxs-lookup"><span data-stu-id="9006d-109">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="9006d-110">заполняет Фактическое число повторно скомпилированных идентификаторов с JIT-рекомпиляцией.</span><span class="sxs-lookup"><span data-stu-id="9006d-110">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="9006d-111">заполняет Выделенный вызывающим объектом массив, который будет содержать JIT-перекомпилированные идентификаторы для указанной функции.</span><span class="sxs-lookup"><span data-stu-id="9006d-111">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9006d-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="9006d-112">Remarks</span></span>  

 <span data-ttu-id="9006d-113">`GetReJITIDs` Перечисляет активные JIT-повторно скомпилированные идентификаторы для заданного экземпляра функции.</span><span class="sxs-lookup"><span data-stu-id="9006d-113">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="9006d-114">Он следует той же схеме использования, что и другие `ICorProfilerInfo` функции, принимающие буферы, выделенные вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="9006d-114">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9006d-115">Требования</span><span class="sxs-lookup"><span data-stu-id="9006d-115">Requirements</span></span>  

 <span data-ttu-id="9006d-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9006d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9006d-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9006d-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9006d-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9006d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9006d-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9006d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9006d-120">См. также</span><span class="sxs-lookup"><span data-stu-id="9006d-120">See also</span></span>

- [<span data-ttu-id="9006d-121">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="9006d-121">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="9006d-122">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="9006d-122">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="9006d-123">Профилирование</span><span class="sxs-lookup"><span data-stu-id="9006d-123">Profiling</span></span>](index.md)
