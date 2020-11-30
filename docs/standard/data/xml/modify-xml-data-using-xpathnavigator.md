---
title: Изменение XML-данных с помощью класса XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
ms.openlocfilehash: 10de24d97d15ed4b6de3effa21410fb22054ec68
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714462"
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="442c5-102">Изменение XML-данных с помощью класса XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="442c5-102">Modify XML Data using XPathNavigator</span></span>

<span data-ttu-id="442c5-103">Класс <xref:System.Xml.XPath.XPathNavigator> предоставляет набор методов для изменения узлов и значений в XML-документе.</span><span class="sxs-lookup"><span data-stu-id="442c5-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="442c5-104">Для использования этих методов необходимо сделать редактируемым объект <xref:System.Xml.XPath.XPathNavigator>, то есть установить для свойства <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="442c5-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="442c5-105">Объекты <xref:System.Xml.XPath.XPathNavigator> для правки XML-документа создаются с помощью метода <xref:System.Xml.XmlDocument.CreateNavigator%2A> класса <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="442c5-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="442c5-106">Объекты <xref:System.Xml.XPath.XPathNavigator>, созданные классом <xref:System.Xml.XPath.XPathDocument>, доступны только для чтения, и любая попытка вызова методов редактирования объекта <xref:System.Xml.XPath.XPathNavigator>, созданного объектом <xref:System.Xml.XPath.XPathDocument>, приводит к возникновению исключения <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="442c5-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="442c5-107">Дополнительные сведения о доступных только для чтения и изменяемых объектах <xref:System.Xml.XPath.XPathNavigator> см. в руководстве по [чтению данных XML с помощью XPathDocument и XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="442c5-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="442c5-108">Изменение узлов</span><span class="sxs-lookup"><span data-stu-id="442c5-108">Modifying Nodes</span></span>  

 <span data-ttu-id="442c5-109">Удобнее всего изменять значение узла с помощью методов <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> и <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> класса <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="442c5-109">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="442c5-110">В следующей таблице описывается действие этих методов на различные типы узлов.</span><span class="sxs-lookup"><span data-stu-id="442c5-110">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="442c5-111">Измененные данные</span><span class="sxs-lookup"><span data-stu-id="442c5-111">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="442c5-112">Не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="442c5-112">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="442c5-113">Содержимое элемента.</span><span class="sxs-lookup"><span data-stu-id="442c5-113">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="442c5-114">Значение атрибута.</span><span class="sxs-lookup"><span data-stu-id="442c5-114">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="442c5-115">Текстовое содержимое.</span><span class="sxs-lookup"><span data-stu-id="442c5-115">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="442c5-116">Содержимое, за исключением цели.</span><span class="sxs-lookup"><span data-stu-id="442c5-116">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="442c5-117">Содержимое комментария.</span><span class="sxs-lookup"><span data-stu-id="442c5-117">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="442c5-118">Не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="442c5-118">Not Supported.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="442c5-119">Изменение узлов <xref:System.Xml.XPath.XPathNodeType.Namespace> и узла <xref:System.Xml.XPath.XPathNodeType.Root> не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="442c5-119">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="442c5-120">Класс <xref:System.Xml.XPath.XPathNavigator> предоставляет также набор методов для вставки и удаления узлов.</span><span class="sxs-lookup"><span data-stu-id="442c5-120">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="442c5-121">Дополнительные сведения о вставке и удалении узлов в XML-документах вы найдете в статьях [Вставка XML-данных с помощью XPathNavigator](insert-xml-data-using-xpathnavigator.md) и [Удаление XML-данных с помощью XPathNavigator](remove-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="442c5-121">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="442c5-122">Изменение нетипизированных значений</span><span class="sxs-lookup"><span data-stu-id="442c5-122">Modifying Untyped Values</span></span>  

 <span data-ttu-id="442c5-123">Метод <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> просто вставляет нетипизированное значение `string`, переданное в качестве параметра, как значение узла, на котором в данный момент позиционируется объект <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="442c5-123">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="442c5-124">Значение вставляется без какого-либо типа и без проверки допустимости нового значения в соответствии с типом узла, если доступны сведения о схеме.</span><span class="sxs-lookup"><span data-stu-id="442c5-124">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="442c5-125">В следующем примере метод <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> используется для обновления всех элементов `price` в файле `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="442c5-125">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="442c5-126">В примере в качестве входных данных используется файл `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="442c5-126">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="442c5-127">Изменение типизированных значений</span><span class="sxs-lookup"><span data-stu-id="442c5-127">Modifying Typed Values</span></span>  

 <span data-ttu-id="442c5-128">Когда тип узла является простым типом XML-схемы W3C, новое значение, вставленное методом <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>, проверяется по особенностям простого типа, прежде чем будет установлено значение.</span><span class="sxs-lookup"><span data-stu-id="442c5-128">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="442c5-129">Если новое значение недопустимо в соответствии с типом узла (например, при установке значения `-1` для элемента с типом `xs:positiveInteger`), возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="442c5-129">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="442c5-130">В следующем примере предпринимается попытка изменить значение элемента `price` первого элемента `book` в файле `contosoBooks.xml` на <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="442c5-130">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="442c5-131">Так как в файлах `price` тип элемента `xs:decimal` по XML-схеме определен как `contosoBooks.xsd`, возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="442c5-131">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 <span data-ttu-id="442c5-132">В примере в качестве входных данных используется файл `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="442c5-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="442c5-133">В примере также в качестве входных данных используется `contosoBooks.xsd`.</span><span class="sxs-lookup"><span data-stu-id="442c5-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="442c5-134">Последствия изменения строго типизированных XML-данных</span><span class="sxs-lookup"><span data-stu-id="442c5-134">The Effects of Editing Strongly Typed XML Data</span></span>  

 <span data-ttu-id="442c5-135">Класс <xref:System.Xml.XPath.XPathNavigator> использует схему XML W3C как основу для описания строго типизированного XML.</span><span class="sxs-lookup"><span data-stu-id="442c5-135">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly typed XML.</span></span> <span data-ttu-id="442c5-136">Элементы и атрибуты могут сопровождаться информацией о типе, создаваемой по результатам проверки на основе документа схемы XML W3C.</span><span class="sxs-lookup"><span data-stu-id="442c5-136">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="442c5-137">Элементы, содержащие другие элементы или атрибуты, называются сложными типами, а имеющие только текстовое содержимое - простыми типами.</span><span class="sxs-lookup"><span data-stu-id="442c5-137">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="442c5-138">Атрибуты могут иметь только простой тип.</span><span class="sxs-lookup"><span data-stu-id="442c5-138">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="442c5-139">Элемент или атрибут считается соответствующим схеме, если он соответствует всем правилам, специфичным для определения его типа.</span><span class="sxs-lookup"><span data-stu-id="442c5-139">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="442c5-140">Элемент, относящийся к простому типу `xs:int`, чтобы соответствовать схеме, должен содержать числовое значение в диапазоне от -2147483648 до 2147483647.</span><span class="sxs-lookup"><span data-stu-id="442c5-140">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="442c5-141">Для сложных типов соответствие элемента схеме определяется на основе соответствия схеме его дочерних элементов и атрибутов.</span><span class="sxs-lookup"><span data-stu-id="442c5-141">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="442c5-142">Таким образом, если элемент соответствует определению своего сложного типа, все его дочерние элементы и атрибуты соответствуют определениям своих типов.</span><span class="sxs-lookup"><span data-stu-id="442c5-142">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="442c5-143">Аналогично, если хотя бы один из дочерних элементов или атрибутов элемента не соответствует определению своего типа или факт его соответствия не установлен, весь элемент также не соответствует или его соответствие не установлено.</span><span class="sxs-lookup"><span data-stu-id="442c5-143">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="442c5-144">Поскольку соответствие элемента зависит от соответствия его дочерних элементов и атрибутов, их изменения могут повлиять на соответствие элемента, который ранее соответствовал.</span><span class="sxs-lookup"><span data-stu-id="442c5-144">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="442c5-145">Конкретнее, если дочерние элементы или атрибуты элемента добавляются, изменяются или удаляются, элемент переходит в состояние неустановленного соответствия.</span><span class="sxs-lookup"><span data-stu-id="442c5-145">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="442c5-146">Чтобы отразить этот факт, свойство <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> свойства <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> элемента получает значение <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span><span class="sxs-lookup"><span data-stu-id="442c5-146">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="442c5-147">Затем этот эффект рекурсивно распространяется вверх по XML-документу, поскольку соответствие родительского элемента данного элемента (и его родительского элемента и т. п.) также приходит в неустановленное состояние.</span><span class="sxs-lookup"><span data-stu-id="442c5-147">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="442c5-148">Дополнительные сведения о проверке схемы и классе <xref:System.Xml.XPath.XPathNavigator> см. в статье [Проверка по схеме с помощью XPathNavigator](schema-validation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="442c5-148">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="442c5-149">Изменение атрибутов</span><span class="sxs-lookup"><span data-stu-id="442c5-149">Modifying Attributes</span></span>  

 <span data-ttu-id="442c5-150">Для изменения узлов типизированных и нетипизированных атрибутов, а также других типов узлов, перечисленных в разделе «Изменение узлов», применяются методы <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> и <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="442c5-150">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="442c5-151">В следующем примере изменяется значение атрибута `genre` первого элемента `book` в файле `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="442c5-151">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="442c5-152">Дополнительные сведения о методах <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> и <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> см. в разделах «Изменение нетипизированных значений» и «Изменение типизированных значений».</span><span class="sxs-lookup"><span data-stu-id="442c5-152">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="442c5-153">Свойства InnerXml и OuterXml</span><span class="sxs-lookup"><span data-stu-id="442c5-153">InnerXml and OuterXml Properties</span></span>  

 <span data-ttu-id="442c5-154">Свойства <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> и <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> класса <xref:System.Xml.XPath.XPathNavigator> изменяют XML-разметку узлов, на которых в данный момент позиционируется объект <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="442c5-154">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="442c5-155">Свойство <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> изменяет XML-разметку дочерних узлов, на которых в данный момент позиционируется объект <xref:System.Xml.XPath.XPathNavigator>, разобранный содержимым заданной XML-строки (`string`).</span><span class="sxs-lookup"><span data-stu-id="442c5-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="442c5-156">Подобным образом свойство <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> изменяет XML-разметку дочерних узлов, на которых в данный момент позиционируется объект <xref:System.Xml.XPath.XPathNavigator>, так же как и самого текущего узла.</span><span class="sxs-lookup"><span data-stu-id="442c5-156">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="442c5-157">В следующем примере свойство <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> используется для изменения значения элемента `price` и вставки нового атрибута `discount` в первый элемент `book` в файле `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="442c5-157">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="442c5-158">В примере в качестве входных данных используется файл `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="442c5-158">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="442c5-159">Изменение узлов пространств имен</span><span class="sxs-lookup"><span data-stu-id="442c5-159">Modifying Namespace Nodes</span></span>  

 <span data-ttu-id="442c5-160">В модели DOM декларации пространств имен обрабатываются как обычные атрибуты, которые можно вставлять, изменять и удалять.</span><span class="sxs-lookup"><span data-stu-id="442c5-160">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="442c5-161">Класс <xref:System.Xml.XPath.XPathNavigator> не допускает подобных операций на узлах пространств имен, поскольку изменение значения узла пространства имен может изменить идентификатор элементов и атрибутов в области действия узла пространства имен, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="442c5-161">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="442c5-162">Если изменить приведенный выше пример следующим образом, это эквивалентно переименованию всех элементов документа, поскольку изменится значение URI-кода пространства имен всех элементов.</span><span class="sxs-lookup"><span data-stu-id="442c5-162">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="442c5-163">Класс <xref:System.Xml.XPath.XPathNavigator> разрешает вставлять узлы пространств имен, не конфликтующие с декларациями пространств имен в данной области действия.</span><span class="sxs-lookup"><span data-stu-id="442c5-163">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="442c5-164">В данном случае декларации пространств имен не производятся в нижележащих областях действия XML-документа и не вызывают переименования, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="442c5-164">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="442c5-165">Если изменить приведенный выше пример следующим образом, декларации пространств имен корректно распространяются по всему XML-документу ниже областей действия других деклараций пространств имен.</span><span class="sxs-lookup"><span data-stu-id="442c5-165">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/" />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="442c5-166">В приведенном выше примере атрибут `a:parent-id` вставляется в элемент `parent` в пространстве имен `http://www.contoso.com/parent-id`.</span><span class="sxs-lookup"><span data-stu-id="442c5-166">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="442c5-167">Метод <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> используется для вставки атрибута для текущего элемента `parent`.</span><span class="sxs-lookup"><span data-stu-id="442c5-167">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="442c5-168">Декларация пространства имен `http://www.contoso.com` автоматически вставляется классом <xref:System.Xml.XPath.XPathNavigator> для сохранения согласованности всего остального XML-документа.</span><span class="sxs-lookup"><span data-stu-id="442c5-168">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="442c5-169">Изменение узлов ссылок на сущности</span><span class="sxs-lookup"><span data-stu-id="442c5-169">Modifying Entity Reference Nodes</span></span>  

 <span data-ttu-id="442c5-170">Ссылки на сущности в объекте <xref:System.Xml.XmlDocument> служат только для чтения; их нельзя изменять ни с помощью класса <xref:System.Xml.XPath.XPathNavigator>, ни с помощью класса <xref:System.Xml.XmlNode>.</span><span class="sxs-lookup"><span data-stu-id="442c5-170">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="442c5-171">Любые попытки изменения узла ссылки на сущность приводят к исключению <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="442c5-171">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="442c5-172">Изменение узлов xsi:nil</span><span class="sxs-lookup"><span data-stu-id="442c5-172">Modifying xsi:nil Nodes</span></span>  

 <span data-ttu-id="442c5-173">Рекомендации схемы XML W3C содержат понятие обнуляемого (nillable) элемента.</span><span class="sxs-lookup"><span data-stu-id="442c5-173">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="442c5-174">Обнуляемый элемент может не иметь никакого содержимого и все же быть допустимым.</span><span class="sxs-lookup"><span data-stu-id="442c5-174">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="442c5-175">Понятие обнуляемого элемента аналогично понятию объекта со значением `null`.</span><span class="sxs-lookup"><span data-stu-id="442c5-175">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="442c5-176">Основное различие заключается в том, что объект со значением `null` недоступен ни для каких взаимодействий, в то время как элемент `xsi:nil` все же обладает доступными свойствами (например, атрибутами), но не имеет содержимого (дочерних элементов или текста).</span><span class="sxs-lookup"><span data-stu-id="442c5-176">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="442c5-177">Существование атрибута `xsi:nil` со значением `true` у элемента в XML-документе используется для обозначения отсутствия содержимого у данного элемента.</span><span class="sxs-lookup"><span data-stu-id="442c5-177">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="442c5-178">Если объект <xref:System.Xml.XPath.XPathNavigator> используется для добавления содержимого к допустимому элементу с атрибутом `xsi:nil` со значением `true`, для его атрибута `xsi:nil` будет установлено значение `false`.</span><span class="sxs-lookup"><span data-stu-id="442c5-178">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="442c5-179">Если содержимое элемента с атрибутом `xsi:nil`, значение которого равно `false`, удалить, значение атрибута не будет изменено на `true`.</span><span class="sxs-lookup"><span data-stu-id="442c5-179">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="442c5-180">Сохранение XML-документа</span><span class="sxs-lookup"><span data-stu-id="442c5-180">Saving an XML Document</span></span>  

 <span data-ttu-id="442c5-181">Сохранение изменений, внесенных в объект <xref:System.Xml.XmlDocument> с помощью описанных в данном разделе методов, выполняется с помощью методов класса <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="442c5-181">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="442c5-182">Дополнительные сведения о сохранении изменений, внесенных в объект <xref:System.Xml.XmlDocument>, см. в руководстве по [созданию и сохранению документов](saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="442c5-182">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="442c5-183">См. также</span><span class="sxs-lookup"><span data-stu-id="442c5-183">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="442c5-184">Обработка XML-данных с использованием модели данных XPath</span><span class="sxs-lookup"><span data-stu-id="442c5-184">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="442c5-185">Вставка XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="442c5-185">Insert XML Data using XPathNavigator</span></span>](insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="442c5-186">Удаление XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="442c5-186">Remove XML Data using XPathNavigator</span></span>](remove-xml-data-using-xpathnavigator.md)
