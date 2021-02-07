---
description: 'Дополнительные сведения: <federationConfiguration>'
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: f8793a8fbd6fc6d5e6994c8e368f587b740e5973
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748990"
---
# \<federationConfiguration>

<span data-ttu-id="0d77f-102">Настраивает <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (всфам) и <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) при использовании федеративной проверки подлинности через протокол WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="0d77f-102">Configures the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) when using federated authentication through the WS-Federation protocol.</span></span> <span data-ttu-id="0d77f-103">Настраивает <xref:System.Security.Claims.ClaimsAuthorizationManager> при использовании <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> класса или для предоставления управления доступом на основе утверждений.</span><span class="sxs-lookup"><span data-stu-id="0d77f-103">Configures the <xref:System.Security.Claims.ClaimsAuthorizationManager> when using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="0d77f-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0d77f-104">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d77f-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0d77f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0d77f-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0d77f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d77f-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0d77f-107">Attributes</span></span>  
  
|<span data-ttu-id="0d77f-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0d77f-108">Attribute</span></span>|<span data-ttu-id="0d77f-109">Описание</span><span class="sxs-lookup"><span data-stu-id="0d77f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d77f-110">name</span><span class="sxs-lookup"><span data-stu-id="0d77f-110">name</span></span>|<span data-ttu-id="0d77f-111">Имя этого элемента конфигурации федерации.</span><span class="sxs-lookup"><span data-stu-id="0d77f-111">The name of this federation configuration element.</span></span> <span data-ttu-id="0d77f-112">Этот атрибут в основном предоставляет точку расширения для будущих протоколов.</span><span class="sxs-lookup"><span data-stu-id="0d77f-112">This attribute primarily provides an extensibility point for future protocols.</span></span> <span data-ttu-id="0d77f-113">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d77f-113">Optional.</span></span>|  
|<span data-ttu-id="0d77f-114">идентитиконфигуратионнаме</span><span class="sxs-lookup"><span data-stu-id="0d77f-114">identityConfigurationName</span></span>|<span data-ttu-id="0d77f-115">Имя раздела конфигурации удостоверений, указанное в [\<identityConfiguration>](identityconfiguration.md) используемом элементе.</span><span class="sxs-lookup"><span data-stu-id="0d77f-115">The name of the identity configuration section as specified in an [\<identityConfiguration>](identityconfiguration.md) element to use.</span></span> <span data-ttu-id="0d77f-116">Если этот атрибут не указан, используется раздел конфигурации удостоверения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0d77f-116">If this attribute is not specified, the default identity configuration section is used.</span></span> <span data-ttu-id="0d77f-117">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d77f-117">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d77f-118">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0d77f-118">Child Elements</span></span>  
  
|<span data-ttu-id="0d77f-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="0d77f-119">Element</span></span>|<span data-ttu-id="0d77f-120">Описание</span><span class="sxs-lookup"><span data-stu-id="0d77f-120">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="0d77f-121">Настраивает обработчик файлов cookie, используемый SAM.</span><span class="sxs-lookup"><span data-stu-id="0d77f-121">Configures the cookie handler used by the SAM.</span></span> <span data-ttu-id="0d77f-122">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d77f-122">Optional.</span></span>|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="0d77f-123">Настраивает сертификат, используемый для шифрования и расшифровки маркеров.</span><span class="sxs-lookup"><span data-stu-id="0d77f-123">Configures the certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="0d77f-124">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d77f-124">Optional.</span></span>|  
|[\<wsFederation>](wsfederation.md)|<span data-ttu-id="0d77f-125">Настраивает модуль проверки подлинности WS-Federation (ВСФАМ).</span><span class="sxs-lookup"><span data-stu-id="0d77f-125">Configures the WS-Federation Authentication Module (WSFAM).</span></span> <span data-ttu-id="0d77f-126">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0d77f-126">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d77f-127">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0d77f-127">Parent Elements</span></span>  
  
|<span data-ttu-id="0d77f-128">Элемент</span><span class="sxs-lookup"><span data-stu-id="0d77f-128">Element</span></span>|<span data-ttu-id="0d77f-129">Описание</span><span class="sxs-lookup"><span data-stu-id="0d77f-129">Description</span></span>|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|<span data-ttu-id="0d77f-130">Раздел конфигурации для проверки подлинности с помощью протокола WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="0d77f-130">Configuration section for authentication using the WS-Federation protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d77f-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="0d77f-131">Remarks</span></span>  

 <span data-ttu-id="0d77f-132">\<federationConfiguration>Элемент предоставляет параметры в двух различных сценариях:</span><span class="sxs-lookup"><span data-stu-id="0d77f-132">The \<federationConfiguration> element provides settings in two different scenarios:</span></span>  
  
- <span data-ttu-id="0d77f-133">При использовании WS-Federation в пассивном веб-приложении элемент содержит параметры, которые настраивают <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (всфам) и <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="0d77f-133">When using WS-Federation in a passive Web application, the element contains settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span> <span data-ttu-id="0d77f-134">Он также ссылается на конфигурацию удостоверения, которая будет использоваться для настройки обработчиков маркеров безопасности и сертификатов, и таких компонентов, как диспетчер авторизации утверждений и диспетчер проверки подлинности утверждений.</span><span class="sxs-lookup"><span data-stu-id="0d77f-134">It also references the identity configuration to be used to configure security token handlers and certificates, and components like the claims authorization manager and the claims authentication manager.</span></span>  
  
- <span data-ttu-id="0d77f-135">При использовании <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> класса или для предоставления управления доступом на основе утверждений в коде элемент ссылается на конфигурацию удостоверения, которая настраивает диспетчер авторизации утверждений и политику, используемые для принятия решений об авторизации.</span><span class="sxs-lookup"><span data-stu-id="0d77f-135">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the element references the identity configuration that configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="0d77f-136">Это справедливо даже в сценариях, которые не являются пассивными веб-сценариями. Например, Windows Communication Foundation приложения (WCF) или приложение, не основанное на веб-интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="0d77f-136">This is true, even in scenarios that are not passive Web scenarios; for example, Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="0d77f-137">Если приложение не является пассивным веб-приложением, то [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) `<federationConfiguration>` к нему будут применены только элементы (и дочерние элемент политики, если таковые имеются) конфигурации удостоверений, на которые ссылается элемент.</span><span class="sxs-lookup"><span data-stu-id="0d77f-137">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (and its child policy elements, if present) of the identity configuration referenced by the `<federationConfiguration>` element are the only settings applied.</span></span> <span data-ttu-id="0d77f-138">Другие атрибуты игнорируются.</span><span class="sxs-lookup"><span data-stu-id="0d77f-138">All others are ignored.</span></span>  
  
 <span data-ttu-id="0d77f-139">Независимо от сценария среда выполнения загружает конфигурацию Федерации по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0d77f-139">Regardless of the scenario, the runtime loads the default federation configuration.</span></span> <span data-ttu-id="0d77f-140">Поведение определяется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0d77f-140">The behavior is defined as follows:</span></span>  
  
1. <span data-ttu-id="0d77f-141">Если `<federationConfiguration>` элемент отсутствует, среда выполнения создает конфигурацию Федерации и заполняет ее значениями по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0d77f-141">If there is no `<federationConfiguration>` element present, the runtime creates a federation configuration and populates it with default values.</span></span> <span data-ttu-id="0d77f-142">Эта конфигурация Федерации по умолчанию будет ссылаться на конфигурацию удостоверения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0d77f-142">This default federation configuration will reference the default identity configuration.</span></span>  
  
2. <span data-ttu-id="0d77f-143">Если имеется один `<federationConfiguration>` элемент, то это конфигурация Федерации по умолчанию, независимо от того, является ли она именованной или безымянной.</span><span class="sxs-lookup"><span data-stu-id="0d77f-143">If a single `<federationConfiguration>` element is present, it is the default federation configuration regardless of whether it is named or unnamed.</span></span> <span data-ttu-id="0d77f-144">Если `identityConfiguration` указан его атрибут, указывается именованная конфигурация удостоверений; в противном случае указывается ссылка на конфигурацию удостоверения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0d77f-144">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
3. <span data-ttu-id="0d77f-145">Если неименованный `<federationConfiguration>` элемент имеется, это конфигурация Федерации по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0d77f-145">If an unnamed `<federationConfiguration>` element is present, it is the default federation configuration.</span></span> <span data-ttu-id="0d77f-146">Если `identityConfiguration` указан его атрибут, указывается именованная конфигурация удостоверений; в противном случае указывается ссылка на конфигурацию удостоверения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0d77f-146">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
4. <span data-ttu-id="0d77f-147">Если имеется несколько именованных `<federationConfiguration>` элементов и отсутствует неименованный `<federationConfiguration>` элемент, возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="0d77f-147">If multiple named `<federationConfiguration>` elements are present and no unnamed `<federationConfiguration>` element is present, an exception is thrown.</span></span>  
  
 <span data-ttu-id="0d77f-148">Как правило, определен только один `<federationConfiguration>` раздел.</span><span class="sxs-lookup"><span data-stu-id="0d77f-148">Typically, only a single `<federationConfiguration>` section is defined.</span></span> <span data-ttu-id="0d77f-149">Этот раздел является конфигурацией Федерации по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0d77f-149">This section is the default federation configuration.</span></span> <span data-ttu-id="0d77f-150">Можно указать несколько элементов с уникальными именами, `<federationConfiguration>` однако в этом случае, если требуется загрузить конфигурацию Федерации, отличную от безымянной, необходимо предоставить обработчик для.</span><span class="sxs-lookup"><span data-stu-id="0d77f-150">You may specify multiple, uniquely-named `<federationConfiguration>` elements; however, in this case, if you want to load a federation configuration other than the unnamed one, you must provide a handler for the.</span></span> <span data-ttu-id="0d77f-151"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> и установить <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> свойство внутри обработчика в <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> объект, инициализируемый значениями из соответствующего `<federationConfiguration>` элемента в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="0d77f-151"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> event and set the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> property inside the handler to a <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object initialized with values from the appropriate `<federationConfiguration>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="0d77f-152">`<federationConfiguration>`Элемент представлен <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> классом.</span><span class="sxs-lookup"><span data-stu-id="0d77f-152">The `<federationConfiguration>` element is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> class.</span></span> <span data-ttu-id="0d77f-153">Сам объект конфигурации представлен <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> классом.</span><span class="sxs-lookup"><span data-stu-id="0d77f-153">The configuration object itself is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> class.</span></span> <span data-ttu-id="0d77f-154">Для <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> свойства задается единственный экземпляр <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> и обеспечивается Федеративная конфигурация для приложения.</span><span class="sxs-lookup"><span data-stu-id="0d77f-154">A single <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance is set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property and provides federated configuration for the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d77f-155">Пример</span><span class="sxs-lookup"><span data-stu-id="0d77f-155">Example</span></span>  

 <span data-ttu-id="0d77f-156">В следующем XML-коде показан `<federationConfiguration>` элемент, указывающий параметры для всфам и указывающий, что SAM использует обработчик файлов cookie по умолчанию (экземпляр <xref:System.IdentityModel.Services.ChunkedCookieHandler> класса).</span><span class="sxs-lookup"><span data-stu-id="0d77f-156">The following XML shows a `<federationConfiguration>` element that specifies settings for the WSFAM and specifies that the default cookie handler (an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class) be used by the SAM.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="0d77f-157">В этом примере ни обработчику файлов cookie, ни ВСФАМ не требуются для использования HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0d77f-157">In this example, neither the cookie handler nor WSFAM are required to use HTTPS.</span></span> <span data-ttu-id="0d77f-158">Это обусловлено тем, что `requireHttps` атрибут `<wsFederation>` элемента и `requireSsl` атрибут в имеют значение `<cookieHandlerElement>` `false` .</span><span class="sxs-lookup"><span data-stu-id="0d77f-158">This is because the `requireHttps` attribute on the `<wsFederation>` element and the `requireSsl` attribute on the `<cookieHandlerElement>` are `false`.</span></span> <span data-ttu-id="0d77f-159">Эти параметры не рекомендуются для большинства рабочих сред, так как они могут представлять угрозу безопасности.</span><span class="sxs-lookup"><span data-stu-id="0d77f-159">These settings are not recommended for most production environments as they may present a security risk.</span></span>  
  
```xml  
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
```  
  
## <a name="see-also"></a><span data-ttu-id="0d77f-160">См. также</span><span class="sxs-lookup"><span data-stu-id="0d77f-160">See also</span></span>

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<identityConfiguration>](identityconfiguration.md)
