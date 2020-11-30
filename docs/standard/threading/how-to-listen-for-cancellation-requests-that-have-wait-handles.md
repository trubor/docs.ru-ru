---
title: Практическое руководство. Прослушивание запросов на отмену, содержащих дескрипторы ожидания
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
ms.openlocfilehash: 74b32144a1c49fe6adfc5aa1fbdcf5dc9c8a4dd7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728502"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="4917a-102">Практическое руководство. Прослушивание запросов на отмену, содержащих дескрипторы ожидания</span><span class="sxs-lookup"><span data-stu-id="4917a-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>

<span data-ttu-id="4917a-103">Если метод блокируется на время ожидания сигнала события, он не может проверить значение токена отмены и своевременно отреагировать на него.</span><span class="sxs-lookup"><span data-stu-id="4917a-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="4917a-104">Первый пример демонстрирует, как эту проблему можно решить для таких событий, как <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, которые не реализуют поддержку унифицированной инфраструктуры отмены.</span><span class="sxs-lookup"><span data-stu-id="4917a-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="4917a-105">Второй пример демонстрирует более простой подход с применением <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, который поддерживает унифицированную отмену.</span><span class="sxs-lookup"><span data-stu-id="4917a-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4917a-106">Если включен режим "Только мой код", Visual Studio иногда прерывает выполнение программы на строке, в которой создается исключение, и выводит сообщение об ошибке "Исключение, которое не может быть обработано пользовательским кодом".</span><span class="sxs-lookup"><span data-stu-id="4917a-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="4917a-107">Эта ошибка не является критической.</span><span class="sxs-lookup"><span data-stu-id="4917a-107">This error is benign.</span></span> <span data-ttu-id="4917a-108">Вы можете нажать клавишу F5, чтобы продолжить выполнение программы и увидеть поведение системы при обработке этого исключения, которое продемонстрировано в примерах ниже.</span><span class="sxs-lookup"><span data-stu-id="4917a-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="4917a-109">Чтобы выполнение программы не прерывалось после первой ошибки в Visual Studio, снимите флажок "Только мой код" в меню **Сервис > Параметры > Отладка > Общие**.</span><span class="sxs-lookup"><span data-stu-id="4917a-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4917a-110">Пример</span><span class="sxs-lookup"><span data-stu-id="4917a-110">Example</span></span>  

 <span data-ttu-id="4917a-111">Следующий пример с помощью <xref:System.Threading.ManualResetEvent> демонстрирует, как разблокировать дескрипторы ожидания, не поддерживающие унифицированную отмену.</span><span class="sxs-lookup"><span data-stu-id="4917a-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="4917a-112">Пример</span><span class="sxs-lookup"><span data-stu-id="4917a-112">Example</span></span>  

 <span data-ttu-id="4917a-113">Следующий пример с помощью <xref:System.Threading.ManualResetEventSlim> демонстрирует, как разблокировать примитивы координации, поддерживающие унифицированную отмену.</span><span class="sxs-lookup"><span data-stu-id="4917a-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="4917a-114">Этот же подход можно использовать для других простых примитивов координации, таких как <xref:System.Threading.Semaphore>`Slim` и <xref:System.Threading.CountdownEvent>.</span><span class="sxs-lookup"><span data-stu-id="4917a-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="4917a-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4917a-115">See also</span></span>

- [<span data-ttu-id="4917a-116">Отмена в управляемых потоках</span><span class="sxs-lookup"><span data-stu-id="4917a-116">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
