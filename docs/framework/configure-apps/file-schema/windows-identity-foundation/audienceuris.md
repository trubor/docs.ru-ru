---
description: 'Дополнительные сведения: <audienceUris>'
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 98b411e73d4b9941e65daaf5d1d63285cdc90fd0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681855"
---
# \<audienceUris>

<span data-ttu-id="ce22e-102">Указывает набор универсальных кодов ресурса (URI), которые являются допустимыми идентификаторами проверяющей стороны (RP).</span><span class="sxs-lookup"><span data-stu-id="ce22e-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="ce22e-103">Маркеры не будут приниматься, если они не относятся к одному из разрешенных URI аудитории.</span><span class="sxs-lookup"><span data-stu-id="ce22e-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**  
  
## <a name="syntax"></a><span data-ttu-id="ce22e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ce22e-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce22e-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ce22e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ce22e-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ce22e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce22e-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ce22e-107">Attributes</span></span>  
  
|<span data-ttu-id="ce22e-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ce22e-108">Attribute</span></span>|<span data-ttu-id="ce22e-109">Описание</span><span class="sxs-lookup"><span data-stu-id="ce22e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce22e-110">mode</span><span class="sxs-lookup"><span data-stu-id="ce22e-110">mode</span></span>|<span data-ttu-id="ce22e-111"><xref:System.IdentityModel.Selectors.AudienceUriMode>Значение типа, указывающее, следует ли применять ограничение аудитории к входящему токену.</span><span class="sxs-lookup"><span data-stu-id="ce22e-111">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="ce22e-112">Возможные значения: "всегда", "Never" и "Беареркэйонли".</span><span class="sxs-lookup"><span data-stu-id="ce22e-112">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="ce22e-113">Значение по умолчанию — Always.</span><span class="sxs-lookup"><span data-stu-id="ce22e-113">The default is "Always".</span></span> <span data-ttu-id="ce22e-114">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="ce22e-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce22e-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ce22e-115">Child Elements</span></span>  
  
|<span data-ttu-id="ce22e-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="ce22e-116">Element</span></span>|<span data-ttu-id="ce22e-117">Описание</span><span class="sxs-lookup"><span data-stu-id="ce22e-117">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="ce22e-118">Добавляет URI, указанный `value` атрибутом, в коллекцию audienceUris.</span><span class="sxs-lookup"><span data-stu-id="ce22e-118">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="ce22e-119">Атрибут `value` является обязательным.</span><span class="sxs-lookup"><span data-stu-id="ce22e-119">The `value` attribute is required.</span></span> <span data-ttu-id="ce22e-120">В URI учитывается регистр.</span><span class="sxs-lookup"><span data-stu-id="ce22e-120">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="ce22e-121">Очищает коллекцию audienceUris.</span><span class="sxs-lookup"><span data-stu-id="ce22e-121">Clears the audienceUris collection.</span></span> <span data-ttu-id="ce22e-122">Все идентификаторы удаляются из коллекции.</span><span class="sxs-lookup"><span data-stu-id="ce22e-122">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="ce22e-123">Удаляет URI, указанный `value` атрибутом из коллекции audienceUris.</span><span class="sxs-lookup"><span data-stu-id="ce22e-123">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="ce22e-124">Атрибут `value` является обязательным.</span><span class="sxs-lookup"><span data-stu-id="ce22e-124">The `value` attribute is required.</span></span> <span data-ttu-id="ce22e-125">В URI учитывается регистр.</span><span class="sxs-lookup"><span data-stu-id="ce22e-125">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce22e-126">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ce22e-126">Parent Elements</span></span>  
  
|<span data-ttu-id="ce22e-127">Элемент</span><span class="sxs-lookup"><span data-stu-id="ce22e-127">Element</span></span>|<span data-ttu-id="ce22e-128">Описание</span><span class="sxs-lookup"><span data-stu-id="ce22e-128">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="ce22e-129">Предоставляет конфигурацию для коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="ce22e-129">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce22e-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="ce22e-130">Remarks</span></span>  

 <span data-ttu-id="ce22e-131">По умолчанию коллекция пуста; Используйте `<add>` `<clear>` элементы, и `<remove>` для изменения коллекции.</span><span class="sxs-lookup"><span data-stu-id="ce22e-131">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="ce22e-132"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler><xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>объекты и используют значения в коллекции URI аудитории для настройки любых допустимых ограничений URI аудитории в <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> объектах.</span><span class="sxs-lookup"><span data-stu-id="ce22e-132"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="ce22e-133">`<audienceUris>`Элемент представлен <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> классом.</span><span class="sxs-lookup"><span data-stu-id="ce22e-133">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="ce22e-134">Отдельный URI, добавленный в коллекцию, представлен <xref:System.IdentityModel.Configuration.AudienceUriElement> классом.</span><span class="sxs-lookup"><span data-stu-id="ce22e-134">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce22e-135">Использование `<audienceUris>` элемента в качестве дочернего элемента [\<identityConfiguration>](identityconfiguration.md) элемента является устаревшим, но по-прежнему поддерживается для обратной совместимости.</span><span class="sxs-lookup"><span data-stu-id="ce22e-135">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="ce22e-136">Параметры `<securityTokenHandlerConfiguration>` элемента переопределяют их для `<identityConfiguration>` элемента.</span><span class="sxs-lookup"><span data-stu-id="ce22e-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce22e-137">Пример</span><span class="sxs-lookup"><span data-stu-id="ce22e-137">Example</span></span>  

 <span data-ttu-id="ce22e-138">В следующем коде XML показано, как настроить допустимые URI аудитории для приложения.</span><span class="sxs-lookup"><span data-stu-id="ce22e-138">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="ce22e-139">В этом примере настраивается один универсальный код ресурса (URI).</span><span class="sxs-lookup"><span data-stu-id="ce22e-139">This example configures a single URI.</span></span> <span data-ttu-id="ce22e-140">Маркеры, областью которых является этот URI, будут приняты, все остальные будут отклонены.</span><span class="sxs-lookup"><span data-stu-id="ce22e-140">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
