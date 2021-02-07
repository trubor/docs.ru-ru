---
description: 'Дополнительные сведения: Расширение трассировки'
title: Расширение трассировки
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: e387f49eb4b31ce8dc0b726853ef69d20c8af063
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752370"
---
# <a name="extend-tracing"></a><span data-ttu-id="430ae-103">Расширить трассировку</span><span class="sxs-lookup"><span data-stu-id="430ae-103">Extend tracing</span></span>

<span data-ttu-id="430ae-104">В этом примере показано, как расширить функцию трассировки Windows Communication Foundation (WCF) путем написания пользовательских трассировок действий в клиенте и в коде службы.</span><span class="sxs-lookup"><span data-stu-id="430ae-104">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="430ae-105">Написание трассировки определяемых пользователем действий позволяет пользователю создавать действия трассировки и группировать трассировки в логические единицы работы.</span><span class="sxs-lookup"><span data-stu-id="430ae-105">Writing user-defined activity traces allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="430ae-106">Кроме того, возможно согласование действий с помощью передач (в рамках одной конечной точки) и распространения (между конечными точками).</span><span class="sxs-lookup"><span data-stu-id="430ae-106">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="430ae-107">В этом образце трассировка включается как для клиента, так и для службы.</span><span class="sxs-lookup"><span data-stu-id="430ae-107">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="430ae-108">Дополнительные сведения о включении трассировки в файлах конфигурации клиента и службы см. в разделе [Трассировка и ведение журнала сообщений](tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="430ae-108">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="430ae-109">Этот образец основан на [Начало работы](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="430ae-109">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="430ae-110">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="430ae-110">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="430ae-111">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="430ae-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="430ae-112">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="430ae-112">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="430ae-113">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="430ae-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="430ae-114">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="430ae-114">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="430ae-115">Трассировка и распространение действий</span><span class="sxs-lookup"><span data-stu-id="430ae-115">Tracing and Activity Propagation</span></span>  

 <span data-ttu-id="430ae-116">Определяемая пользователем трассировка действий позволяет пользователю создавать собственные действия трассировки для группирования трассировок в логические единицы работы, сопоставлять действия посредством передачи и распространения, а также уменьшить затраты на производительность трассировки WCF (например, стоимость дискового пространства в файле журнала).</span><span class="sxs-lookup"><span data-stu-id="430ae-116">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="add-custom-sources"></a><span data-ttu-id="430ae-117">Добавление пользовательских источников</span><span class="sxs-lookup"><span data-stu-id="430ae-117">Add custom sources</span></span>  

 <span data-ttu-id="430ae-118">Пользовательские трассировки можно добавлять как в код клиента, так и в код службы.</span><span class="sxs-lookup"><span data-stu-id="430ae-118">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="430ae-119">Добавление источников трассировки в файлы конфигурации клиента или службы позволяет записывать и отображать эти пользовательские трассировки в средстве [Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="430ae-119">Adding trace sources to the client or service configuration files allows for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="430ae-120">В следующем примере кода показано, как добавить в файл конфигурации пользовательский источник трассировки с именем `ServerCalculatorTraceSource`.</span><span class="sxs-lookup"><span data-stu-id="430ae-120">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>
....
```  
  
### <a name="correlate-activities"></a><span data-ttu-id="430ae-121">Корреляция действий</span><span class="sxs-lookup"><span data-stu-id="430ae-121">Correlate activities</span></span>  

 <span data-ttu-id="430ae-122">Для непосредственного согласования действий между конечными точками в источнике трассировки `propagateActivity` атрибут `true` должен иметь значение `System.ServiceModel`.</span><span class="sxs-lookup"><span data-stu-id="430ae-122">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="430ae-123">Кроме того, для распространения трассировок без выполнения действий WCF трассировка действий ServiceModel должна быть отключена.</span><span class="sxs-lookup"><span data-stu-id="430ae-123">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="430ae-124">Это показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="430ae-124">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="430ae-125">Отключение трассировки действия ServiceModel не эквивалентно указанию значения off для уровня трассировки, обозначаемого свойством `switchValue`.</span><span class="sxs-lookup"><span data-stu-id="430ae-125">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessen-performance-cost"></a><span data-ttu-id="430ae-126">Снижение затрат на производительность</span><span class="sxs-lookup"><span data-stu-id="430ae-126">Lessen performance cost</span></span>  

 <span data-ttu-id="430ae-127">Установка для свойства `ActivityTracing` значения off в трассировке `System.ServiceModel` создает файл трассировки, который содержит только пользовательские трассировки действий без включения каких-либо трассировок действий ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="430ae-127">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="430ae-128">Исключение трассировки действий ServiceModel приводит к тому, что файл журнала намного меньше.</span><span class="sxs-lookup"><span data-stu-id="430ae-128">Excluding ServiceModel activity traces results in a much smaller log file.</span></span> <span data-ttu-id="430ae-129">Однако возможность корреляции трассировок обработки WCF теряется.</span><span class="sxs-lookup"><span data-stu-id="430ae-129">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="430ae-130">Настройка, сборка и запуск примера</span><span class="sxs-lookup"><span data-stu-id="430ae-130">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="430ae-131">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="430ae-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="430ae-132">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="430ae-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="430ae-133">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="430ae-133">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430ae-134">См. также</span><span class="sxs-lookup"><span data-stu-id="430ae-134">See also</span></span>

- <span data-ttu-id="430ae-135">[Образцы наблюдения за AppFabric](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="430ae-135">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
