---
description: 'Дополнительные сведения: <dns>'
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: a5c0601a027c72b4d6307261793bd5725979db92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803897"
---
# \<dns>

<span data-ttu-id="fe298-102">Задает ожидаемое удостоверение сервера.</span><span class="sxs-lookup"><span data-stu-id="fe298-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="fe298-103">Удостоверение является действительным для режима проверки подлинности сертификата X509, если сертификат сервера содержит DNS с тем же самым значением.</span><span class="sxs-lookup"><span data-stu-id="fe298-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="fe298-104">Оно также действительно для режима проверки подлинности Windows, если SPN имеет такое же значение.</span><span class="sxs-lookup"><span data-stu-id="fe298-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="fe298-105">Дополнительные сведения о задании значения элемента см. в разделе [удостоверение службы и проверка подлинности](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fe298-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**  
  
## <a name="syntax"></a><span data-ttu-id="fe298-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fe298-106">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe298-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fe298-107">Attributes and Elements</span></span>  

 <span data-ttu-id="fe298-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fe298-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe298-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fe298-109">Attributes</span></span>  
  
|<span data-ttu-id="fe298-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="fe298-110">Attribute</span></span>|<span data-ttu-id="fe298-111">Описание</span><span class="sxs-lookup"><span data-stu-id="fe298-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe298-112">value</span><span class="sxs-lookup"><span data-stu-id="fe298-112">value</span></span>|<span data-ttu-id="fe298-113">Сервер DNS сертификата.</span><span class="sxs-lookup"><span data-stu-id="fe298-113">The DNS of the certificate.</span></span> <span data-ttu-id="fe298-114">Протокол DNS - это отраслевой протокол, используемый для нахождения компьютеров в сетях, использующих протокол IP.</span><span class="sxs-lookup"><span data-stu-id="fe298-114">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="fe298-115">Пользователи могут запоминать отображаемые имена, например `https://go.microsoft.com/fwlink/?prd=10929` или `https://go.microsoft.com/fwlink/?LinkID=96165` , проще, чем адреса на основе чисел, например 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="fe298-115">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe298-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fe298-116">Child Elements</span></span>  

 <span data-ttu-id="fe298-117">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="fe298-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe298-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fe298-118">Parent Elements</span></span>  
  
|<span data-ttu-id="fe298-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="fe298-119">Element</span></span>|<span data-ttu-id="fe298-120">Описание</span><span class="sxs-lookup"><span data-stu-id="fe298-120">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="fe298-121">Задает удостоверение службы, подлинность которой должна быть проверена клиентом.</span><span class="sxs-lookup"><span data-stu-id="fe298-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fe298-122">Пример</span><span class="sxs-lookup"><span data-stu-id="fe298-122">Example</span></span>  

 <span data-ttu-id="fe298-123">В следующем коде конфигурации задается значение сервера DNS сертификата X.509, используемого для проверки подлинности сервера.</span><span class="sxs-lookup"><span data-stu-id="fe298-123">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="fe298-124">См. также</span><span class="sxs-lookup"><span data-stu-id="fe298-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="fe298-125">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="fe298-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
