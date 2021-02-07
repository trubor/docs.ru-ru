---
description: Дополнительные сведения о примере потоковой передачи — пример
title: Пример потоковой передачи каналов
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 1de295391316396d6c454496d34d8b82ad8129d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668752"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="7dc51-103">Пример потоковой передачи каналов</span><span class="sxs-lookup"><span data-stu-id="7dc51-103">Streaming Feeds Sample</span></span>

<span data-ttu-id="7dc51-104">В этом образце показано, как управлять веб-каналами синдикации, содержащими большое число элементов.</span><span class="sxs-lookup"><span data-stu-id="7dc51-104">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="7dc51-105">На стороне сервера этот пример показывает, как откладывать создание отдельных объектов <xref:System.ServiceModel.Syndication.SyndicationItem> в веб-канале до момента записи элемента в сетевой поток.</span><span class="sxs-lookup"><span data-stu-id="7dc51-105">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="7dc51-106">На стороне клиента этот пример показывает, что для чтения отдельных элементов из сетевого потока можно использовать пользовательский модуль форматирования веб-канала синдикации, чтобы читаемый веб-канал никогда не буферизовался в памяти целиком.</span><span class="sxs-lookup"><span data-stu-id="7dc51-106">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="7dc51-107">Для лучшей демонстрации возможности потоковой передачи API синдикации в этом образце используется достаточно нереальный сценарий, при котором сервер предоставляет веб-канал с бесконечным числом элементов.</span><span class="sxs-lookup"><span data-stu-id="7dc51-107">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="7dc51-108">В этом случае сервер продолжает создавать в веб-канале новые элементы, пока он не определит, что клиент не прочитал из веб-канала заданное число элементов (по умолчанию - 10).</span><span class="sxs-lookup"><span data-stu-id="7dc51-108">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="7dc51-109">Для простоты клиент и служба реализованы в одном процессе и используют общий объект `ItemCounter` для отслеживания числа элементов, созданных клиентом.</span><span class="sxs-lookup"><span data-stu-id="7dc51-109">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="7dc51-110">Тип `ItemCounter` нужен лишь для того, чтобы пример можно было верно завершить, и не является ключевым элементом демонстрируемого сценария.</span><span class="sxs-lookup"><span data-stu-id="7dc51-110">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="7dc51-111">В демонстрации используются итераторы Visual C# (с использованием `yield return` конструкции ключевого слова).</span><span class="sxs-lookup"><span data-stu-id="7dc51-111">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="7dc51-112">Дополнительные сведения о итераторах см. в разделе "использование итераторов" на сайте MSDN.</span><span class="sxs-lookup"><span data-stu-id="7dc51-112">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="7dc51-113">Служба</span><span class="sxs-lookup"><span data-stu-id="7dc51-113">Service</span></span>  

 <span data-ttu-id="7dc51-114">Служба реализует базовый контракт <xref:System.ServiceModel.Web.WebGetAttribute>, состоящий из одной операции, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="7dc51-114">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="7dc51-115">Служба реализует этот контракт с помощью класса `ItemGenerator`, создающего потенциально бесконечный поток экземпляров <xref:System.ServiceModel.Syndication.SyndicationItem> с использованием итератора, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="7dc51-115">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
```csharp
class ItemGenerator  
{  
    public IEnumerable<SyndicationItem> GenerateItems()  
    {  
        while (counter.GetCount() < maxItemsRead)  
        {  
            itemsReturned++;  
            yield return CreateNextItem();  
        }  
  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="7dc51-116">Когда реализация службы создает веб-канал, вместо буферизованной коллекции элементов используется вывод метода `ItemGenerator.GenerateItems()`.</span><span class="sxs-lookup"><span data-stu-id="7dc51-116">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
```csharp
public Atom10FeedFormatter StreamedFeed()  
{  
    SyndicationFeed feed = new SyndicationFeed("Streamed feed", "Feed to test streaming", null);  
    //Generate an infinite stream of items. Both the client and the service share  
    //a reference to the ItemCounter, which allows the sample to terminate  
    //execution after the client has read 10 items from the stream  
    ItemGenerator itemGenerator = new ItemGenerator(this.counter, 10);  
  
    feed.Items = itemGenerator.GenerateItems();  
    return feed.GetAtom10Formatter();  
}  
```  
  
 <span data-ttu-id="7dc51-117">В результате поток элементов никогда не помещается в буфер памяти целиком.</span><span class="sxs-lookup"><span data-stu-id="7dc51-117">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="7dc51-118">Это поведение можно проследить, установив точку останова в `yield return` операторе внутри `ItemGenerator.GenerateItems()` метода и отметив, что эта точка останова встречается в первый раз после того, как служба возвращала результат `StreamedFeed()` метода.</span><span class="sxs-lookup"><span data-stu-id="7dc51-118">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="7dc51-119">Клиент</span><span class="sxs-lookup"><span data-stu-id="7dc51-119">Client</span></span>  

 <span data-ttu-id="7dc51-120">Клиент в этом образце применяет пользовательскую реализацию <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>, которая задерживает воссоздание отдельных элементов в веб-канале вместо их записи в буфер в памяти.</span><span class="sxs-lookup"><span data-stu-id="7dc51-120">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="7dc51-121">Пользовательский экземпляр `StreamedAtom10FeedFormatter` используется следующим образом.</span><span class="sxs-lookup"><span data-stu-id="7dc51-121">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="7dc51-122">Обычно вызов метода <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> не завершается, пока будет прочитано из сети и записано в буфер в памяти все содержимое веб-канала.</span><span class="sxs-lookup"><span data-stu-id="7dc51-122">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="7dc51-123">Однако класс `StreamedAtom10FeedFormatter` переопределяет метод <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29>, чтобы вместо буферизованной коллекции он возвращал итератор, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="7dc51-123">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
```csharp  
protected override IEnumerable<SyndicationItem> ReadItems(XmlReader reader, SyndicationFeed feed, out bool areAllItemsRead)  
{  
    areAllItemsRead = false;  
    return DelayReadItems(reader, feed);  
}  
  
private IEnumerable<SyndicationItem> DelayReadItems(XmlReader reader, SyndicationFeed feed)  
{  
    while (reader.IsStartElement("entry", "http://www.w3.org/2005/Atom"))  
    {  
        yield return this.ReadItem(reader, feed);  
    }  
  
    reader.ReadEndElement();  
}  
```  
  
 <span data-ttu-id="7dc51-124">В результате элемент не будет прочитан из сети, пока клиентское приложение, через которое проходят результаты вызова метода `ReadItems()`, не будет готово к использованию этого элемента.</span><span class="sxs-lookup"><span data-stu-id="7dc51-124">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="7dc51-125">Это поведение можно проследить, установив точку останова в `yield return` операторе в `StreamedAtom10FeedFormatter.DelayReadItems()` и убедившись, что эта точка останова встречается в первый раз после вызова метода `ReadFrom()` .</span><span class="sxs-lookup"><span data-stu-id="7dc51-125">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="7dc51-126">Ниже показано, как выполнить построение и запуск этого образца.</span><span class="sxs-lookup"><span data-stu-id="7dc51-126">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="7dc51-127">Обратите внимание, что хотя сервер прекращает создание элементов после того, как клиент прочтет 10 элементов, результат работы программы показывает, что клиент прочитывает гораздо больше, чем 10 элементов.</span><span class="sxs-lookup"><span data-stu-id="7dc51-127">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="7dc51-128">Это связано с тем, что используемая сетевая привязка передает данные фрагментами по 4 килобайта (КБ).</span><span class="sxs-lookup"><span data-stu-id="7dc51-128">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="7dc51-129">Таким образом, клиент получает 4 КБ данных элемента раньше, чем он сможет прочитать хотя бы один элемент.</span><span class="sxs-lookup"><span data-stu-id="7dc51-129">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="7dc51-130">Это нормальное поведение (разбиение данных на небольшие фрагменты при их потоковой передаче по протоколу HTTP повышает производительность).</span><span class="sxs-lookup"><span data-stu-id="7dc51-130">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7dc51-131">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="7dc51-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7dc51-132">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7dc51-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7dc51-133">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7dc51-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7dc51-134">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7dc51-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7dc51-135">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="7dc51-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7dc51-136">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="7dc51-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7dc51-137">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="7dc51-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7dc51-138">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="7dc51-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="7dc51-139">См. также</span><span class="sxs-lookup"><span data-stu-id="7dc51-139">See also</span></span>

- [<span data-ttu-id="7dc51-140">Автономный веб-канал диагностики</span><span class="sxs-lookup"><span data-stu-id="7dc51-140">Stand-Alone Diagnostics Feed</span></span>](stand-alone-diagnostics-feed-sample.md)
