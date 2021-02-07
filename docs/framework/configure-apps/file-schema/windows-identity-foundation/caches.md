---
description: 'Дополнительные сведения: <caches>'
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: ebc2fa66ab8b657f7cc3741668c9f27fc60510b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681842"
---
# \<caches>

<span data-ttu-id="bdda2-102">Регистрирует кэши, используемые для маркеров сеансов и определения воспроизведения маркеров.</span><span class="sxs-lookup"><span data-stu-id="bdda2-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a><span data-ttu-id="bdda2-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bdda2-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bdda2-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="bdda2-104">Attributes and Elements</span></span>  

 <span data-ttu-id="bdda2-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="bdda2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bdda2-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="bdda2-106">Attributes</span></span>  

 <span data-ttu-id="bdda2-107">None</span><span class="sxs-lookup"><span data-stu-id="bdda2-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bdda2-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="bdda2-108">Child Elements</span></span>  
  
|<span data-ttu-id="bdda2-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="bdda2-109">Element</span></span>|<span data-ttu-id="bdda2-110">Описание</span><span class="sxs-lookup"><span data-stu-id="bdda2-110">Description</span></span>|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|<span data-ttu-id="bdda2-111">Регистрирует кэш для токенов сеанса с помощью службы или коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="bdda2-111">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[\<tokenReplayCache>](tokenreplaycache.md)|<span data-ttu-id="bdda2-112">Регистрирует кэш воспроизведения токенов с помощью службы или коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="bdda2-112">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bdda2-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="bdda2-113">Parent Elements</span></span>  
  
|<span data-ttu-id="bdda2-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="bdda2-114">Element</span></span>|<span data-ttu-id="bdda2-115">Описание</span><span class="sxs-lookup"><span data-stu-id="bdda2-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="bdda2-116">Задает параметры удостоверений уровня службы.</span><span class="sxs-lookup"><span data-stu-id="bdda2-116">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="bdda2-117">Предоставляет конфигурацию для коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="bdda2-117">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdda2-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="bdda2-118">Remarks</span></span>  

 <span data-ttu-id="bdda2-119">`<caches>`Элемент можно указать на уровне службы в `<identityConfiguration>` элементе или на уровне коллекции обработчика маркеров безопасности под `<securityTokenHandlerConfiguration>` элементом.</span><span class="sxs-lookup"><span data-stu-id="bdda2-119">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="bdda2-120">Параметры коллекции обработчиков маркеров переопределяют указанные в службе.</span><span class="sxs-lookup"><span data-stu-id="bdda2-120">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="bdda2-121">`<caches>`Элемент представлен <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> классом.</span><span class="sxs-lookup"><span data-stu-id="bdda2-121">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="bdda2-122">Настроенные кэши представлены <xref:System.IdentityModel.Configuration.IdentityModelCaches> классом.</span><span class="sxs-lookup"><span data-stu-id="bdda2-122">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdda2-123">Пример</span><span class="sxs-lookup"><span data-stu-id="bdda2-123">Example</span></span>  

 <span data-ttu-id="bdda2-124">В следующем коде XML показана конфигурация пользовательского кэша для хранения маркеров безопасности сеанса ( <xref:System.IdentityModel.Tokens.SessionSecurityToken> ).</span><span class="sxs-lookup"><span data-stu-id="bdda2-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="bdda2-125">Конфигурация берется из `ClaimsAwareWebFarm` примера.</span><span class="sxs-lookup"><span data-stu-id="bdda2-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
