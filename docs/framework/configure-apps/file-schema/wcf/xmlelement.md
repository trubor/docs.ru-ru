---
description: 'Дополнительные сведения: <xmlElement>'
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 891f1a95c1f6a79127d48a1572bc805574225530
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682011"
---
# \<xmlElement>

<span data-ttu-id="f0407-102">Указывает элемент XML, отправляемый в тексте сообщения службе маркеров безопасности при запросе маркера.</span><span class="sxs-lookup"><span data-stu-id="f0407-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="f0407-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f0407-103">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0407-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="f0407-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f0407-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f0407-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0407-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f0407-106">Attributes</span></span>  
  
|<span data-ttu-id="f0407-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="f0407-107">Attribute</span></span>|<span data-ttu-id="f0407-108">Описание</span><span class="sxs-lookup"><span data-stu-id="f0407-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0407-109">xmlElement</span><span class="sxs-lookup"><span data-stu-id="f0407-109">xmlElement</span></span>|<span data-ttu-id="f0407-110">Строка, указывающая элемент XML, который отправляется в тексте сообщения службе маркеров безопасности при запросе маркера.</span><span class="sxs-lookup"><span data-stu-id="f0407-110">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0407-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f0407-111">Child Elements</span></span>  

 <span data-ttu-id="f0407-112">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="f0407-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0407-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f0407-113">Parent Elements</span></span>  
  
|<span data-ttu-id="f0407-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="f0407-114">Element</span></span>|<span data-ttu-id="f0407-115">Описание</span><span class="sxs-lookup"><span data-stu-id="f0407-115">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="f0407-116">Коллекция параметров запроса маркера.</span><span class="sxs-lookup"><span data-stu-id="f0407-116">A collection of token request parameters.</span></span> <span data-ttu-id="f0407-117">Каждый параметр представляет собой элемент XML.</span><span class="sxs-lookup"><span data-stu-id="f0407-117">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0407-118">См. также</span><span class="sxs-lookup"><span data-stu-id="f0407-118">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="f0407-119">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="f0407-119">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="f0407-120">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="f0407-120">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="f0407-121">Возможности безопасности при использовании пользовательских привязок</span><span class="sxs-lookup"><span data-stu-id="f0407-121">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="f0407-122">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="f0407-122">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="f0407-123">Привязки</span><span class="sxs-lookup"><span data-stu-id="f0407-123">Bindings</span></span>](../../../wcf/bindings.md)
