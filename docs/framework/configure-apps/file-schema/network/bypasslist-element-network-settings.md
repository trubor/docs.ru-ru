---
title: Элемент <bypasslist> (параметры сети)
description: <bypasslist>Элемент Network Settings предоставляет набор регулярных выражений, описывающих адреса, которые не используют прокси-сервер в платформа .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 0a03b391c839b7255fdd423a305d474d0e48ad39
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259360"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="a8706-103">Элемент \<bypasslist> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="a8706-103">\<bypasslist> Element (Network Settings)</span></span>

<span data-ttu-id="a8706-104">Предоставляет набор регулярных выражений, описывающих адреса, которые не используют прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="a8706-104">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a><span data-ttu-id="a8706-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a8706-105">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8706-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a8706-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a8706-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a8706-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8706-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a8706-108">Attributes</span></span>  

 <span data-ttu-id="a8706-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="a8706-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a8706-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a8706-110">Child Elements</span></span>  
  
|<span data-ttu-id="a8706-111">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="a8706-111">**Element**</span></span>|<span data-ttu-id="a8706-112">**Описание**</span><span class="sxs-lookup"><span data-stu-id="a8706-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a8706-113">add</span><span class="sxs-lookup"><span data-stu-id="a8706-113">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="a8706-114">Добавление в список обхода прокси IP-адреса или DNS-имени.</span><span class="sxs-lookup"><span data-stu-id="a8706-114">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="a8706-115">пусто</span><span class="sxs-lookup"><span data-stu-id="a8706-115">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="a8706-116">Очищает список обхода.</span><span class="sxs-lookup"><span data-stu-id="a8706-116">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="a8706-117">remove</span><span class="sxs-lookup"><span data-stu-id="a8706-117">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="a8706-118">Удаляет IP-адрес или DNS-имя из списка обхода прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="a8706-118">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8706-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a8706-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a8706-120">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="a8706-120">**Element**</span></span>|<span data-ttu-id="a8706-121">**Описание**</span><span class="sxs-lookup"><span data-stu-id="a8706-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a8706-122">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="a8706-122">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="a8706-123">Настраивает прокси-сервер протокола передачи гипертекста (HTTP).</span><span class="sxs-lookup"><span data-stu-id="a8706-123">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8706-124">Комментарии</span><span class="sxs-lookup"><span data-stu-id="a8706-124">Remarks</span></span>  

 <span data-ttu-id="a8706-125">Список обхода содержит регулярные выражения, описывающие URI, которые <xref:System.Net.WebRequest> обращаются к экземплярам напрямую, а не через прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="a8706-125">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="a8706-126">При указании регулярного выражения для этого элемента следует соблюдать осторожность.</span><span class="sxs-lookup"><span data-stu-id="a8706-126">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="a8706-127">Регулярное выражение `[a-z]+\\.contoso\\.com` соответствует любому узлу в домене contoso.com, но оно также соответствует любому узлу в домене contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="a8706-127">The regular expression `[a-z]+\\.contoso\\.com` matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="a8706-128">Чтобы сопоставить только узел в домене contoso.com, используйте привязку ( `$` ): `[a-z]+\\.contoso\\.com$` .</span><span class="sxs-lookup"><span data-stu-id="a8706-128">To match only a host in the contoso.com domain, use an anchor (`$`): `[a-z]+\\.contoso\\.com$`.</span></span>
  
 <span data-ttu-id="a8706-129">Дополнительные сведения о регулярных выражениях см. в разделе. [Платформа .NET Framework регулярных выражений](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a8706-129">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a8706-130">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="a8706-130">Configuration Files</span></span>  

 <span data-ttu-id="a8706-131">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a8706-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8706-132">Пример</span><span class="sxs-lookup"><span data-stu-id="a8706-132">Example</span></span>  

 <span data-ttu-id="a8706-133">В следующем примере в список обхода добавляется два адреса.</span><span class="sxs-lookup"><span data-stu-id="a8706-133">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="a8706-134">Первый обход прокси-сервера для всех серверов в домене contoso.com; во втором случае прокси-сервер обходится для всех серверов, IP-адреса которых начинаются с 192,168.</span><span class="sxs-lookup"><span data-stu-id="a8706-134">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a8706-135">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a8706-135">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="a8706-136">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="a8706-136">Network Settings Schema</span></span>](index.md)
