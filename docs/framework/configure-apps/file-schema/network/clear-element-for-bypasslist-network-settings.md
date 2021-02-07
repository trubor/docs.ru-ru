---
description: 'Дополнительные сведения о: <clear> элемент для бипасслист (параметры сети)'
title: Элемент <clear> для bypasslist (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: 4ddb66c837c55391a19826c44c6df7a3e88c8e0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729904"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="2c119-103">Элемент \<clear> для bypasslist (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="2c119-103">\<clear> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="2c119-104">Очищает список обхода прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="2c119-104">Clears the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="2c119-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2c119-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c119-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="2c119-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2c119-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="2c119-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c119-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2c119-108">Attributes</span></span>  

 <span data-ttu-id="2c119-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="2c119-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2c119-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="2c119-110">Child Elements</span></span>  

 <span data-ttu-id="2c119-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="2c119-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c119-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="2c119-112">Parent Elements</span></span>  
  
|<span data-ttu-id="2c119-113">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="2c119-113">**Element**</span></span>|<span data-ttu-id="2c119-114">**Описание**</span><span class="sxs-lookup"><span data-stu-id="2c119-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2c119-115">bypasslist</span><span class="sxs-lookup"><span data-stu-id="2c119-115">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="2c119-116">Предоставляет набор регулярных выражений, описывающих адреса, которые не используют прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="2c119-116">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c119-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="2c119-117">Remarks</span></span>  

 <span data-ttu-id="2c119-118">`clear`Элемент удаляет все записи из списка обхода.</span><span class="sxs-lookup"><span data-stu-id="2c119-118">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2c119-119">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="2c119-119">Configuration Files</span></span>  

 <span data-ttu-id="2c119-120">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="2c119-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c119-121">Пример</span><span class="sxs-lookup"><span data-stu-id="2c119-121">Example</span></span>  

 <span data-ttu-id="2c119-122">В следующем примере очищается список обхода, а затем два адреса добавляются в список обхода.</span><span class="sxs-lookup"><span data-stu-id="2c119-122">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="2c119-123">Первый обход прокси-сервера для всех серверов в домене contoso.com; во втором пропускается прокси-сервер для всех серверов, IP-адрес которых начинается с 192,168.</span><span class="sxs-lookup"><span data-stu-id="2c119-123">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="2c119-124">См. также</span><span class="sxs-lookup"><span data-stu-id="2c119-124">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="2c119-125">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="2c119-125">Network Settings Schema</span></span>](index.md)
