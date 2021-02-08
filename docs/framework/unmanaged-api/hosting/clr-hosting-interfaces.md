---
description: 'Дополнительные сведения: интерфейсы размещения CLR'
title: Интерфейсы размещения CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: f42a74698607ffbed4a981f061d13ea4e9d634d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799906"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="dd36d-103">Интерфейсы размещения CLR</span><span class="sxs-lookup"><span data-stu-id="dd36d-103">CLR Hosting Interfaces</span></span>

<span data-ttu-id="dd36d-104">В этом разделе описываются интерфейсы, которые неуправляемые узлы могут использовать для интеграции среды CLR в свои приложения.</span><span class="sxs-lookup"><span data-stu-id="dd36d-104">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="dd36d-105">Информация относится к платформа .NET Framework версии 2,0 и более поздним версиям.</span><span class="sxs-lookup"><span data-stu-id="dd36d-105">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="dd36d-106">Эти интерфейсы позволяют ведущему приложению управлять многими другими аспектами среды выполнения, чем было возможно в версиях 1,0 и 1,1, и обеспечивать более тесную интеграцию между средой CLR и моделью выполнения узла.</span><span class="sxs-lookup"><span data-stu-id="dd36d-106">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="dd36d-107">В платформа .NET Framework версии 1,0 и 1,1 модель размещения позволяла неуправляемому узлу загружать среду CLR в процесс, настраивать определенные параметры и получать уведомления о событиях.</span><span class="sxs-lookup"><span data-stu-id="dd36d-107">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="dd36d-108">Однако в общем случае узел и среда CLR выполнялись независимо в этом процессе.</span><span class="sxs-lookup"><span data-stu-id="dd36d-108">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="dd36d-109">В платформа .NET Framework версии 2,0 и более поздних новые уровни абстракции позволяют ведущему приложению предоставлять множество ресурсов, предоставляемых типами в сборке Win32, и расширять набор возможностей, которые может настраивать узел.</span><span class="sxs-lookup"><span data-stu-id="dd36d-109">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd36d-110">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="dd36d-110">In This Section</span></span>  

 [<span data-ttu-id="dd36d-111">Интерфейс IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="dd36d-111">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)  
 <span data-ttu-id="dd36d-112">Предоставляет метод, который выполняет обратный вызов для зарегистрированного события.</span><span class="sxs-lookup"><span data-stu-id="dd36d-112">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="dd36d-113">Интерфейс IApartmentCallback</span><span class="sxs-lookup"><span data-stu-id="dd36d-113">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)  
 <span data-ttu-id="dd36d-114">Предоставляет методы для выполнения обратных вызовов в апартаменте.</span><span class="sxs-lookup"><span data-stu-id="dd36d-114">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="dd36d-115">Интерфейс IAppDomainBinding</span><span class="sxs-lookup"><span data-stu-id="dd36d-115">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)  
 <span data-ttu-id="dd36d-116">Предоставляет методы для настройки конфигурации времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="dd36d-116">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="dd36d-117">Интерфейс ICatalogServices</span><span class="sxs-lookup"><span data-stu-id="dd36d-117">ICatalogServices Interface</span></span>](icatalogservices-interface.md)  
 <span data-ttu-id="dd36d-118">Предоставляет методы для каталогизации служб.</span><span class="sxs-lookup"><span data-stu-id="dd36d-118">Provides methods for cataloging services.</span></span> <span data-ttu-id="dd36d-119">(Этот интерфейс поддерживает платформа .NET Frameworkную инфраструктуру и не предназначен для непосредственного использования в коде.)</span><span class="sxs-lookup"><span data-stu-id="dd36d-119">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="dd36d-120">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-120">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="dd36d-121">Предоставляет методы, поддерживающие взаимодействие между узлом и средой CLR о сборках.</span><span class="sxs-lookup"><span data-stu-id="dd36d-121">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="dd36d-122">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="dd36d-122">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="dd36d-123">Управляет списком сборок, загружаемых средой CLR, а не узлом.</span><span class="sxs-lookup"><span data-stu-id="dd36d-123">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="dd36d-124">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="dd36d-124">ICLRControl Interface</span></span>](iclrcontrol-interface.md)  
 <span data-ttu-id="dd36d-125">Предоставляет узлу методы для получения доступа и настройки различных аспектов среды CLR.</span><span class="sxs-lookup"><span data-stu-id="dd36d-125">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="dd36d-126">Интерфейс ICLRDebugManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-126">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)  
 <span data-ttu-id="dd36d-127">Предоставляет методы, позволяющие узлу связать набор задач с идентификатором и понятным именем.</span><span class="sxs-lookup"><span data-stu-id="dd36d-127">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="dd36d-128">Интерфейс ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-128">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="dd36d-129">Предоставляет методы, позволяющие основному приложению настраивать дампы пользовательской кучи для отчетов об ошибках.</span><span class="sxs-lookup"><span data-stu-id="dd36d-129">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="dd36d-130">Интерфейс ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-130">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)  
 <span data-ttu-id="dd36d-131">Предоставляет методы, позволяющие основному приложению взаимодействовать с системой сборки мусора среды CLR.</span><span class="sxs-lookup"><span data-stu-id="dd36d-131">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="dd36d-132">Интерфейс ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-132">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="dd36d-133">Предоставляет методам для узла возможность оценивать и передавать изменения в сведениях о политике для сборок.</span><span class="sxs-lookup"><span data-stu-id="dd36d-133">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="dd36d-134">Интерфейс ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-134">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="dd36d-135">Позволяет узлу блокировать выполнение конкретных управляемых классов, методов, свойств и полей в частично доверяемом коде.</span><span class="sxs-lookup"><span data-stu-id="dd36d-135">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="dd36d-136">Интерфейс ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)  
 <span data-ttu-id="dd36d-137">Реализует метод обратного вызова, который позволяет ведущему приложению уведомлять среду CLR о состоянии указанных запросов ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="dd36d-137">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="dd36d-138">Интерфейс ICLRMemoryNotificationCallback</span><span class="sxs-lookup"><span data-stu-id="dd36d-138">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="dd36d-139">Позволяет узлу сообщать об условиях нехватки памяти с помощью подхода, аналогичного функции Win32 `CreateMemoryResourceNotification` .</span><span class="sxs-lookup"><span data-stu-id="dd36d-139">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="dd36d-140">Интерфейс ICLROnEventManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-140">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)  
 <span data-ttu-id="dd36d-141">Предоставляет методы, позволяющие основному приложению регистрировать и отменять регистрацию обратных вызовов для событий CLR.</span><span class="sxs-lookup"><span data-stu-id="dd36d-141">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="dd36d-142">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-142">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)  
 <span data-ttu-id="dd36d-143">Предоставляет методы, позволяющие основному приложению указывать действия политики, выполняемые в случае сбоев и истечения времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="dd36d-143">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="dd36d-144">Интерфейс ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="dd36d-144">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="dd36d-145">Предоставляет методы, позволяющие основному приложению получать идентификаторы проверки сборки с помощью сведений об удостоверении сборки, которые являются внутренними для CLR, без необходимости создания или понимания этого удостоверения.</span><span class="sxs-lookup"><span data-stu-id="dd36d-145">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="dd36d-146">Интерфейс ICLRReferenceAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="dd36d-146">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="dd36d-147">Предоставляет методы, позволяющие основному приложению манипулировать набором сборок, на которые ссылается файл или поток, с помощью данных идентификации сборок, которые являются внутренними для CLR, без необходимости создавать или анализировать эти удостоверения.</span><span class="sxs-lookup"><span data-stu-id="dd36d-147">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="dd36d-148">Интерфейс ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="dd36d-148">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)  
 <span data-ttu-id="dd36d-149">Предоставляет возможности, аналогичные [ICorRuntimeHost](icorruntimehost-interface.md), и дополнительный метод для установки интерфейса управления узла.</span><span class="sxs-lookup"><span data-stu-id="dd36d-149">Provides capabilities similar to [ICorRuntimeHost](icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="dd36d-150">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-150">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)  
 <span data-ttu-id="dd36d-151">Предоставляет основному приложению методы для получения сведений о запрошенных задачах и обнаружения взаимоблокировок в своей реализации синхронизации.</span><span class="sxs-lookup"><span data-stu-id="dd36d-151">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="dd36d-152">Интерфейс ICLRTask</span><span class="sxs-lookup"><span data-stu-id="dd36d-152">ICLRTask Interface</span></span>](iclrtask-interface.md)  
 <span data-ttu-id="dd36d-153">Предоставляет методы, позволяющие основному приложению выполнять запросы среды CLR или предоставлять для среды CLR уведомление о связанной задаче.</span><span class="sxs-lookup"><span data-stu-id="dd36d-153">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="dd36d-154">Интерфейс ICLRTaskManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-154">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)  
 <span data-ttu-id="dd36d-155">Предоставляет методы, позволяющие основному приложению запрашивать явно, что среда CLR создает новую задачу, получает текущую выполняемую задачу и задает язык и региональные параметры для задачи.</span><span class="sxs-lookup"><span data-stu-id="dd36d-155">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="dd36d-156">Интерфейс ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="dd36d-156">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)  
 <span data-ttu-id="dd36d-157">Предоставляет методы для проверки переносимых исполняемых (PE) образов и создания отчетов об ошибках проверки.</span><span class="sxs-lookup"><span data-stu-id="dd36d-157">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="dd36d-158">Интерфейс ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="dd36d-158">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)  
 <span data-ttu-id="dd36d-159">Предоставляет методы для настройки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="dd36d-159">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="dd36d-160">Интерфейс ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="dd36d-160">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)  
 <span data-ttu-id="dd36d-161">Предоставляет методы для доступа к пулу потоков.</span><span class="sxs-lookup"><span data-stu-id="dd36d-161">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="dd36d-162">Интерфейс IDebuggerInfo</span><span class="sxs-lookup"><span data-stu-id="dd36d-162">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)  
 <span data-ttu-id="dd36d-163">Предоставляет методы для получения сведений о состоянии служб отладки.</span><span class="sxs-lookup"><span data-stu-id="dd36d-163">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="dd36d-164">Интерфейс IDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="dd36d-164">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="dd36d-165">Предоставляет методы для уведомления узла о блокировке и разблокировке потоков службами отладки.</span><span class="sxs-lookup"><span data-stu-id="dd36d-165">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="dd36d-166">Интерфейс IGCHost</span><span class="sxs-lookup"><span data-stu-id="dd36d-166">IGCHost Interface</span></span>](igchost-interface.md)  
 <span data-ttu-id="dd36d-167">Предоставляет методы для получения сведений о системе сборки мусора и для управления некоторыми аспектами сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="dd36d-167">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="dd36d-168">Интерфейс IGCHost2</span><span class="sxs-lookup"><span data-stu-id="dd36d-168">IGCHost2 Interface</span></span>](igchost2-interface.md)  
 <span data-ttu-id="dd36d-169">Предоставляет метод [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) , позволяющий основному приложению задавать размер сегмента сборки мусора и максимальный размер нулевого поколения системы сборки мусора для значений, превышающих значение `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="dd36d-169">Provides the [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="dd36d-170">Интерфейс IGCHostControl</span><span class="sxs-lookup"><span data-stu-id="dd36d-170">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)  
 <span data-ttu-id="dd36d-171">Предоставляет метод, позволяющий сборщику мусора запрашивать изменение ограничений виртуальной памяти на узле.</span><span class="sxs-lookup"><span data-stu-id="dd36d-171">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="dd36d-172">Интерфейс IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="dd36d-172">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)  
 <span data-ttu-id="dd36d-173">Предоставляет методы для участия в планировании потоков, которые в противном случае были бы заблокированы для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="dd36d-173">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="dd36d-174">Интерфейс IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-174">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)  
 <span data-ttu-id="dd36d-175">Предоставляет методы, позволяющие основному приложению указывать наборы сборок, которые должны загружаться средой CLR или узлом.</span><span class="sxs-lookup"><span data-stu-id="dd36d-175">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="dd36d-176">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="dd36d-176">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)  
 <span data-ttu-id="dd36d-177">Предоставляет методы, позволяющие основному приложению загружать сборки и модули независимо от среды CLR.</span><span class="sxs-lookup"><span data-stu-id="dd36d-177">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="dd36d-178">Интерфейс IHostAutoEvent</span><span class="sxs-lookup"><span data-stu-id="dd36d-178">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)  
 <span data-ttu-id="dd36d-179">Предоставляет представление события автоматического сброса, реализованного хостом.</span><span class="sxs-lookup"><span data-stu-id="dd36d-179">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="dd36d-180">Интерфейс IHostControl</span><span class="sxs-lookup"><span data-stu-id="dd36d-180">IHostControl Interface</span></span>](ihostcontrol-interface.md)  
 <span data-ttu-id="dd36d-181">Предоставляет методы для настройки загрузки сборок и для определения того, какие интерфейсы размещения поддерживает узел.</span><span class="sxs-lookup"><span data-stu-id="dd36d-181">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="dd36d-182">Интерфейс IHostCrst</span><span class="sxs-lookup"><span data-stu-id="dd36d-182">IHostCrst Interface</span></span>](ihostcrst-interface.md)  
 <span data-ttu-id="dd36d-183">Служит в качестве представления критической секции для потоков в основном приложении.</span><span class="sxs-lookup"><span data-stu-id="dd36d-183">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="dd36d-184">Интерфейс IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-184">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)  
 <span data-ttu-id="dd36d-185">Предоставляет методы, которые уведомляют узел о событиях в механизме сборки мусора, реализованном средой CLR.</span><span class="sxs-lookup"><span data-stu-id="dd36d-185">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="dd36d-186">Интерфейс IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-186">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="dd36d-187">Предоставляет методы, позволяющие среде CLR взаимодействовать с портами завершения ввода-вывода, предоставляемыми узлом.</span><span class="sxs-lookup"><span data-stu-id="dd36d-187">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="dd36d-188">Интерфейс IHostMalloc</span><span class="sxs-lookup"><span data-stu-id="dd36d-188">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)  
 <span data-ttu-id="dd36d-189">Предоставляет методы для CLR, чтобы запрашивать детализированные выделения из кучи через узел.</span><span class="sxs-lookup"><span data-stu-id="dd36d-189">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="dd36d-190">Интерфейс IHostManualEvent</span><span class="sxs-lookup"><span data-stu-id="dd36d-190">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)  
 <span data-ttu-id="dd36d-191">Предоставляет реализацию представления события ручного сброса в узле.</span><span class="sxs-lookup"><span data-stu-id="dd36d-191">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="dd36d-192">Интерфейс IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-192">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)  
 <span data-ttu-id="dd36d-193">Предоставляет методы для среды CLR для выполнения запросов к виртуальной памяти через основное приложение вместо использования стандартных функций виртуальной памяти Win32.</span><span class="sxs-lookup"><span data-stu-id="dd36d-193">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="dd36d-194">Интерфейс IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-194">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)  
 <span data-ttu-id="dd36d-195">Предоставляет методы, уведомляющие узел о действиях, выполняемых средой CLR в случае прерываний, времени ожидания или сбоев.</span><span class="sxs-lookup"><span data-stu-id="dd36d-195">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="dd36d-196">Интерфейс IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="dd36d-196">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)  
 <span data-ttu-id="dd36d-197">Позволяет среде CLR поддерживать сведения о контексте безопасности, реализуемые узлом.</span><span class="sxs-lookup"><span data-stu-id="dd36d-197">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="dd36d-198">Интерфейс IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-198">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)  
 <span data-ttu-id="dd36d-199">Предоставляет методы, обеспечивающие доступ к контексту безопасности выполняющегося потока и управление им.</span><span class="sxs-lookup"><span data-stu-id="dd36d-199">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="dd36d-200">Интерфейс IHostSemaphore</span><span class="sxs-lookup"><span data-stu-id="dd36d-200">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)  
 <span data-ttu-id="dd36d-201">Предоставляет представление семафора, реализованного узлом.</span><span class="sxs-lookup"><span data-stu-id="dd36d-201">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="dd36d-202">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-202">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="dd36d-203">Предоставляет методы для среды CLR для создания примитивов синхронизации путем вызова узла вместо использования функций синхронизации Win32.</span><span class="sxs-lookup"><span data-stu-id="dd36d-203">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="dd36d-204">Интерфейс IHostTask</span><span class="sxs-lookup"><span data-stu-id="dd36d-204">IHostTask Interface</span></span>](ihosttask-interface.md)  
 <span data-ttu-id="dd36d-205">Предоставляет методы, позволяющие среде CLR взаимодействовать с узлом для управления задачами.</span><span class="sxs-lookup"><span data-stu-id="dd36d-205">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="dd36d-206">Интерфейс IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-206">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)  
 <span data-ttu-id="dd36d-207">Предоставляет методы, позволяющие среде CLR работать с задачами через основное приложение, а не использовать стандартные функции потоков или волоконно-оптической операционной системы.</span><span class="sxs-lookup"><span data-stu-id="dd36d-207">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="dd36d-208">Интерфейс IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="dd36d-208">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="dd36d-209">Предоставляет методы для среды CLR для настройки пула потоков и постановки рабочих элементов в очередь в пул потоков.</span><span class="sxs-lookup"><span data-stu-id="dd36d-209">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="dd36d-210">Интерфейс IManagedObject</span><span class="sxs-lookup"><span data-stu-id="dd36d-210">IManagedObject Interface</span></span>](imanagedobject-interface.md)  
 <span data-ttu-id="dd36d-211">Предоставляет методы для управления управляемым объектом.</span><span class="sxs-lookup"><span data-stu-id="dd36d-211">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="dd36d-212">"Иобжександле"</span><span class="sxs-lookup"><span data-stu-id="dd36d-212">"IObjectHandle"</span></span>  
 <span data-ttu-id="dd36d-213">Предоставляет метод для распаковки объектов, перенаправляемых по значению, из косвенного обращения.</span><span class="sxs-lookup"><span data-stu-id="dd36d-213">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="dd36d-214">Интерфейс ITypeName</span><span class="sxs-lookup"><span data-stu-id="dd36d-214">ITypeName Interface</span></span>](itypename-interface.md)  
 <span data-ttu-id="dd36d-215">Предоставляет методы для получения сведений о имени типа.</span><span class="sxs-lookup"><span data-stu-id="dd36d-215">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="dd36d-216">(Этот интерфейс поддерживает платформа .NET Frameworkную инфраструктуру и не предназначен для непосредственного использования в коде.)</span><span class="sxs-lookup"><span data-stu-id="dd36d-216">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="dd36d-217">Интерфейс ITypeNameBuilder</span><span class="sxs-lookup"><span data-stu-id="dd36d-217">ITypeNameBuilder Interface</span></span>](itypenamebuilder-interface.md)  
 <span data-ttu-id="dd36d-218">Предоставляет методы для создания имени типа.</span><span class="sxs-lookup"><span data-stu-id="dd36d-218">Provides methods for building a type name.</span></span> <span data-ttu-id="dd36d-219">(Этот интерфейс поддерживает платформа .NET Frameworkную инфраструктуру и не предназначен для непосредственного использования в коде.)</span><span class="sxs-lookup"><span data-stu-id="dd36d-219">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="dd36d-220">Интерфейс ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="dd36d-220">ITypeNameFactory Interface</span></span>](itypenamefactory-interface.md)  
 <span data-ttu-id="dd36d-221">Предоставляет методы для деконструирования имени типа.</span><span class="sxs-lookup"><span data-stu-id="dd36d-221">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="dd36d-222">(Этот интерфейс поддерживает платформа .NET Frameworkную инфраструктуру и не предназначен для непосредственного использования в коде.)</span><span class="sxs-lookup"><span data-stu-id="dd36d-222">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="dd36d-223">IValidator</span><span class="sxs-lookup"><span data-stu-id="dd36d-223">"IValidator"</span></span>  
 <span data-ttu-id="dd36d-224">Предоставляет методы для проверки переносимых исполняемых (PE) образов и создания отчетов об ошибках проверки.</span><span class="sxs-lookup"><span data-stu-id="dd36d-224">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dd36d-225">См. также</span><span class="sxs-lookup"><span data-stu-id="dd36d-225">Related Sections</span></span>  

 [<span data-ttu-id="dd36d-226">Устаревшие интерфейсы размещения CLR и CoClasses</span><span class="sxs-lookup"><span data-stu-id="dd36d-226">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="dd36d-227">Содержит разделы, описывающие интерфейсы размещения, предоставляемые в платформа .NET Framework версии 1,0 и 1,1.</span><span class="sxs-lookup"><span data-stu-id="dd36d-227">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="dd36d-228">Интерфейсы размещения CLR, добавленные в версиях .NET Framework 4 и 4.5</span><span class="sxs-lookup"><span data-stu-id="dd36d-228">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="dd36d-229">Содержит разделы, описывающие интерфейсы размещения, предоставляемые в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="dd36d-229">Contains topics that describe the hosting interfaces provided in the .NET Framework 4.</span></span>
