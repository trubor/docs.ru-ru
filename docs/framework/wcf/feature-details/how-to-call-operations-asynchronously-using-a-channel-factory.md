---
description: Дополнительные сведения о том, как вызывать операции асинхронно с помощью фабрики каналов.
title: Практическое руководство. Асинхронный вызов операций с использованием фабрики каналов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: 081211d0202550e93e3aabb5c8b5b5b5adbcdcde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780197"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a><span data-ttu-id="9826f-103">Практическое руководство. Асинхронный вызов операций с использованием фабрики каналов</span><span class="sxs-lookup"><span data-stu-id="9826f-103">How to: Call Operations Asynchronously Using a Channel Factory</span></span>

<span data-ttu-id="9826f-104">В этой теме описывается, каким образом клиент может асинхронно обратиться к операции службы при использовании клиентского приложения, основанного на <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="9826f-104">This topic covers how a client can access a service operation asynchronously when using a <xref:System.ServiceModel.ChannelFactory%601>-based client application.</span></span> <span data-ttu-id="9826f-105">(При вызове службы с помощью объекта <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> можно использовать управляемую событиями модель асинхронных вызовов.</span><span class="sxs-lookup"><span data-stu-id="9826f-105">(When using a <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> object to invoke a service you can use the event-driven asynchronous calling model.</span></span> <span data-ttu-id="9826f-106">Дополнительные сведения см. [в разделе инструкции. асинхронный вызов операций службы](how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="9826f-106">For more information, see [How to: Call Service Operations Asynchronously](how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="9826f-107">Дополнительные сведения о модели асинхронного вызова на основе событий см. в разделе [асинхронная модель на основе событий (EAP)](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="9826f-107">For more information about the event-based asynchronous calling model, see [Event-based Asynchronous Pattern (EAP)](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).)</span></span>  
  
 <span data-ttu-id="9826f-108">Служба в этом разделе реализует интерфейс `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="9826f-108">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="9826f-109">Клиент может асинхронно вызвать операции для этого интерфейса, это означает, что операции типа `Add` разделяются на два метода, `BeginAdd` и `EndAdd`, первый из них инициирует вызов, а второй извлекает результат после завершения операции.</span><span class="sxs-lookup"><span data-stu-id="9826f-109">The client can call the operations on this interface asynchronously, which means that operations like `Add` are split into two methods, `BeginAdd` and `EndAdd`, the former of which initiates the call and the latter of which retrieves the result when the operation completes.</span></span> <span data-ttu-id="9826f-110">Пример, демонстрирующий асинхронную реализацию операции в службе, см. [в разделе как реализовать асинхронную операцию службы](../how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="9826f-110">For an example showing how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="9826f-111">Дополнительные сведения о синхронных и асинхронных операциях см. в разделе [синхронные и асинхронные операции](../synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9826f-111">For details about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../synchronous-and-asynchronous-operations.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="9826f-112">Процедура</span><span class="sxs-lookup"><span data-stu-id="9826f-112">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="9826f-113">Асинхронный вызов операций службы WCF</span><span class="sxs-lookup"><span data-stu-id="9826f-113">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="9826f-114">Запустите средство [служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) с `/async` параметром, как показано в следующей команде.</span><span class="sxs-lookup"><span data-stu-id="9826f-114">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool with the `/async` option as shown in the following command.</span></span>  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     <span data-ttu-id="9826f-115">Результатом станет создание асинхронной версии клиента контракта службы для операции.</span><span class="sxs-lookup"><span data-stu-id="9826f-115">This generates an asynchronous client version of the service contract for the operation.</span></span>  
  
2. <span data-ttu-id="9826f-116">Создайте функцию обратного вызова, вызываемую после завершения асинхронной операции, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="9826f-116">Create a callback function to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3. <span data-ttu-id="9826f-117">Чтобы асинхронно обратиться к операции службы, создайте клиент и вызовите `Begin[Operation]` (например `BeginAdd`) и задайте функцию обратного вызова, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="9826f-117">To access a service operation asynchronously, create the client and call the `Begin[Operation]` (for example, `BeginAdd`) and specify a callback function, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     <span data-ttu-id="9826f-118">При выполнении функции обратного вызова клиент вызывает `End<operation>` (например `EndAdd`), чтобы извлечь результат.</span><span class="sxs-lookup"><span data-stu-id="9826f-118">When the callback function executes, the client calls `End<operation>` (for example, `EndAdd`) to retrieve the result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9826f-119">Пример</span><span class="sxs-lookup"><span data-stu-id="9826f-119">Example</span></span>  

 <span data-ttu-id="9826f-120">Служба, используемая с клиентским кодом, который применяется в предыдущей процедуре, реализует интерфейс `ICalculator`, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="9826f-120">The service that is used with the client code that is used in the preceding procedure implements the `ICalculator` interface as shown in the following code.</span></span> <span data-ttu-id="9826f-121">На стороне службы `Add` операции и в `Subtract` контракте вызываются синхронно с помощью Windows Communication Foundation (WCF) времени выполнения, хотя предыдущие этапы клиента вызываются на клиенте асинхронно.</span><span class="sxs-lookup"><span data-stu-id="9826f-121">On the service side, the `Add` and `Subtract` operations of the contract are invoked synchronously by the Windows Communication Foundation (WCF) run time, even though the preceding client steps are invoked asynchronously on the client.</span></span> <span data-ttu-id="9826f-122">Операции `Multiply` и `Divide` используются для асинхронного вызова службы на стороне службы, даже если клиент вызывает их синхронно.</span><span class="sxs-lookup"><span data-stu-id="9826f-122">The `Multiply` and `Divide` operations are used to invoke the service asynchronously on the service side, even if the client invokes them synchronously.</span></span> <span data-ttu-id="9826f-123">В этом примере свойству <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> присваивается значение `true`.</span><span class="sxs-lookup"><span data-stu-id="9826f-123">This example sets the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property to `true`.</span></span> <span data-ttu-id="9826f-124">Этот параметр свойства в сочетании с реализацией асинхронного шаблона платформа .NET Framework сообщает времени выполнения о необходимости асинхронного вызова операции.</span><span class="sxs-lookup"><span data-stu-id="9826f-124">This property setting, in combination with the implementation of the .NET Framework asynchronous pattern, tells the run time to invoke the operation asynchronously.</span></span>  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
