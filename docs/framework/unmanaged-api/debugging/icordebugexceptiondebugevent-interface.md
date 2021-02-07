---
description: 'Дополнительные сведения о: интерфейс Икордебужексцептиондебужевент'
title: Интерфейс ICorDebugExceptionDebugEvent
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: eacaa344763fb77faef5f66282809d741f017b37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693425"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="ba546-103">Интерфейс ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="ba546-103">ICorDebugExceptionDebugEvent Interface</span></span>

<span data-ttu-id="ba546-104">Расширяет интерфейс [ICorDebugDebugEvent](icordebugdebugevent-interface.md) для поддержки событий исключения.</span><span class="sxs-lookup"><span data-stu-id="ba546-104">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba546-105">Методы</span><span class="sxs-lookup"><span data-stu-id="ba546-105">Methods</span></span>  
  
|<span data-ttu-id="ba546-106">Метод</span><span class="sxs-lookup"><span data-stu-id="ba546-106">Method</span></span>|<span data-ttu-id="ba546-107">Описание</span><span class="sxs-lookup"><span data-stu-id="ba546-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ba546-108">Метод GetFlags</span><span class="sxs-lookup"><span data-stu-id="ba546-108">GetFlags Method</span></span>](icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="ba546-109">Возвращает флаг, указывающий, может ли исключение быть перехвачено.</span><span class="sxs-lookup"><span data-stu-id="ba546-109">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="ba546-110">Метод GetNativeIP</span><span class="sxs-lookup"><span data-stu-id="ba546-110">GetNativeIP Method</span></span>](icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="ba546-111">Получает указатель собственного интерфейса для этого события отладки исключения.</span><span class="sxs-lookup"><span data-stu-id="ba546-111">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="ba546-112">Метод GetStackPointer</span><span class="sxs-lookup"><span data-stu-id="ba546-112">GetStackPointer Method</span></span>](icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="ba546-113">Получает указатель стека для этого события отладки исключения.</span><span class="sxs-lookup"><span data-stu-id="ba546-113">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba546-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="ba546-114">Remarks</span></span>  

 <span data-ttu-id="ba546-115">Интерфейс `ICorDebugExceptionDebugEvent` реализуется с помощью следующих типов событий:</span><span class="sxs-lookup"><span data-stu-id="ba546-115">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="ba546-116">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="ba546-116">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="ba546-117">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="ba546-117">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="ba546-118">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="ba546-118">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="ba546-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="ba546-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="ba546-120">Этот интерфейс доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="ba546-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="ba546-121">Попытка вызова метода `QueryInterface` для получения указателя интерфейса возвращает `E_NOINTERFACE` для сценариев ICorDebug вне .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ba546-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba546-122">Требования</span><span class="sxs-lookup"><span data-stu-id="ba546-122">Requirements</span></span>  

 <span data-ttu-id="ba546-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba546-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba546-124">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba546-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba546-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba546-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba546-126">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba546-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba546-127">См. также</span><span class="sxs-lookup"><span data-stu-id="ba546-127">See also</span></span>

- [<span data-ttu-id="ba546-128">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="ba546-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ba546-129">Отладка</span><span class="sxs-lookup"><span data-stu-id="ba546-129">Debugging</span></span>](index.md)
