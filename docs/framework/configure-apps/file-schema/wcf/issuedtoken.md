---
description: 'Дополнительные сведения: <issuedToken>'
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: aa7486a621d5a6e6900f67300792e29ce2538257
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725692"
---
# \<issuedToken>

<span data-ttu-id="3b36d-102">Задает пользовательский маркер, используемый для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="3b36d-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**  
  
## <a name="syntax"></a><span data-ttu-id="3b36d-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3b36d-103">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b36d-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="3b36d-104">Attributes and Elements</span></span>  

 <span data-ttu-id="3b36d-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="3b36d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b36d-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="3b36d-106">Attributes</span></span>  
  
|<span data-ttu-id="3b36d-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="3b36d-107">Attribute</span></span>|<span data-ttu-id="3b36d-108">Описание</span><span class="sxs-lookup"><span data-stu-id="3b36d-108">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="3b36d-109">Дополнительный логический атрибут, указывающий, выполняется ли кэширование маркеров.</span><span class="sxs-lookup"><span data-stu-id="3b36d-109">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="3b36d-110">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="3b36d-110">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="3b36d-111">Дополнительный строковый атрибут, указывающий, какие случайные значения (показатели энтропии) используются для операций «рукопожатия».</span><span class="sxs-lookup"><span data-stu-id="3b36d-111">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="3b36d-112">Допустимы следующие значения: `ClientEntropy`, `ServerEntropy` и `CombinedEntropy`. Значение по умолчанию - `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="3b36d-112">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="3b36d-113">Это атрибут типа <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="3b36d-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="3b36d-114">Дополнительный целочисленный атрибут, задающий время в процентах от срока действия (предоставляемого издателем маркера), которое может пройти до обновления маркера.</span><span class="sxs-lookup"><span data-stu-id="3b36d-114">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="3b36d-115">Диапазон значений: 0–100.</span><span class="sxs-lookup"><span data-stu-id="3b36d-115">Values are from 0 to 100.</span></span> <span data-ttu-id="3b36d-116">Значение по умолчанию, равное 60, указывает, что попытка возобновления предпринимается по истечении 60% времени.</span><span class="sxs-lookup"><span data-stu-id="3b36d-116">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="3b36d-117">Дополнительный атрибут, определяющий поведения канала во время связи с издателем.</span><span class="sxs-lookup"><span data-stu-id="3b36d-117">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="3b36d-118">Дополнительный атрибут, определяющий поведения канала во время связи с локальным издателем.</span><span class="sxs-lookup"><span data-stu-id="3b36d-118">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="3b36d-119">Дополнительный атрибут Timespan, задающий промежуток времени, в течение которого выданные маркеры сохраняются в кэше, если время не указывается издателем маркера (службой маркеров безопасности).</span><span class="sxs-lookup"><span data-stu-id="3b36d-119">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="3b36d-120">Значение по умолчанию — "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="3b36d-120">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b36d-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="3b36d-121">Child Elements</span></span>  
  
|<span data-ttu-id="3b36d-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="3b36d-122">Element</span></span>|<span data-ttu-id="3b36d-123">Описание</span><span class="sxs-lookup"><span data-stu-id="3b36d-123">Description</span></span>|  
|-------------|-----------------|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="3b36d-124">Определяет адрес локального издателя маркера и привязку, используемую для взаимодействия с конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="3b36d-124">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="3b36d-125">Задает поведения конечной точки, используемое при связи с локальным издателем.</span><span class="sxs-lookup"><span data-stu-id="3b36d-125">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3b36d-126">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="3b36d-126">Parent Elements</span></span>  
  
|<span data-ttu-id="3b36d-127">Элемент</span><span class="sxs-lookup"><span data-stu-id="3b36d-127">Element</span></span>|<span data-ttu-id="3b36d-128">Описание</span><span class="sxs-lookup"><span data-stu-id="3b36d-128">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="3b36d-129">Задает учетные данные, используемые для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="3b36d-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b36d-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="3b36d-130">Remarks</span></span>  

 <span data-ttu-id="3b36d-131">Выданный маркер представляет собой пользовательские учетные данные, используемые, например, при проверке подлинности с помощью службы маркеров безопасности при федеративном доступе.</span><span class="sxs-lookup"><span data-stu-id="3b36d-131">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="3b36d-132">По умолчанию используется маркер SAML.</span><span class="sxs-lookup"><span data-stu-id="3b36d-132">By default, the token is a SAML token.</span></span> <span data-ttu-id="3b36d-133">Дополнительные сведения см. в статьях [Федерация и выданные токены](../../../wcf/feature-details/federation-and-issued-tokens.md), [Федерация и выданные токены](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="3b36d-133">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="3b36d-134">Этот раздел содержит элементы, используемые для настройки локального издателя маркеров, или поведения, используемые при работе со службой маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="3b36d-134">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="3b36d-135">Инструкции по настройке клиента для использования локального издателя см. [в разделе как настроить локальный издатель](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="3b36d-135">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b36d-136">См. также</span><span class="sxs-lookup"><span data-stu-id="3b36d-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="3b36d-137">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="3b36d-137">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3b36d-138">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="3b36d-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3b36d-139">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="3b36d-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3b36d-140">Обеспечение безопасности клиентов</span><span class="sxs-lookup"><span data-stu-id="3b36d-140">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="3b36d-141">Практическое руководство. Создание федеративного клиента</span><span class="sxs-lookup"><span data-stu-id="3b36d-141">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="3b36d-142">Практическое руководство. Настройка локального издателя</span><span class="sxs-lookup"><span data-stu-id="3b36d-142">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="3b36d-143">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="3b36d-143">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
