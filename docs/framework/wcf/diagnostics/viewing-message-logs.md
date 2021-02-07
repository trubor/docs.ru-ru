---
description: 'Дополнительные сведения: Просмотр журналов сообщений'
title: Просмотр журналов сообщений
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: c640b2c3793839be4a31123701865fa944eaebc8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99758038"
---
# <a name="viewing-message-logs"></a><span data-ttu-id="d13cf-103">Просмотр журналов сообщений</span><span class="sxs-lookup"><span data-stu-id="d13cf-103">Viewing Message Logs</span></span>

<span data-ttu-id="d13cf-104">В этом разделе описывается порядок просмотра журналов сообщений.</span><span class="sxs-lookup"><span data-stu-id="d13cf-104">This topic describes how you can view message logs.</span></span>  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a><span data-ttu-id="d13cf-105">Просмотр журналов сообщений с помощью программы Service Trace Viewer</span><span class="sxs-lookup"><span data-stu-id="d13cf-105">Viewing Message Logs in the Service Trace Viewer</span></span>  

 <span data-ttu-id="d13cf-106">Сообщение будет преобразовано в том виде, в котором оно обрабатывается WCF.</span><span class="sxs-lookup"><span data-stu-id="d13cf-106">A message will be transformed as it is processed by WCF.</span></span> <span data-ttu-id="d13cf-107">Следовательно, заносимое в журнал сообщение отражает только содержимое сообщения в точке его регистрации (записи в журнал), но не содержимое, передаваемое по линии связи.</span><span class="sxs-lookup"><span data-stu-id="d13cf-107">Therefore, a message being logged reflects only the message's content at the point it was logged, not the content on the wire.</span></span>  
  
 <span data-ttu-id="d13cf-108">Поскольку формат записи сообщения в журнал никак не связан с форматом передачи сообщения, в журнал сообщения всегда заносятся в раскодированном виде.</span><span class="sxs-lookup"><span data-stu-id="d13cf-108">Since the output of message logging has no relationship to the transfer format of the message, message logging always outputs the decoded message.</span></span> <span data-ttu-id="d13cf-109">Если ведение журнала сообщений настроено надлежащим образом, все сообщения в журнале должны быть представлены в виде обычного текста.</span><span class="sxs-lookup"><span data-stu-id="d13cf-109">If you have configured message logging properly, any logged message should be in plain text.</span></span> <span data-ttu-id="d13cf-110">Например, на формат (обычный текст) сообщений в журнале никак не влияет использование двоичного кодировщика сообщений.</span><span class="sxs-lookup"><span data-stu-id="d13cf-110">For example, the format (plain text) of the logged messages is not affected by the usage of a binary message encoder.</span></span>  
  
 <span data-ttu-id="d13cf-111">Выходные данные прослушивателя XmlWriterTraceListener представляют собой файл, содержащий последовательность XML-фрагментов.</span><span class="sxs-lookup"><span data-stu-id="d13cf-111">The output of the XmlWriterTraceListener is a file that contains a sequence of XML fragments.</span></span> <span data-ttu-id="d13cf-112">Необходимо иметь в виду, что этот файл не является допустимым файлом XML.</span><span class="sxs-lookup"><span data-stu-id="d13cf-112">You should be aware that the file is not a valid XML file.</span></span> <span data-ttu-id="d13cf-113">Для просмотра файлов журнала сообщений рекомендуется использовать [средство Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="d13cf-113">It is recommended that you use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) to view the message log files.</span></span> <span data-ttu-id="d13cf-114">Дополнительные сведения об использовании этого средства см. в разделе [Использование Service Trace Viewer для просмотра коррелированных трассировок и устранения неполадок](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="d13cf-114">For more information on how to use this tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="d13cf-115">В средстве просмотра трассировки служб сообщения отображаются на вкладке **сообщение** . Сообщения, которые вызывают или связаны с, ошибка обработки выделены желтым (порогом предупреждений) или красным (уровень ошибки) в зависимости от серьезности ошибки.</span><span class="sxs-lookup"><span data-stu-id="d13cf-115">In the Service Trace Viewer, messages are listed in the **Message** tab. Messages that have caused, or are related to, a processing error are highlighted in yellow (warning level) or red (error level), depending on the severity of the error.</span></span> <span data-ttu-id="d13cf-116">При двойном щелчке на сообщении открывается трассировка сообщения в контексте запроса на обработку.</span><span class="sxs-lookup"><span data-stu-id="d13cf-116">Double-clicking on the message brings up the message trace in the context of the processing request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d13cf-117">Если сообщение не имеет заголовка, тег `<header/>` в журнал не записывается.</span><span class="sxs-lookup"><span data-stu-id="d13cf-117">If a message has no header, no `<header/>` tag is logged.</span></span>  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a><span data-ttu-id="d13cf-118">Просмотр сообщений, записанных в журнал клиентом, ретранслятором и службой</span><span class="sxs-lookup"><span data-stu-id="d13cf-118">Viewing Messages Logged by a Client, a Relay, and a Service</span></span>  

 <span data-ttu-id="d13cf-119">Конкретная среда может содержать клиент, который отправляет сообщение ретранслятору, который в свою очередь пересылает сообщение службе.</span><span class="sxs-lookup"><span data-stu-id="d13cf-119">Your environment may contain a client, which sends a message to a relay, that subsequently forwards the message to the service.</span></span> <span data-ttu-id="d13cf-120">Если ведение журнала сообщений включено для всех трех расположений и все три журнала сообщений просматриваются в средстве [Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) одновременно, то обмен сообщениями с журналами сообщений будет отображаться неправильно.</span><span class="sxs-lookup"><span data-stu-id="d13cf-120">When message logging is enabled on all three locations, and all three message logs are viewed in [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) simultaneously, the message log exchanges will be incorrectly rendered.</span></span> <span data-ttu-id="d13cf-121">Это связано с тем, что идентификаторы `CorrelationId` и `ActivityId` в заголовке сообщения не являются уникальными для каждой пары "отправка-получение".</span><span class="sxs-lookup"><span data-stu-id="d13cf-121">This is because the `CorrelationId` and `ActivityId` in the Message header are not unique for every send-receive pair.</span></span>  
  
 <span data-ttu-id="d13cf-122">Решить эту проблему можно одним из следующих способов.</span><span class="sxs-lookup"><span data-stu-id="d13cf-122">You can use either one of the following methods to resolve this problem.</span></span>  
  
- <span data-ttu-id="d13cf-123">Только два из трех журналов сообщений отображаются в [средстве Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) в любое время.</span><span class="sxs-lookup"><span data-stu-id="d13cf-123">Only view two of the three message logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) at any time.</span></span>  
  
- <span data-ttu-id="d13cf-124">Если необходимо просмотреть все три журнала в средстве [Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) одновременно, можно изменить службу ретрансляции, создав новый <xref:System.ServiceModel.Channels.Message> экземпляр.</span><span class="sxs-lookup"><span data-stu-id="d13cf-124">If you must view all three logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) at the same time, you can modify the relay service by creating a new <xref:System.ServiceModel.Channels.Message> instance.</span></span> <span data-ttu-id="d13cf-125">Этот экземпляр должен представлять собой копию тела входящего сообщения плюс все заголовки, за исключением заголовков `ActivityId` и `Action`.</span><span class="sxs-lookup"><span data-stu-id="d13cf-125">This instance should be a copy of the body of the incoming message, plus all the headers except for the `ActivityId` and `Action` headers.</span></span> <span data-ttu-id="d13cf-126">В следующем примере кода показано, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="d13cf-126">The following example code demonstrates how to do this.</span></span>  
  
```csharp
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a><span data-ttu-id="d13cf-127">Исключительные случаи неточного воспроизведения содержимого сообщений в журналах</span><span class="sxs-lookup"><span data-stu-id="d13cf-127">Exceptional Cases for Inaccurate Message Logging Content</span></span>  

 <span data-ttu-id="d13cf-128">В следующих случаях сообщения, записываемые в журнал, могут не соответствовать в точности потоку октетов, передаваемому по линии связи.</span><span class="sxs-lookup"><span data-stu-id="d13cf-128">Under the following conditions, messages being logged might not be the exact representation of the octet stream present on the wire.</span></span>  
  
- <span data-ttu-id="d13cf-129">При использовании привязки BasicHttpBinding в журнал записываются заголовки конвертов входящих сообщений в пространстве имен /addressing/none.</span><span class="sxs-lookup"><span data-stu-id="d13cf-129">For BasicHttpBinding, envelope headers are logged for the incoming messages in the /addressing/none namespace.</span></span>  
  
- <span data-ttu-id="d13cf-130">Пробелы могут быть несовпадающими.</span><span class="sxs-lookup"><span data-stu-id="d13cf-130">White spaces can be mismatched.</span></span>  
  
- <span data-ttu-id="d13cf-131">Пустые элементы во входящих сообщениях могут быть представлены иначе.</span><span class="sxs-lookup"><span data-stu-id="d13cf-131">For incoming messages, empty elements can be represented differently.</span></span> <span data-ttu-id="d13cf-132">Например, \<tag> \</tag> вместо\<tag/></span><span class="sxs-lookup"><span data-stu-id="d13cf-132">For example, \<tag>\</tag> instead of  \<tag/></span></span>  
  
- <span data-ttu-id="d13cf-133">Когда отключена регистрация известных персональных данных (по умолчанию или путем явного задания enableLoggingKnownPii="true").</span><span class="sxs-lookup"><span data-stu-id="d13cf-133">When known PII logging is disabled either by default or explicit setting enableLoggingKnownPii="true".</span></span>  
  
- <span data-ttu-id="d13cf-134">Когда для преобразования в UTF-8 включено кодирование.</span><span class="sxs-lookup"><span data-stu-id="d13cf-134">Encoding is enabled for transforming to UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d13cf-135">См. также</span><span class="sxs-lookup"><span data-stu-id="d13cf-135">See also</span></span>

- [<span data-ttu-id="d13cf-136">Программа Service Trace Viewer (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="d13cf-136">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../service-trace-viewer-tool-svctraceviewer-exe.md)
- [<span data-ttu-id="d13cf-137">Использование программы Service Trace Viewer для просмотра скоррелированных трассировок и устранения неполадок</span><span class="sxs-lookup"><span data-stu-id="d13cf-137">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="d13cf-138">Ведение журналов сообщений</span><span class="sxs-lookup"><span data-stu-id="d13cf-138">Message Logging</span></span>](message-logging.md)
