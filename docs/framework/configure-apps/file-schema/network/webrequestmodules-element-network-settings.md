---
description: 'Дополнительные сведения о <webRequestModules> элементе: Element (параметры сети)'
title: Элемент <webRequestModules> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 851aec2bf38910239874cb5792239a48de6efb70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698431"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="b2341-103">Элемент \<webRequestModules> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="b2341-103">\<webRequestModules> Element (Network Settings)</span></span>

<span data-ttu-id="b2341-104">Указывает модули, используемые для запроса сведений от сетевых узлов.</span><span class="sxs-lookup"><span data-stu-id="b2341-104">Specifies modules to use to request information from network hosts.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a><span data-ttu-id="b2341-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b2341-105">Syntax</span></span>  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2341-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b2341-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b2341-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b2341-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2341-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b2341-108">Attributes</span></span>  

 <span data-ttu-id="b2341-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b2341-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b2341-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b2341-110">Child Elements</span></span>  
  
|<span data-ttu-id="b2341-111">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="b2341-111">**Element**</span></span>|<span data-ttu-id="b2341-112">**Описание**</span><span class="sxs-lookup"><span data-stu-id="b2341-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b2341-113">add</span><span class="sxs-lookup"><span data-stu-id="b2341-113">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="b2341-114">Добавляет пользовательский модуль веб-запросов в приложение.</span><span class="sxs-lookup"><span data-stu-id="b2341-114">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="b2341-115">пусто</span><span class="sxs-lookup"><span data-stu-id="b2341-115">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="b2341-116">Удаляет из приложения все зарегистрированные модули веб-запросов.</span><span class="sxs-lookup"><span data-stu-id="b2341-116">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="b2341-117">remove</span><span class="sxs-lookup"><span data-stu-id="b2341-117">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="b2341-118">Удаляет пользовательский модуль веб-запросов из приложения.</span><span class="sxs-lookup"><span data-stu-id="b2341-118">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b2341-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b2341-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b2341-120">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="b2341-120">**Element**</span></span>|<span data-ttu-id="b2341-121">**Описание**</span><span class="sxs-lookup"><span data-stu-id="b2341-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b2341-122">system.net</span><span class="sxs-lookup"><span data-stu-id="b2341-122">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="b2341-123">Содержит параметры сети, определяющие способ подключения .NET Framework к Интернету.</span><span class="sxs-lookup"><span data-stu-id="b2341-123">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2341-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="b2341-124">Remarks</span></span>  

 <span data-ttu-id="b2341-125">Элемент `webRequestModules` регистрирует потомки класса <xref:System.Net.WebRequest>, чтобы обработать запросы информации к сетевым узлам.</span><span class="sxs-lookup"><span data-stu-id="b2341-125">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="b2341-126">Модули веб-запросов должны реализовывать <xref:System.Net.IWebRequestCreate> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="b2341-126">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="b2341-127">Платформа .NET Framework включает модули веб-запросов для URI, которые начинаются с `http://` , `https://` и `file://` .</span><span class="sxs-lookup"><span data-stu-id="b2341-127">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="b2341-128">Модули по умолчанию можно переопределить только путем регистрации пользовательского модуля в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b2341-128">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b2341-129">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="b2341-129">Configuration Files</span></span>  

 <span data-ttu-id="b2341-130">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b2341-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2341-131">Пример</span><span class="sxs-lookup"><span data-stu-id="b2341-131">Example</span></span>  

 <span data-ttu-id="b2341-132">В следующем примере регистрируется HTTP-модуль по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b2341-132">The following example registers the default HTTP module.</span></span> <span data-ttu-id="b2341-133">Необходимо заменить значения для Version и PublicKeyToken правильными значениями для указанного модуля.</span><span class="sxs-lookup"><span data-stu-id="b2341-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2341-134">См. также</span><span class="sxs-lookup"><span data-stu-id="b2341-134">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="b2341-135">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="b2341-135">Network Settings Schema</span></span>](index.md)
