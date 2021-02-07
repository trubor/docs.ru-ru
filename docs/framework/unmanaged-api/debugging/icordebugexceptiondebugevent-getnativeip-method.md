---
description: 'Дополнительные сведения о методе: Икордебужексцептиондебужевент:: Жетнативеип'
title: Метод ICorDebugExceptionDebugEvent::GetNativeIP
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 89bda36efc59e2462634c3d8a3a5835c9d4b3354
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693464"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="30c61-103">Метод ICorDebugExceptionDebugEvent::GetNativeIP</span><span class="sxs-lookup"><span data-stu-id="30c61-103">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>

<span data-ttu-id="30c61-104">Получает собственный указатель инструкции для этого события отладки исключения.</span><span class="sxs-lookup"><span data-stu-id="30c61-104">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30c61-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="30c61-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30c61-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="30c61-106">Parameters</span></span>  

 `pIP`  
 <span data-ttu-id="30c61-107">[out] Указатель на указатель инструкции для этого события отладки исключения.</span><span class="sxs-lookup"><span data-stu-id="30c61-107">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="30c61-108">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="30c61-108">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30c61-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="30c61-109">Remarks</span></span>  

 <span data-ttu-id="30c61-110">Смысл этого указателя инструкции стека зависит от типа события, как показано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="30c61-110">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="30c61-111">Тип события</span><span class="sxs-lookup"><span data-stu-id="30c61-111">Event type</span></span>|<span data-ttu-id="30c61-112">Смысл значения `pStackPointer`</span><span class="sxs-lookup"><span data-stu-id="30c61-112">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="30c61-113">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="30c61-113">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="30c61-114">Адрес инструкции со сбоем.</span><span class="sxs-lookup"><span data-stu-id="30c61-114">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="30c61-115">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="30c61-115">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="30c61-116">Адрес кода в кадре, указанный методом [жетстаккпоинтер](icordebugexceptiondebugevent-getstackpointer-method.md) , где выполнение возобновится, если исключение не было вызвано.</span><span class="sxs-lookup"><span data-stu-id="30c61-116">The code address in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="30c61-117">Исключение может вызывать или не вызывать другой код, например блок catch предложения `try/catch/finally`, выполняемый в этом фрейме.</span><span class="sxs-lookup"><span data-stu-id="30c61-117">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="30c61-118">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="30c61-118">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="30c61-119">Адрес кода, с которого начнется `catch` выполнение обработчика в кадре, указанном методом [жетстаккпоинтер](icordebugexceptiondebugevent-getstackpointer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="30c61-119">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="30c61-120">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="30c61-120">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="30c61-121">`pIP` имеет значение 0.</span><span class="sxs-lookup"><span data-stu-id="30c61-121">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="30c61-122">Тип события доступен в методе [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="30c61-122">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30c61-123">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="30c61-123">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30c61-124">Требования</span><span class="sxs-lookup"><span data-stu-id="30c61-124">Requirements</span></span>  

 <span data-ttu-id="30c61-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30c61-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30c61-126">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30c61-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30c61-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30c61-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30c61-128">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30c61-128">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c61-129">См. также</span><span class="sxs-lookup"><span data-stu-id="30c61-129">See also</span></span>

- [<span data-ttu-id="30c61-130">Интерфейс ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="30c61-130">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="30c61-131">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="30c61-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
