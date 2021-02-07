---
description: 'Дополнительные сведения о <webProxyScript> элементе: Element (параметры сети)'
title: Элемент <webProxyScript> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: 1627b6650582202f3f1a4c1fdebf2d183e4a894b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740110"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="a1d25-103">Элемент \<webProxyScript> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="a1d25-103">\<webProxyScript> Element (Network Settings)</span></span>

<span data-ttu-id="a1d25-104">Настраивает характеристики сценария, используемого для обнаружения веб-прокси.</span><span class="sxs-lookup"><span data-stu-id="a1d25-104">Configures the characteristics of the script used to discover Web proxies.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**

## <a name="syntax"></a><span data-ttu-id="a1d25-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a1d25-105">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1d25-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a1d25-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a1d25-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a1d25-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1d25-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a1d25-108">Attributes</span></span>  
  
|<span data-ttu-id="a1d25-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a1d25-109">Attribute</span></span>|<span data-ttu-id="a1d25-110">Описание</span><span class="sxs-lookup"><span data-stu-id="a1d25-110">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="a1d25-111">Указывает максимальное время загрузки скрипта в часах, минутах и секундах.</span><span class="sxs-lookup"><span data-stu-id="a1d25-111">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="a1d25-112">Значение по умолчанию — одна минута.</span><span class="sxs-lookup"><span data-stu-id="a1d25-112">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1d25-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a1d25-113">Child Elements</span></span>  

 <span data-ttu-id="a1d25-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="a1d25-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a1d25-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a1d25-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a1d25-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="a1d25-116">Element</span></span>|<span data-ttu-id="a1d25-117">Описание</span><span class="sxs-lookup"><span data-stu-id="a1d25-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1d25-118">параметры</span><span class="sxs-lookup"><span data-stu-id="a1d25-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="a1d25-119">Настраивает основные параметры сети для пространства имен <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="a1d25-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1d25-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="a1d25-120">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a1d25-121">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="a1d25-121">Configuration Files</span></span>  

 <span data-ttu-id="a1d25-122">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a1d25-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d25-123">См. также</span><span class="sxs-lookup"><span data-stu-id="a1d25-123">See also</span></span>

- [<span data-ttu-id="a1d25-124">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="a1d25-124">Network Settings Schema</span></span>](index.md)
