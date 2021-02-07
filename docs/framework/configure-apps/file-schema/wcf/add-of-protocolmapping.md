---
description: 'Дополнительные сведения <add> о: <protocolMapping>'
title: <add> из <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 530ef6b2893eb55a979aba2ef7ec21efffc3070a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750251"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="7d609-103">\<add> из \<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="7d609-103">\<add> of \<protocolMapping></span></span>

<span data-ttu-id="7d609-104">Представляет сопоставление протокола по умолчанию между схемой транспортного протокола (например, HTTP, net. TCP, net. pipe и т. д.) и привязкой Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7d609-104">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="7d609-105">При создании конечных точек по умолчанию во время выполнения WCF проверяет настроенные сопоставления и решает, какая привязка будет использоваться для конкретного адреса на основе.</span><span class="sxs-lookup"><span data-stu-id="7d609-105">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<protocolMapping>**](protocolmapping.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="7d609-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7d609-106">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d609-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="7d609-107">Attributes and Elements</span></span>  

 <span data-ttu-id="7d609-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="7d609-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d609-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="7d609-109">Attributes</span></span>  
  
|<span data-ttu-id="7d609-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="7d609-110">Element</span></span>|<span data-ttu-id="7d609-111">Описание</span><span class="sxs-lookup"><span data-stu-id="7d609-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d609-112">binding</span><span class="sxs-lookup"><span data-stu-id="7d609-112">binding</span></span>|<span data-ttu-id="7d609-113">Строка, в которой указан тип привязки, используемый для конечной точки во время создания конечной точки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="7d609-113">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="7d609-114">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="7d609-114">bindingConfiguration</span></span>|<span data-ttu-id="7d609-115">Строка, содержащая имя раздела конфигурации привязки, на который будет установлена ссылка.</span><span class="sxs-lookup"><span data-stu-id="7d609-115">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="7d609-116">схема</span><span class="sxs-lookup"><span data-stu-id="7d609-116">scheme</span></span>|<span data-ttu-id="7d609-117">Схема транспортного протокола, которая будет использоваться для конечной точки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="7d609-117">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d609-118">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="7d609-118">Child Elements</span></span>  

 <span data-ttu-id="7d609-119">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="7d609-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d609-120">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="7d609-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7d609-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="7d609-121">Element</span></span>|<span data-ttu-id="7d609-122">Описание</span><span class="sxs-lookup"><span data-stu-id="7d609-122">Description</span></span>|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="7d609-123">Представляет раздел конфигурации для определения сопоставлений протоколов по умолчанию между схемами транспортного протокола (например, HTTP, net. TCP, net. pipe и т. д.) и привязками Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7d609-123">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7d609-124">Пример</span><span class="sxs-lookup"><span data-stu-id="7d609-124">Example</span></span>  

 <span data-ttu-id="7d609-125">В следующем примере конфигурации показано сопоставление протокола по умолчанию в файле machine.config.</span><span class="sxs-lookup"><span data-stu-id="7d609-125">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="7d609-126">Это сопоставление по умолчанию можно переопределить на уровне компьютера путем изменения файла machine.config.</span><span class="sxs-lookup"><span data-stu-id="7d609-126">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="7d609-127">Или же, если необходимо переопределить это сопоставление только в области приложения, можно отменить этот раздел в файле конфигурации приложения и изменить сопоставление для отдельных схем протокола.</span><span class="sxs-lookup"><span data-stu-id="7d609-127">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7d609-128">См. также</span><span class="sxs-lookup"><span data-stu-id="7d609-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
