---
description: 'Дополнительные сведения о: <remove> элемент для webRequestModules (параметры сети)'
title: Элемент <remove> для webRequestModules (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
ms.openlocfilehash: db65c91417af2538e27b65e0ae28d06a6bfcde0a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713004"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="d6632-103">Элемент \<remove> для webRequestModules (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="d6632-103">\<remove> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="d6632-104">Удаляет пользовательский модуль веб-запросов из приложения.</span><span class="sxs-lookup"><span data-stu-id="d6632-104">Removes a custom Web request module from the application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**
  
## <a name="syntax"></a><span data-ttu-id="d6632-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d6632-105">Syntax</span></span>  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6632-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d6632-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d6632-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d6632-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6632-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d6632-108">Attributes</span></span>  
  
|<span data-ttu-id="d6632-109">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="d6632-109">**Attribute**</span></span>|<span data-ttu-id="d6632-110">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d6632-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="d6632-111">Префикс URI для запросов, обрабатываемых этим модулем веб-запросов.</span><span class="sxs-lookup"><span data-stu-id="d6632-111">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6632-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d6632-112">Child Elements</span></span>  

 <span data-ttu-id="d6632-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="d6632-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6632-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d6632-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d6632-115">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="d6632-115">**Element**</span></span>|<span data-ttu-id="d6632-116">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d6632-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d6632-117">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="d6632-117">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="d6632-118">Указывает модули, используемые для запроса сведений от сетевых узлов.</span><span class="sxs-lookup"><span data-stu-id="d6632-118">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6632-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="d6632-119">Remarks</span></span>  

 <span data-ttu-id="d6632-120">`remove`Элемент удаляет зарегистрированный модуль веб-запросов для указанного префикса URI.</span><span class="sxs-lookup"><span data-stu-id="d6632-120">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="d6632-121">Значение `prefix` атрибута должно быть начальными символами допустимого универсального кода ресурса (URI), например " `http` " или " `http://www.contoso.com` ".</span><span class="sxs-lookup"><span data-stu-id="d6632-121">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d6632-122">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="d6632-122">Configuration Files</span></span>  

 <span data-ttu-id="d6632-123">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d6632-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6632-124">Пример</span><span class="sxs-lookup"><span data-stu-id="d6632-124">Example</span></span>  

<span data-ttu-id="d6632-125">В следующем примере удаляется существующий модуль веб-запросов для HTTP, а затем регистрируется новый пользовательский модуль веб-запросов для HTTP-запросов к `www.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="d6632-125">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6632-126">См. также</span><span class="sxs-lookup"><span data-stu-id="d6632-126">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="d6632-127">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="d6632-127">Network Settings Schema</span></span>](index.md)
