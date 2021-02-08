---
description: 'Дополнительные сведения: <rsa>'
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 5e558e608ec1196081166d01415e12fb2c3083b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786880"
---
# \<rsa>

<span data-ttu-id="0d2cc-102">Защищенный клиент WCF, подключающийся к конечной точке с использованием этого удостоверения, проверяет, что среди утверждений, представленных сервером, есть утверждение, содержащее открытый ключ RSA, который используется для конструирования этого удостоверения.</span><span class="sxs-lookup"><span data-stu-id="0d2cc-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**  
  
## <a name="syntax"></a><span data-ttu-id="0d2cc-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0d2cc-103">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d2cc-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0d2cc-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0d2cc-105">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0d2cc-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d2cc-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0d2cc-106">Attributes</span></span>  
  
|<span data-ttu-id="0d2cc-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0d2cc-107">Attribute</span></span>|<span data-ttu-id="0d2cc-108">Описание</span><span class="sxs-lookup"><span data-stu-id="0d2cc-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d2cc-109">value</span><span class="sxs-lookup"><span data-stu-id="0d2cc-109">value</span></span>|<span data-ttu-id="0d2cc-110">Дополнительная строка.</span><span class="sxs-lookup"><span data-stu-id="0d2cc-110">Optional String.</span></span> <span data-ttu-id="0d2cc-111">Значение открытого ключа RSA, с которым происходит сравнение на клиенте.</span><span class="sxs-lookup"><span data-stu-id="0d2cc-111">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d2cc-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0d2cc-112">Child Elements</span></span>  

 <span data-ttu-id="0d2cc-113">None</span><span class="sxs-lookup"><span data-stu-id="0d2cc-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d2cc-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0d2cc-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0d2cc-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="0d2cc-115">Element</span></span>|<span data-ttu-id="0d2cc-116">Описание</span><span class="sxs-lookup"><span data-stu-id="0d2cc-116">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="0d2cc-117">Задает удостоверение службы, подлинность которой должна быть проверена клиентом.</span><span class="sxs-lookup"><span data-stu-id="0d2cc-117">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d2cc-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="0d2cc-118">Remarks</span></span>  

 <span data-ttu-id="0d2cc-119">Проверка RSA дает возможность ограничить проверку подлинности, задействовав один сертификат с использованием его ключа RSA или другого значения ключа RSA, созданного в отдельном порядке.</span><span class="sxs-lookup"><span data-stu-id="0d2cc-119">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="0d2cc-120">Это позволяет выполнить более строгую проверку подлинности конкретного ключа RSA, однако если значение ключа RSA будет изменено, служба больше не будет работать с существующими клиентами.</span><span class="sxs-lookup"><span data-stu-id="0d2cc-120">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="0d2cc-121">Дополнительные сведения об использовании удостоверения для проверки службы для клиента см. в статье [удостоверение службы и проверка подлинности](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0d2cc-121">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d2cc-122">Пример</span><span class="sxs-lookup"><span data-stu-id="0d2cc-122">Example</span></span>  

 <span data-ttu-id="0d2cc-123">В следующем коде конфигурации задается значение открытого ключа сертификата X.509, используемого для проверки подлинности сервера.</span><span class="sxs-lookup"><span data-stu-id="0d2cc-123">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="0d2cc-124">См. также</span><span class="sxs-lookup"><span data-stu-id="0d2cc-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="0d2cc-125">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="0d2cc-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
