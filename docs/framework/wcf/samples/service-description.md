---
description: 'Дополнительные сведения о: описание службы'
title: Описание службы
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: 0985933bb48708faac716575f6a95588df1620d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793094"
---
# <a name="service-description"></a><span data-ttu-id="a3bb0-103">Описание службы</span><span class="sxs-lookup"><span data-stu-id="a3bb0-103">Service Description</span></span>

<span data-ttu-id="a3bb0-104">Образец "Описание службы" показывает, как служба может получать свое описание службы в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-104">The Service Description sample demonstrates how a service can retrieve its service description information at runtime.</span></span> <span data-ttu-id="a3bb0-105">Образец основан на [Начало работы](getting-started-sample.md)с дополнительной операцией службы, которая возвращает описательные сведения о службе.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-105">The sample is based on the [Getting Started](getting-started-sample.md), with an additional service operation defined to return descriptive information about the service.</span></span> <span data-ttu-id="a3bb0-106">Возвращаемые сведения содержат базовые адреса и конечные точки службы.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-106">The information that is returned lists the base addresses and endpoints for the service.</span></span> <span data-ttu-id="a3bb0-107">Служба предоставляет эти сведения с помощью классов <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost> и <xref:System.ServiceModel.Description.ServiceDescription>.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-107">The service provides this information using the <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, and <xref:System.ServiceModel.Description.ServiceDescription> classes.</span></span>  
  
 <span data-ttu-id="a3bb0-108">В этом образце клиентом является консольное приложение (EXE), а служба размещается в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3bb0-109">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a3bb0-110">Этот образец содержит модифицированную версию контракта калькулятора под названием `IServiceDescriptionCalculator`.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-110">This sample has a modified version of the calculator contract called `IServiceDescriptionCalculator`.</span></span> <span data-ttu-id="a3bb0-111">Контракт определяет дополнительную операцию службы с именем `GetServiceDescriptionInfo`, возвращающую клиенту многострочный текст, описывающий базовый адрес или адреса и конечную точку или точки службы.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-111">The contract defines an additional service operation named `GetServiceDescriptionInfo` that returns a multi-line string to the client that describes the base address or addresses and service endpoint or endpoints for the service.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IServiceDescriptionCalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    int Divide(int n1, int n2);  
    [OperationContract]  
    string GetServiceDescriptionInfo();  
}  
```  
  
 <span data-ttu-id="a3bb0-112">Код реализации операции `GetServiceDescriptionInfo` использует класс <xref:System.ServiceModel.Description.ServiceDescription> для перечисления конечных точек службы.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-112">The implementation code for `GetServiceDescriptionInfo` uses the <xref:System.ServiceModel.Description.ServiceDescription> to list the service endpoints.</span></span> <span data-ttu-id="a3bb0-113">Так как у конечных точек службы могут быть относительные адреса, он сначала перечисляет базовые адреса службы.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-113">Because service endpoints can have relative addresses, it first lists the base addresses for the service.</span></span> <span data-ttu-id="a3bb0-114">Чтобы вернуть все эти сведения, код получает контекст операции с помощью <xref:System.ServiceModel.OperationContext.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-114">To get all of this information, the code obtains its operation context using <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="a3bb0-115">Класс <xref:System.ServiceModel.ServiceHost> и его объект <xref:System.ServiceModel.Description.ServiceDescription> извлекаются из контекста операции.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-115">The <xref:System.ServiceModel.ServiceHost> and its <xref:System.ServiceModel.Description.ServiceDescription> object are retrieved from the operation context.</span></span> <span data-ttu-id="a3bb0-116">Чтобы перечислить конечные точки службы, код выполняет итерацию коллекции <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> узла службы.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-116">To list the base endpoints for the service, the code iterates through the service host's <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> collection.</span></span> <span data-ttu-id="a3bb0-117">Чтобы перечислить служебные конечные точки службы, код выполняет итерацию коллекции конечных точек описания службы.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-117">To list the service endpoints for the service, the code iterates through the service description's endpoints collection.</span></span>  
  
```csharp
public string GetServiceDescriptionInfo()  
{  
    string info = "";  
    OperationContext operationContext = OperationContext.Current;  
    ServiceHost host = (ServiceHost)operationContext.Host;  
    ServiceDescription desc = host.Description;  
    // Enumerate the base addresses in the service host.  
    info += "Base addresses:\n";  
    foreach (Uri uri in host.BaseAddresses)  
    {  
        info += "    " + uri + "\n";  
    }  
    // Enumerate the service endpoints in the service description.  
    info += "Service endpoints:\n";  
    foreach (ServiceEndpoint endpoint in desc.Endpoints)  
    {  
        info += "    Address:  " + endpoint.Address + "\n";  
        info += "    Binding:  " + endpoint.Binding.Name + "\n";  
        info += "    Contract: " + endpoint.Contract.Name + "\n";  
    }  
     return info;  
}  
```  
  
 <span data-ttu-id="a3bb0-118">При выполнении образца видны операции калькулятора и сведения службы, возвращаемые операцией `GetServiceDescriptionInfo`.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-118">When you run the sample, you see the calculator operations and then the service information returned by the `GetServiceDescriptionInfo` operation.</span></span> <span data-ttu-id="a3bb0-119">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Divide(22,7) = 3  
GetServiceDescriptionInfo  
Base addresses:  
    http://<machine-name>/ServiceModelSamples/service.svc  
    https://<machine-name>/ServiceModelSamples/service.svc  
Service endpoints:  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc  
    Binding:  WSHttpBinding  
    Contract: IServiceDescriptionCalculator  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc/mex  
    Binding:  MetadataExchangeHttpBinding  
    Contract: IMetadataExchange  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a3bb0-120">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="a3bb0-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a3bb0-121">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a3bb0-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a3bb0-122">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a3bb0-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a3bb0-123">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a3bb0-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a3bb0-124">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a3bb0-125">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="a3bb0-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a3bb0-126">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a3bb0-127">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="a3bb0-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
