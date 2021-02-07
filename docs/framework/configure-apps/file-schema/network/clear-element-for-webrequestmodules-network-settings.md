---
description: 'Дополнительные сведения о: <clear> элемент для webRequestModules (параметры сети)'
title: Элемент <clear> для webRequestModules (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
ms.openlocfilehash: 0782bf9edeafed2d61a368c3f6a8b37ef226c990
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740422"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="2c378-103">Элемент \<clear> для webRequestModules (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="2c378-103">\<clear> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="2c378-104">Удаляет из приложения все зарегистрированные модули веб-запросов.</span><span class="sxs-lookup"><span data-stu-id="2c378-104">Removes all registered Web request modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="2c378-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2c378-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c378-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="2c378-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2c378-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="2c378-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c378-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2c378-108">Attributes</span></span>  

 <span data-ttu-id="2c378-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="2c378-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2c378-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="2c378-110">Child Elements</span></span>  

 <span data-ttu-id="2c378-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="2c378-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c378-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="2c378-112">Parent Elements</span></span>  
  
|<span data-ttu-id="2c378-113">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="2c378-113">**Element**</span></span>|<span data-ttu-id="2c378-114">**Описание**</span><span class="sxs-lookup"><span data-stu-id="2c378-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2c378-115">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="2c378-115">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="2c378-116">Указывает модули, используемые для запроса сведений от сетевых узлов.</span><span class="sxs-lookup"><span data-stu-id="2c378-116">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c378-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="2c378-117">Remarks</span></span>  

 <span data-ttu-id="2c378-118">`clear`Элемент удаляет все зарегистрированные модули веб-запросов, определенные ранее в файле конфигурации или на более высоком уровне иерархии конфигурации.</span><span class="sxs-lookup"><span data-stu-id="2c378-118">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2c378-119">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="2c378-119">Configuration Files</span></span>  

 <span data-ttu-id="2c378-120">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="2c378-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c378-121">Пример</span><span class="sxs-lookup"><span data-stu-id="2c378-121">Example</span></span>  

 <span data-ttu-id="2c378-122">В следующем примере очищаются все модули веб-запросов, а затем выполняется регистрация модуля веб-запросов для HTTP.</span><span class="sxs-lookup"><span data-stu-id="2c378-122">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c378-123">См. также</span><span class="sxs-lookup"><span data-stu-id="2c378-123">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="2c378-124">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="2c378-124">Network Settings Schema</span></span>](index.md)
