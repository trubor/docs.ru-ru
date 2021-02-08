---
description: 'Дополнительные сведения о: <add> <claimTypeRequirements> element'
title: <add> элемента <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
ms.openlocfilehash: 7ad93c4e1c2379704b38d3cdc68fddca62b3c057
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804040"
---
# <a name="add-of-claimtyperequirements-element"></a><span data-ttu-id="a6663-103">\<add> элемента \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="a6663-103">\<add> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="a6663-104">Задает типы обязательных и необязательных утверждений, которые могут появляться в федеративных учетных данных.</span><span class="sxs-lookup"><span data-stu-id="a6663-104">Specifies the types of required and optional claims expected to appear in the federated credential.</span></span> <span data-ttu-id="a6663-105">Например, службы предъявляют требования к входящим учетным данным, которые должны обладать определенным набором типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="a6663-105">For example, services state the requirements on incoming credentials, which must possess a certain set of claim types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**
  
## <a name="syntax"></a><span data-ttu-id="a6663-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a6663-106">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <add claimType="URI"
       isOptional="Boolean" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6663-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a6663-107">Attributes and Elements</span></span>  

 <span data-ttu-id="a6663-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a6663-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6663-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a6663-109">Attributes</span></span>  
  
|<span data-ttu-id="a6663-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a6663-110">Attribute</span></span>|<span data-ttu-id="a6663-111">Описание</span><span class="sxs-lookup"><span data-stu-id="a6663-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6663-112">claimType</span><span class="sxs-lookup"><span data-stu-id="a6663-112">claimType</span></span>|<span data-ttu-id="a6663-113">Универсальный код ресурса (URI), определяющий тип утверждения.</span><span class="sxs-lookup"><span data-stu-id="a6663-113">A URI that defines the type of a claim.</span></span> <span data-ttu-id="a6663-114">Например, для приобретения товара с веб-узла пользователь должен представить действительную кредитную карту с достаточным кредитным лимитом.</span><span class="sxs-lookup"><span data-stu-id="a6663-114">For example, to purchase a product from a Web site, the user must present a valid credit card with sufficient credit limit.</span></span> <span data-ttu-id="a6663-115">Типом утверждения будет универсальный код ресурса (URI) кредитной карты.</span><span class="sxs-lookup"><span data-stu-id="a6663-115">The claim type would be the credit card URI.</span></span>|  
|<span data-ttu-id="a6663-116">isOptional</span><span class="sxs-lookup"><span data-stu-id="a6663-116">isOptional</span></span>|<span data-ttu-id="a6663-117">Логическое значение, указывающее, является ли утверждение необязательным.</span><span class="sxs-lookup"><span data-stu-id="a6663-117">A Boolean value that specifies if this is for an optional claim.</span></span> <span data-ttu-id="a6663-118">Если утверждение является обязательным, установите для этого атрибута значение `false`.</span><span class="sxs-lookup"><span data-stu-id="a6663-118">Set this attribute to `false` if this is a required claim.</span></span><br /><br /> <span data-ttu-id="a6663-119">Этот атрибут можно использовать, если служба запрашивает определенные данные, но они не являются необходимыми.</span><span class="sxs-lookup"><span data-stu-id="a6663-119">You can use this attribute when the service asks for some information but does not require it.</span></span> <span data-ttu-id="a6663-120">Например, если требуется, чтобы пользователь вводил имя, фамилию и адрес, но решите, что номер телефона является необязательным.</span><span class="sxs-lookup"><span data-stu-id="a6663-120">For example, if you require the user to enter their first name, last name, and address, but decide that phone number is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6663-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a6663-121">Child Elements</span></span>  

 <span data-ttu-id="a6663-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="a6663-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6663-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a6663-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a6663-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="a6663-124">Element</span></span>|<span data-ttu-id="a6663-125">Описание</span><span class="sxs-lookup"><span data-stu-id="a6663-125">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="a6663-126">Задает коллекцию обязательных типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="a6663-126">Specifies a collection of required claim types.</span></span> <span data-ttu-id="a6663-127">Каждый элемент имеет тип <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="a6663-127">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="a6663-128">В федеративном сценарии службы предъявляют требования к входящим учетным данным.</span><span class="sxs-lookup"><span data-stu-id="a6663-128">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="a6663-129">Например, входящие учетные данные должны обладать определенным набором типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="a6663-129">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="a6663-130">Каждый элемент в этой коллекции задает типы обязательных и необязательных утверждений, которые могут появляться в федеративных учетных данных.</span><span class="sxs-lookup"><span data-stu-id="a6663-130">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6663-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="a6663-131">Remarks</span></span>  

 <span data-ttu-id="a6663-132">В федеративном сценарии службы предъявляют требования к входящим учетным данным.</span><span class="sxs-lookup"><span data-stu-id="a6663-132">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="a6663-133">Например, входящие учетные данные должны обладать определенным набором типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="a6663-133">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="a6663-134">Это требование представлено в политике безопасности.</span><span class="sxs-lookup"><span data-stu-id="a6663-134">This requirement is manifested in a security policy.</span></span> <span data-ttu-id="a6663-135">Когда клиент запрашивает учетные данные в федеративной службе (например, CardSpace), требования помещаются в запрос маркера (RequestSecurityToken), что позволяет федеративной службе выдать учетные данные, полностью отвечающие требованиям.</span><span class="sxs-lookup"><span data-stu-id="a6663-135">When a client requests credentials from a federated service (for example, CardSpace), it puts the requirements into a token request (RequestSecurityToken) so that the federated service can issue the credentials that satisfy the requirements accordingly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6663-136">Пример</span><span class="sxs-lookup"><span data-stu-id="a6663-136">Example</span></span>  

 <span data-ttu-id="a6663-137">Следующая конфигурация добавляет два требования типа утверждения к привязке безопасности.</span><span class="sxs-lookup"><span data-stu-id="a6663-137">The following configuration adds two claim type requirements to a security binding.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="myFederatedBinding">
      <security mode="Message">
        <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">
          <claimTypeRequirements>
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress" />
            <add claimType="http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"
                 optional="true" />
          </claimTypeRequirements>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="a6663-138">См. также</span><span class="sxs-lookup"><span data-stu-id="a6663-138">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
