---
title: Взаимодействие с другими асинхронными шаблонами и типами
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous design patterns, .NET
- TAP, .NET support for
- Task-based Asynchronous Pattern, .NET support for
- .NET, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
ms.openlocfilehash: 2ae1c514185152dd709fe06018df513fb54b874b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726721"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="ec751-102">Взаимодействие с другими асинхронными шаблонами и типами</span><span class="sxs-lookup"><span data-stu-id="ec751-102">Interop with Other Asynchronous Patterns and Types</span></span>

<span data-ttu-id="ec751-103">Краткая история асинхронных шаблонов в .NET</span><span class="sxs-lookup"><span data-stu-id="ec751-103">A brief history of asynchronous patterns in .NET:</span></span>

- <span data-ttu-id="ec751-104">В .NET Framework 1.0 появился шаблон <xref:System.IAsyncResult>, также известный как [асинхронная модель программирования (APM)](asynchronous-programming-model-apm.md) или шаблон `Begin/End`.</span><span class="sxs-lookup"><span data-stu-id="ec751-104">.NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>
- <span data-ttu-id="ec751-105">В .NET Framework 2.0 была добавлена [асинхронная модель на основе событий (EAP)](event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="ec751-105">.NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>
- <span data-ttu-id="ec751-106">В .NET Framework 4 появилась [асинхронная модель на основе задач (TAP)](task-based-asynchronous-pattern-tap.md), которая заменила APM и EAP и предоставила возможность легко строить процедуры миграции с более ранних шаблонов.</span><span class="sxs-lookup"><span data-stu-id="ec751-106">.NET Framework 4 introduced the [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md), which supersedes both APM and EAP and provides the ability to easily build migration routines from the earlier patterns.</span></span>
  
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="ec751-107">Задачи и асинхронная модель программирования (APM)</span><span class="sxs-lookup"><span data-stu-id="ec751-107">Tasks and the Asynchronous Programming Model (APM)</span></span>

### <a name="from-apm-to-tap"></a><span data-ttu-id="ec751-108">от APM к TAP</span><span class="sxs-lookup"><span data-stu-id="ec751-108">From APM to TAP</span></span>  

 <span data-ttu-id="ec751-109">Так как шаблон [Асинхронная модель программирования (APM)](asynchronous-programming-model-apm.md) структурирован, можно довольно легко создавать оболочки для предоставления реализации APM в качестве реализации TAP.</span><span class="sxs-lookup"><span data-stu-id="ec751-109">Because the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md) pattern is structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="ec751-110">Платформа .NET Framework 4 и более поздних версий включает вспомогательные процедуры в форме перегрузок методов <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> для реализации этого преобразования.</span><span class="sxs-lookup"><span data-stu-id="ec751-110">.NET Framework 4 and later versions include helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="ec751-111">Рассмотрим класс <xref:System.IO.Stream> и его методы <xref:System.IO.Stream.BeginRead%2A> и <xref:System.IO.Stream.EndRead%2A> , которые представляют аналог APM для синхронного метода <xref:System.IO.Stream.Read%2A> :</span><span class="sxs-lookup"><span data-stu-id="ec751-111">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="ec751-112">Можно использовать метод <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> для реализации оболочки TAP этой операции следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ec751-112">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="ec751-113">Эта реализация похожа на следующее:</span><span class="sxs-lookup"><span data-stu-id="ec751-113">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
### <a name="from-tap-to-apm"></a><span data-ttu-id="ec751-114">от TAP к APM</span><span class="sxs-lookup"><span data-stu-id="ec751-114">From TAP to APM</span></span>  

 <span data-ttu-id="ec751-115">Если существующая инфраструктура предполагает использование шаблона APM, также может потребоваться использовать реализацию TAP там, где ожидается реализация APM.</span><span class="sxs-lookup"><span data-stu-id="ec751-115">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="ec751-116">Поскольку задачи можно создавать, а класс <xref:System.Threading.Tasks.Task> реализует интерфейс <xref:System.IAsyncResult>, для этого можно использовать простую вспомогательную функцию.</span><span class="sxs-lookup"><span data-stu-id="ec751-116">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="ec751-117">В следующем коде используется расширение класса <xref:System.Threading.Tasks.Task%601> , но можно использовать почти такую же функцию для неуниверсальных задач.</span><span class="sxs-lookup"><span data-stu-id="ec751-117">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="ec751-118">Теперь рассмотрим случай, когда есть следующая реализация TAP:</span><span class="sxs-lookup"><span data-stu-id="ec751-118">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="ec751-119">При этом необходимо предоставить следующую реализацию APM:</span><span class="sxs-lookup"><span data-stu-id="ec751-119">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="ec751-120">В следующем примере показана одна миграция на APM:</span><span class="sxs-lookup"><span data-stu-id="ec751-120">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="ec751-121">Задачи и асинхронная модель, основанная на событиях</span><span class="sxs-lookup"><span data-stu-id="ec751-121">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  

 <span data-ttu-id="ec751-122">Создание оболочки для реализации [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md) сложнее создания оболочки для шаблона APM, так как шаблон EAP имеет несколько вариантов и менее структурирован, чем шаблон APM.</span><span class="sxs-lookup"><span data-stu-id="ec751-122">Wrapping an [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="ec751-123">В качестве демонстрации следующий код создает оболочку метода `DownloadStringAsync` .</span><span class="sxs-lookup"><span data-stu-id="ec751-123">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="ec751-124">`DownloadStringAsync` принимает универсальный код ресурса (URI), создает событие `DownloadProgressChanged` во время скачивания, чтобы периодически передавать данные о ходе загрузки, а когда загрузка завершена, создает событие `DownloadStringCompleted` .</span><span class="sxs-lookup"><span data-stu-id="ec751-124">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="ec751-125">Конечным результатом является строка, содержащая оглавление страницы по указанному URI.</span><span class="sxs-lookup"><span data-stu-id="ec751-125">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="ec751-126">Задачи и дескрипторы ожидания</span><span class="sxs-lookup"><span data-stu-id="ec751-126">Tasks and Wait Handles</span></span>  
  
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="ec751-127">от дескрипторов ожидания к TAP</span><span class="sxs-lookup"><span data-stu-id="ec751-127">From Wait Handles to TAP</span></span>  

 <span data-ttu-id="ec751-128">Хотя дескрипторы ожидания не реализуют асинхронную модель, опытные разработчики могут использовать класс <xref:System.Threading.WaitHandle> и метод <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> для асинхронных уведомлений, когда задан дескриптор ожидания.</span><span class="sxs-lookup"><span data-stu-id="ec751-128">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="ec751-129">Можно создать оболочку метода <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> для создания альтернативы синхронного ожидания на основе задач для дескриптора ожидания:</span><span class="sxs-lookup"><span data-stu-id="ec751-129">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="ec751-130">С помощью этого метода можно использовать существующие реализации <xref:System.Threading.WaitHandle> в асинхронных методах.</span><span class="sxs-lookup"><span data-stu-id="ec751-130">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="ec751-131">Например, если необходимо регулировать число асинхронных операций, которые выполняются в определенный момент времени, можно использовать семафор (объект <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="ec751-131">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="ec751-132">Можно отрегулировать число операций, выполняемых параллельно, до *N* путем инициализации счетчика семафора равным *N*, выполняя на нем ожидание каждый раз, когда необходимо выполнить операцию, и освобождая его после завершения операции.</span><span class="sxs-lookup"><span data-stu-id="ec751-132">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore's count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you're done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="ec751-133">Можно также создать асинхронный семафор, который не зависит от дескрипторов ожидания и вместо этого работает только с задачами.</span><span class="sxs-lookup"><span data-stu-id="ec751-133">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="ec751-134">Для этого используются методы, описанные в разделе [Consuming the Task-based Asynchronous Pattern](consuming-the-task-based-asynchronous-pattern.md) для построения структур данных на основе <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="ec751-134">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="ec751-135">от TAP к дескрипторам ожидания</span><span class="sxs-lookup"><span data-stu-id="ec751-135">From TAP to Wait Handles</span></span>  

 <span data-ttu-id="ec751-136">Как упоминалось ранее, класс <xref:System.Threading.Tasks.Task> реализует <xref:System.IAsyncResult>, и эта реализация предоставляет свойство <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> , которое возвращает дескриптор ожидания, задаваемое при завершении <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="ec751-136">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="ec751-137">Можно получить <xref:System.Threading.WaitHandle> для <xref:System.Threading.Tasks.Task> следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ec751-137">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="ec751-138">См. также</span><span class="sxs-lookup"><span data-stu-id="ec751-138">See also</span></span>

- <span data-ttu-id="ec751-139">[Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md) (Асинхронный шаблон, основанный на задачах (TAP))</span><span class="sxs-lookup"><span data-stu-id="ec751-139">[Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md)</span></span>
- [<span data-ttu-id="ec751-140">Реализация асинхронной модели на основе задач</span><span class="sxs-lookup"><span data-stu-id="ec751-140">Implementing the Task-based Asynchronous Pattern</span></span>](implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="ec751-141">Consuming the Task-based Asynchronous Pattern</span><span class="sxs-lookup"><span data-stu-id="ec751-141">Consuming the Task-based Asynchronous Pattern</span></span>](consuming-the-task-based-asynchronous-pattern.md)
