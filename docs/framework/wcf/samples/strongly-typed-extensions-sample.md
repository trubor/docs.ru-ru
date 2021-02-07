---
description: 'Дополнительные сведения о: пример строго типизированных расширений'
title: Пример строго типизированных расширений
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: dd0a12b07db3f805f041742c8957cd46bb418bad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668764"
---
# <a name="strongly-typed-extensions-sample"></a><span data-ttu-id="40c69-103">Пример строго типизированных расширений</span><span class="sxs-lookup"><span data-stu-id="40c69-103">Strongly typed extensions sample</span></span>

<span data-ttu-id="40c69-104">В этом примере используется класс <xref:System.ServiceModel.Syndication.SyndicationFeed>.</span><span class="sxs-lookup"><span data-stu-id="40c69-104">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="40c69-105">Однако показанные в примере шаблоны можно использовать со всеми классами Syndication, которые поддерживают данные расширения.</span><span class="sxs-lookup"><span data-stu-id="40c69-105">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data.</span></span>  
  
 <span data-ttu-id="40c69-106">Объектная модель синдикации (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem> и связанные классы) поддерживает слабо типизированный доступ к данным расширений с использованием свойств <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> и <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span><span class="sxs-lookup"><span data-stu-id="40c69-106">The Syndication object model (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, and related classes) supports loosely-typed access to extension data by using the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> properties.</span></span> <span data-ttu-id="40c69-107">В этом примере показано, как обеспечить строго типизированный доступ к данным расширения путем реализации пользовательских производных классов <xref:System.ServiceModel.Syndication.SyndicationFeed> и <xref:System.ServiceModel.Syndication.SyndicationItem> сделать доступными определенные расширения для конкретных приложений как строго типизированные свойства.</span><span class="sxs-lookup"><span data-stu-id="40c69-107">This sample shows how to provide strongly typed access to extension data by implementing custom derived classes of <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> that make available certain application-specific extensions as strongly typed properties.</span></span>  
  
 <span data-ttu-id="40c69-108">Например, здесь показано, как реализовать элемент расширения, определенный в документе RFC "Atom Threading Extensions".</span><span class="sxs-lookup"><span data-stu-id="40c69-108">As an example, this sample shows how to implement an extension element defined in the proposed Atom Threading Extensions RFC.</span></span> <span data-ttu-id="40c69-109">Этот образец приводится исключительно с целью демонстрации и не является полной реализацией предлагаемой спецификации.</span><span class="sxs-lookup"><span data-stu-id="40c69-109">This is for demonstration purposes only and this sample is not intended to be a full implementation of the proposed specification.</span></span>  
  
## <a name="sample-xml"></a><span data-ttu-id="40c69-110">Образец XML</span><span class="sxs-lookup"><span data-stu-id="40c69-110">Sample XML</span></span>  

 <span data-ttu-id="40c69-111">В следующем примере XML показана запись Atom 1.0 с дополнительным элементом расширения `<in-reply-to>`.</span><span class="sxs-lookup"><span data-stu-id="40c69-111">The following XML example shows an Atom 1.0 entry with an additional `<in-reply-to>` extension element.</span></span>  
  
```xml  
<entry>  
    <id>tag:example.org,2005:1,2</id>  
    <title type="text">Another response to the original</title>  
    <summary type="text">  
         This is a response to the original entry</summary>  
    <updated>2006-03-01T12:12:13Z</updated>  
    <link href="http://www.example.org/entries/1/2" />  
    <in-reply-to p3:ref="tag:example.org,2005:1"
                 p3:href="http://www.example.org/entries/1"
                 p3:type="application/xhtml+xml"
                 xmlns:p3="http://contoso.org/syndication/thread/1.0"
                 xmlns="http://contoso.org/syndication/thread/1.0">  
      <anotherElement xmlns="http://www.w3.org/2005/Atom">  
                     Some more data</anotherElement>  
      <aDifferentElement xmlns="http://www.w3.org/2005/Atom">  
                     Even more data</aDifferentElement>  
    </in-reply-to>  
</entry>  
```  
  
 <span data-ttu-id="40c69-112">`<in-reply-to>`Элемент задает три обязательных атрибута ( `ref` `type` и), `href` а также разрешение на присутствие дополнительных атрибутов расширения и элементов расширения.</span><span class="sxs-lookup"><span data-stu-id="40c69-112">The `<in-reply-to>` element specifies three required attributes (`ref`, `type` and `href`) while also allowing for the presence of additional extension attributes and extension elements.</span></span>  
  
## <a name="modeling-the-in-reply-to-element"></a><span data-ttu-id="40c69-113">Моделирование элемента In-Reply-To</span><span class="sxs-lookup"><span data-stu-id="40c69-113">Modeling the In-Reply-To element</span></span>  

 <span data-ttu-id="40c69-114">В этом образце элемент `<in-reply-to>` моделируется в среде CLR, которая реализует интерфейс <xref:System.Xml.Serialization.IXmlSerializable>, позволяющий использовать его с <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="40c69-114">In this sample, the `<in-reply-to>` element is modeled as CLR that implements <xref:System.Xml.Serialization.IXmlSerializable>, which enables its use with the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="40c69-115">Он также реализует некоторые методы и свойства для доступа к данным элемента, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="40c69-115">It also implements some methods and properties for accessing the element's data, as shown in the following sample code.</span></span>  
  
```csharp  
[XmlRoot(ElementName = "in-reply-to", Namespace = "http://contoso.org/syndication/thread/1.0")]  
public class InReplyToElement : IXmlSerializable  
{  
    internal const string ElementName = "in-reply-to";  
    internal const string NsUri =
                  "http://contoso.org/syndication/thread/1.0";  
    private Dictionary<XmlQualifiedName, string> extensionAttributes;  
    private Collection<XElement> extensionElements;  
  
    public InReplyToElement()  
    {  
        this.extensionElements = new Collection<XElement>();  
        this.extensionAttributes = new Dictionary<XmlQualifiedName,
                                                          string>();  
    }  
  
    public Dictionary<XmlQualifiedName, string> AttributeExtensions  
    {  
        get { return this.extensionAttributes; }  
    }  
  
    public Collection<XElement> ElementExtensions  
    {  
        get { return this.extensionElements; }  
    }  
  
    public Uri Href  
    { get; set; }  
  
    public string MediaType  
    { get; set; }  
  
    public string Ref  
    { get; set; }  
  
    public Uri Source  
    { get; set; }  
}  
```  
  
 <span data-ttu-id="40c69-116">Класс `InReplyToElement` реализует свойства для обязательного атрибута (`HRef`, `MediaType` и `Source`), а также коллекцию для хранения расширений <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> и <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span><span class="sxs-lookup"><span data-stu-id="40c69-116">The `InReplyToElement` class implements properties for the required attribute (`HRef`, `MediaType`, and `Source`) as well as collections to hold <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span></span>  
  
 <span data-ttu-id="40c69-117">Класс `InReplyToElement` реализует интерфейс <xref:System.Xml.Serialization.IXmlSerializable>, который позволяет напрямую управлять тем, как экземпляры объектов считываются из XML и записываются в XML.</span><span class="sxs-lookup"><span data-stu-id="40c69-117">The `InReplyToElement` class implements the <xref:System.Xml.Serialization.IXmlSerializable> interface, which allows direct control over how object instances are read from and written to XML.</span></span> <span data-ttu-id="40c69-118">Метод `ReadXml` сначала считывает значения свойств `Ref`, `HRef`, `Source` и `MediaType` из переданного ему объекта <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="40c69-118">The `ReadXml` method first reads the values for the `Ref`, `HRef`, `Source`, and `MediaType` properties from the <xref:System.Xml.XmlReader> passed to it.</span></span> <span data-ttu-id="40c69-119">Все неизвестные атрибуты хранятся в коллекции <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A>.</span><span class="sxs-lookup"><span data-stu-id="40c69-119">Any unknown attributes are stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection.</span></span> <span data-ttu-id="40c69-120">После чтения всех атрибутов вызывается метод <xref:System.Xml.XmlReader.ReadStartElement>, чтобы перевести средство чтения к следующему элементу.</span><span class="sxs-lookup"><span data-stu-id="40c69-120">When all the attributes have been read, <xref:System.Xml.XmlReader.ReadStartElement> is called to advance the reader to the next element.</span></span> <span data-ttu-id="40c69-121">Поскольку у моделируемого этим классом элемента нет обязательных дочерних элементов, дочерние элементы буферизуются в экземплярах `XElement` и хранятся в коллекции <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="40c69-121">Because the element modeled by this class has no required children, the child elements get buffered into `XElement` instances and stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection, as shown in the following code.</span></span>  
  
```csharp
public void ReadXml(System.Xml.XmlReader reader)  
{  
    bool isEmpty = reader.IsEmptyElement;  
  
    if (reader.HasAttributes)  
    {  
        for (int i = 0; i < reader.AttributeCount; i++)  
        {  
            reader.MoveToNextAttribute();  
  
            if (reader.NamespaceURI == "")  
            {  
                if (reader.LocalName == "ref")  
                {  
                    this.Ref = reader.Value;  
                }  
                else if (reader.LocalName == "href")  
                {  
                    this.Href = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "source")  
                {  
                    this.Source = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "type")  
                {  
                    this.MediaType = reader.Value;  
                }  
                else  
                {  
                    this.AttributeExtensions.Add(new
                                 XmlQualifiedName(reader.LocalName,
                                 reader.NamespaceURI),
                                 reader.Value);  
                }  
            }  
        }  
    }  
  
    reader.ReadStartElement();  
  
    if (!isEmpty)  
    {  
        while (reader.IsStartElement())  
        {  
            ElementExtensions.Add(  
                  (XElement) XElement.ReadFrom(reader));  
        }  
        reader.ReadEndElement();  
    }  
}  
```  
  
 <span data-ttu-id="40c69-122">В `WriteXml` в методе `InReplyToElement` сначала записывает значения из свойств `Ref`, `HRef`, `Source` и `MediaType` в виде атрибутов XML (`WriteXml` не отвечает за запись самого внешнего элемента, поскольку это делает сторона, вызывающая `WriteXml`).</span><span class="sxs-lookup"><span data-stu-id="40c69-122">In `WriteXml`, the `InReplyToElement` method first writes out the values of the `Ref`, `HRef`, `Source`, and `MediaType` properties as XML attributes (`WriteXml` is not responsible for writing the actual outer element itself, as that done by the caller of `WriteXml`).</span></span> <span data-ttu-id="40c69-123">Кроме того, он записывает содержимое свойств <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> и <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> в средство записи, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="40c69-123">It also writes the contents of the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> to the writer, as shown in the following code.</span></span>  
  
```csharp
public void WriteXml(System.Xml.XmlWriter writer)  
{  
    if (this.Ref != null)  
    {  
        writer.WriteAttributeString("ref", InReplyToElement.NsUri,
                                            this.Ref);  
    }  
    if (this.Href != null)  
    {  
        writer.WriteAttributeString("href", InReplyToElement.NsUri,
                                                this.Href.ToString());  
    }  
    if (this.Source != null)  
    {  
        writer.WriteAttributeString("source", InReplyToElement.NsUri,
                                              this.Source.ToString());  
    }  
    if (this.MediaType != null)  
    {  
        writer.WriteAttributeString("type", InReplyToElement.NsUri,
                                                    this.MediaType);  
    }  
  
    foreach (KeyValuePair<XmlQualifiedName, string> kvp in
                                             this.AttributeExtensions)  
    {  
        writer.WriteAttributeString(kvp.Key.Name, kvp.Key.Namespace,
                                                   kvp.Value);  
    }  
  
    foreach (XElement element in this.ElementExtensions)  
    {  
        element.WriteTo(writer);  
    }  
}  
```  
  
## <a name="threadedfeed-and-threadeditem"></a><span data-ttu-id="40c69-124">ThreadedFeed и ThreadedItem</span><span class="sxs-lookup"><span data-stu-id="40c69-124">ThreadedFeed and ThreadedItem</span></span>  

 <span data-ttu-id="40c69-125">В этом образце элементы `SyndicationItems` с расширениями `InReplyTo` моделируются с помощью класса `ThreadedItem`.</span><span class="sxs-lookup"><span data-stu-id="40c69-125">In the sample, `SyndicationItems` with `InReplyTo` extensions are modeled by the `ThreadedItem` class.</span></span> <span data-ttu-id="40c69-126">Аналогично класс `ThreadedFeed` является каналом `SyndicationFeed`, элементы которого являются экземплярами `ThreadedItem`.</span><span class="sxs-lookup"><span data-stu-id="40c69-126">Similarly, the `ThreadedFeed` class is a `SyndicationFeed` whose items are all instances of `ThreadedItem`.</span></span>  
  
 <span data-ttu-id="40c69-127">Класс `ThreadedFeed` наследует классу `SyndicationFeed` и переопределяет метод `OnCreateItem`, чтобы он возвращал элементы `ThreadedItem`.</span><span class="sxs-lookup"><span data-stu-id="40c69-127">The `ThreadedFeed` class inherits from `SyndicationFeed` and overrides `OnCreateItem` to return a `ThreadedItem`.</span></span> <span data-ttu-id="40c69-128">Кроме того, он реализует метод для доступа к коллекции `Items` в виде `ThreadedItems`, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="40c69-128">It also implements a method for accessing the `Items` collection as `ThreadedItems`, as shown in the following code.</span></span>  
  
```csharp
public class ThreadedFeed : SyndicationFeed  
{  
    public ThreadedFeed()  
    {  
    }  
  
    public IEnumerable<ThreadedItem> ThreadedItems  
    {  
        get  
        {  
            return this.Items.Cast<ThreadedItem>();  
        }  
    }  
  
    protected override SyndicationItem CreateItem()  
    {  
        return new ThreadedItem();  
    }  
}  
```  
  
 <span data-ttu-id="40c69-129">Класс `ThreadedItem` наследует от класса `SyndicationItem` и делает `InReplyToElement` его свойством со строгой типизацией.</span><span class="sxs-lookup"><span data-stu-id="40c69-129">The class `ThreadedItem` inherits from `SyndicationItem` and makes `InReplyToElement` as a strongly typed property.</span></span> <span data-ttu-id="40c69-130">Это делает возможным удобный программный доступ к данным расширений `InReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="40c69-130">This provides for convenient programmatic access to the `InReplyTo` extension data.</span></span> <span data-ttu-id="40c69-131">Кроме того, он реализует методы `TryParseElement` и `WriteElementExtensions` для чтения и записи данных расширений, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="40c69-131">It also implements `TryParseElement` and `WriteElementExtensions` for reading and writing its extension data, as shown in the following code.</span></span>  
  
```csharp
public class ThreadedItem : SyndicationItem  
{  
    private InReplyToElement inReplyTo;  
    // Constructors  
        public ThreadedItem()  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
        public ThreadedItem(string title, string content, Uri itemAlternateLink, string id, DateTimeOffset lastUpdatedTime) : base(title, content, itemAlternateLink, id, lastUpdatedTime)  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
    public InReplyToElement InReplyTo  
    {  
        get { return this.inReplyTo; }  
    }  
  
    protected override bool TryParseElement(  
                        System.Xml.XmlReader reader,
                        string version)  
    {  
        if (version == SyndicationVersions.Atom10 &&  
            reader.NamespaceURI == InReplyToElement.NsUri &&  
            reader.LocalName == InReplyToElement.ElementName)  
        {  
            this.inReplyTo = new InReplyToElement();  
  
            this.InReplyTo.ReadXml(reader);  
  
            return true;  
        }  
        else  
        {  
            return base.TryParseElement(reader, version);  
        }  
    }  
  
    protected override void WriteElementExtensions(XmlWriter writer,
                                                 string version)  
    {  
        if (this.InReplyTo != null &&
                     version == SyndicationVersions.Atom10)  
        {  
            writer.WriteStartElement(InReplyToElement.ElementName,
                                           InReplyToElement.NsUri);  
            this.InReplyTo.WriteXml(writer);  
            writer.WriteEndElement();  
        }  
  
        base.WriteElementExtensions(writer, version);  
    }  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="40c69-132">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="40c69-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="40c69-133">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40c69-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="40c69-134">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40c69-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="40c69-135">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40c69-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="40c69-136">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="40c69-136">The samples may already be installed on your computer.</span></span> <span data-ttu-id="40c69-137">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="40c69-137">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="40c69-138">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="40c69-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="40c69-139">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="40c69-139">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
