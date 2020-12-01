---
title: Настройка веб-приложений
description: Сведения об использовании элемента <system.Net> для настройки интернет-приложений в .NET Framework. Эта статья содержит пример кода.
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, default proxy
- sending data, default proxy
- receiving data, default proxy
- downloading Internet resources, configuring Internet applications
- protocol-specific modules
- custom authentication modules
- receiving data, configuring Internet applications
- configuration settings [.NET Framework], Internet applications
- requesting data from Internet, configuring Internet applications
- requesting data from Internet, default proxy
- response to Internet request, default proxy
- Internet, configuring Internet applications
- response to Internet request, configuring Internet applications
- default proxy
- network resources, default proxy
- sending data, configuring Internet applications
- network resources, configuring Internet applications
- Internet, default proxy
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
ms.openlocfilehash: 796752ebf6e3cc5c3dac2a20213934f35d31b392
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287466"
---
# <a name="configuring-internet-applications"></a><span data-ttu-id="a1d4a-104">Настройка веб-приложений</span><span class="sxs-lookup"><span data-stu-id="a1d4a-104">Configuring Internet Applications</span></span>

<span data-ttu-id="a1d4a-105">[Элемент конфигурации \<system.Net> (параметры сети)](../configure-apps/file-schema/network/system-net-element-network-settings.md) содержит сведения о конфигурации сети для приложений.</span><span class="sxs-lookup"><span data-stu-id="a1d4a-105">The [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) configuration element contains network configuration information for applications.</span></span> <span data-ttu-id="a1d4a-106">С помощью [элемента \<system.Net> (параметры сети)](../configure-apps/file-schema/network/system-net-element-network-settings.md) можно задавать прокси-серверы, устанавливать параметры управления подключениями и включать в приложение пользовательские модули проверки подлинности и запросов.</span><span class="sxs-lookup"><span data-stu-id="a1d4a-106">Using the [\<system.Net> Element (Network Settings)](../configure-apps/file-schema/network/system-net-element-network-settings.md) element, you can set proxy servers, set connection management parameters, and include custom authentication and request modules in your application.</span></span>  
  
 <span data-ttu-id="a1d4a-107">[Элемент \<defaultProxy> (параметры сети)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) определяет прокси-сервер, который возвращается классом `GlobalProxySelection`.</span><span class="sxs-lookup"><span data-stu-id="a1d4a-107">The [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) element defines the proxy server returned by the `GlobalProxySelection` class.</span></span> <span data-ttu-id="a1d4a-108">Любой объект <xref:System.Net.HttpWebRequest>, для которого не установлено свойство <xref:System.Net.HttpWebRequest.Proxy%2A>, использует прокси-сервер по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a1d4a-108">Any <xref:System.Net.HttpWebRequest> that does not have its own <xref:System.Net.HttpWebRequest.Proxy%2A> property set to a specific value uses the default proxy.</span></span> <span data-ttu-id="a1d4a-109">Помимо настройки адреса прокси-сервера можно создать список адресов серверов, которые не будут использовать прокси-сервер. Кроме того, можно запретить использование прокси-сервера локальным адресам.</span><span class="sxs-lookup"><span data-stu-id="a1d4a-109">In addition to setting the proxy address, you can create a list of server addresses that will not use the proxy, and you can indicate that the proxy should not be used for local addresses.</span></span>  
  
 <span data-ttu-id="a1d4a-110">Важно отметить, что параметры Microsoft Internet Explorer объединены с параметрами конфигурации, причем последние имеют приоритет.</span><span class="sxs-lookup"><span data-stu-id="a1d4a-110">It is important to note that the Microsoft Internet Explorer settings are combined with the configuration settings, with the latter taking precedence.</span></span>  
  
 <span data-ttu-id="a1d4a-111">В следующем примере устанавливается адрес прокси-сервера по умолчанию `http://proxyserver`, а также указывается, что прокси-сервер не должен использоваться локальными адресами и все запросы к серверам в домене contoso.com должны направляться в обход прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="a1d4a-111">The following example sets the default proxy server address to `http://proxyserver`, indicates that the proxy should not be used for local addresses, and specifies that all requests to servers located in the contoso.com domain should bypass the proxy.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <defaultProxy>  
            <proxy  
                usesystemdefault = "false"  
                proxyaddress = "http://proxyserver:80"  
                bypassonlocal = "true"  
            />  
            <bypasslist>  
                <add address="http://[a-z]+\.contoso\.com/" />  
            </bypasslist>  
        </defaultProxy>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="a1d4a-112">[Элемент \<connectionManagement> (параметры сети)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) задает число постоянных подключений, которые могут устанавливаться к конкретному серверу или ко всем остальным серверам.</span><span class="sxs-lookup"><span data-stu-id="a1d4a-112">Use the [\<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) element to configure the number of persistent connections that can be made to a specific server or to all other servers.</span></span> <span data-ttu-id="a1d4a-113">В следующем примере показано приложение, которое использует два постоянных подключения к серверу `www.contoso.com`, четыре постоянных подключения к серверу с IP-адресом 192.168.1.2, а также одно постоянное подключение ко всем остальным серверам.</span><span class="sxs-lookup"><span data-stu-id="a1d4a-113">The following example configures the application to use two persistent connections to the server `www.contoso.com`, four persistent connections to the server with the IP address 192.168.1.2, and one persistent connection to all other servers.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <connectionManagement>  
            <add address="http://www.contoso.com" maxconnection="2" />  
            <add address="192.168.1.2" maxconnection="4" />  
            <add address="*" maxconnection="1" />  
        </connectionManagement>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="a1d4a-114">Для настройки пользовательских модулей проверки подлинности используется [элемент \<authenticationModules> (параметры сети)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="a1d4a-114">Custom authentication modules are configured with the [\<authenticationModules> Element (Network Settings)](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) element.</span></span> <span data-ttu-id="a1d4a-115">Пользовательские модули проверки подлинности должны реализовывать интерфейс <xref:System.Net.IAuthenticationModule>.</span><span class="sxs-lookup"><span data-stu-id="a1d4a-115">Custom authentication modules must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
 <span data-ttu-id="a1d4a-116">В следующем примере выполняется настройка пользовательского модуля проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="a1d4a-116">The following example configures a custom authentication module.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 <span data-ttu-id="a1d4a-117">С помощью [элемента \<webRequestModules> (параметры сети)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) можно настроить приложение для работы с пользовательскими модулями определенного протокола, которые позволяют запрашивать данные из интернет-ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a1d4a-117">You can use the [\<webRequestModules> Element (Network Settings)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) element to configure your application to use custom protocol-specific modules to request information from Internet resources.</span></span> <span data-ttu-id="a1d4a-118">Указанные модули должны реализовывать интерфейс <xref:System.Net.IWebRequestCreate>.</span><span class="sxs-lookup"><span data-stu-id="a1d4a-118">The specified modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span> <span data-ttu-id="a1d4a-119">Вы можете переопределить установленные по умолчанию модули запросов HTTP, HTTPS и файлов, указав в файле конфигурации собственный модуль, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a1d4a-119">You can override the default HTTP, HTTPS, and file request modules by specifying your custom module in the configuration file, as in the following example.</span></span>  
  
```xml  
<configuration>  
    <system.net>  
        <webRequestModules>  
            <add  
                prefix="HTTP"  
                type = "MyHttpRequest.dll, MyHttpRequestCreator"  
            />  
        </webRequestModules>  
    </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1d4a-120">См. также</span><span class="sxs-lookup"><span data-stu-id="a1d4a-120">See also</span></span>

- [<span data-ttu-id="a1d4a-121">Сетевое программирование в .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a1d4a-121">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="a1d4a-122">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="a1d4a-122">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="a1d4a-123">Элемент \<system.Net> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="a1d4a-123">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
