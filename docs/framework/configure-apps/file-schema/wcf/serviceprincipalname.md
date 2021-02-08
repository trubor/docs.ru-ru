---
description: 'Дополнительные сведения: <servicePrincipalName>'
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 494368f1f47f10aac8009e47a9219966c87e5eda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786698"
---
# \<servicePrincipalName>

<span data-ttu-id="09377-102">Указывает идентификацию службы по имени субъекта-службы (SPN).</span><span class="sxs-lookup"><span data-stu-id="09377-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="09377-103">Дополнительные сведения о настройке имени субъекта-службы см. в статье [удостоверение службы и проверка подлинности](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="09377-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="09377-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="09377-104">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09377-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="09377-105">Attributes and Elements</span></span>  

 <span data-ttu-id="09377-106">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="09377-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09377-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="09377-107">Attributes</span></span>  
  
|<span data-ttu-id="09377-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="09377-108">Attribute</span></span>|<span data-ttu-id="09377-109">Описание</span><span class="sxs-lookup"><span data-stu-id="09377-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09377-110">value</span><span class="sxs-lookup"><span data-stu-id="09377-110">value</span></span>|<span data-ttu-id="09377-111">Имя, по которому клиент однозначно определяет экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="09377-111">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="09377-112">Если на компьютерах в лесу установлено несколько экземпляров службы, то каждый экземпляр должен иметь свое имя участника-службы.</span><span class="sxs-lookup"><span data-stu-id="09377-112">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="09377-113">Каждый экземпляр службы может иметь несколько имен участников-служб при наличии нескольких имен, которые могут использоваться клиентами для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="09377-113">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09377-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="09377-114">Child Elements</span></span>  

 <span data-ttu-id="09377-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="09377-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09377-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="09377-116">Parent Elements</span></span>  
  
|<span data-ttu-id="09377-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="09377-117">Element</span></span>|<span data-ttu-id="09377-118">Описание</span><span class="sxs-lookup"><span data-stu-id="09377-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="09377-119">Задает удостоверение службы, подлинность которой должна быть проверена клиентом.</span><span class="sxs-lookup"><span data-stu-id="09377-119">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09377-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="09377-120">Remarks</span></span>  

 <span data-ttu-id="09377-121">Клиент Secure Windows Communication Foundation (WCF), который подключается к конечной точке с этим удостоверением, использует имя субъекта-службы при выполнении проверки подлинности SSPI с конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="09377-121">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09377-122">См. также</span><span class="sxs-lookup"><span data-stu-id="09377-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="09377-123">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="09377-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
