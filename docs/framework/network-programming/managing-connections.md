---
title: Управление подключениями
description: Узнайте, как приложения, использующие HTTP для ресурсов данных, используют классы .NET Framework ServicePoint и ServicePointManager для управления соединениями.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, connections
- HTTP, classes for connecting
- requesting data from Internet, connections
- sending data, connections
- receiving data, connections
- ServicePoint class, about ServicePoint class
- response to Internet request, connections
- connections [.NET Framework], classes
- network resources, connections
- downloading Internet resources, connections
- ServicePointManager class, about ServicePointManager class
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
ms.openlocfilehash: 00db05c99cf232a31b10bbd0356e6d43d3bc3e28
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96282864"
---
# <a name="managing-connections"></a><span data-ttu-id="df78d-103">Управление подключениями</span><span class="sxs-lookup"><span data-stu-id="df78d-103">Managing Connections</span></span>

<span data-ttu-id="df78d-104">Приложения, которые используют протокол HTTP для подключения к ресурсам данных, могут использовать классы <xref:System.Net.ServicePoint> и <xref:System.Net.ServicePointManager> .NET Framework для управления подключением к Интернету и для оптимизации масштабирования и производительности.</span><span class="sxs-lookup"><span data-stu-id="df78d-104">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  
  
 <span data-ttu-id="df78d-105">Класс **ServicePoint** предоставляет приложению конечную точку, которое оно может использовать для доступа к ресурсам в Интернете.</span><span class="sxs-lookup"><span data-stu-id="df78d-105">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="df78d-106">Каждый экземпляр класса **ServicePoint** содержит сведения, которые помогают оптимизировать подключения к интернет-серверу с помощью анализа сведений о подключениях для повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="df78d-106">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="df78d-107">Каждый класс **ServicePoint** определяется с помощью универсального кода ресурса (URI). Классы разбиваются на категории на основе идентификатора схемы и фрагмента узла URI.</span><span class="sxs-lookup"><span data-stu-id="df78d-107">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="df78d-108">Например, один и тот же экземпляр **ServicePoint** может предоставлять запросы к URI `http://www.contoso.com/index.htm` и `http://www.contoso.com/news.htm?date=today`, так как в этих URI используется один и тот же идентификатор схемы (http) и фрагмент узла (`www.contoso.com`).</span><span class="sxs-lookup"><span data-stu-id="df78d-108">For example, the same **ServicePoint** instance would provide requests to the URIs `http://www.contoso.com/index.htm` and `http://www.contoso.com/news.htm?date=today` since they have the same scheme identifier (http) and host fragments (`www.contoso.com`).</span></span> <span data-ttu-id="df78d-109">Если у приложения уже есть постоянное подключение к серверу `www.contoso.com`, приложение использует это подключение для обработки обоих запросов, поэтому создавать два подключения не требуется.</span><span class="sxs-lookup"><span data-stu-id="df78d-109">If the application already has a persistent connection to the server `www.contoso.com`, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="df78d-110">**ServicePointManager** — статический класс, который управляет созданием и уничтожением экземпляров класса **ServicePoint**.</span><span class="sxs-lookup"><span data-stu-id="df78d-110">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="df78d-111">Класс **ServicePointManager** создает класс **ServicePoint**, когда приложение запрашивает интернет-ресурс, не входящий в коллекцию существующих экземпляров классов **ServicePoint**.</span><span class="sxs-lookup"><span data-stu-id="df78d-111">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="df78d-112">Классы **ServicePoint** уничтожаются, если превышается максимальное время ожидания или количество существующих экземпляров классов **ServicePoint** превышает максимальное количество экземпляров классов **ServicePoint** для приложения.</span><span class="sxs-lookup"><span data-stu-id="df78d-112">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="df78d-113">Вы можете задать как максимальное время ожидания по умолчанию, так и максимальное количество экземпляров классов **ServicePoint**, установив свойства <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> и <xref:System.Net.ServicePointManager.MaxServicePoints%2A> для класса **ServicePointManager**.</span><span class="sxs-lookup"><span data-stu-id="df78d-113">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="df78d-114">Количество подключений между клиентом и сервером может оказывать большое влияние на пропускную способность приложения.</span><span class="sxs-lookup"><span data-stu-id="df78d-114">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="df78d-115">По умолчанию приложение, в котором используется экземпляр класса <xref:System.Net.HttpWebRequest>, создает не более двух постоянных подключений к одному серверу, но вы можете установить максимальное количество приложений для отдельных приложений.</span><span class="sxs-lookup"><span data-stu-id="df78d-115">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df78d-116">Спецификация HTTP/1.1 ограничивает количество подключений для каждого приложения двумя подключениями к одному серверу.</span><span class="sxs-lookup"><span data-stu-id="df78d-116">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="df78d-117">Оптимальное количество подключений зависит от фактических условий, в которых запускается приложение.</span><span class="sxs-lookup"><span data-stu-id="df78d-117">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="df78d-118">Увеличение количества доступных подключений для приложения может не влиять на производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="df78d-118">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="df78d-119">Для определения влияния дополнительных подключений на производительность приложения запустите тесты производительности, изменяя количество подключений.</span><span class="sxs-lookup"><span data-stu-id="df78d-119">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="df78d-120">Вы можете изменить количество подключений, используемых приложением, изменив статическое свойство <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> класса **ServicePointManager** при инициализации приложения, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="df78d-120">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="df78d-121">Изменение свойства **ServicePointManager.DefaultConnectionLimit** не влияет на ранее инициализированные экземпляры класса **ServicePoint**.</span><span class="sxs-lookup"><span data-stu-id="df78d-121">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="df78d-122">В следующем коде показано изменение количества подключений для существующего класса **ServicePoint** для сервера `http://www.contoso.com` на значение, которое хранится в `newLimit`.</span><span class="sxs-lookup"><span data-stu-id="df78d-122">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server `http://www.contoso.com` to the value stored in `newLimit`.</span></span>  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## <a name="see-also"></a><span data-ttu-id="df78d-123">См. также</span><span class="sxs-lookup"><span data-stu-id="df78d-123">See also</span></span>

- [<span data-ttu-id="df78d-124">Группирование подключений</span><span class="sxs-lookup"><span data-stu-id="df78d-124">Connection Grouping</span></span>](connection-grouping.md)
- [<span data-ttu-id="df78d-125">Использование протоколов приложений</span><span class="sxs-lookup"><span data-stu-id="df78d-125">Using Application Protocols</span></span>](using-application-protocols.md)
