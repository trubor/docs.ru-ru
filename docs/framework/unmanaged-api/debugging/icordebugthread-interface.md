---
description: Дополнительные сведения о интерфейсе ICorDebugThread
title: Интерфейс ICorDebugThread
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
ms.openlocfilehash: 7e16fa2a82a004a5c85d60a278cdd14df6ab2300
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658832"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="92201-103">Интерфейс ICorDebugThread</span><span class="sxs-lookup"><span data-stu-id="92201-103">ICorDebugThread Interface</span></span>

<span data-ttu-id="92201-104">Представляет поток в процессе.</span><span class="sxs-lookup"><span data-stu-id="92201-104">Represents a thread in a process.</span></span> <span data-ttu-id="92201-105">Время существования экземпляра `ICorDebugThread` равно времени существования потока, который он представляет.</span><span class="sxs-lookup"><span data-stu-id="92201-105">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92201-106">Методы</span><span class="sxs-lookup"><span data-stu-id="92201-106">Methods</span></span>  
  
|<span data-ttu-id="92201-107">Метод</span><span class="sxs-lookup"><span data-stu-id="92201-107">Method</span></span>|<span data-ttu-id="92201-108">Описание</span><span class="sxs-lookup"><span data-stu-id="92201-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92201-109">Метод ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="92201-109">ClearCurrentException Method</span></span>](icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="92201-110">Этот метод не реализован.</span><span class="sxs-lookup"><span data-stu-id="92201-110">This method is not implemented.</span></span> <span data-ttu-id="92201-111">Не используйте его.</span><span class="sxs-lookup"><span data-stu-id="92201-111">Do not use it.</span></span>|  
|[<span data-ttu-id="92201-112">Метод CreateEval</span><span class="sxs-lookup"><span data-stu-id="92201-112">CreateEval Method</span></span>](icordebugthread-createeval-method.md)|<span data-ttu-id="92201-113">Создает объект ICorDebugEval, который работает с этим объектом `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="92201-113">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="92201-114">Метод CreateStepper</span><span class="sxs-lookup"><span data-stu-id="92201-114">CreateStepper Method</span></span>](icordebugthread-createstepper-method.md)|<span data-ttu-id="92201-115">Создает объект ICorDebugStepper, позволяющий пошаговое выполнение активного кадра в этом объекте `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="92201-115">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="92201-116">Метод EnumerateChains</span><span class="sxs-lookup"><span data-stu-id="92201-116">EnumerateChains Method</span></span>](icordebugthread-enumeratechains-method.md)|<span data-ttu-id="92201-117">Получает указатель интерфейса на перечислитель Икордебугчаиненум, который содержит все цепочки стека в этом `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="92201-117">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="92201-118">Метод GetActiveChain</span><span class="sxs-lookup"><span data-stu-id="92201-118">GetActiveChain Method</span></span>](icordebugthread-getactivechain-method.md)|<span data-ttu-id="92201-119">Возвращает указатель интерфейса на активный ICorDebugChain для этого объекта `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="92201-119">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="92201-120">Метод GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="92201-120">GetActiveFrame Method</span></span>](icordebugthread-getactiveframe-method.md)|<span data-ttu-id="92201-121">Получает указатель интерфейса на активный объект ICorDebugFrame для этого `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="92201-121">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="92201-122">Метод GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="92201-122">GetAppDomain Method</span></span>](icordebugthread-getappdomain-method.md)|<span data-ttu-id="92201-123">Возвращает указатель интерфейса на домен приложения, в котором выполняется в `ICorDebugThread` данный момент.</span><span class="sxs-lookup"><span data-stu-id="92201-123">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="92201-124">Метод GetCurrentException</span><span class="sxs-lookup"><span data-stu-id="92201-124">GetCurrentException Method</span></span>](icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="92201-125">Возвращает указатель интерфейса на объект ICorDebugValue, представляющий исключение, которое в данный момент вызывается управляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="92201-125">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="92201-126">Метод GetDebugState</span><span class="sxs-lookup"><span data-stu-id="92201-126">GetDebugState Method</span></span>](icordebugthread-getdebugstate-method.md)|<span data-ttu-id="92201-127">Возвращает значение Кордебугсреадстате, описывающее текущее состояние отладки этого объекта `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="92201-127">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="92201-128">Метод GetHandle</span><span class="sxs-lookup"><span data-stu-id="92201-128">GetHandle Method</span></span>](icordebugthread-gethandle-method.md)|<span data-ttu-id="92201-129">Возвращает текущий обработчик для активной части этого объекта `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="92201-129">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="92201-130">Метод GetID</span><span class="sxs-lookup"><span data-stu-id="92201-130">GetID Method</span></span>](icordebugthread-getid-method.md)|<span data-ttu-id="92201-131">Возвращает идентификатор текущей операционной системы активной части `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="92201-131">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="92201-132">Метод GetObject</span><span class="sxs-lookup"><span data-stu-id="92201-132">GetObject Method</span></span>](icordebugthread-getobject-method.md)|<span data-ttu-id="92201-133">Возвращает указатель интерфейса на поток среды CLR.</span><span class="sxs-lookup"><span data-stu-id="92201-133">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="92201-134">Метод GetProcess</span><span class="sxs-lookup"><span data-stu-id="92201-134">GetProcess Method</span></span>](icordebugthread-getprocess-method.md)|<span data-ttu-id="92201-135">Возвращает указатель интерфейса для процесса, частью которого является эта `ICorDebugThread` форма.</span><span class="sxs-lookup"><span data-stu-id="92201-135">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="92201-136">Метод GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="92201-136">GetRegisterSet Method</span></span>](icordebugthread-getregisterset-method.md)|<span data-ttu-id="92201-137">Возвращает указатель интерфейса на набор регистров, связанный с этим `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="92201-137">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="92201-138">Метод GetUserState</span><span class="sxs-lookup"><span data-stu-id="92201-138">GetUserState Method</span></span>](icordebugthread-getuserstate-method.md)|<span data-ttu-id="92201-139">Возвращает побитовое сочетание значений Кордебугусерстате, описывающих текущее состояние этого объекта `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="92201-139">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="92201-140">Метод SetDebugState</span><span class="sxs-lookup"><span data-stu-id="92201-140">SetDebugState Method</span></span>](icordebugthread-setdebugstate-method.md)|<span data-ttu-id="92201-141">Задает побитовое сочетание `CorDebugThreadState` значений, описывающих состояние отладки этого объекта `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="92201-141">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92201-142">Remarks</span><span class="sxs-lookup"><span data-stu-id="92201-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92201-143">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="92201-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92201-144">Требования</span><span class="sxs-lookup"><span data-stu-id="92201-144">Requirements</span></span>  

 <span data-ttu-id="92201-145">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92201-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92201-146">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92201-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92201-147">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92201-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92201-148">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92201-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92201-149">См. также</span><span class="sxs-lookup"><span data-stu-id="92201-149">See also</span></span>

- [<span data-ttu-id="92201-150">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="92201-150">Debugging Interfaces</span></span>](debugging-interfaces.md)
