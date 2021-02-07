---
description: 'Дополнительные сведения о: <clear> Element для <namedCaches>'
title: Элемент <clear> для <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: 9d883c102fc76875ce155f353920f730bf9700c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719101"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="f1d78-103">Элемент \<clear> для \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="f1d78-103">\<clear> Element for \<namedCaches></span></span>

<span data-ttu-id="f1d78-104">Очищает все `namedCache` записи в `namedCaches` коллекции для кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="f1d78-104">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="f1d78-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f1d78-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="f1d78-106">Тип</span><span class="sxs-lookup"><span data-stu-id="f1d78-106">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1d78-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="f1d78-107">Attributes and Elements</span></span>  

 <span data-ttu-id="f1d78-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f1d78-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1d78-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f1d78-109">Attributes</span></span>  

 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="f1d78-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f1d78-110">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="f1d78-111">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f1d78-111">Parent Elements</span></span>  
  
|<span data-ttu-id="f1d78-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="f1d78-112">Element</span></span>|<span data-ttu-id="f1d78-113">Описание</span><span class="sxs-lookup"><span data-stu-id="f1d78-113">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="f1d78-114">Содержит коллекцию параметров конфигурации для именованных <xref:System.Runtime.Caching.MemoryCache> экземпляров.</span><span class="sxs-lookup"><span data-stu-id="f1d78-114">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1d78-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="f1d78-115">Remarks</span></span>  

 <span data-ttu-id="f1d78-116">`clear`Элемент очищает все `namedCache` записи в именованной коллекции кэша для кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="f1d78-116">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="f1d78-117">Элемент можно использовать `clear` перед тем, как использовать `add` элемент для добавления новой именованной записи кэша, чтобы быть уверенным в том, что в коллекции нет других именованных кэшей.</span><span class="sxs-lookup"><span data-stu-id="f1d78-117">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1d78-118">См. также</span><span class="sxs-lookup"><span data-stu-id="f1d78-118">See also</span></span>

- [<span data-ttu-id="f1d78-119">\<namedCaches> Элемент (параметры кэша)</span><span class="sxs-lookup"><span data-stu-id="f1d78-119">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
