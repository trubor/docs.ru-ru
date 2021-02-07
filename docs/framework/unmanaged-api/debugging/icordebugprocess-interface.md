---
description: 'Дополнительные сведения о: Интерфейс ICorDebugProcess'
title: Интерфейс ICorDebugProcess
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
ms.openlocfilehash: 7172ee12bf450235db1c18601c8ff7de51435520
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746793"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="41d35-103">Интерфейс ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="41d35-103">ICorDebugProcess Interface</span></span>

<span data-ttu-id="41d35-104">Представляет процесс, выполняющий управляемый код.</span><span class="sxs-lookup"><span data-stu-id="41d35-104">Represents a process that is executing managed code.</span></span> <span data-ttu-id="41d35-105">Этот интерфейс является подклассом ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="41d35-105">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41d35-106">Методы</span><span class="sxs-lookup"><span data-stu-id="41d35-106">Methods</span></span>  
  
|<span data-ttu-id="41d35-107">Метод</span><span class="sxs-lookup"><span data-stu-id="41d35-107">Method</span></span>|<span data-ttu-id="41d35-108">Описание</span><span class="sxs-lookup"><span data-stu-id="41d35-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41d35-109">Метод ClearCurrentException</span><span class="sxs-lookup"><span data-stu-id="41d35-109">ClearCurrentException Method</span></span>](icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="41d35-110">Очищает текущее неуправляемое исключение для данного потока.</span><span class="sxs-lookup"><span data-stu-id="41d35-110">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="41d35-111">Метод EnableLogMessages</span><span class="sxs-lookup"><span data-stu-id="41d35-111">EnableLogMessages Method</span></span>](icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="41d35-112">Включает и отключает отправку сообщений журнала отладчику.</span><span class="sxs-lookup"><span data-stu-id="41d35-112">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="41d35-113">Метод EnumerateAppDomains</span><span class="sxs-lookup"><span data-stu-id="41d35-113">EnumerateAppDomains Method</span></span>](icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="41d35-114">Перечисляет все домены приложений в процессе.</span><span class="sxs-lookup"><span data-stu-id="41d35-114">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="41d35-115">Метод EnumerateObjects</span><span class="sxs-lookup"><span data-stu-id="41d35-115">EnumerateObjects Method</span></span>](icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="41d35-116">Не реализован.</span><span class="sxs-lookup"><span data-stu-id="41d35-116">Not implemented.</span></span>|  
|[<span data-ttu-id="41d35-117">Метод GetHandle</span><span class="sxs-lookup"><span data-stu-id="41d35-117">GetHandle Method</span></span>](icordebugprocess-gethandle-method.md)|<span data-ttu-id="41d35-118">Возвращает маркер процесса.</span><span class="sxs-lookup"><span data-stu-id="41d35-118">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="41d35-119">Метод GetHelperThreadID</span><span class="sxs-lookup"><span data-stu-id="41d35-119">GetHelperThreadID Method</span></span>](icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="41d35-120">Возвращает идентификатор потока операционной системы (ОС) для внутреннего вспомогательного потока отладчика.</span><span class="sxs-lookup"><span data-stu-id="41d35-120">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="41d35-121">Метод GetID</span><span class="sxs-lookup"><span data-stu-id="41d35-121">GetID Method</span></span>](icordebugprocess-getid-method.md)|<span data-ttu-id="41d35-122">Возвращает идентификатор операционной системы (ОС) процесса.</span><span class="sxs-lookup"><span data-stu-id="41d35-122">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="41d35-123">Метод GetObject</span><span class="sxs-lookup"><span data-stu-id="41d35-123">GetObject Method</span></span>](icordebugprocess-getobject-method.md)|<span data-ttu-id="41d35-124">Не реализован.</span><span class="sxs-lookup"><span data-stu-id="41d35-124">Not implemented.</span></span>|  
|[<span data-ttu-id="41d35-125">Метод GetThread</span><span class="sxs-lookup"><span data-stu-id="41d35-125">GetThread Method</span></span>](icordebugprocess-getthread-method.md)|<span data-ttu-id="41d35-126">Возвращает экземпляр ICorDebugThread с указанным ИДЕНТИФИКАТОРом потока ОС.</span><span class="sxs-lookup"><span data-stu-id="41d35-126">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="41d35-127">Метод GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="41d35-127">GetThreadContext Method</span></span>](icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="41d35-128">Возвращает контекст для заданного потока.</span><span class="sxs-lookup"><span data-stu-id="41d35-128">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="41d35-129">Метод IsOSSuspended</span><span class="sxs-lookup"><span data-stu-id="41d35-129">IsOSSuspended Method</span></span>](icordebugprocess-isossuspended-method.md)|<span data-ttu-id="41d35-130">Определяет, был ли поток приостановлен в результате остановки процесса отладчиком.</span><span class="sxs-lookup"><span data-stu-id="41d35-130">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="41d35-131">Метод IsTransitionStub</span><span class="sxs-lookup"><span data-stu-id="41d35-131">IsTransitionStub Method</span></span>](icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="41d35-132">Определяет, находится ли адрес в заглушке, что приведет к переходу в управляемый код.</span><span class="sxs-lookup"><span data-stu-id="41d35-132">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="41d35-133">Метод ModifyLogSwitch</span><span class="sxs-lookup"><span data-stu-id="41d35-133">ModifyLogSwitch Method</span></span>](icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="41d35-134">Задает уровень серьезности указанного переключателя журнала.</span><span class="sxs-lookup"><span data-stu-id="41d35-134">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="41d35-135">Метод ReadMemory</span><span class="sxs-lookup"><span data-stu-id="41d35-135">ReadMemory Method</span></span>](icordebugprocess-readmemory-method.md)|<span data-ttu-id="41d35-136">Считывает память из процесса.</span><span class="sxs-lookup"><span data-stu-id="41d35-136">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="41d35-137">Метод SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="41d35-137">SetThreadContext Method</span></span>](icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="41d35-138">Задает контекст для заданного потока.</span><span class="sxs-lookup"><span data-stu-id="41d35-138">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="41d35-139">Метод ThreadForFiberCookie</span><span class="sxs-lookup"><span data-stu-id="41d35-139">ThreadForFiberCookie Method</span></span>](icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="41d35-140">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="41d35-140">Deprecated.</span></span>|  
|[<span data-ttu-id="41d35-141">Метод WriteMemory</span><span class="sxs-lookup"><span data-stu-id="41d35-141">WriteMemory Method</span></span>](icordebugprocess-writememory-method.md)|<span data-ttu-id="41d35-142">Записывает данные в область памяти в процессе.</span><span class="sxs-lookup"><span data-stu-id="41d35-142">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41d35-143">Remarks</span><span class="sxs-lookup"><span data-stu-id="41d35-143">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41d35-144">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="41d35-144">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41d35-145">Требования</span><span class="sxs-lookup"><span data-stu-id="41d35-145">Requirements</span></span>  

 <span data-ttu-id="41d35-146">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41d35-146">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41d35-147">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41d35-147">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41d35-148">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41d35-148">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41d35-149">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41d35-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d35-150">См. также</span><span class="sxs-lookup"><span data-stu-id="41d35-150">See also</span></span>

- [<span data-ttu-id="41d35-151">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="41d35-151">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="41d35-152">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="41d35-152">Debugging Interfaces</span></span>](debugging-interfaces.md)
