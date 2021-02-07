---
description: 'Дополнительные сведения о: <add> элемент для бипасслист (параметры сети)'
title: Элемент <add> для bypasslist (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 6bbd42cdf5d3b9bc31326b619cde96cfac0c755a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698639"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="7003f-103">Элемент \<add> для bypasslist (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="7003f-103">\<add> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="7003f-104">Добавление в список обхода прокси IP-адреса или DNS-имени.</span><span class="sxs-lookup"><span data-stu-id="7003f-104">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="7003f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7003f-105">Syntax</span></span>  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7003f-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="7003f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7003f-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="7003f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7003f-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="7003f-108">Attributes</span></span>  
  
|<span data-ttu-id="7003f-109">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="7003f-109">**Attribute**</span></span>|<span data-ttu-id="7003f-110">**Описание**</span><span class="sxs-lookup"><span data-stu-id="7003f-110">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="7003f-111">**address**</span><span class="sxs-lookup"><span data-stu-id="7003f-111">**address**</span></span>|<span data-ttu-id="7003f-112">Регулярное выражение, описывающее IP-адрес или DNS-имя.</span><span class="sxs-lookup"><span data-stu-id="7003f-112">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7003f-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="7003f-113">Child Elements</span></span>  

 <span data-ttu-id="7003f-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="7003f-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7003f-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="7003f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="7003f-116">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="7003f-116">**Element**</span></span>|<span data-ttu-id="7003f-117">**Описание**</span><span class="sxs-lookup"><span data-stu-id="7003f-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7003f-118">bypasslist</span><span class="sxs-lookup"><span data-stu-id="7003f-118">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="7003f-119">Предоставляет набор регулярных выражений, описывающих адреса, которые не используют прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="7003f-119">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7003f-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="7003f-120">Remarks</span></span>  

 <span data-ttu-id="7003f-121">`add`Элемент вставляет регулярные выражения, описывающие IP-адреса или имена DNS-серверов, в список адресов, которые обходят прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="7003f-121">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="7003f-122">Значение `address` атрибута должно быть регулярным выражением, описывающим набор IP-адресов или имен узлов.</span><span class="sxs-lookup"><span data-stu-id="7003f-122">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="7003f-123">При указании регулярного выражения для этого элемента следует соблюдать осторожность.</span><span class="sxs-lookup"><span data-stu-id="7003f-123">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="7003f-124">Регулярное выражение "[a-z] + \\ . contoso \\ . com" соответствует любому узлу в домене contoso.com, но также соответствует любому узлу в домене contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="7003f-124">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="7003f-125">Чтобы сопоставить только узел в домене contoso.com, используйте привязку ("$"): "[a-z] + \\ . contoso \\ . com $".</span><span class="sxs-lookup"><span data-stu-id="7003f-125">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="7003f-126">Дополнительные сведения о регулярных выражениях см. в разделе. [Платформа .NET Framework регулярных выражений](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="7003f-126">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7003f-127">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="7003f-127">Configuration Files</span></span>  

 <span data-ttu-id="7003f-128">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="7003f-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7003f-129">Пример</span><span class="sxs-lookup"><span data-stu-id="7003f-129">Example</span></span>  

 <span data-ttu-id="7003f-130">В следующем примере в список обхода добавляется два адреса.</span><span class="sxs-lookup"><span data-stu-id="7003f-130">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="7003f-131">Первый обход прокси-сервера для всех серверов в домене contoso.com; во втором пропускается прокси-сервер для всех серверов, IP-адрес которых начинается с 192,168.</span><span class="sxs-lookup"><span data-stu-id="7003f-131">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7003f-132">См. также</span><span class="sxs-lookup"><span data-stu-id="7003f-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="7003f-133">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="7003f-133">Network Settings Schema</span></span>](index.md)
