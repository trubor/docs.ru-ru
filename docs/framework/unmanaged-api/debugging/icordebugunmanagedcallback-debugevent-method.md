---
description: 'Дополнительные сведения о методе: Икордебугунманажедкаллбакк::D Ебужевент'
title: Метод ICorDebugUnmanagedCallback::DebugEvent
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
ms.openlocfilehash: fcd7bc3b380add7465473cb01585eb1656d00aad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690578"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="11cfa-103">Метод ICorDebugUnmanagedCallback::DebugEvent</span><span class="sxs-lookup"><span data-stu-id="11cfa-103">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>

<span data-ttu-id="11cfa-104">Уведомляет отладчик о срабатывании собственного события.</span><span class="sxs-lookup"><span data-stu-id="11cfa-104">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11cfa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="11cfa-105">Syntax</span></span>  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11cfa-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="11cfa-106">Parameters</span></span>  

 `pDebugEvent`  
 <span data-ttu-id="11cfa-107">окне Указатель на собственное событие.</span><span class="sxs-lookup"><span data-stu-id="11cfa-107">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="11cfa-108">[in] `true` , если взаимодействие с состоянием управляемого процесса невозможно после возникновения неуправляемого события, до тех пор, пока отладчик не вызовет [ICorDebugController:: Continue](icordebugcontroller-continue-method.md); в противном случае — значение `false` .</span><span class="sxs-lookup"><span data-stu-id="11cfa-108">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11cfa-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="11cfa-109">Remarks</span></span>  

 <span data-ttu-id="11cfa-110">Если отлаживаемый поток является потоком Win32, не используйте члены интерфейса отладки Win32.</span><span class="sxs-lookup"><span data-stu-id="11cfa-110">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="11cfa-111">Можно вызывать `ICorDebugController::Continue` только в потоке Win32 и продолжать событие за пределами внешнего управления.</span><span class="sxs-lookup"><span data-stu-id="11cfa-111">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="11cfa-112">`DebugEvent`Обратный вызов не соответствует стандартным правилам для обратных вызовов.</span><span class="sxs-lookup"><span data-stu-id="11cfa-112">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="11cfa-113">При вызове `DebugEvent` процесс будет выполняться в состоянии "необработанный", "ОС-Отладка" остановлена.</span><span class="sxs-lookup"><span data-stu-id="11cfa-113">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="11cfa-114">Процесс не будет синхронизирован.</span><span class="sxs-lookup"><span data-stu-id="11cfa-114">The process will not be synchronized.</span></span> <span data-ttu-id="11cfa-115">Он автоматически вводит синхронизированное состояние при необходимости для удовлетворения запросов сведений об управляемом коде, что может привести к появлению других вложенных `DebugEvent` обратных вызовов.</span><span class="sxs-lookup"><span data-stu-id="11cfa-115">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="11cfa-116">Перед продолжением процесса вызовите [ICorDebugProcess:: ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) в процессе, чтобы проигнорировать событие исключения.</span><span class="sxs-lookup"><span data-stu-id="11cfa-116">Call [ICorDebugProcess::ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="11cfa-117">Вызов этого метода отправляет DBG_CONTINUE вместо DBG_EXCEPTION_NOT_HANDLED в запросе continue и автоматически очищает невыполненные точки останова и одношаговые исключения.</span><span class="sxs-lookup"><span data-stu-id="11cfa-117">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="11cfa-118">События по внешнему каналу могут быть получены в любое время, даже если отладка приложения будет остановлена и когда уже существует необработанное событие в полосе.</span><span class="sxs-lookup"><span data-stu-id="11cfa-118">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="11cfa-119">В платформа .NET Framework версии 2,0 отладчик должен немедленно продолжить работу после события нестандартной точки останова.</span><span class="sxs-lookup"><span data-stu-id="11cfa-119">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="11cfa-120">Для добавления и удаления точек останова отладчик должен использовать методы [ICorDebugProcess2:: сетунманажедбреакпоинт](icordebugprocess2-setunmanagedbreakpoint-method.md) и [ICorDebugProcess2:: клеарунманажедбреакпоинт](icordebugprocess2-clearunmanagedbreakpoint-method.md) .</span><span class="sxs-lookup"><span data-stu-id="11cfa-120">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="11cfa-121">Эти методы будут автоматически пропускать любые точки останова по внешнему каналу.</span><span class="sxs-lookup"><span data-stu-id="11cfa-121">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="11cfa-122">Таким образом, только точки останова по внешнему каналу, которые были отправлены, должны быть необработанными точками останова, которые уже находятся в потоке инструкций, например в вызове `DebugBreak` функции Win32.</span><span class="sxs-lookup"><span data-stu-id="11cfa-122">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="11cfa-123">Не пытайтесь использовать `ICorDebugProcess::ClearCurrentException` , [ICorDebugProcess:: GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: SetThreadContext](icordebugprocess-setthreadcontext-method.md)или любой другой член [API отладки](index.md).</span><span class="sxs-lookup"><span data-stu-id="11cfa-123">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11cfa-124">Требования</span><span class="sxs-lookup"><span data-stu-id="11cfa-124">Requirements</span></span>  

 <span data-ttu-id="11cfa-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11cfa-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11cfa-126">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11cfa-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11cfa-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11cfa-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11cfa-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11cfa-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11cfa-129">См. также</span><span class="sxs-lookup"><span data-stu-id="11cfa-129">See also</span></span>

- [<span data-ttu-id="11cfa-130">Интерфейс ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="11cfa-130">ICorDebugUnmanagedCallback Interface</span></span>](icordebugunmanagedcallback-interface.md)
