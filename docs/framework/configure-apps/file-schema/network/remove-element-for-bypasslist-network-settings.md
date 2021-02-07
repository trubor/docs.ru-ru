---
description: 'Дополнительные сведения о: <remove> элемент для бипасслист (параметры сети)'
title: Элемент <remove> для bypasslist (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 48441f1b402b339a1bd2ea069678afb4b1d5f2e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740292"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="f8219-103">Элемент \<remove> для bypasslist (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="f8219-103">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="f8219-104">Удаляет IP-адрес или DNS-имя из списка обхода прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="f8219-104">Removes an IP address or DNS name from the proxy bypass list.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  

## <a name="syntax"></a><span data-ttu-id="f8219-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f8219-105">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8219-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="f8219-106">Attributes and Elements</span></span>

<span data-ttu-id="f8219-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f8219-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8219-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f8219-108">Attributes</span></span>

|<span data-ttu-id="f8219-109">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="f8219-109">**Attribute**</span></span>|<span data-ttu-id="f8219-110">**Описание**</span><span class="sxs-lookup"><span data-stu-id="f8219-110">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="f8219-111">Регулярное выражение, описывающее IP-адрес или DNS-имя.</span><span class="sxs-lookup"><span data-stu-id="f8219-111">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f8219-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f8219-112">Child Elements</span></span>

<span data-ttu-id="f8219-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="f8219-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f8219-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f8219-114">Parent Elements</span></span>

|<span data-ttu-id="f8219-115">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="f8219-115">**Element**</span></span>|<span data-ttu-id="f8219-116">**Описание**</span><span class="sxs-lookup"><span data-stu-id="f8219-116">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="f8219-117">bypasslist</span><span class="sxs-lookup"><span data-stu-id="f8219-117">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="f8219-118">Предоставляет набор регулярных выражений, описывающих адреса, которые не используют прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="f8219-118">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f8219-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="f8219-119">Remarks</span></span>

<span data-ttu-id="f8219-120">`remove`Элемент удаляет регулярные выражения, описывающие IP-адреса или имена DNS-серверов, из списка адресов, которые обходят прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="f8219-120">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="f8219-121">Адреса были определены ранее в файле конфигурации или на более высоком уровне иерархии конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f8219-121">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="f8219-122">Значение `address` атрибута должно быть регулярным выражением, описывающим набор IP-адресов или имен узлов.</span><span class="sxs-lookup"><span data-stu-id="f8219-122">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="f8219-123">Дополнительные сведения о регулярных выражениях см. в разделе. [Платформа .NET Framework регулярных выражений](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f8219-123">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="f8219-124">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="f8219-124">Configuration Files</span></span>

<span data-ttu-id="f8219-125">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="f8219-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="f8219-126">Пример</span><span class="sxs-lookup"><span data-stu-id="f8219-126">Example</span></span>

<span data-ttu-id="f8219-127">В следующем примере удаляется предыдущее определение для домена adventure-works.com, а затем домен contoso.com добавляется в список обхода.</span><span class="sxs-lookup"><span data-stu-id="f8219-127">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f8219-128">См. также</span><span class="sxs-lookup"><span data-stu-id="f8219-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="f8219-129">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="f8219-129">Network Settings Schema</span></span>](index.md)
