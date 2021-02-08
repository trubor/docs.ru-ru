---
description: 'Дополнительные сведения <add> о: <authorizationPolicies>'
title: <add> из <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 616f09abfad51f41348b0ffa8557a4fd54492437
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804105"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="b89db-103">\<add> из \<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="b89db-103">\<add> of \<authorizationPolicies></span></span>

<span data-ttu-id="b89db-104">Задает политику авторизации для преобразования требований.</span><span class="sxs-lookup"><span data-stu-id="b89db-104">Specifies an authorization policy for claim transformation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="b89db-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b89db-105">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="b89db-106">Тип</span><span class="sxs-lookup"><span data-stu-id="b89db-106">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b89db-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b89db-107">Attributes and Elements</span></span>  

 <span data-ttu-id="b89db-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b89db-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b89db-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b89db-109">Attributes</span></span>  
  
|<span data-ttu-id="b89db-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b89db-110">Attribute</span></span>|<span data-ttu-id="b89db-111">Описание</span><span class="sxs-lookup"><span data-stu-id="b89db-111">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="b89db-112">Обязательный строковый атрибут.</span><span class="sxs-lookup"><span data-stu-id="b89db-112">A required String attribute.</span></span><br /><br /> <span data-ttu-id="b89db-113">Модель управления доступом Windows Communication Foundation (WCF) поддерживает подготовку набора политик авторизации в качестве типов.</span><span class="sxs-lookup"><span data-stu-id="b89db-113">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="b89db-114">Данный атрибут определяет политику авторизации, которая позволяет преобразовывать один набор входных требований в другой набор требований.</span><span class="sxs-lookup"><span data-stu-id="b89db-114">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="b89db-115">В зависимости от этого может быть предоставлено управление доступом или отказано в предоставлении управления доступом.</span><span class="sxs-lookup"><span data-stu-id="b89db-115">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b89db-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b89db-116">Child Elements</span></span>  

 <span data-ttu-id="b89db-117">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b89db-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b89db-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b89db-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b89db-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="b89db-119">Element</span></span>|<span data-ttu-id="b89db-120">Описание</span><span class="sxs-lookup"><span data-stu-id="b89db-120">Description</span></span>|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|<span data-ttu-id="b89db-121">Задает коллекцию типов политики авторизации.</span><span class="sxs-lookup"><span data-stu-id="b89db-121">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b89db-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="b89db-122">Remarks</span></span>  

 <span data-ttu-id="b89db-123">Каждая политика авторизации содержит один обязательный атрибут `policyType`, который имеет строковый тип.</span><span class="sxs-lookup"><span data-stu-id="b89db-123">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="b89db-124">Данный атрибут определяет политику авторизации, которая позволяет преобразовывать один набор входных требований в другой набор требований.</span><span class="sxs-lookup"><span data-stu-id="b89db-124">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="b89db-125">В зависимости от этого может быть предоставлено управление доступом или отказано в предоставлении управления доступом.</span><span class="sxs-lookup"><span data-stu-id="b89db-125">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="b89db-126">Дополнительные сведения о принципах работы политики авторизации см. в разделе <xref:System.IdentityModel.Policy.IAuthorizationPolicy> и [Политика авторизации](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="b89db-126">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b89db-127">См. также</span><span class="sxs-lookup"><span data-stu-id="b89db-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="b89db-128">Авторизация доступа к операциям службы</span><span class="sxs-lookup"><span data-stu-id="b89db-128">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="b89db-129">Практическое руководство. Создание пользовательского диспетчера авторизации для службы</span><span class="sxs-lookup"><span data-stu-id="b89db-129">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="b89db-130">Политика авторизации</span><span class="sxs-lookup"><span data-stu-id="b89db-130">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
