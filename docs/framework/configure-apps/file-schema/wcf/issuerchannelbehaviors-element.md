---
description: 'Дополнительные сведения о: <issuerChannelBehaviors> element'
title: Элемент <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
no-loc:
- <system.serviceModel>
- <behaviors>
- <endpointBehaviors>
- <behavior>
- <clientCredentials>
- <issuedToken>
- <issuerChannelBehaviors>
- <dataContractSerializer>
ms.openlocfilehash: 6be79f2ee6afb442a7a399ce49df4ad59dff2db5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725549"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="f5f26-103">\::: No-Loc ( <issuerChannelBehaviors> )::: элемент</span><span class="sxs-lookup"><span data-stu-id="f5f26-103">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="f5f26-104">Содержит коллекцию поведений конечной точки клиента Windows Communication Foundation (WCF) (определенную в конфигурации) для использования при взаимодействии с указанными службами маркеров службы.</span><span class="sxs-lookup"><span data-stu-id="f5f26-104">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="f5f26-105">Определенные поведения не могут содержать элементы [ \: :: No-Loc ( <clientCredentials> ):::](clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="f5f26-105">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

[\<configuration>](../configuration-element.md)\
<span data-ttu-id="f5f26-106">&nbsp;&nbsp;[\::: No-Loc (<System. serviceModel>):::](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f5f26-106">&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)</span></span>\
<span data-ttu-id="f5f26-107">&nbsp;&nbsp;&nbsp;&nbsp;[\::: No-Loc ( <behaviors> ):::](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f5f26-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)</span></span>\
<span data-ttu-id="f5f26-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: No-Loc ( <endpointBehaviors> ):::](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f5f26-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)</span></span>\
<span data-ttu-id="f5f26-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: No-Loc ( <behavior> ):::](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f5f26-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="f5f26-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: No-Loc ( <clientCredentials> ):::](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="f5f26-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)</span></span>\
<span data-ttu-id="f5f26-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\::: No-Loc ( <issuedToken> ):::](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="f5f26-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)</span></span>\
<span data-ttu-id="f5f26-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\::: No-Loc ( <issuerChannelBehaviors> ):::</span><span class="sxs-lookup"><span data-stu-id="f5f26-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors></span></span>

## <a name="syntax"></a><span data-ttu-id="f5f26-113">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f5f26-113">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5f26-114">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="f5f26-114">Attributes and elements</span></span>

<span data-ttu-id="f5f26-115">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f5f26-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5f26-116">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f5f26-116">Attributes</span></span>

<span data-ttu-id="f5f26-117">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="f5f26-117">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f5f26-118">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f5f26-118">Child elements</span></span>

|<span data-ttu-id="f5f26-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="f5f26-119">Element</span></span>|<span data-ttu-id="f5f26-120">Описание</span><span class="sxs-lookup"><span data-stu-id="f5f26-120">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="f5f26-121">Добавляет поведение в коллекцию.</span><span class="sxs-lookup"><span data-stu-id="f5f26-121">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f5f26-122">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f5f26-122">Parent elements</span></span>

|<span data-ttu-id="f5f26-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="f5f26-123">Element</span></span>|<span data-ttu-id="f5f26-124">Описание</span><span class="sxs-lookup"><span data-stu-id="f5f26-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5f26-125">\::: No-Loc ( <issuedToken> ):::</span><span class="sxs-lookup"><span data-stu-id="f5f26-125">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="f5f26-126">Задает пользовательский маркер, используемый для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="f5f26-126">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f5f26-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="f5f26-127">Remarks</span></span>

<span data-ttu-id="f5f26-128">Этот элемент используется, когда для связи со службой необходимо любое поведение (кроме поведений, в которые включаются элементы `<clientCredentials>`).</span><span class="sxs-lookup"><span data-stu-id="f5f26-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="f5f26-129">Например, если необходимо добавить элемент [ \: :: No-Loc ( <dataContractSerializer> ):::](datacontractserializer-element.md) Behavior.</span><span class="sxs-lookup"><span data-stu-id="f5f26-129">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5f26-130">См. также</span><span class="sxs-lookup"><span data-stu-id="f5f26-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="f5f26-131">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="f5f26-131">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="f5f26-132">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="f5f26-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="f5f26-133">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="f5f26-133">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="f5f26-134">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="f5f26-134">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f5f26-135">Обеспечение безопасности клиентов</span><span class="sxs-lookup"><span data-stu-id="f5f26-135">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="f5f26-136">Практическое руководство. Создание федеративного клиента</span><span class="sxs-lookup"><span data-stu-id="f5f26-136">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="f5f26-137">Практическое руководство. Настройка локального издателя</span><span class="sxs-lookup"><span data-stu-id="f5f26-137">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="f5f26-138">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="f5f26-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
