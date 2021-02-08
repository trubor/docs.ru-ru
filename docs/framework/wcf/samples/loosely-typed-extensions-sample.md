---
description: 'Дополнительные сведения: пример расширений Loosely-Typed'
title: Пример слабо типизированных расширений
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: cd430a922a35baf0ed9ce387b7df81fa3af6b35d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793237"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="36e93-103">Пример слабо типизированных расширений</span><span class="sxs-lookup"><span data-stu-id="36e93-103">Loosely-Typed Extensions Sample</span></span>

<span data-ttu-id="36e93-104">Объектная модель синдикации обеспечивает широкую поддержку работы с данными расширения - информацией, присутствующей в XML-представлении канала синдикации, но не предоставляемой в явном виде такими классами, как <xref:System.ServiceModel.Syndication.SyndicationFeed> и <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="36e93-104">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="36e93-105">Этот пример иллюстрирует основные приемы работы с данными расширения.</span><span class="sxs-lookup"><span data-stu-id="36e93-105">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="36e93-106">В этом примере используется класс <xref:System.ServiceModel.Syndication.SyndicationFeed>.</span><span class="sxs-lookup"><span data-stu-id="36e93-106">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="36e93-107">Однако показанные в примере шаблоны можно использовать со всеми классами Syndication, которые поддерживают данные расширения:</span><span class="sxs-lookup"><span data-stu-id="36e93-107">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="36e93-108">Образец XML</span><span class="sxs-lookup"><span data-stu-id="36e93-108">Sample XML</span></span>  

 <span data-ttu-id="36e93-109">Для справки: в этом примере используется следующий XML-документ.</span><span class="sxs-lookup"><span data-stu-id="36e93-109">For reference, the following XML document is used in this sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<feed myAttribute="someValue" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text"></title>  
  <id>uuid:8f60c7b3-a3c0-4de7-a642-2165d77ce3c1;id=1</id>  
  <updated>2007-09-07T22:15:34Z</updated>  
  <simpleString xmlns="">hello, world!</simpleString>  
  <simpleString xmlns="">another simple string</simpleString>  
  <DataContractExtension xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.d  
atacontract.org/2004/07/Microsoft.Syndication.Samples">  
    <Key>X</Key>  
    <Value>4</Value>  
  </DataContractExtension>  
  <XmlSerializerExtension xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://ww  
w.w3.org/2001/XMLSchema" xmlns="">  
    <Key>Y</Key>  
    <Value>8</Value>  
  </XmlSerializerExtension>  
  <xElementExtension xmlns="">  
    <Key attr1="someValue">Z</Key>  
    <Value attr1="someValue">15</Value>  
  </xElementExtension>  
</feed>  
```  
  
 <span data-ttu-id="36e93-110">Этот документ содержит следующие части данных расширения:</span><span class="sxs-lookup"><span data-stu-id="36e93-110">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="36e93-111">Атрибут `myAttribute` элемента `<feed>`.</span><span class="sxs-lookup"><span data-stu-id="36e93-111">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="36e93-112">Элемент `<simpleString>`.</span><span class="sxs-lookup"><span data-stu-id="36e93-112">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="36e93-113">Элемент `<DataContractExtension>`.</span><span class="sxs-lookup"><span data-stu-id="36e93-113">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="36e93-114">Элемент `<XmlSerializerExtension>`.</span><span class="sxs-lookup"><span data-stu-id="36e93-114">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="36e93-115">Элемент `<xElementExtension>`.</span><span class="sxs-lookup"><span data-stu-id="36e93-115">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="36e93-116">Запись данных расширений</span><span class="sxs-lookup"><span data-stu-id="36e93-116">Writing Extension Data</span></span>  

 <span data-ttu-id="36e93-117">Расширения атрибутов создаются путем добавления записей в коллекцию <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A>, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="36e93-117">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="36e93-118">Расширения элементов создаются путем добавления записей в коллекцию <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span><span class="sxs-lookup"><span data-stu-id="36e93-118">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="36e93-119">Эти расширения могут быть базовыми значениями, такими как строки, XML-сериализациями объектов платформы .NET Framework или XML-узлами, код которых написан вручную.</span><span class="sxs-lookup"><span data-stu-id="36e93-119">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="36e93-120">В следующем примере кода создается элемент расширения с именем `simpleString`.</span><span class="sxs-lookup"><span data-stu-id="36e93-120">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="36e93-121">Пространством имен XML для этого элемента является пустое пространство имен (""), а его значение является текстовым узлом, содержащим строку "Hello, World!".</span><span class="sxs-lookup"><span data-stu-id="36e93-121">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="36e93-122">Одним из способов создания расширений сложных элементов, содержащий много вложенных элементов, является использование для сериализации интерфейсов API платформы .NET Framework (поддерживаются как <xref:System.Runtime.Serialization.DataContractSerializer>, так и <xref:System.Xml.Serialization.XmlSerializer>), как показано в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="36e93-122">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="36e93-123">В этом примере `DataContractExtension` и `XmlSerializerExtension` представляют собой пользовательские типы, созданные для использования с сериализатором.</span><span class="sxs-lookup"><span data-stu-id="36e93-123">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="36e93-124">Класс <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> также может использоваться для создания расширений элементов из экземпляра <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="36e93-124">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="36e93-125">Это обеспечивает простую интеграцию с интерфейсами API, обрабатывающими XML, такими как <xref:System.Xml.Linq.XElement>, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="36e93-125">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="36e93-126">Чтение данных расширений</span><span class="sxs-lookup"><span data-stu-id="36e93-126">Reading Extension Data</span></span>  

 <span data-ttu-id="36e93-127">Значения для расширений атрибутов можно получить, произведя поиск атрибута в коллекции <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> по его имени <xref:System.Xml.XmlQualifiedName>, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="36e93-127">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="36e93-128">Для доступа к расширениям элементов служит метод `ReadElementExtensions<T>`.</span><span class="sxs-lookup"><span data-stu-id="36e93-128">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
```csharp  
foreach( string s in feed2.ElementExtensions.ReadElementExtensions<string>("simpleString", ""))  
{  
    Console.WriteLine(s);  
}  
  
foreach (DataContractExtension dce in feed2.ElementExtensions.ReadElementExtensions<DataContractExtension>("DataContractExtension",  
"http://schemas.datacontract.org/2004/07/SyndicationExtensions"))  
{  
    Console.WriteLine(dce.ToString());  
}  
  
foreach (XmlSerializerExtension xse in feed2.ElementExtensions.ReadElementExtensions<XmlSerializerExtension>("XmlSerializerExtension", "", new XmlSerializer(typeof(XmlSerializerExtension))))  
{  
    Console.WriteLine(xse.ToString());  
}  
```  
  
 <span data-ttu-id="36e93-129">Можно также получить средство чтения `XmlReader` для расширений отдельных элементов с помощью метода <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader>.</span><span class="sxs-lookup"><span data-stu-id="36e93-129">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="36e93-130">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="36e93-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="36e93-131">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="36e93-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="36e93-132">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="36e93-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="36e93-133">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="36e93-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="36e93-134">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="36e93-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="36e93-135">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="36e93-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="36e93-136">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="36e93-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="36e93-137">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="36e93-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="36e93-138">См. также</span><span class="sxs-lookup"><span data-stu-id="36e93-138">See also</span></span>

- [<span data-ttu-id="36e93-139">Строго типизированные расширения</span><span class="sxs-lookup"><span data-stu-id="36e93-139">Strongly typed Extensions</span></span>](strongly-typed-extensions-sample.md)
- [<span data-ttu-id="36e93-140">Синдикация WCF</span><span class="sxs-lookup"><span data-stu-id="36e93-140">WCF Syndication</span></span>](../feature-details/wcf-syndication.md)
