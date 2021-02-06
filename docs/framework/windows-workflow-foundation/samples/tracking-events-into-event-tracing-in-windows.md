---
description: 'Дополнительные сведения: отслеживание событий в трассировке событий в Windows'
title: Отслеживание событий в системе трассировки событий Windows
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 92ad4aaee100bb3ba7f4174bbbde1dc7eaed58de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653749"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a><span data-ttu-id="253fb-103">Отслеживание событий в системе трассировки событий Windows</span><span class="sxs-lookup"><span data-stu-id="253fb-103">Tracking Events into Event Tracing in Windows</span></span>

<span data-ttu-id="253fb-104">В этом примере показано, как включить отслеживание Windows Workflow Foundation (WF) в службе рабочего процесса и выдать события отслеживания в трассировке событий для Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="253fb-104">This sample demonstrates how to enable Windows Workflow Foundation (WF) tracking on a workflow service and emit the tracking events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="253fb-105">Для создания записей отслеживания рабочих процессов в ETW в этом образце используется участник отслеживания трассировки событий Windows (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span><span class="sxs-lookup"><span data-stu-id="253fb-105">To emit workflow tracking records into ETW, the sample uses the ETW tracking participant (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span></span>

<span data-ttu-id="253fb-106">В образце рабочий процесс получает запрос, присваивает обратное значение входных данных входной переменной и возвращает обратное значение клиенту.</span><span class="sxs-lookup"><span data-stu-id="253fb-106">The workflow in the sample receives a request, assigns the reciprocal of the input data to the input variable and returns the reciprocal back to the client.</span></span> <span data-ttu-id="253fb-107">Если входные данные равны 0, то возникнет необрабатываемое исключение деления на ноль, которое приводит к прерыванию рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="253fb-107">When the input data is 0, a divide by zero exception occurs that is unhandled that causes the workflow to abort.</span></span> <span data-ttu-id="253fb-108">При включенном отслеживании в трассировке событий Windows создается запись отслеживания ошибки, которая в дальнейшем может быть использована для исправления ошибки.</span><span class="sxs-lookup"><span data-stu-id="253fb-108">With tracking enabled, the error track record is emitted to ETW, which can help troubleshoot the error later.</span></span> <span data-ttu-id="253fb-109">Для подписки на записи отслеживания в участнике отслеживания трассировка событий Windows задается профиль отслеживания.</span><span class="sxs-lookup"><span data-stu-id="253fb-109">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="253fb-110">Профиль отслеживания определяется в файле Web.config и предоставляется участнику отслеживания трассировки событий Windows как параметр конфигурации.</span><span class="sxs-lookup"><span data-stu-id="253fb-110">The tracking profile is defined in the Web.config file and provided as a configuration parameter to the ETW tracking participant.</span></span> <span data-ttu-id="253fb-111">Участник отслеживания трассировки событий Windows настраивается в файле Web.config службы рабочего процесса и применяется к службе как поведение службы.</span><span class="sxs-lookup"><span data-stu-id="253fb-111">The ETW tracking participant is configured in the Web.config file of the workflow service and is applied to the service as a service behavior.</span></span> <span data-ttu-id="253fb-112">В этом образце события отслеживания просматриваются в журнале событий с помощью средства просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="253fb-112">In this sample, you view the tracking events in the event log using Event Viewer.</span></span>

## <a name="workflow-tracking-details"></a><span data-ttu-id="253fb-113">Подробные сведения об отслеживании рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="253fb-113">Workflow Tracking Details</span></span>

<span data-ttu-id="253fb-114">Windows Workflow Foundation предоставляет инфраструктуру отслеживания для отслеживания выполнения экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="253fb-114">Windows Workflow Foundation provides a tracking infrastructure to track the execution of a workflow instance.</span></span> <span data-ttu-id="253fb-115">Среды выполнения отслеживания создает экземпляр рабочего процесса для создания событий, связанных с жизненным циклом рабочего процесса, событиями из действий рабочего процесса и пользовательскими событиями.</span><span class="sxs-lookup"><span data-stu-id="253fb-115">The tracking runtime creates a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom events.</span></span> <span data-ttu-id="253fb-116">В следующих сведениях о таблице подробно описаны основные компоненты инфраструктуры отслеживания.</span><span class="sxs-lookup"><span data-stu-id="253fb-116">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="253fb-117">Компонент</span><span class="sxs-lookup"><span data-stu-id="253fb-117">Component</span></span>|<span data-ttu-id="253fb-118">Описание</span><span class="sxs-lookup"><span data-stu-id="253fb-118">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="253fb-119">Среда выполнения отслеживания</span><span class="sxs-lookup"><span data-stu-id="253fb-119">Tracking runtime</span></span>|<span data-ttu-id="253fb-120">Предоставляет инфраструктуру для передачи записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="253fb-120">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="253fb-121">Участники отслеживания</span><span class="sxs-lookup"><span data-stu-id="253fb-121">Tracking participants</span></span>|<span data-ttu-id="253fb-122">Открывает записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="253fb-122">Accesses the tracking records.</span></span> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] <span data-ttu-id="253fb-123">поставляется с участником отслеживания, который записывает записи отслеживания в виде событий средства трассировки событий для Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="253fb-123">ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="253fb-124">Профиль отслеживания</span><span class="sxs-lookup"><span data-stu-id="253fb-124">Tracking profile</span></span>|<span data-ttu-id="253fb-125">Механизм фильтрации, который позволяет участнику отслеживания подписаться на подмножество записей отслеживания, передаваемых из экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="253fb-125">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

<span data-ttu-id="253fb-126">Следующая таблица содержит подробные сведения о записях отслеживания, создаваемых средой выполнения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="253fb-126">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="253fb-127">Запись отслеживания</span><span class="sxs-lookup"><span data-stu-id="253fb-127">Tracking record</span></span>|<span data-ttu-id="253fb-128">Описание</span><span class="sxs-lookup"><span data-stu-id="253fb-128">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="253fb-129">Записи отслеживания экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="253fb-129">Workflow instance tracking records.</span></span>|<span data-ttu-id="253fb-130">Описывает жизненный цикл экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="253fb-130">Describes the lifecycle of the workflow instance.</span></span> <span data-ttu-id="253fb-131">Например, запись экземпляра создается при запуске и завершении рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="253fb-131">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="253fb-132">Записи отслеживания состояний действия.</span><span class="sxs-lookup"><span data-stu-id="253fb-132">Activity state tracking records.</span></span>|<span data-ttu-id="253fb-133">Подробные сведения о выполнении действия.</span><span class="sxs-lookup"><span data-stu-id="253fb-133">Details activity execution.</span></span> <span data-ttu-id="253fb-134">Эти записи сообщают о состоянии действия рабочего процесса, например о планировании выполнения действия, о завершении действия или о возникновении ошибки.</span><span class="sxs-lookup"><span data-stu-id="253fb-134">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="253fb-135">Запись возобновления закладки.</span><span class="sxs-lookup"><span data-stu-id="253fb-135">Bookmark resumption record.</span></span>|<span data-ttu-id="253fb-136">Создается при возобновлении закладки в экземпляре рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="253fb-136">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="253fb-137">Пользовательские записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="253fb-137">Custom tracking records.</span></span>|<span data-ttu-id="253fb-138">Автор рабочего процесса может создавать настраиваемые записи отслеживания и выдавать их в рамках пользовательской операции.</span><span class="sxs-lookup"><span data-stu-id="253fb-138">A workflow author can create custom tracking records and emit them within the custom activity.</span></span>|
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|<span data-ttu-id="253fb-139">Эта запись создается, когда действие планирует другое действие.</span><span class="sxs-lookup"><span data-stu-id="253fb-139">This record is emitted when an activity schedules another activity.</span></span>|
|<xref:System.Activities.Tracking.FaultPropagationRecord>|<span data-ttu-id="253fb-140">Эта запись создается, когда от действия передается ошибка.</span><span class="sxs-lookup"><span data-stu-id="253fb-140">This record is emitted when a fault is propagated from an activity.</span></span>|
|<xref:System.Activities.Tracking.CancelRequestedRecord>|<span data-ttu-id="253fb-141">Эта запись создается, когда действие отменяется другим действием.</span><span class="sxs-lookup"><span data-stu-id="253fb-141">This record is emitted when an activity is canceled by another activity.</span></span>|

<span data-ttu-id="253fb-142">Участник отслеживания подписывается на часть создаваемых записей отслеживания с помощью профилей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="253fb-142">The tracking participant subscribes for a subset of the emitted tracking records using tracking profiles.</span></span> <span data-ttu-id="253fb-143">Профиль отслеживания содержит запросы отслеживания, которые позволяют подписываться на определенный тип записей отслеживания.</span><span class="sxs-lookup"><span data-stu-id="253fb-143">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="253fb-144">Профили отслеживания можно указывать в коде или в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="253fb-144">Tracking profiles can be specified in code or in configuration.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="253fb-145">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="253fb-145">To use this sample</span></span>

1. <span data-ttu-id="253fb-146">С помощью Visual Studio 2010 откройте файл решения ЕтвтраккингпартиЦипантсампле. sln.</span><span class="sxs-lookup"><span data-stu-id="253fb-146">Using Visual Studio 2010, open the EtwTrackingParticipantSample.sln solution file.</span></span>

2. <span data-ttu-id="253fb-147">Для построения решения нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="253fb-147">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="253fb-148">Чтобы запустить решение, нажмите клавишу F5.</span><span class="sxs-lookup"><span data-stu-id="253fb-148">To run the solution, press F5.</span></span>

    <span data-ttu-id="253fb-149">По умолчанию служба прослушивает порт 53797 ( `http://localhost:53797/SampleWorkflowService.xamlx` ).</span><span class="sxs-lookup"><span data-stu-id="253fb-149">By default, the service is listening on port 53797 (`http://localhost:53797/SampleWorkflowService.xamlx`).</span></span>

4. <span data-ttu-id="253fb-150">В проводнике откройте тестовый клиент WCF.</span><span class="sxs-lookup"><span data-stu-id="253fb-150">Using File Explorer, open the WCF test client.</span></span>

    <span data-ttu-id="253fb-151">Тестовый клиент WCF (WcfTestClient.exe) находится в \<Visual Studio 2010 installation folder> папке \Common7\IDE\</span><span class="sxs-lookup"><span data-stu-id="253fb-151">The WCF test client (WcfTestClient.exe) is located in the \<Visual Studio 2010 installation folder>\Common7\IDE\ folder.</span></span>

    <span data-ttu-id="253fb-152">Папка установки Visual Studio 2010 по умолчанию — C:\Program Files\Microsoft Visual Studio 10,0.</span><span class="sxs-lookup"><span data-stu-id="253fb-152">The default Visual Studio 2010 installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>

5. <span data-ttu-id="253fb-153">В тестовом клиенте WCF выберите **Добавить службу** в меню **файл** .</span><span class="sxs-lookup"><span data-stu-id="253fb-153">In WCF test client, select **Add Service** from the **File** menu.</span></span>

    <span data-ttu-id="253fb-154">Добавьте адрес конечной точки в поле ввода.</span><span class="sxs-lookup"><span data-stu-id="253fb-154">Add the endpoint address in the input box.</span></span> <span data-ttu-id="253fb-155">Значение по умолчанию — `http://localhost:53797/SampleWorkflowService.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="253fb-155">The default is `http://localhost:53797/SampleWorkflowService.xamlx`.</span></span>

6. <span data-ttu-id="253fb-156">Откройте приложение просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="253fb-156">Open the Event Viewer application.</span></span>

    <span data-ttu-id="253fb-157">Перед вызовом службы запустите Просмотр событий из меню **Пуск** , выберите пункт **выполнить** и введите в `eventvwr.exe` .</span><span class="sxs-lookup"><span data-stu-id="253fb-157">Before invoking the service, start Event Viewer from the **Start** menu, select **Run** and type in `eventvwr.exe`.</span></span> <span data-ttu-id="253fb-158">Убедитесь, что журнал событий прослушивает события отслеживания, создаваемые службой рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="253fb-158">Ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>

7. <span data-ttu-id="253fb-159">В древовидном представлении Просмотр событий перейдите к **Просмотр событий**, **журналы приложений и служб** и **Майкрософт**.</span><span class="sxs-lookup"><span data-stu-id="253fb-159">In the tree view of the Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="253fb-160">Щелкните правой кнопкой мыши **Майкрософт** и выберите пункт **Просмотр** , а затем **Показать журналы аналитики и отладки** , чтобы включить журналы аналитики и отладки.</span><span class="sxs-lookup"><span data-stu-id="253fb-160">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs** to enable the analytic and debug logs</span></span>

    <span data-ttu-id="253fb-161">Убедитесь, что установлен флажок **отображать журналы аналитики и отладки** .</span><span class="sxs-lookup"><span data-stu-id="253fb-161">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

8. <span data-ttu-id="253fb-162">В древовидном представлении в Просмотр событий перейдите к **Просмотр событий**, **журналы приложений и служб**, **Microsoft**, **Windows**, **сервер приложений — приложения**.</span><span class="sxs-lookup"><span data-stu-id="253fb-162">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="253fb-163">Щелкните правой кнопкой мыши **аналитика** и выберите **Включить журнал** , чтобы включить **аналитический** журнал.</span><span class="sxs-lookup"><span data-stu-id="253fb-163">Right-click **Analytic** and select **Enable Log** to enable the **Analytic** log.</span></span>

9. <span data-ttu-id="253fb-164">Проверьте службу с помощью тестового клиента WCF, дважды щелкнув `GetData`.</span><span class="sxs-lookup"><span data-stu-id="253fb-164">Test the service using the WCF test client by double-clicking `GetData`.</span></span>

    <span data-ttu-id="253fb-165">Откроется метод `GetData`.</span><span class="sxs-lookup"><span data-stu-id="253fb-165">This opens the `GetData` method.</span></span> <span data-ttu-id="253fb-166">Запрос принимает один параметр и проверяет, равно ли значение 0 (значение по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="253fb-166">The request accepts one parameter and ensures that the value is 0, which is the default.</span></span>

     <span data-ttu-id="253fb-167">Нажмите кнопку **вызвать**.</span><span class="sxs-lookup"><span data-stu-id="253fb-167">Click **Invoke**.</span></span>

10. <span data-ttu-id="253fb-168">Просмотрите события, переданные из рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="253fb-168">Observe the events emitted from the workflow.</span></span>

    <span data-ttu-id="253fb-169">Вернитесь к Просмотр событий и перейдите в раздел **Просмотр событий**, **журналы приложений и служб**, **Microsoft**, **Windows**, **сервер приложений — приложения**.</span><span class="sxs-lookup"><span data-stu-id="253fb-169">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="253fb-170">Щелкните правой кнопкой мыши **аналитика** и выберите **Обновить**.</span><span class="sxs-lookup"><span data-stu-id="253fb-170">Right-click **Analytic** and select **Refresh**.</span></span>

    <span data-ttu-id="253fb-171">События рабочего процесса отображаются в средстве просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="253fb-171">The workflow events are displayed in the event viewer.</span></span> <span data-ttu-id="253fb-172">Обратите внимание, что отображаются события выполнения рабочего процесса и одно из них является необработанным исключением, соответствующим ошибке в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="253fb-172">Notice that workflow execution events are displayed and that one of them is an unhandled exception that corresponds to the error in workflow.</span></span> <span data-ttu-id="253fb-173">Кроме того, действие рабочего процесса создает событие предупреждения, указывающее, какое действие выдало ошибку.</span><span class="sxs-lookup"><span data-stu-id="253fb-173">Also, a warning event is emitted from the workflow activity, which indicates that the activity is throwing a fault.</span></span>

11. <span data-ttu-id="253fb-174">Повторите шаги 9 и 10, введя данные, отличные от 0, чтобы ошибка не появлялась.</span><span class="sxs-lookup"><span data-stu-id="253fb-174">Repeat steps 9 and 10 with an input of data other than 0, so that no error is thrown.</span></span>

<span data-ttu-id="253fb-175">Профили отслеживания позволяют подписаться на события, создаваемые средой выполнения при изменении состояния экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="253fb-175">Tracking profiles allow you to subscribe to events that are emitted by the runtime when the state of a workflow instance changes.</span></span> <span data-ttu-id="253fb-176">Исходя из потребностей, можно создать профиль с низкой детализацией, который будет подписан на небольшой набор изменений состояния высокого уровня в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="253fb-176">Depending on your monitoring requirements, you can create a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="253fb-177">В то же время можно создать очень точный профиль, выходные данные которого будут достаточно полными для последующей реконструкции выполнения.</span><span class="sxs-lookup"><span data-stu-id="253fb-177">On the other hand, you can create a very precise profile whose output is rich enough to reconstruct the execution later.</span></span> <span data-ttu-id="253fb-178">Образец демонстрирует события, создаваемые средой выполнения рабочего процесса для трассировки событий Windows с помощью `HealthMonitoring Tracking Profile`, создающего небольшой набор событий.</span><span class="sxs-lookup"><span data-stu-id="253fb-178">The sample demonstrates the events emitted from the workflow runtime to ETW using the `HealthMonitoring Tracking Profile`, which emits a small set of events.</span></span> <span data-ttu-id="253fb-179">В файле Web.config имеется другой профиль, создающий больше событий отслеживания, он называется `Troubleshooting Tracking Profile`.</span><span class="sxs-lookup"><span data-stu-id="253fb-179">A different profile that emits more workflow tracking events is also provided in the Web.config that is named `Troubleshooting Tracking Profile`.</span></span> <span data-ttu-id="253fb-180">При установке [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] в файле Machine.config настраивается профиль по умолчанию с пустым именем.</span><span class="sxs-lookup"><span data-stu-id="253fb-180">When the [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] is installed, a default profile with an empty name is configured in the Machine.config file.</span></span> <span data-ttu-id="253fb-181">Этот профиль используется конфигурацией поведения отслеживания ETW при отсутствии имени профиля или при задании пустого имени.</span><span class="sxs-lookup"><span data-stu-id="253fb-181">This profile is used by the ETW tracking behavior configuration when no profile name or an empty profile name is specified.</span></span>

<span data-ttu-id="253fb-182">Профиль отслеживания мониторинга работоспособности создает записи экземпляра рабочего процесса и записи распространения ошибок действий.</span><span class="sxs-lookup"><span data-stu-id="253fb-182">The health monitoring tracking profile emits workflow instance records and activity fault propagation records.</span></span> <span data-ttu-id="253fb-183">Этот профиль создается путем добавления следующего профиля отслеживания в файл конфигурации Web.config.</span><span class="sxs-lookup"><span data-stu-id="253fb-183">This profile is created by adding the following tracking profile to a Web.config configuration file.</span></span>

```xml
<tracking>
  <profiles>
    <trackingProfile name="HealthMonitoring Tracking Profile">
      <workflow activityDefinitionId="*">
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Started"/>
              <state name="Completed"/>
              <state name="Aborted"/>
              <state name="UnhandledException"/>
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

 <span data-ttu-id="253fb-184">Профиль может быть изменен путем изменения конфигурации `EtwTrackingParticipant` на следующую.</span><span class="sxs-lookup"><span data-stu-id="253fb-184">The profile can be changed by changing the `EtwTrackingParticipant` configuration to the following.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <etwTracking profileName="HealthMonitoring Tracking Profile"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

#### <a name="to-clean-up-optional"></a><span data-ttu-id="253fb-185">Очистка (необязательно)</span><span class="sxs-lookup"><span data-stu-id="253fb-185">To clean up (Optional)</span></span>

1. <span data-ttu-id="253fb-186">Откройте средство просмотра событий.</span><span class="sxs-lookup"><span data-stu-id="253fb-186">Open Event Viewer.</span></span>

2. <span data-ttu-id="253fb-187">Перейдите в раздел **Просмотр событий**, **журналы приложений и служб**, **Microsoft**, **Windows**, **сервер приложений — приложения**.</span><span class="sxs-lookup"><span data-stu-id="253fb-187">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="253fb-188">Щелкните правой кнопкой мыши **аналитика** и выберите **Отключить журнал**.</span><span class="sxs-lookup"><span data-stu-id="253fb-188">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="253fb-189">Перейдите в раздел **Просмотр событий**, **журналы приложений и служб**, **Microsoft**, **Windows**, **сервер приложений — приложения**.</span><span class="sxs-lookup"><span data-stu-id="253fb-189">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="253fb-190">Щелкните правой кнопкой мыши **аналитика** и выберите **Очистить журнал**.</span><span class="sxs-lookup"><span data-stu-id="253fb-190">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="253fb-191">Выберите параметр **clear (очистить** ), чтобы очистить события.</span><span class="sxs-lookup"><span data-stu-id="253fb-191">Choose the **Clear** option to clear the events.</span></span>

## <a name="known-issue"></a><span data-ttu-id="253fb-192">Известная проблема</span><span class="sxs-lookup"><span data-stu-id="253fb-192">Known Issue</span></span>

> [!NOTE]
> <span data-ttu-id="253fb-193">В средстве просмотра событий есть известная проблема, связанная с ошибкой декодирования событий трассировки событий Windows.</span><span class="sxs-lookup"><span data-stu-id="253fb-193">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="253fb-194">Может выводиться следующее сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="253fb-194">You may see an error message that looks like the following.</span></span>
>
> <span data-ttu-id="253fb-195">Не удается найти описание для идентификатора события \<id> из источника Microsoft-Windows-Application Server-Applications.</span><span class="sxs-lookup"><span data-stu-id="253fb-195">The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="253fb-196">Компонент, вызывающий это событие, не установлен на локальном компьютере или установка повреждена.</span><span class="sxs-lookup"><span data-stu-id="253fb-196">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="253fb-197">Вы можете установить или исправить компонент на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="253fb-197">You can install or repair the component on the local computer.</span></span>
>
> <span data-ttu-id="253fb-198">При появлении этой ошибки нажмите кнопку «Обновить» в области действий.</span><span class="sxs-lookup"><span data-stu-id="253fb-198">If you encounter this error, click refresh in the actions pane.</span></span> <span data-ttu-id="253fb-199">Теперь декодирование события должно выполняться правильно.</span><span class="sxs-lookup"><span data-stu-id="253fb-199">The event should now decode properly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="253fb-200">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="253fb-200">The samples may already be installed on your computer.</span></span> <span data-ttu-id="253fb-201">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="253fb-201">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="253fb-202">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="253fb-202">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="253fb-203">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="253fb-203">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`

## <a name="see-also"></a><span data-ttu-id="253fb-204">См. также</span><span class="sxs-lookup"><span data-stu-id="253fb-204">See also</span></span>

- <span data-ttu-id="253fb-205">[Образцы наблюдения за AppFabric](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="253fb-205">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
