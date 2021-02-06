---
description: 'Дополнительные сведения о методе: Икордебугстакквалк:: oncontext'
title: Метод ICorDebugStackWalk::GetContext
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
ms.openlocfilehash: 30beefaa1e0e2e4c5043cae7213658ac24e8a1b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649615"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="d7189-103">Метод ICorDebugStackWalk::GetContext</span><span class="sxs-lookup"><span data-stu-id="d7189-103">ICorDebugStackWalk::GetContext Method</span></span>

<span data-ttu-id="d7189-104">Возвращает контекст для текущего кадра в объекте [икордебугстакквалк](icordebugstackwalk-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d7189-104">Returns the context for the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7189-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d7189-105">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7189-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7189-106">Parameters</span></span>  

 `contextFlags`  
 <span data-ttu-id="d7189-107">окне Флаги, указывающие запрошенное содержимое буфера контекста (определенного в WinNT. h).</span><span class="sxs-lookup"><span data-stu-id="d7189-107">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="d7189-108">окне Выделенный размер буфера контекста.</span><span class="sxs-lookup"><span data-stu-id="d7189-108">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="d7189-109">заполняет Фактический размер контекста.</span><span class="sxs-lookup"><span data-stu-id="d7189-109">[out] The actual size of the context.</span></span> <span data-ttu-id="d7189-110">Это значение должно быть меньше или равно размеру буфера контекста.</span><span class="sxs-lookup"><span data-stu-id="d7189-110">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="d7189-111">заполняет Буфер контекста.</span><span class="sxs-lookup"><span data-stu-id="d7189-111">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7189-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d7189-112">Return Value</span></span>  

 <span data-ttu-id="d7189-113">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="d7189-113">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d7189-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7189-114">HRESULT</span></span>|<span data-ttu-id="d7189-115">Описание:</span><span class="sxs-lookup"><span data-stu-id="d7189-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7189-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="d7189-116">S_OK</span></span>|<span data-ttu-id="d7189-117">Контекст для текущего кадра успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="d7189-117">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="d7189-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d7189-118">E_FAIL</span></span>|<span data-ttu-id="d7189-119">Не удалось вернуть контекст.</span><span class="sxs-lookup"><span data-stu-id="d7189-119">The context could not be returned.</span></span>|  
|<span data-ttu-id="d7189-120">HRESULT_FROM_WIN32 (БУФЕР ERROR_INSUFFICIENT)</span><span class="sxs-lookup"><span data-stu-id="d7189-120">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="d7189-121">Буфер контекста слишком мал.</span><span class="sxs-lookup"><span data-stu-id="d7189-121">The context buffer is too small.</span></span>|  
|<span data-ttu-id="d7189-122">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="d7189-122">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="d7189-123">Указатель фрейма уже находится в конце стека; Поэтому доступ к дополнительным кадрам невозможен.</span><span class="sxs-lookup"><span data-stu-id="d7189-123">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="d7189-124">Исключения</span><span class="sxs-lookup"><span data-stu-id="d7189-124">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7189-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="d7189-125">Remarks</span></span>  

 <span data-ttu-id="d7189-126">Поскольку при очистке восстанавливаются только подмножество регистров, например непостоянные регистры, контекст может точно не соответствовать состоянию регистрации во время вызова.</span><span class="sxs-lookup"><span data-stu-id="d7189-126">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7189-127">Требования</span><span class="sxs-lookup"><span data-stu-id="d7189-127">Requirements</span></span>  

 <span data-ttu-id="d7189-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7189-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7189-129">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7189-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7189-130">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7189-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7189-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7189-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7189-132">См. также</span><span class="sxs-lookup"><span data-stu-id="d7189-132">See also</span></span>

- [<span data-ttu-id="d7189-133">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="d7189-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d7189-134">Отладка</span><span class="sxs-lookup"><span data-stu-id="d7189-134">Debugging</span></span>](index.md)
