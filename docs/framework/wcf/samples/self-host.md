---
description: 'Дополнительные сведения: Self-Host'
title: Резидентное размещение
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: 7421e5e24534fbae16d1ddd11c488ad0269883e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793146"
---
# <a name="self-host"></a><span data-ttu-id="a3e66-103">Резидентное размещение</span><span class="sxs-lookup"><span data-stu-id="a3e66-103">Self-Host</span></span>

<span data-ttu-id="a3e66-104">В этом образце показано, как реализовать резидентную службу в консольном приложения.</span><span class="sxs-lookup"><span data-stu-id="a3e66-104">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="a3e66-105">Этот образец основан на [Начало работы](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a3e66-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="a3e66-106">Файл конфигурации приложения был переименован из Web.config в App.config, и в нем был указан базовый адрес, используемый ведущим приложением.</span><span class="sxs-lookup"><span data-stu-id="a3e66-106">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="a3e66-107">Исходный код службы был изменен, чтобы он реализовывал статическую функцию `Main`, которая создает и открывает узел службы, предоставляющее настроенный базовый адрес.</span><span class="sxs-lookup"><span data-stu-id="a3e66-107">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="a3e66-108">Реализация службы была изменена, чтобы для каждой операции выводить результат на консоль.</span><span class="sxs-lookup"><span data-stu-id="a3e66-108">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="a3e66-109">Клиент остался неизменным, но для него был задан правильный конечный адрес службы.</span><span class="sxs-lookup"><span data-stu-id="a3e66-109">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3e66-110">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="a3e66-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a3e66-111">Этот образец реализует статическую функцию main для создания объекта <xref:System.ServiceModel.ServiceHost> для заданного типа `CalculatorService`, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="a3e66-111">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="a3e66-112">Если служба размещается в службах IIS или службе активации Windows (WAS), базовый адрес службы предоставляется средой размещения.</span><span class="sxs-lookup"><span data-stu-id="a3e66-112">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="a3e66-113">В случае резидентного размещения базовый адрес необходимо указывать самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="a3e66-113">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="a3e66-114">Это делается с помощью элемента, дочернего элемента, дочернего элемента дочернего элемента, `add` [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md) [\<host>](../../configure-apps/file-schema/wcf/host.md) [\<service>](../../configure-apps/file-schema/wcf/service.md) как показано в следующем примере конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a3e66-114">This is done using the `add` element, child of [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../configure-apps/file-schema/wcf/host.md), child of [\<service>](../../configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 <span data-ttu-id="a3e66-115">При запуске данного примера запросы и ответы операций отображаются в окнах консоли как службы, так и клиента.</span><span class="sxs-lookup"><span data-stu-id="a3e66-115">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="a3e66-116">Нажмите клавишу ВВОД в каждом окне консоли, чтобы закрыть службу и клиент.</span><span class="sxs-lookup"><span data-stu-id="a3e66-116">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a3e66-117">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="a3e66-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a3e66-118">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a3e66-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a3e66-119">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a3e66-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a3e66-120">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a3e66-120">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a3e66-121">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="a3e66-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a3e66-122">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="a3e66-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a3e66-123">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="a3e66-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a3e66-124">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="a3e66-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="a3e66-125">См. также</span><span class="sxs-lookup"><span data-stu-id="a3e66-125">See also</span></span>

- <span data-ttu-id="a3e66-126">[Образцы размещения и сохраняемости AppFabric](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a3e66-126">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
