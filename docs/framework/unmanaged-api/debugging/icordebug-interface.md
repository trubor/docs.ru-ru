---
description: Дополнительные сведения о интерфейсе ICorDebug
title: Интерфейс ICorDebug
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
ms.openlocfilehash: b989013f7eb54e163feeb965e10448a3a1756e3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772527"
---
# <a name="icordebug-interface"></a><span data-ttu-id="2eec7-103">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="2eec7-103">ICorDebug Interface</span></span>

<span data-ttu-id="2eec7-104">Предоставляет методы, позволяющие разработчикам отлаживать приложения в среде среды CLR.</span><span class="sxs-lookup"><span data-stu-id="2eec7-104">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2eec7-105">Отладка в смешанном режиме (управляемый и машинный код) не поддерживается в Windows 95, Windows 98 или Windows ME или на платформах, отличных от x86 (например, IA64 и AMD64).</span><span class="sxs-lookup"><span data-stu-id="2eec7-105">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2eec7-106">Методы</span><span class="sxs-lookup"><span data-stu-id="2eec7-106">Methods</span></span>  
  
|<span data-ttu-id="2eec7-107">Метод</span><span class="sxs-lookup"><span data-stu-id="2eec7-107">Method</span></span>|<span data-ttu-id="2eec7-108">Описание</span><span class="sxs-lookup"><span data-stu-id="2eec7-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2eec7-109">Метод CanLaunchOrAttach</span><span class="sxs-lookup"><span data-stu-id="2eec7-109">CanLaunchOrAttach Method</span></span>](icordebug-canlaunchorattach-method.md)|<span data-ttu-id="2eec7-110">Определяет, возможен ли запуск нового процесса или присоединение к данному процессу в контексте текущей конфигурации компьютера и среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="2eec7-110">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="2eec7-111">Метод CreateProcess</span><span class="sxs-lookup"><span data-stu-id="2eec7-111">CreateProcess Method</span></span>](icordebug-createprocess-method.md)|<span data-ttu-id="2eec7-112">Запускает процесс и его основной поток под управлением отладчика.</span><span class="sxs-lookup"><span data-stu-id="2eec7-112">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="2eec7-113">Метод DebugActiveProcess</span><span class="sxs-lookup"><span data-stu-id="2eec7-113">DebugActiveProcess Method</span></span>](icordebug-debugactiveprocess-method.md)|<span data-ttu-id="2eec7-114">Присоединяет отладчик к существующему процессу.</span><span class="sxs-lookup"><span data-stu-id="2eec7-114">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="2eec7-115">Метод EnumerateProcesses</span><span class="sxs-lookup"><span data-stu-id="2eec7-115">EnumerateProcesses Method</span></span>](icordebug-enumerateprocesses-method.md)|<span data-ttu-id="2eec7-116">Возвращает перечислитель для отлаживаемых процессов.</span><span class="sxs-lookup"><span data-stu-id="2eec7-116">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="2eec7-117">Метод GetProcess</span><span class="sxs-lookup"><span data-stu-id="2eec7-117">GetProcess Method</span></span>](icordebug-getprocess-method.md)|<span data-ttu-id="2eec7-118">Возвращает объект "ICorDebugProcess" с заданным ИДЕНТИФИКАТОРом процесса.</span><span class="sxs-lookup"><span data-stu-id="2eec7-118">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="2eec7-119">Метод Initialize</span><span class="sxs-lookup"><span data-stu-id="2eec7-119">Initialize Method</span></span>](icordebug-initialize-method.md)|<span data-ttu-id="2eec7-120">Выполняет инициализацию объекта `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="2eec7-120">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="2eec7-121">Метод SetManagedHandler</span><span class="sxs-lookup"><span data-stu-id="2eec7-121">SetManagedHandler Method</span></span>](icordebug-setmanagedhandler-method.md)|<span data-ttu-id="2eec7-122">Указывает объект обработчика событий для управляемых событий.</span><span class="sxs-lookup"><span data-stu-id="2eec7-122">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="2eec7-123">Метод SetUnmanagedHandler</span><span class="sxs-lookup"><span data-stu-id="2eec7-123">SetUnmanagedHandler Method</span></span>](icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="2eec7-124">Указывает объект обработчика событий для неуправляемых событий.</span><span class="sxs-lookup"><span data-stu-id="2eec7-124">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="2eec7-125">Метод Terminate</span><span class="sxs-lookup"><span data-stu-id="2eec7-125">Terminate Method</span></span>](icordebug-terminate-method.md)|<span data-ttu-id="2eec7-126">Завершает `ICorDebug` объект.</span><span class="sxs-lookup"><span data-stu-id="2eec7-126">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2eec7-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="2eec7-127">Remarks</span></span>  

 <span data-ttu-id="2eec7-128">`ICorDebug` представляет цикл обработки событий для процесса отладчика.</span><span class="sxs-lookup"><span data-stu-id="2eec7-128">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="2eec7-129">Перед освобождением этого интерфейса отладчик должен ожидать обратного вызова [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) для всех отлаживаемых процессов.</span><span class="sxs-lookup"><span data-stu-id="2eec7-129">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="2eec7-130">`ICorDebug`Объект является начальным объектом для управления всеми дальнейшими управляемыми отладками.</span><span class="sxs-lookup"><span data-stu-id="2eec7-130">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="2eec7-131">В платформа .NET Framework версиях 1,0 и 1,1 этот объект был `CoClass` объектом, созданным из com.</span><span class="sxs-lookup"><span data-stu-id="2eec7-131">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="2eec7-132">В платформа .NET Framework версии 2,0 этот объект больше не является `CoClass` объектом.</span><span class="sxs-lookup"><span data-stu-id="2eec7-132">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="2eec7-133">Она должна быть создана функцией [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) , которая поддерживает больше версий.</span><span class="sxs-lookup"><span data-stu-id="2eec7-133">It must be created by the [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="2eec7-134">Эта новая функция создания позволяет клиентам получить определенную реализацию `ICorDebug` , которая также эмулирует определенную версию API отладки.</span><span class="sxs-lookup"><span data-stu-id="2eec7-134">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2eec7-135">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="2eec7-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2eec7-136">Требования</span><span class="sxs-lookup"><span data-stu-id="2eec7-136">Requirements</span></span>  

 <span data-ttu-id="2eec7-137">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2eec7-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eec7-138">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2eec7-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2eec7-139">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2eec7-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2eec7-140">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2eec7-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eec7-141">См. также</span><span class="sxs-lookup"><span data-stu-id="2eec7-141">See also</span></span>

- [<span data-ttu-id="2eec7-142">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="2eec7-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
