---
description: 'Дополнительные сведения о: интерфейс ICorProfilerInfo10'
title: Интерфейс ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: fd24491cb1ca55ad48137522c63e78e6387d33e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753293"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="756c1-103">Интерфейс ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="756c1-103">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="756c1-104">Подкласс [ICorProfilerInfo9](icorprofilerinfo9-interface.md) , предоставляющий методы для изменения Il функции, запроса сведений из среды выполнения, а также приостановки и возобновления работы среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="756c1-104">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="756c1-105">Методы</span><span class="sxs-lookup"><span data-stu-id="756c1-105">Methods</span></span>  

| <span data-ttu-id="756c1-106">Метод</span><span class="sxs-lookup"><span data-stu-id="756c1-106">Method</span></span>|<span data-ttu-id="756c1-107">Описание</span><span class="sxs-lookup"><span data-stu-id="756c1-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="756c1-108">Метод EnumerateObjectReferences</span><span class="sxs-lookup"><span data-stu-id="756c1-108">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="756c1-109">При наличии ObjectID, callback и Клиентдата перечисляет ссылки на все объекты (если таковые имеются).</span><span class="sxs-lookup"><span data-stu-id="756c1-109">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="756c1-110">Метод IsFrozenObject</span><span class="sxs-lookup"><span data-stu-id="756c1-110">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="756c1-111">Определяет, находится ли объект в сегменте, доступном только для чтения.</span><span class="sxs-lookup"><span data-stu-id="756c1-111">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="756c1-112">Метод GetLOHObjectSizeThreshold</span><span class="sxs-lookup"><span data-stu-id="756c1-112">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="756c1-113">Возвращает значение заданного порога LOH.</span><span class="sxs-lookup"><span data-stu-id="756c1-113">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="756c1-114">Метод RequestReJITWithInliners</span><span class="sxs-lookup"><span data-stu-id="756c1-114">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="756c1-115">Режитс запрошенные методы, а также любые запрашиваются методы.</span><span class="sxs-lookup"><span data-stu-id="756c1-115">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="756c1-116">Метод SuspendRuntime</span><span class="sxs-lookup"><span data-stu-id="756c1-116">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="756c1-117">Приостанавливает выполнение среды выполнения без выполнения сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="756c1-117">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="756c1-118">Метод ResumeRuntime</span><span class="sxs-lookup"><span data-stu-id="756c1-118">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="756c1-119">Возобновляет работу среды выполнения без выполнения сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="756c1-119">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="756c1-120">Требования</span><span class="sxs-lookup"><span data-stu-id="756c1-120">Requirements</span></span>  

<span data-ttu-id="756c1-121">**Платформы:** См. раздел [Поддерживаемые операционные системы .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="756c1-121">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="756c1-122">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="756c1-122">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="756c1-123">**Версии .NET:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="756c1-123">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="756c1-124">См. также</span><span class="sxs-lookup"><span data-stu-id="756c1-124">See also</span></span>

- [<span data-ttu-id="756c1-125">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="756c1-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
