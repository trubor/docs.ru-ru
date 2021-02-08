---
description: 'Дополнительные сведения о: интерфейс ICorDebugHeapValue3'
title: Интерфейс ICorDebugHeapValue3
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3
helpviewer_keywords:
- ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type:
- apiref
ms.openlocfilehash: 2483f74e2cfc105fd23c37af6ada467f17b9556b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791469"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="ffaaf-103">Интерфейс ICorDebugHeapValue3</span><span class="sxs-lookup"><span data-stu-id="ffaaf-103">ICorDebugHeapValue3 Interface</span></span>

<span data-ttu-id="ffaaf-104">Предоставляет свойства блокировки монитора объектов.</span><span class="sxs-lookup"><span data-stu-id="ffaaf-104">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="ffaaf-105">Этот интерфейс расширяет интерфейсы ICorDebugHeapValue и ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="ffaaf-105">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ffaaf-106">Методы</span><span class="sxs-lookup"><span data-stu-id="ffaaf-106">Methods</span></span>  
  
|<span data-ttu-id="ffaaf-107">Метод</span><span class="sxs-lookup"><span data-stu-id="ffaaf-107">Method</span></span>|<span data-ttu-id="ffaaf-108">Описание</span><span class="sxs-lookup"><span data-stu-id="ffaaf-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ffaaf-109">Метод GetThreadOwningMonitorLock</span><span class="sxs-lookup"><span data-stu-id="ffaaf-109">GetThreadOwningMonitorLock Method</span></span>](icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="ffaaf-110">Возвращает управляемый поток, которому принадлежит блокировка монитора для этого объекта.</span><span class="sxs-lookup"><span data-stu-id="ffaaf-110">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="ffaaf-111">Метод GetMonitorEventWaitList</span><span class="sxs-lookup"><span data-stu-id="ffaaf-111">GetMonitorEventWaitList Method</span></span>](icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="ffaaf-112">Предоставляет упорядоченный список потоков, поставленных в очередь на событие, связанное с блокировкой монитора.</span><span class="sxs-lookup"><span data-stu-id="ffaaf-112">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffaaf-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="ffaaf-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ffaaf-114">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="ffaaf-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffaaf-115">Требования</span><span class="sxs-lookup"><span data-stu-id="ffaaf-115">Requirements</span></span>  

 <span data-ttu-id="ffaaf-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffaaf-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffaaf-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ffaaf-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffaaf-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffaaf-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffaaf-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffaaf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffaaf-120">См. также</span><span class="sxs-lookup"><span data-stu-id="ffaaf-120">See also</span></span>

- [<span data-ttu-id="ffaaf-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="ffaaf-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ffaaf-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="ffaaf-122">Debugging</span></span>](index.md)
