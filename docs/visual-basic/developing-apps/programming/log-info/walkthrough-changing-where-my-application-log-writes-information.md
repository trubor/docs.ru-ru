---
description: 'Подробнее о следующем: Пошаговое руководство. Изменение места записи информации для My.Application.Log (Visual Basic)'
title: Изменение места записи сведений для My.Application.Log
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: aa4e1b8ce33e2afd8dd51c68340feb3e85eb8966
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731426"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="541b5-103">Пошаговое руководство. Изменение места записи информации для My.Application.Log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="541b5-103">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="541b5-104">Объекты `My.Application.Log` и `My.Log` можно использовать для записи в журнал информации о событиях, происходящих в приложении.</span><span class="sxs-lookup"><span data-stu-id="541b5-104">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="541b5-105">В этом пошаговом руководстве показано, как переопределить параметры по умолчанию и настроить объект `Log` на запись в другие прослушиватели журналов.</span><span class="sxs-lookup"><span data-stu-id="541b5-105">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="541b5-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="541b5-106">Prerequisites</span></span>

<span data-ttu-id="541b5-107">Объект `Log` может записывать информацию в несколько прослушивателей журналов.</span><span class="sxs-lookup"><span data-stu-id="541b5-107">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="541b5-108">Перед изменением конфигурации необходимо определить текущую конфигурацию прослушивателей журналов.</span><span class="sxs-lookup"><span data-stu-id="541b5-108">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="541b5-109">Дополнительные сведения см. в разделе [Пошаговое руководство. Определение места записи информации для My.Application.Log](walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="541b5-109">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

<span data-ttu-id="541b5-110">Также см. разделы [Практическое руководство. Запись сведений о событиях в текстовый файл](how-to-write-event-information-to-a-text-file.md) и [Практическое руководство. Запись в журнал событий приложения](how-to-write-to-an-application-event-log.md).</span><span class="sxs-lookup"><span data-stu-id="541b5-110">You may want to review [How to: Write Event Information to a Text File](how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](how-to-write-to-an-application-event-log.md).</span></span>

### <a name="to-add-listeners"></a><span data-ttu-id="541b5-111">Добавление прослушивателей</span><span class="sxs-lookup"><span data-stu-id="541b5-111">To add listeners</span></span>

1. <span data-ttu-id="541b5-112">Щелкните правой кнопкой мыши файл app.config в **обозревателе решений** и выберите команду **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="541b5-112">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="541b5-113">\- или -</span><span class="sxs-lookup"><span data-stu-id="541b5-113">\- or -</span></span>

     <span data-ttu-id="541b5-114">Если файл app.config отсутствует, выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="541b5-114">If there is no app.config file:</span></span>

    1. <span data-ttu-id="541b5-115">В меню **Проект** выберите пункт **Добавить новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="541b5-115">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="541b5-116">В диалоговом окне **Добавление нового элемента** выберите элемент **Файл конфигурации приложения**.</span><span class="sxs-lookup"><span data-stu-id="541b5-116">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>

    3. <span data-ttu-id="541b5-117">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="541b5-117">Click **Add**.</span></span>

2. <span data-ttu-id="541b5-118">Найдите раздел `<listeners>` в разделе `<source>` с атрибутом `name` , равным DefaultSource, в разделе `<sources>` .</span><span class="sxs-lookup"><span data-stu-id="541b5-118">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="541b5-119">Раздел `<sources>` находится в разделе `<system.diagnostics>` в разделе `<configuration>` верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="541b5-119">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="541b5-120">Добавьте в этот раздел `<listeners>` следующие элементы.</span><span class="sxs-lookup"><span data-stu-id="541b5-120">Add these elements to that `<listeners>` section.</span></span>

    ```xml
    <!-- Uncomment to connect the application file log. -->
    <!-- <add name="FileLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="EventLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="Delimited" /> -->
    <!-- Uncomment to connect the XML log. -->
    <!-- <add name="XmlWriter" /> -->
    <!-- Uncomment to connect the console log. -->
    <!-- <add name="Console" /> -->
    ```

4. <span data-ttu-id="541b5-121">Раскомментируйте прослушиватели журналов, которые должны получать сообщения `Log` .</span><span class="sxs-lookup"><span data-stu-id="541b5-121">Uncomment the log listeners that you want to receive `Log` messages.</span></span>

5. <span data-ttu-id="541b5-122">Найдите раздел `<sharedListeners>` в разделе `<system.diagnostics>` в разделе `<configuration>` верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="541b5-122">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="541b5-123">Добавьте в этот раздел `<sharedListeners>` следующие элементы.</span><span class="sxs-lookup"><span data-stu-id="541b5-123">Add these elements to that `<sharedListeners>` section.</span></span>

    ```xml
    <add name="FileLog"
         type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
               Microsoft.VisualBasic, Version=8.0.0.0,
               Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
         initializeData="FileLogWriter" />
    <add name="EventLog"
         type="System.Diagnostics.EventLogTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="sample application"/>
    <add name="Delimited"
         type="System.Diagnostics.DelimitedListTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleDelimitedFile.txt"
         traceOutputOptions="DateTime" />
    <add name="XmlWriter"
         type="System.Diagnostics.XmlWriterTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleLogFile.xml" />
    <add name="Console"
         type="System.Diagnostics.ConsoleTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="true" />
    ```

7. <span data-ttu-id="541b5-124">Содержимое файла app.config должно быть похоже на следующий код XML:</span><span class="sxs-lookup"><span data-stu-id="541b5-124">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
              <!-- Uncomment to connect the application file log. -->
              <!-- <add name="FileLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="EventLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="Delimited" /> -->
              <!-- Uncomment to connect the XML log. -->
              <!-- <add name="XmlWriter" /> -->
              <!-- Uncomment to connect the console log. -->
              <!-- <add name="Console" /> -->
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
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
               initializeData="FileLogWriter" />
          <add name="EventLog"
               type="System.Diagnostics.EventLogTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="sample application"/>
          <add name="Delimited"
               type="System.Diagnostics.DelimitedListTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleDelimitedFile.txt"
               traceOutputOptions="DateTime" />
          <add name="XmlWriter"
               type="System.Diagnostics.XmlWriterTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleLogFile.xml" />
          <add name="Console"
               type="System.Diagnostics.ConsoleTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="true" />
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="541b5-125">Перенастройка прослушивателя</span><span class="sxs-lookup"><span data-stu-id="541b5-125">To reconfigure a listener</span></span>

1. <span data-ttu-id="541b5-126">Найдите элемент `<add>` прослушивателя из раздела `<sharedListeners>` .</span><span class="sxs-lookup"><span data-stu-id="541b5-126">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>

2. <span data-ttu-id="541b5-127">Атрибут `type` содержит имя типа прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="541b5-127">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="541b5-128">Этот тип должен наследоваться от класса <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="541b5-128">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="541b5-129">Используйте строгое имя типа, чтобы гарантировать, что используется верный тип.</span><span class="sxs-lookup"><span data-stu-id="541b5-129">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="541b5-130">Дополнительные сведения см. в разделе "Создание ссылки на строго именованный тип" ниже.</span><span class="sxs-lookup"><span data-stu-id="541b5-130">For more information, see the "To reference a strongly named type" section below.</span></span>

     <span data-ttu-id="541b5-131">Вот некоторые типы, которые можно использовать:</span><span class="sxs-lookup"><span data-stu-id="541b5-131">Some types that you can use are:</span></span>

    - <span data-ttu-id="541b5-132">прослушиватель <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> , ведущий запись в журнал файлов;</span><span class="sxs-lookup"><span data-stu-id="541b5-132">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>

    - <span data-ttu-id="541b5-133">прослушиватель <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> , записывающий информацию в журнал событий компьютера, заданный параметром `initializeData` ;</span><span class="sxs-lookup"><span data-stu-id="541b5-133">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>

    - <span data-ttu-id="541b5-134">прослушиватели <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> и <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> , ведущие запись в файл, указанный в параметре `initializeData` ;</span><span class="sxs-lookup"><span data-stu-id="541b5-134">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="541b5-135">прослушиватель <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> , ведущий запись в консоль командной строки.</span><span class="sxs-lookup"><span data-stu-id="541b5-135">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>

     <span data-ttu-id="541b5-136">Сведения о том, куда записывают информацию другие типы прослушивателей журналов, приведены в документации по этим типам.</span><span class="sxs-lookup"><span data-stu-id="541b5-136">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

3. <span data-ttu-id="541b5-137">Когда приложение создает объект прослушивателя журнала, оно передает атрибут `initializeData` в качестве параметра конструктора.</span><span class="sxs-lookup"><span data-stu-id="541b5-137">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="541b5-138">Значение атрибута `initializeData` зависит от прослушивателя трассировки.</span><span class="sxs-lookup"><span data-stu-id="541b5-138">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>

4. <span data-ttu-id="541b5-139">После создания прослушивателя журнала приложение задает его свойства.</span><span class="sxs-lookup"><span data-stu-id="541b5-139">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="541b5-140">Эти свойства определяются другими атрибутами в элементе `<add>` .</span><span class="sxs-lookup"><span data-stu-id="541b5-140">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="541b5-141">Дополнительные сведения о свойствах конкретного прослушивателя см. в документации к соответствующему типу прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="541b5-141">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>

### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="541b5-142">Создание ссылки на строго именованный тип</span><span class="sxs-lookup"><span data-stu-id="541b5-142">To reference a strongly named type</span></span>

1. <span data-ttu-id="541b5-143">Чтобы гарантировать, что для прослушивателя журнала используется правильный тип, убедитесь в том, что используется полное имя типа и строгое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="541b5-143">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="541b5-144">Синтаксис строго именованного типа выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="541b5-144">The syntax of a strongly named type is as follows:</span></span>

     <span data-ttu-id="541b5-145">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span><span class="sxs-lookup"><span data-stu-id="541b5-145">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>

2. <span data-ttu-id="541b5-146">В этом примере кода показано, как определить строгое имя для типа с полным именем System.Diagnostics.FileLogTraceListener.</span><span class="sxs-lookup"><span data-stu-id="541b5-146">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     <span data-ttu-id="541b5-147">Это выходные данные, и они могут использоваться для уникальной ссылки на строго именованный тип, как показано выше в процедуре "Добавление прослушивателей".</span><span class="sxs-lookup"><span data-stu-id="541b5-147">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a><span data-ttu-id="541b5-148">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="541b5-148">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [<span data-ttu-id="541b5-149">Практическое руководство. Запись сведений о событиях в текстовый файл</span><span class="sxs-lookup"><span data-stu-id="541b5-149">How to: Write Event Information to a Text File</span></span>](how-to-write-event-information-to-a-text-file.md)
- [<span data-ttu-id="541b5-150">Практическое руководство. Запись в журнал событий приложения</span><span class="sxs-lookup"><span data-stu-id="541b5-150">How to: Write to an Application Event Log</span></span>](how-to-write-to-an-application-event-log.md)
