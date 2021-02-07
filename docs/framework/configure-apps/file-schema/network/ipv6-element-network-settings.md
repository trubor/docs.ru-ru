---
description: 'Дополнительные сведения о <ipv6> элементе: Element (параметры сети)'
title: Элемент <ipv6> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: 667acaebdb290140f67ea36020bb191cd1a44f34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698652"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="725ad-103">Элемент \<ipv6> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="725ad-103">\<ipv6> Element (Network Settings)</span></span>

<span data-ttu-id="725ad-104">Включает отклики протокола IP версии 6 (IPv6) от устаревших членов <xref:System.Net.Dns> класса.</span><span class="sxs-lookup"><span data-stu-id="725ad-104">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ipv6>**

## <a name="syntax"></a><span data-ttu-id="725ad-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="725ad-105">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="725ad-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="725ad-106">Attributes and Elements</span></span>  

 <span data-ttu-id="725ad-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="725ad-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="725ad-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="725ad-108">Attributes</span></span>  
  
|<span data-ttu-id="725ad-109">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="725ad-109">**Attribute**</span></span>|<span data-ttu-id="725ad-110">**Описание**</span><span class="sxs-lookup"><span data-stu-id="725ad-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="725ad-111">Указывает, <xref:System.Net.Dns> возвращают ли члены класса IPv6-адреса.</span><span class="sxs-lookup"><span data-stu-id="725ad-111">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="725ad-112">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="725ad-112">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="725ad-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="725ad-113">Child Elements</span></span>  

 <span data-ttu-id="725ad-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="725ad-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="725ad-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="725ad-115">Parent Elements</span></span>  
  
|<span data-ttu-id="725ad-116">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="725ad-116">**Element**</span></span>|<span data-ttu-id="725ad-117">**Описание**</span><span class="sxs-lookup"><span data-stu-id="725ad-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="725ad-118">параметры</span><span class="sxs-lookup"><span data-stu-id="725ad-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="725ad-119">Настраивает основные параметры сети для пространства имен <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="725ad-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="725ad-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="725ad-120">Remarks</span></span>  

 <span data-ttu-id="725ad-121">Этот параметр включает поддержку IPv6 для устаревших членов <xref:System.Net.Dns> класса: <xref:System.Net.Dns.BeginGetHostByName%2A> , <xref:System.Net.Dns.BeginResolve%2A> ,,, <xref:System.Net.Dns.EndGetHostByName%2A> , <xref:System.Net.Dns.EndResolve%2A> <xref:System.Net.Dns.GetHostByAddress%2A> <xref:System.Net.Dns.GetHostByName%2A> и <xref:System.Net.Dns.Resolve%2A> .</span><span class="sxs-lookup"><span data-stu-id="725ad-121">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="725ad-122">Для других членов <xref:System.Net?displayProperty=nameWithType> пространства имен IPv6-адреса могут возвращаться, если в операционной системе включен протокол IPv6.</span><span class="sxs-lookup"><span data-stu-id="725ad-122">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="725ad-123">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="725ad-123">Configuration Files</span></span>  

 <span data-ttu-id="725ad-124">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="725ad-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="725ad-125">Пример</span><span class="sxs-lookup"><span data-stu-id="725ad-125">Example</span></span>  

 <span data-ttu-id="725ad-126">В следующем примере показано, как включить поддержку IPv6 для <xref:System.Net.Dns> класса.</span><span class="sxs-lookup"><span data-stu-id="725ad-126">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="725ad-127">См. также</span><span class="sxs-lookup"><span data-stu-id="725ad-127">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="725ad-128">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="725ad-128">Network Settings Schema</span></span>](index.md)
