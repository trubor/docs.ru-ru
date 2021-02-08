---
description: 'Дополнительные сведения о: <System. identityModel. Services>'
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 037a96c2620e06ef6aed85d1dbaba62aca72e9eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786555"
---
# \<system.identityModel.services>

<span data-ttu-id="fc6a3-103">Раздел конфигурации для проверки подлинности с помощью протокола WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="fc6a3-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
## <a name="syntax"></a><span data-ttu-id="fc6a3-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fc6a3-104">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc6a3-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fc6a3-105">Attributes and Elements</span></span>  

 <span data-ttu-id="fc6a3-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fc6a3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc6a3-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fc6a3-107">Attributes</span></span>  

 <span data-ttu-id="fc6a3-108">None</span><span class="sxs-lookup"><span data-stu-id="fc6a3-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fc6a3-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fc6a3-109">Child Elements</span></span>  
  
|<span data-ttu-id="fc6a3-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="fc6a3-110">Element</span></span>|<span data-ttu-id="fc6a3-111">Описание</span><span class="sxs-lookup"><span data-stu-id="fc6a3-111">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="fc6a3-112">Содержит параметры, которые настраивают <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (всфам) и <xref:System.IdentityModel.Services.SessionAuthenticationModule> HTTP-модули (SAM).</span><span class="sxs-lookup"><span data-stu-id="fc6a3-112">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fc6a3-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fc6a3-113">Parent Elements</span></span>  

 <span data-ttu-id="fc6a3-114">None</span><span class="sxs-lookup"><span data-stu-id="fc6a3-114">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc6a3-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="fc6a3-115">Remarks</span></span>  

 <span data-ttu-id="fc6a3-116">Добавьте `<system.identityModel.services>` раздел в файл конфигурации приложения, чтобы указать параметры для SAM и всфам.</span><span class="sxs-lookup"><span data-stu-id="fc6a3-116">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fc6a3-117">При использовании <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> класса или для предоставления управления доступом на основе утверждений в коде Диспетчер авторизации утверждений ( <xref:System.Security.Claims.ClaimsAuthorizationManager> ) и политика, используемые для принятия решений об авторизации, настраиваются с помощью `<identityConfiguration>` элемента, который неявно или явно упоминается в `<federationConfiguration>` элементе в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="fc6a3-117">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="fc6a3-118">Дополнительные сведения см. в разделе **Примечания** в [\<federationConfiguration>](federationconfiguration.md) элементе.</span><span class="sxs-lookup"><span data-stu-id="fc6a3-118">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="fc6a3-119">`<system.identityModel.services>`Раздел представлен <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> классом.</span><span class="sxs-lookup"><span data-stu-id="fc6a3-119">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="fc6a3-120">Коллекция дочерних элементов, `<federationConfiguration>` настроенных в разделе, представлена <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> классом.</span><span class="sxs-lookup"><span data-stu-id="fc6a3-120">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc6a3-121">Пример</span><span class="sxs-lookup"><span data-stu-id="fc6a3-121">Example</span></span>  

 <span data-ttu-id="fc6a3-122">В следующем коде XML показано, как добавить `<system.identityModel.services>` раздел в файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="fc6a3-122">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="fc6a3-123">Сначала необходимо добавить объявления разделов как для `<system.identityModel.services>` раздела, так и для `<system.identityModel>` разделов.</span><span class="sxs-lookup"><span data-stu-id="fc6a3-123">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="fc6a3-124">(При добавлении раздела необходимо `<system.identityModel.services>` также добавить объявление для `<system.identityModel>` раздела, чтобы гарантировать, что при необходимости раздел по умолчанию `<identityConfiguration>` может быть создан средой выполнения.) После добавления объявлений разделов можно настроить параметры федеративной проверки подлинности в `<system.identityModel.services>` элементе.</span><span class="sxs-lookup"><span data-stu-id="fc6a3-124">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true"
        issuer="http://localhost:15839/wsFederationSTS/Issue"
        realm="http://localhost:50969/" reply="http://localhost:50969/"
        requireHttps="false"
        signOutReply="http://localhost:50969/SignedOutPage.html"
        signOutQueryString="Param1=value2&Param2=value2"
        persistentCookiesOnPassiveRedirects="true" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
  
</configuration>  
```
