---
description: 'Дополнительные сведения: One-Way'
title: Одностороннее взаимодействие
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: fef940f6e0787b7dc91f02442597625b8c4cca50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726290"
---
# <a name="one-way"></a><span data-ttu-id="3d8c6-103">Одностороннее взаимодействие</span><span class="sxs-lookup"><span data-stu-id="3d8c6-103">One-Way</span></span>

<span data-ttu-id="3d8c6-104">В этом образце демонстрируется контакт службы с односторонними операциями службы.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-104">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="3d8c6-105">Клиент не ожидает завершения операций службы, как это происходит в случае двусторонних операций службы.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-105">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="3d8c6-106">Этот образец основан на [Начало работы](getting-started-sample.md) и использует `wsHttpBinding` привязку.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-106">This sample is based on the [Getting Started](getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="3d8c6-107">В данном образце служба представляет собой резидентное консольное приложение, позволяющее наблюдать за тем, как служба получает и обрабатывает запросы.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-107">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="3d8c6-108">Клиент также является консольным приложением.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-108">The client is also a console application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d8c6-109">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3d8c6-110">Чтобы создать односторонний контракт службы, определите контракт службы, примените класс <xref:System.ServiceModel.OperationContractAttribute> к каждой из операций и присвойте свойству <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> логическое значение `true`, как показано в следующем образце кода:</span><span class="sxs-lookup"><span data-stu-id="3d8c6-110">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="3d8c6-111">В следующем образце кода показано, что клиент не ждет момента завершения операций службы. Для наглядной демонстрации код службы реализует пятисекундную задержку:</span><span class="sxs-lookup"><span data-stu-id="3d8c6-111">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
```csharp
// This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="3d8c6-112">Когда клиент вызывает службу, вызов возвращается без ожидания завершения операции службы.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-112">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="3d8c6-113">При выполнении образца действия клиента и службы отображаются в окнах консоли как службы, так и клиента.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-113">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="3d8c6-114">Можно видеть, как служба получает сообщения от клиента.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-114">You can see the service receive messages from the client.</span></span> <span data-ttu-id="3d8c6-115">Нажмите клавишу ВВОД в каждом окне консоли, чтобы закрыть и службу, и клиент.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-115">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="3d8c6-116">Клиент завершает работу раньше службы, демонстрируя таким образом, что клиент не ожидает завершения односторонних операций службы.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-116">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="3d8c6-117">Результат работы клиента имеет следующий вид:</span><span class="sxs-lookup"><span data-stu-id="3d8c6-117">The client output is as follows:</span></span>  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="3d8c6-118">Показан следующий результат работы службы:</span><span class="sxs-lookup"><span data-stu-id="3d8c6-118">The following service output is shown:</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
```  
  
> [!NOTE]
> <span data-ttu-id="3d8c6-119">HTTP, по определению, является протоколом запроса-ответа. На переданный запрос должен быть возвращен ответ.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-119">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="3d8c6-120">Это справедливо даже для односторонней операции службы, предоставляемой через HTTP.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-120">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="3d8c6-121">При вызове операции служба возвращает код состояния HTTP 202 до момента, когда операция службы уже выполнена.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-121">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="3d8c6-122">Этот код состояния означает, что запрос принят для обработки, но обработка еще не была закончена.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-122">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="3d8c6-123">Вызвавший операцию клиент блокируется до момента получения ответа 202 от службы.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-123">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="3d8c6-124">Это может являться причиной непредвиденного поведения, когда передано множество односторонних сообщений с использованием привязки, которая сконфигурирована для использования сеансов.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-124">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="3d8c6-125">Использованная в этом образце привязка `wsHttpBinding` по умолчанию сконфигурирована для использования сеансов, чтобы устанавливать контекст безопасности.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-125">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="3d8c6-126">По умолчанию сообщения в сеансе прибывают точно в том порядке, в котором отправлены.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-126">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="3d8c6-127">По этой причине не обрабатывается второе переданное в сеансе сообщение, пока не обработано первое сообщение.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-127">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="3d8c6-128">В результате клиент не получает ответ 202 для текущего сообщения до момента завершения обработки предыдущего сообщения.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-128">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="3d8c6-129">Поэтому клиент блокируется для каждого последующего вызов операции.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-129">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="3d8c6-130">Для предотвращения такого поведения этот образец конфигурирует среду выполнения таким образом, чтобы одновременно определить сообщения различным экземплярам для обработки.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-130">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="3d8c6-131">Образец устанавливает свойству <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> значение `PerCall`, чтобы каждое сообщение обрабатывалось отдельным экземпляром.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-131">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="3d8c6-132">Свойству <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> задается значение `Multiple`, которое позволяет нескольким потокам одновременно отправлять сообщения.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-132"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3d8c6-133">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="3d8c6-133">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3d8c6-134">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d8c6-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3d8c6-135">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d8c6-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3d8c6-136">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d8c6-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d8c6-137">Запустите службу перед запуском клиента и завершите работу клиента перед завершением работы службы.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-137">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="3d8c6-138">Это предотвратит исключение для клиента, если клиент не может завершить сеанс безопасности без ошибок по причине отсутствия службы.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-138">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3d8c6-139">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3d8c6-140">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="3d8c6-140">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3d8c6-141">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3d8c6-142">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="3d8c6-142">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
