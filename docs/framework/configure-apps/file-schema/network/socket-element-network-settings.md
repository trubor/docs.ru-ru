---
description: 'Дополнительные сведения о <socket> элементе: Element (параметры сети)'
title: Элемент <socket> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: 564d6566bf6f6b1997b986cb6c0d85f841195e55
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740136"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="7dd60-103">Элемент \<socket> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="7dd60-103">\<socket> Element (Network Settings)</span></span>

<span data-ttu-id="7dd60-104">Указывает, используют ли операции сокета порты завершения.</span><span class="sxs-lookup"><span data-stu-id="7dd60-104">Specifies whether socket operations use completion ports.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**

## <a name="syntax"></a><span data-ttu-id="7dd60-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7dd60-105">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7dd60-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="7dd60-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7dd60-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="7dd60-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7dd60-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="7dd60-108">Attributes</span></span>  
  
|<span data-ttu-id="7dd60-109">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="7dd60-109">**Attribute**</span></span>|<span data-ttu-id="7dd60-110">**Описание**</span><span class="sxs-lookup"><span data-stu-id="7dd60-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="7dd60-111">Указывает, должен ли сокет всегда использовать порты завершения для вызовов метода Accept.</span><span class="sxs-lookup"><span data-stu-id="7dd60-111">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="7dd60-112">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="7dd60-112">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="7dd60-113">Указывает, должен ли сокет всегда использовать порты завершения для вызовов метода Connect.</span><span class="sxs-lookup"><span data-stu-id="7dd60-113">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="7dd60-114">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="7dd60-114">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="7dd60-115">Указывает значение по умолчанию, <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> используемое для сокета.</span><span class="sxs-lookup"><span data-stu-id="7dd60-115">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="7dd60-116">Значение по умолчанию зависит от версии Windows.</span><span class="sxs-lookup"><span data-stu-id="7dd60-116">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7dd60-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="7dd60-117">Child Elements</span></span>  

 <span data-ttu-id="7dd60-118">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="7dd60-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7dd60-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="7dd60-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7dd60-120">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="7dd60-120">**Element**</span></span>|<span data-ttu-id="7dd60-121">**Описание**</span><span class="sxs-lookup"><span data-stu-id="7dd60-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7dd60-122">параметры</span><span class="sxs-lookup"><span data-stu-id="7dd60-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="7dd60-123">Настраивает основные параметры сети для пространства имен <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="7dd60-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7dd60-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="7dd60-124">Remarks</span></span>  

 <span data-ttu-id="7dd60-125">Атрибуты `alwaysUseCompletionPortsForAccept` и `alwaysUseCompletionPortsForConnect` используются для задания поведения по умолчанию в отношении использования портов завершения классами в пространстве имен <xref:System.Net.Sockets?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7dd60-125">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="7dd60-126">Порты завершения рекомендуются для высокопроизводительных серверных приложений.</span><span class="sxs-lookup"><span data-stu-id="7dd60-126">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="7dd60-127">По умолчанию для `alwaysUseCompletionPortsForAccept` атрибутов и `alwaysUseCompletionPortsForConnect` задано значение **false**.</span><span class="sxs-lookup"><span data-stu-id="7dd60-127">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="7dd60-128"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A>Можно использовать для получения текущего значения `alwaysUseCompletionPortsForAccept` атрибута из применимых файлов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="7dd60-128">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="7dd60-129"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>Можно использовать для получения текущего значения `alwaysUseCompletionPortsForConnect` атрибута из применимых файлов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="7dd60-129">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="7dd60-130">`ipProtectionLevel`Атрибут указывает значение по умолчанию, <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> используемое для сокета.</span><span class="sxs-lookup"><span data-stu-id="7dd60-130">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="7dd60-131"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>Свойство позволяет настроить ограничение сокета IPv6 на указанную область, например адреса с одинаковой локальной ссылкой или локальным префиксом сайта.</span><span class="sxs-lookup"><span data-stu-id="7dd60-131">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="7dd60-132">Этот параметр позволяет приложениям размещать ограничения доступа к сокетам IPv6.</span><span class="sxs-lookup"><span data-stu-id="7dd60-132">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="7dd60-133">Такие ограничения позволяют приложению, работающему в частной локальной сети, просто и надежно защититься от внешних атак.</span><span class="sxs-lookup"><span data-stu-id="7dd60-133">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="7dd60-134">Этот параметр расширяет или ограничивает область действия прослушивающего сокета, обеспечивая неограниченный доступ от общедоступных и частных пользователей при необходимости или ограничивающий доступ только для того же сайта, если это необходимо.</span><span class="sxs-lookup"><span data-stu-id="7dd60-134">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="7dd60-135">Этот `ipProtectionLevel` параметр атрибута влияет только на первоначальный входящий трафик.</span><span class="sxs-lookup"><span data-stu-id="7dd60-135">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="7dd60-136">TCP-сервер, прослушивающий входящие подключения на сокете.</span><span class="sxs-lookup"><span data-stu-id="7dd60-136">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="7dd60-137">Приложение UDP, получающее пакет на сокете.</span><span class="sxs-lookup"><span data-stu-id="7dd60-137">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="7dd60-138">Этот параметр конфигурации не влияет на уже установленные TCP-подключения (трафик в обоих направлениях не ограничен) и не влияет на приложение, отправляющее пакеты UDP.</span><span class="sxs-lookup"><span data-stu-id="7dd60-138">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="7dd60-139">Возможные значения для `ipProtectionLevel` параметра атрибута соответствуют определенным уровням защиты, указанным в <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> перечислении, следующим образом:</span><span class="sxs-lookup"><span data-stu-id="7dd60-139">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="7dd60-140">**Значение атрибута**</span><span class="sxs-lookup"><span data-stu-id="7dd60-140">**Attribute Value**</span></span>|<span data-ttu-id="7dd60-141">**Описание**</span><span class="sxs-lookup"><span data-stu-id="7dd60-141">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="7dd60-142">еджерестриктед</span><span class="sxs-lookup"><span data-stu-id="7dd60-142">EdgeRestricted</span></span>|<span data-ttu-id="7dd60-143">Уровень защиты IP — предельно ограничено.</span><span class="sxs-lookup"><span data-stu-id="7dd60-143">The IP protection level is edge restricted.</span></span> <span data-ttu-id="7dd60-144">Это значение используется приложениями, разработанными для работы в Интернете.</span><span class="sxs-lookup"><span data-stu-id="7dd60-144">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="7dd60-145">Этот параметр не позволяет обойти механизм преобразования сетевых адресов (NAT) с помощью реализации Windows Teredo.</span><span class="sxs-lookup"><span data-stu-id="7dd60-145">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="7dd60-146">Эти приложения могут обходить брандмауэры протокола IPv4, поэтому они должны быть защищены от атак из Интернета, направленных на открытый порт.</span><span class="sxs-lookup"><span data-stu-id="7dd60-146">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="7dd60-147">В Windows Server 2003 и Windows XP значение по умолчанию для уровня защиты IP сокета — предельно ограничено.</span><span class="sxs-lookup"><span data-stu-id="7dd60-147">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="7dd60-148">С ограниченным доступом</span><span class="sxs-lookup"><span data-stu-id="7dd60-148">Restricted</span></span>|<span data-ttu-id="7dd60-149">Уровень защиты IP — ограничено.</span><span class="sxs-lookup"><span data-stu-id="7dd60-149">The IP protection level is restricted.</span></span> <span data-ttu-id="7dd60-150">Это значение используется приложениями интрасети, не работающих в Интернете.</span><span class="sxs-lookup"><span data-stu-id="7dd60-150">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="7dd60-151">Эти приложения обычно не тестируются и не защищаются против атак из Интернета.</span><span class="sxs-lookup"><span data-stu-id="7dd60-151">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="7dd60-152">Этот параметр ограничивает получаемый трафик локальным.</span><span class="sxs-lookup"><span data-stu-id="7dd60-152">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="7dd60-153">С неограниченным доступом</span><span class="sxs-lookup"><span data-stu-id="7dd60-153">Unrestricted</span></span>|<span data-ttu-id="7dd60-154">Уровень защиты IP — неограниченно.</span><span class="sxs-lookup"><span data-stu-id="7dd60-154">The IP protection level is unrestricted.</span></span> <span data-ttu-id="7dd60-155">Это значение используется приложениями, разработанными для работы в Интернете, включая приложения, использующие возможности обхода IPv6 NAT, включенные в Windows (например, Teredo).</span><span class="sxs-lookup"><span data-stu-id="7dd60-155">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="7dd60-156">Эти приложения могут обходить брандмауэры протокола IPv4, поэтому они должны быть защищены от атак из Интернета, направленных на открытый порт.</span><span class="sxs-lookup"><span data-stu-id="7dd60-156">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="7dd60-157">В Windows Server 2008 R2 и Windows Vista значение по умолчанию для уровня защиты IP сокета — неограниченно.</span><span class="sxs-lookup"><span data-stu-id="7dd60-157">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="7dd60-158">Не указан</span><span class="sxs-lookup"><span data-stu-id="7dd60-158">Unspecified</span></span>|<span data-ttu-id="7dd60-159">Уровень защиты IP — не указано.</span><span class="sxs-lookup"><span data-stu-id="7dd60-159">The IP protection level is unspecified.</span></span> <span data-ttu-id="7dd60-160">В Windows 7 и Windows Server 2008 R2 и значение по умолчанию для уровня защиты IP сокета — не указано.</span><span class="sxs-lookup"><span data-stu-id="7dd60-160">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="7dd60-161">Значение по умолчанию для `ipProtectionLevel` атрибута не **указано**.</span><span class="sxs-lookup"><span data-stu-id="7dd60-161">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="7dd60-162"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>Свойство можно использовать для получения текущего значения `ipProtectionLevel` атрибута из применимых файлов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="7dd60-162">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7dd60-163">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="7dd60-163">Configuration Files</span></span>  

 <span data-ttu-id="7dd60-164">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="7dd60-164">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dd60-165">Пример</span><span class="sxs-lookup"><span data-stu-id="7dd60-165">Example</span></span>  

 <span data-ttu-id="7dd60-166">В следующем примере показано, как указать, что порты завершения должны использоваться и что значение по умолчанию <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> должно быть неограниченным.</span><span class="sxs-lookup"><span data-stu-id="7dd60-166">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7dd60-167">См. также</span><span class="sxs-lookup"><span data-stu-id="7dd60-167">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="7dd60-168">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="7dd60-168">Network Settings Schema</span></span>](index.md)
