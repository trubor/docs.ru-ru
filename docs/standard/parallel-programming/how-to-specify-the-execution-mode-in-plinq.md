---
title: Практическое руководство. Задание режима выполнения в PLINQ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: 725f232337952449cd8569b12f65da75569996df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722411"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="c36a3-102">Практическое руководство. Задание режима выполнения в PLINQ</span><span class="sxs-lookup"><span data-stu-id="c36a3-102">How to: Specify the Execution Mode in PLINQ</span></span>

<span data-ttu-id="c36a3-103">В этом примере показано, как принудительно отключить эвристический анализ PLINQ по умолчанию, чтобы параллелизовать запрос независимо от его формы.</span><span class="sxs-lookup"><span data-stu-id="c36a3-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c36a3-104">Этот пример предназначен для демонстрации использования и может выполняться не быстрее аналогичного последовательного запроса LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="c36a3-104">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="c36a3-105">См. дополнительные сведения об [ускорении выполнения в PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c36a3-105">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c36a3-106">Пример</span><span class="sxs-lookup"><span data-stu-id="c36a3-106">Example</span></span>  

 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="c36a3-107">PLINQ разработан для того, чтобы применить преимущества параллелизации.</span><span class="sxs-lookup"><span data-stu-id="c36a3-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="c36a3-108">Но не все запросы станут быстрее при параллельном выполнении.</span><span class="sxs-lookup"><span data-stu-id="c36a3-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="c36a3-109">Например, если запрос содержит только один пользовательский делегат с небольшим числом задач, последовательно запрос выполняется быстрее.</span><span class="sxs-lookup"><span data-stu-id="c36a3-109">For example, when a query contains a single user delegate that does little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="c36a3-110">Это связано с тем, что нагрузка на управление параллельным выполнением превышает полученную выгоду от ускорения работы.</span><span class="sxs-lookup"><span data-stu-id="c36a3-110">Sequential execution is faster because the overhead involved in enabling parallelizing execution is more expensive than the speedup that's obtained.</span></span> <span data-ttu-id="c36a3-111">По этой причине PLINQ не применяет параллелизацию к каждому запросу автоматически.</span><span class="sxs-lookup"><span data-stu-id="c36a3-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="c36a3-112">Сначала он проверяет форму запроса и входящие в него операторы.</span><span class="sxs-lookup"><span data-stu-id="c36a3-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="c36a3-113">Исходя из этих результатов анализа, PLINQ в стандартном режиме выполнения самостоятельно решает, нужно ли выполнять параллельно весь запрос или некоторые его элементы.</span><span class="sxs-lookup"><span data-stu-id="c36a3-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="c36a3-114">Но в некоторых случаях у вас есть больше сведений о запросе, чем доступно PLINQ на основе такого анализа.</span><span class="sxs-lookup"><span data-stu-id="c36a3-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="c36a3-115">Например, вы знаете, что делегат затратный и в любом случае выиграет от применения параллелизации.</span><span class="sxs-lookup"><span data-stu-id="c36a3-115">For example, you may know that a delegate is expensive and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="c36a3-116">В таких случаях вы можете применить метод <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> со значением <xref:System.Linq.ParallelExecutionMode.ForceParallelism>, чтобы PLINQ всегда выполнял этот запрос параллельно.</span><span class="sxs-lookup"><span data-stu-id="c36a3-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c36a3-117">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="c36a3-117">Compiling the Code</span></span>  

 <span data-ttu-id="c36a3-118">Скопируйте и вставьте этот код в [пример данных PLINQ](plinq-data-sample.md), затем вызовите этот метод из `Main`.</span><span class="sxs-lookup"><span data-stu-id="c36a3-118">Cut and paste this code into the [PLINQ Data Sample](plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c36a3-119">См. также</span><span class="sxs-lookup"><span data-stu-id="c36a3-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="c36a3-120">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="c36a3-120">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
