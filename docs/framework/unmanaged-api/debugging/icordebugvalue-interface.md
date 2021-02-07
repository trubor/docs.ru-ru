---
description: Дополнительные сведения о интерфейсе ICorDebugValue
title: Интерфейс ICorDebugValue
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
ms.openlocfilehash: cae8fdef5c1c49cbabc25d3d547cb5748a9eeee1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690319"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="2e688-103">Интерфейс ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="2e688-103">ICorDebugValue Interface</span></span>

<span data-ttu-id="2e688-104">Представляет значение в отлаживаемом процессе.</span><span class="sxs-lookup"><span data-stu-id="2e688-104">Represents a value in the process being debugged.</span></span> <span data-ttu-id="2e688-105">Значением может быть значение Read или Write.</span><span class="sxs-lookup"><span data-stu-id="2e688-105">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e688-106">Методы</span><span class="sxs-lookup"><span data-stu-id="2e688-106">Methods</span></span>  
  
|<span data-ttu-id="2e688-107">Метод</span><span class="sxs-lookup"><span data-stu-id="2e688-107">Method</span></span>|<span data-ttu-id="2e688-108">Описание</span><span class="sxs-lookup"><span data-stu-id="2e688-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e688-109">Метод CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2e688-109">CreateBreakpoint Method</span></span>](icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="2e688-110">Этот метод в настоящее время не реализован.</span><span class="sxs-lookup"><span data-stu-id="2e688-110">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="2e688-111">Метод GetAddress</span><span class="sxs-lookup"><span data-stu-id="2e688-111">GetAddress Method</span></span>](icordebugvalue-getaddress-method.md)|<span data-ttu-id="2e688-112">Возвращает адрес этого `ICorDebugValue` объекта, который находится в процессе отладки.</span><span class="sxs-lookup"><span data-stu-id="2e688-112">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="2e688-113">Метод GetSize</span><span class="sxs-lookup"><span data-stu-id="2e688-113">GetSize Method</span></span>](icordebugvalue-getsize-method.md)|<span data-ttu-id="2e688-114">Возвращает размер данного объекта в байтах `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="2e688-114">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="2e688-115">Метод GetType</span><span class="sxs-lookup"><span data-stu-id="2e688-115">GetType Method</span></span>](icordebugvalue-gettype-method.md)|<span data-ttu-id="2e688-116">Возвращает тип примитива этого `ICorDebugValue` объекта.</span><span class="sxs-lookup"><span data-stu-id="2e688-116">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e688-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="2e688-117">Remarks</span></span>  

 <span data-ttu-id="2e688-118">В общем случае владение объектом значения передается при его возврате.</span><span class="sxs-lookup"><span data-stu-id="2e688-118">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="2e688-119">Получатель отвечает за удаление ссылки из объекта после завершения работы с объектом.</span><span class="sxs-lookup"><span data-stu-id="2e688-119">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="2e688-120">В зависимости от того, откуда было получено значение, оно может остаться недействительным после возобновления процесса.</span><span class="sxs-lookup"><span data-stu-id="2e688-120">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="2e688-121">Поэтому в общем случае значение не должно удерживаться в вызове метода [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2e688-121">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e688-122">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="2e688-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e688-123">Требования</span><span class="sxs-lookup"><span data-stu-id="2e688-123">Requirements</span></span>  

 <span data-ttu-id="2e688-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e688-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e688-125">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e688-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e688-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e688-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e688-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e688-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e688-128">См. также</span><span class="sxs-lookup"><span data-stu-id="2e688-128">See also</span></span>

- [<span data-ttu-id="2e688-129">Интерфейс ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="2e688-129">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="2e688-130">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="2e688-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
