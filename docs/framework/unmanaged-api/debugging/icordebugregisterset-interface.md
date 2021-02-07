---
description: 'Дополнительные сведения о: интерфейс ICorDebugRegisterSet'
title: Интерфейс ICorDebugRegisterSet
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
ms.openlocfilehash: 7d888e9e395e9f5fa88c6a6d96b2b8e3171ef4ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690786"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="b6c0e-103">Интерфейс ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="b6c0e-103">ICorDebugRegisterSet Interface</span></span>

<span data-ttu-id="b6c0e-104">Представляет набор регистров, доступных на компьютере, который выполняет код в данный момент.</span><span class="sxs-lookup"><span data-stu-id="b6c0e-104">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6c0e-105">Методы</span><span class="sxs-lookup"><span data-stu-id="b6c0e-105">Methods</span></span>  
  
|<span data-ttu-id="b6c0e-106">Метод</span><span class="sxs-lookup"><span data-stu-id="b6c0e-106">Method</span></span>|<span data-ttu-id="b6c0e-107">Описание</span><span class="sxs-lookup"><span data-stu-id="b6c0e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6c0e-108">Метод GetRegisters</span><span class="sxs-lookup"><span data-stu-id="b6c0e-108">GetRegisters Method</span></span>](icordebugregisterset-getregisters-method.md)|<span data-ttu-id="b6c0e-109">Возвращает значение каждого регистра (на компьютере, выполняющем в данный момент код), который задается битовой маской.</span><span class="sxs-lookup"><span data-stu-id="b6c0e-109">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="b6c0e-110">Метод GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="b6c0e-110">GetRegistersAvailable Method</span></span>](icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="b6c0e-111">Возвращает битовую маску, указывающую, какие регистры в данный `ICorDebugRegisterSet` момент доступны.</span><span class="sxs-lookup"><span data-stu-id="b6c0e-111">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="b6c0e-112">Метод GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="b6c0e-112">GetThreadContext Method</span></span>](icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="b6c0e-113">Возвращает контекст текущего потока.</span><span class="sxs-lookup"><span data-stu-id="b6c0e-113">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="b6c0e-114">Метод SetRegisters</span><span class="sxs-lookup"><span data-stu-id="b6c0e-114">SetRegisters Method</span></span>](icordebugregisterset-setregisters-method.md)|<span data-ttu-id="b6c0e-115">Не реализовано для платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="b6c0e-115">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="b6c0e-116">Метод SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="b6c0e-116">SetThreadContext Method</span></span>](icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="b6c0e-117">Не реализовано для платформа .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="b6c0e-117">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6c0e-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="b6c0e-118">Remarks</span></span>  

 <span data-ttu-id="b6c0e-119">`ICorDebugRegisterSet`Интерфейс поддерживает только 32-разрядные регистры.</span><span class="sxs-lookup"><span data-stu-id="b6c0e-119">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="b6c0e-120">Используйте интерфейс [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) на платформах, таких как IA-64, требующих дополнительных регистров.</span><span class="sxs-lookup"><span data-stu-id="b6c0e-120">Use the [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6c0e-121">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="b6c0e-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6c0e-122">Требования</span><span class="sxs-lookup"><span data-stu-id="b6c0e-122">Requirements</span></span>  

 <span data-ttu-id="b6c0e-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6c0e-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6c0e-124">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6c0e-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6c0e-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6c0e-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6c0e-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6c0e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6c0e-127">См. также</span><span class="sxs-lookup"><span data-stu-id="b6c0e-127">See also</span></span>

- [<span data-ttu-id="b6c0e-128">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="b6c0e-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b6c0e-129">Интерфейс ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="b6c0e-129">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
