---
description: 'Дополнительные сведения: поведение службы по умолчанию'
title: Поведение служб по умолчанию
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: a0b83180c9ab758cb7a8db7f92a8bf0c081e4489
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631987"
---
# <a name="default-service-behavior"></a><span data-ttu-id="14d03-103">Поведение служб по умолчанию</span><span class="sxs-lookup"><span data-stu-id="14d03-103">Default Service Behavior</span></span>

<span data-ttu-id="14d03-104">В этом образце показано, как могут настраиваться параметры поведения службы.</span><span class="sxs-lookup"><span data-stu-id="14d03-104">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="14d03-105">Образец основан на [Начало работы](getting-started-sample.md), который реализует `ICalculator` контракт службы.</span><span class="sxs-lookup"><span data-stu-id="14d03-105">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="14d03-106">В этом образце с помощью атрибутов <xref:System.ServiceModel.ServiceBehaviorAttribute> и <xref:System.ServiceModel.OperationBehaviorAttribute> явным образом определены поведения службы и операции.</span><span class="sxs-lookup"><span data-stu-id="14d03-106">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="14d03-107">Поведения можно настраивать в файлах конфигурации или непосредственно в коде (как показано в этом образце).</span><span class="sxs-lookup"><span data-stu-id="14d03-107">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="14d03-108">В этом образце клиентом является консольное приложение (EXE), а служба размещается в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="14d03-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14d03-109">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="14d03-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="14d03-110">Класс службы задает поведение с помощью атрибутов <xref:System.ServiceModel.ServiceBehaviorAttribute> и <xref:System.ServiceModel.OperationBehaviorAttribute>, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="14d03-110">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="14d03-111">Все заданные значения являются значениями по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="14d03-111">All values specified are the defaults.</span></span>  
  
```csharp
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="14d03-112">Поведения службы задаются атрибутом <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="14d03-112">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="14d03-113">В приведенной ниже таблице описаны некоторые из этих поведений.</span><span class="sxs-lookup"><span data-stu-id="14d03-113">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="14d03-114">Поведение службы</span><span class="sxs-lookup"><span data-stu-id="14d03-114">Service behavior</span></span>|<span data-ttu-id="14d03-115">Описание</span><span class="sxs-lookup"><span data-stu-id="14d03-115">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="14d03-116">Автоматически завершает сеанс по запросу клиента.</span><span class="sxs-lookup"><span data-stu-id="14d03-116">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="14d03-117">Задает режим параллелизма для каждого из экземпляров служб.</span><span class="sxs-lookup"><span data-stu-id="14d03-117">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="14d03-118">Задает режим контекста экземпляра.</span><span class="sxs-lookup"><span data-stu-id="14d03-118">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="14d03-119">Определяет, нужно ли использовать предоставляемый контекст синхронизации, если он задан.</span><span class="sxs-lookup"><span data-stu-id="14d03-119">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="14d03-120">Его следует использовать, если требуется определить, нужно ли использовать `WindowsFormsSynchronizationContext` в приложениях Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="14d03-120">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="14d03-121">Определяет, что общие необработанные исключения выполнения должны преобразовываться в `Fault<string>` и отправляться как сообщения об ошибках.</span><span class="sxs-lookup"><span data-stu-id="14d03-121">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="14d03-122">Задает уровень изоляции транзакций.</span><span class="sxs-lookup"><span data-stu-id="14d03-122">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="14d03-123">Определяет, вызывают ли неожиданные заголовки сообщений ошибку.</span><span class="sxs-lookup"><span data-stu-id="14d03-123">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="14d03-124">Поведения операций задаются атрибутом <xref:System.ServiceModel.OperationBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="14d03-124">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="14d03-125">В приведенной ниже таблице описаны некоторые из этих поведений.</span><span class="sxs-lookup"><span data-stu-id="14d03-125">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="14d03-126">Поведение операции</span><span class="sxs-lookup"><span data-stu-id="14d03-126">Operation Behavior</span></span>|<span data-ttu-id="14d03-127">Описание</span><span class="sxs-lookup"><span data-stu-id="14d03-127">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="14d03-128">Определяет, приводит ли завершение операции службы к завершению текущей транзакции.</span><span class="sxs-lookup"><span data-stu-id="14d03-128">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="14d03-129">Определяет, зачислятся ли операция службы в транзакции потока клиента.</span><span class="sxs-lookup"><span data-stu-id="14d03-129">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="14d03-130">Определяет, олицетворяет ли операция службы удостоверение вызывающей стороны.</span><span class="sxs-lookup"><span data-stu-id="14d03-130">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="14d03-131">Определяет, удаляются ли экземпляры служб при начале и завершении вызова операции службы.</span><span class="sxs-lookup"><span data-stu-id="14d03-131">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="14d03-132">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="14d03-132">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="14d03-133">Задержка между вызовами связана с вызовами метода `System.Threading.Thread.Sleep()` в операциях службы.</span><span class="sxs-lookup"><span data-stu-id="14d03-133">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="14d03-134">В остальных образцах поведений эти поведения описаны более подробно.</span><span class="sxs-lookup"><span data-stu-id="14d03-134">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="14d03-135">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="14d03-135">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="14d03-136">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="14d03-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="14d03-137">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="14d03-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="14d03-138">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="14d03-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="14d03-139">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="14d03-139">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="14d03-140">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="14d03-140">The samples may already be installed on your machine.</span></span> <span data-ttu-id="14d03-141">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="14d03-141">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="14d03-142">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="14d03-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="14d03-143">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="14d03-143">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
