---
description: 'Дополнительные сведения о методе: ICorProfilerInfo3:: EnumJITedFunctions'
title: Метод ICorProfilerInfo3::EnumJITedFunctions
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
ms.openlocfilehash: 2f5f8358e7f01c20fc6edee60869bad01b0936c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646937"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="0f9a8-103">Метод ICorProfilerInfo3::EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="0f9a8-103">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>

<span data-ttu-id="0f9a8-104">Возвращает перечислитель для всех функций, которые были ранее скомпилированы JIT-компилятором.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-104">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f9a8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0f9a8-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f9a8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0f9a8-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="0f9a8-107">заполняет Указатель на перечислитель [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0f9a8-107">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f9a8-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="0f9a8-108">Remarks</span></span>  

 <span data-ttu-id="0f9a8-109">Этот метод может пересекаться с `JITCompilation` обратными вызовами, такими как метод [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0f9a8-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="0f9a8-110">Перечислитель, возвращаемый этим методом, не включает функции, загруженные из образов в машинном кодах, созданных с помощью Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-110">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f9a8-111">Возвращаемое перечисление содержит только значение "0" для значения `COR_PRF_FUNCTION::reJitId` поля.</span><span class="sxs-lookup"><span data-stu-id="0f9a8-111">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="0f9a8-112">Если требуются допустимые `COR_PRF_FUNCTION::reJitId` значения, используйте метод [метод icorprofilerinfo4:: EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0f9a8-112">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f9a8-113">Требования</span><span class="sxs-lookup"><span data-stu-id="0f9a8-113">Requirements</span></span>  

 <span data-ttu-id="0f9a8-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f9a8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f9a8-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0f9a8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0f9a8-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f9a8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f9a8-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f9a8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f9a8-118">См. также</span><span class="sxs-lookup"><span data-stu-id="0f9a8-118">See also</span></span>

- [<span data-ttu-id="0f9a8-119">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="0f9a8-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="0f9a8-120">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="0f9a8-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0f9a8-121">Профилирование</span><span class="sxs-lookup"><span data-stu-id="0f9a8-121">Profiling</span></span>](index.md)
