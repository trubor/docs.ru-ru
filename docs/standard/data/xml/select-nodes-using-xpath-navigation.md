---
title: Выбор узлов с помощью XPath-навигации
description: Сведения о том, как выбрать XML-узлы в .NET. Вы можете применять методы модели DOM, позволяющие использовать навигацию языка XPath для запроса данных в модели DOM.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
ms.openlocfilehash: b6b68d9351431acc6d9ef20276f51ac4d667d325
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734690"
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="bf94d-104">Выбор узлов с помощью XPath-навигации</span><span class="sxs-lookup"><span data-stu-id="bf94d-104">Select Nodes Using XPath Navigation</span></span>

<span data-ttu-id="bf94d-105">Модель DOM содержит методы, позволяющие использовать навигацию языка XPath для запроса данных в модели DOM.</span><span class="sxs-lookup"><span data-stu-id="bf94d-105">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="bf94d-106">Язык XPath используется для поиска конкретного одиночного узла или всех узлов, соответствующих некоторым условиям.</span><span class="sxs-lookup"><span data-stu-id="bf94d-106">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="bf94d-107">Методы выбора XPath</span><span class="sxs-lookup"><span data-stu-id="bf94d-107">XPath Select Methods</span></span>  

 <span data-ttu-id="bf94d-108">Классы DOM предоставляют два способа выбора XPath: метод <xref:System.Xml.XmlNode.SelectSingleNode%2A> и метод <xref:System.Xml.XmlNode.SelectNodes%2A>.</span><span class="sxs-lookup"><span data-stu-id="bf94d-108">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="bf94d-109">Метод <xref:System.Xml.XmlNode.SelectSingleNode%2A> возвращает первый узел, соответствующий критериям выбора.</span><span class="sxs-lookup"><span data-stu-id="bf94d-109">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="bf94d-110">Метод <xref:System.Xml.XmlNode.SelectNodes%2A> возвращает список <xref:System.Xml.XmlNodeList>, содержащий соответствующие узлы.</span><span class="sxs-lookup"><span data-stu-id="bf94d-110">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="bf94d-111">В следующем примере метод <xref:System.Xml.XmlNode.SelectSingleNode%2A> используется для выбора первого узла `book`, в котором фамилия автора соответствует указанному критерию.</span><span class="sxs-lookup"><span data-stu-id="bf94d-111">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="bf94d-112">Файл bookstore.xml (приведенный в конце этого раздела) используется в качестве входного файла.</span><span class="sxs-lookup"><span data-stu-id="bf94d-112">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 <span data-ttu-id="bf94d-113">В следующем примере метод <xref:System.Xml.XmlNode.SelectNodes%2A> используется для выбора всех узлов для книг, где цена превышает указанное значение.</span><span class="sxs-lookup"><span data-stu-id="bf94d-113">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="bf94d-114">Затем цена каждой из книг в списке выборки программным способом уменьшается на 10 %.</span><span class="sxs-lookup"><span data-stu-id="bf94d-114">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="bf94d-115">Наконец, файл с внесенными изменениями выводится на консоль.</span><span class="sxs-lookup"><span data-stu-id="bf94d-115">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="bf94d-116">Файл bookstore.xml (приведенный в конце этого раздела) используется в качестве входного файла.</span><span class="sxs-lookup"><span data-stu-id="bf94d-116">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 <span data-ttu-id="bf94d-117">В вышеприведенных примерах запрос XPath начинается с элемента документа.</span><span class="sxs-lookup"><span data-stu-id="bf94d-117">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="bf94d-118">Указание начальной точки для запроса XPath устанавливает контекстный узел, с которого начинается запрос XPath.</span><span class="sxs-lookup"><span data-stu-id="bf94d-118">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="bf94d-119">Если нужно начать не с элемента документа, а с первого дочернего элемента, можно использовать инструкцию выбора следующим образом.</span><span class="sxs-lookup"><span data-stu-id="bf94d-119">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="bf94d-120">Все объекты <xref:System.Xml.XmlNodeList> синхронизируются с базовым документом.</span><span class="sxs-lookup"><span data-stu-id="bf94d-120">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="bf94d-121">Поэтому если при проходе по списку узлов изменить значение узла, этот узел также обновляется в исходном документе.</span><span class="sxs-lookup"><span data-stu-id="bf94d-121">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="bf94d-122">В вышеприведенном примере обратите внимание, что при изменении узла в выбранном списке узлов <xref:System.Xml.XmlNodeList> базовый документ также изменится.</span><span class="sxs-lookup"><span data-stu-id="bf94d-122">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf94d-123">При изменении базового документа рекомендуется повторно запустить выбор.</span><span class="sxs-lookup"><span data-stu-id="bf94d-123">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="bf94d-124">Если изменение узла может привести к его добавлению в список узлов, где он ранее отсутствовал, или удалению из списка узлов, точность списка узлов не гарантируется.</span><span class="sxs-lookup"><span data-stu-id="bf94d-124">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="bf94d-125">Пространства имен в выражениях XPath</span><span class="sxs-lookup"><span data-stu-id="bf94d-125">Namespaces in XPath Expressions</span></span>  

 <span data-ttu-id="bf94d-126">Выражения XPath могут включать пространства имен.</span><span class="sxs-lookup"><span data-stu-id="bf94d-126">XPath expressions can include namespaces.</span></span> <span data-ttu-id="bf94d-127">Разрешение пространства имен поддерживается с помощью объекта <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="bf94d-127">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="bf94d-128">Если выражение XPath содержит префикс, этот префикс вместе с URI-кодом пространства имен необходимо добавить к объекту <xref:System.Xml.XmlNamespaceManager>, и объект <xref:System.Xml.XmlNamespaceManager> передается методу <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> или <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29>.</span><span class="sxs-lookup"><span data-stu-id="bf94d-128">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="bf94d-129">Обратите внимание, что вышеприведенные примеры кода пользуются диспетчером <xref:System.Xml.XmlNamespaceManager> для разрешения пространства имен документа bookstore.xml.</span><span class="sxs-lookup"><span data-stu-id="bf94d-129">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf94d-130">Если выражение XPath не содержит префикс, предполагается, что URI-код пространства имен указывает на пустое пространство имен.</span><span class="sxs-lookup"><span data-stu-id="bf94d-130">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="bf94d-131">Если XML включает пространство имен по умолчанию, необходимо добавить префикс вместе с URI-кодом пространства имен к объекту <xref:System.Xml.XmlNamespaceManager>, в противном случае невозможно будет выбрать узлы.</span><span class="sxs-lookup"><span data-stu-id="bf94d-131">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="bf94d-132">Входной файл</span><span class="sxs-lookup"><span data-stu-id="bf94d-132">Input File</span></span>  

 <span data-ttu-id="bf94d-133">Файл bookstore.xml используется в качестве входного файла в примерах этого раздела.</span><span class="sxs-lookup"><span data-stu-id="bf94d-133">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf94d-134">См. также</span><span class="sxs-lookup"><span data-stu-id="bf94d-134">See also</span></span>

- [<span data-ttu-id="bf94d-135">Модель объектов документов XML (DOM)</span><span class="sxs-lookup"><span data-stu-id="bf94d-135">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
