---
title: Практическое руководство. Указание степени параллелизма в блоке потока данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
ms.openlocfilehash: 76ab17750edb6aac72a6c74da67ecbc14a4edcdc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722457"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a><span data-ttu-id="ef078-102">Практическое руководство. Указание степени параллелизма в блоке потока данных</span><span class="sxs-lookup"><span data-stu-id="ef078-102">How to: Specify the Degree of Parallelism in a Dataflow Block</span></span>

<span data-ttu-id="ef078-103">В этом документе описывается, как задать свойство <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType>, чтобы позволить блоку выполнения потока данных обрабатывать более одного сообщения единовременно.</span><span class="sxs-lookup"><span data-stu-id="ef078-103">This document describes how to set the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> property to enable an execution dataflow block to process more than one message at a time.</span></span> <span data-ttu-id="ef078-104">Это удобно при наличии блока потока данных, который выполняет длительное вычисление и может получить выгоду от обработки сообщений параллельным образом.</span><span class="sxs-lookup"><span data-stu-id="ef078-104">Doing this is useful when you have a dataflow block that performs a long-running computation and can benefit from processing messages in parallel.</span></span> <span data-ttu-id="ef078-105">В этом примере используется класс <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> для параллельного выполнения нескольких операций потока данных; однако можно задать максимальную степень параллелизма в любом из предопределенных типов блоков выполнения, предоставляемых библиотекой потоков данных: <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType> и <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef078-105">This example uses the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> class to perform multiple dataflow operations concurrently; however, you can specify the maximum degree of parallelism in any of the predefined execution block types that the TPL Dataflow Library provides, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="ef078-106">Пример</span><span class="sxs-lookup"><span data-stu-id="ef078-106">Example</span></span>  

 <span data-ttu-id="ef078-107">В следующем примере выполняется два вычисления потока данных и выводится остаток времени, необходимый для каждого вычисления.</span><span class="sxs-lookup"><span data-stu-id="ef078-107">The following example performs two dataflow computations and prints the elapsed time that is required for each computation.</span></span> <span data-ttu-id="ef078-108">Первое вычисление указывает максимальную степень параллелизма 1, что является значением по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ef078-108">The first computation specifies a maximum degree of parallelism of 1, which is the default.</span></span> <span data-ttu-id="ef078-109">Максимальная степень параллелизма 1 заставляет блок потока данных обрабатывать сообщения последовательно.</span><span class="sxs-lookup"><span data-stu-id="ef078-109">A maximum degree of parallelism of 1 causes the dataflow block to process messages serially.</span></span> <span data-ttu-id="ef078-110">Второе вычисление напоминает первое за исключением того, что для него указывается максимальная степень параллелизма, равная числу доступных процессоров.</span><span class="sxs-lookup"><span data-stu-id="ef078-110">The second computation resembles the first, except that it specifies a maximum degree of parallelism that is equal to the number of available processors.</span></span> <span data-ttu-id="ef078-111">Это позволяет блоку потока данных выполнять несколько операций параллельно.</span><span class="sxs-lookup"><span data-stu-id="ef078-111">This enables the dataflow block to perform multiple operations in parallel.</span></span>  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ef078-112">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="ef078-112">Robust Programming</span></span>  

 <span data-ttu-id="ef078-113">По умолчанию все предопределенные блоки потока данных распространяют сообщения в том порядке, в котором они их получают.</span><span class="sxs-lookup"><span data-stu-id="ef078-113">By default, each predefined dataflow block propagates out messages in the order in which the messages are received.</span></span>  <span data-ttu-id="ef078-114">Хотя при указании максимальной степени параллелизма больше 1 несколько сообщений обрабатываются одновременно, они по-прежнему распространяются в порядке, в котором были получены.</span><span class="sxs-lookup"><span data-stu-id="ef078-114">Although multiple messages are processed simultaneously when you specify a maximum degree of parallelism that is greater than 1, they are still propagated out in the order in which they are received.</span></span>  
  
 <span data-ttu-id="ef078-115">Поскольку свойство <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> представляет максимальную степень параллелизма, блок потока данных может выполняться с меньшей степенью параллелизма, чем задано.</span><span class="sxs-lookup"><span data-stu-id="ef078-115">Because the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> property represents the maximum degree of parallelism, the dataflow block might execute with a lesser degree of parallelism than you specify.</span></span> <span data-ttu-id="ef078-116">Блок потока данных может использовать меньшую степень параллелизма для удовлетворения функциональных требований или при недостатке доступных системных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="ef078-116">The dataflow block can use a lesser degree of parallelism to meet its functional requirements or to account for a lack of available system resources.</span></span> <span data-ttu-id="ef078-117">Блок потока данных никогда не выбирает степень параллелизма, превосходящую указанную.</span><span class="sxs-lookup"><span data-stu-id="ef078-117">A dataflow block never chooses a greater degree of parallelism than you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef078-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ef078-118">See also</span></span>

- [<span data-ttu-id="ef078-119">Поток данных</span><span class="sxs-lookup"><span data-stu-id="ef078-119">Dataflow</span></span>](dataflow-task-parallel-library.md)
