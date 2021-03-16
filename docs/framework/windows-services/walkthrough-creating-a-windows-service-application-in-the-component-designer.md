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
# <a name="tutorial-create-a-windows-service-app"></a>Учебник. Создание приложения службы Windows

Из этой статьи вы узнаете, как создать в Visual Studio приложение службы Windows, которое записывает сообщения в журнал событий.

## <a name="create-a-service"></a>Создание службы

Для начала создайте проект и настройте значения, необходимые для правильной работы службы.

1. В Visual Studio в меню **Файл** последовательно выберите пункты **Создать** > **Проект** (или нажмите клавиши **CTRL**+**SHIFT**+**N**), чтобы открыть окно **Новый проект**.

2. Найдите и выберите шаблон проекта **Служба Windows (.NET Framework)** . Чтобы найти его, разверните узел **Установленные**, затем узел **Visual C#** или **Visual Basic** и выберите **Рабочий стол Windows**. Можно также ввести запрос *Служба Windows* в поле поиска в правом верхнем углу и нажать клавишу **ВВОД**.

   ![Шаблон приложения Windows в диалоговом окне нового проекта Visual Studio](./media/new-project-dialog.png)

   > [!NOTE]
   > Если вы не видите здесь шаблон **Служба Windows**, попробуйте установить рабочую нагрузку **Разработка классических приложений .NET**.
   >
   > В диалоговом окне **Новый проект** выберите ссылку **Открыть установщик Visual Studio**. Выберите рабочую нагрузку **Разработка классических приложений .NET** и нажмите кнопку **Изменить**.

3. В поле **Имя** введите *MyNewService*, а затем нажмите кнопку **ОК**.

   Откроется вкладка **Проект** (**Service1.cs [Проект]** или **Service1.vb [Проект]** ).

   Этот шаблон проекта содержит класс компонента с именем `Service1`, наследуемый от <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>. В нем собран основной служебный код, в том числе код для запуска службы.

## <a name="rename-the-service"></a>Переименование службы

Измените имя службы с **Service1** на **MyNewService**.

1. В **обозревателе решений** выберите файл **Service1.cs** или **Service1.vb**, а затем выберите в контекстном меню команду **Переименовать**. Переименуйте файл в **MyNewService.cs** или **MyNewService.vb** и нажмите клавишу **ВВОД**.

    Появится всплывающее окно, предлагающее переименовать все ссылки на элемент кода *Service1*.

2. Выберите **Да**.

    ![Запрос на переименование](./media/windows-service-rename.png "Запрос на переименование службы Windows")

3. На вкладке **Проект** выберите в контекстном меню пункт **Свойства**. В окне **Свойства** измените значение **ServiceName** на *MyNewService*.

    ![Свойства службы](./media/windows-service-properties.png "Свойства службы Windows")

4. В меню **Файл** выберите команду **Сохранить все**.

## <a name="add-features-to-the-service"></a>Добавление компонентов в службу

В этом разделе к службе Windows будет добавлен настраиваемый журнал событий. Компонент <xref:System.Diagnostics.EventLog> — это пример типа компонента, который можно добавить в службу Windows.

### <a name="add-custom-event-log-functionality"></a>Добавление возможности работы с настраиваемым журналом событий

1. В **обозревателе решений** в контекстном меню для файла **MyNewService.cs** или **MyNewService.vb** выберите пункт **Показать конструктор**.

2. На **панели элементов** разверните раздел **Компоненты** и перетащите компонент **EventLog** на вкладку **Service1.cs [Проект]** или **Service1.vb [Проект]** .

3. В **обозревателе решений** в контекстном меню для файла **MyNewService.cs** или **MyNewService.vb** выберите пункт **Просмотреть код**.

4. Определите пользовательский журнал событий. Для C# измените существующий конструктор `MyNewService()`. Для Visual Basic добавьте конструктор `New()`.

   [!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#2)]
   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

5. Добавьте оператор `using` в файл **MyNewService.cs** (если его еще нет) или оператор `Imports` в файл **MyNewService.vb** для пространства имен <xref:System.Diagnostics?displayProperty=nameWithType>.

    ```csharp
    using System.Diagnostics;
    ```

    ```vb
    Imports System.Diagnostics
    ```

6. В меню **Файл** выберите команду **Сохранить все**.

### <a name="define-what-occurs-when-the-service-starts"></a>Определение действий при запуске службы

В редакторе кода для файла **MyNewService.cs** или **MyNewService.vb** найдите метод <xref:System.ServiceProcess.ServiceBase.OnStart%2A>. Пустое определение метода было автоматически добавлено при создании проекта в Visual Studio. Добавьте код, с помощью которой запись сохраняется в журнале событий при запуске службы:

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

#### <a name="polling"></a>Опрос

Так как приложение службы предполагает длительное время выполнения, оно обычно опрашивает или отслеживает систему. Отслеживание настраивается в методе <xref:System.ServiceProcess.ServiceBase.OnStart%2A>. После начала работы службы метод `OnStart` должен возвращать управление операционной системе, чтобы она не блокировалась.

Для создания простого механизма опроса используйте компонент <xref:System.Timers.Timer?displayProperty=nameWithType>. Таймер через определенные интервалы времени генерирует событие <xref:System.Timers.Timer.Elapsed>, при возникновении которых служба может выполнять отслеживание. Компонент <xref:System.Timers.Timer> используется следующим образом:

- Задайте свойства компонента <xref:System.Timers.Timer> в методе `MyNewService.OnStart`.
- Запустите таймер, вызвав метод <xref:System.Timers.Timer.Start%2A>.

##### <a name="set-up-the-polling-mechanism"></a>Настройка механизма опроса.

1. Чтобы настроить механизм опроса, добавьте следующий код в событие `MyNewService.OnStart`:

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

2. Добавьте оператор `using` в файл **MyNewService.cs** или оператор `Imports` в файл **MyNewService.vb** для пространства имен <xref:System.Timers?displayProperty=nameWithType>.

   ```csharp
   using System.Timers;
   ```

   ```vb
   Imports System.Timers
   ```

3. В классе `MyNewService` добавьте метод `OnTimer` для обработки события <xref:System.Timers.Timer.Elapsed?displayProperty=nameWithType>.

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

4. В класс `MyNewService` добавьте переменную-член. Она содержит идентификатор следующего события, которое сохраняется в журнале событий.

   ```csharp
   private int eventId = 1;
   ```

   ```vb
   Private eventId As Integer = 1
   ```

Задачи можно выполнять с помощью фоновых рабочих потоков, а не выполнять всю работу в основном потоке. Для получения дополнительной информации см. <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.

### <a name="define-what-occurs-when-the-service-is-stopped"></a>Определение действий при остановке службы

Вставьте в метод <xref:System.ServiceProcess.ServiceBase.OnStop%2A> строку кода, с помощью которой запись сохраняется в журнале событий при остановке службы:

[!code-csharp[VbRadconService#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#4)]
[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a>Определение других действий для службы

Вы можете переопределить методы <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> и <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>, добавив дополнительные процессы обработки.

Следующий код показывает, как можно переопределить метод <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> в классе `MyNewService`:

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

## <a name="set-service-status"></a>Установка состояния службы

Службы сообщают о своем состоянии [диспетчеру служб](/windows/desktop/Services/service-control-manager), чтобы пользователь мог определить, работает ли служба правильно. По умолчанию служба, которая наследуется от <xref:System.ServiceProcess.ServiceBase>, сообщает ограниченный набор состояний, включая SERVICE_STOPPED, SERVICE_PAUSED и SERVICE_RUNNING. Если служба запускается не сразу, полезно обеспечить сообщение состояния SERVICE_START_PENDING.

Состояния ERVICE_START_PENDING и SERVICE_STOP_PENDING можно реализовать путем добавления кода, вызывающего функцию Windows [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).

### <a name="implement-service-pending-status"></a>Реализация состояния ожидания службы

1. Добавьте оператор `using` в файл **MyNewService.cs** или оператор `Imports` в файл **MyNewService.vb** для пространства имен <xref:System.Runtime.InteropServices?displayProperty=nameWithType>.

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. Добавьте следующий код в файл **MyNewService.cs** или **MyNewService.vb** для объявления значений `ServiceState` и добавления структуры для состояния, которая будет использоваться при вызове неуправляемого кода:

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
    > Диспетчер служб использует члены `dwWaitHint` и `dwCheckpoint`[структуры SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status), чтобы определить время, в течение которого нужно ожидать запуска или завершения работы службы Windows. Если методы `OnStart` и `OnStop` выполняются долго, служба может запросить больше времени, повторно вызвав функцию `SetServiceStatus` с увеличенным значением `dwCheckPoint`.

3. В классе `MyNewService` объявите функцию [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) с помощью [вызова неуправляемого кода](../interop/consuming-unmanaged-dll-functions.md):

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. Для реализации состояния SERVICE_START_PENDING добавьте следующий код в начало метода <xref:System.ServiceProcess.ServiceBase.OnStart%2A>:

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

5. Для установки состояния SERVICE_RUNNING добавьте код в конце метода `OnStart`:

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

6. Если метод <xref:System.ServiceProcess.ServiceBase.OnStop%2A> выполняется долго, повторите данную процедуру для `OnStop` (необязательно). Реализуйте состояние SERVICE_STOP_PENDING и обеспечьте возврат состояния SERVICE_STOPPED до того, как метод `OnStop` вернет управление.

   Пример:

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

## <a name="add-installers-to-the-service"></a>Добавление установщиков в службу

Перед тем как запускать службу Windows, ее нужно установить. При этом она регистрируется в диспетчере служб. В проект можно добавить установщики, которые обрабатывают сведения о регистрации.

1. В **обозревателе решений** в контекстном меню для файла **MyNewService.cs** или **MyNewService.vb** выберите пункт **Показать конструктор**.

2. В представлении **Конструктор** щелкните область фона правой кнопкой мыши и выберите в контекстном меню команду **Добавить установщик**.

     По умолчанию Visual Studio добавляет в проект класс компонента `ProjectInstaller`, содержащий два установщика. Они предназначены для установки службы и связанного со службой процесса.

3. В представлении **Конструктор** для **ProjectInstaller** выберите **serviceInstaller1** для проекта Visual C# или **ServiceInstaller1** для проекта Visual Basic. Затем в контекстном меню выберите пункт **Свойства**.

4. Убедитесь в том, что в окне **Свойства** свойство <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> имеет значение **MyNewService**.

5. Введите для свойства <xref:System.ServiceProcess.ServiceInstaller.Description%2A> какой нибудь текст, например *Пример службы*.

     Этот текст отображается в столбце **Описание** в окне **Службы** и помогает пользователю понять, для чего служба нужна.

    ![Описание службы в окне "Службы".](./media/windows-service-description.png "Описание службы")

6. Введите текст для свойства <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A>, например *Отображаемое имя MyNewService*.

     Этот текст отображается в столбце **Отображаемое имя** в окне **Службы**. Это имя может отличаться от значения свойства <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>, которое представляет собой имя, используемое в системе (например, когда вы запускаете службу с помощью команды `net start`).

7. Выберите для свойства <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> значение <xref:System.ServiceProcess.ServiceStartMode.Automatic> в раскрывающемся списке.

8. В итоге окно **Свойства** должно выглядеть так:

     ![Свойства установщика для службы Windows](./media/windows-service-installer-properties.png "Свойства установщика службы Windows")

9. В представлении **Конструктор** для **ProjectInstaller** выберите **serviceProcessInstaller1** для проекта Visual C# или **ServiceProcessInstaller1** для проекта Visual Basic. Затем в контекстном меню выберите пункт **Свойства**. Выберите для свойства <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> значение <xref:System.ServiceProcess.ServiceAccount.LocalSystem> в раскрывающемся списке.

     Это позволит установить и запускать службу от имени локальной системной учетной записи.

    > [!IMPORTANT]
    > У учетной записи <xref:System.ServiceProcess.ServiceAccount.LocalSystem> имеется множество разрешений, включая разрешение на запись в журнал событий. Эту учетную запись следует использовать с осторожностью, поскольку это может увеличить риск атак с помощью вредоносных программ. Для других задач следует рассмотреть возможность использования учетной записи <xref:System.ServiceProcess.ServiceAccount.LocalService> , которая аналогична учетной записи непривилегированного пользователя локального компьютера. Удаленным серверам при этом передаются учетные данные анонимного пользователя. В этом примере произойдет ошибка, если вы попытаетесь использовать учетную запись <xref:System.ServiceProcess.ServiceAccount.LocalService> , так как для нее требуется разрешение на запись в журнал событий.

Дополнительные сведения об установщиках см. в руководстве по [ добавлению установщиков в приложение-службу](how-to-add-installers-to-your-service-application.md).

## <a name="optional-set-startup-parameters"></a>Установка параметров запуска (необязательно)

> [!NOTE]
> Прежде чем добавлять параметры запуска, решите, является ли это наилучшим способом передачи информации в службу. Хотя параметры запуска просты для использования и синтаксического анализа и пользователи могут легко их переопределять, для пользователей их поиск и применение могут оказаться затрудненными (без документации). Как правило, если вашей службе требуется всего несколько параметров запуска, то следует использовать реестр или файл конфигурации.

Служба Windows может принимать аргументы командной строки или параметры запуска. При добавлении кода в параметры запуска процесса пользователь может запускать службу со своими собственными специальными параметрами из окна свойств службы. Однако эти параметры запуска не сохраняются при следующем запуске службы. Задать постоянные параметры запуска можно в реестре.

Для каждой службы Windows создается запись в разделе реестра **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services**. Для хранения информации, к которой может обращаться ваша служба, в разделе службы можно использовать подраздел **Parameters**. Файлы конфигурации приложения для службы Windows можно использовать так же, как и для программ других типов. Пример кода см. в разделе <xref:System.Configuration.ConfigurationManager.AppSettings?displayProperty=nameWithType>.

### <a name="to-add-startup-parameters"></a>Добавление параметров запуска

1. Выберите файл **Program.cs** или **MyNewService.Designer.vb**, а затем в контекстном меню выберите пункт **Просмотреть код**. Измените код метода `Main`, добавив входной параметр, который будет передаваться в конструктор службы:

   [!code-csharp[VbRadconService](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/Program-add-parameter.cs?highlight=1,6)]
   [!code-vb[VbRadconService](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.Designer-add-parameter.vb?highlight=1-2)]

2. В файле **MyNewService.cs** или **MyNewService.vb** измените конструктор `MyNewService` для обработки входного параметра следующим образом:

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

   Этот код задает имя источника события и журнала в соответствии с указанными пользователем параметрами запуска. Если аргументы не заданы, используются значения по умолчанию.

3. Чтобы задать аргументы командной строки, добавьте следующий код в класс `ProjectInstaller` в файле **ProjectInstaller.cs** или **ProjectInstaller.vb**:

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

   Как правило, это значение представляет собой полный путь к исполняемому файлу службы Windows. Для правильного запуска службы пользователь должен заключить путь и каждый параметр в кавычки. Чтобы изменить параметры запуска службы Windows, пользователь может настроить параметры в разделе реестра **ImagePath**. Однако лучше изменять их программными средствами и создать для пользователей удобный интерфейс для этой возможности, например в виде программы управления или настройки.

## <a name="build-the-service"></a>Сборка службы

1. В **обозревателе решений** выберите пункт **Свойства** в контекстном меню проекта **MyNewService**.

   Отобразятся страницы свойств для проекта.

2. На вкладке **Приложение** в списке **Автоматически запускаемый объект** выберите **MyNewService.Program** (или **Sub Main** для проекта Visual Basic).

3. Чтобы выполнить сборку проекта, в **обозревателе решений** выберите в контекстном меню проекта пункт **Сборка** (или нажмите клавиши **CTRL**+**SHIFT**+**B**).

## <a name="install-the-service"></a>Установка службы

После создания службы Windows ее можно установить. Чтобы установить службу Windows, необходимо иметь разрешения администратора на том компьютере, где выполняется установка.

1. Откройте [Командную строку разработчика Visual Studio](/visualstudio/ide/reference/command-prompt-powershell) с учетными данными администратора.

2. В **командной строке разработчика для Visual Studio** перейдите к папке, которая содержит выходные данные проекта (по умолчанию это подкаталог *\bin\Debug* проекта).

3. Введите следующую команду:

    ```shell
    installutil MyNewService.exe
    ```

    Если служба установлена успешно, команда сообщит об успешном выполнении.

    Если система не может найти файл *installutil.exe*, убедитесь в том, что он есть на вашем компьютере. Это средство устанавливается вместе с платформой .NET Framework в папке *%windir%\Microsoft.NET\Framework[64]\\&lt;версия платформы&gt;* . Например, для 64-разрядной версии по умолчанию используется путь *%windir%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

    Если процесс **installutil.exe** завершается сбоем, найдите причину в журнале установки. По умолчанию журнал находится в той же папке, что и исполняемый файл службы. Установка может завершиться сбоем по указанным ниже причинам.
    - Класс <xref:System.ComponentModel.RunInstallerAttribute> отсутствует в классе `ProjectInstaller`.
    - Значение атрибута отличается от `true`.
    - Класс `ProjectInstaller` не определен как `public`.

Дополнительные сведения см. в разделе [Практическое руководство. Установка и удаление служб](how-to-install-and-uninstall-services.md).

## <a name="start-and-run-the-service"></a>Запуск и выполнение службы

1. В Windows откройте классическое приложение **Службы**. Нажмите клавиши **Windows**+**R**, чтобы открыть окно **Выполнить**, введите *services.msc* и нажмите клавишу **ВВОД** или кнопку **ОК**.

     Заданное вами отображаемое имя службы отобразится в списке **Службы**, представленном в алфавитном порядке.

     ![MyNewService в окне "Службы".](./media/windowsservices-serviceswindow.PNG)

2. Чтобы запустить службу, в ее контекстном меню выберите пункт **Запустить**.

3. Чтобы остановить службу, в ее контекстном меню выберите пункт **Остановить**.

4. Для запуска и остановки службы в командной строке можно использовать команды **net start &lt;имя службы&gt;** и **net stop &lt;имя службы&gt;** (необязательно).

### <a name="verify-the-event-log-output-of-your-service"></a>Проверка журнала событий для службы

1. В Windows откройте классическое приложение **Просмотр событий**. Введите строку *Просмотр событий* в поле поиска Windows и выберите **Просмотр событий** в результатах поиска.

   > [!TIP]
   > В Visual Studio доступ к журналам событий можно получить, открыв **обозреватель сервера** в меню **Вид** (или нажав клавиши **CTRL**+**ALT**+**S**) и развернув узел **Журналы событий** для локального компьютера.

2. В **средстве просмотра событий** разверните узел **Журналы приложений и служб**.

3. Найдите в списке элемент **MyNewLog** (или **MyLogFile1**, если вы использовали процедуру добавления аргументов командной строки) и разверните его. Вы увидите записи для двух действий (запуск и остановка), которые выполнила ваша служба.

     ![Просмотр записей в журнале событий с помощью компонента "Просмотр событий"](./media/windows-service-event-viewer.png)

## <a name="clean-up-resources"></a>Очистка ресурсов

Если приложение службы Windows вам больше не нужно, его можно удалить.

1. Откройте **Командную строку разработчика Visual Studio** с учетными данными администратора.

2. В окне **Командная строка разработчика для Visual Studio** перейдите к папке, которая содержит выходные данные проекта.

3. Введите следующую команду:

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   Если служба удалена успешно, команда сообщит об этом. Дополнительные сведения см. в разделе [Практическое руководство. Установка и удаление служб](how-to-install-and-uninstall-services.md).

## <a name="next-steps"></a>Следующие шаги

Теперь, после создания службы, можно выполнить указанные ниже действия.

- Создайте автономную программу установки, с помощью которой другие пользователи могут устанавливать вашу службу Windows. Создать установщик для службы Windows можно с помощью [набора инструментов WiX](https://wixtoolset.org/). Другие идеи можно почерпнуть в статье [о создании пакета установщика](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).

- Изучите возможности компонента <xref:System.ServiceProcess.ServiceController>, который позволяет отправлять команды в установленную службу.

- Для создания журнала событий при установке приложения, а не во время его запуска, можно воспользоваться установщиком. В этом случае журнал событий удаляется установщиком при удалении приложения. Для получения дополнительной информации см. <xref:System.Diagnostics.EventLogInstaller>.

## <a name="see-also"></a>См. также

- [Приложения служб Windows](index.md)
- [Знакомство с приложениями служб Windows](introduction-to-windows-service-applications.md)
- [Практическое руководство. Отладка приложений служб Windows](how-to-debug-windows-service-applications.md)
- [Службы (Windows)](/windows/desktop/Services/services)
