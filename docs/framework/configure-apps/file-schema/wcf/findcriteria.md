---
description: 'Дополнительные сведения: <findCriteria>'
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 6415dfd4614122ac361fd7d5b872f840b01734f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767951"
---
# \<findCriteria>

<span data-ttu-id="899a2-102">Элемент конфигурации, который предоставляет набор критериев, используемых клиентским приложением для поиска службы обнаружения.</span><span class="sxs-lookup"><span data-stu-id="899a2-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="899a2-103">Критерии могут быть сгруппированы в критерии поиска (с указанием искомых служб) и критерии прекращения поиска (как долго должен длиться поиск).</span><span class="sxs-lookup"><span data-stu-id="899a2-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<findCriteria>**  
  
## <a name="syntax"></a><span data-ttu-id="899a2-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="899a2-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            </contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="899a2-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="899a2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="899a2-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="899a2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="899a2-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="899a2-107">Attributes</span></span>  
  
|<span data-ttu-id="899a2-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="899a2-108">Attribute</span></span>|<span data-ttu-id="899a2-109">Описание</span><span class="sxs-lookup"><span data-stu-id="899a2-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="899a2-110">длительность</span><span class="sxs-lookup"><span data-stu-id="899a2-110">duration</span></span>|<span data-ttu-id="899a2-111">Значение Timespan, указывающее максимальное время ожидания ответа от служб в сети.</span><span class="sxs-lookup"><span data-stu-id="899a2-111">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="899a2-112">Значение времени ожидания по умолчанию - 20 секунд.</span><span class="sxs-lookup"><span data-stu-id="899a2-112">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="899a2-113">maxResults</span><span class="sxs-lookup"><span data-stu-id="899a2-113">maxResults</span></span>|<span data-ttu-id="899a2-114">Целочисленное значение, указывающее максимальное количество ответов, ожидаемых от служб по сети или через Интернет.</span><span class="sxs-lookup"><span data-stu-id="899a2-114">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="899a2-115">Операция поиска завершается, если максимальное число ответов достигнуто до истечения срока, указанного в атрибуте `duration`.</span><span class="sxs-lookup"><span data-stu-id="899a2-115">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="899a2-116">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="899a2-116">scopeMatchBy</span></span>|<span data-ttu-id="899a2-117">URI, указывающий алгоритм сопоставления, который используется для сопоставления областей из сообщения зонда с областями из конечной точки.</span><span class="sxs-lookup"><span data-stu-id="899a2-117">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="899a2-118">Поддерживаются пять правил сопоставления областей.</span><span class="sxs-lookup"><span data-stu-id="899a2-118">There are five supported scope-matching rules.</span></span> <span data-ttu-id="899a2-119">Если правило сопоставления областей не указано, используется `ScopeMatchByPrefix`.</span><span class="sxs-lookup"><span data-stu-id="899a2-119">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="899a2-120">Дополнительные сведения см. в разделе <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="899a2-120">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="899a2-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="899a2-121">Child Elements</span></span>  
  
|<span data-ttu-id="899a2-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="899a2-122">Element</span></span>|<span data-ttu-id="899a2-123">Описание</span><span class="sxs-lookup"><span data-stu-id="899a2-123">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="899a2-124">Коллекция элементов конфигурации, содержащих имена типов контрактов службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="899a2-124">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="899a2-125">\<extensions> из \<findCriteria></span><span class="sxs-lookup"><span data-stu-id="899a2-125">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="899a2-126">Коллекция объектов элементов XML, предоставляющих расширения.</span><span class="sxs-lookup"><span data-stu-id="899a2-126">A collection of XML element objects that provide extensions.</span></span>|  
|[\<scopes>](scopes.md)|<span data-ttu-id="899a2-127">Коллекция объектов, содержащих абсолютные URI, по которым определяется расположение отдельных служб в ходе операции поиска.</span><span class="sxs-lookup"><span data-stu-id="899a2-127">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="899a2-128">Если найдена определенная служба, URI службы и URI области были успешно сопоставлены, иногда с помощью правил области, предназначенных для преодоления сложностей совпадения.</span><span class="sxs-lookup"><span data-stu-id="899a2-128">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="899a2-129">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="899a2-129">Parent Elements</span></span>  
  
|<span data-ttu-id="899a2-130">Элемент</span><span class="sxs-lookup"><span data-stu-id="899a2-130">Element</span></span>|<span data-ttu-id="899a2-131">Описание</span><span class="sxs-lookup"><span data-stu-id="899a2-131">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="899a2-132">Содержит параметры, необходимые приложению для участия в процессе обнаружения служб в качестве клиента.</span><span class="sxs-lookup"><span data-stu-id="899a2-132">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="899a2-133">См. также</span><span class="sxs-lookup"><span data-stu-id="899a2-133">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
