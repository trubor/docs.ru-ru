---
description: 'Подробнее: поведение при отладке службы'
title: Поведение отладки службы
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 3aae4a4cca53fce50bff8ec02896e748f430166f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793107"
---
# <a name="service-debug-behavior"></a><span data-ttu-id="69d5a-103">Поведение отладки службы</span><span class="sxs-lookup"><span data-stu-id="69d5a-103">Service Debug Behavior</span></span>

<span data-ttu-id="69d5a-104">В этом образце показано, как могут настраиваться параметры поведения отладки службы.</span><span class="sxs-lookup"><span data-stu-id="69d5a-104">This sample demonstrates how service debug behavior settings can be configured.</span></span> <span data-ttu-id="69d5a-105">Образец основан на [Начало работы](getting-started-sample.md), который реализует `ICalculator` контракт службы.</span><span class="sxs-lookup"><span data-stu-id="69d5a-105">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="69d5a-106">Этот образец явно определяет поведение отладки службы в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="69d5a-106">This sample explicitly defines service debug behavior in the configuration file.</span></span> <span data-ttu-id="69d5a-107">Это также можно выполнить императивно в коде.</span><span class="sxs-lookup"><span data-stu-id="69d5a-107">It can also be done imperatively in code.</span></span>

<span data-ttu-id="69d5a-108">В этом образце клиентом является консольное приложение (EXE), а служба размещается в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="69d5a-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="69d5a-109">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="69d5a-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="69d5a-110">Файл Web.config для сервера определяет поведение отладки службы для включения страницы справки и обработки исключений, как показано в следующем образце.</span><span class="sxs-lookup"><span data-stu-id="69d5a-110">The Web.config file for the server defines the service debug behavior to enable the help page and exception handling as shown in the following sample.</span></span>

```xml
<behaviors>
     <serviceBehaviors>
         <behavior name="CalculatorServiceBehavior">
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->
         <!-- Please set this to false when deploying -->
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>
         </behavior>
     </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="69d5a-111">[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md) — Это элемент конфигурации, позволяющий изменять свойства поведения при отладке службы.</span><span class="sxs-lookup"><span data-stu-id="69d5a-111">[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md) is the configuration element that allows changing the service debug behavior properties.</span></span> <span data-ttu-id="69d5a-112">Пользователь может изменять это поведение для достижения следующих целей.</span><span class="sxs-lookup"><span data-stu-id="69d5a-112">The user can modify this behavior to achieve the following:</span></span>

- <span data-ttu-id="69d5a-113">Это позволяет службе возвращать любое исключение, вызванное кодом приложения, даже если это исключение не объявлено с помощью атрибута <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="69d5a-113">This allows the service to return any exception that is thrown by the application code even if the exception is not declared using the <xref:System.ServiceModel.FaultContractAttribute>.</span></span> <span data-ttu-id="69d5a-114">Для этого необходимо присвоить параметру `includeExceptionDetailInFaults` значение `true`.</span><span class="sxs-lookup"><span data-stu-id="69d5a-114">It is done by setting `includeExceptionDetailInFaults` to `true`.</span></span> <span data-ttu-id="69d5a-115">Этот параметр полезен при отладке в тех случаях, когда сервер создает непредвиденное исключение.</span><span class="sxs-lookup"><span data-stu-id="69d5a-115">This setting is useful when debugging cases where the server is throwing an unexpected exception.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="69d5a-116">Включать этот параметр в производственной среде небезопасно.</span><span class="sxs-lookup"><span data-stu-id="69d5a-116">It is not secure to turn this setting on in a production environment.</span></span> <span data-ttu-id="69d5a-117">В непредвиденном исключении сервера может содержаться информация, не предназначенная для клиента, поэтому присвоение параметру `includeExceptionDetailsInFaults` значения `true` может привести к утечке информации.</span><span class="sxs-lookup"><span data-stu-id="69d5a-117">An unexpected server exception may have some information that is not intended for the client and so setting `includeExceptionDetailsInFaults` to `true` might result in an information leak.</span></span>

- <span data-ttu-id="69d5a-118">[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md)Кроме того, позволяет пользователю включать или отключать страницу справки.</span><span class="sxs-lookup"><span data-stu-id="69d5a-118">The [\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md) also allows a user to enable or disable the help page.</span></span> <span data-ttu-id="69d5a-119">Каждая служба может предоставлять страницу справки, которая содержит данные о службе, включая сведения о конечной точке для получения WSDL для службы.</span><span class="sxs-lookup"><span data-stu-id="69d5a-119">Each service can optionally expose a help page that contains information about the service including the endpoint to get WSDL for the service.</span></span> <span data-ttu-id="69d5a-120">Эту возможность можно включить, присвоив параметру `httpHelpPageEnabled` значение `true`.</span><span class="sxs-lookup"><span data-stu-id="69d5a-120">This can be enabled by setting `httpHelpPageEnabled` to `true`.</span></span> <span data-ttu-id="69d5a-121">Это позволяет возвращать страницу справки в ответ на запрос GET к базовому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="69d5a-121">This enables the help page to be returned to a GET request to the base address of the service.</span></span> <span data-ttu-id="69d5a-122">Этот адрес можно изменить, задав другой атрибут `httpHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="69d5a-122">You can change this address by setting another attribute `httpHelpPageUrl`.</span></span> <span data-ttu-id="69d5a-123">Можно сделать этот процесс безопасным, если использовать транспорт HTTPS вместо HTTP.</span><span class="sxs-lookup"><span data-stu-id="69d5a-123">You can make this secure by using HTTPS instead of HTTP.</span></span> <span data-ttu-id="69d5a-124">Для этого необходимо задать `httpsHelpPageEnabled` и `httpsHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="69d5a-124">This can be done by setting `httpsHelpPageEnabled` and `httpsHelpPageUrl`.</span></span>

<span data-ttu-id="69d5a-125">При выполнении примера запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="69d5a-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="69d5a-126">Первые три операции (сложение, вычитание и умножение) должны выполняться успешно.</span><span class="sxs-lookup"><span data-stu-id="69d5a-126">The first three operations (Add, Subtract and Multiply) must succeed.</span></span> <span data-ttu-id="69d5a-127">Последняя операция (деление) завершается неудачей - выдается исключение в результате деления на ноль.</span><span class="sxs-lookup"><span data-stu-id="69d5a-127">The last operation ("divide") fails with a division by zero exception.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="69d5a-128">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="69d5a-128">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="69d5a-129">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="69d5a-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="69d5a-130">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="69d5a-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="69d5a-131">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="69d5a-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="69d5a-132">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="69d5a-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="69d5a-133">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="69d5a-133">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="69d5a-134">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="69d5a-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="69d5a-135">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="69d5a-135">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`
