---
title: Использование делегата AsyncCallback для завершения асинхронной операции
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: 1da6bd95c79b25b5bbf6674cf7e9ef48d19cb708
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677964"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="4ad16-102">Использование делегата AsyncCallback для завершения асинхронной операции</span><span class="sxs-lookup"><span data-stu-id="4ad16-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>

<span data-ttu-id="4ad16-103">Приложения, которые могут выполнять работу во время ожидания результатов асинхронной операции, не должны блокироваться до завершения этой операции.</span><span class="sxs-lookup"><span data-stu-id="4ad16-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="4ad16-104">Используйте один из следующих вариантов, чтобы продолжить выполнение инструкций в период ожидания асинхронной операции.</span><span class="sxs-lookup"><span data-stu-id="4ad16-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="4ad16-105">Используйте делегат <xref:System.AsyncCallback> для обработки результатов асинхронной операции в отдельном потоке.</span><span class="sxs-lookup"><span data-stu-id="4ad16-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="4ad16-106">Именно этот подход демонстрируется в этой статье.</span><span class="sxs-lookup"><span data-stu-id="4ad16-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="4ad16-107">Чтобы определить, завершена ли операция, используется свойство <xref:System.IAsyncResult.IsCompleted%2A> объекта <xref:System.IAsyncResult>, возвращаемого методом **Begin**_имя_операции_ асинхронной операции.</span><span class="sxs-lookup"><span data-stu-id="4ad16-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="4ad16-108">Пример, демонстрирующий этот подход, см. в разделе [Запрос состояния асинхронной операции](polling-for-the-status-of-an-asynchronous-operation.md).</span><span class="sxs-lookup"><span data-stu-id="4ad16-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ad16-109">Пример</span><span class="sxs-lookup"><span data-stu-id="4ad16-109">Example</span></span>  

 <span data-ttu-id="4ad16-110">В следующем примере кода асинхронные методы класса <xref:System.Net.Dns> используются для получения из службы доменных имен (DNS) сведений об указанных пользователем компьютерах.</span><span class="sxs-lookup"><span data-stu-id="4ad16-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="4ad16-111">Этот пример создает делегат <xref:System.AsyncCallback>, который ссылается на метод `ProcessDnsInformation`.</span><span class="sxs-lookup"><span data-stu-id="4ad16-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="4ad16-112">Этот метод вызывается один раз для каждого асинхронного запроса сведений DNS.</span><span class="sxs-lookup"><span data-stu-id="4ad16-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="4ad16-113">Обратите внимание, что в параметре <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> передается узел, указанный пользователем.</span><span class="sxs-lookup"><span data-stu-id="4ad16-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="4ad16-114">Пример, демонстрирующий определения и использования более сложного объекта состояния, представлен в статье [Использование делегата AsyncCallback и объекта состояния](using-an-asynccallback-delegate-and-state-object.md).</span><span class="sxs-lookup"><span data-stu-id="4ad16-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4ad16-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4ad16-115">See also</span></span>

- [<span data-ttu-id="4ad16-116">Асинхронная модель на основе событий (EAP)</span><span class="sxs-lookup"><span data-stu-id="4ad16-116">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="4ad16-117">Обзор асинхронной модели, основанной на событиях</span><span class="sxs-lookup"><span data-stu-id="4ad16-117">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="4ad16-118">Вызов асинхронных методов с помощью IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="4ad16-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](calling-asynchronous-methods-using-iasyncresult.md)
- [<span data-ttu-id="4ad16-119">Использование делегата AsyncCallback и объекта состояния</span><span class="sxs-lookup"><span data-stu-id="4ad16-119">Using an AsyncCallback Delegate and State Object</span></span>](using-an-asynccallback-delegate-and-state-object.md)
