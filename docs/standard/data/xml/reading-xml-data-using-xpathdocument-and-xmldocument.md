---
title: Чтение XML-данных с помощью XPathDocument и XmlDocument
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
ms.openlocfilehash: 8ffd03d1a9915bade6c4d421d5fad096a4784fb8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686791"
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a><span data-ttu-id="3be06-102">Чтение XML-данных с помощью XPathDocument и XmlDocument</span><span class="sxs-lookup"><span data-stu-id="3be06-102">Reading XML Data using XPathDocument and XmlDocument</span></span>

<span data-ttu-id="3be06-103">Существует два способа чтения XML-документа в пространстве имен <xref:System.Xml.XPath?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3be06-103">There are two ways to read an XML document in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="3be06-104">Один - считывание XML-документа с использованием доступного только для чтения класса <xref:System.Xml.XPath.XPathDocument>, а другой - считывание XML-документа с использованием редактируемого класса <xref:System.Xml.XmlDocument> в пространстве имен <xref:System.Xml?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3be06-104">One is to read an XML document using the read-only <xref:System.Xml.XPath.XPathDocument> class and the other is to read an XML document using the editable <xref:System.Xml.XmlDocument> class in the <xref:System.Xml?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a><span data-ttu-id="3be06-105">Чтение XML-документов с использованием класса XPathDocument</span><span class="sxs-lookup"><span data-stu-id="3be06-105">Reading XML Documents using the XPathDocument Class</span></span>  

 <span data-ttu-id="3be06-106">Класс <xref:System.Xml.XPath.XPathDocument> обеспечивает быстрое и доступное только для чтения представление XML-документа в памяти с использованием модели данных XPath.</span><span class="sxs-lookup"><span data-stu-id="3be06-106">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="3be06-107">Экземпляры класса <xref:System.Xml.XPath.XPathDocument> создаются с использованием одного из шести конструкторов.</span><span class="sxs-lookup"><span data-stu-id="3be06-107">Instances of the <xref:System.Xml.XPath.XPathDocument> class are created using one of its six constructors.</span></span> <span data-ttu-id="3be06-108">Эти конструкторы позволяют прочитать XML-документ с использованием как объектов <xref:System.IO.Stream>, <xref:System.IO.TextReader> или <xref:System.Xml.XmlReader>, так и строкового `string` пути к XML-файлу.</span><span class="sxs-lookup"><span data-stu-id="3be06-108">These constructors allow you to read an XML document using a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="3be06-109">В следующем примере продемонстрировано использование конструктора <xref:System.Xml.XPath.XPathDocument> класса `string` для чтения XML-документа.</span><span class="sxs-lookup"><span data-stu-id="3be06-109">The following example illustrates using the <xref:System.Xml.XPath.XPathDocument> class's `string` constructor to read an XML document.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a><span data-ttu-id="3be06-110">Чтение XML-документов с помощью класса XmlDocument</span><span class="sxs-lookup"><span data-stu-id="3be06-110">Reading XML Documents using the XmlDocument Class</span></span>  

 <span data-ttu-id="3be06-111">Класс <xref:System.Xml.XmlDocument> представляет собой изменяемое в памяти представление XML-документа, реализующего модель W3C DOM базового уровня 1 и базового уровня 2.</span><span class="sxs-lookup"><span data-stu-id="3be06-111">The <xref:System.Xml.XmlDocument> class is an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="3be06-112">Экземпляры класса <xref:System.Xml.XmlDocument> создаются с использованием одного из трех конструкторов.</span><span class="sxs-lookup"><span data-stu-id="3be06-112">Instances of the <xref:System.Xml.XmlDocument> class are created using one of its three constructors.</span></span> <span data-ttu-id="3be06-113">Можно создать новый, пустой объект <xref:System.Xml.XmlDocument> путем вызова конструктора класса <xref:System.Xml.XmlDocument> без параметров.</span><span class="sxs-lookup"><span data-stu-id="3be06-113">You can create a new, empty <xref:System.Xml.XmlDocument> object by calling the <xref:System.Xml.XmlDocument> class constructor with no parameters.</span></span> <span data-ttu-id="3be06-114">После вызова конструктора используйте метод <xref:System.Xml.XmlDocument.Load%2A>, чтобы загрузить XML-данные в новый объект <xref:System.Xml.XmlDocument> из объекта <xref:System.IO.Stream>, <xref:System.IO.TextReader> или <xref:System.Xml.XmlReader>, либо из строкового `string` пути к XML-файлу.</span><span class="sxs-lookup"><span data-stu-id="3be06-114">After calling the constructor, use the <xref:System.Xml.XmlDocument.Load%2A> method to load XML data into the new <xref:System.Xml.XmlDocument> object from a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="3be06-115">В следующем примере продемонстрировано использование конструктора класса <xref:System.Xml.XmlDocument> без параметров и метода <xref:System.Xml.XmlDocument.Load%2A> для чтения XML-документа.</span><span class="sxs-lookup"><span data-stu-id="3be06-115">The following example illustrates using the <xref:System.Xml.XmlDocument> class constructor with no parameters and the <xref:System.Xml.XmlDocument.Load%2A> method to read an XML document.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a><span data-ttu-id="3be06-116">Определение кодировки XML-документа</span><span class="sxs-lookup"><span data-stu-id="3be06-116">Determining the Encoding of an XML Document</span></span>  

 <span data-ttu-id="3be06-117">Объект <xref:System.Xml.XmlReader> можно использовать для чтения XML-документа и создания объектов <xref:System.Xml.XPath.XPathDocument> и <xref:System.Xml.XmlDocument>, как показано в предыдущих разделах.</span><span class="sxs-lookup"><span data-stu-id="3be06-117">An <xref:System.Xml.XmlReader> object can be used to read an XML document and to create <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> objects as shown in the previous sections.</span></span> <span data-ttu-id="3be06-118">Однако объект <xref:System.Xml.XmlReader> может считывать данные, которые не закодированы и не содержат никаких сведений о кодировке.</span><span class="sxs-lookup"><span data-stu-id="3be06-118">However, an <xref:System.Xml.XmlReader> object may read data that is not encoded and as a result does not provide any encoding information.</span></span>  
  
 <span data-ttu-id="3be06-119">Класс <xref:System.Xml.XmlTextReader> наследуется от класса <xref:System.Xml.XmlReader> и предоставляет сведения о кодировке с помощью свойства <xref:System.Xml.XmlTextReader.Encoding%2A>. Его можно использовать для создания объекта <xref:System.Xml.XPath.XPathDocument> или объекта <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="3be06-119">The <xref:System.Xml.XmlTextReader> class inherits from the <xref:System.Xml.XmlReader> class, provides encoding information using its <xref:System.Xml.XmlTextReader.Encoding%2A> property, and can be used to create an <xref:System.Xml.XPath.XPathDocument> object or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="3be06-120">Дополнительные сведения о кодировке, предоставляемых классом <xref:System.Xml.XmlTextReader> см. в справочной документации по свойству <xref:System.Xml.XmlTextReader.Encoding%2A> класса <xref:System.Xml.XmlTextReader>.</span><span class="sxs-lookup"><span data-stu-id="3be06-120">For more information about the encoding information provided by the <xref:System.Xml.XmlTextReader> class, see the <xref:System.Xml.XmlTextReader.Encoding%2A> property in the <xref:System.Xml.XmlTextReader> class reference documentation.</span></span>  
  
## <a name="creating-xpathnavigator-objects"></a><span data-ttu-id="3be06-121">Создание объектов XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3be06-121">Creating XPathNavigator Objects</span></span>  

 <span data-ttu-id="3be06-122">После считывания XML-документа в объект <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument>, можно создать объект <xref:System.Xml.XPath.XPathNavigator> для выбора, оценки, навигации и, в некоторых случаях, изменения базовых XML-данных.</span><span class="sxs-lookup"><span data-stu-id="3be06-122">After you have read an XML document into either an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, you can create an <xref:System.Xml.XPath.XPathNavigator> object to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="3be06-123">Как класс <xref:System.Xml.XPath.XPathDocument>, так и <xref:System.Xml.XmlDocument>, наряду с классом <xref:System.Xml.XmlNode>, реализуют интерфейс <xref:System.Xml.XPath.IXPathNavigable> пространства имен <xref:System.Xml.XPath?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3be06-123">Both the <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> classes, in addition to the <xref:System.Xml.XmlNode> class, implement the <xref:System.Xml.XPath.IXPathNavigable> interface of the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="3be06-124">В результате все три класса предоставляют метод <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A>, который возвращает объект <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="3be06-124">As a result, all three classes provide a <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> method that returns an <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a><span data-ttu-id="3be06-125">Изменение XML-документов с помощью класса XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3be06-125">Editing XML Documents using the XPathNavigator Class</span></span>  

 <span data-ttu-id="3be06-126">Кроме выборки, оценки и навигации по XML-данным, класс <xref:System.Xml.XPath.XPathNavigator> в некоторых случаях можно использовать для изменения XML-документа, в зависимости от создавшего его объекта.</span><span class="sxs-lookup"><span data-stu-id="3be06-126">In addition to selecting, evaluating, and navigating XML data, the <xref:System.Xml.XPath.XPathNavigator> class can be used to edit an XML document in some cases, based on the object that created it.</span></span>  
  
 <span data-ttu-id="3be06-127">Класс <xref:System.Xml.XPath.XPathDocument> предназначен только для чтения, а класс <xref:System.Xml.XmlDocument> доступен для редактирования и, в результате, объекты <xref:System.Xml.XPath.XPathNavigator>, созданные из объекта <xref:System.Xml.XPath.XPathDocument>, не могут быть использованы для изменения XML-документа, а созданные из объекта <xref:System.Xml.XmlDocument> - могут.</span><span class="sxs-lookup"><span data-stu-id="3be06-127">The <xref:System.Xml.XPath.XPathDocument> class is read-only while the <xref:System.Xml.XmlDocument> class is editable and as a result, <xref:System.Xml.XPath.XPathNavigator> objects created from an <xref:System.Xml.XPath.XPathDocument> object cannot be used to edit an XML document while those created from an <xref:System.Xml.XmlDocument> object can.</span></span> <span data-ttu-id="3be06-128">Класс <xref:System.Xml.XPath.XPathDocument> должен использоваться только для чтения XML-документа.</span><span class="sxs-lookup"><span data-stu-id="3be06-128">The <xref:System.Xml.XPath.XPathDocument> class should be used to read an XML document only.</span></span> <span data-ttu-id="3be06-129">В случаях, когда нужно изменить XML-документ или требуется доступ к дополнительной функциональности, предоставленной классом <xref:System.Xml.XmlDocument>, например, при обработке событий, нужно использовать класс <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="3be06-129">In cases where you need to edit an XML document, or require access to the additional functionality provided by the <xref:System.Xml.XmlDocument> class, like event handling, the <xref:System.Xml.XmlDocument> class should be used.</span></span>  
  
 <span data-ttu-id="3be06-130">Свойство <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> класса <xref:System.Xml.XPath.XPathNavigator> указывает, может ли объект <xref:System.Xml.XPath.XPathNavigator> изменить XML-данные.</span><span class="sxs-lookup"><span data-stu-id="3be06-130">The <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class specifies if an <xref:System.Xml.XPath.XPathNavigator> object may edit XML data.</span></span>  
  
 <span data-ttu-id="3be06-131">В следующей таблице описаны значения свойства <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> для каждого класса.</span><span class="sxs-lookup"><span data-stu-id="3be06-131">The following table describes the value of the <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property for each class.</span></span>  
  
|<span data-ttu-id="3be06-132">Реализация интерфейса <xref:System.Xml.XPath.IXPathNavigable></span><span class="sxs-lookup"><span data-stu-id="3be06-132"><xref:System.Xml.XPath.IXPathNavigable> Implementation</span></span>|<span data-ttu-id="3be06-133">Значение <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A></span><span class="sxs-lookup"><span data-stu-id="3be06-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Value</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a><span data-ttu-id="3be06-134">См. также</span><span class="sxs-lookup"><span data-stu-id="3be06-134">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="3be06-135">Обработка XML-данных с использованием модели данных XPath</span><span class="sxs-lookup"><span data-stu-id="3be06-135">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="3be06-136">Доступ к XML-данным с помощью класса XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3be06-136">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="3be06-137">Изменение XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3be06-137">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="3be06-138">Проверка по схеме с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3be06-138">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)
