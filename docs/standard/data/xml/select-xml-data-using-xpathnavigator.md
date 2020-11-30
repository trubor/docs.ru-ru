---
title: Выборка XML-данных с помощью XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: 9b12e60fcfac8c8fc4c2f2c80aac7400dfc8d6f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673466"
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="439b8-102">Выборка XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="439b8-102">Select XML Data Using XPathNavigator</span></span>

<span data-ttu-id="439b8-103">Класс <xref:System.Xml.XPath.XPathNavigator> содержит набор методов, используемых для выборки набора узлов в объекте <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument> с помощью выражения XPath.</span><span class="sxs-lookup"><span data-stu-id="439b8-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="439b8-104">По набору выбранных узлов можно передвигаться в цикле итерации.</span><span class="sxs-lookup"><span data-stu-id="439b8-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="439b8-105">Методы выбора в классе XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="439b8-105">XPathNavigator Selection Methods</span></span>  

 <span data-ttu-id="439b8-106">Класс <xref:System.Xml.XPath.XPathNavigator> содержит набор методов, используемых для выборки набора узлов в объекте <xref:System.Xml.XPath.XPathDocument> или <xref:System.Xml.XmlDocument> с помощью выражения XPath.</span><span class="sxs-lookup"><span data-stu-id="439b8-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="439b8-107">Класс <xref:System.Xml.XPath.XPathNavigator> содержит также набор оптимизированных методов для выборки узлов-предков, дочерних узлов и узлов-потомков быстрее, чем это можно сделать с помощью выражения XPath.</span><span class="sxs-lookup"><span data-stu-id="439b8-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="439b8-108">Набор выбранных узлов возвращается в объекте <xref:System.Xml.XPath.XPathNodeIterator> или, если набор состоит из одного узла, в объекте <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="439b8-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="439b8-109">Выбор узлов с помощью выражений XPath</span><span class="sxs-lookup"><span data-stu-id="439b8-109">Selecting Nodes Using XPath Expressions</span></span>  

 <span data-ttu-id="439b8-110">Для выбора узлов с помощью выражений XPath используется один из перечисленных ниже методов выборки.</span><span class="sxs-lookup"><span data-stu-id="439b8-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="439b8-111">Эти методы возвращают набор узлов, по которому можно свободно перемещаться с помощью объекта <xref:System.Xml.XPath.XPathNodeIterator>, или, если выбран один узел, в объекте <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="439b8-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="439b8-112">Перемещение с помощью объекта <xref:System.Xml.XPath.XPathNodeIterator> не влияет на позицию объекта <xref:System.Xml.XPath.XPathNavigator>, использованного для его создания.</span><span class="sxs-lookup"><span data-stu-id="439b8-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="439b8-113">Объект <xref:System.Xml.XPath.XPathNavigator>, возвращаемый методами <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>, располагается в единственном возвращаемом узле и также не влияет на положение объекта <xref:System.Xml.XPath.XPathNavigator>, с помощью которого создавался.</span><span class="sxs-lookup"><span data-stu-id="439b8-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="439b8-114">В следующем примере показано создание объекта <xref:System.Xml.XPath.XPathNavigator> из объекта <xref:System.Xml.XPath.XPathDocument>, использование метода <xref:System.Xml.XPath.XPathNavigator.Select%2A> для выбора узлов в объекте <xref:System.Xml.XPath.XPathDocument> и использование объекта <xref:System.Xml.XPath.XPathNodeIterator> для итеративного прохода по выбранным узлам.</span><span class="sxs-lookup"><span data-stu-id="439b8-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 <span data-ttu-id="439b8-115">В примере в качестве входных данных используется файл `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="439b8-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="439b8-116">Оптимизированные методы выбора</span><span class="sxs-lookup"><span data-stu-id="439b8-116">Optimized Selection Methods</span></span>  

 <span data-ttu-id="439b8-117">Методы <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> и <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> класса <xref:System.Xml.XPath.XPathNavigator> представляют выражения XPath, часто применяемые для получения дочерних узлов, узлов-потомков и узлов-предков.</span><span class="sxs-lookup"><span data-stu-id="439b8-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="439b8-118">Эти методы оптимизированы по производительности и работают быстрее, чем соответствующие им выражения XPath.</span><span class="sxs-lookup"><span data-stu-id="439b8-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="439b8-119">Методы <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> и <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> выбирают узлы-потомки, дочерние узлы и узлы-предки на основании значения <xref:System.Xml.XPath.XPathNodeType> или локального имени и URI-кода пространства имен узлов, которые нужно выбрать.</span><span class="sxs-lookup"><span data-stu-id="439b8-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="439b8-120">Выбранные узлы-потомки, дочерние узлы и узлы-предки возвращаются в объекте <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="439b8-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="439b8-121">См. также</span><span class="sxs-lookup"><span data-stu-id="439b8-121">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="439b8-122">Обработка XML-данных с использованием модели данных XPath</span><span class="sxs-lookup"><span data-stu-id="439b8-122">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="439b8-123">Вычисление выражения XPath с помощью класса XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="439b8-123">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="439b8-124">Соответствие узлов с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="439b8-124">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="439b8-125">Типы узлов, распознаваемые запросами XPath</span><span class="sxs-lookup"><span data-stu-id="439b8-125">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="439b8-126">Запросы XPath и пространства имен</span><span class="sxs-lookup"><span data-stu-id="439b8-126">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="439b8-127">Скомпилированные выражения XPath</span><span class="sxs-lookup"><span data-stu-id="439b8-127">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
