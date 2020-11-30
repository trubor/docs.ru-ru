---
title: Исключения в управляемых потоках
description: Узнайте, как обрабатываются необработанные исключения в .NET. Большинство необработанных исключений потоков приводит к завершению работы приложения.
ms.date: 03/30/2017
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET],unhandled exceptions
- threading [.NET],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
ms.openlocfilehash: 740cd1b78b96c2fcaecf39a725973d738037f403
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723757"
---
# <a name="exceptions-in-managed-threads"></a><span data-ttu-id="d927d-104">Исключения в управляемых потоках</span><span class="sxs-lookup"><span data-stu-id="d927d-104">Exceptions in managed threads</span></span>

<span data-ttu-id="d927d-105">Среда CLR позволяет большинству необработанных исключений выполняться в потоках.</span><span class="sxs-lookup"><span data-stu-id="d927d-105">The common language runtime allows most unhandled exceptions in threads to proceed naturally.</span></span> <span data-ttu-id="d927d-106">Как правило, это означает, что необработанное исключение будет вызывать завершение работы приложения.</span><span class="sxs-lookup"><span data-stu-id="d927d-106">In most cases this means that the unhandled exception causes the application to terminate.</span></span>
  
<span data-ttu-id="d927d-107">Среда CLR предоставляет поддержку для определенных необработанных исключений, которые используются для управления потоком выполнения программы:</span><span class="sxs-lookup"><span data-stu-id="d927d-107">The common language runtime provides a backstop for certain unhandled exceptions that are used for controlling program flow:</span></span>  
  
- <span data-ttu-id="d927d-108">В потоке создается исключение <xref:System.Threading.ThreadAbortException> из-за вызова <xref:System.Threading.Thread.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="d927d-108">A <xref:System.Threading.ThreadAbortException> is thrown in a thread because <xref:System.Threading.Thread.Abort%2A> was called.</span></span>  
  
- <span data-ttu-id="d927d-109">В потоке создается исключение <xref:System.AppDomainUnloadedException> из-за того, что в данный момент выгружается домен приложения, в котором выполняется поток.</span><span class="sxs-lookup"><span data-stu-id="d927d-109">An <xref:System.AppDomainUnloadedException> is thrown in a thread because the application domain in which the thread is executing is being unloaded.</span></span>  
  
- <span data-ttu-id="d927d-110">Среда CLR или ведущий процесс прерывает выполнение потока путем создания внутреннего исключения.</span><span class="sxs-lookup"><span data-stu-id="d927d-110">The common language runtime or a host process terminates the thread by throwing an internal exception.</span></span>  
  
 <span data-ttu-id="d927d-111">Если любые из этих исключений не обрабатываются в потоках, созданных в среде CLR, исключение завершает поток, однако среда CLR не позволяет исключению выполнять какие-либо дополнительные действия.</span><span class="sxs-lookup"><span data-stu-id="d927d-111">If any of these exceptions are unhandled in threads created by the common language runtime, the exception terminates the thread, but the common language runtime does not allow the exception to proceed further.</span></span>  
  
 <span data-ttu-id="d927d-112">Если эти исключения не обрабатываются в главном потоке или в потоках, которые перешли в среду выполнения из неуправляемого кода, они продолжают выполнение, что приводит к завершению работы приложения.</span><span class="sxs-lookup"><span data-stu-id="d927d-112">If these exceptions are unhandled in the main thread, or in threads that entered the runtime from unmanaged code, they proceed normally, resulting in termination of the application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d927d-113">Среда выполнения может создать необработанное исключение до того, как любой управляемый код сможет установить обработчик исключения.</span><span class="sxs-lookup"><span data-stu-id="d927d-113">It is possible for the runtime to throw an unhandled exception before any managed code has had a chance to install an exception handler.</span></span> <span data-ttu-id="d927d-114">Даже если управляемый код не в состоянии обработать такое исключение, исключение может продолжать выполняться.</span><span class="sxs-lookup"><span data-stu-id="d927d-114">Even though managed code had no chance to handle such an exception, the exception is allowed to proceed naturally.</span></span>  
  
## <a name="exposing-threading-problems-during-development"></a><span data-ttu-id="d927d-115">Создание проблем при работе с потоками во время разработки</span><span class="sxs-lookup"><span data-stu-id="d927d-115">Exposing Threading Problems During Development</span></span>  

 <span data-ttu-id="d927d-116">Если потоки могут завершаться сбоем без уведомления и без завершения работы приложения, при программировании могут оставаться незамеченными серьезные ошибки.</span><span class="sxs-lookup"><span data-stu-id="d927d-116">When threads are allowed to fail silently, without terminating the application, serious programming problems can go undetected.</span></span> <span data-ttu-id="d927d-117">Это создает серьезную проблему для служб и других приложений, которые выполняются продолжительное время.</span><span class="sxs-lookup"><span data-stu-id="d927d-117">This is a particular problem for services and other applications that run for extended periods.</span></span> <span data-ttu-id="d927d-118">В случае сбоя потоков состояние программы постепенно нарушается.</span><span class="sxs-lookup"><span data-stu-id="d927d-118">As threads fail, program state gradually becomes corrupted.</span></span> <span data-ttu-id="d927d-119">Производительность приложения может ухудшаться, или приложение может перестать отвечать на запросы.</span><span class="sxs-lookup"><span data-stu-id="d927d-119">Application performance may degrade, or the application might become unresponsive.</span></span>  
  
 <span data-ttu-id="d927d-120">Предоставление возможности необработанным исключениям продолжать выполняться в потоках, пока операционная система не завершит программу, создает проблемы во время разработки и тестирования.</span><span class="sxs-lookup"><span data-stu-id="d927d-120">Allowing unhandled exceptions in threads to proceed naturally, until the operating system terminates the program, exposes such problems during development and testing.</span></span> <span data-ttu-id="d927d-121">Отчеты об ошибках при завершении программы поддерживают процесс отладки.</span><span class="sxs-lookup"><span data-stu-id="d927d-121">Error reports on program terminations support debugging.</span></span>  
  
## <a name="change-from-previous-versions"></a><span data-ttu-id="d927d-122">Отличия от предыдущих версий</span><span class="sxs-lookup"><span data-stu-id="d927d-122">Change from previous versions</span></span>

<span data-ttu-id="d927d-123">В .NET Framework версий 1.0 и 1.1 среда CLR обеспечивает поддержку для необработанных исключений в следующих ситуациях.</span><span class="sxs-lookup"><span data-stu-id="d927d-123">In .NET Framework versions 1.0 and 1.1, the common language runtime provides a backstop for unhandled exceptions in the following situations:</span></span>  
  
- <span data-ttu-id="d927d-124">В потоке пула потоков необработанные исключения больше не могут существовать.</span><span class="sxs-lookup"><span data-stu-id="d927d-124">There is no such thing as an unhandled exception on a thread pool thread.</span></span> <span data-ttu-id="d927d-125">Если задача создает исключение, которое остается необработанным, среда выполнения отображает трассировку стека исключений на консоли, а затем возвращает поток в пул потоков.</span><span class="sxs-lookup"><span data-stu-id="d927d-125">When a task throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then returns the thread to the thread pool.</span></span>  
  
- <span data-ttu-id="d927d-126">В потоке, созданном методом <xref:System.Threading.Thread.Start%2A> класса <xref:System.Threading.Thread>, необработанные исключения не могут существовать.</span><span class="sxs-lookup"><span data-stu-id="d927d-126">There is no such thing as an unhandled exception on a thread created with the <xref:System.Threading.Thread.Start%2A> method of the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="d927d-127">Если код, выполняемый в таком потоке, создает исключение, которое остается необработанным, среда выполнения отображает трассировку стека исключений на консоли и корректно завершает поток.</span><span class="sxs-lookup"><span data-stu-id="d927d-127">When code running on such a thread throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then gracefully terminates the thread.</span></span>  
  
- <span data-ttu-id="d927d-128">В потоке метода завершения необработанные исключения больше не могут существовать.</span><span class="sxs-lookup"><span data-stu-id="d927d-128">There is no such thing as an unhandled exception on the finalizer thread.</span></span> <span data-ttu-id="d927d-129">Если метод завершения создает исключение, которое остается необработанным, среда выполнения отображает трассировку стека исключений на консоли и позволяет потоку метода завершения продолжить выполнение работающих методов завершения.</span><span class="sxs-lookup"><span data-stu-id="d927d-129">When a finalizer throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then allows the finalizer thread to resume running finalizers.</span></span>  
  
 <span data-ttu-id="d927d-130">Основное или фоновое состояние управляемого потока не влияет на такое поведение.</span><span class="sxs-lookup"><span data-stu-id="d927d-130">The foreground or background status of a managed thread does not affect this behavior.</span></span>  
  
 <span data-ttu-id="d927d-131">Для необработанных исключений в потоках, происходящих в неуправляемом коде, существует не такая заметная разница.</span><span class="sxs-lookup"><span data-stu-id="d927d-131">For unhandled exceptions on threads originating in unmanaged code, the difference is more subtle.</span></span> <span data-ttu-id="d927d-132">Диалог с JIT-присоединением среды выполнения выгружает диалог операционной системы для управляемых или собственных исключений в потоках, которые прошли через машинный код.</span><span class="sxs-lookup"><span data-stu-id="d927d-132">The runtime JIT-attach dialog preempts the operating system dialog for managed exceptions or native exceptions on threads that have passed through native code.</span></span> <span data-ttu-id="d927d-133">Процесс завершается во всех случаях.</span><span class="sxs-lookup"><span data-stu-id="d927d-133">The process terminates in all cases.</span></span>

### <a name="migration"></a><span data-ttu-id="d927d-134">Миграция</span><span class="sxs-lookup"><span data-stu-id="d927d-134">Migration</span></span>

<span data-ttu-id="d927d-135">Если при переходе с .NET Framework 1.0 или 1.1 вы используете возможность поддержки среды выполнения, например для завершения потоков, рекомендуется одна из следующих стратегий перехода.</span><span class="sxs-lookup"><span data-stu-id="d927d-135">If you are migrating from .NET Framework 1.0 or 1.1 and took advantage of the runtime backstop, for example to terminate threads, consider one of the following migration strategies:</span></span>  
  
- <span data-ttu-id="d927d-136">Реструктурируйте код, чтобы при получении сигнала поток корректно выполнял выход.</span><span class="sxs-lookup"><span data-stu-id="d927d-136">Restructure the code so the thread exits gracefully when a signal is received.</span></span>  
  
- <span data-ttu-id="d927d-137">Использование метода <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> для отмены потока.</span><span class="sxs-lookup"><span data-stu-id="d927d-137">Use the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method to abort the thread.</span></span>  
  
- <span data-ttu-id="d927d-138">Если поток необходимо остановить, чтобы было можно продолжить завершение процесса, сделайте поток фоновым, чтобы он автоматически завершался при выходе процесса.</span><span class="sxs-lookup"><span data-stu-id="d927d-138">If a thread must be stopped so that process termination can proceed, make the thread a background thread so that it is automatically terminated on process exit.</span></span>  
  
<span data-ttu-id="d927d-139">Во всех случаях стратегия должна соответствовать правилам разработки исключений.</span><span class="sxs-lookup"><span data-stu-id="d927d-139">In all cases, the strategy should follow the design guidelines for exceptions.</span></span> <span data-ttu-id="d927d-140">См. раздел [Правила разработки исключений](../design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="d927d-140">See [Design Guidelines for Exceptions](../design-guidelines/exceptions.md).</span></span>  
  
<span data-ttu-id="d927d-141">В качестве временной меры обеспечения совместимости администраторы могут поместить флаг совместимости в раздел `<runtime>` файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="d927d-141">As a temporary compatibility measure, administrators can place a compatibility flag in the `<runtime>` section of the application configuration file.</span></span> <span data-ttu-id="d927d-142">Это приведет к возврату среды CLR к поведению версий 1.0 и 1.1.</span><span class="sxs-lookup"><span data-stu-id="d927d-142">This causes the common language runtime to revert to the behavior of versions 1.0 and 1.1.</span></span>  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a><span data-ttu-id="d927d-143">Переопределение узла</span><span class="sxs-lookup"><span data-stu-id="d927d-143">Host Override</span></span>

<span data-ttu-id="d927d-144">Неуправляемый узел может использовать интерфейс [ICLRPolicyManager](../../framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) в API размещения для переопределения политики необработанных исключений по умолчанию среды CLR.</span><span class="sxs-lookup"><span data-stu-id="d927d-144">An unmanaged host can use the [ICLRPolicyManager](../../framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface in the Hosting API to override the default unhandled exception policy of the common language runtime.</span></span> <span data-ttu-id="d927d-145">Чтобы задать политику для необработанных исключений, используется функция [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md).</span><span class="sxs-lookup"><span data-stu-id="d927d-145">The [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) function is used to set the policy for unhandled exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d927d-146">См. также</span><span class="sxs-lookup"><span data-stu-id="d927d-146">See also</span></span>

- [<span data-ttu-id="d927d-147">Основы управляемых потоков</span><span class="sxs-lookup"><span data-stu-id="d927d-147">Managed Threading Basics</span></span>](managed-threading-basics.md)
