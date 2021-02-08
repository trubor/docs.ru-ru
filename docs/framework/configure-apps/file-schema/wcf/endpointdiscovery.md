---
description: 'Дополнительные сведения: <endpointDiscovery>'
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 01913de37ae426484d5bb1ff6a815a64302024fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782134"
---
# \<endpointDiscovery>

<span data-ttu-id="ff0d0-102">Указывает различные параметры обнаружения для конечной точки, такие как возможность обнаружения, области и любые пользовательские модули для ее метаданных.</span><span class="sxs-lookup"><span data-stu-id="ff0d0-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="ff0d0-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ff0d0-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff0d0-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ff0d0-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ff0d0-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ff0d0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff0d0-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ff0d0-106">Attributes</span></span>  
  
|<span data-ttu-id="ff0d0-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ff0d0-107">Attribute</span></span>|<span data-ttu-id="ff0d0-108">Описание</span><span class="sxs-lookup"><span data-stu-id="ff0d0-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff0d0-109">Включено</span><span class="sxs-lookup"><span data-stu-id="ff0d0-109">enabled</span></span>|<span data-ttu-id="ff0d0-110">Логическое значение, указывающее, включена ли возможность обнаружения в этой конечной точке.</span><span class="sxs-lookup"><span data-stu-id="ff0d0-110">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="ff0d0-111">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="ff0d0-111">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff0d0-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ff0d0-112">Child Elements</span></span>  
  
|<span data-ttu-id="ff0d0-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="ff0d0-113">Element</span></span>|<span data-ttu-id="ff0d0-114">Описание</span><span class="sxs-lookup"><span data-stu-id="ff0d0-114">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="ff0d0-115">Коллекция URI областей для этой конечной точки.</span><span class="sxs-lookup"><span data-stu-id="ff0d0-115">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="ff0d0-116">С одной конечной точкой можно связать несколько URI областей.</span><span class="sxs-lookup"><span data-stu-id="ff0d0-116">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="ff0d0-117">[\<extensions>](extensions.md) [из \<endpointDiscovery> ]</span><span class="sxs-lookup"><span data-stu-id="ff0d0-117">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="ff0d0-118">Коллекция элементов XML, позволяющая указывать пользовательские метаданные, публикуемые для конечной точки.</span><span class="sxs-lookup"><span data-stu-id="ff0d0-118">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|\<types>|<span data-ttu-id="ff0d0-119">Коллекция интерфейсов, которые нужно найти.</span><span class="sxs-lookup"><span data-stu-id="ff0d0-119">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff0d0-120">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ff0d0-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ff0d0-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="ff0d0-121">Element</span></span>|<span data-ttu-id="ff0d0-122">Описание</span><span class="sxs-lookup"><span data-stu-id="ff0d0-122">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ff0d0-123">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="ff0d0-123">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="ff0d0-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="ff0d0-124">Remarks</span></span>  

 <span data-ttu-id="ff0d0-125">Если добавить этот элемент конфигурации в конфигурацию поведения конечной точки и присвоить атрибуту `enabled` значение `true`, то будет включена возможность обнаружения.</span><span class="sxs-lookup"><span data-stu-id="ff0d0-125">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="ff0d0-126">Кроме того, можно использовать [\<scopes>](scopes.md) дочерний элемент для указания универсальных кодов ресурсов (URI) настраиваемой области, которые можно использовать для фильтрации конечных точек службы во время запроса, а также [\<extensions>](extensions.md) дочерний элемент для указания пользовательских метаданных, которые должны быть опубликованы вместе со стандартными обнаруживаемыми метаданными (EPR, Контракттипенаме, Биндингнаме, Scope и ListenUri).</span><span class="sxs-lookup"><span data-stu-id="ff0d0-126">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="ff0d0-127">Этот элемент конфигурации зависит от [\<serviceDiscovery>](servicediscovery.md) элемента, который обеспечивает контроль уровня обслуживания для обнаружения.</span><span class="sxs-lookup"><span data-stu-id="ff0d0-127">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="ff0d0-128">Это означает, что параметры этого элемента игнорируются, если они отсутствуют [\<serviceDiscovery>](servicediscovery.md) в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ff0d0-128">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff0d0-129">Пример</span><span class="sxs-lookup"><span data-stu-id="ff0d0-129">Example</span></span>  

 <span data-ttu-id="ff0d0-130">В следующем примере конфигурации определены области фильтрации и метаданные расширения, которые будут опубликованы для конечной точки.</span><span class="sxs-lookup"><span data-stu-id="ff0d0-130">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService"
              behaviorConfiguration="calculatorEndpointBehavior" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery />
    </behavior>
  </serviceBehaviors>
  <endpointBehaviors>
    <behavior name="calculatorEndpointBehavior">
      <endpointDiscovery enabled="true">
        <scopes>
          <add scope="http://contoso/test1" />
          <add scope="http://contoso/test2" />
        </scopes>
        <extensions>
          <e:Publisher xmlns:e="http://example.org">
            <e:Name>The Example Organization</e:Name>
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>
            <e:Contact>support@example.org</e:Contact>
          </e:Publisher>
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>
        </extensions>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="ff0d0-131">См. также</span><span class="sxs-lookup"><span data-stu-id="ff0d0-131">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
