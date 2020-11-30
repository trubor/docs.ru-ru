---
title: Вычисление выражения XPath с помощью класса XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: 19e3287a990bbfd793bce892b14f08f31c53faa2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687207"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="a154c-102">Вычисление выражения XPath с помощью класса XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a154c-102">Evaluate XPath Expressions using XPathNavigator</span></span>

<span data-ttu-id="a154c-103">Класс <xref:System.Xml.XPath.XPathNavigator> содержит метод <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> для вычисления выражения Xpath.</span><span class="sxs-lookup"><span data-stu-id="a154c-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="a154c-104">Метод <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> принимает выражение XPath, вычисляет его и возвращает соответствующий стандарту W3C тип XPath Boolean, Number, String или Node Set, основанный на результате вычисления выражения XPath.</span><span class="sxs-lookup"><span data-stu-id="a154c-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="a154c-105">Метод Evaluate</span><span class="sxs-lookup"><span data-stu-id="a154c-105">The Evaluate Method</span></span>  

 <span data-ttu-id="a154c-106">Метод <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> принимает выражение XPath, вычисляет его и возвращает типизированный результат Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>) или Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span><span class="sxs-lookup"><span data-stu-id="a154c-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="a154c-107">К примеру, метод <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> можно использовать в математическом методе.</span><span class="sxs-lookup"><span data-stu-id="a154c-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="a154c-108">В следующем примере кода рассчитывается совокупная стоимость всех книг в файле `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="a154c-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 <span data-ttu-id="a154c-109">В примере в качестве входных данных используется файл `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="a154c-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="a154c-110">Функции position и last</span><span class="sxs-lookup"><span data-stu-id="a154c-110">position and last Functions</span></span>  

 <span data-ttu-id="a154c-111">Метод <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> перегружен.</span><span class="sxs-lookup"><span data-stu-id="a154c-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="a154c-112">Один из методов <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> принимает объект <xref:System.Xml.XPath.XPathNodeIterator> в качестве параметра.</span><span class="sxs-lookup"><span data-stu-id="a154c-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="a154c-113">Данный конкретный метод <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> идентичен методу <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>, который принимает в качестве параметра только объект <xref:System.Xml.XPath.XPathExpression>; единственное отличие состоит в том, что первый метод допускает применение в качестве аргумента набора узлов для обозначения текущего контекста, в котором будут осуществляться вычисления.</span><span class="sxs-lookup"><span data-stu-id="a154c-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="a154c-114">Этот контекст требуется для функций `position()` и `last()`, поскольку они работают относительно текущего узла контекста.</span><span class="sxs-lookup"><span data-stu-id="a154c-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="a154c-115">Если функции `position()` и `last()` не используются в качестве предикатов в шаге доступа, эти функции требуют ссылки на набор узлов для выполнения вычислений; иначе функции `position` и `last` возвращают значение `0`.</span><span class="sxs-lookup"><span data-stu-id="a154c-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a154c-116">См. также</span><span class="sxs-lookup"><span data-stu-id="a154c-116">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="a154c-117">Обработка XML-данных с использованием модели данных XPath</span><span class="sxs-lookup"><span data-stu-id="a154c-117">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="a154c-118">Выборка XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a154c-118">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="a154c-119">Соответствие узлов с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a154c-119">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="a154c-120">Типы узлов, распознаваемые запросами XPath</span><span class="sxs-lookup"><span data-stu-id="a154c-120">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="a154c-121">Запросы XPath и пространства имен</span><span class="sxs-lookup"><span data-stu-id="a154c-121">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="a154c-122">Скомпилированные выражения XPath</span><span class="sxs-lookup"><span data-stu-id="a154c-122">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
