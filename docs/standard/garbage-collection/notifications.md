---
title: Уведомления о сборке мусора
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
ms.openlocfilehash: 70343851ba73af9041014e8654f5df82d8389c39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734781"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="1e46d-102">Уведомления о сборке мусора</span><span class="sxs-lookup"><span data-stu-id="1e46d-102">Garbage Collection Notifications</span></span>

<span data-ttu-id="1e46d-103">В некоторых случаях полная сборка мусора (сборка объектов поколения 2) средой CLR может отрицательно сказаться на производительности.</span><span class="sxs-lookup"><span data-stu-id="1e46d-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="1e46d-104">Это может стать проблемой, особенно для серверов, которые обрабатывают большие объемы запросов. Длительный процесс сборки может привести к потере запросов из-за превышения времени ожидания. Чтобы предотвратить запуск полной сборки мусора в критически важные периоды, вы можете настроить уведомления о ее приближении. Это позволит принять меры и перенести нагрузку на другой экземпляр сервера.</span><span class="sxs-lookup"><span data-stu-id="1e46d-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="1e46d-105">Также вы можете самостоятельно запустить сборку мусора на экземплярах сервера, которые в текущий момент не применяются для обработки запросов.</span><span class="sxs-lookup"><span data-stu-id="1e46d-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="1e46d-106">Метод <xref:System.GC.RegisterForFullGCNotification%2A> позволяет зарегистрироваться для получения уведомлений о приближении полной сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="1e46d-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="1e46d-107">Вы получите два уведомления: при приближении полной сборки мусора и по ее завершении.</span><span class="sxs-lookup"><span data-stu-id="1e46d-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1e46d-108">Только блокировка сборки мусора создает уведомления.</span><span class="sxs-lookup"><span data-stu-id="1e46d-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="1e46d-109">Если включен элемент конфигурации [\<gcConcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), при фоновой сборке мусора уведомления не создаются.</span><span class="sxs-lookup"><span data-stu-id="1e46d-109">When the [\<gcConcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="1e46d-110">Чтобы определить, когда было создано уведомление, используйте методы <xref:System.GC.WaitForFullGCApproach%2A> и <xref:System.GC.WaitForFullGCComplete%2A>.</span><span class="sxs-lookup"><span data-stu-id="1e46d-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="1e46d-111">Как правило, они вызываются в цикле `while`, чтобы постоянно получать перечисление <xref:System.GCNotificationStatus> с информацией о состоянии уведомления.</span><span class="sxs-lookup"><span data-stu-id="1e46d-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="1e46d-112">Если вы получите значение <xref:System.GCNotificationStatus.Succeeded>, можете выполнить следующие действия:</span><span class="sxs-lookup"><span data-stu-id="1e46d-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
- <span data-ttu-id="1e46d-113">В ответ на уведомление, полученное с помощью метода <xref:System.GC.WaitForFullGCApproach%2A>, перераспределите рабочую нагрузку и при необходимости самостоятельно запустите сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="1e46d-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
- <span data-ttu-id="1e46d-114">В ответ на уведомление, полученное с помощью метода <xref:System.GC.WaitForFullGCComplete%2A>, восстановите доступность текущего экземпляра сервера для обработки запросов.</span><span class="sxs-lookup"><span data-stu-id="1e46d-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="1e46d-115">Вы также можете собирать сведения.</span><span class="sxs-lookup"><span data-stu-id="1e46d-115">You can also gather information.</span></span> <span data-ttu-id="1e46d-116">Например, метод <xref:System.GC.CollectionCount%2A> позволяет зафиксировать количество сборок мусора.</span><span class="sxs-lookup"><span data-stu-id="1e46d-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="1e46d-117">Методы <xref:System.GC.WaitForFullGCApproach%2A> и <xref:System.GC.WaitForFullGCComplete%2A> следует использовать совместно.</span><span class="sxs-lookup"><span data-stu-id="1e46d-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="1e46d-118">Вызов только одного из них может привести к непредсказуемым результатам.</span><span class="sxs-lookup"><span data-stu-id="1e46d-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="1e46d-119">Полная сборка мусора</span><span class="sxs-lookup"><span data-stu-id="1e46d-119">Full Garbage Collection</span></span>  

 <span data-ttu-id="1e46d-120">Среда выполнения инициирует полную сборку мусора в одной из следующих ситуаций:</span><span class="sxs-lookup"><span data-stu-id="1e46d-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
- <span data-ttu-id="1e46d-121">В состояние поколения 2 переведен достаточный объем памяти, чтобы выполнить очередную сборку мусора поколения 2.</span><span class="sxs-lookup"><span data-stu-id="1e46d-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="1e46d-122">В состояние кучи для массивных объектов переведен достаточный объем памяти, чтобы выполнить очередную сборку мусора поколения 2.</span><span class="sxs-lookup"><span data-stu-id="1e46d-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="1e46d-123">Уровень сборки мусора поколения 1 повышен до поколения 2 в силу других факторов.</span><span class="sxs-lookup"><span data-stu-id="1e46d-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="1e46d-124">Пороговые значения, указанные в методе <xref:System.GC.RegisterForFullGCNotification%2A>, применяются к двум первым ситуациям.</span><span class="sxs-lookup"><span data-stu-id="1e46d-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="1e46d-125">Но в первом случае вы не обязательно будете получать уведомление в момент, который точно соответствует заданному пропорциональному значению пороговых уровней. Для этого есть две причины:</span><span class="sxs-lookup"><span data-stu-id="1e46d-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
- <span data-ttu-id="1e46d-126">в среде выполнения не проверяется каждое выделение небольших объектов (чтобы не снижать производительность);</span><span class="sxs-lookup"><span data-stu-id="1e46d-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
- <span data-ttu-id="1e46d-127">перевод памяти в состояние поколения 2 выполняется только при сборке мусора поколения 1.</span><span class="sxs-lookup"><span data-stu-id="1e46d-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="1e46d-128">В третьем сценарии также нельзя точно определить время получения уведомлений.</span><span class="sxs-lookup"><span data-stu-id="1e46d-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="1e46d-129">Этот подход не дает гарантий, он очень полезен для устранения негативных последствий несвоевременной полной сборки мусора, так как позволяет перенаправить запросы на время сборки или вызвать ее самостоятельно в более удобное время.</span><span class="sxs-lookup"><span data-stu-id="1e46d-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="1e46d-130">Параметры порогов уведомлений</span><span class="sxs-lookup"><span data-stu-id="1e46d-130">Notification Threshold Parameters</span></span>  

 <span data-ttu-id="1e46d-131">Метод <xref:System.GC.RegisterForFullGCNotification%2A> имеет два параметра, которые позволяют задать пороговые значения для объектов поколения 2 и кучи больших объектов.</span><span class="sxs-lookup"><span data-stu-id="1e46d-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="1e46d-132">При достижении этих значений будет создаваться уведомление о сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="1e46d-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="1e46d-133">Эти параметры описаны в приведенной ниже таблице.</span><span class="sxs-lookup"><span data-stu-id="1e46d-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="1e46d-134">Параметр</span><span class="sxs-lookup"><span data-stu-id="1e46d-134">Parameter</span></span>|<span data-ttu-id="1e46d-135">Описание</span><span class="sxs-lookup"><span data-stu-id="1e46d-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="1e46d-136">Число от 1 до 99, которое указывает условия для создания уведомления в зависимости от объектов, переведенных в состояние поколения 2.</span><span class="sxs-lookup"><span data-stu-id="1e46d-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="1e46d-137">Число от 1 до 99, которое указывает условия для создания уведомления в зависимости от объема объектов, помещенных в кучу больших объектов.</span><span class="sxs-lookup"><span data-stu-id="1e46d-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="1e46d-138">Если вы укажете очень большое значение, вероятность получить уведомление повышается. Но вам придется довольно долго ждать, пока в среде выполнения будет вызвана сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="1e46d-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="1e46d-139">Если вы запустите сборку мусора самостоятельно, будет освобождено больше объектов, чем при сборке мусора, запущенной в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="1e46d-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="1e46d-140">Если вы укажете очень низкое значение, сборку мусора может запуститься в среде выполнения раньше, чем вы получите и (или) обработаете уведомление.</span><span class="sxs-lookup"><span data-stu-id="1e46d-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e46d-141">Пример</span><span class="sxs-lookup"><span data-stu-id="1e46d-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="1e46d-142">Описание</span><span class="sxs-lookup"><span data-stu-id="1e46d-142">Description</span></span>  

 <span data-ttu-id="1e46d-143">В приведенном ниже примере группа серверов обрабатывает входящие веб-запросы.</span><span class="sxs-lookup"><span data-stu-id="1e46d-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="1e46d-144">Для имитации рабочей нагрузки по обработке запросов в коллекцию <xref:System.Collections.Generic.List%601> добавляются массивы байтов.</span><span class="sxs-lookup"><span data-stu-id="1e46d-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="1e46d-145">Каждый сервер регистрируется для получения уведомлений о сборке мусора и запускает поток с пользовательским методом `WaitForFullGCProc` для постоянного наблюдения за перечислением <xref:System.GCNotificationStatus>, которое возвращают методы <xref:System.GC.WaitForFullGCApproach%2A> и <xref:System.GC.WaitForFullGCComplete%2A>.</span><span class="sxs-lookup"><span data-stu-id="1e46d-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="1e46d-146">Методы <xref:System.GC.WaitForFullGCApproach%2A> и <xref:System.GC.WaitForFullGCComplete%2A> при получении уведомлений вызывают соответствующие пользовательские методы для обработки событий.</span><span class="sxs-lookup"><span data-stu-id="1e46d-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
- `OnFullGCApproachNotify`  
  
     <span data-ttu-id="1e46d-147">Этот метод вызывает пользовательский метод `RedirectRequests`, который передает на сервер очереди команду прекратить отправку запросов на свой сервер.</span><span class="sxs-lookup"><span data-stu-id="1e46d-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="1e46d-148">Для имитации этого поведения переменной `bAllocate` уровня класса присваивается значение `false`. После этого выделение новых объектов прекращается.</span><span class="sxs-lookup"><span data-stu-id="1e46d-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="1e46d-149">Теперь вызывается пользовательский метод `FinishExistingRequests`, чтобы завершить обработку текущих запросов на сервере.</span><span class="sxs-lookup"><span data-stu-id="1e46d-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="1e46d-150">Для имитации этого действия коллекция <xref:System.Collections.Generic.List%601> очищается.</span><span class="sxs-lookup"><span data-stu-id="1e46d-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="1e46d-151">И, наконец, в период низкой нагрузки вызывается сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="1e46d-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
- `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="1e46d-152">Этот метод вызывает пользовательский метод `AcceptRequests`, чтобы возобновить прием запросов, так как теперь серверу не угрожает полная сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="1e46d-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="1e46d-153">Для имитации этого поведения переменной `bAllocate` уровня класса присваивается значение `true`, чтобы новые объекты снова добавлялись в коллекцию <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="1e46d-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="1e46d-154">Следующий код содержит метод `Main` для нашего примера:</span><span class="sxs-lookup"><span data-stu-id="1e46d-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="1e46d-155">Следующий код содержит пользовательский метод `WaitForFullGCProc`, при помощи которого выполняется непрерывный цикл проверки уведомлений о сборке мусора:</span><span class="sxs-lookup"><span data-stu-id="1e46d-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="1e46d-156">Следующий код содержит метод `OnFullGCApproachNotify`, вызываемый из</span><span class="sxs-lookup"><span data-stu-id="1e46d-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="1e46d-157">Метод `WaitForFullGCProc`.</span><span class="sxs-lookup"><span data-stu-id="1e46d-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="1e46d-158">Следующий код содержит метод `OnFullGCApproachComplete`, вызываемый из</span><span class="sxs-lookup"><span data-stu-id="1e46d-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="1e46d-159">Метод `WaitForFullGCProc`.</span><span class="sxs-lookup"><span data-stu-id="1e46d-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="1e46d-160">Приведенный ниже код содержит пользовательские методы, которые вызываются из методов `OnFullGCApproachNotify` и `OnFullGCCompleteNotify`.</span><span class="sxs-lookup"><span data-stu-id="1e46d-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="1e46d-161">Пользовательские методы позволяют перенаправить запросы, завершить обработку существующих запросов и возобновить прием запросов после полной сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="1e46d-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="1e46d-162">Полный пример кода выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="1e46d-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1e46d-163">См. также</span><span class="sxs-lookup"><span data-stu-id="1e46d-163">See also</span></span>

- [<span data-ttu-id="1e46d-164">Сборка мусора</span><span class="sxs-lookup"><span data-stu-id="1e46d-164">Garbage Collection</span></span>](index.md)
