---
description: 'Дополнительные сведения о: интерфейс ICorDebugExceptionObjectCallStackEnum'
title: Интерфейс ICorDebugExceptionObjectCallStackEnum
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
ms.openlocfilehash: c72f4299bf3ebc5de2d2ed196801d93ff5fe4356
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693360"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="3db8a-103">Интерфейс ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="3db8a-103">ICorDebugExceptionObjectCallStackEnum Interface</span></span>

<span data-ttu-id="3db8a-104">Предоставляет перечислитель для сведений стека вызовов, встроенных в объект исключения.</span><span class="sxs-lookup"><span data-stu-id="3db8a-104">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="3db8a-105">Этот интерфейс является подклассом интерфейса ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="3db8a-105">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3db8a-106">Методы</span><span class="sxs-lookup"><span data-stu-id="3db8a-106">Methods</span></span>  
  
|<span data-ttu-id="3db8a-107">Метод</span><span class="sxs-lookup"><span data-stu-id="3db8a-107">Method</span></span>|<span data-ttu-id="3db8a-108">Описание</span><span class="sxs-lookup"><span data-stu-id="3db8a-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3db8a-109">ICorDebugExceptionObjectCallStackEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="3db8a-109">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="3db8a-110">Возвращает указанное число объектов [кордебужексцептионобжектстаккфраме](cordebugexceptionobjectstackframe-structure.md) , содержащих сведения о стеке вызовов объекта исключения.</span><span class="sxs-lookup"><span data-stu-id="3db8a-110">Gets a specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3db8a-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="3db8a-111">Remarks</span></span>  

 <span data-ttu-id="3db8a-112">`ICorDebugExceptionObjectCallStackEnum`Интерфейс реализует интерфейс ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="3db8a-112">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="3db8a-113">`ICorDebugExceptionObjectCallStackEnum`Экземпляр заполняется объектами [кордебужексцептионобжектстаккфраме](cordebugexceptionobjectstackframe-structure.md) путем вызова метода [ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3db8a-113">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="3db8a-114">Элементы стека вызовов в коллекции можно перечислить, вызвав метод [ICorDebugExceptionObjectCallStackEnum:: Next.](icordebugexceptionobjectcallstackenum-next-method.md)</span><span class="sxs-lookup"><span data-stu-id="3db8a-114">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3db8a-115">Требования</span><span class="sxs-lookup"><span data-stu-id="3db8a-115">Requirements</span></span>  

 <span data-ttu-id="3db8a-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3db8a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3db8a-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3db8a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3db8a-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3db8a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3db8a-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3db8a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db8a-120">См. также</span><span class="sxs-lookup"><span data-stu-id="3db8a-120">See also</span></span>

- [<span data-ttu-id="3db8a-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="3db8a-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3db8a-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="3db8a-122">Debugging</span></span>](index.md)
