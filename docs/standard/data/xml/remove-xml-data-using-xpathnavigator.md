---
title: Удаление XML-данных с помощью XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
ms.openlocfilehash: 265275e3b200ec7bf38df997ace622f2056ad66f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697627"
---
# <a name="remove-xml-data-using-xpathnavigator"></a><span data-ttu-id="29d6f-102">Удаление XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="29d6f-102">Remove XML Data using XPathNavigator</span></span>

<span data-ttu-id="29d6f-103">Класс <xref:System.Xml.XPath.XPathNavigator> располагает набором методов, используемых для удаления узлов и значений из XML-документа.</span><span class="sxs-lookup"><span data-stu-id="29d6f-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="29d6f-104">Для использования этих методов необходимо сделать редактируемым объект <xref:System.Xml.XPath.XPathNavigator>, то есть установить для свойства <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="29d6f-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="29d6f-105">Объекты <xref:System.Xml.XPath.XPathNavigator> для правки XML-документа создаются с помощью метода <xref:System.Xml.XmlDocument.CreateNavigator%2A> класса <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="29d6f-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="29d6f-106">Объекты <xref:System.Xml.XPath.XPathNavigator>, созданные классом <xref:System.Xml.XPath.XPathDocument>, доступны только для чтения, и любая попытка вызова методов редактирования объекта <xref:System.Xml.XPath.XPathNavigator>, созданного объектом <xref:System.Xml.XPath.XPathDocument>, приводит к возникновению исключения <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="29d6f-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="29d6f-107">Дополнительные сведения о доступных только для чтения и изменяемых объектах <xref:System.Xml.XPath.XPathNavigator> см. в руководстве по [чтению данных XML с помощью XPathDocument и XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="29d6f-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="removing-nodes"></a><span data-ttu-id="29d6f-108">Удаление узлов</span><span class="sxs-lookup"><span data-stu-id="29d6f-108">Removing Nodes</span></span>  

 <span data-ttu-id="29d6f-109">Класс <xref:System.Xml.XPath.XPathNavigator> представляет метод <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> для удаления узлов из XML-документа.</span><span class="sxs-lookup"><span data-stu-id="29d6f-109">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to remove nodes from an XML document.</span></span>  
  
### <a name="removing-a-node"></a><span data-ttu-id="29d6f-110">Удаление узла</span><span class="sxs-lookup"><span data-stu-id="29d6f-110">Removing a Node</span></span>  

 <span data-ttu-id="29d6f-111">Класс <xref:System.Xml.XPath.XPathNavigator> представляет метод <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> для удаления узлов текущего узла, на котором в данное время позиционирован объект <xref:System.Xml.XPath.XPathNavigator>, из XML-документа.</span><span class="sxs-lookup"><span data-stu-id="29d6f-111">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to delete the current node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on from an XML document.</span></span>  
  
 <span data-ttu-id="29d6f-112">Узел, удаленный с помощью метода <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>, более недоступен из корня объекта <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="29d6f-112">After a node has been deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method, it is no longer reachable from the root of the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="29d6f-113">После удаления узла объект <xref:System.Xml.XPath.XPathNavigator> позиционируется на родительском узле удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="29d6f-113">After a node has been deleted, the <xref:System.Xml.XPath.XPathNavigator> is positioned on the parent node of the deleted node.</span></span>  
  
 <span data-ttu-id="29d6f-114">Операция удаления не влияет на позицию любого объекта <xref:System.Xml.XPath.XPathNavigator>, позиционированного на удаленном узле.</span><span class="sxs-lookup"><span data-stu-id="29d6f-114">A delete operation doesn't affect the position of any <xref:System.Xml.XPath.XPathNavigator> object positioned on the deleted node.</span></span> <span data-ttu-id="29d6f-115">Эти объекты <xref:System.Xml.XPath.XPathNavigator> допустимы в том отношении, что могут перемещаться внутри удаленного поддерева, но не могут быть перенесены в главный узел дерева с помощью обычных методов перемещения по набору узлов класса <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="29d6f-115">These <xref:System.Xml.XPath.XPathNavigator> objects are valid in the sense that they can move within the deleted subtree, but cannot be moved to the main node tree using the regular node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29d6f-116">Метод <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> класса <xref:System.Xml.XPath.XPathNavigator> может быть использован для перемещения этих объектов <xref:System.Xml.XPath.XPathNavigator> назад в главный узел дерева или из главного узла дерева в удаленное поддерево.</span><span class="sxs-lookup"><span data-stu-id="29d6f-116">The <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class can be used to move these <xref:System.Xml.XPath.XPathNavigator> objects back into the main node tree, or from the main node tree to the deleted subtree.</span></span>  
  
 <span data-ttu-id="29d6f-117">В следующем примере элемент `price` первого элемента `book` файла `contosoBooks.xml` удаляется с помощью метода <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="29d6f-117">In the following example, the `price` element of the first `book` element of the `contosoBooks.xml` file is deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span> <span data-ttu-id="29d6f-118">Позиция объекта <xref:System.Xml.XPath.XPathNavigator> после удаления элемента `price` - на родительском элементе `book`.</span><span class="sxs-lookup"><span data-stu-id="29d6f-118">The position of the <xref:System.Xml.XPath.XPathNavigator> object after the `price` element is deleted is on the parent `book` element.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="29d6f-119">В примере в качестве входных данных используется файл `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="29d6f-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a><span data-ttu-id="29d6f-120">Удаление узла атрибута</span><span class="sxs-lookup"><span data-stu-id="29d6f-120">Removing an Attribute Node</span></span>  

 <span data-ttu-id="29d6f-121">Узлы атрибута удаляются из XML-документа с помощью метода <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="29d6f-121">Attribute nodes are removed from an XML document using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span>  
  
 <span data-ttu-id="29d6f-122">Удаленный узел атрибута более недоступен из корневого узла объекта <xref:System.Xml.XmlDocument>, и объект <xref:System.Xml.XPath.XPathNavigator> позиционируется на родительском элементе.</span><span class="sxs-lookup"><span data-stu-id="29d6f-122">After an attribute node has been deleted, it is no longer reachable from the root node of an <xref:System.Xml.XmlDocument> object and the <xref:System.Xml.XPath.XPathNavigator> object is positioned on the parent element.</span></span>  
  
#### <a name="default-attributes"></a><span data-ttu-id="29d6f-123">Атрибуты по умолчанию</span><span class="sxs-lookup"><span data-stu-id="29d6f-123">Default Attributes</span></span>  

 <span data-ttu-id="29d6f-124">Независимо от метода удаления атрибутов, существуют специальные ограничения на удаление атрибутов, определенных как атрибуты по умолчанию в определении DTD или схеме XML для XML-документа.</span><span class="sxs-lookup"><span data-stu-id="29d6f-124">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the DTD or XML Schema for the XML document.</span></span> <span data-ttu-id="29d6f-125">Атрибуты по умолчанию нельзя удалить, если не удален элемент, к которому они принадлежат.</span><span class="sxs-lookup"><span data-stu-id="29d6f-125">Default attributes cannot be removed unless the element they belong to is also removed.</span></span> <span data-ttu-id="29d6f-126">Атрибуты по умолчанию всегда присутствуют для элементов с объявленными атрибутами по умолчанию, и в результате удаление атрибута по умолчанию приводит к вставке в элемент атрибута замены, инициируемого с декларированным значением по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="29d6f-126">Default attributes are always present for elements that have default attributes declared, and as a result, deleting a default attribute results in a replacement attribute being inserted into the element and initialized to the default value that was declared.</span></span>  
  
## <a name="removing-values"></a><span data-ttu-id="29d6f-127">Удаление значений</span><span class="sxs-lookup"><span data-stu-id="29d6f-127">Removing Values</span></span>  

 <span data-ttu-id="29d6f-128">Класс <xref:System.Xml.XPath.XPathNavigator> представляет методы <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> и <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> для удаления узлов нетипизированных и типизированных значений из XML-документа.</span><span class="sxs-lookup"><span data-stu-id="29d6f-128">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to remove untyped and typed values from an XML document.</span></span>  
  
### <a name="removing-untyped-values"></a><span data-ttu-id="29d6f-129">Удаление нетипизированных значений</span><span class="sxs-lookup"><span data-stu-id="29d6f-129">Removing Untyped Values</span></span>  

 <span data-ttu-id="29d6f-130">Метод <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> просто вставляет нетипизированное значение `string`, переданное в качестве параметра, как значение узла, на котором в данный момент позиционируется объект <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="29d6f-130">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="29d6f-131">Передача пустой строки в метод <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> удаляет значение текущего узла.</span><span class="sxs-lookup"><span data-stu-id="29d6f-131">Passing an empty string to the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method removes the value of the current node.</span></span>  
  
 <span data-ttu-id="29d6f-132">В следующем примере значение элемента `price` первого элемента `book` в файле `contosoBooks.xml` удаляется с помощью метода <xref:System.Xml.XPath.XPathNavigator.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="29d6f-132">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
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
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="29d6f-133">В примере в качестве входных данных используется файл `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="29d6f-133">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a><span data-ttu-id="29d6f-134">Удаление типизированных значений</span><span class="sxs-lookup"><span data-stu-id="29d6f-134">Removing Typed Values</span></span>  

 <span data-ttu-id="29d6f-135">Когда тип узла является простым типом XML-схемы W3C, новое значение, вставленное методом <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>, проверяется по особенностям простого типа, прежде чем будет установлено значение.</span><span class="sxs-lookup"><span data-stu-id="29d6f-135">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="29d6f-136">Если новое значение недопустимо в соответствии с типом узла (например, при установке значения `-1` для элемента с типом `xs:positiveInteger`), возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="29d6f-136">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span> <span data-ttu-id="29d6f-137">Методу <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> также невозможно передать значение `null` в качестве параметра.</span><span class="sxs-lookup"><span data-stu-id="29d6f-137">The <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method also cannot be passed `null` as a parameter.</span></span> <span data-ttu-id="29d6f-138">В результате удаления значение типизированного узла должно соответствовать типу схемы узла.</span><span class="sxs-lookup"><span data-stu-id="29d6f-138">As a result removing the value of a typed node must comply with the schema type of the node.</span></span>  
  
 <span data-ttu-id="29d6f-139">В следующем примере значение элемента `price` первого элемента `book` в файле `contosoBooks.xml` удаляется с помощью метода <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> путем присвоения значения `0`.</span><span class="sxs-lookup"><span data-stu-id="29d6f-139">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method by setting the value to `0`.</span></span> <span data-ttu-id="29d6f-140">Значение узла не удаляется, но цена книги удалена в соответствии с ее типом данных `xs:decimal`.</span><span class="sxs-lookup"><span data-stu-id="29d6f-140">The value of the node is not removed, but the price of the book has been removed according to its data type of `xs:decimal`.</span></span>  
  
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
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
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
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a><span data-ttu-id="29d6f-141">Узлы пространства имен</span><span class="sxs-lookup"><span data-stu-id="29d6f-141">Namespace Nodes</span></span>  

 <span data-ttu-id="29d6f-142">Узлы пространства имен нельзя удалить из объекта <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="29d6f-142">Namespace nodes cannot be deleted from an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="29d6f-143">Попытки удалить узлы пространства имен с помощью метода <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> приводят к исключению.</span><span class="sxs-lookup"><span data-stu-id="29d6f-143">Attempts to delete namespace nodes using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method results in an exception.</span></span>  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="29d6f-144">Свойства InnerXml и OuterXml</span><span class="sxs-lookup"><span data-stu-id="29d6f-144">The InnerXml and OuterXml Properties</span></span>  

 <span data-ttu-id="29d6f-145">Свойства <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> и <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> класса <xref:System.Xml.XPath.XPathNavigator> изменяют XML-разметку узлов, на которых в данный момент позиционируется объект <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="29d6f-145">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="29d6f-146">Свойство <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> изменяет XML-разметку дочерних узлов, на которых в данный момент позиционируется объект <xref:System.Xml.XPath.XPathNavigator>, разобранный содержимым заданной XML-строки (`string`).</span><span class="sxs-lookup"><span data-stu-id="29d6f-146">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="29d6f-147">Подобным образом свойство <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> изменяет XML-разметку дочерних узлов, на которых в данный момент позиционируется объект <xref:System.Xml.XPath.XPathNavigator>, так же как и самого текущего узла.</span><span class="sxs-lookup"><span data-stu-id="29d6f-147">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="29d6f-148">В дополнение к методам, описанным в этом разделе, свойства <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> и <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> могут использоваться, чтобы удалить узлы и значения из XML-документа.</span><span class="sxs-lookup"><span data-stu-id="29d6f-148">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="29d6f-149">Дополнительные сведения об использовании свойств <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> и [ для изменения узлов см. в <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>руководстве по изменению данных XML с помощью XPathNavigator](modify-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="29d6f-149">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to modify nodes, see the [Modify XML Data using XPathNavigator](modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="29d6f-150">Сохранение XML-документа</span><span class="sxs-lookup"><span data-stu-id="29d6f-150">Saving an XML Document</span></span>  

 <span data-ttu-id="29d6f-151">Сохранение изменений, внесенных в объект <xref:System.Xml.XmlDocument> в результате выполнения описанных в данном разделе методов, выполняется с помощью методов класса <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="29d6f-151">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="29d6f-152">Дополнительные сведения о сохранении изменений, внесенных в объект <xref:System.Xml.XmlDocument>, см. в руководстве по [созданию и сохранению документов](saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="29d6f-152">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d6f-153">См. также</span><span class="sxs-lookup"><span data-stu-id="29d6f-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="29d6f-154">Обработка XML-данных с использованием модели данных XPath</span><span class="sxs-lookup"><span data-stu-id="29d6f-154">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="29d6f-155">Вставка XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="29d6f-155">Insert XML Data using XPathNavigator</span></span>](insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="29d6f-156">Изменение XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="29d6f-156">Modify XML Data using XPathNavigator</span></span>](modify-xml-data-using-xpathnavigator.md)
