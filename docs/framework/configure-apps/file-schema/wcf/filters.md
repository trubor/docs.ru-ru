---
description: 'Дополнительные сведения: <filters>'
title: <filters>
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: c66dd07c91e78d1ae6e10790014c3d1b25e5538d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664604"
---
# \<filters>

<span data-ttu-id="5ce2d-102">Элемент `filters` содержит коллекцию фильтров XPath, используемых для отбора сообщений, записываемых в журнал.</span><span class="sxs-lookup"><span data-stu-id="5ce2d-102">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="5ce2d-103">Фильтры применяются только на транспортном уровне, когда параметр `logMessagesAtTransportLevel` имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="5ce2d-103">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="5ce2d-104">Фильтры не влияют на ведение журнала сообщений уровня службы и неправильно сформированных сообщений.</span><span class="sxs-lookup"><span data-stu-id="5ce2d-104">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="5ce2d-105">Для добавления нового фильтра в коллекцию используется ключевое слово `add`.</span><span class="sxs-lookup"><span data-stu-id="5ce2d-105">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="5ce2d-106">Если в файле конфигурации определены один или несколько фильтров, в журнал записываются только сообщения, соответствующие хотя бы одному из фильтров.</span><span class="sxs-lookup"><span data-stu-id="5ce2d-106">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="5ce2d-107">Если фильтры не заданы, в журнал записываются все сообщения.</span><span class="sxs-lookup"><span data-stu-id="5ce2d-107">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="5ce2d-108">Фильтры поддерживают полный синтаксис XPath и применяются в том порядке, в котором они записаны в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5ce2d-108">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="5ce2d-109">Синтаксически неверные фильтры вызывают исключения конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5ce2d-109">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="5ce2d-110">В следующем примере показано, как настроить фильтр для записи только сообщений с разделом заголовка SOAP.</span><span class="sxs-lookup"><span data-stu-id="5ce2d-110">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">
  <filters>
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
      /soap:Envelope/soap:Headers
    </add>
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="5ce2d-111">См. также</span><span class="sxs-lookup"><span data-stu-id="5ce2d-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="5ce2d-112">Настройка ведения журналов сообщений</span><span class="sxs-lookup"><span data-stu-id="5ce2d-112">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
