---
description: 'Дополнительные сведения о методе: Икордебугстакквалк:: SetContext'
title: Метод ICorDebugStackWalk::SetContext
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
ms.openlocfilehash: 20e18460d237a63e4c2695b9e7cbfa766ed3908f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794719"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="50ee2-103">Метод ICorDebugStackWalk::SetContext</span><span class="sxs-lookup"><span data-stu-id="50ee2-103">ICorDebugStackWalk::SetContext Method</span></span>

<span data-ttu-id="50ee2-104">Задает для текущего контекста объекта [икордебугстакквалк](icordebugstackwalk-interface.md) допустимый контекст для потока.</span><span class="sxs-lookup"><span data-stu-id="50ee2-104">Sets the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50ee2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="50ee2-105">Syntax</span></span>  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50ee2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="50ee2-106">Parameters</span></span>  

 `flag`  
 <span data-ttu-id="50ee2-107">окне Флаг [кордебугсетконтекстфлаг](cordebugsetcontextflag-enumeration.md) , который указывает, относится ли контекст к активному кадру в стеке или к контексту, полученному путем очистки стека.</span><span class="sxs-lookup"><span data-stu-id="50ee2-107">[in] A [CorDebugSetContextFlag](cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="50ee2-108">окне Выделенный размер `CONTEXT` буфера.</span><span class="sxs-lookup"><span data-stu-id="50ee2-108">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="50ee2-109">окне `CONTEXT` Буфер.</span><span class="sxs-lookup"><span data-stu-id="50ee2-109">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50ee2-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="50ee2-110">Return Value</span></span>  

 <span data-ttu-id="50ee2-111">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="50ee2-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="50ee2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50ee2-112">HRESULT</span></span>|<span data-ttu-id="50ee2-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="50ee2-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50ee2-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="50ee2-114">S_OK</span></span>|<span data-ttu-id="50ee2-115">`ICorDebugStackWalk`Контекст объекта успешно установлен.</span><span class="sxs-lookup"><span data-stu-id="50ee2-115">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="50ee2-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50ee2-116">E_FAIL</span></span>|<span data-ttu-id="50ee2-117">`ICorDebugStackWalk`Контекст объекта не задан.</span><span class="sxs-lookup"><span data-stu-id="50ee2-117">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="50ee2-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="50ee2-118">E_INVALIDARG</span></span>|<span data-ttu-id="50ee2-119">Контекст имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="50ee2-119">The context is null.</span></span>|  
|<span data-ttu-id="50ee2-120">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="50ee2-120">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="50ee2-121">Буфер контекста слишком мал.</span><span class="sxs-lookup"><span data-stu-id="50ee2-121">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="50ee2-122">Исключения</span><span class="sxs-lookup"><span data-stu-id="50ee2-122">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50ee2-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="50ee2-123">Remarks</span></span>  

 <span data-ttu-id="50ee2-124">Этот метод не изменяет текущий контекст потока.</span><span class="sxs-lookup"><span data-stu-id="50ee2-124">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="50ee2-125">Установка текущего контекста в недопустимый контекст может привести к непредсказуемым результатам обхода стека.</span><span class="sxs-lookup"><span data-stu-id="50ee2-125">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="50ee2-126">Вы можете получить точную побитовую копию этого контекста путем немедленного вызова метода [икордебугстакквалк:: oncontext](icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="50ee2-126">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50ee2-127">Требования</span><span class="sxs-lookup"><span data-stu-id="50ee2-127">Requirements</span></span>  

 <span data-ttu-id="50ee2-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50ee2-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50ee2-129">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50ee2-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50ee2-130">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50ee2-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50ee2-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50ee2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50ee2-132">См. также</span><span class="sxs-lookup"><span data-stu-id="50ee2-132">See also</span></span>

- [<span data-ttu-id="50ee2-133">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="50ee2-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="50ee2-134">Отладка</span><span class="sxs-lookup"><span data-stu-id="50ee2-134">Debugging</span></span>](index.md)
