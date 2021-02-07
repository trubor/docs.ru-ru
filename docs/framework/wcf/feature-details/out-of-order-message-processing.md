---
description: 'Подробнее: обработка неупорядоченных сообщений'
title: Обработка неупорядоченных сообщений
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 4349b7d72c080dff579eda18ce51de99ab5e91fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733610"
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="d9253-103">Обработка неупорядоченных сообщений</span><span class="sxs-lookup"><span data-stu-id="d9253-103">Out-of-Order Message Processing</span></span>

<span data-ttu-id="d9253-104">Службы рабочих процессов могут зависеть от порядка отправки сообщений.</span><span class="sxs-lookup"><span data-stu-id="d9253-104">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="d9253-105">Служба рабочих процессов содержит одно или несколько действий <xref:System.ServiceModel.Activities.Receive>. Каждое из этих действий <xref:System.ServiceModel.Activities.Receive> рассчитано на определенное сообщение.</span><span class="sxs-lookup"><span data-stu-id="d9253-105">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="d9253-106">Поскольку доставка данных не гарантируется, отправляемые клиентами сообщения могут задерживаться и доставляться в порядке, на который служба рабочих процессов не рассчитана.</span><span class="sxs-lookup"><span data-stu-id="d9253-106">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="d9253-107">Реализация службы рабочих процессов, которая не требует отправки сообщений в определенном порядке, обычно осуществляется с использованием параллельных действий.</span><span class="sxs-lookup"><span data-stu-id="d9253-107">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="d9253-108">В результате усложнения протокола приложения рабочий процесс также слишком быстро становится сложным.</span><span class="sxs-lookup"><span data-stu-id="d9253-108">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="d9253-109">Функция обработки неупорядоченных сообщений в Windows Communication Foundation (WCF) позволяет создавать такой рабочий процесс без какой-либо сложности вложенных параллельных действий.</span><span class="sxs-lookup"><span data-stu-id="d9253-109">The out-of-order message processing feature in Windows Communication Foundation (WCF) allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="d9253-110">Обработка неупорядоченных сообщений поддерживается только для каналов, которые поддерживают <xref:System.ServiceModel.Channels.ReceiveContext> такие привязки MSMQ в WCF.</span><span class="sxs-lookup"><span data-stu-id="d9253-110">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the WCF MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="d9253-111">Реализация обработки внеочередных сообщений</span><span class="sxs-lookup"><span data-stu-id="d9253-111">Enabling Out-Of-Order Message Processing</span></span>  

 <span data-ttu-id="d9253-112">Чтобы включить обработку внеочередных сообщений, в WorkflowService установите свойство <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> в значение `true`.</span><span class="sxs-lookup"><span data-stu-id="d9253-112">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="d9253-113">В следующем примере кода показана установка свойства <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> в коде.</span><span class="sxs-lookup"><span data-stu-id="d9253-113">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="d9253-114">Можно также применить атрибут `AllowBufferedReceive` к службе рабочих процессов в XAML, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d9253-114">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9253-115">См. также</span><span class="sxs-lookup"><span data-stu-id="d9253-115">See also</span></span>

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [<span data-ttu-id="d9253-116">Службы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="d9253-116">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="d9253-117">Очереди и надежные сеансы</span><span class="sxs-lookup"><span data-stu-id="d9253-117">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
