---
description: 'Дополнительные сведения <issuerMetadata> о: <issuedTokenParameters>'
title: <issuerMetadata> из <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: 6b0b5064254caf1c6bcf72c2e6d3449402853b98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802246"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="0e7f1-103">\<issuerMetadata> из \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="0e7f1-103">\<issuerMetadata> of \<issuedTokenParameters></span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="0e7f1-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0e7f1-104">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e7f1-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0e7f1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0e7f1-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e7f1-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0e7f1-107">Attributes</span></span>  
  
|<span data-ttu-id="0e7f1-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0e7f1-108">Attribute</span></span>|<span data-ttu-id="0e7f1-109">Описание</span><span class="sxs-lookup"><span data-stu-id="0e7f1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0e7f1-110">address</span><span class="sxs-lookup"><span data-stu-id="0e7f1-110">address</span></span>|<span data-ttu-id="0e7f1-111">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-111">Required.</span></span> <span data-ttu-id="0e7f1-112">Строка, задающая адрес конечной точки.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-112">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="0e7f1-113">Адрес должен быть абсолютным универсальным кодом ресурса (URI).</span><span class="sxs-lookup"><span data-stu-id="0e7f1-113">The address must be an absolute URI.</span></span> <span data-ttu-id="0e7f1-114">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-114">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e7f1-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0e7f1-115">Child Elements</span></span>  
  
|<span data-ttu-id="0e7f1-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="0e7f1-116">Element</span></span>|<span data-ttu-id="0e7f1-117">Описание</span><span class="sxs-lookup"><span data-stu-id="0e7f1-117">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="0e7f1-118">Коллекция заголовков адреса.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-118">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="0e7f1-119">Удостоверение, обеспечивающее проверку подлинности конечной точки другими конечными точками, которые обмениваются с ней сообщениями.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-119">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e7f1-120">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0e7f1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0e7f1-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="0e7f1-121">Element</span></span>|<span data-ttu-id="0e7f1-122">Описание</span><span class="sxs-lookup"><span data-stu-id="0e7f1-122">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="0e7f1-123">Задает параметры маркера безопасности, выданного в федеративном сценарии безопасности.</span><span class="sxs-lookup"><span data-stu-id="0e7f1-123">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e7f1-124">См. также</span><span class="sxs-lookup"><span data-stu-id="0e7f1-124">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0e7f1-125">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="0e7f1-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0e7f1-126">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="0e7f1-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0e7f1-127">Возможности безопасности при использовании пользовательских привязок</span><span class="sxs-lookup"><span data-stu-id="0e7f1-127">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="0e7f1-128">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="0e7f1-128">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0e7f1-129">Привязки</span><span class="sxs-lookup"><span data-stu-id="0e7f1-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0e7f1-130">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="0e7f1-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0e7f1-131">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="0e7f1-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="0e7f1-132">Практическое руководство. Создание пользовательской привязки с использованием элемента SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="0e7f1-132">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="0e7f1-133">Безопасность пользовательской привязки</span><span class="sxs-lookup"><span data-stu-id="0e7f1-133">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
