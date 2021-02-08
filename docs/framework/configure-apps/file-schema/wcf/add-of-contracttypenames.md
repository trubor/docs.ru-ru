---
description: 'Дополнительные сведения <add> о: <contractTypeNames>'
title: <add> из <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: 0708aa277b4250cb4134a98ddf7af661840981a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804001"
---
# <a name="add-of-contracttypenames"></a><span data-ttu-id="46a8f-103">\<add> из \<contractTypeNames></span><span class="sxs-lookup"><span data-stu-id="46a8f-103">\<add> of \<contractTypeNames></span></span>

<span data-ttu-id="46a8f-104">Элемент конфигурации, указывающий имя контракта искомых служб, а также критерии, обычно используемые при поиске служб.</span><span class="sxs-lookup"><span data-stu-id="46a8f-104">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="46a8f-105">Если указано несколько имен контрактов, будет получен ответ только от конечных точек службы, совпадающих со ВСЕМИ контрактами.</span><span class="sxs-lookup"><span data-stu-id="46a8f-105">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="46a8f-106">Обратите внимание, что в Windows Communication Foundation (WCF) конечная точка может поддерживать только один контракт.</span><span class="sxs-lookup"><span data-stu-id="46a8f-106">Note that in Windows Communication Foundation (WCF), an endpoint can only support one contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<findCriteria>**](findcriteria.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<contractTypeNames>**](contracttypenames.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="46a8f-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="46a8f-107">Syntax</span></span>  
  
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
              <add name="String" namespace="String" />
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46a8f-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="46a8f-108">Attributes and Elements</span></span>  

 <span data-ttu-id="46a8f-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="46a8f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46a8f-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="46a8f-110">Attributes</span></span>  
  
|<span data-ttu-id="46a8f-111">Атрибут</span><span class="sxs-lookup"><span data-stu-id="46a8f-111">Attribute</span></span>|<span data-ttu-id="46a8f-112">Описание</span><span class="sxs-lookup"><span data-stu-id="46a8f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46a8f-113">name</span><span class="sxs-lookup"><span data-stu-id="46a8f-113">name</span></span>|<span data-ttu-id="46a8f-114">Строка, в которой указано имя типа контракта.</span><span class="sxs-lookup"><span data-stu-id="46a8f-114">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="46a8f-115">пространство имен</span><span class="sxs-lookup"><span data-stu-id="46a8f-115">namespace</span></span>|<span data-ttu-id="46a8f-116">Строка, в которой указано пространство имен типа контракта.</span><span class="sxs-lookup"><span data-stu-id="46a8f-116">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46a8f-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="46a8f-117">Child Elements</span></span>  

 <span data-ttu-id="46a8f-118">None</span><span class="sxs-lookup"><span data-stu-id="46a8f-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46a8f-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="46a8f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="46a8f-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="46a8f-120">Element</span></span>|<span data-ttu-id="46a8f-121">Описание</span><span class="sxs-lookup"><span data-stu-id="46a8f-121">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="46a8f-122">Коллекция имен типа контракта.</span><span class="sxs-lookup"><span data-stu-id="46a8f-122">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46a8f-123">См. также</span><span class="sxs-lookup"><span data-stu-id="46a8f-123">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
