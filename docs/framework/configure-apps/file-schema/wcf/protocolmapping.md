---
description: 'Дополнительные сведения: <protocolMapping>'
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: defdf3129122212dac9481dc5d8d48a0dfa94d72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786919"
---
# \<protocolMapping>

<span data-ttu-id="6695d-102">Представляет раздел конфигурации, в котором определяется набор сопоставления протоколов по умолчанию между схемами транспортных протоколов (например, http, net.tcp, net.pipe и т. д.) и привязками WCF.</span><span class="sxs-lookup"><span data-stu-id="6695d-102">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="6695d-103">При создании конечных точек по умолчанию во время выполнения Windows Communication Foundation (WCF) рассматривает настроенные сопоставления и решает, какую привязку использовать для конкретного адреса на основе.</span><span class="sxs-lookup"><span data-stu-id="6695d-103">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<protocolMapping>**  
  
## <a name="syntax"></a><span data-ttu-id="6695d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6695d-104">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6695d-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="6695d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6695d-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="6695d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6695d-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="6695d-107">Attributes</span></span>  

 <span data-ttu-id="6695d-108">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="6695d-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6695d-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="6695d-109">Child Elements</span></span>  
  
|<span data-ttu-id="6695d-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="6695d-110">Element</span></span>|<span data-ttu-id="6695d-111">Описание</span><span class="sxs-lookup"><span data-stu-id="6695d-111">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="6695d-112">Содержит сопоставление протокола по умолчанию между схемой транспортного протокола (например http, net.tcp, net.pipe и т. д.) и привязкой WCF.</span><span class="sxs-lookup"><span data-stu-id="6695d-112">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6695d-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="6695d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="6695d-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="6695d-114">Element</span></span>|<span data-ttu-id="6695d-115">Описание</span><span class="sxs-lookup"><span data-stu-id="6695d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="6695d-116">Корневой элемент всех элементов конфигурации WCF.</span><span class="sxs-lookup"><span data-stu-id="6695d-116">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6695d-117">Пример</span><span class="sxs-lookup"><span data-stu-id="6695d-117">Example</span></span>  

 <span data-ttu-id="6695d-118">В следующем примере конфигурации показано сопоставление протокола по умолчанию в файле machine.config.</span><span class="sxs-lookup"><span data-stu-id="6695d-118">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="6695d-119">Это сопоставление по умолчанию можно переопределить на уровне компьютера путем изменения файла machine.config.</span><span class="sxs-lookup"><span data-stu-id="6695d-119">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="6695d-120">Или же, если необходимо переопределить это сопоставление только в области приложения, можно отменить этот раздел в файле конфигурации приложения и изменить сопоставление для отдельных схем протокола.</span><span class="sxs-lookup"><span data-stu-id="6695d-120">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a><span data-ttu-id="6695d-121">См. также</span><span class="sxs-lookup"><span data-stu-id="6695d-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
