---
description: 'Подробнее о следующем: Пошаговое руководство. Фильтрация вывода My.Application.Log (Visual Basic)'
title: Фильтрация выходных данных My.Application.Log
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: 0fa64bde27be17b1809e45bfe294e70c7dd33563
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792262"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="14fc1-103">Пошаговое руководство. Фильтрация вывода My.Application.Log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14fc1-103">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>

<span data-ttu-id="14fc1-104">В этом пошаговом руководстве демонстрируется изменение фильтрации журнала по умолчанию для объекта `My.Application.Log`, чтобы контролировать, какие данные передаются из объекта `Log` в прослушиватели и какие данные записываются прослушивателями.</span><span class="sxs-lookup"><span data-stu-id="14fc1-104">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="14fc1-105">Режим ведения журнала можно изменить даже после создания приложения, поскольку сведения о конфигурации хранятся в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="14fc1-105">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>

## <a name="getting-started"></a><span data-ttu-id="14fc1-106">Приступая к работе</span><span class="sxs-lookup"><span data-stu-id="14fc1-106">Getting Started</span></span>

<span data-ttu-id="14fc1-107">Каждое сообщение, записываемое объектом `My.Application.Log`, имеет соответствующий уровень степени серьезности, используемый механизмами фильтрации для управления выходными данными журнала.</span><span class="sxs-lookup"><span data-stu-id="14fc1-107">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="14fc1-108">В этом примере приложения используются методы `My.Application.Log` для записи нескольких сообщений журналов с различными уровнями степени серьезности.</span><span class="sxs-lookup"><span data-stu-id="14fc1-108">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>

#### <a name="to-build-the-sample-application"></a><span data-ttu-id="14fc1-109">Создание примера приложения</span><span class="sxs-lookup"><span data-stu-id="14fc1-109">To build the sample application</span></span>

1. <span data-ttu-id="14fc1-110">Откройте новый проект приложения Windows на Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="14fc1-110">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="14fc1-111">Добавьте кнопку с именем Button1 в форму Form1.</span><span class="sxs-lookup"><span data-stu-id="14fc1-111">Add a button named Button1 to Form1.</span></span>

3. <span data-ttu-id="14fc1-112">В обработчик события <xref:System.Windows.Forms.Control.Click> добавьте следующий код для Button1:</span><span class="sxs-lookup"><span data-stu-id="14fc1-112">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. <span data-ttu-id="14fc1-113">Запустите приложение в отладчике.</span><span class="sxs-lookup"><span data-stu-id="14fc1-113">Run the application in the debugger.</span></span>

5. <span data-ttu-id="14fc1-114">Нажмите кнопку **Button1**.</span><span class="sxs-lookup"><span data-stu-id="14fc1-114">Press **Button1**.</span></span>

     <span data-ttu-id="14fc1-115">Приложение записывает следующие сведения в файл выходных данных отладки и файл журнала приложения.</span><span class="sxs-lookup"><span data-stu-id="14fc1-115">The application writes the following information to the application's debug output and log file.</span></span>

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. <span data-ttu-id="14fc1-116">Закройте приложение.</span><span class="sxs-lookup"><span data-stu-id="14fc1-116">Close the application.</span></span>

     <span data-ttu-id="14fc1-117">Сведения о просмотре окна вывода отладочных данных приложения см. в разделе [Окно вывода](/visualstudio/ide/reference/output-window).</span><span class="sxs-lookup"><span data-stu-id="14fc1-117">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="14fc1-118">Сведения о расположении файла журнала приложения см. в разделе [Пошаговое руководство. Определение места записи информации для My.Application.Log](walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="14fc1-118">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="14fc1-119">По умолчанию приложение записывает выходные данные в файл журнала при закрытии приложения.</span><span class="sxs-lookup"><span data-stu-id="14fc1-119">By default, the application flushes the log-file output when the application closes.</span></span>

     <span data-ttu-id="14fc1-120">В приведенном выше примере второй вызов метода <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> и вызов метода <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> приводят к получению данных журнала, а первый и последний вызовы метода `WriteEntry` — нет.</span><span class="sxs-lookup"><span data-stu-id="14fc1-120">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="14fc1-121">Это связано с тем, что уровнями серьезности для `WriteEntry` и `WriteException` являются "Информация" и "Ошибка". Оба эти значения разрешены при фильтрации журнала по умолчанию для объекта `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="14fc1-121">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="14fc1-122">Однако событиям с уровнями серьезности "Запуск" и "Остановка" запрещено создание выходных данных журнала.</span><span class="sxs-lookup"><span data-stu-id="14fc1-122">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>

## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="14fc1-123">Фильтрация всех прослушивателей My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="14fc1-123">Filtering for All My.Application.Log Listeners</span></span>

<span data-ttu-id="14fc1-124">Объект `My.Application.Log` использует <xref:System.Diagnostics.SourceSwitch> с именем `DefaultSwitch` для управления сообщениями, передаваемыми из методов `WriteEntry` и `WriteException` в прослушиватели журнала.</span><span class="sxs-lookup"><span data-stu-id="14fc1-124">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="14fc1-125">`DefaultSwitch` можно настроить в файле конфигурации приложения, задав в качестве его значения одно из значений перечисления <xref:System.Diagnostics.SourceLevels>.</span><span class="sxs-lookup"><span data-stu-id="14fc1-125">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="14fc1-126">По умолчанию используется значение "Информация".</span><span class="sxs-lookup"><span data-stu-id="14fc1-126">By default, its value is "Information".</span></span>

<span data-ttu-id="14fc1-127">В этой таблице показан уровень серьезности, необходимый журналу для записи сообщения в прослушиватели с конкретным параметром `DefaultSwitch`.</span><span class="sxs-lookup"><span data-stu-id="14fc1-127">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>

|<span data-ttu-id="14fc1-128">Значение DefaultSwitch</span><span class="sxs-lookup"><span data-stu-id="14fc1-128">DefaultSwitch Value</span></span>|<span data-ttu-id="14fc1-129">Уровень серьезности сообщения, необходимый для вывода</span><span class="sxs-lookup"><span data-stu-id="14fc1-129">Message severity required for output</span></span>|
|---|---|
|`Critical`|`Critical`|
|`Error`|<span data-ttu-id="14fc1-130">`Critical` или `Error`</span><span class="sxs-lookup"><span data-stu-id="14fc1-130">`Critical` or `Error`</span></span>|
|`Warning`|<span data-ttu-id="14fc1-131">`Critical`, `Error`или `Warning`</span><span class="sxs-lookup"><span data-stu-id="14fc1-131">`Critical`, `Error`, or `Warning`</span></span>|
|`Information`|<span data-ttu-id="14fc1-132">`Critical`, `Error`, `Warning` или `Information`</span><span class="sxs-lookup"><span data-stu-id="14fc1-132">`Critical`, `Error`, `Warning`, or `Information`</span></span>|
|`Verbose`|<span data-ttu-id="14fc1-133">`Critical`, `Error`, `Warning`, `Information` или `Verbose`</span><span class="sxs-lookup"><span data-stu-id="14fc1-133">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|
|`ActivityTracing`|<span data-ttu-id="14fc1-134">`Start`, `Stop`, `Suspend`, `Resume` или `Transfer`</span><span class="sxs-lookup"><span data-stu-id="14fc1-134">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|
|`All`|<span data-ttu-id="14fc1-135">Все сообщения разрешены.</span><span class="sxs-lookup"><span data-stu-id="14fc1-135">All messages are allowed.</span></span>|
|`Off`|<span data-ttu-id="14fc1-136">Все сообщения блокируются.</span><span class="sxs-lookup"><span data-stu-id="14fc1-136">All messages are blocked.</span></span>|

> [!NOTE]
> <span data-ttu-id="14fc1-137">Каждый метод `WriteEntry` и `WriteException` имеет перегрузку, которая не указывает уровень серьезности.</span><span class="sxs-lookup"><span data-stu-id="14fc1-137">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="14fc1-138">Неявным уровнем серьезности для перегрузки `WriteEntry` является "Информация", а неявным уровнем серьезности для перегрузки `WriteException` — "Ошибка".</span><span class="sxs-lookup"><span data-stu-id="14fc1-138">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>

<span data-ttu-id="14fc1-139">В этой таблице приводятся выходные данные журнала из предыдущего примера: с параметром `DefaultSwitch` по умолчанию "Информация" только второй вызов метода `WriteEntry` и вызов метода `WriteException` формируют выходные данные журнала.</span><span class="sxs-lookup"><span data-stu-id="14fc1-139">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>

#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="14fc1-140">Запись в журнал только событий трассировки действий</span><span class="sxs-lookup"><span data-stu-id="14fc1-140">To log only activity tracing events</span></span>

1. <span data-ttu-id="14fc1-141">Щелкните правой кнопкой мыши файл app.config в **обозревателе решений** и выберите команду **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="14fc1-141">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>

     <span data-ttu-id="14fc1-142">-или-</span><span class="sxs-lookup"><span data-stu-id="14fc1-142">-or-</span></span>

     <span data-ttu-id="14fc1-143">Если файл app.config отсутствует, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="14fc1-143">If there is no app.config file:</span></span>

    1. <span data-ttu-id="14fc1-144">В меню **Проект** выберите пункт **Добавить новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="14fc1-144">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="14fc1-145">В диалоговом окне **Добавление нового элемента** выберите элемент **Файл конфигурации приложения**.</span><span class="sxs-lookup"><span data-stu-id="14fc1-145">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="14fc1-146">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="14fc1-146">Click **Add**.</span></span>

2. <span data-ttu-id="14fc1-147">Найдите раздел `<switches>` в разделе `<system.diagnostics>` раздела `<configuration>` верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="14fc1-147">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="14fc1-148">Найдите элемент, добавляющий `DefaultSwitch` в коллекцию переключателей.</span><span class="sxs-lookup"><span data-stu-id="14fc1-148">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="14fc1-149">Он должен выглядеть аналогично следующему элементу:</span><span class="sxs-lookup"><span data-stu-id="14fc1-149">It should look similar to this element:</span></span>

     `<add name="DefaultSwitch" value="Information" />`

4. <span data-ttu-id="14fc1-150">Измените значение атрибута `value` данного свойства на "ActivityTracing".</span><span class="sxs-lookup"><span data-stu-id="14fc1-150">Change the value of the `value` attribute to "ActivityTracing".</span></span>

5. <span data-ttu-id="14fc1-151">Содержимое файла app.config должно быть похоже на следующий код XML:</span><span class="sxs-lookup"><span data-stu-id="14fc1-151">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="ActivityTracing" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,
                     processorArchitecture=MSIL"
               initializeData="FileLogWriter"/>
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

6. <span data-ttu-id="14fc1-152">Запустите приложение в отладчике.</span><span class="sxs-lookup"><span data-stu-id="14fc1-152">Run the application in the debugger.</span></span>

7. <span data-ttu-id="14fc1-153">Нажмите кнопку **Button1**.</span><span class="sxs-lookup"><span data-stu-id="14fc1-153">Press **Button1**.</span></span>

     <span data-ttu-id="14fc1-154">Приложение записывает следующие сведения в файл выходных данных отладки и файл журнала приложения.</span><span class="sxs-lookup"><span data-stu-id="14fc1-154">The application writes the following information to the application's debug output and log file:</span></span>

     `DefaultSource Start: 4 : Entering Button1_Click`

     `DefaultSource Stop: 5 : Leaving Button1_Click`

8. <span data-ttu-id="14fc1-155">Закройте приложение.</span><span class="sxs-lookup"><span data-stu-id="14fc1-155">Close the application.</span></span>

9. <span data-ttu-id="14fc1-156">Измените значение атрибута `value` снова на "Информация".</span><span class="sxs-lookup"><span data-stu-id="14fc1-156">Change the value of the `value` attribute back to "Information".</span></span>

    > [!NOTE]
    > <span data-ttu-id="14fc1-157">Параметр переключателя `DefaultSwitch` контролирует только `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="14fc1-157">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="14fc1-158">На поведение классов <xref:System.Diagnostics.Trace?displayProperty=nameWithType> и <xref:System.Diagnostics.Debug?displayProperty=nameWithType> .NET он не влияет.</span><span class="sxs-lookup"><span data-stu-id="14fc1-158">It does not change how the .NET <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span></span>

## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="14fc1-159">Отдельная фильтрация прослушивателей My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="14fc1-159">Individual Filtering For My.Application.Log Listeners</span></span>

<span data-ttu-id="14fc1-160">В предыдущем примере показано, как изменить фильтрацию для всех выходных данных `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="14fc1-160">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="14fc1-161">В этом примере демонстрируется способ фильтрации отдельных прослушивателей журнала.</span><span class="sxs-lookup"><span data-stu-id="14fc1-161">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="14fc1-162">По умолчанию приложение имеет два прослушивателя, которые выполняют запись в файл выходных данных отладки и файл журнала приложения.</span><span class="sxs-lookup"><span data-stu-id="14fc1-162">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>

<span data-ttu-id="14fc1-163">Файл конфигурации управляет поведением прослушивателей журнала, разрешая каждому из них иметь фильтр, аналогичный переключателю `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="14fc1-163">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="14fc1-164">Прослушиватель журнала будет выводить сообщение только в том случае, если уровень серьезности сообщения допускается фильтром `DefaultSwitch` журнала и фильтром прослушивателя журнала.</span><span class="sxs-lookup"><span data-stu-id="14fc1-164">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>

<span data-ttu-id="14fc1-165">В этом примере демонстрируется настройка фильтрации для нового прослушивателя отладки и добавление его в объект `Log`.</span><span class="sxs-lookup"><span data-stu-id="14fc1-165">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="14fc1-166">Прослушиватель отладки по умолчанию должен быть удален из объекта `Log`, чтобы сообщения отладки поступали только из нового прослушивателя отладки.</span><span class="sxs-lookup"><span data-stu-id="14fc1-166">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>

#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="14fc1-167">Запись в журнал только событий трассировки действий</span><span class="sxs-lookup"><span data-stu-id="14fc1-167">To log only activity-tracing events</span></span>

1. <span data-ttu-id="14fc1-168">Щелкните правой кнопкой мыши файл app.config в **обозревателе решений** и выберите команду **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="14fc1-168">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="14fc1-169">\-или-</span><span class="sxs-lookup"><span data-stu-id="14fc1-169">\-or-</span></span>

     <span data-ttu-id="14fc1-170">Если файл app.config отсутствует, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="14fc1-170">If there is no app.config file:</span></span>

    1. <span data-ttu-id="14fc1-171">В меню **Проект** выберите пункт **Добавить новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="14fc1-171">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="14fc1-172">В диалоговом окне **Добавление нового элемента** выберите элемент **Файл конфигурации приложения**.</span><span class="sxs-lookup"><span data-stu-id="14fc1-172">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="14fc1-173">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="14fc1-173">Click **Add**.</span></span>

2. <span data-ttu-id="14fc1-174">Щелкните правой кнопкой мыши файл app.config в **обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="14fc1-174">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="14fc1-175">Выберите команду **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="14fc1-175">Choose **Open**.</span></span>

3. <span data-ttu-id="14fc1-176">Найдите раздел `<listeners>` в разделе `<source>` с атрибутом `name`, равным DefaultSource, в разделе `<sources>`.</span><span class="sxs-lookup"><span data-stu-id="14fc1-176">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="14fc1-177">Раздел `<sources>` находится в разделе `<system.diagnostics>` раздела `<configuration>` верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="14fc1-177">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

4. <span data-ttu-id="14fc1-178">Добавьте этот элемент в раздел `<listeners>`:</span><span class="sxs-lookup"><span data-stu-id="14fc1-178">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. <span data-ttu-id="14fc1-179">Найдите раздел `<sharedListeners>` в разделе `<system.diagnostics>` в разделе `<configuration>` верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="14fc1-179">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="14fc1-180">Добавьте в этот раздел `<sharedListeners>` следующий элемент:</span><span class="sxs-lookup"><span data-stu-id="14fc1-180">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="NewDefault"
         type="System.Diagnostics.DefaultTraceListener,
               System, Version=2.0.0.0, Culture=neutral,
               PublicKeyToken=b77a5c561934e089,
               processorArchitecture=MSIL">
        <filter type="System.Diagnostics.EventTypeFilter"
                initializeData="Error" />
    </add>
    ```

     <span data-ttu-id="14fc1-181">Фильтр <xref:System.Diagnostics.EventTypeFilter> принимает одно из значений перечисления <xref:System.Diagnostics.SourceLevels> как атрибут `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="14fc1-181">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>

7. <span data-ttu-id="14fc1-182">Содержимое файла app.config должно быть похоже на следующий код XML:</span><span class="sxs-lookup"><span data-stu-id="14fc1-182">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
              <!-- Remove the default debug listener. -->
              <remove name="Default"/>
              <!-- Add a filterable debug listener. -->
              <add name="NewDefault"/>
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="Information" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,
                     processorArchitecture=MSIL"
               initializeData="FileLogWriter"/>
          <add name="NewDefault"
               type="System.Diagnostics.DefaultTraceListener,
                     System, Version=2.0.0.0, Culture=neutral,
                     PublicKeyToken=b77a5c561934e089,
                     processorArchitecture=MSIL">
            <filter type="System.Diagnostics.EventTypeFilter"
                    initializeData="Error" />
          </add>
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

8. <span data-ttu-id="14fc1-183">Запустите приложение в отладчике.</span><span class="sxs-lookup"><span data-stu-id="14fc1-183">Run the application in the debugger.</span></span>

9. <span data-ttu-id="14fc1-184">Нажмите кнопку **Button1**.</span><span class="sxs-lookup"><span data-stu-id="14fc1-184">Press **Button1**.</span></span>

     <span data-ttu-id="14fc1-185">Приложение записывает следующие сведения в файл выходных данных приложения:</span><span class="sxs-lookup"><span data-stu-id="14fc1-185">The application writes the following information to the application's log file:</span></span>

     `Default Information: 0 : In Button1_Click`

     `Default Error: 2 : Error in the application.`

     <span data-ttu-id="14fc1-186">В связи с более ограничивающим фильтром приложение записывает меньше данных в выходные данные отладки приложения.</span><span class="sxs-lookup"><span data-stu-id="14fc1-186">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>

     `Default Error   2   Error`

10. <span data-ttu-id="14fc1-187">Закройте приложение.</span><span class="sxs-lookup"><span data-stu-id="14fc1-187">Close the application.</span></span>

<span data-ttu-id="14fc1-188">Дополнительные сведения об изменении параметров журнала после развертывания см. в разделе [Работа с журналами приложения](working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="14fc1-188">For more information about changing log settings after deployment, see [Working with Application Logs](working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="14fc1-189">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="14fc1-189">See also</span></span>

- [<span data-ttu-id="14fc1-190">Пошаговое руководство. Определение места записи сведений для My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="14fc1-190">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="14fc1-191">Пошаговое руководство. Изменение места записи сведений для My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="14fc1-191">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="14fc1-192">Пошаговое руководство. Создание пользовательских прослушивателей журнала</span><span class="sxs-lookup"><span data-stu-id="14fc1-192">Walkthrough: Creating Custom Log Listeners</span></span>](walkthrough-creating-custom-log-listeners.md)
- [<span data-ttu-id="14fc1-193">Практическое руководство. Запись сообщений в журнал</span><span class="sxs-lookup"><span data-stu-id="14fc1-193">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="14fc1-194">Переключатели трассировки</span><span class="sxs-lookup"><span data-stu-id="14fc1-194">Trace Switches</span></span>](../../../../framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="14fc1-195">Запись сведений в журнал из приложения</span><span class="sxs-lookup"><span data-stu-id="14fc1-195">Logging Information from the Application</span></span>](index.md)
