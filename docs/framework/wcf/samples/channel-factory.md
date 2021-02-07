---
description: Дополнительные сведения о фабрике каналов
title: Фабрика каналов
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: fad406e14887524fc69900e9775f1b6fbbcbecda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704138"
---
# <a name="channel-factory"></a><span data-ttu-id="8d8d4-103">Фабрика каналов</span><span class="sxs-lookup"><span data-stu-id="8d8d4-103">Channel Factory</span></span>

<span data-ttu-id="8d8d4-104">В этом образце показано, как клиентское приложение может создать канал с помощью <xref:System.ServiceModel.ChannelFactory>, вместо использования созданного клиента.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-104">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="8d8d4-105">Этот образец основан на [Начало работы](getting-started-sample.md) , который реализует службу калькулятора.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>

> [!NOTE]
> <span data-ttu-id="8d8d4-106">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="8d8d4-107">Чтобы создать канал для конечной точки службы, в этом образце используется класс <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-107">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="8d8d4-108">Как правило, для создания канала к конечной точке службы вы создаете тип клиента с помощью [средства служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) и создаете экземпляр созданного типа.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-108">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="8d8d4-109">Кроме того, канал можно создать с помощью класса <xref:System.ServiceModel.ChannelFactory%601>, как показано в этом образце.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-109">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="8d8d4-110">Служба, созданная с помощью следующего примера кода, идентична службе в [Начало работы](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8d8d4-110">The service created by the following sample code is identical to the service in the [Getting Started](getting-started-sample.md).</span></span>

```csharp
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
WSHttpBinding binding = new WSHttpBinding();
ChannelFactory<ICalculator> factory = new
                    ChannelFactory<ICalculator>(binding, address);
ICalculator channel = factory.CreateChannel();
```

> [!IMPORTANT]
> <span data-ttu-id="8d8d4-111">Если этот образец выполняется на нескольких компьютерах, в предыдущем фрагменте кода необходимо заменить localhost на полное имя компьютера, на котором выполняется служба.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-111">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="8d8d4-112">В этом образце для задания адреса конечной точки конфигурация не используется, поэтому это необходимо сделать в коде.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-112">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>

<span data-ttu-id="8d8d4-113">После создания канала можно вызывать операции службы, как это можно было бы делать с помощью созданного клиента.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-113">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>

```csharp
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = channel.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

<span data-ttu-id="8d8d4-114">Чтобы закрыть канал, его необходимо сначала привести к интерфейсу <xref:System.ServiceModel.IClientChannel>.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-114">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="8d8d4-115">Это связано с тем, что канал обычно объявляется в клиентском приложении с помощью интерфейса `ICalculator`, имеющего методы `Add` и `Subtract`, но не имеющего метода `Close`.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-115">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="8d8d4-116">Метод `Close` наследуется от интерфейса <xref:System.ServiceModel.ICommunicationObject>.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-116">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>

```csharp
// Close the channel.
 ((IClientChannel)client).Close();
```

<span data-ttu-id="8d8d4-117">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-117">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8d8d4-118">Чтобы закрыть клиентское приложение, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-118">Press ENTER in the client window to shut down the client application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8d8d4-119">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="8d8d4-119">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="8d8d4-120">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8d8d4-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="8d8d4-121">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8d8d4-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span> <span data-ttu-id="8d8d4-122">Обратите внимание, что этот в этом образце не включается публикация метаданных.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-122">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="8d8d4-123">Чтобы заново создать тип клиента, необходимо включить в образце публикацию метаданных.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-123">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>

3. <span data-ttu-id="8d8d4-124">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8d8d4-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="8d8d4-125">Запуск образца на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="8d8d4-125">To run the sample cross machine</span></span>

1. <span data-ttu-id="8d8d4-126">В следующем фрагменте кода замените localhost на полное имя компьютера, на котором выполняется служба.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-126">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>

    ```csharp
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
    ```

> [!IMPORTANT]
> <span data-ttu-id="8d8d4-127">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8d8d4-128">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="8d8d4-128">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="8d8d4-129">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8d8d4-130">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="8d8d4-130">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`
