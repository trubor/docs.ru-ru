---
description: <certificate>Дополнительные сведения о:<identity>
title: <certificate> для <identity>;
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: b1ccda7e8e84825cc0b2b2be123fe30be449189a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639111"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="306a2-103">\<certificate> для \<identity>;</span><span class="sxs-lookup"><span data-stu-id="306a2-103">\<certificate> for \<identity></span></span>

<span data-ttu-id="306a2-104">Задает сертификат X.509, используемый для проверки сервера при подключении к клиенту.</span><span class="sxs-lookup"><span data-stu-id="306a2-104">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="306a2-105">Дополнительные сведения о задании значения элемента см. в разделе [удостоверение службы и проверка подлинности](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="306a2-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="306a2-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="306a2-106">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="306a2-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="306a2-107">Attributes and Elements</span></span>  

 <span data-ttu-id="306a2-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="306a2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="306a2-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="306a2-109">Attributes</span></span>  
  
|<span data-ttu-id="306a2-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="306a2-110">Attribute</span></span>|<span data-ttu-id="306a2-111">Описание</span><span class="sxs-lookup"><span data-stu-id="306a2-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="306a2-112">encodedValue</span><span class="sxs-lookup"><span data-stu-id="306a2-112">encodedValue</span></span>|<span data-ttu-id="306a2-113">Кодировка Base64 сертификата.</span><span class="sxs-lookup"><span data-stu-id="306a2-113">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="306a2-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="306a2-114">Child Elements</span></span>  

 <span data-ttu-id="306a2-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="306a2-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="306a2-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="306a2-116">Parent Elements</span></span>  
  
|<span data-ttu-id="306a2-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="306a2-117">Element</span></span>|<span data-ttu-id="306a2-118">Описание</span><span class="sxs-lookup"><span data-stu-id="306a2-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="306a2-119">Задает удостоверение службы, подлинность которой должна быть проверена клиентом.</span><span class="sxs-lookup"><span data-stu-id="306a2-119">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="306a2-120">Пример</span><span class="sxs-lookup"><span data-stu-id="306a2-120">Example</span></span>  

 <span data-ttu-id="306a2-121">В следующем коде задается кодированное представление сертификата, используемого для проверки сервера при подключении к клиенту.</span><span class="sxs-lookup"><span data-stu-id="306a2-121">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="306a2-122">См. также</span><span class="sxs-lookup"><span data-stu-id="306a2-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="306a2-123">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="306a2-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
