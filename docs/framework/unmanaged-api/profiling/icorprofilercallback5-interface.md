---
description: 'Дополнительные сведения о: интерфейс ICorProfilerCallback5'
title: Интерфейс ICorProfilerCallback5
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
ms.openlocfilehash: b80b27dc994ad556381228370ece92935d89d293
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788661"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="3eb31-103">Интерфейс ICorProfilerCallback5</span><span class="sxs-lookup"><span data-stu-id="3eb31-103">ICorProfilerCallback5 Interface</span></span>

<span data-ttu-id="3eb31-104">Дополняет сведения, чтобы помочь профилировщику определить полное закрытие динамических объектов при использовании метода [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) или [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) вместе с методами [ICorProfilerCallback:: ObjectReferences](icorprofilercallback-objectreferences-method.md) и [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3eb31-104">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="3eb31-105">Для подписки на уведомления, связанные с зависимыми дескрипторами профилировщик управляемой памяти должен реализовать `ICorProfilerCallback5`.</span><span class="sxs-lookup"><span data-stu-id="3eb31-105">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3eb31-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="3eb31-106">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3eb31-107">Методы</span><span class="sxs-lookup"><span data-stu-id="3eb31-107">Methods</span></span>  
  
|<span data-ttu-id="3eb31-108">Метод</span><span class="sxs-lookup"><span data-stu-id="3eb31-108">Method</span></span>|<span data-ttu-id="3eb31-109">Описание</span><span class="sxs-lookup"><span data-stu-id="3eb31-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3eb31-110">Метод ConditionalWeakTableElementReferences</span><span class="sxs-lookup"><span data-stu-id="3eb31-110">ConditionalWeakTableElementReferences Method</span></span>](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="3eb31-111">Идентифицирует транзитивное замыкание объектов, на которые ссылаются эти корневые элементы как через прямые ссылки на поля члена, так и через зависимости `ConditionalWeakTable`.</span><span class="sxs-lookup"><span data-stu-id="3eb31-111">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3eb31-112">Требования</span><span class="sxs-lookup"><span data-stu-id="3eb31-112">Requirements</span></span>  

 <span data-ttu-id="3eb31-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eb31-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eb31-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3eb31-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3eb31-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eb31-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb31-116">См. также</span><span class="sxs-lookup"><span data-stu-id="3eb31-116">See also</span></span>

- [<span data-ttu-id="3eb31-117">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="3eb31-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3eb31-118">Интерфейс ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="3eb31-118">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
