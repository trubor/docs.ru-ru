---
title: Практическое руководство. Написание пользовательской агрегатной функции PLINQ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: dc03802c960c0926380d7b7fa44fdf436b8fea89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734261"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="58646-102">Практическое руководство. Написание пользовательской агрегатной функции PLINQ</span><span class="sxs-lookup"><span data-stu-id="58646-102">How to: Write a Custom PLINQ Aggregate Function</span></span>

<span data-ttu-id="58646-103">Этот пример демонстрирует, как использовать метод <xref:System.Linq.ParallelEnumerable.Aggregate%2A> для применения пользовательской функции агрегирования к исходной последовательности.</span><span class="sxs-lookup"><span data-stu-id="58646-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="58646-104">Этот пример предназначен для демонстрации использования и может выполняться не быстрее аналогичного последовательного запроса LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="58646-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="58646-105">Дополнительные сведения см. в статье [Общее представление об ускорении выполнения в PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="58646-105">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58646-106">Пример</span><span class="sxs-lookup"><span data-stu-id="58646-106">Example</span></span>  

 <span data-ttu-id="58646-107">Следующий пример вычисляет стандартное отклонение для последовательности целых чисел.</span><span class="sxs-lookup"><span data-stu-id="58646-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="58646-108">В этом примере используется перегрузка стандартного оператора запроса Aggregate, уникального для PLINQ.</span><span class="sxs-lookup"><span data-stu-id="58646-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="58646-109">Эта перегрузка принимает дополнительный <xref:System.Func%603?displayProperty=nameWithType> в качестве третьего входного параметра.</span><span class="sxs-lookup"><span data-stu-id="58646-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="58646-110">Этот делегат объединяет результаты из всех потоков и выполняет окончательный расчет на основе объединенных результатов.</span><span class="sxs-lookup"><span data-stu-id="58646-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="58646-111">В этом примере он складывает суммы из всех потоков.</span><span class="sxs-lookup"><span data-stu-id="58646-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="58646-112">Если тело лямбда-выражения состоит из одного выражения, то возвращаемое значение делегата <xref:System.Func%602?displayProperty=nameWithType> принимает значение этого выражения.</span><span class="sxs-lookup"><span data-stu-id="58646-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58646-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="58646-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="58646-114">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="58646-114">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
