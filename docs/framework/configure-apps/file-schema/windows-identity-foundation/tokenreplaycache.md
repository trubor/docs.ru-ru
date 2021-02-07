---
description: 'Дополнительные сведения: <tokenReplayCache>'
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 793b1f88a9eeb0ebce4cd440e248e81377f17e9b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749003"
---
# \<tokenReplayCache>

<span data-ttu-id="9087a-102">Регистрирует кэш воспроизведения токенов с помощью службы или коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="9087a-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a><span data-ttu-id="9087a-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9087a-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9087a-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="9087a-104">Attributes and Elements</span></span>  

 <span data-ttu-id="9087a-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="9087a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9087a-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="9087a-106">Attributes</span></span>  
  
|<span data-ttu-id="9087a-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="9087a-107">Attribute</span></span>|<span data-ttu-id="9087a-108">Описание</span><span class="sxs-lookup"><span data-stu-id="9087a-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9087a-109">type</span><span class="sxs-lookup"><span data-stu-id="9087a-109">type</span></span>|<span data-ttu-id="9087a-110">Тип, производный от <xref:System.IdentityModel.Tokens.TokenReplayCache> класса.</span><span class="sxs-lookup"><span data-stu-id="9087a-110">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="9087a-111">Дополнительные сведения о том, как указать пользовательский параметр `type` , см. в разделе [ссылки на пользовательские типы].</span><span class="sxs-lookup"><span data-stu-id="9087a-111">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="9087a-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="9087a-112">Child Elements</span></span>  

 <span data-ttu-id="9087a-113">None</span><span class="sxs-lookup"><span data-stu-id="9087a-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9087a-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="9087a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="9087a-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="9087a-115">Element</span></span>|<span data-ttu-id="9087a-116">Описание</span><span class="sxs-lookup"><span data-stu-id="9087a-116">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="9087a-117">Регистрирует кэши, используемые службой или коллекцией обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="9087a-117">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9087a-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="9087a-118">Remarks</span></span>  

 <span data-ttu-id="9087a-119">Кэш воспроизведения токенов используется для обнаружения воспроизводимых токенов.</span><span class="sxs-lookup"><span data-stu-id="9087a-119">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="9087a-120">Обнаружение воспроизведения токенов включается [\<tokenReplayDetection>](tokenreplaydetection.md) элементом, который также указывает максимальное время окончания срока действия токенов.</span><span class="sxs-lookup"><span data-stu-id="9087a-120">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9087a-121">Пример</span><span class="sxs-lookup"><span data-stu-id="9087a-121">Example</span></span>  

 <span data-ttu-id="9087a-122">В следующем коде XML показана конфигурация пользовательского кэша для обнаружения воспроизводимых токенов.</span><span class="sxs-lookup"><span data-stu-id="9087a-122">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9087a-123">См. также</span><span class="sxs-lookup"><span data-stu-id="9087a-123">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
