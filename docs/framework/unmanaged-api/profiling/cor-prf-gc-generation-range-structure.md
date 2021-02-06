---
description: 'Дополнительные сведения: структура COR_PRF_GC_GENERATION_RANGE'
title: Структура COR_PRF_GC_GENERATION_RANGE
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords:
- COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type:
- apiref
ms.openlocfilehash: ea67a6e6b972b9406b84ad331e8af6189327c5ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648926"
---
# <a name="cor_prf_gc_generation_range-structure"></a><span data-ttu-id="763ff-103">Структура COR_PRF_GC_GENERATION_RANGE</span><span class="sxs-lookup"><span data-stu-id="763ff-103">COR_PRF_GC_GENERATION_RANGE Structure</span></span>

<span data-ttu-id="763ff-104">Описывает диапазон (т. е., блок) памяти, который занимается сборкой мусора.</span><span class="sxs-lookup"><span data-stu-id="763ff-104">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="763ff-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="763ff-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="763ff-106">Члены</span><span class="sxs-lookup"><span data-stu-id="763ff-106">Members</span></span>  
  
|<span data-ttu-id="763ff-107">Член</span><span class="sxs-lookup"><span data-stu-id="763ff-107">Member</span></span>|<span data-ttu-id="763ff-108">Описание</span><span class="sxs-lookup"><span data-stu-id="763ff-108">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="763ff-109">Значение перечисления [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) , указывающее поколение, к которому принадлежит блок памяти.</span><span class="sxs-lookup"><span data-stu-id="763ff-109">A value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="763ff-110">Идентификатор объекта, указывающего начальное расположение блока памяти.</span><span class="sxs-lookup"><span data-stu-id="763ff-110">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="763ff-111">Указатель на целое число, задающее размер используемой части блока памяти (то есть объема памяти, используемого в блоке).</span><span class="sxs-lookup"><span data-stu-id="763ff-111">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="763ff-112">Указатель на целое число, задающее размер блока памяти (то есть объема памяти, зарезервированного для блока).</span><span class="sxs-lookup"><span data-stu-id="763ff-112">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="763ff-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="763ff-113">Remarks</span></span>  

 <span data-ttu-id="763ff-114">`rangeLength`Значение гарантированно будет точным только в том случае, если [ICorProfilerInfo2:: GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) или [ICorProfilerInfo2:: GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), обе из которых используют `COR_PRF_GC_GENERATION_RANGE` структуру, вызывается из метода [ICorProfilerCallback2:: GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) или [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="763ff-114">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="763ff-115">Требования</span><span class="sxs-lookup"><span data-stu-id="763ff-115">Requirements</span></span>  

 <span data-ttu-id="763ff-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="763ff-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="763ff-117">**Заголовок:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="763ff-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="763ff-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="763ff-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="763ff-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="763ff-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="763ff-120">См. также</span><span class="sxs-lookup"><span data-stu-id="763ff-120">See also</span></span>

- [<span data-ttu-id="763ff-121">Структуры профилирования</span><span class="sxs-lookup"><span data-stu-id="763ff-121">Profiling Structures</span></span>](profiling-structures.md)
