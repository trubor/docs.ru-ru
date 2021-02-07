---
description: 'Дополнительные сведения о: <add> элемент для webRequestModules (параметры сети)'
title: Элемент <add> для webRequestModules (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: 1edb63a1e1095bb4b3c3d749fd389ffaad5ddf9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729899"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="9f315-103">Элемент \<add> для webRequestModules (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="9f315-103">\<add> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="9f315-104">Добавляет пользовательский модуль веб-запросов в приложение.</span><span class="sxs-lookup"><span data-stu-id="9f315-104">Adds a custom Web request module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="9f315-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9f315-105">Syntax</span></span>  
  
```xml  
<add
  prefix="URI prefix"
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f315-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="9f315-106">Attributes and Elements</span></span>  

 <span data-ttu-id="9f315-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="9f315-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f315-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="9f315-108">Attributes</span></span>  
  
|<span data-ttu-id="9f315-109">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="9f315-109">**Attribute**</span></span>|<span data-ttu-id="9f315-110">**Описание**</span><span class="sxs-lookup"><span data-stu-id="9f315-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="9f315-111">Префикс URI для запросов, обрабатываемых этим модулем веб-запросов.</span><span class="sxs-lookup"><span data-stu-id="9f315-111">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="9f315-112">Полное имя типа (обозначенное <xref:System.Type.FullName%2A> свойством) и имя сборки (обозначенное <xref:System.Reflection.Assembly.FullName%2A> свойством), разделенные запятыми, которые реализуют этот модуль веб-запросов.</span><span class="sxs-lookup"><span data-stu-id="9f315-112">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f315-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="9f315-113">Child Elements</span></span>  

 <span data-ttu-id="9f315-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="9f315-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f315-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="9f315-115">Parent Elements</span></span>  
  
|<span data-ttu-id="9f315-116">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="9f315-116">**Element**</span></span>|<span data-ttu-id="9f315-117">**Описание**</span><span class="sxs-lookup"><span data-stu-id="9f315-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9f315-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="9f315-118">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="9f315-119">Указывает модули, используемые для запроса сведений от сетевых узлов.</span><span class="sxs-lookup"><span data-stu-id="9f315-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f315-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="9f315-120">Remarks</span></span>  

 <span data-ttu-id="9f315-121">`prefix`Атрибут определяет префикс URI, который использует указанный модуль веб-запросов.</span><span class="sxs-lookup"><span data-stu-id="9f315-121">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="9f315-122">Модули веб-запросов обычно регистрируются для работы с конкретным протоколом, например HTTP или FTP, но могут быть зарегистрированы, чтобы обрабатывать запросы к определенному серверу или пути на сервере.</span><span class="sxs-lookup"><span data-stu-id="9f315-122">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="9f315-123">Модуль веб-запросов создается, когда в метод передается соответствующий префикс URI <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9f315-123">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="9f315-124">Значение `prefix` атрибута должно быть начальными символами допустимого URI.</span><span class="sxs-lookup"><span data-stu-id="9f315-124">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="9f315-125">Например, `http` или `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="9f315-125">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="9f315-126">Значением `type` атрибута должно быть допустимое имя типа и соответствующее имя сборки, разделенные запятыми.</span><span class="sxs-lookup"><span data-stu-id="9f315-126">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="9f315-127">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="9f315-127">Configuration Files</span></span>  

 <span data-ttu-id="9f315-128">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="9f315-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f315-129">Пример</span><span class="sxs-lookup"><span data-stu-id="9f315-129">Example</span></span>  

 <span data-ttu-id="9f315-130">В следующем примере регистрируется пользовательский модуль веб-запросов для HTTP.</span><span class="sxs-lookup"><span data-stu-id="9f315-130">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="9f315-131">Необходимо заменить значения для Version и PublicKeyToken правильными значениями для указанного модуля.</span><span class="sxs-lookup"><span data-stu-id="9f315-131">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f315-132">См. также</span><span class="sxs-lookup"><span data-stu-id="9f315-132">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="9f315-133">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="9f315-133">Network Settings Schema</span></span>](index.md)
