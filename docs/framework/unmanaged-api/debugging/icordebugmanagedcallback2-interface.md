---
description: 'Дополнительные сведения о: интерфейс ICorDebugManagedCallback2'
title: Интерфейс ICorDebugManagedCallback2
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
ms.openlocfilehash: a6a5b05479ea0f9e2d86f7c0ce42f5edd35bcb7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691761"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="a40fc-103">Интерфейс ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="a40fc-103">ICorDebugManagedCallback2 Interface</span></span>

<span data-ttu-id="a40fc-104">Предоставляет методы для поддержки обработки исключений отладчика и управляемых помощников по отладке (MDA).</span><span class="sxs-lookup"><span data-stu-id="a40fc-104">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="a40fc-105">`ICorDebugManagedCallback2` является логическим расширением интерфейса [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a40fc-105">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a40fc-106">Методы</span><span class="sxs-lookup"><span data-stu-id="a40fc-106">Methods</span></span>  
  
|<span data-ttu-id="a40fc-107">Метод</span><span class="sxs-lookup"><span data-stu-id="a40fc-107">Method</span></span>|<span data-ttu-id="a40fc-108">Описание</span><span class="sxs-lookup"><span data-stu-id="a40fc-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a40fc-109">Метод ChangeConnection</span><span class="sxs-lookup"><span data-stu-id="a40fc-109">ChangeConnection Method</span></span>](icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="a40fc-110">Уведомляет отладчик о том, что набор задач, связанных с указанным соединением, изменился.</span><span class="sxs-lookup"><span data-stu-id="a40fc-110">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="a40fc-111">Метод CreateConnection</span><span class="sxs-lookup"><span data-stu-id="a40fc-111">CreateConnection Method</span></span>](icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="a40fc-112">Уведомляет отладчик о создании нового соединения.</span><span class="sxs-lookup"><span data-stu-id="a40fc-112">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="a40fc-113">Метод DestroyConnection</span><span class="sxs-lookup"><span data-stu-id="a40fc-113">DestroyConnection Method</span></span>](icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="a40fc-114">Уведомляет отладчик о завершении указанного соединения.</span><span class="sxs-lookup"><span data-stu-id="a40fc-114">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="a40fc-115">Метод Exception</span><span class="sxs-lookup"><span data-stu-id="a40fc-115">Exception Method</span></span>](icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="a40fc-116">Уведомляет отладчик о запуске поиска обработчика исключений.</span><span class="sxs-lookup"><span data-stu-id="a40fc-116">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="a40fc-117">Метод ExceptionUnwind</span><span class="sxs-lookup"><span data-stu-id="a40fc-117">ExceptionUnwind Method</span></span>](icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="a40fc-118">Предоставляет уведомление о состоянии во время процесса очистки исключения.</span><span class="sxs-lookup"><span data-stu-id="a40fc-118">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="a40fc-119">Метод FunctionRemapComplete</span><span class="sxs-lookup"><span data-stu-id="a40fc-119">FunctionRemapComplete Method</span></span>](icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="a40fc-120">Уведомляет отладчик о том, что выполнение кода переключено на новую версию измененной функции.</span><span class="sxs-lookup"><span data-stu-id="a40fc-120">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="a40fc-121">Метод FunctionRemapOpportunity</span><span class="sxs-lookup"><span data-stu-id="a40fc-121">FunctionRemapOpportunity Method</span></span>](icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="a40fc-122">Уведомляет отладчик о том, что выполнение кода достигло точки последовательности в более ранней версии измененной функции.</span><span class="sxs-lookup"><span data-stu-id="a40fc-122">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="a40fc-123">Метод MDANotification</span><span class="sxs-lookup"><span data-stu-id="a40fc-123">MDANotification Method</span></span>](icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="a40fc-124">Предоставляет уведомление о том, что при выполнении кода было обнаружено сообщение MDA.</span><span class="sxs-lookup"><span data-stu-id="a40fc-124">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a40fc-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="a40fc-125">Remarks</span></span>  

 <span data-ttu-id="a40fc-126">`ICorDebugManagedCallback2`Интерфейс расширяет `ICorDebugManagedCallback` интерфейс для поддержки новых событий отладки, появившихся в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="a40fc-126">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="a40fc-127">`ICorDebugManagedCallback2`При отладке приложений платформа .NET Framework 2,0 в отладчике должен быть реализован.</span><span class="sxs-lookup"><span data-stu-id="a40fc-127">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="a40fc-128">Экземпляр `ICorDebugManagedCallback` или `ICorDebugManagedCallback2` передается как объект обратного вызова в [ICorDebug:: SetManagedHandler](icordebug-setmanagedhandler-method.md).</span><span class="sxs-lookup"><span data-stu-id="a40fc-128">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a40fc-129">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="a40fc-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a40fc-130">Требования</span><span class="sxs-lookup"><span data-stu-id="a40fc-130">Requirements</span></span>  

 <span data-ttu-id="a40fc-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a40fc-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a40fc-132">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a40fc-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a40fc-133">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a40fc-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a40fc-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a40fc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a40fc-135">См. также</span><span class="sxs-lookup"><span data-stu-id="a40fc-135">See also</span></span>

- [<span data-ttu-id="a40fc-136">Диагностика ошибок посредством управляемых помощников по отладке</span><span class="sxs-lookup"><span data-stu-id="a40fc-136">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a40fc-137">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="a40fc-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a40fc-138">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="a40fc-138">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
