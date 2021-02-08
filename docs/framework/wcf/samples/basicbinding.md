---
description: 'Дополнительные сведения о: Басикбиндинг'
title: BasicBinding
ms.date: 03/30/2017
ms.assetid: 86fbeb87-4d89-4b61-9577-867e0ac12945
ms.openlocfilehash: 3a539ccec12d86b40198b01597b152b60b03c49b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778767"
---
# <a name="basicbinding"></a><span data-ttu-id="7e0d6-103">BasicBinding</span><span class="sxs-lookup"><span data-stu-id="7e0d6-103">BasicBinding</span></span>

<span data-ttu-id="7e0d6-104">В следующем примере кода показано использование привязки `basicHttpBinding`, которая обеспечивает взаимодействие по HTTP-протоколу и максимальные возможности взаимодействия с веб-службами первого и второго поколений.</span><span class="sxs-lookup"><span data-stu-id="7e0d6-104">This sample demonstrates the use of `basicHttpBinding` that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span>

> [!NOTE]
> <span data-ttu-id="7e0d6-105">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="7e0d6-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e0d6-106">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="7e0d6-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7e0d6-107">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="7e0d6-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7e0d6-108">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="7e0d6-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7e0d6-109">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="7e0d6-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\Http`

## <a name="sample-details"></a><span data-ttu-id="7e0d6-110">Подробные сведения об образце</span><span class="sxs-lookup"><span data-stu-id="7e0d6-110">Sample Details</span></span>

<span data-ttu-id="7e0d6-111">Этот образец основан на [Начало работы](getting-started-sample.md) , который реализует службу калькулятора.</span><span class="sxs-lookup"><span data-stu-id="7e0d6-111">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>

<span data-ttu-id="7e0d6-112">Для использования базовой привязки с поведением по умолчанию требуется только имя раздела привязки.</span><span class="sxs-lookup"><span data-stu-id="7e0d6-112">To use the basic binding with default behavior, only the binding section name is required.</span></span> <span data-ttu-id="7e0d6-113">Если необходимо настроить основную привязку и изменить некоторые из ее параметров, необходимо определить конфигурацию привязки.</span><span class="sxs-lookup"><span data-stu-id="7e0d6-113">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="7e0d6-114">Конечная точка должна ссылаться на конфигурацию привязки по имени с помощью `bindingConfiguration` атрибута `endpoint` элемента <>, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="7e0d6-114">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the <`endpoint`> element, as shown in the following sample code.</span></span>

```xml
<services>
    <service
        type="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
       <endpoint address=""
             binding="basicHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
</services>
```

<span data-ttu-id="7e0d6-115">В этом образце конфигурация привязки именуется `"Binding1"` и определена, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="7e0d6-115">In this sample, the binding configuration is named `"Binding1"` and is defined as shown in the following code example.</span></span>

```xml
<bindings>
   <basicHttpBinding>
      <binding name="Binding1"
               hostNameComparisonMode="StrongWildcard"
               receiveTimeout="00:10:00"
               sendTimeout="00:10:00"
               openTimeout="00:10:00"
               closeTimeout="00:10:00"
               maxMessageSize="65536"
               maxBufferSize="65536"
               maxBufferPoolSize="524288"
               transferMode="Buffered"
               messageEncoding="Text"
               textEncoding="utf-8"
               bypassProxyOnLocal="false"
               useDefaultWebProxy="true" >
         <security mode="None" />
      </binding>
   </basicHttpBinding>
</bindings>
```

<span data-ttu-id="7e0d6-116">Элемент привязки обеспечивает атрибуты для установки режима сравнения имени узла, максимального размера сообщения, параметр прокси, времени ожидания, кодирования сообщений и прочих опций.</span><span class="sxs-lookup"><span data-stu-id="7e0d6-116">The binding element provides attributes for setting the host name comparison mode, maximum message size, proxy options, timeouts, message encoding, and other options.</span></span>

<span data-ttu-id="7e0d6-117">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="7e0d6-117">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7e0d6-118">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="7e0d6-118">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7e0d6-119">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="7e0d6-119">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="7e0d6-120">Установите ASP.NET 4,0 с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="7e0d6-120">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="7e0d6-121">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7e0d6-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="7e0d6-122">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7e0d6-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="7e0d6-123">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7e0d6-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>
