---
description: 'Дополнительные сведения <add> о: <filters>'
title: <add> из <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 546ff41fddfd8a48e14508e27f09236c67c9abc9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802350"
---
# <a name="add-of-filters"></a><span data-ttu-id="ad989-103">\<add> из \<filters></span><span class="sxs-lookup"><span data-stu-id="ad989-103">\<add> of \<filters></span></span>

<span data-ttu-id="ad989-104">Фильтр XPath, задающий тип сообщений для записи в журнал.</span><span class="sxs-lookup"><span data-stu-id="ad989-104">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ad989-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ad989-105">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad989-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ad989-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ad989-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ad989-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad989-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ad989-108">Attributes</span></span>  
  
|<span data-ttu-id="ad989-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ad989-109">Attribute</span></span>|<span data-ttu-id="ad989-110">Описание</span><span class="sxs-lookup"><span data-stu-id="ad989-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad989-111">фильтр</span><span class="sxs-lookup"><span data-stu-id="ad989-111">filter</span></span>|<span data-ttu-id="ad989-112">Строка, задающая запрос к документу XML, определенный в виде выражения XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="ad989-112">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="ad989-113">Для получения дополнительной информации см. <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="ad989-113">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad989-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ad989-114">Child Elements</span></span>  

 <span data-ttu-id="ad989-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ad989-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad989-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ad989-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ad989-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="ad989-117">Element</span></span>|<span data-ttu-id="ad989-118">Описание</span><span class="sxs-lookup"><span data-stu-id="ad989-118">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters.md)|<span data-ttu-id="ad989-119">Содержит коллекцию фильтров XPath, используемых для контроля типов регистрируемых сообщений.</span><span class="sxs-lookup"><span data-stu-id="ad989-119">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad989-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="ad989-120">Remarks</span></span>  

 <span data-ttu-id="ad989-121">Фильтры применяются только на транспортном уровне, когда параметр `logMessagesAtTransportLevel` имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="ad989-121">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="ad989-122">Фильтры не влияют на ведение журнала сообщений уровня службы и неправильно сформированных сообщений.</span><span class="sxs-lookup"><span data-stu-id="ad989-122">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="ad989-123">Для добавления нового фильтра в коллекцию используется ключевое слово `add`.</span><span class="sxs-lookup"><span data-stu-id="ad989-123">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="ad989-124">Если в файле конфигурации определены один или несколько фильтров, в журнал записываются только сообщения, соответствующие хотя бы одному из фильтров.</span><span class="sxs-lookup"><span data-stu-id="ad989-124">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="ad989-125">Если фильтры не заданы, в журнал записываются все сообщения.</span><span class="sxs-lookup"><span data-stu-id="ad989-125">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="ad989-126">Фильтры поддерживают полный синтаксис XPath и применяются в том порядке, в котором они записаны в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ad989-126">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="ad989-127">Синтаксически неверные фильтры вызывают исключения конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ad989-127">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="ad989-128">В следующем примере показано, как настроить фильтр для записи только сообщений с разделом заголовка SOAP.</span><span class="sxs-lookup"><span data-stu-id="ad989-128">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad989-129">Пример</span><span class="sxs-lookup"><span data-stu-id="ad989-129">Example</span></span>  

 <span data-ttu-id="ad989-130">В следующем примере показано, как настроить фильтр для записи только сообщений с разделом заголовка SOAP.</span><span class="sxs-lookup"><span data-stu-id="ad989-130">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad989-131">См. также</span><span class="sxs-lookup"><span data-stu-id="ad989-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="ad989-132">Настройка ведения журналов сообщений</span><span class="sxs-lookup"><span data-stu-id="ad989-132">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
