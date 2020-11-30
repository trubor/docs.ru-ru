---
title: Практическое руководство. Прослушивание нескольких запросов на отмену
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
ms.openlocfilehash: e5ec32d486dd5eafc8c456c5a4b0b3297f043499
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728528"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="3972d-102">Практическое руководство. Прослушивание нескольких запросов на отмену</span><span class="sxs-lookup"><span data-stu-id="3972d-102">How to: Listen for Multiple Cancellation Requests</span></span>

<span data-ttu-id="3972d-103">В этом примере показано, как одновременно прослушивать два маркера отмены, любой из которых запускает отмену операции.</span><span class="sxs-lookup"><span data-stu-id="3972d-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3972d-104">Если включен режим "Только мой код", Visual Studio иногда прерывает выполнение программы на строке, в которой создается исключение, и выводит сообщение об ошибке "Исключение, которое не может быть обработано пользовательским кодом".</span><span class="sxs-lookup"><span data-stu-id="3972d-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="3972d-105">Эта ошибка не является критической.</span><span class="sxs-lookup"><span data-stu-id="3972d-105">This error is benign.</span></span> <span data-ttu-id="3972d-106">Вы можете нажать клавишу F5, чтобы продолжить выполнение программы и увидеть поведение системы при обработке этого исключения, которое продемонстрировано в примерах ниже.</span><span class="sxs-lookup"><span data-stu-id="3972d-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="3972d-107">Чтобы выполнение программы не прерывалось после первой ошибки в Visual Studio, снимите флажок "Только мой код" в меню **Сервис > Параметры > Отладка > Общие**.</span><span class="sxs-lookup"><span data-stu-id="3972d-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3972d-108">Пример</span><span class="sxs-lookup"><span data-stu-id="3972d-108">Example</span></span>  

 <span data-ttu-id="3972d-109">В следующем примере используется метод <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> для объединения двух маркеров в один.</span><span class="sxs-lookup"><span data-stu-id="3972d-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="3972d-110">Это позволяет передавать маркер в методы, которые принимают в качестве аргумента только один маркер отмены.</span><span class="sxs-lookup"><span data-stu-id="3972d-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="3972d-111">В этом примере показан типичный сценарий, в котором методу нужно одновременно отслеживать два маркера: полученный вне класса и созданный внутри класса.</span><span class="sxs-lookup"><span data-stu-id="3972d-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="3972d-112">Если связанный токен создает исключение <xref:System.OperationCanceledException>, в это исключение передается именно связанный маркер, а не один из тех, на основе которых он создан.</span><span class="sxs-lookup"><span data-stu-id="3972d-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="3972d-113">Чтобы определить, какой из маркеров использовался для отмены, напрямую проверьте состояние объединенных маркеров.</span><span class="sxs-lookup"><span data-stu-id="3972d-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="3972d-114">В этом примере никогда не возникнет исключение <xref:System.AggregateException>, но мы включаем его перехват, поскольку в реальных сценариях любые исключения, кроме <xref:System.OperationCanceledException>, передаются из делегата задачи именно в оболочке <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="3972d-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.AggregateException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3972d-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3972d-115">See also</span></span>

- [<span data-ttu-id="3972d-116">Отмена в управляемых потоках</span><span class="sxs-lookup"><span data-stu-id="3972d-116">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
