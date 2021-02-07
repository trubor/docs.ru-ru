---
description: 'Дополнительные сведения: <localIssuer>'
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 38928f1bfd7740aa902de46958740a1e8fe63e5a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725484"
---
# \<localIssuer>

<span data-ttu-id="2ee4d-102">Указывает адрес и привязку локального издателя, используемого для получения маркера безопасности.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**  
  
## <a name="syntax"></a><span data-ttu-id="2ee4d-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2ee4d-103">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ee4d-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="2ee4d-104">Attributes and Elements</span></span>  

 <span data-ttu-id="2ee4d-105">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ee4d-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2ee4d-106">Attributes</span></span>  
  
|<span data-ttu-id="2ee4d-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="2ee4d-107">Attribute</span></span>|<span data-ttu-id="2ee4d-108">Описание</span><span class="sxs-lookup"><span data-stu-id="2ee4d-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ee4d-109">address</span><span class="sxs-lookup"><span data-stu-id="2ee4d-109">address</span></span>|<span data-ttu-id="2ee4d-110">Обязательная строка.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-110">Required string.</span></span> <span data-ttu-id="2ee4d-111">Указывает универсальный код ресурса (URI) локального издателя.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-111">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="2ee4d-112">binding</span><span class="sxs-lookup"><span data-stu-id="2ee4d-112">binding</span></span>|<span data-ttu-id="2ee4d-113">Необязательная строка.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-113">Optional string.</span></span> <span data-ttu-id="2ee4d-114">Одна из привязок, предоставляемых системой.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-114">One of the system-provided bindings.</span></span> <span data-ttu-id="2ee4d-115">Список см. в разделе [привязки, предоставляемые системой](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="2ee4d-115">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="2ee4d-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="2ee4d-116">bindingConfiguration</span></span>|<span data-ttu-id="2ee4d-117">Необязательная строка.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-117">Optional string.</span></span> <span data-ttu-id="2ee4d-118">Указывает конфигурацию привязки в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-118">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ee4d-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="2ee4d-119">Child Elements</span></span>  
  
|<span data-ttu-id="2ee4d-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="2ee4d-120">Element</span></span>|<span data-ttu-id="2ee4d-121">Описание</span><span class="sxs-lookup"><span data-stu-id="2ee4d-121">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="2ee4d-122">Указывает идентификационные данные для локального издателя.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-122">Specifies identity information for the local issuer.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="2ee4d-123">Коллекция заголовков адреса, требуемых для правильного обращения к локальному издателю.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-123">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="2ee4d-124">Заголовок в эту коллекцию можно добавить с помощью ключевого слова `add`.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-124">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2ee4d-125">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="2ee4d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="2ee4d-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="2ee4d-126">Element</span></span>|<span data-ttu-id="2ee4d-127">Описание</span><span class="sxs-lookup"><span data-stu-id="2ee4d-127">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="2ee4d-128">Задает пользовательский маркер, используемый для проверки подлинности клиента при подключении к службе.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-128">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ee4d-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="2ee4d-129">Remarks</span></span>  

 <span data-ttu-id="2ee4d-130">При получении маркера от службы маркеров безопасности (STS) в клиентском приложении должны быть заданы адрес и привязка для установления соединения с STS.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-130">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="2ee4d-131">Если <xref:System.ServiceModel.WSFederationHttpBinding> компонент не предоставляет URL-адрес для службы маркеров безопасности или если адресом издателя Федеративной привязки является `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` или `null` , канал Windows Communication Foundation клиента (WCF) использует значения, заданные параметром, `address` и, `binding` чтобы взаимодействовать с STS для получения выданного маркера.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-131">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="2ee4d-132">Дополнительные сведения о настройке локального издателя см. в разделе [как настроить локальный издатель](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="2ee4d-132">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ee4d-133">Пример</span><span class="sxs-lookup"><span data-stu-id="2ee4d-133">Example</span></span>  

 <span data-ttu-id="2ee4d-134">В следующем примере устанавливаются атрибуты `address`, `binding` и `bindingConfiguration` элемента `localIssuer`.</span><span class="sxs-lookup"><span data-stu-id="2ee4d-134">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="MyEndpointBehavior">
        <clientCredentials>
          <issuedToken cacheIssuedTokens="false"
                       defaultKeyEntropyMode="ClientEntropy">
            <localIssuer address="net.tcp://cohowinery/tokens"
                         binding="netTcpBinding"
                         bindingConfiguration="myTcpBindingConfig" />
          </issuedToken>
        </clientCredentials>
      </behavior>
    </endpointBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="2ee4d-135">См. также</span><span class="sxs-lookup"><span data-stu-id="2ee4d-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="2ee4d-136">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="2ee4d-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="2ee4d-137">Практическое руководство. Настройка локального издателя</span><span class="sxs-lookup"><span data-stu-id="2ee4d-137">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="2ee4d-138">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="2ee4d-138">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2ee4d-139">Поведение безопасности</span><span class="sxs-lookup"><span data-stu-id="2ee4d-139">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="2ee4d-140">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="2ee4d-140">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="2ee4d-141">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="2ee4d-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2ee4d-142">Обеспечение безопасности клиентов</span><span class="sxs-lookup"><span data-stu-id="2ee4d-142">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="2ee4d-143">Практическое руководство. Создание федеративного клиента</span><span class="sxs-lookup"><span data-stu-id="2ee4d-143">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="2ee4d-144">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="2ee4d-144">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
