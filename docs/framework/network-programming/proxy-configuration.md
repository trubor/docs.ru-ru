---
title: Настройка прокси-сервера
description: Узнайте, как настроить адаптивные и статические прокси-серверы. Конфигурация прокси-сервера обрабатывает клиентские запросы для ресурсов.
ms.date: 06/18/2018
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
ms.openlocfilehash: 668e6a4082a132d94e6aa8039e2afaaf543fb5e9
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938160"
---
# <a name="proxy-configuration"></a><span data-ttu-id="f46ab-104">Настройка прокси-сервера</span><span class="sxs-lookup"><span data-stu-id="f46ab-104">Proxy Configuration</span></span>

<span data-ttu-id="f46ab-105">Прокси-сервер обрабатывает клиентские запросы на ресурсы.</span><span class="sxs-lookup"><span data-stu-id="f46ab-105">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="f46ab-106">Прокси-сервер может возвращать запрошенный ресурс из своего кэша или пересылать запрос на сервер, на котором находится данный ресурс.</span><span class="sxs-lookup"><span data-stu-id="f46ab-106">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="f46ab-107">Прокси-серверы могут повышать производительность сети, благодаря уменьшению числа запросов, отправляемых на удаленные серверы.</span><span class="sxs-lookup"><span data-stu-id="f46ab-107">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="f46ab-108">Прокси-серверы также можно использовать для ограничения доступа к ресурсам.</span><span class="sxs-lookup"><span data-stu-id="f46ab-108">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="f46ab-109">Адаптивные прокси-серверы</span><span class="sxs-lookup"><span data-stu-id="f46ab-109">Adaptive Proxies</span></span>  

 <span data-ttu-id="f46ab-110">На платформе .NET Framework могут иметься прокси-серверы двух видов: адаптивные и статические.</span><span class="sxs-lookup"><span data-stu-id="f46ab-110">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="f46ab-111">Адаптивный прокси-серверы настраивают свои параметры при изменении конфигурации сети.</span><span class="sxs-lookup"><span data-stu-id="f46ab-111">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="f46ab-112">Например, если пользователь ноутбука запускает коммутируемое сетевое соединение, то адаптивный прокси-сервер определит это изменение, обнаружит и выполнит свой новый скрипт конфигурации, а также настроит свои параметры соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="f46ab-112">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="f46ab-113">Адаптивные прокси-серверы настраиваются с помощью скрипта конфигурации (см. раздел [Автоматическое обнаружение прокси-сервера](automatic-proxy-detection.md)).</span><span class="sxs-lookup"><span data-stu-id="f46ab-113">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](automatic-proxy-detection.md)).</span></span> <span data-ttu-id="f46ab-114">Скрипт создает набор протоколов приложений и прокси-сервер для каждого протокола.</span><span class="sxs-lookup"><span data-stu-id="f46ab-114">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="f46ab-115">В сетевой среде может потребоваться внесение изменений, если система использует новый набор прокси-серверов.</span><span class="sxs-lookup"><span data-stu-id="f46ab-115">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="f46ab-116">Если сетевое соединение пропадает, или выполняется инициализация нового сетевого соединения, то система должна обнаружить соответствующий источник скрипта конфигурации в новой среде и запустить новый скрипт.</span><span class="sxs-lookup"><span data-stu-id="f46ab-116">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="f46ab-117">Можно использовать атрибут `usesystemdefault` элемента [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f46ab-117">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="f46ab-118">Атрибут `usesystemdefault` определяет, должны ли параметры статического прокси-сервера (адрес прокси-сервера, список обхода и локальный обход) считываться из параметров прокси Internet Explorer для пользователя.</span><span class="sxs-lookup"><span data-stu-id="f46ab-118">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="f46ab-119">Если установлено значение `true`, будут использоваться параметры статического прокси-сервера из Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f46ab-119">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="f46ab-120">Если установлено значение `false` (или значение вообще не задано), то параметры статического прокси-сервера можно указать в конфигурации, и они будут переопределять параметры прокси-сервера в Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f46ab-120">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="f46ab-121">Для включения адаптивного прокси-сервера необходимо установить значение `false` (либо вообще не задавать).</span><span class="sxs-lookup"><span data-stu-id="f46ab-121">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="f46ab-122">В следующем примере показана конфигурация обычного адаптивного прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="f46ab-122">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="f46ab-123">Статические прокси-серверы</span><span class="sxs-lookup"><span data-stu-id="f46ab-123">Static Proxies</span></span>  

 <span data-ttu-id="f46ab-124">Статические прокси-серверы обычно настраиваются явным образом приложением, или когда файл конфигурации вызывается приложением или системой.</span><span class="sxs-lookup"><span data-stu-id="f46ab-124">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="f46ab-125">Статические прокси-серверы применяются в сетях, топология которых изменяется редко, например, когда настольный компьютер подключен к корпоративной сети.</span><span class="sxs-lookup"><span data-stu-id="f46ab-125">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="f46ab-126">Работой статического прокси-сервера управляют несколько параметров.</span><span class="sxs-lookup"><span data-stu-id="f46ab-126">Several options control how a static proxy operates.</span></span> <span data-ttu-id="f46ab-127">Можно задать следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="f46ab-127">You can specify the following:</span></span>  
  
- <span data-ttu-id="f46ab-128">Адрес прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="f46ab-128">The address of the proxy.</span></span>  
  
- <span data-ttu-id="f46ab-129">Определяет, нужно ли обходить прокси-сервер для локальных адресов.</span><span class="sxs-lookup"><span data-stu-id="f46ab-129">Whether the proxy should be bypassed for local addresses.</span></span>  
  
- <span data-ttu-id="f46ab-130">Определяет, нужно ли обходить прокси-сервер для набора адресов.</span><span class="sxs-lookup"><span data-stu-id="f46ab-130">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="f46ab-131">Ниже указаны параметры конфигурации для статического прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="f46ab-131">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="f46ab-132">Параметр атрибута, свойства или файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="f46ab-132">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="f46ab-133">Описание</span><span class="sxs-lookup"><span data-stu-id="f46ab-133">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="f46ab-134">`proxyaddress` или <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="f46ab-134">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="f46ab-135">Адрес используемого прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="f46ab-135">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="f46ab-136">`bypassonlocal` или <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="f46ab-136">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="f46ab-137">Определяет, выполняется ли обход прокси-сервера для локальных адресов.</span><span class="sxs-lookup"><span data-stu-id="f46ab-137">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="f46ab-138">`bypasslist` или <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="f46ab-138">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="f46ab-139">Описывает (с помощью регулярных выражений) набор адресов, которые обходят прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="f46ab-139">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="f46ab-140">Определяет, должны ли параметры статического прокси-сервера (адрес прокси-сервера, список обхода и локальный обход) считываться из параметров прокси-сервера Internet Explorer для пользователя.</span><span class="sxs-lookup"><span data-stu-id="f46ab-140">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="f46ab-141">Если установлено значение `true`, будут использоваться параметры статического прокси-сервера из Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f46ab-141">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="f46ab-142">На платформе .NET Framework 2.0 (если установлено значение `true`) параметры прокси-сервера обозревателя Internet Explorer не переопределяются другими параметрами прокси-сервера в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f46ab-142">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="f46ab-143">На платформе .NET Framework 1.1 параметры прокси-сервера обозревателя Internet Explorer могут переопределяться другими параметрами прокси-сервера в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f46ab-143">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="f46ab-144">Если установлено значение `false` (или значение вообще не задано), то параметры статического прокси-сервера можно указать в конфигурации, и они будут переопределять параметры прокси-сервера в Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f46ab-144">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="f46ab-145">Для включения адаптивного прокси-сервера необходимо установить значение `false` (либо вообще не задавать).</span><span class="sxs-lookup"><span data-stu-id="f46ab-145">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="f46ab-146">В следующем примере показана типовая конфигурация адаптивного прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="f46ab-146">The following example shows a typical static proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="True"  
        />  
        <bypasslist>  
            <add address="[a-z]+\.blueyonderairlines\.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f46ab-147">См. также</span><span class="sxs-lookup"><span data-stu-id="f46ab-147">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="f46ab-148">Автоматическое обнаружение прокси-сервера</span><span class="sxs-lookup"><span data-stu-id="f46ab-148">Automatic Proxy Detection</span></span>](automatic-proxy-detection.md)
