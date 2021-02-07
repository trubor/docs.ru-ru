---
description: 'Дополнительные сведения о методе: Икордебугстакквалк:: Next'
title: Метод ICorDebugStackWalk::Next
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
ms.openlocfilehash: 27a48ca40f6b43cae32511b71b73e68d88eb60c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717762"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="650b1-103">Метод ICorDebugStackWalk::Next</span><span class="sxs-lookup"><span data-stu-id="650b1-103">ICorDebugStackWalk::Next Method</span></span>

<span data-ttu-id="650b1-104">Перемещает объект [икордебугстакквалк](icordebugstackwalk-interface.md) в следующий кадр.</span><span class="sxs-lookup"><span data-stu-id="650b1-104">Moves the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="650b1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="650b1-105">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="650b1-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="650b1-106">Return Value</span></span>  

 <span data-ttu-id="650b1-107">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="650b1-107">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="650b1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="650b1-108">HRESULT</span></span>|<span data-ttu-id="650b1-109">Описание:</span><span class="sxs-lookup"><span data-stu-id="650b1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="650b1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="650b1-110">S_OK</span></span>|<span data-ttu-id="650b1-111">Среда выполнения успешно развернута до следующего кадра (см. примечания).</span><span class="sxs-lookup"><span data-stu-id="650b1-111">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="650b1-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="650b1-112">E_FAIL</span></span>|<span data-ttu-id="650b1-113">`ICorDebugStackWalk`Объект не может быть расширен.</span><span class="sxs-lookup"><span data-stu-id="650b1-113">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="650b1-114">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="650b1-114">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="650b1-115">В результате этого очистки достигнут конец стека.</span><span class="sxs-lookup"><span data-stu-id="650b1-115">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="650b1-116">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="650b1-116">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="650b1-117">Указатель фрейма уже находится в конце стека; Поэтому доступ к дополнительным кадрам невозможен.</span><span class="sxs-lookup"><span data-stu-id="650b1-117">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="650b1-118">Исключения</span><span class="sxs-lookup"><span data-stu-id="650b1-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="650b1-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="650b1-119">Remarks</span></span>  

 <span data-ttu-id="650b1-120">`Next`Метод перемещает `ICorDebugStackWalk` объект в вызывающий кадр только в том случае, если среда выполнения может очистить текущий кадр.</span><span class="sxs-lookup"><span data-stu-id="650b1-120">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="650b1-121">В противном случае объект переходит к следующему кадру, который среда выполнения может очистить.</span><span class="sxs-lookup"><span data-stu-id="650b1-121">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="650b1-122">Требования</span><span class="sxs-lookup"><span data-stu-id="650b1-122">Requirements</span></span>  

 <span data-ttu-id="650b1-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="650b1-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="650b1-124">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="650b1-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="650b1-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="650b1-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="650b1-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="650b1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="650b1-127">См. также</span><span class="sxs-lookup"><span data-stu-id="650b1-127">See also</span></span>

- [<span data-ttu-id="650b1-128">Интерфейс ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="650b1-128">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="650b1-129">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="650b1-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="650b1-130">Отладка</span><span class="sxs-lookup"><span data-stu-id="650b1-130">Debugging</span></span>](index.md)
