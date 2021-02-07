---
description: 'Дополнительные сведения о: NetNamedPipeBinding'
title: NetNamedPipeBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
ms.openlocfilehash: b405ab63fb9aa6b54ed29f45f1024a346c818bd2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752149"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="3199f-103">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="3199f-103">NetNamedPipeBinding</span></span>

<span data-ttu-id="3199f-104">В этом образце показана привязка `netNamedPipeBinding`, обеспечивающая обмен данными между процессами одного компьютера.</span><span class="sxs-lookup"><span data-stu-id="3199f-104">This sample demonstrates the `netNamedPipeBinding` binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="3199f-105">Использование именованных каналов для обмена данными между компьютерами не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="3199f-105">Named pipes do not work across machines.</span></span> <span data-ttu-id="3199f-106">Этот образец основан на службе калькулятора [Начало работы](getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="3199f-106">This sample is based on The [Getting Started](getting-started-sample.md) calculator service.</span></span>  
  
 <span data-ttu-id="3199f-107">В этом образце служба является резидентной.</span><span class="sxs-lookup"><span data-stu-id="3199f-107">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="3199f-108">И клиент, и служба являются консольными приложениями.</span><span class="sxs-lookup"><span data-stu-id="3199f-108">Both the client and the service are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3199f-109">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="3199f-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3199f-110">Привязка задается в файлах конфигурации для клиента и службы.</span><span class="sxs-lookup"><span data-stu-id="3199f-110">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="3199f-111">Тип привязки указывается в `binding` атрибуте [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) или [ \<endpoint> \<client> элемента](../../configure-apps/file-schema/wcf/endpoint-of-client.md) , как показано в следующем образце конфигурации:</span><span class="sxs-lookup"><span data-stu-id="3199f-111">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) or [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element, as shown in the following sample configuration:</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="3199f-112">В предыдущем примере показано, как настроить конечную точку для использования привязки `netNamedPipeBinding` с параметрами по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3199f-112">The previous sample shows how to configure an endpoint to use the `netNamedPipeBinding` binding with the default settings.</span></span> <span data-ttu-id="3199f-113">Чтобы настроить привязку `netNamedPipeBinding` и изменить некоторые ее параметры, необходимо определить конфигурацию привязки.</span><span class="sxs-lookup"><span data-stu-id="3199f-113">If you want to configure the `netNamedPipeBinding` binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="3199f-114">Конечная точка должна ссылаться на конфигурацию привязки по имени с атрибутом `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="3199f-114">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="3199f-115">В этом образце конфигурация привязки называется `Binding1` и имеет следующее определение.</span><span class="sxs-lookup"><span data-stu-id="3199f-115">In this sample, the binding configuration is named `Binding1` and has the following definition:</span></span>  
  
```xml  
<bindings>  
  <!--   
        Following is the expanded configuration section for a NetNamedPipeBinding.  
        Each property is configured with the default value.  
     -->  
  <netNamedPipeBinding>  
    <binding name="Binding1"
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"  
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"
             maxBufferPoolSize="524288"  
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">  
      <security mode="Transport">  
        <transport protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netNamedPipeBinding>  
</bindings>  
```  
  
 <span data-ttu-id="3199f-116">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="3199f-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3199f-117">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="3199f-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3199f-118">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="3199f-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3199f-119">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3199f-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3199f-120">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3199f-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3199f-121">Чтобы запустить пример в конфигурации с одним компьютером, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3199f-121">To run the sample in a single machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3199f-122">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="3199f-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3199f-123">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="3199f-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3199f-124">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="3199f-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3199f-125">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="3199f-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
