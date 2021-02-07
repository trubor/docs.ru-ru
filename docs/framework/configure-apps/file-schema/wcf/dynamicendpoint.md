---
description: 'Дополнительные сведения: <dynamicEndpoint>'
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: 0fe30492e1daeecca5e27aef844f5f6977396049
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725900"
---
# \<dynamicEndpoint>

<span data-ttu-id="0bb1c-102">Этот элемент конфигурации определяет стандартную конечную точку, содержащую сведения, позволяющие приложению работать в качестве клиентской программы, которая может найти адрес конечной точки динамически во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0bb1c-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="0bb1c-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0bb1c-103">Syntax</span></span>  
  
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
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bb1c-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0bb1c-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0bb1c-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0bb1c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bb1c-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0bb1c-106">Attributes</span></span>  

 <span data-ttu-id="0bb1c-107">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="0bb1c-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0bb1c-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0bb1c-108">Child Elements</span></span>  
  
|<span data-ttu-id="0bb1c-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="0bb1c-109">Element</span></span>|<span data-ttu-id="0bb1c-110">Описание</span><span class="sxs-lookup"><span data-stu-id="0bb1c-110">Description</span></span>|  
|-------------|-----------------|  
|[\<discoveryClientSettings>](discoveryclientsettings.md)|<span data-ttu-id="0bb1c-111">Содержит параметры, необходимые приложению для участия в процессе обнаружения служб в качестве клиента.</span><span class="sxs-lookup"><span data-stu-id="0bb1c-111">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0bb1c-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0bb1c-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0bb1c-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="0bb1c-113">Element</span></span>|<span data-ttu-id="0bb1c-114">Описание</span><span class="sxs-lookup"><span data-stu-id="0bb1c-114">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="0bb1c-115">Коллекция стандартных конечных точек, одно или несколько свойств которых (адрес, привязка, контракт) являются фиксированными.</span><span class="sxs-lookup"><span data-stu-id="0bb1c-115">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0bb1c-116">См. также</span><span class="sxs-lookup"><span data-stu-id="0bb1c-116">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
