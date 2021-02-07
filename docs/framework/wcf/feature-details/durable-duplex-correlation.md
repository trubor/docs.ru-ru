---
description: 'Подробнее: устойчивая дуплексная корреляция'
title: Сохраняемая дуплексная корреляция
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: e30356e03ccb6f8fae7ca735d2ad674bbe2a191d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704957"
---
# <a name="durable-duplex-correlation"></a><span data-ttu-id="2e8b5-103">Сохраняемая дуплексная корреляция</span><span class="sxs-lookup"><span data-stu-id="2e8b5-103">Durable Duplex Correlation</span></span>

<span data-ttu-id="2e8b5-104">Сохраняемую дуплексную корреляцию, также называемую корреляцией обратных вызовов, удобно использовать, когда служба рабочего процесса должна отправлять обратный вызов исходному вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-104">Durable duplex correlation, also known as callback correlation, is useful when a workflow service has a requirement to send a callback to the initial caller.</span></span> <span data-ttu-id="2e8b5-105">В отличие от дуплекса WCF, обратный вызов может выполняться в любой момент в будущем и не связан с одним и тем же каналом или временем существования канала. Единственное требование - у вызывающего должна быть конечная точка, прослушивающая сообщение обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-105">Unlike WCF duplex, the callback can happen at any time in the future and is not tied to the same channel or the channel lifetime; the only requirement is that the caller have an active endpoint listening for the callback message.</span></span> <span data-ttu-id="2e8b5-106">Благодаря этому обеспечивается возможность взаимодействия двух служб рабочего процесса в долговременных диалогах.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-106">This allows two workflow services to communicate in a long-running conversation.</span></span> <span data-ttu-id="2e8b5-107">В данном разделе приведены общие сведения о сохраняемой дуплексной корреляции.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-107">This topic provides an overview of durable duplex correlation.</span></span>  
  
## <a name="using-durable-duplex-correlation"></a><span data-ttu-id="2e8b5-108">Использование сохраняемой дуплексной корреляции</span><span class="sxs-lookup"><span data-stu-id="2e8b5-108">Using Durable Duplex Correlation</span></span>  

 <span data-ttu-id="2e8b5-109">Чтобы использовать сохраняемую дуплексную корреляцию, две службы должны использовать контекстную привязку, которая поддерживает двусторонние операции, такие как <xref:System.ServiceModel.NetTcpContextBinding> или <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-109">To use durable duplex correlation, the two services must use a context-enabled binding that supports two-way operations, such as <xref:System.ServiceModel.NetTcpContextBinding> or <xref:System.ServiceModel.WSHttpContextBinding>.</span></span> <span data-ttu-id="2e8b5-110">Вызывающая служба регистрирует <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> с привязкой на их клиентской конечной точке <xref:System.ServiceModel.Endpoint>.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-110">The calling service registers a <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> with the desired binding on their client <xref:System.ServiceModel.Endpoint>.</span></span> <span data-ttu-id="2e8b5-111">Принимающая служба получает эти данные в первоначальном вызове, а затем использует их для собственных <xref:System.ServiceModel.Endpoint> в действии <xref:System.ServiceModel.Activities.Send>, выполняющем обратный вызов вызывающей службы.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-111">The receiving service receives this data in the initial call and then uses it on its own <xref:System.ServiceModel.Endpoint> in the <xref:System.ServiceModel.Activities.Send> activity that makes the call back to the calling service.</span></span> <span data-ttu-id="2e8b5-112">В этом примере две службы взаимодействуют друг с другом.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-112">In this example, two services communicate with each other.</span></span> <span data-ttu-id="2e8b5-113">Первая служба вызывает метод для второй службы, а затем ожидает ответа.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-113">The first service invokes a method on the second service and then waits for a reply.</span></span> <span data-ttu-id="2e8b5-114">Второй службе известно имя метода обратного вызова, но во время разработки конечная точка службы, реализующая этот метод, неизвестна.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-114">The second service knows the name of the callback method, but the endpoint of the service that implements this method is not known at design time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e8b5-115">Сохраняемая дуплексная корреляция может быть использована только в случае, если параметр <xref:System.ServiceModel.Channels.AddressingVersion> конечной точки установлен в значение <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-115">Durable duplex can only be used when the <xref:System.ServiceModel.Channels.AddressingVersion> of the endpoint is configured with <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span></span> <span data-ttu-id="2e8b5-116">Если это не так, <xref:System.InvalidOperationException> создается исключение со следующим сообщением: "сообщение содержит заголовок контекста обратного вызова со ссылкой на конечную точку для [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span><span class="sxs-lookup"><span data-stu-id="2e8b5-116">If it is not, then an <xref:System.InvalidOperationException> exception is thrown with the following message: "The message contains a callback context header with an endpoint reference for [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span></span> <span data-ttu-id="2e8b5-117">Контекст обратного вызова можно передавать, только если для AddressingVersion настроено значение "WSAddressing10".</span><span class="sxs-lookup"><span data-stu-id="2e8b5-117">Callback context can only be transmitted when the AddressingVersion is configured with 'WSAddressing10'.</span></span>
  
 <span data-ttu-id="2e8b5-118">В следующем примере выполняется размещение службы рабочего процесса, с помощью которой создается обратный вызов <xref:System.ServiceModel.Endpoint> с помощью привязки <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-118">In the following example, a workflow service is hosted that creates a callback <xref:System.ServiceModel.Endpoint> using <xref:System.ServiceModel.WSHttpContextBinding>.</span></span>  
  
```csharp  
// Host WF Service 1.  
string baseAddress1 = "http://localhost:8080/Service1";  
WorkflowServiceHost host1 = new WorkflowServiceHost(GetWF1(), new Uri(baseAddress1));  
  
// Add the callback endpoint.  
WSHttpContextBinding Binding1 = new WSHttpContextBinding();  
host1.AddServiceEndpoint("ICallbackItemsReady", Binding1, "ItemsReady");  
  
// Add the service endpoint.  
host1.AddServiceEndpoint("IService1", Binding1, baseAddress1);  
  
// Open the first workflow service.  
host1.Open();  
Console.WriteLine("Service1 waiting at: {0}", baseAddress1);  
```  
  
 <span data-ttu-id="2e8b5-119">Рабочий процесс, реализующий эту службу рабочего процесса, инициализирует корреляцию обратного вызова со своим действием <xref:System.ServiceModel.Activities.Send> и ссылается на эту конечную точку обратного вызова из действия <xref:System.ServiceModel.Activities.Receive>, для которого выполнена корреляция с действием <xref:System.ServiceModel.Activities.Send>.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-119">The workflow that implements this workflow service initializes the callback correlation with its <xref:System.ServiceModel.Activities.Send> activity, and references this callback endpoint from the <xref:System.ServiceModel.Activities.Receive> activity that correlates with the <xref:System.ServiceModel.Activities.Send>.</span></span> <span data-ttu-id="2e8b5-120">В следующем примере представлен рабочий процесс, который возвращается из метода `GetWF1`.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-120">The following example represents the workflow that is returned from the `GetWF1` method.</span></span>  
  
```csharp  
Variable<CorrelationHandle> CallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IService1",  
    OperationName = "StartOrder"  
};  
  
Send GetItems = new Send  
{  
    CorrelationInitializers =
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = CallbackHandle  
        }  
    },  
    ServiceContractName = "IService2",  
    OperationName = "StartItems",  
    Endpoint = new Endpoint  
    {  
        AddressUri = new Uri("http://localhost:8081/Service2"),  
        Binding = new WSHttpContextBinding  
        {  
            ClientCallbackAddress = new Uri("http://localhost:8080/Service1/ItemsReady")
        }  
    }  
};  
  
Receive ItemsReady = new Receive  
{  
    ServiceContractName = "ICallbackItemsReady",  
    OperationName = "ItemsReady",  
    CorrelatesWith = CallbackHandle,  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        CallbackHandle  
    },  
    Activities =  
    {  
        StartOrder,  
        new WriteLine  
        {  
            Text = "WF1 - Started"  
        },  
        GetItems,  
        new WriteLine  
        {  
            Text = "WF1 - Request Submitted"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF1 - Items Received"  
        }  
     }  
};  
```  
  
 <span data-ttu-id="2e8b5-121">Вторая служба рабочего процесса размещается с использованием предоставленной системой контекстной привязки.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-121">The second workflow service is hosted using a system-provided, context-based binding.</span></span>  
  
```csharp  
// Host WF Service 2.  
string baseAddress2 = "http://localhost:8081/Service2";  
WorkflowServiceHost host2 = new WorkflowServiceHost(GetWF2(), new Uri(baseAddress2));  
  
// Add the service endpoint.  
WSHttpContextBinding Binding2 = new WSHttpContextBinding();  
host2.AddServiceEndpoint("IService2", Binding2, baseAddress2);  
  
// Open the second workflow service.  
host2.Open();  
Console.WriteLine("Service2 waiting at: {0}", baseAddress2);  
```  
  
 <span data-ttu-id="2e8b5-122">Рабочий процесс, реализующий эту службу рабочего процесса, начинается с действия <xref:System.ServiceModel.Activities.Receive>.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-122">The workflow that implements this workflow service begins with a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="2e8b5-123">Это действие получения инициализирует корреляцию обратного вызова для этой службы, откладывает выполнение на определенный период времени для моделирования долгосрочных работ, а затем выполняет обратный вызов в первую службу с использованием контекста обратного вызова, переданного в первом вызове в службу.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-123">This receive activity initializes the callback correlation for this service, delays for a period of time to simulate long-running work, and then calls back into the first service using the callback context that was passed in the first call into the service.</span></span> <span data-ttu-id="2e8b5-124">В следующем примере представлен рабочий процесс, который возвращается из вызова `GetWF2`.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-124">The following example represents the workflow that is returned from a call to `GetWF2`.</span></span> <span data-ttu-id="2e8b5-125">Обратите внимание, что в действии <xref:System.ServiceModel.Activities.Send> имеется адрес местозаполнителя `http://www.contoso.com`; фактический адрес, используемый во время выполнения, предоставляется обратным вызовом.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-125">Note that the <xref:System.ServiceModel.Activities.Send> activity has a placeholder address of `http://www.contoso.com`; the actual address used at runtime is the supplied callback address.</span></span>  
  
```csharp  
Variable<CorrelationHandle> ItemsCallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartItems = new Receive  
{  
    CorrelationInitializers =
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = ItemsCallbackHandle  
        }  
    },  
    CanCreateInstance = true,  
    ServiceContractName = "IService2",  
    OperationName = "StartItems"  
};  
  
Send ItemsReady = new Send  
{  
    CorrelatesWith = ItemsCallbackHandle,  
    Endpoint = new Endpoint  
    {  
        // The callback address on the binding is used  
        // instead of this placeholder address.  
        AddressUri = new Uri("http://www.contoso.com"),  
  
        Binding = new WSHttpContextBinding()  
    },  
    OperationName = "ItemsReady",  
    ServiceContractName = "ICallbackItemsReady"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        ItemsCallbackHandle  
    },  
    Activities =  
    {  
        StartItems,  
        new WriteLine  
        {  
            Text = "WF2 - Request Received"  
        },  
        new Delay  
        {  
            Duration = TimeSpan.FromMinutes(90)  
        },  
        new WriteLine  
        {  
            Text = "WF2 - Sending items"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF2 - Items sent"  
        }  
     }  
};  
```  
  
 <span data-ttu-id="2e8b5-126">При вызове метода `StartOrder` в первом рабочем процессе отображается следующий результат, в котором показан ход выполнения с двумя рабочими процессами.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-126">When the `StartOrder` method is invoked on the first workflow, the following output is displayed, which shows the flow of execution through the two workflows.</span></span>  
  
```output  
Service1 waiting at: http://localhost:8080/Service1  
Service2 waiting at: http://localhost:8081/Service2  
Press enter to exit.
WF1 - Started  
WF2 - Request Received  
WF1 - Request Submitted  
WF2 - Sending items  
WF2 - Items sent  
WF1 - Items Received  
```  
  
 <span data-ttu-id="2e8b5-127">В этом примере оба рабочих процесса явно управляют корреляцией с помощью объекта <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-127">In this example, both workflows explicitly manage correlation using a <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span></span> <span data-ttu-id="2e8b5-128">Поскольку в этих образцах имеется только одна корреляция, настройки управления <xref:System.ServiceModel.Activities.CorrelationHandle>, заданные по умолчанию, не требуют изменений.</span><span class="sxs-lookup"><span data-stu-id="2e8b5-128">Because there was only a single correlation in these sample workflows, the default <xref:System.ServiceModel.Activities.CorrelationHandle> management would have been sufficient.</span></span>
