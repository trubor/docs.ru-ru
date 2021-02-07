---
description: 'Дополнительные сведения: <userPrincipalName>'
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 73ace3d6f3d5cb88f2630a4a2ae319decf420021
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664422"
---
# \<userPrincipalName>

<span data-ttu-id="61871-102">Задает имя участника-пользователя (UPN) для службы, подлинность которой должна быть проверена клиентом.</span><span class="sxs-lookup"><span data-stu-id="61871-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="61871-103">Дополнительные сведения о настройке имени участника-пользователя см. в статье [удостоверение службы и проверка подлинности](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="61871-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="61871-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="61871-104">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61871-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="61871-105">Attributes and Elements</span></span>  

 <span data-ttu-id="61871-106">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="61871-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61871-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="61871-107">Attributes</span></span>  
  
|<span data-ttu-id="61871-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="61871-108">Attribute</span></span>|<span data-ttu-id="61871-109">Описание</span><span class="sxs-lookup"><span data-stu-id="61871-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61871-110">value</span><span class="sxs-lookup"><span data-stu-id="61871-110">value</span></span>|<span data-ttu-id="61871-111">Имя учетной записи пользователя (которая иногда называется именем входа пользователя) и имя домена, которое определяет домен, в котором располагается учетная запись пользователя.</span><span class="sxs-lookup"><span data-stu-id="61871-111">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="61871-112">Это стандартный способ входа в домен Windows.</span><span class="sxs-lookup"><span data-stu-id="61871-112">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="61871-113">Формат: someone@example.com (как для адреса электронной почты).</span><span class="sxs-lookup"><span data-stu-id="61871-113">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61871-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="61871-114">Child Elements</span></span>  

 <span data-ttu-id="61871-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="61871-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61871-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="61871-116">Parent Elements</span></span>  
  
|<span data-ttu-id="61871-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="61871-117">Element</span></span>|<span data-ttu-id="61871-118">Описание</span><span class="sxs-lookup"><span data-stu-id="61871-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="61871-119">Задает удостоверение службы, подлинность которой должна быть проверена клиентом.</span><span class="sxs-lookup"><span data-stu-id="61871-119">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61871-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="61871-120">Remarks</span></span>  

 <span data-ttu-id="61871-121">Клиент Secure Windows Communication Foundation (WCF), который подключается к конечной точке с этим удостоверением, использует имя участника-пользователя при выполнении проверки подлинности SSPI с конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="61871-121">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61871-122">Пример</span><span class="sxs-lookup"><span data-stu-id="61871-122">Example</span></span>  

 <span data-ttu-id="61871-123">Приводимый ниже код конфигурации задает имя участника-пользователя (UPN) для службы, подлинность которой должна быть проверена клиентом.</span><span class="sxs-lookup"><span data-stu-id="61871-123">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="61871-124">См. также</span><span class="sxs-lookup"><span data-stu-id="61871-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="61871-125">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="61871-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
