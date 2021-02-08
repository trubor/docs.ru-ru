---
description: 'Дополнительные сведения о методе: Икордебугстакквалк:: NOFRAMES'
title: Метод ICorDebugStackWalk::GetFrame
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
ms.openlocfilehash: b00ddb6a475aff4263a922f5a20b866cd0e1b2ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794745"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="dfba7-103">Метод ICorDebugStackWalk::GetFrame</span><span class="sxs-lookup"><span data-stu-id="dfba7-103">ICorDebugStackWalk::GetFrame Method</span></span>

<span data-ttu-id="dfba7-104">Возвращает текущий кадр в объекте [икордебугстакквалк](icordebugstackwalk-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="dfba7-104">Gets the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfba7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dfba7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfba7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dfba7-106">Parameters</span></span>  

 `pFrame`  
 <span data-ttu-id="dfba7-107">окне Указатель на адрес созданного объекта Frame, представляющий текущий кадр в стеке.</span><span class="sxs-lookup"><span data-stu-id="dfba7-107">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfba7-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dfba7-108">Return Value</span></span>  

 <span data-ttu-id="dfba7-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="dfba7-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="dfba7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dfba7-110">HRESULT</span></span>|<span data-ttu-id="dfba7-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="dfba7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dfba7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="dfba7-112">S_OK</span></span>|<span data-ttu-id="dfba7-113">Среда выполнения успешно вернула текущий кадр.</span><span class="sxs-lookup"><span data-stu-id="dfba7-113">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="dfba7-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dfba7-114">E_FAIL</span></span>|<span data-ttu-id="dfba7-115">Текущий кадр не был возвращен.</span><span class="sxs-lookup"><span data-stu-id="dfba7-115">The current frame was not returned.</span></span>|  
|<span data-ttu-id="dfba7-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="dfba7-116">S_FALSE</span></span>|<span data-ttu-id="dfba7-117">Текущий кадр является машинным кадром стека.</span><span class="sxs-lookup"><span data-stu-id="dfba7-117">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="dfba7-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="dfba7-118">E_INVALIDARG</span></span>|<span data-ttu-id="dfba7-119">Параметр `pFrame` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="dfba7-119">`pFrame` is null.</span></span>|  
|<span data-ttu-id="dfba7-120">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="dfba7-120">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="dfba7-121">Указатель фрейма уже находится в конце стека; Поэтому доступ к дополнительным кадрам невозможен.</span><span class="sxs-lookup"><span data-stu-id="dfba7-121">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="dfba7-122">Исключения</span><span class="sxs-lookup"><span data-stu-id="dfba7-122">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfba7-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="dfba7-123">Remarks</span></span>  

 <span data-ttu-id="dfba7-124">`ICorDebugStackWalk` Возвращает только фактические кадры стека.</span><span class="sxs-lookup"><span data-stu-id="dfba7-124">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="dfba7-125">Используйте метод [ICorDebugThread3:: жетактивеинтерналфрамес](icordebugthread3-getactiveinternalframes-method.md) для возврата внутренних кадров.</span><span class="sxs-lookup"><span data-stu-id="dfba7-125">Use the [ICorDebugThread3::GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="dfba7-126">(Внутренние кадры — это структуры данных, помещаемые в стек средой выполнения для хранения временных данных.)</span><span class="sxs-lookup"><span data-stu-id="dfba7-126">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfba7-127">Требования</span><span class="sxs-lookup"><span data-stu-id="dfba7-127">Requirements</span></span>  

 <span data-ttu-id="dfba7-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfba7-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfba7-129">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfba7-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfba7-130">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfba7-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfba7-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfba7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfba7-132">См. также</span><span class="sxs-lookup"><span data-stu-id="dfba7-132">See also</span></span>

- [<span data-ttu-id="dfba7-133">Интерфейс ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="dfba7-133">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="dfba7-134">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="dfba7-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="dfba7-135">Отладка</span><span class="sxs-lookup"><span data-stu-id="dfba7-135">Debugging</span></span>](index.md)
