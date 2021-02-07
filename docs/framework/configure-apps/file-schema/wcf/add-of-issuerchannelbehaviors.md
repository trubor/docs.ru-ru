---
description: 'Дополнительные сведения <add> о: <issuerChannelBehaviors>'
title: <add> из <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: ccd8ba015b7a6837c74ce2c051a794d36ce8ceaa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750303"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="ce35a-103">\<add> из \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="ce35a-103">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="ce35a-104">Добавляет поведение конечной точки, которое должно использоваться при взаимодействии со службой маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="ce35a-104">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="ce35a-105">Если какое-либо поведение конечной точки содержит [\<clientCredentials>](clientcredentials.md) элемент, будет создано исключение.</span><span class="sxs-lookup"><span data-stu-id="ce35a-105">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="ce35a-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ce35a-106">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ce35a-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ce35a-107">Attributes and Elements</span></span>

<span data-ttu-id="ce35a-108">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ce35a-108">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="ce35a-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ce35a-109">Attributes</span></span>

|<span data-ttu-id="ce35a-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ce35a-110">Attribute</span></span>|<span data-ttu-id="ce35a-111">Описание</span><span class="sxs-lookup"><span data-stu-id="ce35a-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="ce35a-112">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="ce35a-112">issuerAddress</span></span>|<span data-ttu-id="ce35a-113">Универсальный код ресурса (URI) издателя маркера безопасности, с которым осуществляется взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="ce35a-113">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="ce35a-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="ce35a-114">behaviorConfiguration</span></span>|<span data-ttu-id="ce35a-115">Имя поведения конечной точки, определенное в том же файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ce35a-115">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ce35a-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ce35a-116">Child Elements</span></span>

<span data-ttu-id="ce35a-117">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ce35a-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ce35a-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ce35a-118">Parent Elements</span></span>

|<span data-ttu-id="ce35a-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="ce35a-119">Element</span></span>|<span data-ttu-id="ce35a-120">Описание</span><span class="sxs-lookup"><span data-stu-id="ce35a-120">Description</span></span>|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="ce35a-121">Содержит коллекцию поведений конечной точки клиента Windows Communication Foundation (WCF) для использования при взаимодействии с указанными службами маркеров службы.</span><span class="sxs-lookup"><span data-stu-id="ce35a-121">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ce35a-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="ce35a-122">Remarks</span></span>

<span data-ttu-id="ce35a-123">`issuerAddress` содержит URI службы токенов безопасности, с которым клиент хочет обмениваться данными.</span><span class="sxs-lookup"><span data-stu-id="ce35a-123">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="ce35a-124">`behaviorConfiguration` Указывает на поведение конечной точки, используемое приложением в каналах, созданных Windows Communication Foundation (WCF) для получения выданных маркеров от служб маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="ce35a-124">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce35a-125">См. также</span><span class="sxs-lookup"><span data-stu-id="ce35a-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="ce35a-126">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="ce35a-126">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ce35a-127">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="ce35a-127">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ce35a-128">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="ce35a-128">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ce35a-129">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="ce35a-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ce35a-130">Обеспечение безопасности клиентов</span><span class="sxs-lookup"><span data-stu-id="ce35a-130">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="ce35a-131">Практическое руководство. Создание федеративного клиента</span><span class="sxs-lookup"><span data-stu-id="ce35a-131">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="ce35a-132">Практическое руководство. Настройка локального издателя</span><span class="sxs-lookup"><span data-stu-id="ce35a-132">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="ce35a-133">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="ce35a-133">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
