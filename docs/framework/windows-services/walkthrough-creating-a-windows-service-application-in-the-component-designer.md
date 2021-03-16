---
title: Учебник. Создание приложения службы Windows
description: Из этого учебника вы узнаете, как создать в Visual Studio приложение службы Windows, которое записывает сообщения в журнал событий. Добавляйте компоненты, задавайте состояние, добавляйте установщики и выполняйте другие действия.
ms.date: 03/27/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
ms.openlocfilehash: b6e4937b71c50f887a7eb784bc9106360a05fdc2
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259802"
---
# <a name="tutorial-create-a-windows-service-app"></a><span data-ttu-id="daf94-104">Учебник. Создание приложения службы Windows</span><span class="sxs-lookup"><span data-stu-id="daf94-104">Tutorial: Create a Windows service app</span></span>

<span data-ttu-id="daf94-105">Из этой статьи вы узнаете, как создать в Visual Studio приложение службы Windows, которое записывает сообщения в журнал событий.</span><span class="sxs-lookup"><span data-stu-id="daf94-105">This article demonstrates how to create a Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="daf94-106">Создание службы</span><span class="sxs-lookup"><span data-stu-id="daf94-106">Create a service</span></span>

<span data-ttu-id="daf94-107">Для начала создайте проект и настройте значения, необходимые для правильной работы службы.</span><span class="sxs-lookup"><span data-stu-id="daf94-107">To begin, create the project and set the values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="daf94-108">В Visual Studio в меню **Файл** последовательно выберите пункты **Создать** > **Проект** (или нажмите клавиши **CTRL**+**SHIFT**+**N**), чтобы открыть окно **Новый проект**.</span><span class="sxs-lookup"><span data-stu-id="daf94-108">From the Visual Studio **File** menu, select **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** window.</span></span>

2. <span data-ttu-id="daf94-109">Найдите и выберите шаблон проекта **Служба Windows (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="daf94-109">Navigate to and select the **Windows Service (.NET Framework)** project template.</span></span> <span data-ttu-id="daf94-110">Чтобы найти его, разверните узел **Установленные**, затем узел **Visual C#** или **Visual Basic** и выберите **Рабочий стол Windows**.</span><span class="sxs-lookup"><span data-stu-id="daf94-110">To find it, expand **Installed** and **Visual C#** or **Visual Basic**, then select **Windows Desktop**.</span></span> <span data-ttu-id="daf94-111">Можно также ввести запрос *Служба Windows* в поле поиска в правом верхнем углу и нажать клавишу **ВВОД**.</span><span class="sxs-lookup"><span data-stu-id="daf94-111">Or, enter *Windows Service* in the search box on the upper right and press **Enter**.</span></span>

   ![Шаблон приложения Windows в диалоговом окне нового проекта Visual Studio](./media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="daf94-113">Если вы не видите здесь шаблон **Служба Windows**, попробуйте установить рабочую нагрузку **Разработка классических приложений .NET**.</span><span class="sxs-lookup"><span data-stu-id="daf94-113">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload:</span></span>
   >
   > <span data-ttu-id="daf94-114">В диалоговом окне **Новый проект** выберите ссылку **Открыть установщик Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="daf94-114">In the **New Project** dialog, select **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="daf94-115">Выберите рабочую нагрузку **Разработка классических приложений .NET** и нажмите кнопку **Изменить**.</span><span class="sxs-lookup"><span data-stu-id="daf94-115">Select the **.NET desktop development** workload, and then select **Modify**.</span></span>

3. <span data-ttu-id="daf94-116">В поле **Имя** введите *MyNewService*, а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="daf94-116">For **Name**, enter *MyNewService*, and then select **OK**.</span></span>

   <span data-ttu-id="daf94-117">Откроется вкладка **Проект** (**Service1.cs [Проект]** или **Service1.vb [Проект]** ).</span><span class="sxs-lookup"><span data-stu-id="daf94-117">The **Design** tab appears (**Service1.cs [Design]** or **Service1.vb [Design]**).</span></span>

   <span data-ttu-id="daf94-118">Этот шаблон проекта содержит класс компонента с именем `Service1`, наследуемый от <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="daf94-118">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="daf94-119">В нем собран основной служебный код, в том числе код для запуска службы.</span><span class="sxs-lookup"><span data-stu-id="daf94-119">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="daf94-120">Переименование службы</span><span class="sxs-lookup"><span data-stu-id="daf94-120">Rename the service</span></span>

<span data-ttu-id="daf94-121">Измените имя службы с **Service1** на **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="daf94-121">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="daf94-122">В **обозревателе решений** выберите файл **Service1.cs** или **Service1.vb**, а затем выберите в контекстном меню команду **Переименовать**.</span><span class="sxs-lookup"><span data-stu-id="daf94-122">In **Solution Explorer**, select **Service1.cs**, or **Service1.vb**, and choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="daf94-123">Переименуйте файл в **MyNewService.cs** или **MyNewService.vb** и нажмите клавишу **ВВОД**.</span><span class="sxs-lookup"><span data-stu-id="daf94-123">Rename the file to **MyNewService.cs**, or **MyNewService.vb**, and then press **Enter**</span></span>

    <span data-ttu-id="daf94-124">Появится всплывающее окно, предлагающее переименовать все ссылки на элемент кода *Service1*.</span><span class="sxs-lookup"><span data-stu-id="daf94-124">A pop-up window appears asking whether you would like to rename all references to the code element *Service1*.</span></span>

2. <span data-ttu-id="daf94-125">Выберите **Да**.</span><span class="sxs-lookup"><span data-stu-id="daf94-125">In the pop-up window, select **Yes**.</span></span>

    <span data-ttu-id="daf94-126">![Запрос на переименование](./media/windows-service-rename.png "Запрос на переименование службы Windows")</span><span class="sxs-lookup"><span data-stu-id="daf94-126">![Rename prompt](./media/windows-service-rename.png "Windows service rename prompt")</span></span>

3. <span data-ttu-id="daf94-127">На вкладке **Проект** выберите в контекстном меню пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="daf94-127">In the **Design** tab, select **Properties** from the shortcut menu.</span></span> <span data-ttu-id="daf94-128">В окне **Свойства** измените значение **ServiceName** на *MyNewService*.</span><span class="sxs-lookup"><span data-stu-id="daf94-128">From the **Properties** window, change the **ServiceName** value to *MyNewService*.</span></span>

    <span data-ttu-id="daf94-129">![Свойства службы](./media/windows-service-properties.png "Свойства службы Windows")</span><span class="sxs-lookup"><span data-stu-id="daf94-129">![Service properties](./media/windows-service-properties.png "Windows service properties")</span></span>

4. <span data-ttu-id="daf94-130">В меню **Файл** выберите команду **Сохранить все**.</span><span class="sxs-lookup"><span data-stu-id="daf94-130">Select **Save All** from the **File** menu.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="daf94-131">Добавление компонентов в службу</span><span class="sxs-lookup"><span data-stu-id="daf94-131">Add features to the service</span></span>

<span data-ttu-id="daf94-132">В этом разделе к службе Windows будет добавлен настраиваемый журнал событий.</span><span class="sxs-lookup"><span data-stu-id="daf94-132">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="daf94-133">Компонент <xref:System.Diagnostics.EventLog> — это пример типа компонента, который можно добавить в службу Windows.</span><span class="sxs-lookup"><span data-stu-id="daf94-133">The <xref:System.Diagnostics.EventLog> component is an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="daf94-134">Добавление возможности работы с настраиваемым журналом событий</span><span class="sxs-lookup"><span data-stu-id="daf94-134">Add custom event log functionality</span></span>

1. <span data-ttu-id="daf94-135">В **обозревателе решений** в контекстном меню для файла **MyNewService.cs** или **MyNewService.vb** выберите пункт **Показать конструктор**.</span><span class="sxs-lookup"><span data-stu-id="daf94-135">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="daf94-136">На **панели элементов** разверните раздел **Компоненты** и перетащите компонент **EventLog** на вкладку **Service1.cs [Проект]** или **Service1.vb [Проект]** .</span><span class="sxs-lookup"><span data-stu-id="daf94-136">In **Toolbox**, expand **Components**, and then drag the **EventLog** component to the **Service1.cs [Design]**, or **Service1.vb [Design]** tab.</span></span>

3. <span data-ttu-id="daf94-137">В **обозревателе решений** в контекстном меню для файла **MyNewService.cs** или **MyNewService.vb** выберите пункт **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="daf94-137">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Code**.</span></span>

4. <span data-ttu-id="daf94-138">Определите пользовательский журнал событий.</span><span class="sxs-lookup"><span data-stu-id="daf94-138">Define a custom event log.</span></span> <span data-ttu-id="daf94-139">Для C# измените существующий конструктор `MyNewService()`. Для Visual Basic добавьте конструктор `New()`.</span><span class="sxs-lookup"><span data-stu-id="daf94-139">For C#, edit the existing `MyNewService()` constructor; for Visual Basic, add the `New()` constructor:</span></span>

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. <span data-ttu-id="daf94-140">Добавьте оператор `using` в файл **MyNewService.cs** (если его еще нет) или оператор `Imports` в файл **MyNewService.vb** для пространства имен <xref:System.Diagnostics?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="daf94-140">Add a `using` statement to **MyNewService.cs** (if it doesn't already exist), or an `Imports` statement **MyNewService.vb**, for the <xref:System.Diagnostics?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. <span data-ttu-id="daf94-141">В меню **Файл** выберите команду **Сохранить все**.</span><span class="sxs-lookup"><span data-stu-id="daf94-141">Select **Save All** from the **File** menu.</span></span>

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="daf94-142">Определение действий при запуске службы</span><span class="sxs-lookup"><span data-stu-id="daf94-142">Define what occurs when the service starts</span></span>

<span data-ttu-id="daf94-143">В редакторе кода для файла **MyNewService.cs** или **MyNewService.vb** найдите метод <xref:System.ServiceProcess.ServiceBase.OnStart%2A>. Пустое определение метода было автоматически добавлено при создании проекта в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="daf94-143">In the code editor for **MyNewService.cs** or **MyNewService.vb**, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method; Visual Studio automatically created an empty method definition when you created the project.</span></span> <span data-ttu-id="daf94-144">Добавьте код, с помощью которой запись сохраняется в журнале событий при запуске службы:</span><span class="sxs-lookup"><span data-stu-id="daf94-144">Add code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a><span data-ttu-id="daf94-145">Опрос</span><span class="sxs-lookup"><span data-stu-id="daf94-145">Polling</span></span>

<span data-ttu-id="daf94-146">Так как приложение службы предполагает длительное время выполнения, оно обычно опрашивает или отслеживает систему. Отслеживание настраивается в методе <xref:System.ServiceProcess.ServiceBase.OnStart%2A>.</span><span class="sxs-lookup"><span data-stu-id="daf94-146">Because a service application is designed to be long-running, it usually polls or monitors the system, which you set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="daf94-147">После начала работы службы метод `OnStart` должен возвращать управление операционной системе, чтобы она не блокировалась.</span><span class="sxs-lookup"><span data-stu-id="daf94-147">The `OnStart` method must return to the operating system after the service's operation has begun so that the system isn't blocked.</span></span>

<span data-ttu-id="daf94-148">Для создания простого механизма опроса используйте компонент <xref:System.Timers.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="daf94-148">To set up a simple polling mechanism, use the <xref:System.Timers.Timer?displayProperty=nameWithType> component.</span></span> <span data-ttu-id="daf94-149">Таймер через определенные интервалы времени генерирует событие <xref:System.Timers.Timer.Elapsed>, при возникновении которых служба может выполнять отслеживание.</span><span class="sxs-lookup"><span data-stu-id="daf94-149">The timer raises an <xref:System.Timers.Timer.Elapsed> event at regular intervals, at which time your service can do its monitoring.</span></span> <span data-ttu-id="daf94-150">Компонент <xref:System.Timers.Timer> используется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="daf94-150">You use the <xref:System.Timers.Timer> component as follows:</span></span>

- <span data-ttu-id="daf94-151">Задайте свойства компонента <xref:System.Timers.Timer> в методе `MyNewService.OnStart`.</span><span class="sxs-lookup"><span data-stu-id="daf94-151">Set the properties of the <xref:System.Timers.Timer> component in the `MyNewService.OnStart` method.</span></span>
- <span data-ttu-id="daf94-152">Запустите таймер, вызвав метод <xref:System.Timers.Timer.Start%2A>.</span><span class="sxs-lookup"><span data-stu-id="daf94-152">Start the timer by calling the <xref:System.Timers.Timer.Start%2A> method.</span></span>

##### <a name="set-up-the-polling-mechanism"></a><span data-ttu-id="daf94-153">Настройка механизма опроса.</span><span class="sxs-lookup"><span data-stu-id="daf94-153">Set up the polling mechanism.</span></span>

1. <span data-ttu-id="daf94-154">Чтобы настроить механизм опроса, добавьте следующий код в событие `MyNewService.OnStart`:</span><span class="sxs-lookup"><span data-stu-id="daf94-154">Add the following code in the `MyNewService.OnStart` event to set up the polling mechanism:</span></span>

   ```csharp
   // Set up a timer that triggers every minute.
   Timer timer = new Timer();
   timer.Interval = 60000; // 60 seconds
   timer.Elapsed += new ElapsedEventHandler(this.OnTimer);
   timer.Start();
   ```

   ```vb
   ' Set up a timer that triggers every minute.
   Dim timer As Timer = New Timer()
   timer.Interval = 60000 ' 60 seconds
   AddHandler timer.Elapsed, AddressOf Me.OnTimer
   timer.Start()
   ```

2. <span data-ttu-id="daf94-155">Добавьте оператор `using` в файл **MyNewService.cs** или оператор `Imports` в файл **MyNewService.vb** для пространства имен <xref:System.Timers?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="daf94-155">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Timers?displayProperty=nameWithType> namespace:</span></span>

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. <span data-ttu-id="daf94-156">В классе `MyNewService` добавьте метод `OnTimer` для обработки события <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="daf94-156">In the `MyNewService` class, add the `OnTimer` method to handle the <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType> event:</span></span>

   ```csharp
   public void OnTimer(object sender, ElapsedEventArgs args)
   {
       // TODO: Insert monitoring activities here.
       eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId++);
   }
   ```

   ```vb
   Private Sub OnTimer(sender As Object, e As Timers.ElapsedEventArgs)
      ' TODO: Insert monitoring activities here.
      eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId)
      eventId = eventId + 1
   End Sub
   ```

4. <span data-ttu-id="daf94-157">В класс `MyNewService` добавьте переменную-член.</span><span class="sxs-lookup"><span data-stu-id="daf94-157">In the `MyNewService` class, add a member variable.</span></span> <span data-ttu-id="daf94-158">Она содержит идентификатор следующего события, которое сохраняется в журнале событий.</span><span class="sxs-lookup"><span data-stu-id="daf94-158">It contains the identifier of the next event to write into the event log:</span></span>

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

<span data-ttu-id="daf94-159">Задачи можно выполнять с помощью фоновых рабочих потоков, а не выполнять всю работу в основном потоке.</span><span class="sxs-lookup"><span data-stu-id="daf94-159">Instead of running all your work on the main thread, you can run tasks by using background worker threads.</span></span> <span data-ttu-id="daf94-160">Для получения дополнительной информации см. <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="daf94-160">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="daf94-161">Определение действий при остановке службы</span><span class="sxs-lookup"><span data-stu-id="daf94-161">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="daf94-162">Вставьте в метод <xref:System.ServiceProcess.ServiceBase.OnStop%2A> строку кода, с помощью которой запись сохраняется в журнале событий при остановке службы:</span><span class="sxs-lookup"><span data-stu-id="daf94-162">Insert a line of code in the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="daf94-163">Определение других действий для службы</span><span class="sxs-lookup"><span data-stu-id="daf94-163">Define other actions for the service</span></span>

<span data-ttu-id="daf94-164">Вы можете переопределить методы <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> и <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>, добавив дополнительные процессы обработки.</span><span class="sxs-lookup"><span data-stu-id="daf94-164">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span>

<span data-ttu-id="daf94-165">Следующий код показывает, как можно переопределить метод <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> в классе `MyNewService`:</span><span class="sxs-lookup"><span data-stu-id="daf94-165">The following code shows how you to override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method in the `MyNewService` class:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a><span data-ttu-id="daf94-166">Установка состояния службы</span><span class="sxs-lookup"><span data-stu-id="daf94-166">Set service status</span></span>

<span data-ttu-id="daf94-167">Службы сообщают о своем состоянии [диспетчеру служб](/windows/desktop/Services/service-control-manager), чтобы пользователь мог определить, работает ли служба правильно.</span><span class="sxs-lookup"><span data-stu-id="daf94-167">Services report their status to the [Service Control Manager](/windows/desktop/Services/service-control-manager) so that a user can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="daf94-168">По умолчанию служба, которая наследуется от <xref:System.ServiceProcess.ServiceBase>, сообщает ограниченный набор состояний, включая SERVICE_STOPPED, SERVICE_PAUSED и SERVICE_RUNNING.</span><span class="sxs-lookup"><span data-stu-id="daf94-168">By default, a service that inherits from <xref:System.ServiceProcess.ServiceBase> reports a limited set of status settings, which include SERVICE_STOPPED, SERVICE_PAUSED, and SERVICE_RUNNING.</span></span> <span data-ttu-id="daf94-169">Если служба запускается не сразу, полезно обеспечить сообщение состояния SERVICE_START_PENDING.</span><span class="sxs-lookup"><span data-stu-id="daf94-169">If a service takes a while to start up, it's useful to report a SERVICE_START_PENDING status.</span></span>

<span data-ttu-id="daf94-170">Состояния ERVICE_START_PENDING и SERVICE_STOP_PENDING можно реализовать путем добавления кода, вызывающего функцию Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).</span><span class="sxs-lookup"><span data-stu-id="daf94-170">You can implement the SERVICE_START_PENDING and SERVICE_STOP_PENDING status settings by adding code that calls the Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function.</span></span>

### <a name="implement-service-pending-status"></a><span data-ttu-id="daf94-171">Реализация состояния ожидания службы</span><span class="sxs-lookup"><span data-stu-id="daf94-171">Implement service pending status</span></span>

1. <span data-ttu-id="daf94-172">Добавьте оператор `using` в файл **MyNewService.cs** или оператор `Imports` в файл **MyNewService.vb** для пространства имен <xref:System.Runtime.InteropServices?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="daf94-172">Add a `using` statement to **MyNewService.cs**, or an `Imports` statement to **MyNewService.vb**, for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="daf94-173">Добавьте следующий код в файл **MyNewService.cs** или **MyNewService.vb** для объявления значений `ServiceState` и добавления структуры для состояния, которая будет использоваться при вызове неуправляемого кода:</span><span class="sxs-lookup"><span data-stu-id="daf94-173">Add the following code to **MyNewService.cs**, or **MyNewService.vb**, to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

    ```csharp
    public enum ServiceState
    {
        SERVICE_STOPPED = 0x00000001,
        SERVICE_START_PENDING = 0x00000002,
        SERVICE_STOP_PENDING = 0x00000003,
        SERVICE_RUNNING = 0x00000004,
        SERVICE_CONTINUE_PENDING = 0x00000005,
        SERVICE_PAUSE_PENDING = 0x00000006,
        SERVICE_PAUSED = 0x00000007,
    }

    [StructLayout(LayoutKind.Sequential)]
    public struct ServiceStatus
    {
        public int dwServiceType;
        public ServiceState dwCurrentState;
        public int dwControlsAccepted;
        public int dwWin32ExitCode;
        public int dwServiceSpecificExitCode;
        public int dwCheckPoint;
        public int dwWaitHint;
    };
    ```

    ```vb
    Public Enum ServiceState
        SERVICE_STOPPED = 1
        SERVICE_START_PENDING = 2
        SERVICE_STOP_PENDING = 3
        SERVICE_RUNNING = 4
        SERVICE_CONTINUE_PENDING = 5
        SERVICE_PAUSE_PENDING = 6
        SERVICE_PAUSED = 7
    End Enum

    <StructLayout(LayoutKind.Sequential)>
    Public Structure ServiceStatus
        Public dwServiceType As Long
        Public dwCurrentState As ServiceState
        Public dwControlsAccepted As Long
        Public dwWin32ExitCode As Long
        Public dwServiceSpecificExitCode As Long
        Public dwCheckPoint As Long
        Public dwWaitHint As Long
    End Structure
    ```

    > [!NOTE]
    > <span data-ttu-id="daf94-174">Диспетчер служб использует члены `dwWaitHint` и `dwCheckpoint`[структуры SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status), чтобы определить время, в течение которого нужно ожидать запуска или завершения работы службы Windows.</span><span class="sxs-lookup"><span data-stu-id="daf94-174">The Service Control Manager uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/win32/api/winsvc/ns-winsvc-service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="daf94-175">Если методы `OnStart` и `OnStop` выполняются долго, служба может запросить больше времени, повторно вызвав функцию `SetServiceStatus` с увеличенным значением `dwCheckPoint`.</span><span class="sxs-lookup"><span data-stu-id="daf94-175">If your `OnStart` and `OnStop` methods run long, your service can request more time by calling `SetServiceStatus` again with an incremented `dwCheckPoint` value.</span></span>

3. <span data-ttu-id="daf94-176">В классе `MyNewService` объявите функцию [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) с помощью [вызова неуправляемого кода](../interop/consuming-unmanaged-dll-functions.md):</span><span class="sxs-lookup"><span data-stu-id="daf94-176">In the `MyNewService` class, declare the [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) function by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="daf94-177">Для реализации состояния SERVICE_START_PENDING добавьте следующий код в начало метода <xref:System.ServiceProcess.ServiceBase.OnStart%2A>:</span><span class="sxs-lookup"><span data-stu-id="daf94-177">To implement the SERVICE_START_PENDING status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

    ```csharp
    // Update the service state to Start Pending.
    ServiceStatus serviceStatus = new ServiceStatus();
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING;
    serviceStatus.dwWaitHint = 100000;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Start Pending.
    Dim serviceStatus As ServiceStatus = New ServiceStatus()
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING
    serviceStatus.dwWaitHint = 100000
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

5. <span data-ttu-id="daf94-178">Для установки состояния SERVICE_RUNNING добавьте код в конце метода `OnStart`:</span><span class="sxs-lookup"><span data-stu-id="daf94-178">Add code to the end of the `OnStart` method to set the status to SERVICE_RUNNING:</span></span>

    ```csharp
    // Update the service state to Running.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Running.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

6. <span data-ttu-id="daf94-179">Если метод <xref:System.ServiceProcess.ServiceBase.OnStop%2A> выполняется долго, повторите данную процедуру для `OnStop` (необязательно).</span><span class="sxs-lookup"><span data-stu-id="daf94-179">(Optional) If <xref:System.ServiceProcess.ServiceBase.OnStop%2A> is a long-running method, repeat this procedure in the `OnStop` method.</span></span> <span data-ttu-id="daf94-180">Реализуйте состояние SERVICE_STOP_PENDING и обеспечьте возврат состояния SERVICE_STOPPED до того, как метод `OnStop` вернет управление.</span><span class="sxs-lookup"><span data-stu-id="daf94-180">Implement the SERVICE_STOP_PENDING status and return the SERVICE_STOPPED status before the `OnStop` method exits.</span></span>

   <span data-ttu-id="daf94-181">Пример:</span><span class="sxs-lookup"><span data-stu-id="daf94-181">For example:</span></span>

    ```csharp
    // Update the service state to Stop Pending.
    ServiceStatus serviceStatus = new ServiceStatus();
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING;
    serviceStatus.dwWaitHint = 100000;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);

    // Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Stop Pending.
    Dim serviceStatus As ServiceStatus = New ServiceStatus()
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOP_PENDING
    serviceStatus.dwWaitHint = 100000
    SetServiceStatus(Me.ServiceHandle, serviceStatus)

    ' Update the service state to Stopped.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_STOPPED
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

## <a name="add-installers-to-the-service"></a><span data-ttu-id="daf94-182">Добавление установщиков в службу</span><span class="sxs-lookup"><span data-stu-id="daf94-182">Add installers to the service</span></span>

<span data-ttu-id="daf94-183">Перед тем как запускать службу Windows, ее нужно установить. При этом она регистрируется в диспетчере служб.</span><span class="sxs-lookup"><span data-stu-id="daf94-183">Before you run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="daf94-184">В проект можно добавить установщики, которые обрабатывают сведения о регистрации.</span><span class="sxs-lookup"><span data-stu-id="daf94-184">Add installers to your project to handle the registration details.</span></span>

1. <span data-ttu-id="daf94-185">В **обозревателе решений** в контекстном меню для файла **MyNewService.cs** или **MyNewService.vb** выберите пункт **Показать конструктор**.</span><span class="sxs-lookup"><span data-stu-id="daf94-185">In **Solution Explorer**, from the shortcut menu for **MyNewService.cs**, or **MyNewService.vb**, choose **View Designer**.</span></span>

2. <span data-ttu-id="daf94-186">В представлении **Конструктор** щелкните область фона правой кнопкой мыши и выберите в контекстном меню команду **Добавить установщик**.</span><span class="sxs-lookup"><span data-stu-id="daf94-186">In the **Design** view, select the background area, then choose **Add Installer** from the shortcut menu.</span></span>

     <span data-ttu-id="daf94-187">По умолчанию Visual Studio добавляет в проект класс компонента `ProjectInstaller`, содержащий два установщика.</span><span class="sxs-lookup"><span data-stu-id="daf94-187">By default, Visual Studio adds a component class named `ProjectInstaller`, which contains two installers, to your project.</span></span> <span data-ttu-id="daf94-188">Они предназначены для установки службы и связанного со службой процесса.</span><span class="sxs-lookup"><span data-stu-id="daf94-188">These installers are for your service and for the service's associated process.</span></span>

3. <span data-ttu-id="daf94-189">В представлении **Конструктор** для **ProjectInstaller** выберите **serviceInstaller1** для проекта Visual C# или **ServiceInstaller1** для проекта Visual Basic. Затем в контекстном меню выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="daf94-189">In the **Design** view for **ProjectInstaller**, select **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="daf94-190">Убедитесь в том, что в окне **Свойства** свойство <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> имеет значение **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="daf94-190">In the **Properties** window, verify the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

5. <span data-ttu-id="daf94-191">Введите для свойства <xref:System.ServiceProcess.ServiceInstaller.Description%2A> какой нибудь текст, например *Пример службы*.</span><span class="sxs-lookup"><span data-stu-id="daf94-191">Add text to the <xref:System.ServiceProcess.ServiceInstaller.Description%2A> property, such as *A sample service*.</span></span>

     <span data-ttu-id="daf94-192">Этот текст отображается в столбце **Описание** в окне **Службы** и помогает пользователю понять, для чего служба нужна.</span><span class="sxs-lookup"><span data-stu-id="daf94-192">This text appears in the **Description** column of the **Services** window and describes the service to the user.</span></span>

    <span data-ttu-id="daf94-193">![Описание службы в окне "Службы".](./media/windows-service-description.png "Описание службы")</span><span class="sxs-lookup"><span data-stu-id="daf94-193">![Service description in the Services window.](./media/windows-service-description.png "Service description")</span></span>

6. <span data-ttu-id="daf94-194">Введите текст для свойства <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A>,</span><span class="sxs-lookup"><span data-stu-id="daf94-194">Add text to the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property.</span></span> <span data-ttu-id="daf94-195">например *Отображаемое имя MyNewService*.</span><span class="sxs-lookup"><span data-stu-id="daf94-195">For example, *MyNewService Display Name*.</span></span>

     <span data-ttu-id="daf94-196">Этот текст отображается в столбце **Отображаемое имя** в окне **Службы**.</span><span class="sxs-lookup"><span data-stu-id="daf94-196">This text appears in the **Display Name** column of the **Services** window.</span></span> <span data-ttu-id="daf94-197">Это имя может отличаться от значения свойства <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>, которое представляет собой имя, используемое в системе (например, когда вы запускаете службу с помощью команды `net start`).</span><span class="sxs-lookup"><span data-stu-id="daf94-197">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name the system uses (for example, the name you use for the `net start` command to start your service).</span></span>

7. <span data-ttu-id="daf94-198">Выберите для свойства <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> значение <xref:System.ServiceProcess.ServiceStartMode.Automatic> в раскрывающемся списке.</span><span class="sxs-lookup"><span data-stu-id="daf94-198">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic> from the drop-down list.</span></span>

8. <span data-ttu-id="daf94-199">В итоге окно **Свойства** должно выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="daf94-199">When you're finished, the **Properties** windows should look like the following figure:</span></span>

     <span data-ttu-id="daf94-200">![Свойства установщика для службы Windows](./media/windows-service-installer-properties.png "Свойства установщика службы Windows")</span><span class="sxs-lookup"><span data-stu-id="daf94-200">![Installer Properties for a Windows service](./media/windows-service-installer-properties.png "Windows service installer properties")</span></span>

9. <span data-ttu-id="daf94-201">В представлении **Конструктор** для **ProjectInstaller** выберите **serviceProcessInstaller1** для проекта Visual C# или **ServiceProcessInstaller1** для проекта Visual Basic. Затем в контекстном меню выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="daf94-201">In the **Design** view for **ProjectInstaller**, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project, then choose **Properties** from the shortcut menu.</span></span> <span data-ttu-id="daf94-202">Выберите для свойства <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> значение <xref:System.ServiceProcess.ServiceAccount.LocalSystem> в раскрывающемся списке.</span><span class="sxs-lookup"><span data-stu-id="daf94-202">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem> from the drop-down list.</span></span>

     <span data-ttu-id="daf94-203">Это позволит установить и запускать службу от имени локальной системной учетной записи.</span><span class="sxs-lookup"><span data-stu-id="daf94-203">This setting installs the service and runs it by using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="daf94-204">У учетной записи <xref:System.ServiceProcess.ServiceAccount.LocalSystem> имеется множество разрешений, включая разрешение на запись в журнал событий.</span><span class="sxs-lookup"><span data-stu-id="daf94-204">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="daf94-205">Эту учетную запись следует использовать с осторожностью, поскольку это может увеличить риск атак с помощью вредоносных программ.</span><span class="sxs-lookup"><span data-stu-id="daf94-205">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="daf94-206">Для других задач следует рассмотреть возможность использования учетной записи <xref:System.ServiceProcess.ServiceAccount.LocalService> , которая аналогична учетной записи непривилегированного пользователя локального компьютера. Удаленным серверам при этом передаются учетные данные анонимного пользователя.</span><span class="sxs-lookup"><span data-stu-id="daf94-206">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="daf94-207">В этом примере произойдет ошибка, если вы попытаетесь использовать учетную запись <xref:System.ServiceProcess.ServiceAccount.LocalService> , так как для нее требуется разрешение на запись в журнал событий.</span><span class="sxs-lookup"><span data-stu-id="daf94-207">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="daf94-208">Дополнительные сведения об установщиках см. в руководстве по [ добавлению установщиков в приложение-службу](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="daf94-208">For more information about installers, see [How to: Add installers to your service application](how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="daf94-209">Установка параметров запуска (необязательно)</span><span class="sxs-lookup"><span data-stu-id="daf94-209">(Optional) Set startup parameters</span></span>

> [!NOTE]
> <span data-ttu-id="daf94-210">Прежде чем добавлять параметры запуска, решите, является ли это наилучшим способом передачи информации в службу.</span><span class="sxs-lookup"><span data-stu-id="daf94-210">Before you decide to add startup parameters, consider whether it's the best way to pass information to your service.</span></span> <span data-ttu-id="daf94-211">Хотя параметры запуска просты для использования и синтаксического анализа и пользователи могут легко их переопределять, для пользователей их поиск и применение могут оказаться затрудненными (без документации).</span><span class="sxs-lookup"><span data-stu-id="daf94-211">Although they're easy to use and parse, and a user can easily override them, they might be harder for a user to discover and use without documentation.</span></span> <span data-ttu-id="daf94-212">Как правило, если вашей службе требуется всего несколько параметров запуска, то следует использовать реестр или файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="daf94-212">Generally, if your service requires more than just a few startup parameters, you should use the registry or a configuration file instead.</span></span>

<span data-ttu-id="daf94-213">Служба Windows может принимать аргументы командной строки или параметры запуска.</span><span class="sxs-lookup"><span data-stu-id="daf94-213">A Windows service can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="daf94-214">При добавлении кода в параметры запуска процесса пользователь может запускать службу со своими собственными специальными параметрами из окна свойств службы.</span><span class="sxs-lookup"><span data-stu-id="daf94-214">When you add code to process startup parameters, a user can start your service with their own custom startup parameters in the service properties window.</span></span> <span data-ttu-id="daf94-215">Однако эти параметры запуска не сохраняются при следующем запуске службы.</span><span class="sxs-lookup"><span data-stu-id="daf94-215">However, these startup parameters aren't persisted the next time the service starts.</span></span> <span data-ttu-id="daf94-216">Задать постоянные параметры запуска можно в реестре.</span><span class="sxs-lookup"><span data-stu-id="daf94-216">To set startup parameters permanently, set them in the registry.</span></span>

<span data-ttu-id="daf94-217">Для каждой службы Windows создается запись в разделе реестра **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services**.</span><span class="sxs-lookup"><span data-stu-id="daf94-217">Each Windows service has a registry entry under the **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services** subkey.</span></span> <span data-ttu-id="daf94-218">Для хранения информации, к которой может обращаться ваша служба, в разделе службы можно использовать подраздел **Parameters**.</span><span class="sxs-lookup"><span data-stu-id="daf94-218">Under each service's subkey, use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="daf94-219">Файлы конфигурации приложения для службы Windows можно использовать так же, как и для программ других типов.</span><span class="sxs-lookup"><span data-stu-id="daf94-219">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="daf94-220">Пример кода см. в разделе <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="daf94-220">For sample code, see <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.</span></span>

### <a name="to-add-startup-parameters"></a><span data-ttu-id="daf94-221">Добавление параметров запуска</span><span class="sxs-lookup"><span data-stu-id="daf94-221">To add startup parameters</span></span>

1. <span data-ttu-id="daf94-222">Выберите файл **Program.cs** или **MyNewService.Designer.vb**, а затем в контекстном меню выберите пункт **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="daf94-222">Select **Program.cs**, or **MyNewService.Designer.vb**, then choose **View Code** from the shortcut menu.</span></span> <span data-ttu-id="daf94-223">Измените код метода `Main`, добавив входной параметр, который будет передаваться в конструктор службы:</span><span class="sxs-lookup"><span data-stu-id="daf94-223">In the `Main` method, change the code to add an input parameter and pass it to the service constructor:</span></span>

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. <span data-ttu-id="daf94-224">В файле **MyNewService.cs** или **MyNewService.vb** измените конструктор `MyNewService` для обработки входного параметра следующим образом:</span><span class="sxs-lookup"><span data-stu-id="daf94-224">In **MyNewService.cs**, or **MyNewService.vb**, change the `MyNewService` constructor to process the input parameter as follows:</span></span>

   ```csharp
   using System.Diagnostics;

   public MyNewService(string[] args)
   {
       InitializeComponent();

       string eventSourceName = "MySource";
       string logName = "MyNewLog";

       if (args.Length > 0)
       {
          eventSourceName = args[0];
       }

       if (args.Length > 1)
       {
           logName = args[1];
       }

       eventLog1 = new EventLog();

       if (!EventLog.SourceExists(eventSourceName))
       {
           EventLog.CreateEventSource(eventSourceName, logName);
       }

       eventLog1.Source = eventSourceName;
       eventLog1.Log = logName;
   }
   ```

   ```vb
   Imports System.Diagnostics

   Public Sub New(ByVal cmdArgs() As String)
       InitializeComponent()
       Dim eventSourceName As String = "MySource"
       Dim logName As String = "MyNewLog"
       If (cmdArgs.Count() > 0) Then
           eventSourceName = cmdArgs(0)
       End If
       If (cmdArgs.Count() > 1) Then
           logName = cmdArgs(1)
       End If
       eventLog1 = New EventLog()
       If (Not EventLog.SourceExists(eventSourceName)) Then
           EventLog.CreateEventSource(eventSourceName, logName)
       End If
       eventLog1.Source = eventSourceName
       eventLog1.Log = logName
   End Sub
   ```

   <span data-ttu-id="daf94-225">Этот код задает имя источника события и журнала в соответствии с указанными пользователем параметрами запуска.</span><span class="sxs-lookup"><span data-stu-id="daf94-225">This code sets the event source and log name according to the startup parameters that the user supplies.</span></span> <span data-ttu-id="daf94-226">Если аргументы не заданы, используются значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="daf94-226">If no arguments are supplied, it uses default values.</span></span>

3. <span data-ttu-id="daf94-227">Чтобы задать аргументы командной строки, добавьте следующий код в класс `ProjectInstaller` в файле **ProjectInstaller.cs** или **ProjectInstaller.vb**:</span><span class="sxs-lookup"><span data-stu-id="daf94-227">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in **ProjectInstaller.cs**, or **ProjectInstaller.vb**:</span></span>

   ```csharp
   protected override void OnBeforeInstall(IDictionary savedState)
   {
       string parameter = "MySource1\" \"MyLogFile1";
       Context.Parameters["assemblypath"] = "\"" + Context.Parameters["assemblypath"] + "\" \"" + parameter + "\"";
       base.OnBeforeInstall(savedState);
   }
   ```

   ```vb
   Protected Overrides Sub OnBeforeInstall(ByVal savedState As IDictionary)
       Dim parameter As String = "MySource1"" ""MyLogFile1"
       Context.Parameters("assemblypath") = """" + Context.Parameters("assemblypath") + """ """ + parameter + """"
       MyBase.OnBeforeInstall(savedState)
   End Sub
   ```

   <span data-ttu-id="daf94-228">Как правило, это значение представляет собой полный путь к исполняемому файлу службы Windows.</span><span class="sxs-lookup"><span data-stu-id="daf94-228">Typically, this value contains the full path to the executable for the Windows service.</span></span> <span data-ttu-id="daf94-229">Для правильного запуска службы пользователь должен заключить путь и каждый параметр в кавычки.</span><span class="sxs-lookup"><span data-stu-id="daf94-229">For the service to start up correctly, the user must supply quotation marks for the path and each individual parameter.</span></span> <span data-ttu-id="daf94-230">Чтобы изменить параметры запуска службы Windows, пользователь может настроить параметры в разделе реестра **ImagePath**.</span><span class="sxs-lookup"><span data-stu-id="daf94-230">A user can change the parameters in the **ImagePath** registry entry to change the startup parameters for the Windows service.</span></span> <span data-ttu-id="daf94-231">Однако лучше изменять их программными средствами и создать для пользователей удобный интерфейс для этой возможности, например в виде программы управления или настройки.</span><span class="sxs-lookup"><span data-stu-id="daf94-231">However, a better way is to change the value programmatically and expose the functionality in a user-friendly way, such as by using a management or configuration utility.</span></span>

## <a name="build-the-service"></a><span data-ttu-id="daf94-232">Сборка службы</span><span class="sxs-lookup"><span data-stu-id="daf94-232">Build the service</span></span>

1. <span data-ttu-id="daf94-233">В **обозревателе решений** выберите пункт **Свойства** в контекстном меню проекта **MyNewService**.</span><span class="sxs-lookup"><span data-stu-id="daf94-233">In **Solution Explorer**, choose **Properties** from the shortcut menu for the **MyNewService** project.</span></span>

   <span data-ttu-id="daf94-234">Отобразятся страницы свойств для проекта.</span><span class="sxs-lookup"><span data-stu-id="daf94-234">The property pages for your project appear.</span></span>

2. <span data-ttu-id="daf94-235">На вкладке **Приложение** в списке **Автоматически запускаемый объект** выберите **MyNewService.Program** (или **Sub Main** для проекта Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="daf94-235">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**, or **Sub Main** for Visual Basic projects.</span></span>

3. <span data-ttu-id="daf94-236">Чтобы выполнить сборку проекта, в **обозревателе решений** выберите в контекстном меню проекта пункт **Сборка** (или нажмите клавиши **CTRL**+**SHIFT**+**B**).</span><span class="sxs-lookup"><span data-stu-id="daf94-236">To build the project, in **Solution Explorer**, choose **Build** from the shortcut menu for your project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="daf94-237">Установка службы</span><span class="sxs-lookup"><span data-stu-id="daf94-237">Install the service</span></span>

<span data-ttu-id="daf94-238">После создания службы Windows ее можно установить.</span><span class="sxs-lookup"><span data-stu-id="daf94-238">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="daf94-239">Чтобы установить службу Windows, необходимо иметь разрешения администратора на том компьютере, где выполняется установка.</span><span class="sxs-lookup"><span data-stu-id="daf94-239">To install a Windows service, you must have administrator credentials on the computer where it's installed.</span></span>

1. <span data-ttu-id="daf94-240">Откройте [Командную строку разработчика Visual Studio](/visualstudio/ide/reference/command-prompt-powershell) с учетными данными администратора.</span><span class="sxs-lookup"><span data-stu-id="daf94-240">Open [Developer Command Prompt for Visual Studio](/visualstudio/ide/reference/command-prompt-powershell) with administrative credentials.</span></span>

2. <span data-ttu-id="daf94-241">В **командной строке разработчика для Visual Studio** перейдите к папке, которая содержит выходные данные проекта (по умолчанию это подкаталог *\bin\Debug* проекта).</span><span class="sxs-lookup"><span data-stu-id="daf94-241">In **Developer Command Prompt for Visual Studio**, navigate to the folder that contains your project's output (by default, the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="daf94-242">Введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="daf94-242">Enter the following command:</span></span>

    ```shell
    installutil MyNewService.exe
    ```

    <span data-ttu-id="daf94-243">Если служба установлена успешно, команда сообщит об успешном выполнении.</span><span class="sxs-lookup"><span data-stu-id="daf94-243">If the service installs successfully, the command reports success.</span></span>

    <span data-ttu-id="daf94-244">Если система не может найти файл *installutil.exe*, убедитесь в том, что он есть на вашем компьютере.</span><span class="sxs-lookup"><span data-stu-id="daf94-244">If the system can't find *installutil.exe*, make sure that it exists on your computer.</span></span> <span data-ttu-id="daf94-245">Это средство устанавливается вместе с платформой .NET Framework в папке *%windir%\Microsoft.NET\Framework[64]\\&lt;версия платформы&gt;* .</span><span class="sxs-lookup"><span data-stu-id="daf94-245">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\&lt;framework version&gt;*.</span></span> <span data-ttu-id="daf94-246">Например, для 64-разрядной версии по умолчанию используется путь *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span><span class="sxs-lookup"><span data-stu-id="daf94-246">For example, the default path for the 64-bit version is *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="daf94-247">Если процесс **installutil.exe** завершается сбоем, найдите причину в журнале установки.</span><span class="sxs-lookup"><span data-stu-id="daf94-247">If the **installutil.exe** process fails, check the install log to find out why.</span></span> <span data-ttu-id="daf94-248">По умолчанию журнал находится в той же папке, что и исполняемый файл службы.</span><span class="sxs-lookup"><span data-stu-id="daf94-248">By default, the log is in the same folder as the service executable.</span></span> <span data-ttu-id="daf94-249">Установка может завершиться сбоем по указанным ниже причинам.</span><span class="sxs-lookup"><span data-stu-id="daf94-249">The installation can fail if:</span></span>
    - <span data-ttu-id="daf94-250">Класс <xref:System.ComponentModel.RunInstallerAttribute> отсутствует в классе `ProjectInstaller`.</span><span class="sxs-lookup"><span data-stu-id="daf94-250">The <xref:System.ComponentModel.RunInstallerAttribute> class isn't present on the `ProjectInstaller` class.</span></span>
    - <span data-ttu-id="daf94-251">Значение атрибута отличается от `true`.</span><span class="sxs-lookup"><span data-stu-id="daf94-251">The attribute isn't set to `true`.</span></span>
    - <span data-ttu-id="daf94-252">Класс `ProjectInstaller` не определен как `public`.</span><span class="sxs-lookup"><span data-stu-id="daf94-252">The `ProjectInstaller` class isn't defined as `public`.</span></span>

<span data-ttu-id="daf94-253">Дополнительные сведения см. в разделе [Практическое руководство. Установка и удаление служб](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="daf94-253">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="daf94-254">Запуск и выполнение службы</span><span class="sxs-lookup"><span data-stu-id="daf94-254">Start and run the service</span></span>

1. <span data-ttu-id="daf94-255">В Windows откройте классическое приложение **Службы**.</span><span class="sxs-lookup"><span data-stu-id="daf94-255">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="daf94-256">Нажмите клавиши **Windows**+**R**, чтобы открыть окно **Выполнить**, введите *services.msc* и нажмите клавишу **ВВОД** или кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="daf94-256">Press **Windows**+**R** to open the **Run** box, enter *services.msc*, and then press **Enter** or select **OK**.</span></span>

     <span data-ttu-id="daf94-257">Заданное вами отображаемое имя службы отобразится в списке **Службы**, представленном в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="daf94-257">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![MyNewService в окне "Службы".](./media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="daf94-259">Чтобы запустить службу, в ее контекстном меню выберите пункт **Запустить**.</span><span class="sxs-lookup"><span data-stu-id="daf94-259">To start the service, choose **Start** from the service's shortcut menu.</span></span>

3. <span data-ttu-id="daf94-260">Чтобы остановить службу, в ее контекстном меню выберите пункт **Остановить**.</span><span class="sxs-lookup"><span data-stu-id="daf94-260">To stop the service, choose **Stop** from the service's shortcut menu.</span></span>

4. <span data-ttu-id="daf94-261">Для запуска и остановки службы в командной строке можно использовать команды **net start &lt;имя службы&gt;** и **net stop &lt;имя службы&gt;** (необязательно).</span><span class="sxs-lookup"><span data-stu-id="daf94-261">(Optional) From the command line, use the commands **net start &lt;service name&gt;** and **net stop &lt;service name&gt;** to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="daf94-262">Проверка журнала событий для службы</span><span class="sxs-lookup"><span data-stu-id="daf94-262">Verify the event log output of your service</span></span>

1. <span data-ttu-id="daf94-263">В Windows откройте классическое приложение **Просмотр событий**.</span><span class="sxs-lookup"><span data-stu-id="daf94-263">In Windows, open the **Event Viewer** desktop app.</span></span> <span data-ttu-id="daf94-264">Введите строку *Просмотр событий* в поле поиска Windows и выберите **Просмотр событий** в результатах поиска.</span><span class="sxs-lookup"><span data-stu-id="daf94-264">Enter *Event Viewer* in the Windows search bar, and then select **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="daf94-265">В Visual Studio доступ к журналам событий можно получить, открыв **обозреватель сервера** в меню **Вид** (или нажав клавиши **CTRL**+**ALT**+**S**) и развернув узел **Журналы событий** для локального компьютера.</span><span class="sxs-lookup"><span data-stu-id="daf94-265">In Visual Studio, you can access event logs by opening **Server Explorer** from the **View** menu (or press **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="daf94-266">В **средстве просмотра событий** разверните узел **Журналы приложений и служб**.</span><span class="sxs-lookup"><span data-stu-id="daf94-266">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="daf94-267">Найдите в списке элемент **MyNewLog** (или **MyLogFile1**, если вы использовали процедуру добавления аргументов командной строки) и разверните его.</span><span class="sxs-lookup"><span data-stu-id="daf94-267">Locate the listing for **MyNewLog** (or **MyLogFile1** if you followed the procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="daf94-268">Вы увидите записи для двух действий (запуск и остановка), которые выполнила ваша служба.</span><span class="sxs-lookup"><span data-stu-id="daf94-268">You should see the entries for the two actions (start and stop) that your service performed.</span></span>

     ![Просмотр записей в журнале событий с помощью компонента "Просмотр событий"](./media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a><span data-ttu-id="daf94-270">Очистка ресурсов</span><span class="sxs-lookup"><span data-stu-id="daf94-270">Clean up resources</span></span>

<span data-ttu-id="daf94-271">Если приложение службы Windows вам больше не нужно, его можно удалить.</span><span class="sxs-lookup"><span data-stu-id="daf94-271">If you no longer need the Windows service app, you can remove it.</span></span>

1. <span data-ttu-id="daf94-272">Откройте **Командную строку разработчика Visual Studio** с учетными данными администратора.</span><span class="sxs-lookup"><span data-stu-id="daf94-272">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="daf94-273">В окне **Командная строка разработчика для Visual Studio** перейдите к папке, которая содержит выходные данные проекта.</span><span class="sxs-lookup"><span data-stu-id="daf94-273">In the **Developer Command Prompt for Visual Studio** window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="daf94-274">Введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="daf94-274">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="daf94-275">Если служба удалена успешно, команда сообщит об этом.</span><span class="sxs-lookup"><span data-stu-id="daf94-275">If the service uninstalls successfully, the command reports that your service was successfully removed.</span></span> <span data-ttu-id="daf94-276">Дополнительные сведения см. в разделе [Практическое руководство. Установка и удаление служб](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="daf94-276">For more information, see [How to: Install and uninstall services](how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="daf94-277">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="daf94-277">Next steps</span></span>

<span data-ttu-id="daf94-278">Теперь, после создания службы, можно выполнить указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="daf94-278">Now that you've created the service, you can:</span></span>

- <span data-ttu-id="daf94-279">Создайте автономную программу установки, с помощью которой другие пользователи могут устанавливать вашу службу Windows.</span><span class="sxs-lookup"><span data-stu-id="daf94-279">Create a standalone setup program for others to use to install your Windows service.</span></span> <span data-ttu-id="daf94-280">Создать установщик для службы Windows можно с помощью [набора инструментов WiX](https://wixtoolset.org/).</span><span class="sxs-lookup"><span data-stu-id="daf94-280">Use the [WiX Toolset](https://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="daf94-281">Другие идеи можно почерпнуть в статье [о создании пакета установщика](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span><span class="sxs-lookup"><span data-stu-id="daf94-281">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).</span></span>

- <span data-ttu-id="daf94-282">Изучите возможности компонента <xref:System.ServiceProcess.ServiceController>, который позволяет отправлять команды в установленную службу.</span><span class="sxs-lookup"><span data-stu-id="daf94-282">Explore the <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

- <span data-ttu-id="daf94-283">Для создания журнала событий при установке приложения, а не во время его запуска, можно воспользоваться установщиком.</span><span class="sxs-lookup"><span data-stu-id="daf94-283">Instead of creating the event log when the application runs, use an installer to create an event log when you install the application.</span></span> <span data-ttu-id="daf94-284">В этом случае журнал событий удаляется установщиком при удалении приложения.</span><span class="sxs-lookup"><span data-stu-id="daf94-284">The event log is deleted by the installer when you uninstall the application.</span></span> <span data-ttu-id="daf94-285">Для получения дополнительной информации см. <xref:System.Diagnostics.EventLogInstaller>.</span><span class="sxs-lookup"><span data-stu-id="daf94-285">For more information, see <xref:System.Diagnostics.EventLogInstaller>.</span></span>

## <a name="see-also"></a><span data-ttu-id="daf94-286">См. также</span><span class="sxs-lookup"><span data-stu-id="daf94-286">See also</span></span>

- [<span data-ttu-id="daf94-287">Приложения служб Windows</span><span class="sxs-lookup"><span data-stu-id="daf94-287">Windows service applications</span></span>](index.md)
- [<span data-ttu-id="daf94-288">Знакомство с приложениями служб Windows</span><span class="sxs-lookup"><span data-stu-id="daf94-288">Introduction to Windows service applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="daf94-289">Практическое руководство. Отладка приложений служб Windows</span><span class="sxs-lookup"><span data-stu-id="daf94-289">How to: Debug Windows service applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="daf94-290">Службы (Windows)</span><span class="sxs-lookup"><span data-stu-id="daf94-290">Services (Windows)</span></span>](/windows/desktop/Services/services)
