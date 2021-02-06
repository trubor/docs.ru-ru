---
description: 'Дополнительные сведения о: интерфейс Икордебугхеапенум'
title: Интерфейс ICorDebugHeapEnum
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
ms.openlocfilehash: c8a2f46bf412e2c4b2fe43d3eb50169191f40445
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660899"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="72de0-103">Интерфейс ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="72de0-103">ICorDebugHeapEnum Interface</span></span>

<span data-ttu-id="72de0-104">Предоставляет перечислитель для объектов в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="72de0-104">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="72de0-105">Этот интерфейс является подклассом интерфейса ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="72de0-105">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72de0-106">Методы</span><span class="sxs-lookup"><span data-stu-id="72de0-106">Methods</span></span>  
  
|<span data-ttu-id="72de0-107">Метод</span><span class="sxs-lookup"><span data-stu-id="72de0-107">Method</span></span>|<span data-ttu-id="72de0-108">Описание</span><span class="sxs-lookup"><span data-stu-id="72de0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72de0-109">Следующий метод</span><span class="sxs-lookup"><span data-stu-id="72de0-109">Next Method</span></span>](icordebugheapenum-next-method.md)|<span data-ttu-id="72de0-110">Возвращает указанное число экземпляров [COR_HEAPOBJECT](cor-heapobject-structure.md) , содержащих сведения об объектах в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="72de0-110">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72de0-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="72de0-111">Remarks</span></span>  

 <span data-ttu-id="72de0-112">`ICorDebugHeapEnum`Интерфейс реализует интерфейс ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="72de0-112">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="72de0-113">`ICorDebugHeapEnum`Экземпляр заполняется [COR_HEAPOBJECT](cor-heapobject-structure.md) экземплярами путем вызова метода [метод ICorDebugProcess5:: енумератехеап](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="72de0-113">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="72de0-114">Каждый экземпляр [COR_HEAPOBJECT](cor-heapobject-structure.md) в коллекции представляет собой либо динамический объект в куче, либо объект, который не является корневым для какого-либо объекта, но еще не был собран сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="72de0-114">Each [COR_HEAPOBJECT](cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="72de0-115">Объекты [COR_HEAPOBJECT](cor-heapobject-structure.md) в коллекции можно перечислить, вызвав метод [Икордебугхеапенум:: Next](icordebugheapenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="72de0-115">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72de0-116">Требования</span><span class="sxs-lookup"><span data-stu-id="72de0-116">Requirements</span></span>  

 <span data-ttu-id="72de0-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72de0-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72de0-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72de0-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72de0-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72de0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72de0-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72de0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72de0-121">См. также</span><span class="sxs-lookup"><span data-stu-id="72de0-121">See also</span></span>

- [<span data-ttu-id="72de0-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="72de0-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
