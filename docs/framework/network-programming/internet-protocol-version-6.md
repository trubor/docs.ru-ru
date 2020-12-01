---
title: протокол IP версии 6
description: Узнайте о протоколе IPv6 и его отличиях от IPv4. Приложения .NET Framework поддерживают протокол IPv6, но для этого может потребоваться специальная настройка конфигурации.
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: f5b74674ba4144f75d125267f2458394bb74fab1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283956"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="e63df-104">протокол IP версии 6</span><span class="sxs-lookup"><span data-stu-id="e63df-104">Internet Protocol Version 6</span></span>

<span data-ttu-id="e63df-105">Протокол IP версии 6 (IPv6) — это новый набор стандартных протоколов для сетевого уровня Интернета.</span><span class="sxs-lookup"><span data-stu-id="e63df-105">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="e63df-106">IPv6 позволяет устранить множество проблем текущей версии набора интернет-протоколов (известного как IPv4), связанных с нехваткой адресов, безопасностью, автоматической настройкой, расширяемостью и т. д.</span><span class="sxs-lookup"><span data-stu-id="e63df-106">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="e63df-107">IPv6 расширяет возможности Интернета для активации новых видов приложений, включая приложения для одноранговой сети и мобильных устройств.</span><span class="sxs-lookup"><span data-stu-id="e63df-107">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="e63df-108">Ниже приведены основные проблемы текущего протокола IPv4.</span><span class="sxs-lookup"><span data-stu-id="e63df-108">The following are the main issues of the current IPv4 protocol:</span></span>  
  
- <span data-ttu-id="e63df-109">Быстрое исчерпание диапазона адресов.</span><span class="sxs-lookup"><span data-stu-id="e63df-109">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="e63df-110">Это привело к использованию трансляторов сетевых адресов (NAT), которые сопоставляют несколько частных адресов с одним общедоступным IP-адресом.</span><span class="sxs-lookup"><span data-stu-id="e63df-110">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="e63df-111">Основными проблемами, создаваемыми этим механизмом, являются затраты на обработку и отсутствие сквозной связи.</span><span class="sxs-lookup"><span data-stu-id="e63df-111">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
- <span data-ttu-id="e63df-112">Отсутствие поддержки иерархии.</span><span class="sxs-lookup"><span data-stu-id="e63df-112">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="e63df-113">Из-за своей изначально предопределенной организации классов в IPv4 отсутствует настоящая иерархическая поддержка.</span><span class="sxs-lookup"><span data-stu-id="e63df-113">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="e63df-114">Невозможно структурировать IP-адреса таким образом, который действительно сопоставляет топологию сети.</span><span class="sxs-lookup"><span data-stu-id="e63df-114">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="e63df-115">Этот ключевой недостаток приводит к необходимости использования больших таблиц маршрутизации для доставки пакетов IPv4 в любое место в Интернете.</span><span class="sxs-lookup"><span data-stu-id="e63df-115">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
- <span data-ttu-id="e63df-116">Сложная конфигурация сети.</span><span class="sxs-lookup"><span data-stu-id="e63df-116">Complex network configuration.</span></span>  
  
     <span data-ttu-id="e63df-117">При использовании протокола IPv4 адреса должны назначаться статически или с помощью протокола конфигурации, например DHCP.</span><span class="sxs-lookup"><span data-stu-id="e63df-117">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="e63df-118">В идеальном случае узлам не придется зависеть от администрирования инфраструктуры DHCP.</span><span class="sxs-lookup"><span data-stu-id="e63df-118">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="e63df-119">Вместо этого они смогут выполнять самостоятельную настройку с учетом сегмента сети, в котором они расположены.</span><span class="sxs-lookup"><span data-stu-id="e63df-119">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
- <span data-ttu-id="e63df-120">Отсутствие встроенной проверки подлинности и конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="e63df-120">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="e63df-121">Для IPv4 не требуется поддержка какого-либо механизма, обеспечивающего проверку подлинности или шифрование передаваемых данных.</span><span class="sxs-lookup"><span data-stu-id="e63df-121">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="e63df-122">Этот момент меняется при использовании IPv6.</span><span class="sxs-lookup"><span data-stu-id="e63df-122">This changes with IPv6.</span></span> <span data-ttu-id="e63df-123">IPSec является требованием поддержки IPv6.</span><span class="sxs-lookup"><span data-stu-id="e63df-123">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="e63df-124">Новый набор протоколов должен удовлетворять следующим базовым требованиям:</span><span class="sxs-lookup"><span data-stu-id="e63df-124">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
- <span data-ttu-id="e63df-125">Широкомасштабная маршрутизация и адресация с низкими издержками.</span><span class="sxs-lookup"><span data-stu-id="e63df-125">Large-scale routing and addressing with low overhead.</span></span>  
  
- <span data-ttu-id="e63df-126">Автоматическая настройка для различных ситуаций подключения.</span><span class="sxs-lookup"><span data-stu-id="e63df-126">Auto-configuration for various connecting situations.</span></span>  
  
- <span data-ttu-id="e63df-127">Встроенная проверка подлинности и конфиденциальность.</span><span class="sxs-lookup"><span data-stu-id="e63df-127">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="e63df-128">Дополнительные сведения см. в разделах [Адресация IPv6](ipv6-addressing.md), [Маршрутизация IPv6](ipv6-routing.md), [Автоматическая настройка IPv6](ipv6-auto-configuration.md), [Включение и отключение IPv6](enabling-and-disabling-ipv6.md) и [Практическое руководство. Изменение файла конфигурации компьютера для включения поддержки IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="e63df-128">For more information, see [IPv6 Addressing](ipv6-addressing.md), [IPv6 Routing](ipv6-routing.md), [IPv6 Auto-Configuration](ipv6-auto-configuration.md), [Enabling and Disabling IPv6](enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="e63df-129">Ссылки</span><span class="sxs-lookup"><span data-stu-id="e63df-129">References</span></span>  

 <span data-ttu-id="e63df-130">Ниже перечислен ряд документов RFC, которые можно найти на веб-сайте [IETF](https://www.ietf.org/):</span><span class="sxs-lookup"><span data-stu-id="e63df-130">The following are selected RFC documents that you can find at the [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website:</span></span>  
  
- <span data-ttu-id="e63df-131">RFC 1287, Towards the Future Internet Architecture.</span><span class="sxs-lookup"><span data-stu-id="e63df-131">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
- <span data-ttu-id="e63df-132">RFC 1454, Comparison of Proposals for Next Version of IP.</span><span class="sxs-lookup"><span data-stu-id="e63df-132">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
- <span data-ttu-id="e63df-133">RFC 2373, IP Version 6 Addressing Architecture.</span><span class="sxs-lookup"><span data-stu-id="e63df-133">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
- <span data-ttu-id="e63df-134">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span><span class="sxs-lookup"><span data-stu-id="e63df-134">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="e63df-135">Сведения, относящиеся к IP версии 6, можно также найти в [этом разделе](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="e63df-135">You can also find IPv6-related information on the [IP Version 6 (IPv6)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498(v=ws.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e63df-136">См. также</span><span class="sxs-lookup"><span data-stu-id="e63df-136">See also</span></span>

- <span data-ttu-id="e63df-137">[Пример сокетов IPv6](/previous-versions/dotnet/netframework-3.0/ms180981(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="e63df-137">[IPv6 Sockets Sample](/previous-versions/dotnet/netframework-3.0/ms180981(v=vs.85))</span></span>
- [<span data-ttu-id="e63df-138">Примеры сетевого программирования</span><span class="sxs-lookup"><span data-stu-id="e63df-138">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="e63df-139">Сокеты</span><span class="sxs-lookup"><span data-stu-id="e63df-139">Sockets</span></span>](sockets.md)
