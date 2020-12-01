---
title: Запрос данных
description: Узнайте, как благодаря подключаемым протоколам можно разрабатывать приложения, использующие единый интерфейс для извлечения данных из нескольких протоколов.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sending data
- WebRequest class, sending and receiving data
- requesting data from Internet, about requesting data
- WebClient class, sending and receiving data
- network, requesting data
- receiving data
- sending data, about sending data
- response to Internet request, about responding to Internet requests
- data requests
- receiving data, about receiving data
- Internet, requesting data
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
ms.openlocfilehash: 87ad0144f57bdca0e0235aea30c4ab450cc890f4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279302"
---
# <a name="requesting-data"></a><span data-ttu-id="c6344-103">Запрос данных</span><span class="sxs-lookup"><span data-stu-id="c6344-103">Requesting Data</span></span>

<span data-ttu-id="c6344-104">Для разработки современных интернет-приложений, выполняющихся в распределенной операционной среде, требуется простой и эффективный способ извлечения данных из ресурсов любого типа.</span><span class="sxs-lookup"><span data-stu-id="c6344-104">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="c6344-105">Благодаря подключаемым протоколам можно разрабатывать приложения, использующие единый интерфейс для извлечения данных из нескольких интернет-протоколов.</span><span class="sxs-lookup"><span data-stu-id="c6344-105">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="c6344-106">Загрузка и скачивание данных с интернет-сервера</span><span class="sxs-lookup"><span data-stu-id="c6344-106">Uploading and Downloading Data from an Internet Server</span></span>  

 <span data-ttu-id="c6344-107">Для реализации простых операций запроса и ответа класс <xref:System.Net.WebClient> предоставляет простейший способ загрузки данных на интернет-сервер или скачивания с него.</span><span class="sxs-lookup"><span data-stu-id="c6344-107">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="c6344-108">В классе **WebClient** представлены методы для скачивания и загрузки файлов, отправки и получения потоков, а также отправки буфера данных на сервер и получения ответа от него.</span><span class="sxs-lookup"><span data-stu-id="c6344-108">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="c6344-109">Класс **WebClient** использует классы <xref:System.Net.WebRequest> и <xref:System.Net.WebResponse> для установления фактических подключений к интернет-ресурсу, что позволяет использовать любой зарегистрированный подключаемый протокол.</span><span class="sxs-lookup"><span data-stu-id="c6344-109">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="c6344-110">Клиентские приложения, которые выполняют более сложные транзакции, используют для запроса данных с серверов класс **WebRequest** и его потомки.</span><span class="sxs-lookup"><span data-stu-id="c6344-110">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="c6344-111">Класс **WebRequest** инкапсулирует сведения о подключении к серверу, отправке запроса и получении ответа.</span><span class="sxs-lookup"><span data-stu-id="c6344-111">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="c6344-112">**WebRequest** — это абстрактный класс, в котором определяется набор свойств и методов, доступных всем приложениям, использующим подключаемые протоколы.</span><span class="sxs-lookup"><span data-stu-id="c6344-112">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="c6344-113">Потомки класса **WebRequest**, такие как <xref:System.Net.HttpWebRequest>, реализуют свойства и методы, определенные в **WebRequest**, в соответствии с особенностями базового протокола.</span><span class="sxs-lookup"><span data-stu-id="c6344-113">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="c6344-114">Класс **WebRequest** создает экземпляры потомков **WebRequest** для определенных протоколов, используя значение URI, которое передано в его метод <xref:System.Net.WebRequest.Create%2A> и определяет конкретный создаваемый экземпляр производного класса.</span><span class="sxs-lookup"><span data-stu-id="c6344-114">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="c6344-115">Приложения указывают, какой потомок класса **WebRequest** необходимо использовать для обработки запроса, регистрируя конструктор такого потомка с помощью метода <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c6344-115">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="c6344-116">Запрос к интернет-ресурсу выполняется посредством вызова метода <xref:System.Net.WebRequest.GetResponse%2A> для **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="c6344-116">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="c6344-117">Метод **GetResponse** создает запрос для определенного протокола на основании свойств **WebRequest**, устанавливает подключение TCP или UDP к сокету сервера и отправляет запрос.</span><span class="sxs-lookup"><span data-stu-id="c6344-117">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="c6344-118">Для запросов, которые отправляют данные на сервер, таких как HTTP-запрос **Post** или FTP-запрос **Put**, метод <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> предоставляет сетевой поток для отправки данных.</span><span class="sxs-lookup"><span data-stu-id="c6344-118">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="c6344-119">Метод **GetResponse** возвращает **WebResponse** для определенного протокола, соответствующий **WebRequest.**</span><span class="sxs-lookup"><span data-stu-id="c6344-119">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="c6344-120">**WebResponse** — это также абстрактный класс, в котором определяются свойства и методы, доступные всем приложениям, использующим подключаемые протоколы.</span><span class="sxs-lookup"><span data-stu-id="c6344-120">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="c6344-121">Потомки класса **WebResponse** реализуют эти свойства и методы для соответствующих базовых протоколов.</span><span class="sxs-lookup"><span data-stu-id="c6344-121">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="c6344-122">Например, класс <xref:System.Net.HttpWebResponse> реализует класс **WebResponse** для протокола HTTP.</span><span class="sxs-lookup"><span data-stu-id="c6344-122">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="c6344-123">Возвращаемые сервером данные предоставляются приложению в потоке, который возвращается методом <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c6344-123">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c6344-124">Этот поток используется так же, как и любые другие, что показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c6344-124">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6344-125">См. также</span><span class="sxs-lookup"><span data-stu-id="c6344-125">See also</span></span>

- [<span data-ttu-id="c6344-126">Сетевое программирование в .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c6344-126">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="c6344-127">Практическое руководство. Запрос веб-страницы и получение результатов в виде потока</span><span class="sxs-lookup"><span data-stu-id="c6344-127">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)
- [<span data-ttu-id="c6344-128">Практическое руководство. Получение объекта WebResponse, соответствующего объекту WebRequest, для определенного протокола</span><span class="sxs-lookup"><span data-stu-id="c6344-128">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
