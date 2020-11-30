---
title: Практическое руководство. Извлечение вложенной задачи из оболочки
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: 3eec3b7e8cc76ee171d88a7886b4983000848084
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722626"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="c88f0-102">Практическое руководство. Извлечение вложенной задачи из оболочки</span><span class="sxs-lookup"><span data-stu-id="c88f0-102">How to: Unwrap a Nested Task</span></span>

<span data-ttu-id="c88f0-103">Вы можете вернуть задачу из метода, и затем ожидать ее выполнения или продолжить работу после нее, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c88f0-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="c88f0-104">В предыдущем примере свойство <xref:System.Threading.Tasks.Task%601.Result%2A> имеет тип `string` (`String` в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c88f0-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="c88f0-105">Но в некоторых сценариях будет удобно создать в задаче другую задачу и возвратить эту вложенную задачу.</span><span class="sxs-lookup"><span data-stu-id="c88f0-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="c88f0-106">В этом случае `TResult` вызывающей задачи является новой задачей.</span><span class="sxs-lookup"><span data-stu-id="c88f0-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="c88f0-107">В следующем примере в свойстве Result возвращается `Task<Task<string>>` (в C#) или `Task(Of Task(Of String))` (в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c88f0-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="c88f0-108">Вы можете написать свой код, который распаковывает внешнюю задачу и извлекает исходную задачу и ее свойство <xref:System.Threading.Tasks.Task%601.Result%2A>. Но обработка исключений и возможных запросов отмены существенно усложняет такой код.</span><span class="sxs-lookup"><span data-stu-id="c88f0-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="c88f0-109">Поэтому в такой ситуации мы рекомендуем использовать один из методов расширения <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c88f0-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="c88f0-110">С помощью методов <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> можно преобразовать любой объект `Task<Task>` или `Task<Task<TResult>>` (`Task(Of Task)` или `Task(Of Task(Of TResult))` в Visual Basic) в `Task` или `Task<TResult>` (`Task(Of TResult)` в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c88f0-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="c88f0-111">Новая задача в полной мере представляет внутреннюю вложенную задачу с поддержкой состояния отмены и всех исключений.</span><span class="sxs-lookup"><span data-stu-id="c88f0-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c88f0-112">Пример</span><span class="sxs-lookup"><span data-stu-id="c88f0-112">Example</span></span>  

 <span data-ttu-id="c88f0-113">В следующем примере показано, как использовать методы расширения <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="c88f0-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="c88f0-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c88f0-114">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [<span data-ttu-id="c88f0-115">Асинхронное программирование на основе задач</span><span class="sxs-lookup"><span data-stu-id="c88f0-115">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
