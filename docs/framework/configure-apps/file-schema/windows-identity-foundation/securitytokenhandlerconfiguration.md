---
description: 'Дополнительные сведения: <securityTokenHandlerConfiguration>'
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 8c014d971d3e8cc640a3b7042e3a0266d902de7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698314"
---
# \<securityTokenHandlerConfiguration>

<span data-ttu-id="3036c-102">Предоставляет конфигурацию для коллекции обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="3036c-102">Provides configuration for the collection of token handlers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="3036c-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3036c-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3036c-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="3036c-104">Attributes and Elements</span></span>  

 <span data-ttu-id="3036c-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="3036c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3036c-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="3036c-106">Attributes</span></span>  
  
|<span data-ttu-id="3036c-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="3036c-107">Attribute</span></span>|<span data-ttu-id="3036c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="3036c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3036c-109">савебутстрапконтекст</span><span class="sxs-lookup"><span data-stu-id="3036c-109">saveBootstrapContext</span></span>|<span data-ttu-id="3036c-110">Указывает, следует ли включать в маркер сеанса начальные токены.</span><span class="sxs-lookup"><span data-stu-id="3036c-110">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="3036c-111">Значение также может быть задано в коллекции обработчиков маркеров путем установки `saveBootstrapContext` атрибута для [\<identityConfiguration>](identityconfiguration.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="3036c-111">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="3036c-112">Значение, заданное в коллекции обработчиков маркеров, переопределяет значение, заданное для службы.</span><span class="sxs-lookup"><span data-stu-id="3036c-112">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="3036c-113">максимумклоккскев</span><span class="sxs-lookup"><span data-stu-id="3036c-113">maximumClockSkew</span></span>|<span data-ttu-id="3036c-114">Значение типа <xref:System.TimeSpan> , указывающее максимально допустимую отклонение в часах.</span><span class="sxs-lookup"><span data-stu-id="3036c-114">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="3036c-115">Управляет максимально разрешенным отклонением по часам при выполнении операций с учетом времени, таких как проверка срока действия сеанса входа.</span><span class="sxs-lookup"><span data-stu-id="3036c-115">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="3036c-116">Значение по умолчанию — 5 минут, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="3036c-116">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="3036c-117">Дополнительные сведения об указании <xref:System.TimeSpan> значений см. в разделе [значения TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="3036c-117">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="3036c-118">Максимальная разница в часах может также быть задана на уровне службы путем установки `maximumClockSkew` атрибута для [\<identityConfiguration>](identityconfiguration.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="3036c-118">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="3036c-119">Значение, заданное в коллекции обработчиков маркеров, переопределяет значение, заданное для службы.</span><span class="sxs-lookup"><span data-stu-id="3036c-119">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3036c-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="3036c-120">Child Elements</span></span>  
  
|<span data-ttu-id="3036c-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="3036c-121">Element</span></span>|<span data-ttu-id="3036c-122">Описание</span><span class="sxs-lookup"><span data-stu-id="3036c-122">Description</span></span>|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|<span data-ttu-id="3036c-123">Указывает набор универсальных кодов ресурса (URI), которые являются допустимыми идентификаторами этой проверяющей стороны.</span><span class="sxs-lookup"><span data-stu-id="3036c-123">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="3036c-124">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="3036c-124">Optional.</span></span>|  
|[\<caches>](caches.md)|<span data-ttu-id="3036c-125">Регистрирует кэши, используемые для маркеров сеансов и определения воспроизведения маркеров.</span><span class="sxs-lookup"><span data-stu-id="3036c-125">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="3036c-126">Может указываться на уровне службы или в коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="3036c-126">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="3036c-127">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="3036c-127">Optional.</span></span>|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="3036c-128">Управляет параметрами, которые обработчики маркеров используют для проверки сертификатов.</span><span class="sxs-lookup"><span data-stu-id="3036c-128">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="3036c-129">Может указываться на уровне службы или в коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="3036c-129">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="3036c-130">Эти параметры переопределяются, если для определенного обработчика настроен собственный проверяющий элемент управления.</span><span class="sxs-lookup"><span data-stu-id="3036c-130">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="3036c-131">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="3036c-131">Optional.</span></span>|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="3036c-132">Настраивает реестр имен издателя, используемый обработчиками в коллекции обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="3036c-132">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="3036c-133">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="3036c-133">Optional.</span></span>|  
|[\<issuerTokenResolver>](issuertokenresolver.md)|<span data-ttu-id="3036c-134">Регистрирует сопоставитель маркеров издателя, используемый обработчиками в коллекции обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="3036c-134">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="3036c-135">Сопоставитель токенов издателя используется для разрешения маркера подписывания входящих токенов и сообщений.</span><span class="sxs-lookup"><span data-stu-id="3036c-135">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="3036c-136">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="3036c-136">Optional.</span></span>|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|<span data-ttu-id="3036c-137">Регистрирует сопоставитель маркеров службы, используемый обработчиками в коллекции обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="3036c-137">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="3036c-138">Сопоставитель токенов службы используется для разрешения маркера шифрования входящих токенов и сообщений.</span><span class="sxs-lookup"><span data-stu-id="3036c-138">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="3036c-139">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="3036c-139">Optional.</span></span>|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|<span data-ttu-id="3036c-140">Включает обнаружение воспроизведения маркеров и задает срок действия токенов.</span><span class="sxs-lookup"><span data-stu-id="3036c-140">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="3036c-141">Может указываться на уровне службы или в коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="3036c-141">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="3036c-142">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="3036c-142">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3036c-143">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="3036c-143">Parent Elements</span></span>  
  
|<span data-ttu-id="3036c-144">Элемент</span><span class="sxs-lookup"><span data-stu-id="3036c-144">Element</span></span>|<span data-ttu-id="3036c-145">Описание</span><span class="sxs-lookup"><span data-stu-id="3036c-145">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="3036c-146">Указывает коллекцию обработчиков маркеров безопасности, зарегистрированных в конечной точке.</span><span class="sxs-lookup"><span data-stu-id="3036c-146">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3036c-147">Remarks</span><span class="sxs-lookup"><span data-stu-id="3036c-147">Remarks</span></span>  

 <span data-ttu-id="3036c-148">В этом разделе приводятся значения свойств для <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> объекта.</span><span class="sxs-lookup"><span data-stu-id="3036c-148">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="3036c-149">Параметры, настроенные в этом разделе, переопределяют настройки, настроенные в службе.</span><span class="sxs-lookup"><span data-stu-id="3036c-149">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="3036c-150">Некоторые из этих параметров, в свою очередь, могут быть переопределены параметрами, заданными при добавлении обработчика в коллекцию обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="3036c-150">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3036c-151">Пример</span><span class="sxs-lookup"><span data-stu-id="3036c-151">Example</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```
