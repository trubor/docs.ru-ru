---
title: Управление подключениями
description: Узнайте, как приложения, использующие HTTP для ресурсов данных, используют классы .NET Framework ServicePoint и ServicePointManager для управления соединениями.
ms.date: 01/25/2021
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
ms.openlocfilehash: 9ea93c3a9c484fd2a3de58b4d484b1e8445da155
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548062"
---
# <a name="managing-connections"></a><span data-ttu-id="5cd98-103">Управление подключениями</span><span class="sxs-lookup"><span data-stu-id="5cd98-103">Managing Connections</span></span>

<span data-ttu-id="5cd98-104">Приложения, которые используют протокол HTTP для подключения к ресурсам данных, могут использовать классы <xref:System.Net.ServicePoint> и <xref:System.Net.ServicePointManager> .NET Framework для управления подключением к Интернету и для оптимизации масштабирования и производительности.</span><span class="sxs-lookup"><span data-stu-id="5cd98-104">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  

> [!NOTE]
> <span data-ttu-id="5cd98-105">Классы `ServicePoint` и `ServicePointManager` считаются устаревшими в .NET Core, .NET 5 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="5cd98-105">`ServicePoint` and `ServicePointManager` are considered legacy on .NET Core, .NET 5, and later versions.</span></span> <span data-ttu-id="5cd98-106">Большинство их свойств и методов не реализованы в этих версиях.</span><span class="sxs-lookup"><span data-stu-id="5cd98-106">Most of their properties and methods are not implemented in these versions.</span></span> <span data-ttu-id="5cd98-107">При реализации эти классы никак не влияют на сетевые интерфейсы API `HttpClient` и не отслеживают сведения о них.</span><span class="sxs-lookup"><span data-stu-id="5cd98-107">When they are implemented, they don't affect or track anything about `HttpClient` networking APIs.</span></span>
  
 <span data-ttu-id="5cd98-108">Класс **ServicePoint** предоставляет приложению конечную точку, которое оно может использовать для доступа к ресурсам в Интернете.</span><span class="sxs-lookup"><span data-stu-id="5cd98-108">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="5cd98-109">Каждый экземпляр класса **ServicePoint** содержит сведения, которые помогают оптимизировать подключения к интернет-серверу с помощью анализа сведений о подключениях для повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="5cd98-109">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="5cd98-110">Каждый класс **ServicePoint** определяется с помощью универсального кода ресурса (URI). Классы разбиваются на категории на основе идентификатора схемы и фрагмента узла URI.</span><span class="sxs-lookup"><span data-stu-id="5cd98-110">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="5cd98-111">Например, один и тот же экземпляр **ServicePoint** может предоставлять запросы к URI `http://www.contoso.com/index.htm` и `http://www.contoso.com/news.htm?date=today`, так как в этих URI используется один и тот же идентификатор схемы (http) и фрагмент узла (`www.contoso.com`).</span><span class="sxs-lookup"><span data-stu-id="5cd98-111">For example, the same **ServicePoint** instance would provide requests to the URIs `http://www.contoso.com/index.htm` and `http://www.contoso.com/news.htm?date=today` since they have the same scheme identifier (http) and host fragments (`www.contoso.com`).</span></span> <span data-ttu-id="5cd98-112">Если у приложения уже есть постоянное подключение к серверу `www.contoso.com`, приложение использует это подключение для обработки обоих запросов, поэтому создавать два подключения не требуется.</span><span class="sxs-lookup"><span data-stu-id="5cd98-112">If the application already has a persistent connection to the server `www.contoso.com`, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="5cd98-113">**ServicePointManager** — статический класс, который управляет созданием и уничтожением экземпляров класса **ServicePoint**.</span><span class="sxs-lookup"><span data-stu-id="5cd98-113">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="5cd98-114">Класс **ServicePointManager** создает класс **ServicePoint**, когда приложение запрашивает интернет-ресурс, не входящий в коллекцию существующих экземпляров классов **ServicePoint**.</span><span class="sxs-lookup"><span data-stu-id="5cd98-114">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="5cd98-115">Классы **ServicePoint** уничтожаются, если превышается максимальное время ожидания или количество существующих экземпляров классов **ServicePoint** превышает максимальное количество экземпляров классов **ServicePoint** для приложения.</span><span class="sxs-lookup"><span data-stu-id="5cd98-115">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="5cd98-116">Вы можете задать как максимальное время ожидания по умолчанию, так и максимальное количество экземпляров классов **ServicePoint**, установив свойства <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> и <xref:System.Net.ServicePointManager.MaxServicePoints%2A> для класса **ServicePointManager**.</span><span class="sxs-lookup"><span data-stu-id="5cd98-116">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="5cd98-117">Количество подключений между клиентом и сервером может оказывать большое влияние на пропускную способность приложения.</span><span class="sxs-lookup"><span data-stu-id="5cd98-117">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="5cd98-118">По умолчанию приложение, в котором используется экземпляр класса <xref:System.Net.HttpWebRequest>, создает не более двух постоянных подключений к одному серверу, но вы можете установить максимальное количество приложений для отдельных приложений.</span><span class="sxs-lookup"><span data-stu-id="5cd98-118">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5cd98-119">Спецификация HTTP/1.1 ограничивает количество подключений для каждого приложения двумя подключениями к одному серверу.</span><span class="sxs-lookup"><span data-stu-id="5cd98-119">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="5cd98-120">Оптимальное количество подключений зависит от фактических условий, в которых запускается приложение.</span><span class="sxs-lookup"><span data-stu-id="5cd98-120">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="5cd98-121">Увеличение количества доступных подключений для приложения может не влиять на производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="5cd98-121">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="5cd98-122">Для определения влияния дополнительных подключений на производительность приложения запустите тесты производительности, изменяя количество подключений.</span><span class="sxs-lookup"><span data-stu-id="5cd98-122">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="5cd98-123">Вы можете изменить количество подключений, используемых приложением, изменив статическое свойство <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> класса **ServicePointManager** при инициализации приложения, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="5cd98-123">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="5cd98-124">Изменение свойства **ServicePointManager.DefaultConnectionLimit** не влияет на ранее инициализированные экземпляры класса **ServicePoint**.</span><span class="sxs-lookup"><span data-stu-id="5cd98-124">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="5cd98-125">В следующем коде показано изменение количества подключений для существующего класса **ServicePoint** для сервера `http://www.contoso.com` на значение, которое хранится в `newLimit`.</span><span class="sxs-lookup"><span data-stu-id="5cd98-125">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server `http://www.contoso.com` to the value stored in `newLimit`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5cd98-126">См. также</span><span class="sxs-lookup"><span data-stu-id="5cd98-126">See also</span></span>

- [<span data-ttu-id="5cd98-127">Группирование подключений</span><span class="sxs-lookup"><span data-stu-id="5cd98-127">Connection Grouping</span></span>](connection-grouping.md)
- [<span data-ttu-id="5cd98-128">Использование протоколов приложений</span><span class="sxs-lookup"><span data-stu-id="5cd98-128">Using Application Protocols</span></span>](using-application-protocols.md)
