---
description: 'Дополнительные сведения о методе: метод icorprofilerinfo4:: EnumJITedFunctions2'
title: Метод ICorProfilerInfo4::EnumJITedFunctions2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumJITedFunctions2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type:
- apiref
ms.openlocfilehash: 3740236cfe2bc7ecc6cd3bbeb3345c7510dd159f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686951"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="05ec9-103">Метод ICorProfilerInfo4::EnumJITedFunctions2</span><span class="sxs-lookup"><span data-stu-id="05ec9-103">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>

<span data-ttu-id="05ec9-104">Возвращает перечислитель для всех функций, которые были ранее скомпилированы JIT-компилятором и повторно скомпилированы.</span><span class="sxs-lookup"><span data-stu-id="05ec9-104">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="05ec9-105">Этот метод заменяет метод [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) , который не перечисляет идентификаторы, перекомпилированные с помощью JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="05ec9-105">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05ec9-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="05ec9-106">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05ec9-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="05ec9-107">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="05ec9-108">заполняет Указатель на перечислитель [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="05ec9-108">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05ec9-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="05ec9-109">Remarks</span></span>  

 <span data-ttu-id="05ec9-110">Этот метод может пересекаться с `JITCompilation` обратными вызовами, такими как метод [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="05ec9-110">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="05ec9-111">Возвращаемое перечисление содержит значения для `COR_PRF_FUNCTION::reJitId` поля.</span><span class="sxs-lookup"><span data-stu-id="05ec9-111">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="05ec9-112">Метод [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) , который заменяет этот метод, не перечисляет идентификаторы, перекомпилированные с помощью JIT-компилятора, поскольку `COR_PRF_FUNCTION::reJitId` поле всегда имеет значение 0.</span><span class="sxs-lookup"><span data-stu-id="05ec9-112">The [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="05ec9-113">`ICorProfilerInfo4::EnumJITedFunctions`Метод выполняет перечисление идентификаторов, перекомпилированных JIT-компилятором, так как `COR_PRF_FUNCTION::reJitId` поле задано правильно.</span><span class="sxs-lookup"><span data-stu-id="05ec9-113">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="05ec9-114">Обратите внимание, что метод [метод icorprofilerinfo4:: EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) может запускать сборку мусора, в то время как [метод ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) не будет.</span><span class="sxs-lookup"><span data-stu-id="05ec9-114">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="05ec9-115">Дополнительные сведения см. в разделе [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="05ec9-115">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05ec9-116">Требования</span><span class="sxs-lookup"><span data-stu-id="05ec9-116">Requirements</span></span>  

 <span data-ttu-id="05ec9-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05ec9-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05ec9-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="05ec9-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05ec9-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05ec9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05ec9-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05ec9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ec9-121">См. также</span><span class="sxs-lookup"><span data-stu-id="05ec9-121">See also</span></span>

- [<span data-ttu-id="05ec9-122">Метод EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="05ec9-122">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="05ec9-123">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="05ec9-123">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="05ec9-124">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="05ec9-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="05ec9-125">Профилирование</span><span class="sxs-lookup"><span data-stu-id="05ec9-125">Profiling</span></span>](index.md)
