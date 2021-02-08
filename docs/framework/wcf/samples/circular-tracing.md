---
description: 'Дополнительные сведения: Циклическая трассировка'
title: Циклическая трассировка
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: 4b50420c7eb0c6ca9bc6b3354c78e7922b00f16c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778754"
---
# <a name="circular-tracing"></a><span data-ttu-id="46f15-103">Циклическая трассировка</span><span class="sxs-lookup"><span data-stu-id="46f15-103">Circular Tracing</span></span>

<span data-ttu-id="46f15-104">Этот образец демонстрирует реализацию прослушивателя трассировки циклического буфера.</span><span class="sxs-lookup"><span data-stu-id="46f15-104">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="46f15-105">Обычным сценарием для производственных служб является длительная доступность этих служб и включенное ведение журнала трассировки на низком уровне.</span><span class="sxs-lookup"><span data-stu-id="46f15-105">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="46f15-106">Этим службам требуется много пространства на диске.</span><span class="sxs-lookup"><span data-stu-id="46f15-106">These services consume a lot of disk space.</span></span> <span data-ttu-id="46f15-107">При устранении неполадок службы к устранению проблемы имеют отношение последние записанные данные из журнала трассировки.</span><span class="sxs-lookup"><span data-stu-id="46f15-107">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="46f15-108">Этот образец демонстрирует реализацию прослушивателя трассировки циклического буфера, в котором на диске хранятся только самые последние трассировки с объемом данных, не превышающим заданного в настройках.</span><span class="sxs-lookup"><span data-stu-id="46f15-108">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="46f15-109">Этот образец основан на [Начало работы](getting-started-sample.md) и включает пользовательский прослушиватель трассировки.</span><span class="sxs-lookup"><span data-stu-id="46f15-109">This sample is based on the [Getting Started](getting-started-sample.md) and includes a custom tracing listener.</span></span>

> [!NOTE]
> <span data-ttu-id="46f15-110">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="46f15-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="46f15-111">В этом примере предполагается, что вы знакомы с примером [трассировки и ведения журнала сообщений](tracing-and-message-logging.md) и прочитали документацию, предоставленную для примера [трассировки и регистрации сообщений](tracing-and-message-logging.md) .</span><span class="sxs-lookup"><span data-stu-id="46f15-111">This sample assumes that you are familiar with the [Tracing and Message Logging](tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](tracing-and-message-logging.md) sample.</span></span>

## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="46f15-112">Прослушиватель трассировки циклического буфера</span><span class="sxs-lookup"><span data-stu-id="46f15-112">Circular Buffer Trace Listener</span></span>

<span data-ttu-id="46f15-113">Реализация прослушивателя трассировки циклического буфера основана на двух файлах, каждый из которых может содержать до половины общего требуемого объема данных журнала трассировки.</span><span class="sxs-lookup"><span data-stu-id="46f15-113">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="46f15-114">Прослушиватель создает один файл и производит запись в этот файл до тех пор, пока не будет достигнут предел, равный половине объема данных, после чего переключается на второй файл.</span><span class="sxs-lookup"><span data-stu-id="46f15-114">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="46f15-115">После того как прослушивать достигает предела для второго файла, он перезаписывает первый файл, заполняя его новыми трассировками.</span><span class="sxs-lookup"><span data-stu-id="46f15-115">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>

<span data-ttu-id="46f15-116">Этот прослушиватель является производным от `XmlWriteTraceListener` и позволяет просматривать журналы с помощью [средства Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="46f15-116">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="46f15-117">При просмотре журналов можно легко объединить два файла журнала, одновременно открыв их в средстве Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="46f15-117">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="46f15-118">Средство Service Trace Viewer автоматически сортирует трассировки, чтобы они отображались в правильном порядке.</span><span class="sxs-lookup"><span data-stu-id="46f15-118">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>

## <a name="configuration"></a><span data-ttu-id="46f15-119">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="46f15-119">Configuration</span></span>

<span data-ttu-id="46f15-120">Службу можно настроить для использования прослушивателя трассировки циклического буфера, добавив приведенный ниже код в элементы прослушивателя и источника.</span><span class="sxs-lookup"><span data-stu-id="46f15-120">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="46f15-121">Максимальный размер файла задается с помощью атрибута `maxFileSizeKB` в конфигурации прослушивателя трассировки циклического буфера.</span><span class="sxs-lookup"><span data-stu-id="46f15-121">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="46f15-122">Это показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="46f15-122">This is demonstrated in the following code.</span></span>

```xml
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">
      <listeners>
        <add name="CircularTraceListener" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />
  </sharedListeners>
  <trace autoflush="true" />
</system.diagnostics>
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="46f15-123">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="46f15-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="46f15-124">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="46f15-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="46f15-125">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="46f15-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="46f15-126">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="46f15-126">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="46f15-127">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="46f15-127">The samples may already be installed on your computer.</span></span> <span data-ttu-id="46f15-128">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="46f15-128">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="46f15-129">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="46f15-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="46f15-130">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="46f15-130">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`

## <a name="see-also"></a><span data-ttu-id="46f15-131">См. также</span><span class="sxs-lookup"><span data-stu-id="46f15-131">See also</span></span>

- <span data-ttu-id="46f15-132">[Образцы наблюдения за AppFabric](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="46f15-132">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
