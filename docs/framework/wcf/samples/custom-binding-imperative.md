---
description: 'Подробнее: настраиваемая привязка императивная'
title: Императивные пользовательские привязки
ms.date: 03/30/2017
ms.assetid: 6e13bf96-5de0-4476-b646-5f150774418d
ms.openlocfilehash: 670f32f12f85a0ded6f2357d10ac9cfbbd5ac107
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778325"
---
# <a name="custom-binding-imperative"></a><span data-ttu-id="bd826-103">Императивные пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="bd826-103">Custom Binding Imperative</span></span>

<span data-ttu-id="bd826-104">В примере показано, как написать императивный код для определения и использования пользовательских привязок без использования файла конфигурации или клиента, созданного Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bd826-104">The sample demonstrates how to write imperative code to define and use custom bindings without using a configuration file or a Windows Communication Foundation (WCF) generated client.</span></span> <span data-ttu-id="bd826-105">Этот образец объединяет возможности, предоставляемые транспортом HTTP, и канал надежного сеанса, создавая надежную привязку на основе HTTP.</span><span class="sxs-lookup"><span data-stu-id="bd826-105">This sample combines the features provided by the HTTP transport and the reliable session channel to create a reliable HTTP-based binding.</span></span> <span data-ttu-id="bd826-106">Этот образец основан на [Начало работы](getting-started-sample.md) , который реализует службу калькулятора.</span><span class="sxs-lookup"><span data-stu-id="bd826-106">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd826-107">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="bd826-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bd826-108">Со стороны клиента и со стороны службы создается пользовательская привязка, содержащая два элемента привязки (надежный сеанс и HTTP):</span><span class="sxs-lookup"><span data-stu-id="bd826-108">On both the client and the service, a custom binding is created that contains two binding elements (Reliable Session and HTTP):</span></span>  

```csharp
ReliableSessionBindingElement reliableSession = new ReliableSessionBindingElement();  
reliableSession.Ordered = true;  
  
HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
httpTransport.AuthenticationScheme = System.Net.AuthenticationSchemes.Anonymous;  
httpTransport.HostNameComparisonMode = HostNameComparisonMode.StrongWildcard;  
  
CustomBinding binding = new CustomBinding(reliableSession, httpTransport);  
```
  
 <span data-ttu-id="bd826-109">На стороне службы привязка используется за счет добавления к ServiceHost конечной точки:</span><span class="sxs-lookup"><span data-stu-id="bd826-109">On the service, the binding is used by adding an endpoint to the ServiceHost:</span></span>  

```csharp
serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, "");  
```

 <span data-ttu-id="bd826-110">На стороне клиента привязка используется за счет <xref:System.ServiceModel.ChannelFactory> для создания канала к службе:</span><span class="sxs-lookup"><span data-stu-id="bd826-110">On the client, the binding is used by a <xref:System.ServiceModel.ChannelFactory> to create a channel to the service:</span></span>  

```csharp
EndpointAddress address = new EndpointAddress("http://localhost:8000/servicemodelsamples/service");  
ChannelFactory<ICalculator> channelFactory = new ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = channelFactory.CreateChannel();  
```

 <span data-ttu-id="bd826-111">Затем этот канал используется для взаимодействия со службой:</span><span class="sxs-lookup"><span data-stu-id="bd826-111">This channel is then used to interact with the service:</span></span>  

```csharp
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```

 <span data-ttu-id="bd826-112">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="bd826-112">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bd826-113">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="bd826-113">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bd826-114">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="bd826-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bd826-115">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd826-115">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="bd826-116">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd826-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="bd826-117">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd826-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bd826-118">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="bd826-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bd826-119">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="bd826-119">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bd826-120">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="bd826-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bd826-121">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="bd826-121">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Custom\Imperative`  
  
## <a name="see-also"></a><span data-ttu-id="bd826-122">См. также</span><span class="sxs-lookup"><span data-stu-id="bd826-122">See also</span></span>

- [<span data-ttu-id="bd826-123">Примеры пользовательских привязок</span><span class="sxs-lookup"><span data-stu-id="bd826-123">Custom Binding Samples</span></span>](custom-binding.md)
