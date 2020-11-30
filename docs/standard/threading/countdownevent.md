---
title: CountdownEvent
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
ms.openlocfilehash: 15ff3ee8f4ea18b243f5c3070f1c59df4646a1a4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676482"
---
# <a name="countdownevent"></a><span data-ttu-id="c8ffd-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="c8ffd-102">CountdownEvent</span></span>

<span data-ttu-id="c8ffd-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> представляет собой примитив синхронизации, снимающий блокировку потоков в состоянии ожидания после определенного числа сигналов.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="c8ffd-104"><xref:System.Threading.CountdownEvent> предназначен для таких ситуаций, в которых он может заменить вызовы <xref:System.Threading.ManualResetEvent> или <xref:System.Threading.ManualResetEventSlim> с ручным уменьшением значения переменной перед подачей сигнала о событии.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="c8ffd-105">Например, в алгоритме ветвления и соединения вы можете создать <xref:System.Threading.CountdownEvent> со значением 5 для счетчика сигналов, а затем запустить пять рабочих элементов в пуле потоков, каждый из которых будет вызывать <xref:System.Threading.CountdownEvent.Signal%2A> после завершения работы.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="c8ffd-106">Каждый вызов <xref:System.Threading.CountdownEvent.Signal%2A> уменьшает значение счетчика на 1.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="c8ffd-107">В основном потоке вызов <xref:System.Threading.CountdownEvent.Wait%2A> блокируется до тех пор, пока значение счетчика не достигнет нуля.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8ffd-108">Если ваш код не будет взаимодействовать с устаревшими API синхронизации платформы .NET Framework, вы можете еще проще реализовать параллелизм ветвления-соединения с помощью объектов <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> или метода <xref:System.Threading.Tasks.Parallel.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="c8ffd-109"><xref:System.Threading.CountdownEvent> предоставляет следующие дополнительные возможности:</span><span class="sxs-lookup"><span data-stu-id="c8ffd-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
- <span data-ttu-id="c8ffd-110">Операцию ожидания можно отменить с помощью маркеров отмены.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
- <span data-ttu-id="c8ffd-111">Значение счетчика можно увеличивать после создания экземпляра.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-111">Its signal count can be incremented after the instance is created.</span></span>  
  
- <span data-ttu-id="c8ffd-112">Экземпляры можно использовать повторно после того, как <xref:System.Threading.CountdownEvent.Wait%2A> завершает работу и вызывает метод <xref:System.Threading.CountdownEvent.Reset%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
- <span data-ttu-id="c8ffd-113">Экземпляры поддерживают <xref:System.Threading.WaitHandle> для интеграции с другими API синхронизации .NET, например <xref:System.Threading.WaitHandle.WaitAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET synchronization APIs, such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="c8ffd-114">Основное использование</span><span class="sxs-lookup"><span data-stu-id="c8ffd-114">Basic Usage</span></span>  

 <span data-ttu-id="c8ffd-115">В следующем примере демонстрируется применение рабочих элементов <xref:System.Threading.CountdownEvent> и <xref:System.Threading.ThreadPool>.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="c8ffd-116">CountdownEvent с возможностью отмены</span><span class="sxs-lookup"><span data-stu-id="c8ffd-116">CountdownEvent With Cancellation</span></span>  

 <span data-ttu-id="c8ffd-117">В примере ниже показано, как отменить операцию ожидания для <xref:System.Threading.CountdownEvent> с помощью маркера отмены.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="c8ffd-118">Базовый шаблон соответствует универсальной модели отмены, которая появилась в .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-118">The basic pattern follows the model for unified cancellation, which was introduced in .NET Framework 4.</span></span> <span data-ttu-id="c8ffd-119">Дополнительные сведения см. в статье [Отмена в управляемых потоках](cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="c8ffd-119">For more information, see [Cancellation in Managed Threads](cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="c8ffd-120">Обратите внимание, что операция ожидания не отменяет потоки, отправляющие сигналы.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="c8ffd-121">Как правило, отмена применяется к логической операции, которая включает ожидание событий и все рабочие элементы, которые она синхронизирует.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="c8ffd-122">В этом примере каждому рабочему элементу передается копия маркера отмены, чтобы элемент выполнил необходимые действия для завершения работы.</span><span class="sxs-lookup"><span data-stu-id="c8ffd-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8ffd-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c8ffd-123">See also</span></span>

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
