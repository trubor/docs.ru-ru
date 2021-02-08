---
description: 'Дополнительные сведения о: интерфейс ICorDebugGCReferenceEnum'
title: Интерфейс ICorDebugGCReferenceEnum
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: ad4a61cdc2b30fb4c8e2be500eae878327c6b449
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801297"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="b6af3-103">Интерфейс ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="b6af3-103">ICorDebugGCReferenceEnum Interface</span></span>

<span data-ttu-id="b6af3-104">Предоставляет перечислитель для объектов, для которых будет выполнена сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="b6af3-104">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6af3-105">Методы</span><span class="sxs-lookup"><span data-stu-id="b6af3-105">Methods</span></span>  
  
|<span data-ttu-id="b6af3-106">Метод</span><span class="sxs-lookup"><span data-stu-id="b6af3-106">Method</span></span>|<span data-ttu-id="b6af3-107">Описание</span><span class="sxs-lookup"><span data-stu-id="b6af3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6af3-108">Следующий метод</span><span class="sxs-lookup"><span data-stu-id="b6af3-108">Next Method</span></span>](icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="b6af3-109">Возвращает указанное число экземпляров [COR_GC_REFERENCE](cor-gc-reference-structure.md) , содержащих сведения об объектах, которые будут собираться сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="b6af3-109">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6af3-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="b6af3-110">Remarks</span></span>  

 <span data-ttu-id="b6af3-111">`ICorDebugGCReferenceEnum`Интерфейс реализует интерфейс "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="b6af3-111">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="b6af3-112">`ICorDebugGCReferenceEnum`Экземпляр заполняется [COR_GC_REFERENCE](cor-gc-reference-structure.md) экземплярами путем вызова метода [метод ICorDebugProcess5:: енумератегкреференцес](icordebugprocess5-enumerategcreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b6af3-112">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="b6af3-113">[COR_GC_REFERENCE](cor-gc-reference-structure.md) объекты можно перечислить, вызвав метод [Икордебуггкреференце:: Next](icordebuggcreferenceenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b6af3-113">[COR_GC_REFERENCE](cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="b6af3-114">[COR_GC_REFERENCE](cor-gc-reference-structure.md) объекты в коллекции, заполненной этим методом, представляют три вида объектов:</span><span class="sxs-lookup"><span data-stu-id="b6af3-114">The [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="b6af3-115">Объекты из всех управляемых стеков.</span><span class="sxs-lookup"><span data-stu-id="b6af3-115">Objects from all managed stacks.</span></span> <span data-ttu-id="b6af3-116">Сюда входят динамические ссылки в управляемом коде, а также объекты, созданные средой CLR.</span><span class="sxs-lookup"><span data-stu-id="b6af3-116">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="b6af3-117">Объекты из таблицы Handle.</span><span class="sxs-lookup"><span data-stu-id="b6af3-117">Objects from the handle table.</span></span> <span data-ttu-id="b6af3-118">Это включает в себя строгие ссылки ( `HNDTYPE_STRONG` и `HNDTYPE_REFCOUNT` ) и статические переменные в модуле.</span><span class="sxs-lookup"><span data-stu-id="b6af3-118">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="b6af3-119">Объекты из очереди метода завершения.</span><span class="sxs-lookup"><span data-stu-id="b6af3-119">Objects from the finalizer queue.</span></span> <span data-ttu-id="b6af3-120">Очередь метода завершения помещает объекты в корни до запуска метода завершения.</span><span class="sxs-lookup"><span data-stu-id="b6af3-120">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6af3-121">Требования</span><span class="sxs-lookup"><span data-stu-id="b6af3-121">Requirements</span></span>  

 <span data-ttu-id="b6af3-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6af3-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6af3-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6af3-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6af3-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6af3-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6af3-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6af3-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6af3-126">См. также</span><span class="sxs-lookup"><span data-stu-id="b6af3-126">See also</span></span>

- [<span data-ttu-id="b6af3-127">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="b6af3-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
