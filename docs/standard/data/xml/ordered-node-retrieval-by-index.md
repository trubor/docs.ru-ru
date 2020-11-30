---
title: Упорядоченное извлечение узлов по индексу
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
ms.openlocfilehash: 37d350231e03e8a435977328a288abff2f336a4b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731167"
---
# <a name="ordered-node-retrieval-by-index"></a><span data-ttu-id="d6554-102">Упорядоченное извлечение узлов по индексу</span><span class="sxs-lookup"><span data-stu-id="d6554-102">Ordered Node Retrieval by Index</span></span>

<span data-ttu-id="d6554-103">Модель DOM XML-документа консорциума W3C описывает класс NodeList, который позволяет обрабатывать упорядоченные списки узлов, в отличие от неупорядоченного набора, обрабатываемого с помощью класса **XmlNamedNodeMap**.</span><span class="sxs-lookup"><span data-stu-id="d6554-103">The World Wide Web Consortium (W3C) XML Document Object Model (DOM) also describes a NodeList, which has the ability to handle an ordered list of nodes, as opposed to the unordered set handled by the **XmlNamedNodeMap**.</span></span> <span data-ttu-id="d6554-104">Класс NodeList в платформе Microsoft .NET Framework называется **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="d6554-104">The NodeList in the Microsoft .NET Framework is called **XmlNodeList**.</span></span> <span data-ttu-id="d6554-105">Методы и свойства, которые возвращают класс **XmlNodeList**:</span><span class="sxs-lookup"><span data-stu-id="d6554-105">Methods and properties that return an **XmlNodeList** are:</span></span>  
  
- <span data-ttu-id="d6554-106">XmlNode.ChildNodes</span><span class="sxs-lookup"><span data-stu-id="d6554-106">XmlNode.ChildNodes</span></span>  
  
- <span data-ttu-id="d6554-107">XmlDocument.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="d6554-107">XmlDocument.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="d6554-108">XmlElement.GetElementsByTagName;</span><span class="sxs-lookup"><span data-stu-id="d6554-108">XmlElement.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="d6554-109">XmlNode.SelectNodes</span><span class="sxs-lookup"><span data-stu-id="d6554-109">XmlNode.SelectNodes</span></span>  
  
 <span data-ttu-id="d6554-110">Класс **XmlNodeList** имеет свойство **Count**, с помощью которого можно создавать циклы для выполнения итерации по узлам объекта **XmlNodeList**, как показано в следующем примере кода:</span><span class="sxs-lookup"><span data-stu-id="d6554-110">The **XmlNodeList** has a **Count** property that can be used to write loops to iterate over the nodes in the **XmlNodeList**, as shown in the following code sample:</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
   doc.Load("books.xml")  
  
    ' Retrieve all book titles.  
    Dim root as XmlElement = doc.DocumentElement  
    Dim elemList as XmlNodeList = root.GetElementsByTagName("title")  
    Dim i as integer  
    for i=0  to elemList.Count-1  
        ' Display all book titles in the Node List.  
        Console.WriteLine(elemList.ItemOf(i).InnerXml)  
    next  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
// Retrieve all book titles.  
XmlElement root = doc.DocumentElement;  
XmlNodeList elemList = root.GetElementsByTagName("title");  
for (int i=0; i < elemList.Count; i++)  
{
   // Display all book titles in the Node List.  
   Console.WriteLine(elemList[i].InnerXml);  
}
```  
  
 <span data-ttu-id="d6554-111">В дополнение к свойству **Count**, доступен метод **GetEnumerator**, который обеспечивает итерацию в стиле `foreach` по коллекции узлов в объекте **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="d6554-111">In addition to the **Count** property, there is a **GetEnumerator** method that provides a, `foreach` style iteration over the collection of nodes in the **XmlNodeList**.</span></span> <span data-ttu-id="d6554-112">В следующем примере кода показано использование инструкции `foreach`.</span><span class="sxs-lookup"><span data-stu-id="d6554-112">The following code example shows the use of the `foreach` statement.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("books.xml")  
  
' Get book titles.  
Dim root As XmlElement = doc.DocumentElement  
Dim elemList As XmlNodeList = root.GetElementsByTagName("title")  
Dim ienum As IEnumerator = elemList.GetEnumerator()  
' Loop over the XmlNodeList using the enumerator ienum
While ienum.MoveNext()  
    ' Display the book title.  
    Dim title As XmlNode = CType(ienum.Current, XmlNode)  
    Console.WriteLine(title.InnerText)  
End While  
```  
  
```csharp  
{  
     XmlDocument doc = new XmlDocument();  
     doc.Load("books.xml");  
  
     // Get book titles.  
     XmlElement root = doc.DocumentElement;  
     XmlNodeList elemList = root.GetElementsByTagName("title");  
     IEnumerator ienum = elemList.GetEnumerator();
     // Loop over the XmlNodeList using the enumerator ienum
     while (ienum.MoveNext())  
     {  
          // Display the book title.  
           XmlNode title = (XmlNode) ienum.Current;  
           Console.WriteLine(title.InnerText);  
     }  
  }  
```  
  
 <span data-ttu-id="d6554-113">Дополнительные сведения о доступных методах и свойствах класса **XmlNodeList** см. в описании <xref:System.Xml.XmlNodeList>.</span><span class="sxs-lookup"><span data-stu-id="d6554-113">For more information on the methods and properties available on the **XmlNodeList**, see <xref:System.Xml.XmlNodeList>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6554-114">См. также</span><span class="sxs-lookup"><span data-stu-id="d6554-114">See also</span></span>

- [<span data-ttu-id="d6554-115">Модель объектов документов XML (DOM)</span><span class="sxs-lookup"><span data-stu-id="d6554-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
