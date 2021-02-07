---
description: 'Дополнительные сведения: <sessionSecurityTokenCache>'
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 6fc0bb518f546ffd80c68df95a9c0fab145423b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698288"
---
# \<sessionSecurityTokenCache>

<span data-ttu-id="17d3d-102">Регистрирует кэш для токенов сеанса с помощью службы или коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="17d3d-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**  
  
## <a name="syntax"></a><span data-ttu-id="17d3d-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="17d3d-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17d3d-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="17d3d-104">Attributes and Elements</span></span>  

 <span data-ttu-id="17d3d-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="17d3d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17d3d-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="17d3d-106">Attributes</span></span>  
  
|<span data-ttu-id="17d3d-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="17d3d-107">Attribute</span></span>|<span data-ttu-id="17d3d-108">Описание</span><span class="sxs-lookup"><span data-stu-id="17d3d-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17d3d-109">type</span><span class="sxs-lookup"><span data-stu-id="17d3d-109">type</span></span>|<span data-ttu-id="17d3d-110">Тип, производный от <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> класса.</span><span class="sxs-lookup"><span data-stu-id="17d3d-110">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17d3d-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="17d3d-111">Child Elements</span></span>  

 <span data-ttu-id="17d3d-112">None</span><span class="sxs-lookup"><span data-stu-id="17d3d-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17d3d-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="17d3d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="17d3d-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="17d3d-114">Element</span></span>|<span data-ttu-id="17d3d-115">Описание</span><span class="sxs-lookup"><span data-stu-id="17d3d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="17d3d-116">Регистрирует кэши, используемые службой или коллекцией обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="17d3d-116">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="17d3d-117">Пример</span><span class="sxs-lookup"><span data-stu-id="17d3d-117">Example</span></span>  

 <span data-ttu-id="17d3d-118">В следующем коде XML показана конфигурация пользовательского кэша для хранения маркеров безопасности сеанса ( <xref:System.IdentityModel.Tokens.SessionSecurityToken> ).</span><span class="sxs-lookup"><span data-stu-id="17d3d-118">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="17d3d-119">Конфигурация берется из `ClaimsAwareWebFarm` примера.</span><span class="sxs-lookup"><span data-stu-id="17d3d-119">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="17d3d-120">Дополнительные сведения об этом образце см. в разделе [Индекс образца кода WIF](/previous-versions/dotnet/framework/security/wif-code-sample-index).</span><span class="sxs-lookup"><span data-stu-id="17d3d-120">For more information about this sample, see [WIF Code Sample Index](/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="17d3d-121">См. также</span><span class="sxs-lookup"><span data-stu-id="17d3d-121">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
