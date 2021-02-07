---
description: 'Дополнительные сведения: <discoveryClient>'
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: d04eee828bb16e56a65c39059665feb745f3006a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754398"
---
# \<discoveryClient>

<span data-ttu-id="d73ca-102">Элемент конфигурации для создания пользовательской привязки, которая позволяет клиентскому приложению автоматически выполнять поиск обнаруживаемой службы и определять ее адрес во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="d73ca-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**  
  
## <a name="syntax"></a><span data-ttu-id="d73ca-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d73ca-103">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d73ca-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d73ca-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d73ca-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d73ca-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d73ca-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d73ca-106">Attributes</span></span>  
  
|<span data-ttu-id="d73ca-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="d73ca-107">Attribute</span></span>|<span data-ttu-id="d73ca-108">Описание</span><span class="sxs-lookup"><span data-stu-id="d73ca-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d73ca-109">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="d73ca-109">discoveryEndpoint</span></span>|<span data-ttu-id="d73ca-110">Строка, содержащая имя конечной точки обнаружения, которая позволяет клиентскому приложению выполнять автоматический поиск необходимой службы и находить ее адрес во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="d73ca-110">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d73ca-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d73ca-111">Child Elements</span></span>  
  
|<span data-ttu-id="d73ca-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="d73ca-112">Element</span></span>|<span data-ttu-id="d73ca-113">Описание</span><span class="sxs-lookup"><span data-stu-id="d73ca-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="d73ca-114">Элемент конфигурации, который предоставляет набор критериев, используемых клиентским приложением для поиска службы обнаружения.</span><span class="sxs-lookup"><span data-stu-id="d73ca-114">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="d73ca-115">Критерии могут быть сгруппированы в критерии поиска (с указанием искомых служб) и критерии прекращения поиска (как долго должен длиться поиск).</span><span class="sxs-lookup"><span data-stu-id="d73ca-115">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d73ca-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d73ca-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d73ca-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="d73ca-117">Element</span></span>|<span data-ttu-id="d73ca-118">Описание</span><span class="sxs-lookup"><span data-stu-id="d73ca-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d73ca-119">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="d73ca-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d73ca-120">См. также</span><span class="sxs-lookup"><span data-stu-id="d73ca-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
