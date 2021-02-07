---
description: 'Дополнительные сведения <issuer> о: <issuedTokenParameters>'
title: <issuer> из <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 7d67583eda22414750631b6dff40f6e6ea8831e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725653"
---
# <a name="issuer-of-issuedtokenparameters"></a><span data-ttu-id="fb735-103">\<issuer> из \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="fb735-103">\<issuer> of \<issuedTokenParameters></span></span>

<span data-ttu-id="fb735-104">Задает службу маркеров безопасности, выдающую маркеры безопасности.</span><span class="sxs-lookup"><span data-stu-id="fb735-104">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="fb735-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fb735-105">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb735-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fb735-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fb735-107">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fb735-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb735-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fb735-108">Attributes</span></span>  
  
|<span data-ttu-id="fb735-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="fb735-109">Attribute</span></span>|<span data-ttu-id="fb735-110">Описание</span><span class="sxs-lookup"><span data-stu-id="fb735-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fb735-111">address</span><span class="sxs-lookup"><span data-stu-id="fb735-111">address</span></span>|<span data-ttu-id="fb735-112">Обязательная строка.</span><span class="sxs-lookup"><span data-stu-id="fb735-112">Required string.</span></span> <span data-ttu-id="fb735-113">URL-адрес для службы маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="fb735-113">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb735-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fb735-114">Child Elements</span></span>  
  
|<span data-ttu-id="fb735-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="fb735-115">Element</span></span>|<span data-ttu-id="fb735-116">Описание</span><span class="sxs-lookup"><span data-stu-id="fb735-116">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="fb735-117">Коллекция заголовков адресов для конечных точек, которые может создать конструктор.</span><span class="sxs-lookup"><span data-stu-id="fb735-117">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="fb735-118">При использовании выданного маркера задает параметры, позволяющие клиенту проверить подлинность сервера.</span><span class="sxs-lookup"><span data-stu-id="fb735-118">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb735-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fb735-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fb735-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="fb735-120">Element</span></span>|<span data-ttu-id="fb735-121">Описание</span><span class="sxs-lookup"><span data-stu-id="fb735-121">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="fb735-122">Определяет текущий выданный маркер.</span><span class="sxs-lookup"><span data-stu-id="fb735-122">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb735-123">См. также</span><span class="sxs-lookup"><span data-stu-id="fb735-123">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="fb735-124">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="fb735-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="fb735-125">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="fb735-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="fb735-126">Возможности безопасности при использовании пользовательских привязок</span><span class="sxs-lookup"><span data-stu-id="fb735-126">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="fb735-127">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="fb735-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="fb735-128">Привязки</span><span class="sxs-lookup"><span data-stu-id="fb735-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fb735-129">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="fb735-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fb735-130">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="fb735-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="fb735-131">Практическое руководство. Создание пользовательской привязки с использованием элемента SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="fb735-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="fb735-132">Безопасность пользовательской привязки</span><span class="sxs-lookup"><span data-stu-id="fb735-132">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
