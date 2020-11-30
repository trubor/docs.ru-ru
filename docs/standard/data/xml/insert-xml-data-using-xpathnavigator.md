---
title: Вставка XML-данных с помощью XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
ms.openlocfilehash: 50e5b363a35eb3f11d7eb26bb34c53910a59201b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733416"
---
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="9ea94-102">Вставка XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="9ea94-102">Insert XML Data using XPathNavigator</span></span>

<span data-ttu-id="9ea94-103">Класс <xref:System.Xml.XPath.XPathNavigator> предоставляет набор методов для вставки в XML-документ одноуровневых узлов, дочерних узлов и узлов атрибутов.</span><span class="sxs-lookup"><span data-stu-id="9ea94-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="9ea94-104">Для использования этих методов необходимо сделать редактируемым объект <xref:System.Xml.XPath.XPathNavigator>, то есть установить для свойства <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="9ea94-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="9ea94-105">Объекты <xref:System.Xml.XPath.XPathNavigator> для правки XML-документа создаются с помощью метода <xref:System.Xml.XmlDocument.CreateNavigator%2A> класса <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="9ea94-106">Объекты <xref:System.Xml.XPath.XPathNavigator>, созданные классом <xref:System.Xml.XPath.XPathDocument>, доступны только для чтения, и любая попытка вызова методов редактирования объекта <xref:System.Xml.XPath.XPathNavigator>, созданного объектом <xref:System.Xml.XPath.XPathDocument>, приводит к возникновению исключения <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="9ea94-107">Дополнительные сведения о доступных только для чтения и изменяемых объектах <xref:System.Xml.XPath.XPathNavigator> см. в руководстве по [чтению данных XML с помощью XPathDocument и XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="9ea94-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="9ea94-108">Вставка узлов</span><span class="sxs-lookup"><span data-stu-id="9ea94-108">Inserting Nodes</span></span>  

 <span data-ttu-id="9ea94-109">Класс <xref:System.Xml.XPath.XPathNavigator> предоставляет методы для вставки в XML-документ одноуровневых узлов, дочерних узлов и узлов атрибутов.</span><span class="sxs-lookup"><span data-stu-id="9ea94-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="9ea94-110">Эти методы позволяют вставить узлы и атрибуты в разные места относительно текущего положения объекта <xref:System.Xml.XPath.XPathNavigator> и описываются в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="9ea94-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="9ea94-111">Вставка одноуровневых узлов</span><span class="sxs-lookup"><span data-stu-id="9ea94-111">Inserting Sibling Nodes</span></span>  

 <span data-ttu-id="9ea94-112">Класс <xref:System.Xml.XPath.XPathNavigator> предоставляет следующие методы для вставки одноуровневых узлов.</span><span class="sxs-lookup"><span data-stu-id="9ea94-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="9ea94-113">Эти методы вставляют одноуровневые узлы до и после узла, на котором располагается объект <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="9ea94-114">Методы <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> и <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> перегружаются и принимают в качестве параметров объект `string`, <xref:System.Xml.XmlReader> или объект <xref:System.Xml.XPath.XPathNavigator>, содержащий одноуровневый узел.</span><span class="sxs-lookup"><span data-stu-id="9ea94-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="9ea94-115">Оба метода также возвращают объект <xref:System.Xml.XmlWriter>, используемый для вставки одноуровневых узлов.</span><span class="sxs-lookup"><span data-stu-id="9ea94-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="9ea94-116">Методы <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> и <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> вставляют один одноуровневый узел до и после узла, на котором располагается объект <xref:System.Xml.XPath.XPathNavigator>, используя префикс пространства имен, локальное имя, URI-код пространства имен и значение, указанное в параметрах.</span><span class="sxs-lookup"><span data-stu-id="9ea94-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="9ea94-117">В следующем примере новый элемент `pages` вставляется перед дочерним элементом `price` первого элемента `book` в файле `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="9ea94-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="9ea94-118">В примере в качестве входных данных используется файл `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="9ea94-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="9ea94-119">Дополнительные сведения о методах <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> и <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> см. в справочной документации по классу <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="9ea94-120">Вставка дочерних узлов</span><span class="sxs-lookup"><span data-stu-id="9ea94-120">Inserting Child Nodes</span></span>  

 <span data-ttu-id="9ea94-121">Класс <xref:System.Xml.XPath.XPathNavigator> предоставляет следующие методы для вставки дочерних узлов.</span><span class="sxs-lookup"><span data-stu-id="9ea94-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="9ea94-122">Эти методы вставляют дочерние узлы в конец и в начало списка дочерних узлов того узла, на котором в текущий момент располагается объект <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="9ea94-123">Подобно методам из раздела «Вставка одноуровневых узлов», методы <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> и <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> принимают в качестве параметров объект `string`, <xref:System.Xml.XmlReader> или объект <xref:System.Xml.XPath.XPathNavigator>, содержащий дочерний узел.</span><span class="sxs-lookup"><span data-stu-id="9ea94-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="9ea94-124">Оба метода также возвращают объект <xref:System.Xml.XmlWriter>, используемый для вставки дочерних узлов.</span><span class="sxs-lookup"><span data-stu-id="9ea94-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="9ea94-125">Также, подобно методам из раздела «Вставка одноуровневых узлов», методы <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> и <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> вставляют один дочерний узел в начало и конец списка дочерних узлов узла, на котором в текущий момент располагается объект <xref:System.Xml.XPath.XPathNavigator>, используя в качестве параметров префикс пространства имен, локальное имя, URI-код пространства имен и значение, указанное в параметрах.</span><span class="sxs-lookup"><span data-stu-id="9ea94-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="9ea94-126">В следующем примере новый элемент `pages` добавляется в список дочерних элементов первого элемента `book` в файле `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="9ea94-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="9ea94-127">В примере в качестве входных данных используется файл `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="9ea94-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="9ea94-128">Дополнительные сведения о методах <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> и <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> см. в справочной документации по классу <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="9ea94-129">Вставка узлов атрибутов</span><span class="sxs-lookup"><span data-stu-id="9ea94-129">Inserting Attribute Nodes</span></span>  

 <span data-ttu-id="9ea94-130">Класс <xref:System.Xml.XPath.XPathNavigator> предоставляет следующие методы для вставки узлов атрибутов.</span><span class="sxs-lookup"><span data-stu-id="9ea94-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="9ea94-131">Эти методы вставляют узлы атрибутов в узел элемента, на котором в текущий момент находится объект <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="9ea94-132">Метод <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> создает узел атрибута для элемента узла, на котором в текущий момент располагается объект <xref:System.Xml.XPath.XPathNavigator>, используя в качестве параметров префикс пространства имен, локальное имя, URI-код пространства имен и указанное значение.</span><span class="sxs-lookup"><span data-stu-id="9ea94-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="9ea94-133">Метод <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> возвращает объект <xref:System.Xml.XmlWriter>, используемый для вставки узлов атрибутов.</span><span class="sxs-lookup"><span data-stu-id="9ea94-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="9ea94-134">В следующем примере создаются новые атрибуты `discount` и `currency` для дочернего элемента `price` первого элемента `book` в файле `contosoBooks.xml` с использованием объекта <xref:System.Xml.XmlWriter>, возвращаемого методом <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="9ea94-135">В примере в качестве входных данных используется файл `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="9ea94-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="9ea94-136">Дополнительные сведения о методах <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> и <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> см. в справочной документации по классу <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="9ea94-137">Копирование узлов</span><span class="sxs-lookup"><span data-stu-id="9ea94-137">Copying Nodes</span></span>  

 <span data-ttu-id="9ea94-138">В некоторых случаях необходимо заполнить XML-документ содержимым другого XML-документа.</span><span class="sxs-lookup"><span data-stu-id="9ea94-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="9ea94-139">Оба класса, <xref:System.Xml.XPath.XPathNavigator> и <xref:System.Xml.XmlWriter>, могут копировать узлы в объект <xref:System.Xml.XmlDocument> из существующего объекта <xref:System.Xml.XmlReader> или объекта <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="9ea94-140">Методы <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> и <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> класса <xref:System.Xml.XPath.XPathNavigator> имеют перегруженные варианты, которые могут принимать в качестве параметра объект <xref:System.Xml.XPath.XPathNavigator> или объект <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="9ea94-141">Метод <xref:System.Xml.XmlWriter.WriteNode%2A> класса <xref:System.Xml.XmlWriter> имеет перегруженные варианты, которые могут принимать объекты <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader> или <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="9ea94-142">В следующем примере выполняется копирование всех элементов `book` из одного документа в другой.</span><span class="sxs-lookup"><span data-stu-id="9ea94-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
  
Dim newBooks As XPathDocument = New XPathDocument("newBooks.xml")  
Dim newBooksNavigator As XPathNavigator = newBooks.CreateNavigator()  
  
Dim nav As XPathNavigator  
For Each nav in newBooksNavigator.SelectDescendants("book", "", false)  
    navigator.AppendChild(nav)  
Next  
  
document.Save("newBooks.xml");  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
  
XPathDocument newBooks = new XPathDocument("newBooks.xml");  
XPathNavigator newBooksNavigator = newBooks.CreateNavigator();  
  
foreach (XPathNavigator nav in newBooksNavigator.SelectDescendants("book", "", false))  
{  
    navigator.AppendChild(nav);  
}  
  
document.Save("newBooks.xml");  
```  
  
## <a name="inserting-values"></a><span data-ttu-id="9ea94-143">Вставка значений</span><span class="sxs-lookup"><span data-stu-id="9ea94-143">Inserting Values</span></span>  

 <span data-ttu-id="9ea94-144">Класс <xref:System.Xml.XPath.XPathNavigator> предоставляет методы <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> и <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>, чтобы вставить значения для узла в объект <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="9ea94-145">Вставка нетипизированных значений</span><span class="sxs-lookup"><span data-stu-id="9ea94-145">Inserting Untyped Values</span></span>  

 <span data-ttu-id="9ea94-146">Метод <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> просто вставляет нетипизированное значение `string`, переданное в качестве параметра, как значение узла, на котором в данный момент позиционируется объект <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="9ea94-147">Значение вставляется без какого-либо типа и без проверки допустимости нового значения в соответствии с типом узла, если доступны сведения о схеме.</span><span class="sxs-lookup"><span data-stu-id="9ea94-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="9ea94-148">В следующем примере метод <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> используется для обновления всех элементов `price` в файле `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="9ea94-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="9ea94-149">В примере в качестве входных данных используется файл `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="9ea94-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="9ea94-150">Вставка типизированных значений</span><span class="sxs-lookup"><span data-stu-id="9ea94-150">Inserting Typed Values</span></span>  

 <span data-ttu-id="9ea94-151">Когда тип узла является простым типом XML-схемы W3C, новое значение, вставленное методом <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>, проверяется по особенностям простого типа, прежде чем будет установлено значение.</span><span class="sxs-lookup"><span data-stu-id="9ea94-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="9ea94-152">Если новое значение недопустимо в соответствии с типом узла (например, при установке значения `-1` для элемента с типом `xs:positiveInteger`), возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="9ea94-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="9ea94-153">В следующем примере предпринимается попытка изменить значение элемента `price` первого элемента `book` в файле `contosoBooks.xml` на <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="9ea94-154">Так как в файлах `price` тип элемента `xs:decimal` по XML-схеме определен как `contosoBooks.xsd`, возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="9ea94-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="9ea94-155">В примере в качестве входных данных используется файл `contosoBooks.xml`.</span><span class="sxs-lookup"><span data-stu-id="9ea94-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="9ea94-156">В примере также в качестве входных данных используется `contosoBooks.xsd`.</span><span class="sxs-lookup"><span data-stu-id="9ea94-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="9ea94-157">Свойства InnerXml и OuterXml</span><span class="sxs-lookup"><span data-stu-id="9ea94-157">The InnerXml and OuterXml Properties</span></span>  

 <span data-ttu-id="9ea94-158">Свойства <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> и <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> класса <xref:System.Xml.XPath.XPathNavigator> изменяют XML-разметку узлов, на которых в данный момент позиционируется объект <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="9ea94-159">Свойство <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> изменяет XML-разметку дочерних узлов, на которых в данный момент позиционируется объект <xref:System.Xml.XPath.XPathNavigator>, разобранный содержимым заданной XML-строки (`string`).</span><span class="sxs-lookup"><span data-stu-id="9ea94-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="9ea94-160">Подобным образом свойство <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> изменяет XML-разметку дочерних узлов, на которых в данный момент позиционируется объект <xref:System.Xml.XPath.XPathNavigator>, так же как и самого текущего узла.</span><span class="sxs-lookup"><span data-stu-id="9ea94-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="9ea94-161">Помимо методов, описанных в этом разделе, для вставки узлов и значений в XML-документ можно использовать свойства <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> и <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="9ea94-162">Дополнительные сведения об использовании свойств <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> и [ для добавления узлов и значений см. в <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>руководстве по изменению данных XML с помощью XPathNavigator](modify-xml-data-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="9ea94-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="9ea94-163">Конфликты пространства имен и деклараций xml:lang</span><span class="sxs-lookup"><span data-stu-id="9ea94-163">Namespace and xml:lang Conflicts</span></span>  

 <span data-ttu-id="9ea94-164">При вставке XML-данных с помощью методов `xml:lang`, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> и <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> класса <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, принимающих в качестве параметров объекты <xref:System.Xml.XPath.XPathNavigator>, могут возникнуть определенные конфликты, связанные с областью пространства имен и деклараций <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="9ea94-165">Ниже перечислены возможные конфликты пространства имен.</span><span class="sxs-lookup"><span data-stu-id="9ea94-165">The following are the possible namespace conflicts.</span></span>  
  
- <span data-ttu-id="9ea94-166">Если существует пространство имен в контексте объекта <xref:System.Xml.XmlReader>, где префикс сопоставления URI-кода пространства имен не содержится в контексте объекта <xref:System.Xml.XPath.XPathNavigator>, то к вновь добавленному узлу добавляется новая декларация пространства имен.</span><span class="sxs-lookup"><span data-stu-id="9ea94-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="9ea94-167">Если один и тот же URI-код пространства имен находится как в контексте объекта <xref:System.Xml.XmlReader>, так и в контексте объекта <xref:System.Xml.XPath.XPathNavigator>, но префиксы в различных контекстах различаются, то к вновь добавленному узлу добавляется декларация нового пространства имен, а префикс и URI-код пространства имен берутся из объекта <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="9ea94-168">Если один и тот же префикс пространства имен находится как в контексте объекта <xref:System.Xml.XmlReader>, так и в контексте объекта <xref:System.Xml.XPath.XPathNavigator>, но в контекстах ему сопоставлены различные URI-коды пространств имен, то к вновь добавленному узлу добавляется декларация нового пространства имен, а префикс и URI-код пространства имен берутся из объекта <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="9ea94-169">Если и префикс, и URI-код пространства имен в обоих контекстах объекта <xref:System.Xml.XmlReader> и объекта <xref:System.Xml.XPath.XPathNavigator> одинаковы, то к вновь добавленному узлу декларация нового пространства имен не добавляется.</span><span class="sxs-lookup"><span data-stu-id="9ea94-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ea94-170">Приведенное выше описание применимо также к декларациям пространства имен с пустой строкой `string` в качестве префикса (например, декларация пространства имен по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="9ea94-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="9ea94-171">Ниже перечислены возможные конфликты деклараций `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="9ea94-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
- <span data-ttu-id="9ea94-172">Если атрибут `xml:lang` существует в контексте объекта <xref:System.Xml.XmlReader>, но отсутствует в контексте объекта <xref:System.Xml.XPath.XPathNavigator>, то к вновь добавленному узлу добавляется атрибут `xml:lang`, значение которого берется из объекта <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="9ea94-173">Если атрибут `xml:lang` существует в контексте обоих объектов, <xref:System.Xml.XmlReader> и <xref:System.Xml.XPath.XPathNavigator>, но его значения там различаются, то к вновь добавленному узлу добавляется атрибут `xml:lang`, значение которого берется из объекта <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="9ea94-174">Если атрибут `xml:lang` существует в контексте обоих объектов, <xref:System.Xml.XmlReader> и <xref:System.Xml.XPath.XPathNavigator>, с одинаковыми значениями, то к вновь добавленному узлу новый атрибут `xml:lang` не добавляется.</span><span class="sxs-lookup"><span data-stu-id="9ea94-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
- <span data-ttu-id="9ea94-175">Если атрибут `xml:lang` существует в контексте объекта <xref:System.Xml.XPath.XPathNavigator>, но не существует в контексте объекта <xref:System.Xml.XmlReader>, то к вновь добавленному узлу вообще не добавляется атрибут `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="9ea94-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="9ea94-176">Вставка узлов с помощью класса XmlWriter</span><span class="sxs-lookup"><span data-stu-id="9ea94-176">Inserting Nodes with XmlWriter</span></span>  

 <span data-ttu-id="9ea94-177">Методы, используемые для вставки одноуровневых узлов, дочерних узлов и узлов атрибутов, которые описаны в разделе «Вставка узлов и атрибутов», перегружены.</span><span class="sxs-lookup"><span data-stu-id="9ea94-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="9ea94-178">Методы <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> и <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> класса <xref:System.Xml.XPath.XPathNavigator> возвращают объект <xref:System.Xml.XmlWriter>, используемый для вставки узлов.</span><span class="sxs-lookup"><span data-stu-id="9ea94-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="9ea94-179">Неподдерживаемые методы класса XmlWriter</span><span class="sxs-lookup"><span data-stu-id="9ea94-179">Unsupported XmlWriter Methods</span></span>  

 <span data-ttu-id="9ea94-180">Не все методы, используемые для записи данных в XML-документ с помощью класса <xref:System.Xml.XmlWriter>, поддерживаются классом <xref:System.Xml.XPath.XPathNavigator>, что связано с различиями между моделями данных XPath и DOM.</span><span class="sxs-lookup"><span data-stu-id="9ea94-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="9ea94-181">В следующей таблице описаны методы класса <xref:System.Xml.XmlWriter>, которые не поддерживаются в классе <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="9ea94-182">Метод</span><span class="sxs-lookup"><span data-stu-id="9ea94-182">Method</span></span>|<span data-ttu-id="9ea94-183">Описание</span><span class="sxs-lookup"><span data-stu-id="9ea94-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="9ea94-184">Формирует исключение <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="9ea94-185">Не обрабатывается на корневом уровне и формирует исключение <xref:System.NotSupportedException> при вызове на любом другом уровне XML-документа.</span><span class="sxs-lookup"><span data-stu-id="9ea94-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="9ea94-186">Интерпретируется как вызов метода <xref:System.Xml.XmlWriter.WriteString%2A> для эквивалентного символа или символов.</span><span class="sxs-lookup"><span data-stu-id="9ea94-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="9ea94-187">Интерпретируется как вызов метода <xref:System.Xml.XmlWriter.WriteString%2A> для эквивалентного символа или символов.</span><span class="sxs-lookup"><span data-stu-id="9ea94-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="9ea94-188">Интерпретируется как вызов метода <xref:System.Xml.XmlWriter.WriteString%2A> для эквивалентного символа или символов.</span><span class="sxs-lookup"><span data-stu-id="9ea94-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="9ea94-189">Дополнительные сведения о классе <xref:System.Xml.XmlWriter> см. в справочной документации по классу <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="9ea94-190">Несколько объектов XmlWriter</span><span class="sxs-lookup"><span data-stu-id="9ea94-190">Multiple XmlWriter Objects</span></span>  

 <span data-ttu-id="9ea94-191">Можно иметь несколько объектов <xref:System.Xml.XPath.XPathNavigator>, указывающих на различные части XML-документа с одним или более открытыми объектами <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="9ea94-192">Использование нескольких объектов <xref:System.Xml.XmlWriter> разрешено и поддерживается в однопоточных сценариях.</span><span class="sxs-lookup"><span data-stu-id="9ea94-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="9ea94-193">При использовании нескольких объектов <xref:System.Xml.XmlWriter> важно учесть следующие замечания.</span><span class="sxs-lookup"><span data-stu-id="9ea94-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
- <span data-ttu-id="9ea94-194">XML-фрагменты, созданные с помощью объекта <xref:System.Xml.XmlWriter>, добавляются в XML-документ при вызове метода <xref:System.Xml.XmlWriter.Close%2A> для каждого объекта <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="9ea94-195">До этого момента объект <xref:System.Xml.XmlWriter> записывает данные в отсоединенный фрагмент.</span><span class="sxs-lookup"><span data-stu-id="9ea94-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="9ea94-196">Если операция выполняется на открытом XML-документе, то все фрагменты, записываемые объектом <xref:System.Xml.XmlWriter>, не затрагиваются до вызова метода <xref:System.Xml.XmlWriter.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
- <span data-ttu-id="9ea94-197">Если на определенном поддереве XML существует открытый объект <xref:System.Xml.XmlWriter>, и поддерево удаляется, то объект <xref:System.Xml.XmlWriter> все равно может добавляться к поддереву.</span><span class="sxs-lookup"><span data-stu-id="9ea94-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="9ea94-198">Просто это поддерево становится удаленным фрагментом.</span><span class="sxs-lookup"><span data-stu-id="9ea94-198">The subtree simply becomes a deleted fragment.</span></span>  
  
- <span data-ttu-id="9ea94-199">Если в одном XML-документе одновременно открыто несколько объектов <xref:System.Xml.XmlWriter>, то они добавляются в XML-документ в порядке закрытия объектов <xref:System.Xml.XmlWriter>, а не в порядке их открытия.</span><span class="sxs-lookup"><span data-stu-id="9ea94-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="9ea94-200">В следующем примере создается объект <xref:System.Xml.XmlDocument>, создается объект <xref:System.Xml.XPath.XPathNavigator>, а потом используется объект <xref:System.Xml.XmlWriter>, возвращаемый методом <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, чтобы создать структуру первой книги в файле `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="9ea94-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="9ea94-201">Затем файл `book.xml` сохраняется.</span><span class="sxs-lookup"><span data-stu-id="9ea94-201">The example then saves it as the `book.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Using writer As XmlWriter = navigator.PrependChild()  
  
    writer.WriteStartElement("bookstore")  
    writer.WriteStartElement("book")  
    writer.WriteAttributeString("genre", "autobiography")  
    writer.WriteAttributeString("publicationdate", "1981-03-22")  
    writer.WriteAttributeString("ISBN", "1-861003-11-0")  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin")  
    writer.WriteStartElement("author")  
    writer.WriteElementString("first-name", "Benjamin")  
    writer.WriteElementString("last-name", "Franklin")  
    writer.WriteElementString("price", "8.99")  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
  
End Using  
  
document.Save("book.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
XPathNavigator navigator = document.CreateNavigator();  
  
using (XmlWriter writer = navigator.PrependChild())  
{  
    writer.WriteStartElement("bookstore");  
    writer.WriteStartElement("book");  
    writer.WriteAttributeString("genre", "autobiography");  
    writer.WriteAttributeString("publicationdate", "1981-03-22");  
    writer.WriteAttributeString("ISBN", "1-861003-11-0");  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin");  
    writer.WriteStartElement("author");  
    writer.WriteElementString("first-name", "Benjamin");  
    writer.WriteElementString("last-name", "Franklin");  
    writer.WriteElementString("price", "8.99");  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
}  
document.Save("book.xml");  
```  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="9ea94-202">Сохранение XML-документа</span><span class="sxs-lookup"><span data-stu-id="9ea94-202">Saving an XML Document</span></span>  

 <span data-ttu-id="9ea94-203">Сохранение изменений, внесенных в объект <xref:System.Xml.XmlDocument> в результате выполнения описанных в данном разделе методов, выполняется с помощью методов класса <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="9ea94-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="9ea94-204">Дополнительные сведения о сохранении изменений, внесенных в объект <xref:System.Xml.XmlDocument>, см. в руководстве по [созданию и сохранению документов](saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="9ea94-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ea94-205">См. также</span><span class="sxs-lookup"><span data-stu-id="9ea94-205">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="9ea94-206">Обработка XML-данных с использованием модели данных XPath</span><span class="sxs-lookup"><span data-stu-id="9ea94-206">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="9ea94-207">Изменение XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="9ea94-207">Modify XML Data using XPathNavigator</span></span>](modify-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="9ea94-208">Удаление XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="9ea94-208">Remove XML Data using XPathNavigator</span></span>](remove-xml-data-using-xpathnavigator.md)
