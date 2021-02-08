---
description: Дополнительные сведения о параллелизме
title: Параллелизм
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 2fbb6f9fc5ee2807ed0ca0592c364f048d5d8b14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778546"
---
# <a name="concurrency"></a><span data-ttu-id="3cf49-103">Параллелизм</span><span class="sxs-lookup"><span data-stu-id="3cf49-103">Concurrency</span></span>

<span data-ttu-id="3cf49-104">Образец Concurrency демонстрирует использование <xref:System.ServiceModel.ServiceBehaviorAttribute> с перечислением <xref:System.ServiceModel.ConcurrencyMode>, определяющим, будет ли экземпляр службы обрабатывать сообщения последовательно или параллельно.</span><span class="sxs-lookup"><span data-stu-id="3cf49-104">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="3cf49-105">Образец основан на [Начало работы](getting-started-sample.md), который реализует `ICalculator` контракт службы.</span><span class="sxs-lookup"><span data-stu-id="3cf49-105">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="3cf49-106">Этот образец определяет новый контракт, `ICalculatorConcurrency`, унаследованный от `ICalculator`, который добавляет две операции для контроля состояния параллелизма службы.</span><span class="sxs-lookup"><span data-stu-id="3cf49-106">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="3cf49-107">Изменив параметр параллелизма, можно запустить клиент и посмотреть, как изменилось поведение.</span><span class="sxs-lookup"><span data-stu-id="3cf49-107">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="3cf49-108">В этом образце клиентом является консольное приложение (EXE), а служба размещается в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="3cf49-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cf49-109">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="3cf49-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3cf49-110">Доступны три режима параллелизма.</span><span class="sxs-lookup"><span data-stu-id="3cf49-110">There are three concurrency modes available:</span></span>  
  
- <span data-ttu-id="3cf49-111">`Single`: все экземпляры службы обрабатывают в данный момент времени одно сообщение.</span><span class="sxs-lookup"><span data-stu-id="3cf49-111">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="3cf49-112">Это режим параллелизма по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3cf49-112">This is the default concurrency mode.</span></span>  
  
- <span data-ttu-id="3cf49-113">`Multiple`: каждый экземпляр службы обрабатывает несколько сообщений параллельно.</span><span class="sxs-lookup"><span data-stu-id="3cf49-113">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="3cf49-114">Чтобы использовать этот режим параллелизма, реализация службы должна быть потокобезопасной.</span><span class="sxs-lookup"><span data-stu-id="3cf49-114">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
- <span data-ttu-id="3cf49-115">`Reentrant`: каждый экземпляр службы одновременно обрабатывает одно сообщение, но принимает вызовы с повторным входом.</span><span class="sxs-lookup"><span data-stu-id="3cf49-115">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="3cf49-116">Служба принимает эти вызовы только при вызове. Повторный вход показан в образце [ConcurrencyMode.](concurrencymode-reentrant.md) повторного входа.</span><span class="sxs-lookup"><span data-stu-id="3cf49-116">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="3cf49-117">Использование параллелизма связано с режимом создания экземпляров.</span><span class="sxs-lookup"><span data-stu-id="3cf49-117">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="3cf49-118">В режиме создания экземпляров <xref:System.ServiceModel.InstanceContextMode.PerCall> параллелизм не имеет значения, так как каждое сообщение обрабатывается новым экземпляром службы.</span><span class="sxs-lookup"><span data-stu-id="3cf49-118">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="3cf49-119">В режиме создания экземпляров <xref:System.ServiceModel.InstanceContextMode.Single> имеет значение параллелизм <xref:System.ServiceModel.ConcurrencyMode.Single> или <xref:System.ServiceModel.ConcurrencyMode.Multiple>, в зависимости от того, обрабатывает ли один экземпляр сообщения последовательно или параллельно.</span><span class="sxs-lookup"><span data-stu-id="3cf49-119">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="3cf49-120">В режиме создания экземпляров <xref:System.ServiceModel.InstanceContextMode.PerSession> могут иметь значение любые режимы параллелизма.</span><span class="sxs-lookup"><span data-stu-id="3cf49-120">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="3cf49-121">Класс службы задает поведение параллелизма с помощью атрибута `[ServiceBehavior(ConcurrencyMode=<setting>)]`, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="3cf49-121">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="3cf49-122">Преобразуя в комментарий различные строки, можно поэкспериментировать с режимами параллелизма `Single` и `Multiple`.</span><span class="sxs-lookup"><span data-stu-id="3cf49-122">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="3cf49-123">Не забывайте строить службу заново после изменения режима параллелизма.</span><span class="sxs-lookup"><span data-stu-id="3cf49-123">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
```csharp
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 <span data-ttu-id="3cf49-124">По умолчанию образец использует параллелизм <xref:System.ServiceModel.ConcurrencyMode.Multiple> с режимом создания экземпляров <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="3cf49-124">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="3cf49-125">Код клиента изменен для использования асинхронного прокси.</span><span class="sxs-lookup"><span data-stu-id="3cf49-125">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="3cf49-126">Это позволяет клиенту направлять службе сразу несколько вызовов, не дожидаясь ответа на каждый вызов.</span><span class="sxs-lookup"><span data-stu-id="3cf49-126">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="3cf49-127">Можно наблюдать различия в поведении режима параллелизма службы.</span><span class="sxs-lookup"><span data-stu-id="3cf49-127">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="3cf49-128">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="3cf49-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3cf49-129">Отображается режим параллелизма, в котором работает служба, вызываются все операции, и отображается число операций.</span><span class="sxs-lookup"><span data-stu-id="3cf49-129">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="3cf49-130">Обратите внимание, что в режиме параллельности `Multiple` результаты возвращаются в порядке, отличном от порядка вызовов, потому что служба обрабатывает несколько сообщений параллельно.</span><span class="sxs-lookup"><span data-stu-id="3cf49-130">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="3cf49-131">Если изменить режим параллельности на `Single`, результаты возвращаются в порядке вызова, потому что служба обрабатывает все сообщения последовательно.</span><span class="sxs-lookup"><span data-stu-id="3cf49-131">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="3cf49-132">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="3cf49-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3cf49-133">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="3cf49-133">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3cf49-134">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3cf49-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3cf49-135">Если для создания прокси-клиента используется Svcutil.exe, убедитесь, что включен `/async` параметр.</span><span class="sxs-lookup"><span data-stu-id="3cf49-135">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="3cf49-136">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3cf49-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="3cf49-137">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3cf49-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3cf49-138">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="3cf49-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3cf49-139">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="3cf49-139">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3cf49-140">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="3cf49-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3cf49-141">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="3cf49-141">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
