---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: Бреакпоинтсетеррор'
title: Метод ICorDebugManagedCallback::BreakpointSetError
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
ms.openlocfilehash: cf78b4dc06a71b6ac0eb4f653a00c1b3c6ae464b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791092"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a><span data-ttu-id="ca0b0-103">Метод ICorDebugManagedCallback::BreakpointSetError</span><span class="sxs-lookup"><span data-stu-id="ca0b0-103">ICorDebugManagedCallback::BreakpointSetError Method</span></span>

<span data-ttu-id="ca0b0-104">Уведомляет отладчик о том, что среде CLR не удалось точно привязать точку останова, установленную до JIT-компиляции функции.</span><span class="sxs-lookup"><span data-stu-id="ca0b0-104">Notifies the debugger that the common language runtime was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca0b0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ca0b0-105">Syntax</span></span>  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca0b0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ca0b0-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="ca0b0-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, который содержит несвязанную точку останова.</span><span class="sxs-lookup"><span data-stu-id="ca0b0-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the unbound breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ca0b0-108">окне Указатель на объект ICorDebugThread, представляющий поток, содержащий несвязанную точку останова.</span><span class="sxs-lookup"><span data-stu-id="ca0b0-108">[in] A pointer to an ICorDebugThread object that represents the thread that contains the unbound breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="ca0b0-109">окне Указатель на объект Икордебугбреакпоинт, представляющий несвязанную точку останова.</span><span class="sxs-lookup"><span data-stu-id="ca0b0-109">[in] A pointer to an ICorDebugBreakpoint object that represents the unbound breakpoint.</span></span>  
  
 `dwError`  
 <span data-ttu-id="ca0b0-110">окне Целое число, указывающее на ошибку.</span><span class="sxs-lookup"><span data-stu-id="ca0b0-110">[in] An integer that indicates the error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca0b0-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="ca0b0-111">Remarks</span></span>  

 <span data-ttu-id="ca0b0-112">Заданная точка останова никогда не будет достигнута.</span><span class="sxs-lookup"><span data-stu-id="ca0b0-112">The given breakpoint will never be hit.</span></span> <span data-ttu-id="ca0b0-113">Отладчик должен деактивироваться и повторно привязывать его.</span><span class="sxs-lookup"><span data-stu-id="ca0b0-113">The debugger should deactivate and rebind it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca0b0-114">Требования</span><span class="sxs-lookup"><span data-stu-id="ca0b0-114">Requirements</span></span>  

 <span data-ttu-id="ca0b0-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca0b0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca0b0-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca0b0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca0b0-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca0b0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca0b0-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca0b0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca0b0-119">См. также</span><span class="sxs-lookup"><span data-stu-id="ca0b0-119">See also</span></span>

- [<span data-ttu-id="ca0b0-120">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="ca0b0-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
