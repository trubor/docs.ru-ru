---
title: Практическое руководство. Обработка исключений в параллельных циклах
description: Сведения об обработке исключений в параллельных циклах в .NET. См. пример переноса всех исключений из цикла в System.AggregateException.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 903db7f7318a9067c31af090490bab6dd70fa0ad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734482"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="724b2-104">Практическое руководство. Обработка исключений в параллельных циклах</span><span class="sxs-lookup"><span data-stu-id="724b2-104">How to: Handle Exceptions in Parallel Loops</span></span>

<span data-ttu-id="724b2-105">Перегрузки <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> и <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> не имеют каких-либо специальных механизмов для обработки возможных исключений.</span><span class="sxs-lookup"><span data-stu-id="724b2-105">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="724b2-106">В этом отношении они напоминают обычные циклы `for` и `foreach` (`For` и `For Each` в Visual Basic). Необработанное исключение приводит к завершению цикла сразу после выполнения всех текущих итераций.</span><span class="sxs-lookup"><span data-stu-id="724b2-106">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate as soon as all currently running iterations finish.</span></span>
  
 <span data-ttu-id="724b2-107">При добавлении собственной логики обработки исключений в параллельные циклы обработка случая, в котором подобные исключения могут создаваться в нескольких потоках одновременно, и случая, в котором исключение создается в одном потоке, приводит к созданию еще одного исключения в другом потоке.</span><span class="sxs-lookup"><span data-stu-id="724b2-107">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="724b2-108">Оба случая можно обработать путем заключения всех исключений из цикла в <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="724b2-108">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="724b2-109">В примере ниже показан один из возможных способов.</span><span class="sxs-lookup"><span data-stu-id="724b2-109">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="724b2-110">Если включен режим "Только мой код", Visual Studio иногда прерывает выполнение программы на строке, в которой создается исключение, и выводит сообщение об ошибке "Исключение, которое не может быть обработано пользовательским кодом".</span><span class="sxs-lookup"><span data-stu-id="724b2-110">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="724b2-111">Эта ошибка не является критической.</span><span class="sxs-lookup"><span data-stu-id="724b2-111">This error is benign.</span></span> <span data-ttu-id="724b2-112">Вы можете нажать клавишу F5, чтобы продолжить выполнение программы и увидеть поведение системы при обработке этого исключения, которое продемонстрировано в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="724b2-112">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="724b2-113">Чтобы выполнение программы не прерывалось после первой ошибки в Visual Studio, снимите флажок "Только мой код" в меню **Сервис > Параметры > Отладка > Общие**.</span><span class="sxs-lookup"><span data-stu-id="724b2-113">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="724b2-114">Пример</span><span class="sxs-lookup"><span data-stu-id="724b2-114">Example</span></span>  

 <span data-ttu-id="724b2-115">В этом примере все исключения перехватываются и заключаются в созданный объект <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="724b2-115">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="724b2-116">Вызывающая сторона может решать, какие исключения обрабатывать.</span><span class="sxs-lookup"><span data-stu-id="724b2-116">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="724b2-117">См. также</span><span class="sxs-lookup"><span data-stu-id="724b2-117">See also</span></span>

- [<span data-ttu-id="724b2-118">Параллелизм данных</span><span class="sxs-lookup"><span data-stu-id="724b2-118">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="724b2-119">Лямбда-выражения в PLINQ и TPL</span><span class="sxs-lookup"><span data-stu-id="724b2-119">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
