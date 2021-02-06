---
description: 'Дополнительные сведения о: интерфейс Икордебугхеапсегментенум'
title: Интерфейс ICorDebugHeapSegmentEnum
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: 614bae0ea5e3eb7816fdeec23a0dc7aa6e44801d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660886"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="f1988-103">Интерфейс ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="f1988-103">ICorDebugHeapSegmentEnum Interface</span></span>

<span data-ttu-id="f1988-104">Предоставляет перечислитель для областей памяти управляемой кучи.</span><span class="sxs-lookup"><span data-stu-id="f1988-104">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="f1988-105">Этот интерфейс является подклассом интерфейса ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="f1988-105">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1988-106">Методы</span><span class="sxs-lookup"><span data-stu-id="f1988-106">Methods</span></span>  
  
|<span data-ttu-id="f1988-107">Метод</span><span class="sxs-lookup"><span data-stu-id="f1988-107">Method</span></span>|<span data-ttu-id="f1988-108">Описание</span><span class="sxs-lookup"><span data-stu-id="f1988-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1988-109">Следующий метод</span><span class="sxs-lookup"><span data-stu-id="f1988-109">Next Method</span></span>](icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="f1988-110">Возвращает указанное число экземпляров [COR_SEGMENT](cor-segment-structure.md) , содержащих сведения о регионах управляемой кучи.</span><span class="sxs-lookup"><span data-stu-id="f1988-110">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1988-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="f1988-111">Remarks</span></span>  

 <span data-ttu-id="f1988-112">`ICorDebugHeapSegmentEnum`Интерфейс реализует интерфейс ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="f1988-112">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="f1988-113">`ICorDebugHeapSegmentEnum`Экземпляр заполняется [COR_SEGMENT](cor-segment-structure.md) экземплярами путем вызова метода [метод ICorDebugProcess5:: енумератехеапрегионс](icordebugprocess5-enumerateheapregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f1988-113">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_SEGMENT](cor-segment-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="f1988-114">Объекты [COR_SEGMENT](cor-segment-structure.md) в коллекции можно перечислить, вызвав метод [Икордебугхеапсегментенум:: Next](icordebugheapsegmentenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f1988-114">The [COR_SEGMENT](cor-segment-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="f1988-115">`ICorDebugHeapSegmentEnum`Объект Collection перечисляет все области памяти, которые могут содержать управляемые объекты, но не гарантирует, что управляемые объекты фактически находятся в этих регионах.</span><span class="sxs-lookup"><span data-stu-id="f1988-115">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="f1988-116">Он может включать сведения о пустых или зарезервированных регионах памяти.</span><span class="sxs-lookup"><span data-stu-id="f1988-116">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1988-117">Требования</span><span class="sxs-lookup"><span data-stu-id="f1988-117">Requirements</span></span>  

 <span data-ttu-id="f1988-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1988-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1988-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1988-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1988-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1988-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1988-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1988-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1988-122">См. также</span><span class="sxs-lookup"><span data-stu-id="f1988-122">See also</span></span>

- [<span data-ttu-id="f1988-123">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="f1988-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
