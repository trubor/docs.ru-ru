---
description: 'Дополнительные сведения: <clear>'
title: <clear>
ms.date: 03/30/2017
ms.assetid: 54dcd1d1-038f-4fc8-a3a4-56ba7a1ca0fd
author: BrucePerlerMS
ms.openlocfilehash: 460add2722779a61dacc5c7510ea0a94aaef4a3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664136"
---
# \<clear>

<span data-ttu-id="c2049-102">Удаляет все обработчики маркеров безопасности из текущей коллекции обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="c2049-102">Clears all security token handlers from the current token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="c2049-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c2049-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <clear>  
      </clear>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2049-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="c2049-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c2049-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="c2049-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2049-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="c2049-106">Attributes</span></span>  

 <span data-ttu-id="c2049-107">None</span><span class="sxs-lookup"><span data-stu-id="c2049-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c2049-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c2049-108">Child Elements</span></span>  

 <span data-ttu-id="c2049-109">None</span><span class="sxs-lookup"><span data-stu-id="c2049-109">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2049-110">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="c2049-110">Parent Elements</span></span>  
  
|<span data-ttu-id="c2049-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="c2049-111">Element</span></span>|<span data-ttu-id="c2049-112">Описание</span><span class="sxs-lookup"><span data-stu-id="c2049-112">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="c2049-113">Указывает коллекцию обработчиков маркеров безопасности, зарегистрированных в конечной точке.</span><span class="sxs-lookup"><span data-stu-id="c2049-113">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|
