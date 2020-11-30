---
title: Практическое руководство. Отмена запроса PLINQ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
ms.openlocfilehash: f8ca723ca3b9b9428c95651ebe2fa7d92e48ebbb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713292"
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="c25f8-102">Практическое руководство. Отмена запроса PLINQ</span><span class="sxs-lookup"><span data-stu-id="c25f8-102">How to: Cancel a PLINQ Query</span></span>

<span data-ttu-id="c25f8-103">В приведенных ниже примерах показаны два способа отмены запроса PLINQ.</span><span class="sxs-lookup"><span data-stu-id="c25f8-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="c25f8-104">В первом примере отменяется запрос, который состоит в основном из обхода данных.</span><span class="sxs-lookup"><span data-stu-id="c25f8-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="c25f8-105">Во втором примере отменяется запрос, который содержит ресурсоемкую функцию.</span><span class="sxs-lookup"><span data-stu-id="c25f8-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>

> [!NOTE]
> <span data-ttu-id="c25f8-106">Если включен режим "Только мой код", Visual Studio прерывает выполнение программы на той строке, в которой создается исключение, и выводит сообщение об ошибке "Exception not handled by user code" (Исключение, не обработанное пользовательским кодом).</span><span class="sxs-lookup"><span data-stu-id="c25f8-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="c25f8-107">Эта ошибка не является критической.</span><span class="sxs-lookup"><span data-stu-id="c25f8-107">This error is benign.</span></span> <span data-ttu-id="c25f8-108">Вы можете нажать клавишу F5, чтобы продолжить выполнение программы и увидеть поведение системы при обработке этого исключения, которое продемонстрировано в примерах ниже.</span><span class="sxs-lookup"><span data-stu-id="c25f8-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="c25f8-109">Чтобы выполнение программы не прерывалось после первой ошибки в Visual Studio, снимите флажок "Только мой код" в меню **Сервис > Параметры > Отладка > Общие**.</span><span class="sxs-lookup"><span data-stu-id="c25f8-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="c25f8-110">Этот пример предназначен для демонстрации использования и может выполняться не быстрее аналогичного последовательного запроса LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="c25f8-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="c25f8-111">См. дополнительные сведения об [ускорении выполнения в PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c25f8-111">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="c25f8-112">Пример</span><span class="sxs-lookup"><span data-stu-id="c25f8-112">Example</span></span>

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

<span data-ttu-id="c25f8-113">Платформа PLINQ не помещает единственное <xref:System.OperationCanceledException> в <xref:System.AggregateException?displayProperty=nameWithType>. <xref:System.OperationCanceledException> нужно обрабатывать в отдельном блоке catch.</span><span class="sxs-lookup"><span data-stu-id="c25f8-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="c25f8-114">Если один или несколько пользовательских делегатов создают исключение OperationCanceledException(externalCT) (с помощью внешнего объекта <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), но не создают других исключений, и при этом запрос был определен как `AsParallel().WithCancellation(externalCT)`, то PLINQ выдает одно исключение <xref:System.OperationCanceledException> (externalCT), но не <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c25f8-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c25f8-115">Тем не менее, если один пользовательский делегат создает исключение <xref:System.OperationCanceledException>, а другой делегат создает исключение другого типа, то оба этих исключения помещаются в <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="c25f8-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>

<span data-ttu-id="c25f8-116">Общие рекомендации по отмене:</span><span class="sxs-lookup"><span data-stu-id="c25f8-116">The general guidance on cancellation is as follows:</span></span>

1. <span data-ttu-id="c25f8-117">Если вы отменяете пользовательский делегат, известите PLINQ о внешнем <xref:System.Threading.CancellationToken> и создайте исключение <xref:System.OperationCanceledException>(externalCT).</span><span class="sxs-lookup"><span data-stu-id="c25f8-117">If you perform user-delegate cancellation, you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>

2. <span data-ttu-id="c25f8-118">Если выполняется только отмена и нет других исключений, обрабатывайте <xref:System.OperationCanceledException>, а не <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="c25f8-118">If cancellation occurs and no other exceptions are thrown, then handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>

## <a name="example"></a><span data-ttu-id="c25f8-119">Пример</span><span class="sxs-lookup"><span data-stu-id="c25f8-119">Example</span></span>

<span data-ttu-id="c25f8-120">В следующем примере показано, как правильно обрабатывать отмену пользовательского кода, который содержит ресурсоемкую функцию.</span><span class="sxs-lookup"><span data-stu-id="c25f8-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

<span data-ttu-id="c25f8-121">Если вы обрабатываете отмену в пользовательском коде, нет необходимости использовать <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> в определении запроса.</span><span class="sxs-lookup"><span data-stu-id="c25f8-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="c25f8-122">Но мы все же рекомендуем использовать <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>, ведь <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> не влияет на производительность запросов, но зато позволяет обрабатывать отмену как в операторах запроса, так и в пользовательском коде.</span><span class="sxs-lookup"><span data-stu-id="c25f8-122">However, we recommended that you do use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>, because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>

<span data-ttu-id="c25f8-123">Чтобы обеспечить высокую скорость реагирования системы, мы рекомендуем проверять отмену приблизительно каждую миллисекунду. Впрочем, здесь считается допустимым любой период вплоть до 10 мс.</span><span class="sxs-lookup"><span data-stu-id="c25f8-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="c25f8-124">Частота проверок должна быть такой, чтобы не снижать производительность кода.</span><span class="sxs-lookup"><span data-stu-id="c25f8-124">This frequency should not have a negative impact on your code's performance.</span></span>

<span data-ttu-id="c25f8-125">Если удаляется перечислитель, например когда код прерывается вне цикла foreach (For Each в Visual Basic), выполняющего итерацию по результатам запроса, то этот запрос отменяется без создания исключений.</span><span class="sxs-lookup"><span data-stu-id="c25f8-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is canceled, but no exception is thrown.</span></span>

## <a name="see-also"></a><span data-ttu-id="c25f8-126">См. также</span><span class="sxs-lookup"><span data-stu-id="c25f8-126">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="c25f8-127">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="c25f8-127">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
- [<span data-ttu-id="c25f8-128">Отмена в управляемых потоках</span><span class="sxs-lookup"><span data-stu-id="c25f8-128">Cancellation in Managed Threads</span></span>](../threading/cancellation-in-managed-threads.md)
