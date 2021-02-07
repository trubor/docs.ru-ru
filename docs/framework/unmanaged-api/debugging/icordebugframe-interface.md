---
description: Дополнительные сведения о интерфейсе ICorDebugFrame
title: Интерфейс ICorDebugFrame
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: d0fd629672d535f89fe78c178032937443d9dfbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692853"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="fc2f8-103">Интерфейс ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="fc2f8-103">ICorDebugFrame Interface</span></span>

<span data-ttu-id="fc2f8-104">Представляет кадр текущего стека.</span><span class="sxs-lookup"><span data-stu-id="fc2f8-104">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc2f8-105">Методы</span><span class="sxs-lookup"><span data-stu-id="fc2f8-105">Methods</span></span>  
  
|<span data-ttu-id="fc2f8-106">Метод</span><span class="sxs-lookup"><span data-stu-id="fc2f8-106">Method</span></span>|<span data-ttu-id="fc2f8-107">Описание</span><span class="sxs-lookup"><span data-stu-id="fc2f8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc2f8-108">Метод CreateStepper</span><span class="sxs-lookup"><span data-stu-id="fc2f8-108">CreateStepper Method</span></span>](icordebugframe-createstepper-method.md)|<span data-ttu-id="fc2f8-109">Получает объект ICorDebugStepper, выполняющий пошаговые операции по отношению к этому `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="fc2f8-109">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="fc2f8-110">Метод GetCallee</span><span class="sxs-lookup"><span data-stu-id="fc2f8-110">GetCallee Method</span></span>](icordebugframe-getcallee-method.md)|<span data-ttu-id="fc2f8-111">Возвращает указатель на объект `ICorDebugFrame` в текущей цепочке, который вызвал этот кадр, или возвращает значение null, если это внутренняя рамка в цепочке.</span><span class="sxs-lookup"><span data-stu-id="fc2f8-111">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="fc2f8-112">Метод GetCaller</span><span class="sxs-lookup"><span data-stu-id="fc2f8-112">GetCaller Method</span></span>](icordebugframe-getcaller-method.md)|<span data-ttu-id="fc2f8-113">Возвращает указатель на объект `ICorDebugFrame` в текущей цепочке, вызвавшей этот кадр, или возвращает значение null, если это самый внешний кадр в цепочке.</span><span class="sxs-lookup"><span data-stu-id="fc2f8-113">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="fc2f8-114">Метод GetChain</span><span class="sxs-lookup"><span data-stu-id="fc2f8-114">GetChain Method</span></span>](icordebugframe-getchain-method.md)|<span data-ttu-id="fc2f8-115">Возвращает указатель на ICorDebugChain, частью которого `ICorDebugFrame` является.</span><span class="sxs-lookup"><span data-stu-id="fc2f8-115">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="fc2f8-116">Метод GetCode</span><span class="sxs-lookup"><span data-stu-id="fc2f8-116">GetCode Method</span></span>](icordebugframe-getcode-method.md)|<span data-ttu-id="fc2f8-117">Возвращает указатель на ICorDebugCode, связанный с этим кадром стека.</span><span class="sxs-lookup"><span data-stu-id="fc2f8-117">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="fc2f8-118">Метод GetFunction</span><span class="sxs-lookup"><span data-stu-id="fc2f8-118">GetFunction Method</span></span>](icordebugframe-getfunction-method.md)|<span data-ttu-id="fc2f8-119">Возвращает указатель на ICorDebugFunction, содержащий код, связанный с этим кадром стека.</span><span class="sxs-lookup"><span data-stu-id="fc2f8-119">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="fc2f8-120">Метод GetFunctionToken</span><span class="sxs-lookup"><span data-stu-id="fc2f8-120">GetFunctionToken Method</span></span>](icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="fc2f8-121">Возвращает маркер метаданных для функции, которая содержит код, связанный с этим кадром стека.</span><span class="sxs-lookup"><span data-stu-id="fc2f8-121">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="fc2f8-122">Метод GetStackRange</span><span class="sxs-lookup"><span data-stu-id="fc2f8-122">GetStackRange Method</span></span>](icordebugframe-getstackrange-method.md)|<span data-ttu-id="fc2f8-123">Возвращает диапазон абсолютных адресов кадра стека, представленного этим объектом `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="fc2f8-123">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc2f8-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="fc2f8-124">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc2f8-125">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="fc2f8-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc2f8-126">Требования</span><span class="sxs-lookup"><span data-stu-id="fc2f8-126">Requirements</span></span>  

 <span data-ttu-id="fc2f8-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc2f8-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc2f8-128">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc2f8-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc2f8-129">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc2f8-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc2f8-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc2f8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc2f8-131">См. также</span><span class="sxs-lookup"><span data-stu-id="fc2f8-131">See also</span></span>

- [<span data-ttu-id="fc2f8-132">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="fc2f8-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
