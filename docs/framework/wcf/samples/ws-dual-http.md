---
description: 'Подробнее: WS Dual HTTP'
title: WS Dual Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: 44245691a47982f427c82cf8ad81ac2dd8f0b557
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715006"
---
# <a name="ws-dual-http"></a><span data-ttu-id="cd66d-103">WS Dual Http</span><span class="sxs-lookup"><span data-stu-id="cd66d-103">WS Dual Http</span></span>

<span data-ttu-id="cd66d-104">В образце двустороннего HTTP-взаимодействия показано, как настроить привязку `WSDualHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="cd66d-104">The Dual Http sample demonstrates how to configure the `WSDualHttpBinding` binding.</span></span> <span data-ttu-id="cd66d-105">Этот образец содержит консольную программу клиента (EXE) и библиотеку службы (DLL), размещаемую в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="cd66d-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="cd66d-106">Служба реализует дуплексный контракт.</span><span class="sxs-lookup"><span data-stu-id="cd66d-106">The service implements a duplex contract.</span></span> <span data-ttu-id="cd66d-107">Контракт определяется интерфейсом `ICalculatorDuplex`, который предоставляет математические операции (добавить, вычесть, умножить и разделить).</span><span class="sxs-lookup"><span data-stu-id="cd66d-107">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="cd66d-108">В этом образце интерфейс `ICalculatorDuplex` позволяет клиенту выполнять математические операции, вычисляя результат выполнения в сеансе.</span><span class="sxs-lookup"><span data-stu-id="cd66d-108">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over the session.</span></span> <span data-ttu-id="cd66d-109">Независимо от этого служба возвращает результаты в интерфейсе `ICalculatorDuplexCallback`.</span><span class="sxs-lookup"><span data-stu-id="cd66d-109">Independently, the service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="cd66d-110">Для дуплексного контракта требуется сеанс, поскольку необходимо установить контекст для корреляции набора сообщений, обмен которыми осуществляется между клиентом и службой.</span><span class="sxs-lookup"><span data-stu-id="cd66d-110">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between client and service.</span></span> <span data-ttu-id="cd66d-111">Привязка `WSDualHttpBinding` поддерживает дуплексное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="cd66d-111">The `WSDualHttpBinding` binding supports duplex communication.</span></span>

> [!NOTE]
> <span data-ttu-id="cd66d-112">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="cd66d-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cd66d-113">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="cd66d-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cd66d-114">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="cd66d-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="cd66d-115">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="cd66d-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cd66d-116">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="cd66d-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`

<span data-ttu-id="cd66d-117">Чтобы настроить конечную точку службы с привязкой `WSDualHttpBinding`, укажите привязку в конфигурации конечной точки, как показано в примере.</span><span class="sxs-lookup"><span data-stu-id="cd66d-117">To configure a service endpoint with the `WSDualHttpBinding`, specify the binding in the endpoint configuration as shown.</span></span>

```xml
<endpoint address=""
         binding="wsDualHttpBinding"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
```

<span data-ttu-id="cd66d-118">На стороне клиента необходимо настроить адрес, который будет использоваться сервером для подключения к клиенту, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="cd66d-118">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint address=
         "http://localhost/servicemodelsamples/service.svc"
         binding="wsDualHttpBinding"
         bindingConfiguration="Binding1"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
  </client>

  <bindings>
    <!-- Configure a WSDualHttpBinding that supports duplex -->
    <!-- communication. -->
    <wsDualHttpBinding>
      <binding name="Binding1"
               clientBaseAddress="http://localhost:8000/myClient/"
               useDefaultWebProxy="true"
               bypassProxyOnLocal="false">
      </binding>
    </wsDualHttpBinding>
  </bindings>
</system.serviceModel>
```

<span data-ttu-id="cd66d-119">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="cd66d-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="cd66d-120">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="cd66d-120">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate client once the output is displayed.

Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

<span data-ttu-id="cd66d-121">При выполнении образца видны отправляемые службой сообщения, возвращаемые клиенту в интерфейсе обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="cd66d-121">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="cd66d-122">Отображается каждый промежуточный результат с последующим отображением всей формулы после завершения всех операций.</span><span class="sxs-lookup"><span data-stu-id="cd66d-122">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="cd66d-123">Чтобы закрыть клиент, нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="cd66d-123">Press ENTER to shut down the client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cd66d-124">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="cd66d-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="cd66d-125">Установите ASP.NET 4,0 с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="cd66d-125">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="cd66d-126">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cd66d-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="cd66d-127">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cd66d-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="cd66d-128">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cd66d-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="cd66d-129">При запуске клиента в конфигурации с несколькими компьютерами не забудьте заменить localhost как в `address` атрибуте [ \<endpoint> \<client> элемента,](../../configure-apps/file-schema/wcf/endpoint-of-client.md) так и в `clientBaseAddress` атрибуте [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) элемента элемента [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) с именем соответствующего компьютера, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="cd66d-129">When running the client in a cross-machine configuration, be sure to replace localhost in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element of the [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown:</span></span>

    ```xml
    <client>
        <endpoint name = ""
          address=
         "http://service_machine_name/servicemodelsamples/service.svc"
        />
    </client>
    ...
    <wsDualHttpBinding>
        <binding name="DuplexBinding" clientBaseAddress=
            "http://client_machine_name:8000/myClient/">
        </binding>
    </wsDualHttpBinding>
    ```
