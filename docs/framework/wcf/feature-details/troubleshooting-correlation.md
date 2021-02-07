---
description: Дополнительные сведения см. в статье Устранение неполадок корреляции
title: Устранение неполадок корреляции
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: de02017f7a86478147cd12a89c37bb7b5bc89a7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733025"
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="9bef2-103">Устранение неполадок корреляции</span><span class="sxs-lookup"><span data-stu-id="9bef2-103">Troubleshooting Correlation</span></span>

<span data-ttu-id="9bef2-104">Корреляция позволяет сопоставлять сообщения службы рабочего процесса друг с другом и с нужным экземпляром рабочего процесса. Если же корреляция настроена неправильно, то сообщения не будут приниматься и приложения будут работать неправильно.</span><span class="sxs-lookup"><span data-stu-id="9bef2-104">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="9bef2-105">В этом разделе даны общие сведения о нескольких методах устранения неполадок корреляции, а также перечислен ряд распространенных проблем, которые возникают при использовании корреляции.</span><span class="sxs-lookup"><span data-stu-id="9bef2-105">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>

## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="9bef2-106">Обработка события UnknownMessageReceived</span><span class="sxs-lookup"><span data-stu-id="9bef2-106">Handle the UnknownMessageReceived Event</span></span>

 <span data-ttu-id="9bef2-107">Событие <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> происходит, когда служба получает неизвестное сообщение, в том числе сообщение, для которого не удается выполнить корреляцию с существующим экземпляром.</span><span class="sxs-lookup"><span data-stu-id="9bef2-107">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="9bef2-108">Для резидентных служб это событие можно обрабатывать в ведущем приложении.</span><span class="sxs-lookup"><span data-stu-id="9bef2-108">For self-hosted services, this event can be handled in the host application.</span></span>

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 <span data-ttu-id="9bef2-109">Для служб, размещенных на веб-сервере, это событие можно обработать, создав класс, производный от <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory>, и переопределив метод <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bef2-109">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>

```csharp
class CustomFactory : WorkflowServiceHostFactory
{
    protected override WorkflowServiceHost CreateWorkflowServiceHost(Activity activity, Uri[] baseAddresses)
    {
        // Create the WorkflowServiceHost.
        WorkflowServiceHost host = new WorkflowServiceHost(activity, baseAddresses);

        // Handle the UnknownMessageReceived event.
        host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
        {
            Console.WriteLine("Unknown Message Received:");
            Console.WriteLine(e.Message);
        };

        return host;
    }
}
```

 <span data-ttu-id="9bef2-110">Затем этот настраиваемый объект <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> можно указать в файле `svc` для службы.</span><span class="sxs-lookup"><span data-stu-id="9bef2-110">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>

`<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>`

 <span data-ttu-id="9bef2-111">Когда вызывается этот обработчик, сообщение можно получить через свойство <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> объекта <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>. Оно будет выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9bef2-111">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <To s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://localhost:8080/OrderService</To>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
  </s:Header>
  <s:Body>
    <AddItem xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItem>
  </s:Body>
</s:Envelope>
```

 <span data-ttu-id="9bef2-112">Проверка сообщений, передаваемых в обработчик события <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>, может помочь понять, почему не выполнена корреляция сообщения с экземпляром службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="9bef2-112">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="9bef2-113">Использование отслеживания для наблюдения за ходом рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="9bef2-113">Use Tracking to Monitor the Progress of the Workflow</span></span>

 <span data-ttu-id="9bef2-114">Отслеживание позволяет наблюдать за ходом рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="9bef2-114">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="9bef2-115">По умолчанию записи отслеживания создаются для событий жизненного цикла рабочего процесса, событий жизненного цикла действия, распространения ошибок и возобновления закладок.</span><span class="sxs-lookup"><span data-stu-id="9bef2-115">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="9bef2-116">Кроме того, настраиваемые действия могут создавать настраиваемые записи отслеживания.</span><span class="sxs-lookup"><span data-stu-id="9bef2-116">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="9bef2-117">При устранении неполадок корреляции наиболее полезны записи отслеживания действий, записи возобновления закладок и записи распространения ошибок.</span><span class="sxs-lookup"><span data-stu-id="9bef2-117">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="9bef2-118">Записи отслеживания действий позволяют определить текущий ход выполнения рабочего процесса и выявить действие обмена сообщения, которое в данный момент ожидает сообщений.</span><span class="sxs-lookup"><span data-stu-id="9bef2-118">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="9bef2-119">Записи возобновления закладок полезны, поскольку в них указывается, что сообщение получено рабочим процессом, а в записях распространения ошибок регистрируются все ошибки в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="9bef2-119">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="9bef2-120">Чтобы включить отслеживание, укажите нужный объект <xref:System.Activities.Tracking.TrackingParticipant> в свойстве <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> объекта <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="9bef2-120">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="9bef2-121">В следующем примере `ConsoleTrackingParticipant` (из примера [настраиваемого отслеживания](../../windows-workflow-foundation/samples/custom-tracking.md) ) настраивается с помощью профиля отслеживания по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="9bef2-121">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 <span data-ttu-id="9bef2-122">Участник отслеживания, такой как ConsoleTrackingParticipant, удобен для резидентных служб рабочего процесса с окном консоли.</span><span class="sxs-lookup"><span data-stu-id="9bef2-122">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="9bef2-123">Для службы, размещенной в Интернете, следует использовать участника отслеживания, который записывает данные отслеживания в долговременное хранилище, например встроенный <xref:System.Activities.Tracking.EtwTrackingParticipant> или настраиваемый участник отслеживания, который записывает данные в файл.</span><span class="sxs-lookup"><span data-stu-id="9bef2-123">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file.</span></span>

 <span data-ttu-id="9bef2-124">Дополнительные сведения об отслеживании и настройке отслеживания для службы рабочего процесса, размещенной в Интернете, см. в разделе [Отслеживание и трассировка рабочих процессов](../../windows-workflow-foundation/workflow-tracking-and-tracing.md), [Настройка отслеживания для рабочего процесса](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md), а также [примеры отслеживания &#91;WF&#93;](../../windows-workflow-foundation/samples/tracking.md) Samples.</span><span class="sxs-lookup"><span data-stu-id="9bef2-124">For more information about tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../windows-workflow-foundation/samples/tracking.md) samples.</span></span>

## <a name="use-wcf-tracing"></a><span data-ttu-id="9bef2-125">Использование трассировки WCF</span><span class="sxs-lookup"><span data-stu-id="9bef2-125">Use WCF Tracing</span></span>

 <span data-ttu-id="9bef2-126">Трассировка WCF отслеживает поток входящих и исходящих сообщений для службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="9bef2-126">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="9bef2-127">Данные такой трассировки удобны при устранении неполадок корреляции, особенно для корреляции по содержимому.</span><span class="sxs-lookup"><span data-stu-id="9bef2-127">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="9bef2-128">Чтобы включить трассировку, укажите нужные прослушиватели трассировки в разделе `system.diagnostics` файла `web.config` для службы рабочего процесса, размещенной на веб-сервере, или файла `app.config` для резидентной службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="9bef2-128">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="9bef2-129">Чтобы включить содержимое сообщений в файл трассировки, укажите значение `true` для атрибута `logEntireMessage` в элементе `messageLogging` в разделе `diagnostics` объекта `system.serviceModel`.</span><span class="sxs-lookup"><span data-stu-id="9bef2-129">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="9bef2-130">В следующем примере для данных трассировки, включая содержимое сообщений, задается запись в файл с именем `service.svclog`.</span><span class="sxs-lookup"><span data-stu-id="9bef2-130">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.ServiceModel" switchValue="Information" propagateActivity="true">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
      <source name="System.ServiceModel.MessageLogging">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
    </sources>

    <sharedListeners>
      <add name="corr" type="System.Diagnostics.XmlWriterTraceListener" initializeData="c:\logs\service.svclog">
      </add>
    </sharedListeners>
  </system.diagnostics>

  <system.serviceModel>
    <diagnostics>
      <messageLogging logEntireMessage="true" logMalformedMessages="false"
         logMessagesAtServiceLevel="false" logMessagesAtTransportLevel="true" maxSizeOfMessageToLog="2147483647">
      </messageLogging>
    </diagnostics>
  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="9bef2-131">Для просмотра сведений трассировки, содержащихся в `service.svclog` , используется [средство Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="9bef2-131">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="9bef2-132">Оно особенно полезно при устранении неполадок корреляции по содержимому, поскольку можно просматривать содержимое сообщений, точно определять переданные данные и проверять соответствие <xref:System.ServiceModel.CorrelationQuery> для корреляции по содержимому.</span><span class="sxs-lookup"><span data-stu-id="9bef2-132">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> <span data-ttu-id="9bef2-133">Дополнительные сведения о трассировке WCF см. в разделе [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md), [Настройка трассировки](../diagnostics/tracing/configuring-tracing.md)и [Использование трассировки для устранения неполадок в приложении](../diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="9bef2-133">For more information about WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="9bef2-134">Распространенные проблемы корреляции обмена контекстом</span><span class="sxs-lookup"><span data-stu-id="9bef2-134">Common Context Exchange Correlation Issues</span></span>

 <span data-ttu-id="9bef2-135">Для правильной работы некоторых типов корреляции необходимо использовать определенный тип привязки.</span><span class="sxs-lookup"><span data-stu-id="9bef2-135">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="9bef2-136">Примерами служат корреляция по схеме «запрос-ответ», где требуется двусторонняя привязка, такая как <xref:System.ServiceModel.BasicHttpBinding>, и корреляция обмена контекстом, для которой требуется привязка на основе контекста, такая как <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="9bef2-136">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="9bef2-137">Большинство привязок поддерживают двусторонние операции, поэтому проблема совместимости редко возникает для корреляции по схеме «запрос-ответ», однако существует лишь небольшое число привязок на основе контекста, включая <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding> и <xref:System.ServiceModel.NetTcpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="9bef2-137">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="9bef2-138">Если не используется одна из этих привязок, то первый вызов службы рабочего процесса завершится успешно, однако последующие вызовы завершатся ошибкой со следующим исключением <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="9bef2-138">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>

```output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 <span data-ttu-id="9bef2-139">Данные контекста, используемые для корреляции контекста, можно вернуть из <xref:System.ServiceModel.Activities.SendReply> в действие <xref:System.ServiceModel.Activities.Receive>, которое инициализирует корреляцию контекста, если используется двусторонняя операция, или указать в вызывающем объекте в случае односторонней операции.</span><span class="sxs-lookup"><span data-stu-id="9bef2-139">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="9bef2-140">Если контекст не отправляется вызывающим объектом и не возвращается службой рабочего процесса, то при вызове последующей операции будет возвращаться исключение <xref:System.ServiceModel.FaultException>, описанное ранее.</span><span class="sxs-lookup"><span data-stu-id="9bef2-140">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>

## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="9bef2-141">Распространенные проблемы корреляции по схеме «запрос-ответ»</span><span class="sxs-lookup"><span data-stu-id="9bef2-141">Common Request-Reply Correlation Issues</span></span>

 <span data-ttu-id="9bef2-142">Корреляция "запрос-ответ" используется с <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> парой для реализации двусторонней операции в службе рабочего процесса и с <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> парой, которая вызывает двустороннюю операцию в другой веб-службе.</span><span class="sxs-lookup"><span data-stu-id="9bef2-142">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="9bef2-143">При вызове двусторонней операции в службе WCF эта служба может быть традиционной процедурой службы WCF, основанной на коде, или службой рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="9bef2-143">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based WCF service or it can be a workflow service.</span></span> <span data-ttu-id="9bef2-144">Для корреляции «запрос-ответ» необходимо использовать двустороннюю привязку, такую как <xref:System.ServiceModel.BasicHttpBinding>, и операции должны быть двусторонними.</span><span class="sxs-lookup"><span data-stu-id="9bef2-144">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>

 <span data-ttu-id="9bef2-145">Если в службе рабочего процесса параллельно, или пересекается <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> или <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> пары, неявное управление маркерами корреляции, предоставляемое, <xref:System.ServiceModel.Activities.WorkflowServiceHost> может оказаться недостаточно, особенно в сценариях с высокой нагрузкой, и сообщения могут неправильно маршрутизироваться.</span><span class="sxs-lookup"><span data-stu-id="9bef2-145">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="9bef2-146">Чтобы предотвратить эту проблему, рекомендуется всегда явно указывать <xref:System.ServiceModel.Activities.CorrelationHandle> при использовании корреляции «запрос-ответ».</span><span class="sxs-lookup"><span data-stu-id="9bef2-146">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="9bef2-147">При использовании шаблонов **SendAndReceiveReply** и **ReceiveAndSendReply** из раздела Обмен сообщениями **области элементов** в конструкторе рабочих процессов <xref:System.ServiceModel.Activities.CorrelationHandle> по умолчанию явным образом настраивается.</span><span class="sxs-lookup"><span data-stu-id="9bef2-147">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="9bef2-148">Если рабочий процесс создается из программного кода, то дескриптор <xref:System.ServiceModel.Activities.CorrelationHandle> указывается в свойстве <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> первого действия из пары.</span><span class="sxs-lookup"><span data-stu-id="9bef2-148">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="9bef2-149">В следующем примере действие <xref:System.ServiceModel.Activities.Receive> настраивается с явным дескриптором <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A>, указанным в <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="9bef2-149">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>

```csharp
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();

Receive StartOrder = new Receive
{
    CanCreateInstance = true,
    ServiceContractName = OrderContractName,
    OperationName = "StartOrder",
    CorrelationInitializers =
    {
        new RequestReplyCorrelationInitializer
        {
            CorrelationHandle = RRHandle
        }
    }
};

SendReply ReplyToStartOrder = new SendReply
{
    Request = StartOrder,
    Content = ... // Contains the return value, if any.
};

// Construct a workflow using StartOrder and ReplyToStartOrder.
```

 <span data-ttu-id="9bef2-150">Сохраняемость между <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> парой или <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> парой не разрешена.</span><span class="sxs-lookup"><span data-stu-id="9bef2-150">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="9bef2-151">Создается зона несохраняемости, которая существует до завершения обоих действий.</span><span class="sxs-lookup"><span data-stu-id="9bef2-151">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="9bef2-152">Если действие, например действие Delay, находится в этой зоне несохраняемости и вызывает переход рабочего процесса в состояние бездействия, рабочий поток не будет сохранен, даже если узел настроен на сохранение рабочих потоков после их перехода в состояние бездействия.</span><span class="sxs-lookup"><span data-stu-id="9bef2-152">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="9bef2-153">Если действие, например действие Persist, пытается выполнить явное сохранение в зоне несохраняемости, формируется неустранимое исключение, выполнение рабочего процесса прерывается, а вызывающему возвращается исключение <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="9bef2-153">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="9bef2-154">Сообщение о неустранимом исключении: «System.InvalidOperationException: действия Persist не могут содержаться в блоках несохраняемости».</span><span class="sxs-lookup"><span data-stu-id="9bef2-154">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="9bef2-155">Это исключение не возвращается вызывающему, его можно обнаружить, если включено отслеживание.</span><span class="sxs-lookup"><span data-stu-id="9bef2-155">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="9bef2-156">Сообщение об исключении <xref:System.ServiceModel.FaultException>, возвращаемое вызывающему: «Операцию выполнить не удалось, потому что рабочий процесс '5836145b-7da2-49d0-a052-a49162adeab6' завершился».</span><span class="sxs-lookup"><span data-stu-id="9bef2-156">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>

 <span data-ttu-id="9bef2-157">Дополнительные сведения о корреляции запросов и ответов см. в разделе [запрос-ответ](request-reply-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="9bef2-157">For more information about request-reply correlation, see [Request-Reply](request-reply-correlation.md).</span></span>

## <a name="common-content-correlation-issues"></a><span data-ttu-id="9bef2-158">Распространенные проблемы корреляции по содержимому</span><span class="sxs-lookup"><span data-stu-id="9bef2-158">Common Content Correlation Issues</span></span>

 <span data-ttu-id="9bef2-159">Корреляция по содержимому применяется, если служба рабочего процесса получает несколько сообщений, а нужный экземпляр определяется по некоторому фрагменту данных в передаваемых сообщениях.</span><span class="sxs-lookup"><span data-stu-id="9bef2-159">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="9bef2-160">При корреляции по содержимому такие данные в сообщении, например номер заказчика или идентификатор заказа, используются для маршрутизации сообщений в нужный экземпляр рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="9bef2-160">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="9bef2-161">В этом разделе описан ряд распространенных проблем, которые возникают при использовании корреляции по содержимому.</span><span class="sxs-lookup"><span data-stu-id="9bef2-161">This section describes several common issues that may occur when using content-based correlation.</span></span>

### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="9bef2-162">Убедитесь, что определяющие данные уникальны</span><span class="sxs-lookup"><span data-stu-id="9bef2-162">Ensure the Identifying Data Is Unique</span></span>

 <span data-ttu-id="9bef2-163">Данные, используемые для идентификации экземпляра, хэшируются в ключ корреляции.</span><span class="sxs-lookup"><span data-stu-id="9bef2-163">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="9bef2-164">Необходимо обеспечить уникальность данных, используемых для корреляции. В противном случае в хэшированном ключе могут возникнуть конфликты, которые приведут к неправильной маршрутизации сообщений.</span><span class="sxs-lookup"><span data-stu-id="9bef2-164">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="9bef2-165">Например, корреляция на основе только имени заказчика может вызвать конфликт, так как возможно наличие заказчиков с одинаковыми именами.</span><span class="sxs-lookup"><span data-stu-id="9bef2-165">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="9bef2-166">Двоеточие (:) не должно встречаться в данных, используемых для корреляции сообщений, так как оно уже применяется в качестве разделителя ключа и значения в запросе сообщения, формирующих строку, которая затем хэшируется.</span><span class="sxs-lookup"><span data-stu-id="9bef2-166">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="9bef2-167">Если используется сохраняемость, убедитесь, что текущие определяющие данные не используются в ранее сохраненном экземпляре.</span><span class="sxs-lookup"><span data-stu-id="9bef2-167">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="9bef2-168">Эту проблему можно выявить, временно отключив сохраняемость.</span><span class="sxs-lookup"><span data-stu-id="9bef2-168">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="9bef2-169">С помощью трассировки WCF можно просмотреть вычисленный ключ корреляции. Такая трассировка полезна в отладке проблем с ключом корреляции.</span><span class="sxs-lookup"><span data-stu-id="9bef2-169">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>

### <a name="race-conditions"></a><span data-ttu-id="9bef2-170">Конфликты</span><span class="sxs-lookup"><span data-stu-id="9bef2-170">Race Conditions</span></span>

 <span data-ttu-id="9bef2-171">Между получением сообщения службой и инициализацией корреляции проходит некоторое время, в течение которого последующие сообщения будут пропускаться.</span><span class="sxs-lookup"><span data-stu-id="9bef2-171">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="9bef2-172">Если служба рабочего процесса инициализирует корреляцию по содержимому с использованием данных, переданных от клиента через одностороннюю операцию, а вызывающий объект немедленно отправляет последующие сообщения, то такие сообщения будут пропускаться в течение этого интервала.</span><span class="sxs-lookup"><span data-stu-id="9bef2-172">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="9bef2-173">Чтобы избежать этого, используйте для инициализации корреляции двустороннюю операцию или используйте действие <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="9bef2-173">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>

### <a name="correlation-query-issues"></a><span data-ttu-id="9bef2-174">Проблемы с запросами корреляции</span><span class="sxs-lookup"><span data-stu-id="9bef2-174">Correlation Query Issues</span></span>

 <span data-ttu-id="9bef2-175">Запросы корреляции указывают, какие данные в сообщении используются для корреляции сообщения.</span><span class="sxs-lookup"><span data-stu-id="9bef2-175">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="9bef2-176">Эти данные указываются с помощью запроса XPath.</span><span class="sxs-lookup"><span data-stu-id="9bef2-176">This data is specified by using an XPath query.</span></span> <span data-ttu-id="9bef2-177">Если сообщения в службу не доставляются, хотя ошибки не обнаруживаются, то одним из приемов диагностики является указание вместо запроса XPath литерального значения, совпадающего со значением данных сообщения.</span><span class="sxs-lookup"><span data-stu-id="9bef2-177">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="9bef2-178">Чтобы указать литеральное значение, используйте функцию `string`.</span><span class="sxs-lookup"><span data-stu-id="9bef2-178">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="9bef2-179">В следующем примере <xref:System.ServiceModel.MessageQuerySet> настраивается для использования литерального значения `11445` для `OrderId`, а запрос XPath помещается в комментарий.</span><span class="sxs-lookup"><span data-stu-id="9bef2-179">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>

```csharp
MessageQuerySet = new MessageQuerySet
{
    {
        "OrderId",
        //new XPathMessageQuery("sm:body()/tempuri:StartOrderResponse/tempuri:OrderId")
        new XPathMessageQuery("string('11445')")
    }
}
```

 <span data-ttu-id="9bef2-180">Если запрос XPath настроен неправильно, в результате чего данные о корреляции не возвращаются, возвращается ошибка со следующим сообщением: «Запрос корреляции возвратил пустой результирующий набор.</span><span class="sxs-lookup"><span data-stu-id="9bef2-180">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="9bef2-181">Проверьте правильность настройки запросов корреляции для данной конечной точки».</span><span class="sxs-lookup"><span data-stu-id="9bef2-181">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="9bef2-182">Одним из быстрых способов решения этой проблемы является замена запроса XPath на литеральное значение, как описано в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="9bef2-182">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="9bef2-183">Эта проблема может возникнуть при использовании построителя запросов XPath в диалоговых окнах **Добавление инициализаторов корреляции** или **определения CorrelatesOn** , когда служба рабочего процесса использует контракты сообщений.</span><span class="sxs-lookup"><span data-stu-id="9bef2-183">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="9bef2-184">В следующем примере определяется класс контракта сообщения.</span><span class="sxs-lookup"><span data-stu-id="9bef2-184">In the following example, a message contract class is defined.</span></span>

```csharp
[MessageContract]
public class AddItemMessage
{
    [MessageHeader]
    public string CartId;

    [MessageBodyMember]
    public string Item;
}
```

 <span data-ttu-id="9bef2-185">В рабочем процессе этот контракт сообщения используется действием <xref:System.ServiceModel.Activities.Receive>.</span><span class="sxs-lookup"><span data-stu-id="9bef2-185">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="9bef2-186">Идентификатор `CartId` в заголовке сообщения используется для корреляции сообщения с правильным экземпляром.</span><span class="sxs-lookup"><span data-stu-id="9bef2-186">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="9bef2-187">Если запрос XPath, возвращающий идентификатор `CartId`, создается с помощью диалоговых окон корреляции в конструкторе рабочих процессов, формируется следующий неверный запрос XPath.</span><span class="sxs-lookup"><span data-stu-id="9bef2-187">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 <span data-ttu-id="9bef2-188">Этот запрос XPath был бы правильным, если бы действие <xref:System.ServiceModel.Activities.Receive> использовало параметры для данных, но, поскольку оно использует контракт сообщения, запрос является неверным.</span><span class="sxs-lookup"><span data-stu-id="9bef2-188">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="9bef2-189">Следующий запрос XPath является правильным для получения идентификатора `CartId` из заголовка.</span><span class="sxs-lookup"><span data-stu-id="9bef2-189">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>

```
sm:header()/tempuri:CartId
```

<span data-ttu-id="9bef2-190">Это можно проверить, изучив текст сообщения.</span><span class="sxs-lookup"><span data-stu-id="9bef2-190">This can be confirmed by examining the body of the message.</span></span>

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
    <h:CartId xmlns:h="http://tempuri.org/">80c95b41-c98d-4660-a6c1-99412206e54c</h:CartId>
  </s:Header>
  <s:Body>
    <AddItemMessage xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItemMessage>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="9bef2-191">В следующем примере показано действие <xref:System.ServiceModel.Activities.Receive>, настроенное для операции `AddItem`, использующей предыдущий контракт сообщения для получения данных.</span><span class="sxs-lookup"><span data-stu-id="9bef2-191">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="9bef2-192">Запрос XPath настроен правильно.</span><span class="sxs-lookup"><span data-stu-id="9bef2-192">The XPath query is correctly configured.</span></span>

```xaml
<Receive CorrelatesWith="[CCHandle] OperationName="AddItem" ServiceContractName="p:IService">
  <Receive.CorrelatesOn>
    <XPathMessageQuery x:Key="key1">
      <XPathMessageQuery.Namespaces>
        <ssx:XPathMessageContextMarkup>
          <x:String x:Key="xg0">http://schemas.datacontract.org/2004/07/MessageContractWFService</x:String>
        </ssx:XPathMessageContextMarkup>
      </XPathMessageQuery.Namespaces>sm:header()/tempuri:CartId</XPathMessageQuery>
  </Receive.CorrelatesOn>
  <ReceiveMessageContent DeclaredMessageType="m:AddItemMessage">
    <p1:OutArgument x:TypeArguments="m:AddItemMessage">[AddItemMessage]</p1:OutArgument>
  </ReceiveMessageContent>
</Receive>
```
