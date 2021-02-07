---
description: 'Дополнительные сведения о: интерфейс ICorDebugChain'
title: Интерфейс ICorDebugChain
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
ms.openlocfilehash: 391c9a3e54d06d303728da5ab7f105bc8e2558ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661211"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="947da-103">Интерфейс ICorDebugChain</span><span class="sxs-lookup"><span data-stu-id="947da-103">ICorDebugChain Interface</span></span>

<span data-ttu-id="947da-104">Представляет сегмент физического или логического стека вызовов.</span><span class="sxs-lookup"><span data-stu-id="947da-104">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="947da-105">Методы</span><span class="sxs-lookup"><span data-stu-id="947da-105">Methods</span></span>  
  
|<span data-ttu-id="947da-106">Метод</span><span class="sxs-lookup"><span data-stu-id="947da-106">Method</span></span>|<span data-ttu-id="947da-107">Описание</span><span class="sxs-lookup"><span data-stu-id="947da-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="947da-108">Метод EnumerateFrames</span><span class="sxs-lookup"><span data-stu-id="947da-108">EnumerateFrames Method</span></span>](icordebugchain-enumerateframes-method.md)|<span data-ttu-id="947da-109">Возвращает перечислитель, содержащий все управляемые кадры стека в цепочке, начиная с самого последнего кадра.</span><span class="sxs-lookup"><span data-stu-id="947da-109">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="947da-110">Метод GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="947da-110">GetActiveFrame Method</span></span>](icordebugchain-getactiveframe-method.md)|<span data-ttu-id="947da-111">Возвращает активный (то есть самый последний) кадр в цепочке.</span><span class="sxs-lookup"><span data-stu-id="947da-111">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="947da-112">Метод GetCallee</span><span class="sxs-lookup"><span data-stu-id="947da-112">GetCallee Method</span></span>](icordebugchain-getcallee-method.md)|<span data-ttu-id="947da-113">Возвращает цепочку, вызванную этой цепочкой.</span><span class="sxs-lookup"><span data-stu-id="947da-113">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="947da-114">Метод GetCaller</span><span class="sxs-lookup"><span data-stu-id="947da-114">GetCaller Method</span></span>](icordebugchain-getcaller-method.md)|<span data-ttu-id="947da-115">Возвращает цепочку, вызвавшую эту цепь.</span><span class="sxs-lookup"><span data-stu-id="947da-115">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="947da-116">Метод GetContext</span><span class="sxs-lookup"><span data-stu-id="947da-116">GetContext Method</span></span>](icordebugchain-getcontext-method.md)|<span data-ttu-id="947da-117">Не реализован.</span><span class="sxs-lookup"><span data-stu-id="947da-117">Not implemented.</span></span>|  
|[<span data-ttu-id="947da-118">Метод GetNext</span><span class="sxs-lookup"><span data-stu-id="947da-118">GetNext Method</span></span>](icordebugchain-getnext-method.md)|<span data-ttu-id="947da-119">Возвращает следующую цепь кадров для потока.</span><span class="sxs-lookup"><span data-stu-id="947da-119">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="947da-120">Метод GetPrevious</span><span class="sxs-lookup"><span data-stu-id="947da-120">GetPrevious Method</span></span>](icordebugchain-getprevious-method.md)|<span data-ttu-id="947da-121">Возвращает предыдущую цепочку кадров для потока.</span><span class="sxs-lookup"><span data-stu-id="947da-121">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="947da-122">Метод GetReason</span><span class="sxs-lookup"><span data-stu-id="947da-122">GetReason Method</span></span>](icordebugchain-getreason-method.md)|<span data-ttu-id="947da-123">Возвращает причину женесис данной вызывающей цепочки.</span><span class="sxs-lookup"><span data-stu-id="947da-123">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="947da-124">Метод GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="947da-124">GetRegisterSet Method</span></span>](icordebugchain-getregisterset-method.md)|<span data-ttu-id="947da-125">Возвращает набор регистров для активной части этой цепочки.</span><span class="sxs-lookup"><span data-stu-id="947da-125">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="947da-126">Метод GetStackRange</span><span class="sxs-lookup"><span data-stu-id="947da-126">GetStackRange Method</span></span>](icordebugchain-getstackrange-method.md)|<span data-ttu-id="947da-127">Возвращает диапазон адресов сегмента стека для этой цепочки.</span><span class="sxs-lookup"><span data-stu-id="947da-127">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="947da-128">Метод GetThread</span><span class="sxs-lookup"><span data-stu-id="947da-128">GetThread Method</span></span>](icordebugchain-getthread-method.md)|<span data-ttu-id="947da-129">Возвращает физический поток, частью которого является эта цепочка вызовов.</span><span class="sxs-lookup"><span data-stu-id="947da-129">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="947da-130">Метод IsManaged</span><span class="sxs-lookup"><span data-stu-id="947da-130">IsManaged Method</span></span>](icordebugchain-ismanaged-method.md)|<span data-ttu-id="947da-131">Возвращает значение, указывающее, выполняется ли в этой цепочке управляемый код.</span><span class="sxs-lookup"><span data-stu-id="947da-131">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="947da-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="947da-132">Remarks</span></span>  

 <span data-ttu-id="947da-133">Кадры стека в цепочке занимают непрерывное пространство стека и совместно используют один и тот же поток и контекст.</span><span class="sxs-lookup"><span data-stu-id="947da-133">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="947da-134">Цепочка может представлять как управляемые, так и неуправляемые цепочки кода.</span><span class="sxs-lookup"><span data-stu-id="947da-134">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="947da-135">Пустой `ICorDebugChain` экземпляр представляет собой неуправляемую цепочку кода.</span><span class="sxs-lookup"><span data-stu-id="947da-135">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="947da-136">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="947da-136">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="947da-137">Требования</span><span class="sxs-lookup"><span data-stu-id="947da-137">Requirements</span></span>  

 <span data-ttu-id="947da-138">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="947da-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="947da-139">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="947da-139">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="947da-140">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="947da-140">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="947da-141">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="947da-141">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="947da-142">См. также</span><span class="sxs-lookup"><span data-stu-id="947da-142">See also</span></span>

- [<span data-ttu-id="947da-143">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="947da-143">Debugging Interfaces</span></span>](debugging-interfaces.md)
