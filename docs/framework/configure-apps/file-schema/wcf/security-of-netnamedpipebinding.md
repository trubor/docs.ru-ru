---
description: 'Дополнительные сведения <security> о: <netNamedPipeBinding>'
title: <security> из <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: d64917c53390cade00d9e104c8581ce45355ac34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683103"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="fbd4b-103">\<security> из \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="fbd4b-103">\<security> of \<netNamedPipeBinding></span></span>

<span data-ttu-id="fbd4b-104">Определяет параметры безопасности для привязки.</span><span class="sxs-lookup"><span data-stu-id="fbd4b-104">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="fbd4b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fbd4b-105">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbd4b-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fbd4b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fbd4b-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fbd4b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbd4b-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fbd4b-108">Attributes</span></span>  
  
|<span data-ttu-id="fbd4b-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="fbd4b-109">Attribute</span></span>|<span data-ttu-id="fbd4b-110">Описание</span><span class="sxs-lookup"><span data-stu-id="fbd4b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fbd4b-111">mode</span><span class="sxs-lookup"><span data-stu-id="fbd4b-111">mode</span></span>|<span data-ttu-id="fbd4b-112">Задает тип системы безопасности, применяемой к этой привязке.</span><span class="sxs-lookup"><span data-stu-id="fbd4b-112">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="fbd4b-113">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="fbd4b-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fbd4b-114">-None: отключает безопасность.</span><span class="sxs-lookup"><span data-stu-id="fbd4b-114">-   None: This disables security.</span></span><br /><span data-ttu-id="fbd4b-115">-Transport. безопасность обеспечивается с помощью базовой безопасности на основе транспорта.</span><span class="sxs-lookup"><span data-stu-id="fbd4b-115">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="fbd4b-116">Этот режим позволяет контролировать уровень защиты.</span><span class="sxs-lookup"><span data-stu-id="fbd4b-116">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="fbd4b-117">— Значение по умолчанию — Transport.</span><span class="sxs-lookup"><span data-stu-id="fbd4b-117">-   The default value is Transport.</span></span> <span data-ttu-id="fbd4b-118">Это атрибут типа <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="fbd4b-118">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fbd4b-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fbd4b-119">Child Elements</span></span>  
  
|<span data-ttu-id="fbd4b-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="fbd4b-120">Element</span></span>|<span data-ttu-id="fbd4b-121">Описание</span><span class="sxs-lookup"><span data-stu-id="fbd4b-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fbd4b-122">транспорт</span><span class="sxs-lookup"><span data-stu-id="fbd4b-122">transport</span></span>|<span data-ttu-id="fbd4b-123">Определяет параметры безопасности для данного транспорта.</span><span class="sxs-lookup"><span data-stu-id="fbd4b-123">Defines the security settings for the transport.</span></span> <span data-ttu-id="fbd4b-124">Это элемент типа <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="fbd4b-124">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fbd4b-125">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fbd4b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="fbd4b-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="fbd4b-126">Element</span></span>|<span data-ttu-id="fbd4b-127">Описание</span><span class="sxs-lookup"><span data-stu-id="fbd4b-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fbd4b-128">binding</span><span class="sxs-lookup"><span data-stu-id="fbd4b-128">binding</span></span>|<span data-ttu-id="fbd4b-129">Элемент Binding объекта [\<netNamedPipeBinding>](netnamedpipebinding.md) .</span><span class="sxs-lookup"><span data-stu-id="fbd4b-129">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbd4b-130">См. также</span><span class="sxs-lookup"><span data-stu-id="fbd4b-130">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="fbd4b-131">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="fbd4b-131">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fbd4b-132">Выбор типа учетных данных</span><span class="sxs-lookup"><span data-stu-id="fbd4b-132">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="fbd4b-133">Привязки</span><span class="sxs-lookup"><span data-stu-id="fbd4b-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fbd4b-134">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="fbd4b-134">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fbd4b-135">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="fbd4b-135">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
