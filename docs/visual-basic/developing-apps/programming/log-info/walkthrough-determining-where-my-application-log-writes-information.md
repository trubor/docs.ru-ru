---
description: 'Подробнее о следующем: Пошаговое руководство. Определение места записи информации для My.Application.Log (Visual Basic)'
title: Определение места записи сведений для My.Application.Log
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: 4ddb5777bcbdde07069efd2fd3a66f0c220ee135
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792288"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="860aa-103">Пошаговое руководство. Определение места записи информации для My.Application.Log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="860aa-103">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="860aa-104">Объект `My.Application.Log` может записывать информацию в несколько прослушивателей журналов.</span><span class="sxs-lookup"><span data-stu-id="860aa-104">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="860aa-105">Прослушиватели журнала настраиваются в файле конфигурации компьютера и могут переопределяться в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="860aa-105">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="860aa-106">В этом разделе описаны параметры по умолчанию и способ определения параметров для приложения.</span><span class="sxs-lookup"><span data-stu-id="860aa-106">This topic describes the default settings and how to determine the settings for your application.</span></span>

<span data-ttu-id="860aa-107">Дополнительные сведения о расположении выходных данных по умолчанию см. в разделе [Работа с журналами приложения](working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="860aa-107">For more information about the default output locations, see [Working with Application Logs](working-with-application-logs.md).</span></span>

### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="860aa-108">Определение прослушивателей для объекта My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="860aa-108">To determine the listeners for My.Application.Log</span></span>

1. <span data-ttu-id="860aa-109">Найдите файл конфигурации сборки.</span><span class="sxs-lookup"><span data-stu-id="860aa-109">Locate the assembly's configuration file.</span></span> <span data-ttu-id="860aa-110">Во время разработки сборки доступ к файлу app.config в Visual Studio можно получить в **обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="860aa-110">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="860aa-111">В противном случае имя файла конфигурации — это имя сборки с расширением .config, а расположен он в том же каталоге, что и сборка.</span><span class="sxs-lookup"><span data-stu-id="860aa-111">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="860aa-112">Не каждая сборка имеет файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="860aa-112">Not every assembly has a configuration file.</span></span>

    <span data-ttu-id="860aa-113">Файл конфигурации является XML-файлом.</span><span class="sxs-lookup"><span data-stu-id="860aa-113">The configuration file is an XML file.</span></span>

2. <span data-ttu-id="860aa-114">Найдите раздел `<listeners>` в разделе `<source>` с атрибутом `name` , равным DefaultSource, в разделе `<sources>` .</span><span class="sxs-lookup"><span data-stu-id="860aa-114">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="860aa-115">Раздел `<sources>` находится в разделе `<system.diagnostics>` в разделе `<configuration>` верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="860aa-115">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

    <span data-ttu-id="860aa-116">Если эти разделы не существуют, то настройка прослушивателей журнала `My.Application.Log` может быть задана в файле конфигурации компьютера.</span><span class="sxs-lookup"><span data-stu-id="860aa-116">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="860aa-117">Далее описано, как выяснить, что определяется в файле конфигурации компьютера.</span><span class="sxs-lookup"><span data-stu-id="860aa-117">The following steps describe how to determine what the computer configuration file defines:</span></span>

    1. <span data-ttu-id="860aa-118">Найдите файл machine.config компьютера.</span><span class="sxs-lookup"><span data-stu-id="860aa-118">Locate the computer's machine.config file.</span></span> <span data-ttu-id="860aa-119">Как правило, он находится в каталоге *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG*, где `SystemRoot` — каталог операционной системы, а `frameworkVersion` — версия .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="860aa-119">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the .NET Framework.</span></span>

        <span data-ttu-id="860aa-120">Параметры в файле machine.config могут быть переопределены файлом конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="860aa-120">The settings in machine.config can be overridden by an application's configuration file.</span></span>

        <span data-ttu-id="860aa-121">Если необязательные элементы, перечисленные ниже, отсутствуют, их можно создать.</span><span class="sxs-lookup"><span data-stu-id="860aa-121">If the optional elements listed below do not exist, you can create them.</span></span>

    2. <span data-ttu-id="860aa-122">Найдите раздел `<listeners>` в разделе `<source>` с атрибутом `name` , равным DefaultSource, в разделе `<sources>` раздела `<system.diagnostics>` в разделе `<configuration>` верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="860aa-122">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

        <span data-ttu-id="860aa-123">Если эти разделы не существуют, то в объекте `My.Application.Log` имеются только прослушиватели журнала по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="860aa-123">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>

3. <span data-ttu-id="860aa-124">Найдите элементы <`add>` в разделе <`listeners>`.</span><span class="sxs-lookup"><span data-stu-id="860aa-124">Locate the <`add>` elements in the <`listeners>` section.</span></span>

     <span data-ttu-id="860aa-125">Эти элементы добавляют именованные прослушиватели журнала в источник `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="860aa-125">These elements add the named log listeners to `My.Application.Log` source.</span></span>

4. <span data-ttu-id="860aa-126">Найдите элементы `<add>` с именами прослушивателей журнала в разделе `<sharedListeners>` раздела `<system.diagnostics>` в разделе `<configuration>` верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="860aa-126">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="860aa-127">Данные инициализации для многих типов общих прослушивателей включают описание того, куда прослушиватель направляет данные.</span><span class="sxs-lookup"><span data-stu-id="860aa-127">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>

    - <span data-ttu-id="860aa-128">Прослушиватель <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> записывает данные в журнал файлов, как описано во введении.</span><span class="sxs-lookup"><span data-stu-id="860aa-128">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>

    - <span data-ttu-id="860aa-129">Прослушиватель <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> записывает данные в журнал событий компьютера, определяемый параметром `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="860aa-129">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="860aa-130">Для просмотра журнала событий можно использовать **обозреватель сервера** или **средство просмотра событий Windows**.</span><span class="sxs-lookup"><span data-stu-id="860aa-130">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="860aa-131">Дополнительные сведения см. в разделе [События трассировки событий Windows в .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="860aa-131">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

    - <span data-ttu-id="860aa-132">Прослушиватели <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> и <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> записывают данные в файл, указанный в параметре `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="860aa-132">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="860aa-133">Прослушиватель <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> выводит данные в консоль командной строки.</span><span class="sxs-lookup"><span data-stu-id="860aa-133">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>

    - <span data-ttu-id="860aa-134">Сведения о том, куда записывают информацию другие типы прослушивателей журналов, приведены в документации по этим типам.</span><span class="sxs-lookup"><span data-stu-id="860aa-134">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="860aa-135">См. также</span><span class="sxs-lookup"><span data-stu-id="860aa-135">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [<span data-ttu-id="860aa-136">Работа с журналами приложения</span><span class="sxs-lookup"><span data-stu-id="860aa-136">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="860aa-137">Практическое руководство. Исплючения журналов</span><span class="sxs-lookup"><span data-stu-id="860aa-137">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="860aa-138">Практическое руководство. Запись сообщений в журнал</span><span class="sxs-lookup"><span data-stu-id="860aa-138">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="860aa-139">Пошаговое руководство: Изменение места записи сведений для My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="860aa-139">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="860aa-140">ETW Events in the .NET Framework</span><span class="sxs-lookup"><span data-stu-id="860aa-140">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)
- [<span data-ttu-id="860aa-141">Устранение неполадок. Прослушиватели журнала</span><span class="sxs-lookup"><span data-stu-id="860aa-141">Troubleshooting: Log Listeners</span></span>](troubleshooting-log-listeners.md)
