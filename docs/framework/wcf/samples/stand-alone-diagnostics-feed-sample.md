---
description: 'Дополнительные сведения: пример веб-канала диагностики Stand-Alone'
title: Пример автономного веб-канала диагностики
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 98fd65a44f9f6f0183b879627bd8eb444152a8ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668868"
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="15e25-103">Пример автономного веб-канала диагностики</span><span class="sxs-lookup"><span data-stu-id="15e25-103">Stand-Alone Diagnostics Feed Sample</span></span>

<span data-ttu-id="15e25-104">В этом примере показано, как создать канал RSS/Atom для синдикации с помощью Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="15e25-104">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="15e25-105">Это базовая программа "Hello World", которая показывает основы объектной модели и способ ее настройки в службе Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="15e25-105">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="15e25-106">WCF моделирует веб-каналы синдикации как операции службы, возвращающие Специальный тип данных <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> .</span><span class="sxs-lookup"><span data-stu-id="15e25-106">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="15e25-107">Экземпляры <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> могут сериализовать веб-канал в форматы RSS 2.0 и Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="15e25-107">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="15e25-108">В следующем примере кода показан использованный контракт.</span><span class="sxs-lookup"><span data-stu-id="15e25-108">The following sample code shows the contract used.</span></span>  
  
```csharp  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 <span data-ttu-id="15e25-109">`GetProcesses`Операция помечена <xref:System.ServiceModel.Web.WebGetAttribute> атрибутом, который позволяет управлять тем, как WCF отправляет HTTP-запросы GET к операциям службы и задает формат отправленных сообщений.</span><span class="sxs-lookup"><span data-stu-id="15e25-109">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="15e25-110">Как и любая служба WCF, веб-каналы синдикации могут размещаться в любом управляемом приложении.</span><span class="sxs-lookup"><span data-stu-id="15e25-110">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="15e25-111">Для правильной работы служб синдикации требуются особая привязка (<xref:System.ServiceModel.WebHttpBinding>) и специальное поведение конечной точки (<xref:System.ServiceModel.Description.WebHttpBehavior>).</span><span class="sxs-lookup"><span data-stu-id="15e25-111">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="15e25-112">Новый класс <xref:System.ServiceModel.Web.WebServiceHost> обеспечивает удобный программный интерфейс для создания таких конечных точек без особой конфигурации.</span><span class="sxs-lookup"><span data-stu-id="15e25-112">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="15e25-113">В качестве альтернативного варианта можно использовать <xref:System.ServiceModel.Activation.WebServiceHostFactory> из размещенного в службах IIS файла SVC, чтобы обеспечить аналогичную функциональность (этот метод не показан в примере коде).</span><span class="sxs-lookup"><span data-stu-id="15e25-113">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```xml
<% @ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 <span data-ttu-id="15e25-114">Поскольку эта служба получает запросы с использованием стандартного метода HTTP GET, для доступа к службе можно использовать любой клиент, поддерживающий RSS или ATOM.</span><span class="sxs-lookup"><span data-stu-id="15e25-114">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="15e25-115">Например, можно просмотреть выходные данные этой службы, перейдя по `http://localhost:8000/diagnostics/feed/?format=atom` `http://localhost:8000/diagnostics/feed/?format=rss` адресу или в браузере, поддерживающем RSS.</span><span class="sxs-lookup"><span data-stu-id="15e25-115">For example, you can view the output of this service by navigating to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` in an RSS-aware browser.</span></span>
  
 <span data-ttu-id="15e25-116">Вы также можете использовать [объектную модель синдикации WCF для сопоставления с Atom и RSS](../feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) , чтобы считывать данные из синдикации и обрабатывать их с помощью императивного кода.</span><span class="sxs-lookup"><span data-stu-id="15e25-116">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```csharp
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",
    new XmlReaderSettings()
    {
        //MaxCharactersInDocument can be used to control the maximum amount of data
        //read from the reader and helps prevent OutOfMemoryException
        MaxCharactersInDocument = 1024 * 64
    } );

SyndicationFeed feed = SyndicationFeed.Load(reader);

foreach (SyndicationItem i in feed.Items)
{
    XmlSyndicationContent content = i.Content as XmlSyndicationContent;
    ProcessData pd = content.ReadContent<ProcessData>();

    Console.WriteLine(i.Title.Text);
    Console.WriteLine(pd.ToString());
}
```
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="15e25-117">Настройка, сборка и запуск примера</span><span class="sxs-lookup"><span data-stu-id="15e25-117">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="15e25-118">Убедитесь, что у вас есть право на регистрацию адресов HTTP и HTTPS на компьютере, как описано в разделе Настройка инструкций в ходе [одноразовой настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="15e25-118">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="15e25-119">Создайте решение.</span><span class="sxs-lookup"><span data-stu-id="15e25-119">Build the solution.</span></span>

3. <span data-ttu-id="15e25-120">Запустите консольное приложение.</span><span class="sxs-lookup"><span data-stu-id="15e25-120">Run the console application.</span></span>

4. <span data-ttu-id="15e25-121">Во время работы консольного приложения перейдите к `http://localhost:8000/diagnostics/feed/?format=atom` `http://localhost:8000/diagnostics/feed/?format=rss` браузеру, поддерживающему RSS, или используйте его.</span><span class="sxs-lookup"><span data-stu-id="15e25-121">While the console application is running, navigate to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` using an RSS-aware browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="15e25-122">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="15e25-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="15e25-123">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="15e25-123">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="15e25-124">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="15e25-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="15e25-125">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="15e25-125">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a><span data-ttu-id="15e25-126">См. также</span><span class="sxs-lookup"><span data-stu-id="15e25-126">See also</span></span>

- [<span data-ttu-id="15e25-127">Модель веб-программирования HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="15e25-127">WCF Web HTTP Programming Model</span></span>](../feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="15e25-128">Синдикация WCF</span><span class="sxs-lookup"><span data-stu-id="15e25-128">WCF Syndication</span></span>](../feature-details/wcf-syndication.md)
