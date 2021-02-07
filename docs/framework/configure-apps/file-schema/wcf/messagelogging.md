---
description: 'Дополнительные сведения: <messageLogging>'
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: e26a616bb7974a8fbad9a7f920a28e06422e09c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749289"
---
# \<messageLogging>

<span data-ttu-id="50492-102">Данный элемент определяет параметры ведения журнала сообщений для Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="50492-102">This element defines the settings for the message-logging capabilities of Windows Communication Foundation (WCF).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageLogging>**  
  
## <a name="syntax"></a><span data-ttu-id="50492-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="50492-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50492-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="50492-104">Attributes and Elements</span></span>  

 <span data-ttu-id="50492-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="50492-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50492-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="50492-106">Attributes</span></span>  
  
|<span data-ttu-id="50492-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="50492-107">Attribute</span></span>|<span data-ttu-id="50492-108">Описание</span><span class="sxs-lookup"><span data-stu-id="50492-108">Description</span></span>|  
|---------------|-----------------|  
|`logEntireMessage`|<span data-ttu-id="50492-109">Логическое значение, указывающее, заносится ли в журнал сообщение целиком (тело и заголовок сообщения).</span><span class="sxs-lookup"><span data-stu-id="50492-109">A Boolean value that specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="50492-110">Значением по умолчанию является `false`, означающее, что в журнал заносится только заголовок сообщения.</span><span class="sxs-lookup"><span data-stu-id="50492-110">The default is `false`, which means that only the message header is logged.</span></span> <span data-ttu-id="50492-111">Действие этого параметра распространяется на все уровни ведения журнала сообщений (службы, транспорта и неправильных сообщений).</span><span class="sxs-lookup"><span data-stu-id="50492-111">This setting affects all message logging levels (service, transport, and malformed).</span></span>|  
|`logMalformedMessages`|<span data-ttu-id="50492-112">Логическое значение, указывающее, заносятся ли в журнал неправильные сообщения.</span><span class="sxs-lookup"><span data-stu-id="50492-112">A Boolean value that specifies whether malformed messages are logged.</span></span> <span data-ttu-id="50492-113">Такие сообщения не учитываются в значении `maxMessagesToLog`.</span><span class="sxs-lookup"><span data-stu-id="50492-113">Malformed messages do not count toward the `maxMessagesToLog`.</span></span> <span data-ttu-id="50492-114">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="50492-114">The default is `false`.</span></span>|  
|`logMessagesAtServiceLevel`|<span data-ttu-id="50492-115">Логическое значение, указывающее, трассируются ли сообщения на уровне службы (перед шифрованием и преобразованиями, связанными с транспортом).</span><span class="sxs-lookup"><span data-stu-id="50492-115">A Boolean value that specifies whether messages are traced at the service level (before encryption- and transport-related transforms).</span></span> <span data-ttu-id="50492-116">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="50492-116">The default is `false`.</span></span>|  
|`logMessagesAtTransportLevel`|<span data-ttu-id="50492-117">Логическое значение, указывающее, трассируются ли сообщения на уровне транспорта.</span><span class="sxs-lookup"><span data-stu-id="50492-117">A Boolean value that specifies whether messages are traced at the transport level.</span></span> <span data-ttu-id="50492-118">Применяются все фильтры, указанные в файле конфигурации, и трассируются только те сообщения, которые соответствуют данным фильтрам.</span><span class="sxs-lookup"><span data-stu-id="50492-118">Any filters specified in the config file are applied, and only messages that match the filters are traced.</span></span> <span data-ttu-id="50492-119">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="50492-119">The default is `false`.</span></span>|  
|`maxMessagesToLog`|<span data-ttu-id="50492-120">Положительное целое число, указывающее максимальное количество сообщений для внесения в журнал.</span><span class="sxs-lookup"><span data-stu-id="50492-120">A positive integer that specifies the maximum number of messages to log.</span></span> <span data-ttu-id="50492-121">Значение по умолчанию — 1000.</span><span class="sxs-lookup"><span data-stu-id="50492-121">The default is 1000.</span></span>|  
|`maxSizeOfMessageToLog`|<span data-ttu-id="50492-122">Положительное целое число, указывающее максимальный размер сообщения для внесения в журнал (в байтах).</span><span class="sxs-lookup"><span data-stu-id="50492-122">A positive integer that specifies the maximum size, in bytes, of a message to log.</span></span> <span data-ttu-id="50492-123">Сообщения, размер которых превышает данное ограничение, в журнал не вносятся.</span><span class="sxs-lookup"><span data-stu-id="50492-123">Messages larger than the limit will not be logged.</span></span> <span data-ttu-id="50492-124">Действие этого параметра распространяется на все уровни трассировки.</span><span class="sxs-lookup"><span data-stu-id="50492-124">This setting affects all trace levels.</span></span> <span data-ttu-id="50492-125">Значение по умолчанию - 262 144 (0x4000).</span><span class="sxs-lookup"><span data-stu-id="50492-125">The default is 262144(0x4000).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50492-126">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="50492-126">Child Elements</span></span>  
  
|<span data-ttu-id="50492-127">Элемент</span><span class="sxs-lookup"><span data-stu-id="50492-127">Element</span></span>|<span data-ttu-id="50492-128">Описание</span><span class="sxs-lookup"><span data-stu-id="50492-128">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50492-129">filters</span><span class="sxs-lookup"><span data-stu-id="50492-129">filters</span></span>|<span data-ttu-id="50492-130">Элемент `filters` содержит коллекцию фильтров XPath.</span><span class="sxs-lookup"><span data-stu-id="50492-130">The `filters` element holds a collection of XPath filters.</span></span> <span data-ttu-id="50492-131">Если включена регистрация сообщений на уровне транспорта (то есть атрибуту `logMessagesAtTransportLevel` присвоено значение `true`), в журнал заносятся только те сообщения, которые соответствуют фильтрам.</span><span class="sxs-lookup"><span data-stu-id="50492-131">When transport message logging is enabled (`logMessagesAtTransportLevel` is `true`), only messages matching the filters will be logged.</span></span><br /><br /> <span data-ttu-id="50492-132">Фильтры применяются только на уровне транспорта.</span><span class="sxs-lookup"><span data-stu-id="50492-132">Filters are applied only at the transport layer.</span></span> <span data-ttu-id="50492-133">Фильтры не влияют на ведение журнала сообщений уровня службы и неправильно сформированных сообщений.</span><span class="sxs-lookup"><span data-stu-id="50492-133">Service level and malformed message logging are not affected by filters.</span></span><br /><br /> <span data-ttu-id="50492-134">Единственным атрибутом элемента `filter` является XpathFilter.</span><span class="sxs-lookup"><span data-stu-id="50492-134">The only attribute for this element, `filter`, is an XpathFilter.</span></span><br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a><span data-ttu-id="50492-135">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="50492-135">Parent Elements</span></span>  
  
|<span data-ttu-id="50492-136">Элемент</span><span class="sxs-lookup"><span data-stu-id="50492-136">Element</span></span>|<span data-ttu-id="50492-137">Описание</span><span class="sxs-lookup"><span data-stu-id="50492-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50492-138">диагностика</span><span class="sxs-lookup"><span data-stu-id="50492-138">diagnostics</span></span>|<span data-ttu-id="50492-139">Определяет параметры WCF для проверки во время выполнения и управления администратором.</span><span class="sxs-lookup"><span data-stu-id="50492-139">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50492-140">Remarks</span><span class="sxs-lookup"><span data-stu-id="50492-140">Remarks</span></span>  

 <span data-ttu-id="50492-141">Сообщения вносятся в журнал на трех различных уровнях в стеке: сообщения уровня службы, транспорта и неправильные сообщения.</span><span class="sxs-lookup"><span data-stu-id="50492-141">Messages are logged at three different levels in the stack: service, transport, and malformed.</span></span> <span data-ttu-id="50492-142">Активация каждого уровня может происходить отдельно.</span><span class="sxs-lookup"><span data-stu-id="50492-142">Each level can be activated separately.</span></span>  
  
 <span data-ttu-id="50492-143">Фильтры XPath можно добавлять для внесения в журнал отдельных сообщений уровней транспорта и службы.</span><span class="sxs-lookup"><span data-stu-id="50492-143">XPath filters can be added to log specific messages at the transport and service levels.</span></span> <span data-ttu-id="50492-144">Если не определено ни одного фильтра, в журнал вносятся все сообщения.</span><span class="sxs-lookup"><span data-stu-id="50492-144">If no filters are defined, all messages are logged.</span></span> <span data-ttu-id="50492-145">Фильтры применяются только к заголовкам сообщений.</span><span class="sxs-lookup"><span data-stu-id="50492-145">Filters are applied only to the headers of the message.</span></span> <span data-ttu-id="50492-146">Текст сообщения не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="50492-146">The body is ignored.</span></span> <span data-ttu-id="50492-147">WCF игнорирует тело сообщения для повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="50492-147">WCF ignores the message body to improve performance.</span></span> <span data-ttu-id="50492-148">Если требуется применить фильтрацию по содержимому текста сообщения, можно создать пользовательский прослушиватель с фильтром, который будет выполнять эту задачу.</span><span class="sxs-lookup"><span data-stu-id="50492-148">If you want to filter based on the content of the body, you can create a custom listener with a filter that does so.</span></span>  
  
 <span data-ttu-id="50492-149">Чтобы включить трассировку сообщений, необходимо создать прослушиватель трассировки.</span><span class="sxs-lookup"><span data-stu-id="50492-149">You need to create a trace listener to activate message tracing.</span></span> <span data-ttu-id="50492-150">Сам прослушиватель может быть любым прослушивателем, который работает с архитектурой трассировки <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="50492-150">The listener itself can be any listener that works with the <xref:System.Diagnostics> tracing architecture.</span></span> <span data-ttu-id="50492-151">В следующем примере показано создание подобного прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="50492-151">The following example demonstrates how to create such a listener.</span></span>  
  
```xml  
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel"
            switchValue="Verbose">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="ServiceModel Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="MessageLogging Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add initializeData="C:\ItProTools\TraceLog.xml"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="ServiceModel Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
    <add initializeData="C:\ItProTools\MessageLog.log"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="MessageLogging Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
  </sharedListeners>
</system.diagnostics>
```  
  
## <a name="example"></a><span data-ttu-id="50492-152">Пример</span><span class="sxs-lookup"><span data-stu-id="50492-152">Example</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="42"
                maxSizeOfMessageToLog="42">
  <filters>
    <clear />
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="50492-153">См. также</span><span class="sxs-lookup"><span data-stu-id="50492-153">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [<span data-ttu-id="50492-154">Настройка ведения журналов сообщений</span><span class="sxs-lookup"><span data-stu-id="50492-154">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
