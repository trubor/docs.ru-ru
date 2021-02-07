---
description: 'Дополнительные сведения о методе: Икордебужексцептиондебужевент:: Жетстаккпоинтер'
title: Метод ICorDebugExceptionDebugEvent::GetStackPointer
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 5a62a5eb54fff1e94beebc222e3f18cc4655040f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693451"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="af1b6-103">Метод ICorDebugExceptionDebugEvent::GetStackPointer</span><span class="sxs-lookup"><span data-stu-id="af1b6-103">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>

<span data-ttu-id="af1b6-104">Получает указатель стека для этого события отладки исключения.</span><span class="sxs-lookup"><span data-stu-id="af1b6-104">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af1b6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="af1b6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af1b6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="af1b6-106">Parameters</span></span>  

 `pStackPointer`  
 <span data-ttu-id="af1b6-107">[out] Указатель на адрес указателя стека для этого события отладки исключения.</span><span class="sxs-lookup"><span data-stu-id="af1b6-107">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="af1b6-108">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="af1b6-108">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af1b6-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="af1b6-109">Remarks</span></span>  

 <span data-ttu-id="af1b6-110">Смысл этого указателя стека зависит от типа события, как показано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="af1b6-110">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="af1b6-111">Тип события</span><span class="sxs-lookup"><span data-stu-id="af1b6-111">Event type</span></span>|<span data-ttu-id="af1b6-112">Смысл значения `pStackPointer`</span><span class="sxs-lookup"><span data-stu-id="af1b6-112">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="af1b6-113">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="af1b6-113">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="af1b6-114">Указатель стека для фрейма, вызвавшего исключение.</span><span class="sxs-lookup"><span data-stu-id="af1b6-114">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="af1b6-115">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="af1b6-115">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="af1b6-116">Указатель стека для фрейма пользовательского кода, ближайшего к точке вызванного исключения.</span><span class="sxs-lookup"><span data-stu-id="af1b6-116">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="af1b6-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="af1b6-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="af1b6-118">Указатель стека для фрейма, содержащего обработчик catch.</span><span class="sxs-lookup"><span data-stu-id="af1b6-118">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="af1b6-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="af1b6-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="af1b6-120">Параметр `pStackPointer` имеет значение **NULL**.</span><span class="sxs-lookup"><span data-stu-id="af1b6-120">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="af1b6-121">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="af1b6-121">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="af1b6-122">Тип события доступен в методе [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="af1b6-122">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af1b6-123">Требования</span><span class="sxs-lookup"><span data-stu-id="af1b6-123">Requirements</span></span>  

 <span data-ttu-id="af1b6-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af1b6-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af1b6-125">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af1b6-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af1b6-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af1b6-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af1b6-127">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af1b6-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af1b6-128">См. также</span><span class="sxs-lookup"><span data-stu-id="af1b6-128">See also</span></span>

- [<span data-ttu-id="af1b6-129">Интерфейс ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="af1b6-129">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="af1b6-130">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="af1b6-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
