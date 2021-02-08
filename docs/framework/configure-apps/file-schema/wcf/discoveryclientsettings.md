---
description: 'Дополнительные сведения: <discoveryClientSettings>'
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: c2fda0dea33ffd6dbca24881eefab2e54e361f92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802298"
---
# \<discoveryClientSettings>

<span data-ttu-id="9df94-102">Содержит параметры, необходимые приложению для участия в процессе обнаружения служб в качестве клиента.</span><span class="sxs-lookup"><span data-stu-id="9df94-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="9df94-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9df94-103">Syntax</span></span>  
  
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
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9df94-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="9df94-104">Attributes and Elements</span></span>  

 <span data-ttu-id="9df94-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="9df94-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9df94-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="9df94-106">Attributes</span></span>  
  
|<span data-ttu-id="9df94-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="9df94-107">Attribute</span></span>|<span data-ttu-id="9df94-108">Описание</span><span class="sxs-lookup"><span data-stu-id="9df94-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9df94-109">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="9df94-109">discoveryEndpoint</span></span>|<span data-ttu-id="9df94-110">Строка, содержащая имя конечной точки обнаружения, которая позволяет клиентскому приложению выполнять автоматический поиск необходимой службы и находить ее адрес во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="9df94-110">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9df94-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="9df94-111">Child Elements</span></span>  
  
|<span data-ttu-id="9df94-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="9df94-112">Element</span></span>|<span data-ttu-id="9df94-113">Описание</span><span class="sxs-lookup"><span data-stu-id="9df94-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="9df94-114">Элемент конфигурации, который предоставляет набор критериев, используемых клиентским приложением для поиска службы обнаружения.</span><span class="sxs-lookup"><span data-stu-id="9df94-114">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="9df94-115">Критерии могут быть сгруппированы в критерии поиска (с указанием искомых служб) и критерии прекращения поиска (как долго должен длиться поиск).</span><span class="sxs-lookup"><span data-stu-id="9df94-115">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9df94-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="9df94-116">Parent Elements</span></span>  
  
|<span data-ttu-id="9df94-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="9df94-117">Element</span></span>|<span data-ttu-id="9df94-118">Описание</span><span class="sxs-lookup"><span data-stu-id="9df94-118">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="9df94-119">Определяет стандартную конечную точку, сведения которой позволяют приложению работать в качестве клиентской программы, динамически ищущей адрес конечной точки во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="9df94-119">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9df94-120">См. также</span><span class="sxs-lookup"><span data-stu-id="9df94-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
