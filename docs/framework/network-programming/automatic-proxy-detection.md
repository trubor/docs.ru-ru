---
title: Автоматическое обнаружение прокси-сервера
description: Сведения об автоматическом обнаружении прокси-сервера, в ходе которого система определяет сервер веб-прокси, используемый для отправки запросов от имени клиента.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic proxy detections
- Web Proxy Auto-Discovery
- Web proxy
- detecting proxies automatically
- WebProxy class, automatic proxy detections
- proxies, automatically detecting
- network
- WPAD (Web Proxy Auto-Discovery)
ms.assetid: fcd9c3bd-93de-4c92-8ff3-837327ad18de
ms.openlocfilehash: 8d1b904a8acc6d3960a076c54c2d5f5de54820c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250636"
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="8c2dd-103">Автоматическое обнаружение прокси-сервера</span><span class="sxs-lookup"><span data-stu-id="8c2dd-103">Automatic Proxy Detection</span></span>

<span data-ttu-id="8c2dd-104">В ходе автоматического обнаружения прокси-сервера система определяет сервер веб-прокси, который используется для отправки запросов от имени клиента.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-104">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="8c2dd-105">Эта функция также называется автообнаружением веб-прокси (WPAD).</span><span class="sxs-lookup"><span data-stu-id="8c2dd-105">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="8c2dd-106">Если автоматическое обнаружение прокси-сервера включено, система пытается обнаружить скрипт конфигурации прокси-сервера, возвращающий набор прокси-серверов, который можно использовать для обработки запросов.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-106">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="8c2dd-107">Если такой скрипт обнаружен, он скачивается, компилируется и запускается на локальном компьютере при получении информации о прокси-сервере, потока запроса или ответа для запроса, который использует экземпляр <xref:System.Net.WebProxy>.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-107">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="8c2dd-108">Автоматическое обнаружение прокси-сервера реализуется с помощью класса <xref:System.Net.WebProxy>. Параметры этого процесса могут задаваться на уровне запроса, в файлах конфигурации, а также в диалоговом окне **Локальная сеть (LAN)** браузера Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-108">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c2dd-109">Чтобы открыть диалоговое окно **Параметры локальной сети** Internet Explorer, выберите **Сервис** в главном меню этого браузера, а затем пункт **Свойства браузера**.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-109">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="8c2dd-110">Перейдите на вкладку **Подключения** и выберите **Параметры локальной сети**.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-110">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="8c2dd-111">Если автоматическое обнаружение прокси-сервера включено, класс <xref:System.Net.WebProxy> пытается найти скрипт конфигурации прокси-сервера следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8c2dd-111">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1. <span data-ttu-id="8c2dd-112">Функция WinINet `InternetQueryOption` используется для поиска скрипта конфигурации прокси-сервера, который был обнаружен браузером Internet Explorer в последний раз.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-112">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2. <span data-ttu-id="8c2dd-113">Если найти этот скрипт не удается, класс <xref:System.Net.WebProxy> использует для его поиска протокола DHCP.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-113">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="8c2dd-114">DHCP-сервер может вернуть в ответе расположение (имя узла) скрипта или полный URL-адрес скрипта.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-114">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3. <span data-ttu-id="8c2dd-115">Если с помощью DHCP не удалось определить узел автообнаружения веб-прокси (WPAD), выполняется запрос узла DNS, в качестве имени или псевдонима которого используется WPAD.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-115">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4. <span data-ttu-id="8c2dd-116">Если обнаружить узел не удается и расположение скрипта конфигурации прокси-сервера задается в файле конфигурации или параметрах локальной сети браузера Internet Explorer, используется это расположение.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-116">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c2dd-117">Приложения, выполняемые как службы NT или в составе ASP.NET, используют параметры прокси-сервера, задаваемые Internet Explorer (если доступны), вызывающего пользователя.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-117">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="8c2dd-118">Эти параметры могут быть доступны не для всех приложений службы.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-118">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="8c2dd-119">Прокси-серверы настраиваются отдельно для каждого устройства подключения.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-119">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="8c2dd-120">Устройство подключения — это элемент в диалоговом окне сетевого подключения, который может быть как физическим сетевым устройством (модем или плата Ethernet), так и виртуальным интерфейсом (например, VPN-подключение, работающее через сетевое устройство).</span><span class="sxs-lookup"><span data-stu-id="8c2dd-120">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="8c2dd-121">При изменении устройства подключения (например, при смене точки доступа для беспроводного подключения или включении VPN) алгоритм обнаружения прокси-сервера запускается снова.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-121">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="8c2dd-122">По умолчанию для обнаружения прокси-сервера используются параметры прокси, задаваемые браузером Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-122">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="8c2dd-123">Если приложение выполняется под учетной записью, не являющейся интерактивной (не поддерживает удобный способ настройки параметров прокси-сервера в Internet Explorer), или требуется использовать другие параметры прокси-сервера, вы можете настроить собственный прокси-сервер, создав файл конфигурации, в котором определены элементы [\<defaultProxy> (параметры сети)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) и [\<proxy> (параметры сети)](../configure-apps/file-schema/network/proxy-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="8c2dd-123">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="8c2dd-124">Для создаваемых вами запросов можно отключить автоматическое обнаружение прокси-сервера на уровне запроса, указав в нем <xref:System.Net.WebRequest.Proxy%2A> NULL, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-124">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
```csharp  
public static void DisableForMyRequest (Uri resource)  
{  
    WebRequest request = WebRequest.Create (resource);  
    request.Proxy = null;  
    WebResponse response = request.GetResponse ();  
}  
```  
  
```vb  
Public Shared Sub DisableForMyRequest(ByVal resource As Uri)  
    Dim request As WebRequest = WebRequest.Create(resource)  
    request.Proxy = Nothing  
    Dim response As WebResponse = request.GetResponse()  
    End Sub
```  
  
 <span data-ttu-id="8c2dd-125">Для обработки запросов, не указывающих прокси-сервер, используется прокси-сервер по умолчанию домена приложения, который доступен в свойстве <xref:System.Net.WebRequest.DefaultWebProxy%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c2dd-125">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c2dd-126">См. также</span><span class="sxs-lookup"><span data-stu-id="8c2dd-126">See also</span></span>

- <xref:System.Net.WebProxy>
- <xref:System.Net.WebRequest>
- [<span data-ttu-id="8c2dd-127">Элемент \<system.Net> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="8c2dd-127">\<system.Net> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/system-net-element-network-settings.md)
