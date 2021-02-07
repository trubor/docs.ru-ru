---
description: 'Дополнительные сведения: <issuedTokenParameters>'
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 92c8f5aa25ddb71561eb702ba3eb0396456008a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725666"
---
# \<issuedTokenParameters>

<span data-ttu-id="629f8-102">Задает параметры маркера безопасности, выданного в федеративном сценарии безопасности.</span><span class="sxs-lookup"><span data-stu-id="629f8-102">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="629f8-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="629f8-103">Syntax</span></span>  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a><span data-ttu-id="629f8-104">Тип</span><span class="sxs-lookup"><span data-stu-id="629f8-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="629f8-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="629f8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="629f8-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="629f8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="629f8-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="629f8-107">Attributes</span></span>  
  
|<span data-ttu-id="629f8-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="629f8-108">Attribute</span></span>|<span data-ttu-id="629f8-109">Описание</span><span class="sxs-lookup"><span data-stu-id="629f8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="629f8-110">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="629f8-110">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="629f8-111">Задает версии спецификаций безопасности (WS-Security, WS-Trust, WS-Secure Conversation и WS-Security Policy), которые должны поддерживаться привязкой.</span><span class="sxs-lookup"><span data-stu-id="629f8-111">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="629f8-112">Это значение имеет тип <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="629f8-112">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="629f8-113">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="629f8-113">inclusionMode</span></span>|<span data-ttu-id="629f8-114">Задает требования включения маркера.</span><span class="sxs-lookup"><span data-stu-id="629f8-114">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="629f8-115">Это атрибут типа <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="629f8-115">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="629f8-116">keySize</span><span class="sxs-lookup"><span data-stu-id="629f8-116">keySize</span></span>|<span data-ttu-id="629f8-117">Целое число, которое задает размер ключа маркера.</span><span class="sxs-lookup"><span data-stu-id="629f8-117">An integer that specifies the token key size.</span></span> <span data-ttu-id="629f8-118">Значение по умолчанию — 256.</span><span class="sxs-lookup"><span data-stu-id="629f8-118">The default value is 256.</span></span>|  
|<span data-ttu-id="629f8-119">keyType</span><span class="sxs-lookup"><span data-stu-id="629f8-119">keyType</span></span>|<span data-ttu-id="629f8-120">Допустимое значение <xref:System.IdentityModel.Tokens.SecurityKeyType>, которое задает тип ключа.</span><span class="sxs-lookup"><span data-stu-id="629f8-120">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="629f8-121">Значение по умолчанию — `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="629f8-121">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="629f8-122">tokenType</span><span class="sxs-lookup"><span data-stu-id="629f8-122">tokenType</span></span>|<span data-ttu-id="629f8-123">Строка, задающая тип маркера.</span><span class="sxs-lookup"><span data-stu-id="629f8-123">A string that specifies the token type.</span></span> <span data-ttu-id="629f8-124">Значение по умолчанию - «http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML».</span><span class="sxs-lookup"><span data-stu-id="629f8-124">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="629f8-125">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="629f8-125">Child Elements</span></span>  
  
|<span data-ttu-id="629f8-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="629f8-126">Element</span></span>|<span data-ttu-id="629f8-127">Описание</span><span class="sxs-lookup"><span data-stu-id="629f8-127">Description</span></span>|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](additionalrequestparameters-element.md)|<span data-ttu-id="629f8-128">Коллекция элементов конфигурации, задающих дополнительные параметры запросов.</span><span class="sxs-lookup"><span data-stu-id="629f8-128">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="629f8-129">Задает коллекцию обязательных типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="629f8-129">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="629f8-130">В федеративном сценарии службы предъявляют требования к входящим учетным данным.</span><span class="sxs-lookup"><span data-stu-id="629f8-130">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="629f8-131">Например, входящие учетные данные должны обладать определенным набором типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="629f8-131">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="629f8-132">Каждый элемент в этой коллекции задает типы обязательных и необязательных утверждений, которые могут появляться в федеративных учетных данных.</span><span class="sxs-lookup"><span data-stu-id="629f8-132">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[\<issuer>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="629f8-133">Элемент конфигурации, задающий конечную точку, выдавшую текущий маркер.</span><span class="sxs-lookup"><span data-stu-id="629f8-133">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[\<issuerMetadata>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="629f8-134">Элемент конфигурации, задающий адрес конечной точки метаданных поставщика маркера.</span><span class="sxs-lookup"><span data-stu-id="629f8-134">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="629f8-135">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="629f8-135">Parent Elements</span></span>  
  
|<span data-ttu-id="629f8-136">Элемент</span><span class="sxs-lookup"><span data-stu-id="629f8-136">Element</span></span>|<span data-ttu-id="629f8-137">Описание</span><span class="sxs-lookup"><span data-stu-id="629f8-137">Description</span></span>|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="629f8-138">Задает значения по умолчанию, используемые для инициализации службы безопасного обмена данными.</span><span class="sxs-lookup"><span data-stu-id="629f8-138">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="629f8-139">Задает параметры безопасности для пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="629f8-139">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="629f8-140">См. также</span><span class="sxs-lookup"><span data-stu-id="629f8-140">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="629f8-141">Привязки</span><span class="sxs-lookup"><span data-stu-id="629f8-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="629f8-142">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="629f8-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="629f8-143">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="629f8-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="629f8-144">Практическое руководство. Создание пользовательской привязки с использованием элемента SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="629f8-144">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="629f8-145">Безопасность пользовательской привязки</span><span class="sxs-lookup"><span data-stu-id="629f8-145">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="629f8-146">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="629f8-146">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="629f8-147">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="629f8-147">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="629f8-148">Возможности безопасности при использовании пользовательских привязок</span><span class="sxs-lookup"><span data-stu-id="629f8-148">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="629f8-149">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="629f8-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
