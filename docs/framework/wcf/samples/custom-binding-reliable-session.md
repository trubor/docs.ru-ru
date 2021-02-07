---
description: 'Дополнительные сведения: надежный сеанс с настраиваемой привязкой'
title: Надежный сеанс с использованием пользовательской привязки
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: 0799e10c0fb86727bc21553584646031dc6f3606
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752522"
---
# <a name="custom-binding-reliable-session"></a><span data-ttu-id="e2d82-103">Надежный сеанс с использованием пользовательской привязки</span><span class="sxs-lookup"><span data-stu-id="e2d82-103">Custom Binding Reliable Session</span></span>

<span data-ttu-id="e2d82-104">Пользовательская привязка определяется упорядоченным списком отдельных элементов привязки.</span><span class="sxs-lookup"><span data-stu-id="e2d82-104">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="e2d82-105">В этом примере показано, как настроить пользовательскую привязку с различными элементами транспорта и кодирования сообщений, уделяя особое внимание реализации надежных сеансов.</span><span class="sxs-lookup"><span data-stu-id="e2d82-105">This sample demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e2d82-106">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="e2d82-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e2d82-107">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="e2d82-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e2d82-108">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="e2d82-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e2d82-109">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="e2d82-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`

## <a name="sample-details"></a><span data-ttu-id="e2d82-110">Подробные сведения об образце</span><span class="sxs-lookup"><span data-stu-id="e2d82-110">Sample Details</span></span>

<span data-ttu-id="e2d82-111">Надежные сеансы обеспечивают возможности для надежного обмена сообщениями и сеансов.</span><span class="sxs-lookup"><span data-stu-id="e2d82-111">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="e2d82-112">При надежном обмене сообщениями в случае сбоя предпринимается повторная попытка передачи, и можно задать такие гарантии доставки, как соблюдение порядка получения сообщений.</span><span class="sxs-lookup"><span data-stu-id="e2d82-112">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="e2d82-113">Сеансы поддерживают состояние для клиентов между вызовами.</span><span class="sxs-lookup"><span data-stu-id="e2d82-113">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="e2d82-114">Пример реализует сеансы для поддержки состояния клиента и задает гарантии соблюдения очередности доставки сообщений.</span><span class="sxs-lookup"><span data-stu-id="e2d82-114">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="e2d82-115">Образец основан на [Начало работы](getting-started-sample.md) , который реализует службу калькулятора.</span><span class="sxs-lookup"><span data-stu-id="e2d82-115">The sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="e2d82-116">Возможности надежного сеанса включаются и настраиваются в файлах конфигурации приложения для клиента и службы.</span><span class="sxs-lookup"><span data-stu-id="e2d82-116">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>

> [!NOTE]
> <span data-ttu-id="e2d82-117">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="e2d82-117">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="e2d82-118">Порядок элементов привязки важен для определения пользовательской привязки, так как каждый из них представляет слой в стеке каналов (см. раздел [пользовательские привязки](../extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="e2d82-118">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../extending/custom-bindings.md)).</span></span>

<span data-ttu-id="e2d82-119">Конфигурация службы для образца определена, как показано в образце.</span><span class="sxs-lookup"><span data-stu-id="e2d82-119">The service configuration for the sample is defined as shown in the following code example.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                     requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"
                        hostNameComparisonMode="StrongWildcard"
                        proxyAuthenticationScheme="Anonymous" realm=""
                        useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

<span data-ttu-id="e2d82-120">Если пример выполняется на нескольких компьютерах, измените адрес конечной точки клиента, чтобы отразить имя узла службы.</span><span class="sxs-lookup"><span data-stu-id="e2d82-120">When running in a cross-machine scenario, you must change client's endpoint address to reflect the host name of the service.</span></span>

<span data-ttu-id="e2d82-121">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="e2d82-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e2d82-122">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="e2d82-122">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e2d82-123">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="e2d82-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e2d82-124">Установите ASP.NET 4,0 с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="e2d82-124">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="e2d82-125">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2d82-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="e2d82-126">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2d82-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="e2d82-127">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2d82-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="e2d82-128">При запуске клиента в конфигурации с несколькими компьютерами не забудьте заменить "localhost" как в `address` атрибуте элемента, так [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) и `clientBaseAddress` [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) с помощью атрибута с именем соответствующего компьютера, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e2d82-128">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element and the `clientBaseAddress` attribute of the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) with the name of the appropriate machine, as shown in the following example.</span></span>

    ```xml
    <endpoint name = ""
    address="http://service_machine_name/servicemodelsamples/service.svc" />
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />
    ```
