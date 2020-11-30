---
title: Практическое руководство. Повышение скорости выполнения небольших тел циклов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
ms.openlocfilehash: 2597e37ed5901d704c94ff960bcb4b2c97633392
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722408"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="daa70-102">Практическое руководство. Повышение скорости выполнения небольших тел циклов</span><span class="sxs-lookup"><span data-stu-id="daa70-102">How to: Speed Up Small Loop Bodies</span></span>

<span data-ttu-id="daa70-103">Когда цикл <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> имеет небольшое тело, он может выполняться значительно медленнее, чем эквивалентный последовательный цикл, такой как цикл [for](../../csharp/language-reference/keywords/for.md) в C# и цикл [For](/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="daa70-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](../../csharp/language-reference/keywords/for.md) loop in C# and the [For](/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) loop in Visual Basic.</span></span> <span data-ttu-id="daa70-104">Снижение производительности происходит вследствие нагрузки, связанной с секционированием данных и стоимостью вызова делегата в каждой итерации цикла.</span><span class="sxs-lookup"><span data-stu-id="daa70-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="daa70-105">Для разрешения таких сценариев класс <xref:System.Collections.Concurrent.Partitioner> предоставляет метод <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType>, который позволяет выполнять последовательный цикл для тела делегата, чтобы делегат вызывался только один раз для каждой секции, а не по разу в каждой итерации.</span><span class="sxs-lookup"><span data-stu-id="daa70-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="daa70-106">Дополнительные сведения см. в разделе [Пользовательские разделители для PLINQ и TPL](custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="daa70-106">For more information, see [Custom Partitioners for PLINQ and TPL](custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="daa70-107">Пример</span><span class="sxs-lookup"><span data-stu-id="daa70-107">Example</span></span>  

 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="daa70-108">Подход, продемонстрированный в данном примере, полезно использовать в тех случаях, когда цикл выполняет минимальный объем работ.</span><span class="sxs-lookup"><span data-stu-id="daa70-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="daa70-109">Когда работа начнет потреблять больше вычислительных ресурсов, возможно, вы получите такую же или более высокую производительность с помощью цикла <xref:System.Threading.Tasks.Parallel.For%2A> или <xref:System.Threading.Tasks.Parallel.ForEach%2A> с разделителем по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="daa70-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daa70-110">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="daa70-110">See also</span></span>

- [<span data-ttu-id="daa70-111">Параллелизм данных</span><span class="sxs-lookup"><span data-stu-id="daa70-111">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="daa70-112">Пользовательские разделители для PLINQ и TPL</span><span class="sxs-lookup"><span data-stu-id="daa70-112">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="daa70-113">Итераторы (C#)</span><span class="sxs-lookup"><span data-stu-id="daa70-113">Iterators (C#)</span></span>](../../csharp/programming-guide/concepts/iterators.md)
- <span data-ttu-id="daa70-114">[Iterators (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md) (Итераторы (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="daa70-114">[Iterators (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md)</span></span>
- [<span data-ttu-id="daa70-115">Лямбда-выражения в PLINQ и TPL</span><span class="sxs-lookup"><span data-stu-id="daa70-115">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
