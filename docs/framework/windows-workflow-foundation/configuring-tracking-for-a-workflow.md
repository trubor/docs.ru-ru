---
description: Дополнительные сведения о настройке отслеживания для рабочего процесса
title: Настройка отслеживания рабочего процесса
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 061a0edf107296e04d86ed1a50b9a8bfefd7bfce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792769"
---
# <a name="configuring-tracking-for-a-workflow"></a><span data-ttu-id="39a79-103">Настройка отслеживания рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="39a79-103">Configuring Tracking for a Workflow</span></span>

<span data-ttu-id="39a79-104">Рабочий процесс может выполняться тремя способами.</span><span class="sxs-lookup"><span data-stu-id="39a79-104">A workflow can execute in three ways:</span></span>

- <span data-ttu-id="39a79-105">Располагается в среде <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="39a79-105">Hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>

- <span data-ttu-id="39a79-106">Выполняться в виде приложения <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="39a79-106">Executed as a <xref:System.Activities.WorkflowApplication></span></span>

- <span data-ttu-id="39a79-107">Выполняться напрямую с использованием <xref:System.Activities.WorkflowInvoker></span><span class="sxs-lookup"><span data-stu-id="39a79-107">Executed directly using <xref:System.Activities.WorkflowInvoker></span></span>

<span data-ttu-id="39a79-108">В зависимости от выбранного варианта размещения рабочего процесса участник отслеживания может быть добавлен как посредством кода, так и через файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="39a79-108">Depending on the workflow hosting option, a tracking participant can be added either through code or through a configuration file.</span></span> <span data-ttu-id="39a79-109">В этом разделе описывается, как настроить отслеживание посредством добавления участника отслеживания в <xref:System.Activities.WorkflowApplication> и в <xref:System.ServiceModel.Activities.WorkflowServiceHost>, и как включить режим отслеживания с помощью <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="39a79-109">This topic describes how tracking is configured by adding a tracking participant to a <xref:System.Activities.WorkflowApplication> and to a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, and how to enable tracking when using <xref:System.Activities.WorkflowInvoker>.</span></span>

## <a name="configuring-workflow-application-tracking"></a><span data-ttu-id="39a79-110">Настройка отслеживания приложений рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="39a79-110">Configuring Workflow Application Tracking</span></span>

<span data-ttu-id="39a79-111">Запустить рабочий процесс можно с использованием приложения <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="39a79-111">A workflow can run using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="39a79-112">В этом разделе показывается, как настраивается отслеживание для приложения рабочего процесса [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] путем добавления участника отслеживания в узел рабочего процесса <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="39a79-112">This topic demonstrates how tracking is configured for a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] workflow application by adding a tracking participant to the <xref:System.Activities.WorkflowApplication> workflow host.</span></span> <span data-ttu-id="39a79-113">В этом случае рабочий процесс выполняется как приложение рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="39a79-113">In this case, the workflow runs as a workflow application.</span></span> <span data-ttu-id="39a79-114">Приложение рабочего процесса можно настроить посредством кода (без использования файла конфигурации), представляющего собой резидентный EXE-файл, использующий класс <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="39a79-114">You configure a workflow application through code (rather than by using a configuration file), which is a self-hosted .exe file using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="39a79-115">Участник отслеживания добавляется как расширение для экземпляра <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="39a79-115">The tracking participant is added as an extension to the <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="39a79-116">Это выполняется путем добавления <xref:System.Activities.Tracking.TrackingParticipant> в коллекцию расширений для экземпляра WorkflowApplication.</span><span class="sxs-lookup"><span data-stu-id="39a79-116">This is done by adding the <xref:System.Activities.Tracking.TrackingParticipant> to the extensions collection for the WorkflowApplication instance.</span></span>

<span data-ttu-id="39a79-117">Для приложения рабочего процесса можно добавить расширение поведения <xref:System.Activities.Tracking.EtwTrackingParticipant>, как это показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="39a79-117">For a workflow application, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension as shown in the following code.</span></span>

```csharp
LogActivity activity = new LogActivity();

WorkflowApplication instance = new WorkflowApplication(activity);
EtwTrackingParticipant trackingParticipant =
    new EtwTrackingParticipant
{

        TrackingProfile = new TrackingProfile
           {
               Name = "SampleTrackingProfile",
               ActivityDefinitionId = "ProcessOrder",
               Queries = new WorkflowInstanceQuery
               {
                  States = { "*" }
              }
          }
       };
instance.Extensions.Add(trackingParticipant);
```

### <a name="configuring-workflow-service-tracking"></a><span data-ttu-id="39a79-118">Настройка отслеживания службы рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="39a79-118">Configuring Workflow Service Tracking</span></span>

<span data-ttu-id="39a79-119">Рабочий процесс может быть представлен как служба WCF при размещении в <xref:System.ServiceModel.Activities.WorkflowServiceHost> узле службы.</span><span class="sxs-lookup"><span data-stu-id="39a79-119">A workflow can be exposed as a WCF service when hosted in the <xref:System.ServiceModel.Activities.WorkflowServiceHost> service host.</span></span> <span data-ttu-id="39a79-120">Класс <xref:System.ServiceModel.Activities.WorkflowServiceHost> является специализированной реализацией класса ServiceHost библиотеки .NET для службы на основе рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="39a79-120"><xref:System.ServiceModel.Activities.WorkflowServiceHost> is a specialized .NET ServiceHost implementation for a workflow-based service.</span></span> <span data-ttu-id="39a79-121">В этом разделе описывается настройка отслеживания для службы рабочего процесса [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], выполняющейся в <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="39a79-121">This section explains how to configure tracking for a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow service running in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="39a79-122">Его настройка осуществляется с использованием файла Web.config (для служб, размещаемых на веб-сервере) или файла App.config (для служб, размещаемых в автономном приложении, например, в консольном приложении) посредством определения поведения службы или задания кода путем добавления поведения, связанного с отслеживанием, в коллекцию <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> для узла службы.</span><span class="sxs-lookup"><span data-stu-id="39a79-122">It is configured through a Web.config file (for a Web-hosted service) or an App.config file (for a service hosted in a stand-alone application, such as a console application) by specifying a service behavior or through code by adding a tracking-specific behavior to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection for the service host.</span></span>

<span data-ttu-id="39a79-123">Для службы рабочего процесса, размещенной в <xref:System.ServiceModel.WorkflowServiceHost> , можно добавить <xref:System.Activities.Tracking.EtwTrackingParticipant> с помощью `behavior` элемента <> в файле конфигурации, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="39a79-123">For a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="39a79-124">Также для службы рабочего процесса, размещенной в <xref:System.ServiceModel.WorkflowServiceHost>, можно добавить расширение поведения <xref:System.Activities.Tracking.EtwTrackingParticipant> посредством кода.</span><span class="sxs-lookup"><span data-stu-id="39a79-124">Alternatively, for a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension through code.</span></span> <span data-ttu-id="39a79-125">Для добавления пользовательского участника отслеживания создайте новое расширение поведения и добавьте его в <xref:System.ServiceModel.ServiceHost>, как это показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="39a79-125">To add a custom tracking participant, create a new behavior extension and add it to the <xref:System.ServiceModel.ServiceHost> as shown in the following example code.</span></span>

> [!NOTE]
> <span data-ttu-id="39a79-126">Если вы хотите просмотреть пример кода, показывающий, как создать пользовательский элемент поведения, который добавляет настраиваемый участник отслеживания, обратитесь к примерам [отслеживания](./samples/tracking.md) .</span><span class="sxs-lookup"><span data-stu-id="39a79-126">If you want to view sample code that shows how to create a custom behavior element that adds a custom tracking participant, refer to the [Tracking](./samples/tracking.md) samples.</span></span>

```csharp
ServiceHost svcHost = new ServiceHost(typeof(WorkflowService), new
                                 Uri("http://localhost:8001/Sample"));
EtwTrackingBehavior trackingBehavior =
    new EtwTrackingBehavior
    {
        ProfileName = "Sample Tracking Profile"
    };
svcHost.Description.Behaviors.Add(trackingBehavior);
svcHost.Open();
```

<span data-ttu-id="39a79-127">Участник отслеживания добавляется к узлу службы рабочего процесса, как расширение поведения.</span><span class="sxs-lookup"><span data-stu-id="39a79-127">The tracking participant is added to the workflow service host as an extension to the behavior.</span></span>

<span data-ttu-id="39a79-128">В образце кода ниже показано считывание профиля отслеживания из файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="39a79-128">This sample code below shows how to read a tracking profile from configuration file.</span></span>

```csharp
TrackingProfile GetProfile(string profileName, string displayName)
        {
            TrackingProfile trackingProfile = null;
            TrackingSection trackingSection = (TrackingSection)WebConfigurationManager.GetSection("system.serviceModel/tracking");
            if (trackingSection == null)
            {
                return null;
            }

            profileName ??= "";

            //Find the profile with the specified profile name in the list of profile found in config
            var match = from p in new List<TrackingProfile>(trackingSection.TrackingProfiles)
                        where (p.Name == profileName) && ((p.ActivityDefinitionId == displayName) || (p.ActivityDefinitionId == "*"))
                        select p;

            if (match.Count() == 0)
            {
                //return an empty profile
                trackingProfile = new TrackingProfile()
                {
                    ActivityDefinitionId = displayName
                };

            }
            else
            {
                trackingProfile = match.First();
            }

            return trackingProfile;
```

<span data-ttu-id="39a79-129">В образце кода ниже показано добавление профиля отслеживания к узлу рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="39a79-129">This sample code shows how to add a tracking profile to a workflow host.</span></span>

```csharp
WorkflowServiceHost workflowServiceHost = serviceHostBase as WorkflowServiceHost;
if (null != workflowServiceHost)
{
    string workflowDisplayName = workflowServiceHost.Activity.DisplayName;
    TrackingProfile trackingProfile = GetProfile(this.profileName, workflowDisplayName);
    workflowServiceHost.WorkflowExtensions.Add(()  => new EtwTrackingParticipant {
        TrackingProfile = trackingProfile
    });
 }
```

> [!NOTE]
> <span data-ttu-id="39a79-130">Дополнительные сведения о профилях отслеживания см. в статье [Профили отслеживания](tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="39a79-130">For more information on tracking profiles, refer to [Tracking Profiles](tracking-profiles.md).</span></span>

### <a name="configuring-tracking-using-workflowinvoker"></a><span data-ttu-id="39a79-131">Конфигурирование отслеживания с помощью WorkflowInvoker</span><span class="sxs-lookup"><span data-stu-id="39a79-131">Configuring tracking using WorkflowInvoker</span></span>

<span data-ttu-id="39a79-132">Чтобы сконфигурировать отслеживание для рабочего процесса, выполняемого с использованием <xref:System.Activities.WorkflowInvoker>, в экземпляр <xref:System.Activities.WorkflowInvoker> добавляется поставщик отслеживания.</span><span class="sxs-lookup"><span data-stu-id="39a79-132">To configure tracking for a workflow executed using <xref:System.Activities.WorkflowInvoker>, add the tracking provider as an extension to a <xref:System.Activities.WorkflowInvoker> instance.</span></span> <span data-ttu-id="39a79-133">В следующем примере кода из примера [Custom Tracking](./samples/custom-tracking.md) .</span><span class="sxs-lookup"><span data-stu-id="39a79-133">The following code example is from the [Custom Tracking](./samples/custom-tracking.md) sample.</span></span>

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a><span data-ttu-id="39a79-134">Просмотр записей отслеживания в обозревателе событий</span><span class="sxs-lookup"><span data-stu-id="39a79-134">Viewing tracking records in Event Viewer</span></span>

<span data-ttu-id="39a79-135">Особый интерес представляют два журнала средства просмотра при отслеживании выполнения WF - аналитический журнал и журнал отладки.</span><span class="sxs-lookup"><span data-stu-id="39a79-135">There are two Event Viewer logs of particular interest to view when tracking WF execution - the Analytic log and the Debug log.</span></span> <span data-ttu-id="39a79-136">Оба находятся в узле Microsoft&#124;Windows&#124;Application Server-Applications.</span><span class="sxs-lookup"><span data-stu-id="39a79-136">Both reside under the Microsoft&#124;Windows&#124;Application Server-Applications node.</span></span> <span data-ttu-id="39a79-137">В этом разделе журналы содержат события из одного приложения, а не события, влияющие на всю систему.</span><span class="sxs-lookup"><span data-stu-id="39a79-137">Logs within this section contain events from a single application rather than events that have an impact on the entire system.</span></span>

<span data-ttu-id="39a79-138">События трассировки отладки записываются в журнал отладки.</span><span class="sxs-lookup"><span data-stu-id="39a79-138">Debug trace events are written to the Debug Log.</span></span> <span data-ttu-id="39a79-139">Для получения событий трассировки отладки WF в средстве просмотра включите журнал отладки.</span><span class="sxs-lookup"><span data-stu-id="39a79-139">To collect WF debug trace events in the Event Viewer, enable the Debug Log.</span></span>

1. <span data-ttu-id="39a79-140">Чтобы открыть Просмотр событий, нажмите кнопку **Пуск** и выберите команду **выполнить.**</span><span class="sxs-lookup"><span data-stu-id="39a79-140">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="39a79-141">В диалоговом окне Выполнить введите `eventvwr` .</span><span class="sxs-lookup"><span data-stu-id="39a79-141">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="39a79-142">В диалоговом окне Просмотр событий разверните узел **журналы приложений и служб** .</span><span class="sxs-lookup"><span data-stu-id="39a79-142">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="39a79-143">Разверните узлы **Microsoft**, **Windows** и **сервер приложений — приложения** .</span><span class="sxs-lookup"><span data-stu-id="39a79-143">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="39a79-144">Щелкните правой кнопкой мыши узел **Отладка** в узле **сервер приложений — приложения** и выберите **Включить журнал**.</span><span class="sxs-lookup"><span data-stu-id="39a79-144">Right-click the **Debug** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="39a79-145">Чтобы сформировать события трассировки, запустите приложение с включенной функцией трассировки.</span><span class="sxs-lookup"><span data-stu-id="39a79-145">Execute your tracing-enabled application to generate tracing events.</span></span>

6. <span data-ttu-id="39a79-146">Щелкните правой кнопкой мыши узел **Отладка** и выберите команду **Обновить.**</span><span class="sxs-lookup"><span data-stu-id="39a79-146">Right-click the **Debug** node and select **Refresh.**</span></span> <span data-ttu-id="39a79-147">На центральную панель будут выведены события трассировки.</span><span class="sxs-lookup"><span data-stu-id="39a79-147">Tracing events should be visible in the center pane.</span></span>

<span data-ttu-id="39a79-148">WF 4 предоставляет участника отслеживания, который пишет записи трассировки в сеанс ETW (средство трассировки событий для Windows).</span><span class="sxs-lookup"><span data-stu-id="39a79-148">WF 4 provides a tracking participant that writes tracking records to an ETW (Event Tracing for Windows) session.</span></span> <span data-ttu-id="39a79-149">Для подписки на записи отслеживания в участнике отслеживания трассировка событий Windows задается профиль отслеживания.</span><span class="sxs-lookup"><span data-stu-id="39a79-149">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="39a79-150">Если включено отслеживание ошибок, записи отслеживания создаются в трассировке событий Windows.</span><span class="sxs-lookup"><span data-stu-id="39a79-150">When tracking is enabled, errors tracking records are emitted to ETW.</span></span> <span data-ttu-id="39a79-151">События трассировки событий Windows (в диапазоне 100–113), соответствующие событиям отслеживания, выпущенным участником отслеживания трассировки событий Windows, записываются в аналитический журнал.</span><span class="sxs-lookup"><span data-stu-id="39a79-151">ETW tracking events (between the range of 100-113) corresponding to the tracking events emitted by the ETW tracking participant are written to the Analytic Log.</span></span>

<span data-ttu-id="39a79-152">Чтобы просмотреть записи отслеживания, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="39a79-152">To view tracking records, follow these steps.</span></span>

1. <span data-ttu-id="39a79-153">Чтобы открыть Просмотр событий, нажмите кнопку **Пуск** и выберите команду **выполнить.**</span><span class="sxs-lookup"><span data-stu-id="39a79-153">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="39a79-154">В диалоговом окне Выполнить введите `eventvwr` .</span><span class="sxs-lookup"><span data-stu-id="39a79-154">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="39a79-155">В диалоговом окне Просмотр событий разверните узел **журналы приложений и служб** .</span><span class="sxs-lookup"><span data-stu-id="39a79-155">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="39a79-156">Разверните узлы **Microsoft**, **Windows** и **сервер приложений — приложения** .</span><span class="sxs-lookup"><span data-stu-id="39a79-156">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="39a79-157">Щелкните правой кнопкой мыши узел **аналитики** в узле **сервер приложений — приложения** и выберите **Включить журнал**.</span><span class="sxs-lookup"><span data-stu-id="39a79-157">Right-click the **Analytic** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="39a79-158">Чтобы сформировать записи отслеживания, запустите приложение с включенной функцией отслеживания.</span><span class="sxs-lookup"><span data-stu-id="39a79-158">Execute your tracking-enabled application to generate tracking records.</span></span>

6. <span data-ttu-id="39a79-159">Щелкните правой кнопкой мыши **аналитический** узел и выберите **Обновить.**</span><span class="sxs-lookup"><span data-stu-id="39a79-159">Right-click the **Analytic** node and select **Refresh.**</span></span> <span data-ttu-id="39a79-160">В центральную область будут выведены записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="39a79-160">Tracking records should be visible in the center pane.</span></span>

<span data-ttu-id="39a79-161">На следующем рисунке показаны события отслеживания в средстве просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="39a79-161">The following image shows tracking events in the event viewer:</span></span>

![Снимок экрана Просмотр событий, отображающий записи отслеживания.](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a><span data-ttu-id="39a79-163">Регистрация идентификатора поставщика конкретного приложения</span><span class="sxs-lookup"><span data-stu-id="39a79-163">Registering an application-specific provider ID</span></span>

<span data-ttu-id="39a79-164">Если сведения о событии нужно заносить в журнал конкретного приложения, для регистрации манифеста нового поставщика необходимо выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="39a79-164">If events need to be written to a specific application log, follow these steps to register the new provider manifest.</span></span>

1. <span data-ttu-id="39a79-165">Укажите идентификатор поставщика в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="39a79-165">Declare the provider ID in the application configuration file.</span></span>

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. <span data-ttu-id="39a79-166">Скопируйте файл манифеста из%windir%\Microsoft.NET\Framework \\ \<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \микрософт.Виндовс.аппликатионсервер.аппликатионс.Ман во временное расположение и переименуйте его в Microsoft.Windows.ApplicationServer.Applications_Provider1. Man.</span><span class="sxs-lookup"><span data-stu-id="39a79-166">Copy the manifest file from %windir%\Microsoft.NET\Framework\\\<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man to a temporary location, and rename it to Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span></span>

3. <span data-ttu-id="39a79-167">Замените идентификатор GUID в файле манифеста на новый идентификатор.</span><span class="sxs-lookup"><span data-stu-id="39a79-167">Change the GUID in the manifest file to the new GUID.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

4. <span data-ttu-id="39a79-168">Если вы не хотите удалять поставщик по умолчанию, измените имя поставщика.</span><span class="sxs-lookup"><span data-stu-id="39a79-168">Change the provider name if you do not want to uninstall the default provider.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

5. <span data-ttu-id="39a79-169">Если на предыдущем шаге имя поставщика было изменено, измените имена каналов в файле манифеста на имя нового поставщика.</span><span class="sxs-lookup"><span data-stu-id="39a79-169">If you changed the provider name in the previous step, change the channel names in the manifest file to the new provider name.</span></span>

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. <span data-ttu-id="39a79-170">Сформируйте DLL-библиотеку ресурсов, выполнив следующие действия.</span><span class="sxs-lookup"><span data-stu-id="39a79-170">Generate the resource DLL by following these steps.</span></span>

    1. <span data-ttu-id="39a79-171">Установите пакет Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="39a79-171">Install the Windows SDK.</span></span> <span data-ttu-id="39a79-172">Windows SDK включает компилятор сообщений ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) и компилятор ресурсов ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).</span><span class="sxs-lookup"><span data-stu-id="39a79-172">The Windows SDK includes the message compiler ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) and resource compiler ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).</span></span>

    2. <span data-ttu-id="39a79-173">В командной строке Windows SDK примените команду run mc.exe к новому файлу манифеста.</span><span class="sxs-lookup"><span data-stu-id="39a79-173">In a Windows SDK command prompt, run mc.exe on the new manifest file.</span></span>

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. <span data-ttu-id="39a79-174">Примените команду rc.exe к файлу ресурсов, сформированному на предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="39a79-174">Run rc.exe on the resource file generated in the previous step.</span></span>

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. <span data-ttu-id="39a79-175">Создайте пустой файл CS с именем NewProviderReg.cs.</span><span class="sxs-lookup"><span data-stu-id="39a79-175">Create an empty cs file called NewProviderReg.cs.</span></span>

    5. <span data-ttu-id="39a79-176">Создайте DLL-библиотеку ресурсов с помощью компилятора C#.</span><span class="sxs-lookup"><span data-stu-id="39a79-176">Create a resource DLL using the C# compiler.</span></span>

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. <span data-ttu-id="39a79-177">Измените имя ресурса и DLL сообщения в файле манифеста с `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` на новое имя библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="39a79-177">Change the resource and message dll name in the manifest file from `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` to the new dll name.</span></span>

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" />
        ```

    7. <span data-ttu-id="39a79-178">Для регистрации манифеста используйте средство [wevtutil](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) .</span><span class="sxs-lookup"><span data-stu-id="39a79-178">Use [wevtutil](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) to register the manifest.</span></span>

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a><span data-ttu-id="39a79-179">См. также</span><span class="sxs-lookup"><span data-stu-id="39a79-179">See also</span></span>

- <span data-ttu-id="39a79-180">[Мониторинг Windows Server App Fabric](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="39a79-180">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="39a79-181">[Мониторинг приложений с помощью App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="39a79-181">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
