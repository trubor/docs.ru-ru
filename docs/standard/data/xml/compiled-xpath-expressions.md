---
title: Скомпилированные выражения XPath
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
ms.openlocfilehash: 99f06db3c6f1e634e9c4a677c01d1b0849afe43f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701514"
---
# <a name="compiled-xpath-expressions"></a><span data-ttu-id="119e9-102">Скомпилированные выражения XPath</span><span class="sxs-lookup"><span data-stu-id="119e9-102">Compiled XPath Expressions</span></span>

<span data-ttu-id="119e9-103">Объект <xref:System.Xml.XPath.XPathExpression> представляет скомпилированный запрос XPath, возвращаемый либо статическим методом <xref:System.Xml.XPath.XPathExpression.Compile%2A> класса <xref:System.Xml.XPath.XPathExpression>, либо методом <xref:System.Xml.XPath.XPathNavigator.Compile%2A> класса <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="119e9-103">An <xref:System.Xml.XPath.XPathExpression> object represents a compiled XPath query returned from either the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="the-xpathexpression-class"></a><span data-ttu-id="119e9-104">Класс XPathExpression</span><span class="sxs-lookup"><span data-stu-id="119e9-104">The XPathExpression Class</span></span>  

 <span data-ttu-id="119e9-105">Скомпилированный запрос XPath, представляемый объектом <xref:System.Xml.XPath.XPathExpression> полезен в случаях, когда один запрос XPath используется несколько раз.</span><span class="sxs-lookup"><span data-stu-id="119e9-105">A compiled XPath query represented by an <xref:System.Xml.XPath.XPathExpression> object is useful if the same XPath query is being used more than once.</span></span>  
  
 <span data-ttu-id="119e9-106">Например, если метод <xref:System.Xml.XPath.XPathNavigator.Select%2A> вызывается несколько раз, то вместо многократного использования строки, представляющей запрос XPath, используйте метод <xref:System.Xml.XPath.XPathExpression.Compile%2A> класса <xref:System.Xml.XPath.XPathExpression> или метод <xref:System.Xml.XPath.XPathNavigator.Compile%2A> класса <xref:System.Xml.XPath.XPathNavigator>, чтобы скомпилировать запрос XPath и поместить его в кэш в объекте <xref:System.Xml.XPath.XPathExpression> для повторного использования и повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="119e9-106">For example, when calling the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method multiple times, instead of using a string representing the XPath query each time, use the <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class to compile and cache the XPath query in an <xref:System.Xml.XPath.XPathExpression> object for reuse and improved performance.</span></span>  
  
 <span data-ttu-id="119e9-107">Скомпилированный объект <xref:System.Xml.XPath.XPathExpression> можно использовать как входной аргумент для следующих методов класса <xref:System.Xml.XPath.XPathNavigator> в зависимости от типа, возвращаемого запросом XPath.</span><span class="sxs-lookup"><span data-stu-id="119e9-107">Once compiled, the <xref:System.Xml.XPath.XPathExpression> object may be used as input to the following <xref:System.Xml.XPath.XPathNavigator> class methods depending on the type returned from the XPath query.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="119e9-108">В следующей таблице описаны возвращаемые типы W3C XPath и их эквиваленты в платформе Microsoft .NET Framework, а также методы, с которыми можно использовать объект <xref:System.Xml.XPath.XPathExpression> в зависимости от возвращаемого им типа.</span><span class="sxs-lookup"><span data-stu-id="119e9-108">The following table describes each of the W3C XPath return types, their Microsoft .NET Framework equivalencies, and what methods the <xref:System.Xml.XPath.XPathExpression> object may be used with based on its return type.</span></span>  
  
|<span data-ttu-id="119e9-109">Тип возвращаемого значения W3C XPath</span><span class="sxs-lookup"><span data-stu-id="119e9-109">W3C XPath Return Type</span></span>|<span data-ttu-id="119e9-110">Эквивалентный тип в .NET Framework</span><span class="sxs-lookup"><span data-stu-id="119e9-110">.NET Framework Equivalent Type</span></span>|<span data-ttu-id="119e9-111">Описание</span><span class="sxs-lookup"><span data-stu-id="119e9-111">Description</span></span>|<span data-ttu-id="119e9-112">Методы</span><span class="sxs-lookup"><span data-stu-id="119e9-112">Methods</span></span>|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="119e9-113">Неупорядоченная коллекция узлов без повторяющихся узлов, созданная в порядке документа.</span><span class="sxs-lookup"><span data-stu-id="119e9-113">An unordered collection of nodes without duplicates created in document order.</span></span>|<span data-ttu-id="119e9-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> или <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span><span class="sxs-lookup"><span data-stu-id="119e9-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> or <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span></span>|  
|`Boolean`|<xref:System.Boolean>|<span data-ttu-id="119e9-115">Значение `true` или `false`.</span><span class="sxs-lookup"><span data-stu-id="119e9-115">A `true` or `false` value.</span></span>|<span data-ttu-id="119e9-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> или</span><span class="sxs-lookup"><span data-stu-id="119e9-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> or</span></span><br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|<span data-ttu-id="119e9-117">Число с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="119e9-117">A floating-point number.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|<span data-ttu-id="119e9-118">Последовательность символов UCS.</span><span class="sxs-lookup"><span data-stu-id="119e9-118">A sequence of UCS characters.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> <span data-ttu-id="119e9-119">Метод <xref:System.Xml.XPath.XPathNavigator.Matches%2A> принимает в качестве параметра выражение XPath.</span><span class="sxs-lookup"><span data-stu-id="119e9-119">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method accepts an XPath expression as its parameter.</span></span> <span data-ttu-id="119e9-120">Метод <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> возвращает объект <xref:System.Xml.XPath.XPathNavigator>, а не один из возвращаемых типов W3C XPath.</span><span class="sxs-lookup"><span data-stu-id="119e9-120">The <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method returns an <xref:System.Xml.XPath.XPathNavigator> object, not one of the W3C XPath return types.</span></span>  
  
### <a name="the-returntype-property"></a><span data-ttu-id="119e9-121">Свойство ReturnType</span><span class="sxs-lookup"><span data-stu-id="119e9-121">The ReturnType Property</span></span>  

 <span data-ttu-id="119e9-122">После компиляции запроса XPath в объект <xref:System.Xml.XPath.XPathExpression> можно использовать свойство <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> объекта <xref:System.Xml.XPath.XPathExpression>, чтобы определить возвращаемый тип запроса XPath.</span><span class="sxs-lookup"><span data-stu-id="119e9-122">After an XPath query has been compiled into an <xref:System.Xml.XPath.XPathExpression> object, you can use the <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of the <xref:System.Xml.XPath.XPathExpression> object to determine what the XPath query returns.</span></span>  
  
 <span data-ttu-id="119e9-123">Свойство <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> возвращает одно из следующих значений перечисления <xref:System.Xml.XPath.XPathResultType>, представляющего возвращаемые типы W3C XPath.</span><span class="sxs-lookup"><span data-stu-id="119e9-123">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property returns one of the following <xref:System.Xml.XPath.XPathResultType> enumeration values representing the W3C XPath return types.</span></span>  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 <span data-ttu-id="119e9-124">В следующем примере используется объект <xref:System.Xml.XPath.XPathExpression>, чтобы вернуть число и набор узлов из файла `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="119e9-124">The following example uses the <xref:System.Xml.XPath.XPathExpression> object to return a number and a node set from the `books.xml` file.</span></span> <span data-ttu-id="119e9-125">Свойство <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> каждого объекта <xref:System.Xml.XPath.XPathExpression>, а также результаты методов <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> и <xref:System.Xml.XPath.XPathNavigator.Select%2A> записываются в консоль.</span><span class="sxs-lookup"><span data-stu-id="119e9-125">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of each <xref:System.Xml.XPath.XPathExpression> object as well as the results from the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> and <xref:System.Xml.XPath.XPathNavigator.Select%2A> methods are written to the console.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Returns a number.  
Dim query1 As XPathExpression = navigator.Compile("bookstore/book/price/text()*10")  
Console.WriteLine(query1.ReturnType)  
  
Dim number As Double = CType(navigator.Evaluate(query1), Double)  
Console.WriteLine(number)  
  
' Returns a node set.  
Dim query2 As XPathExpression = navigator.Compile("bookstore/book/price")  
Console.WriteLine(query2.ReturnType)  
  
Dim nodes As XPathNodeIterator = navigator.Select(query2)  
nodes.MoveNext()  
Console.WriteLine(nodes.Current.Value)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Returns a number.  
XPathExpression query1 = navigator.Compile("bookstore/book/price/text()*10");  
Console.WriteLine(query1.ReturnType);  
  
Double number = (Double)navigator.Evaluate(query1);  
Console.WriteLine(number);  
  
// Returns a node set.  
XPathExpression query2 = navigator.Compile("bookstore/book/price");  
Console.WriteLine(query2.ReturnType);  
  
XPathNodeIterator nodes = navigator.Select(query2);  
nodes.MoveNext();  
Console.WriteLine(nodes.Current.Value);  
```  
  
 <span data-ttu-id="119e9-126">В примере в качестве входных данных используется файл `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="119e9-126">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a><span data-ttu-id="119e9-127">Выражения XPath повышенной производительности</span><span class="sxs-lookup"><span data-stu-id="119e9-127">Higher Performance XPath Expressions</span></span>  

 <span data-ttu-id="119e9-128">Для повышения производительности используйте в запросах по возможности наиболее точно заданные выражения XPath.</span><span class="sxs-lookup"><span data-stu-id="119e9-128">For better performance, use the most specific XPath expression possible in your queries.</span></span> <span data-ttu-id="119e9-129">Например, если узел `book` является дочерним для узла `bookstore`, а узел `bookstore` является элементом верхнего уровня в XML-документе, то использование выражения XPath `/bookstore/book` обеспечит скорость большую, чем использование выражения `//book`.</span><span class="sxs-lookup"><span data-stu-id="119e9-129">For example, if the `book` node is a child node of the `bookstore` node and the `bookstore` node is the top-most element in an XML document, using the XPath expression `/bookstore/book` is faster than using `//book`.</span></span> <span data-ttu-id="119e9-130">Выражение XPath `//book` будет просматривать каждый узел в XML-дереве для определения совпадающих узлов.</span><span class="sxs-lookup"><span data-stu-id="119e9-130">The `//book` XPath expression will scan every node in the XML tree to identify matching nodes.</span></span>  
  
 <span data-ttu-id="119e9-131">Кроме того, использование методов перемещения по набору узлов, предоставляемых классом <xref:System.Xml.XPath.XPathNavigator>, может повысить производительность по сравнению с методами выбора, предоставляемыми классом <xref:System.Xml.XPath.XPathNavigator>, в случаях с простыми критериями выбора.</span><span class="sxs-lookup"><span data-stu-id="119e9-131">Additionally, using the node set navigation methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class may result in improved performance over the selection methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class in cases where your selection criteria are simple.</span></span> <span data-ttu-id="119e9-132">Например, если нужно выбрать первый дочерний узел текущего узла, быстрее использовать метод <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, чем выражение XPath `child::*[1]` и метод <xref:System.Xml.XPath.XPathNavigator.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="119e9-132">For example, if you need to select the first child of the current node, it is faster to use the <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> method than to use the `child::*[1]` XPath expression and the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method.</span></span>  
  
 <span data-ttu-id="119e9-133">Дополнительные сведения о методах перемещения по набору узлов в классе <xref:System.Xml.XPath.XPathNavigator> см. в руководстве по [перемещению по узлам с помощью XPathNavigator](node-set-navigation-using-xpathnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="119e9-133">For more information about the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class, see [Node Set Navigation Using XPathNavigator](node-set-navigation-using-xpathnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119e9-134">См. также</span><span class="sxs-lookup"><span data-stu-id="119e9-134">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="119e9-135">Обработка XML-данных с использованием модели данных XPath</span><span class="sxs-lookup"><span data-stu-id="119e9-135">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="119e9-136">Выборка XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="119e9-136">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="119e9-137">Вычисление выражения XPath с помощью класса XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="119e9-137">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="119e9-138">Соответствие узлов с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="119e9-138">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="119e9-139">Типы узлов, распознаваемые запросами XPath</span><span class="sxs-lookup"><span data-stu-id="119e9-139">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="119e9-140">Запросы XPath и пространства имен</span><span class="sxs-lookup"><span data-stu-id="119e9-140">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
