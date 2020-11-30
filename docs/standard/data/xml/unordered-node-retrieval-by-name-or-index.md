---
title: Неупорядоченное извлечение узлов по имени или индексу
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
ms.openlocfilehash: c3358f6cca27fbe61ba2b59fe6f2eb5df81c91ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675650"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="33d15-102">Неупорядоченное извлечение узлов по имени или индексу</span><span class="sxs-lookup"><span data-stu-id="33d15-102">Unordered Node Retrieval by Name or Index</span></span>

<span data-ttu-id="33d15-103">Класс **XmlNamedNodeMap** описан в спецификации консорциума W3C как NamedNodeMap. Он нужен для обработки неупорядоченного набора узлов с возможностью ссылаться на узлы по их именам и индексам.</span><span class="sxs-lookup"><span data-stu-id="33d15-103">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="33d15-104">Единственный способ доступа к классу **XmlNamedNodeMap** — возврат **XmlNamedNodeMap** через метод или свойство.</span><span class="sxs-lookup"><span data-stu-id="33d15-104">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="33d15-105">Есть три метода или свойства, возвращающих класс **XmlNamedNodeMap**:</span><span class="sxs-lookup"><span data-stu-id="33d15-105">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
- <span data-ttu-id="33d15-106">XmlElement.Attributes;</span><span class="sxs-lookup"><span data-stu-id="33d15-106">XmlElement.Attributes</span></span>  
  
- <span data-ttu-id="33d15-107">XmlDocumentType.Entities;</span><span class="sxs-lookup"><span data-stu-id="33d15-107">XmlDocumentType.Entities</span></span>  
  
- <span data-ttu-id="33d15-108">XmlDocumentType.Notations.</span><span class="sxs-lookup"><span data-stu-id="33d15-108">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="33d15-109">Например, свойство **XmlDocumentType.Entities** получает коллекцию узлов **XmlEntity**, указанных в декларации типа документа.</span><span class="sxs-lookup"><span data-stu-id="33d15-109">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="33d15-110">Эта коллекция возвращается как **XmlNamedNodeMap**. Можно выполнить итерацию по коллекции с помощью свойства **Count** и отобразить данные о сущности.</span><span class="sxs-lookup"><span data-stu-id="33d15-110">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="33d15-111">Пример выполнения итерации по **XmlNamedNodeMap** см. в описании <xref:System.Xml.XmlDocumentType.Entities%2A>.</span><span class="sxs-lookup"><span data-stu-id="33d15-111">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="33d15-112">Коллекция **XmlAttributeCollection** является производной от **XmlNamedNodeMap**. Изменять можно только атрибуты, а нотации и сущности доступны только для чтения.</span><span class="sxs-lookup"><span data-stu-id="33d15-112">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="33d15-113">С помощью коллекции **XmlNamedNodeMap** для атрибутов можно получить узлы на основе их XML-имен.</span><span class="sxs-lookup"><span data-stu-id="33d15-113">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="33d15-114">Это дает простой метод управления коллекцией атрибутов на узле элемента.</span><span class="sxs-lookup"><span data-stu-id="33d15-114">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="33d15-115">Этот метод можно противопоставить напрямую коллекции **XmlNodeList**, в которой также реализован интерфейс **IEnumerable**, но с использованием метода доступа по индексу, а не по строке.</span><span class="sxs-lookup"><span data-stu-id="33d15-115">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="33d15-116">Методы **RemoveNamedItem** и **SetNamedItem** используются только с коллекцией **XmlAttributeCollection**.</span><span class="sxs-lookup"><span data-stu-id="33d15-116">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="33d15-117">Добавление или удаление из коллекции атрибутов, как с помощью реализации **AttributeCollection**, так и с помощью **XmlNamedNodeMap**, изменяет коллекцию атрибутов в элементе.</span><span class="sxs-lookup"><span data-stu-id="33d15-117">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="33d15-118">В следующем примере кода показан способ перемещения атрибута и создания атрибута.</span><span class="sxs-lookup"><span data-stu-id="33d15-118">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
  
Class test  
  
    Public Shared Sub Main()  
        Dim doc As New XmlDocument()  
        doc.LoadXml("<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> ")  
  
        ' Get the attributes of node "child2 "  
        Dim ac As XmlAttributeCollection = doc.DocumentElement.ChildNodes(1).Attributes  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
        Dim i As Integer  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Get the 'attr1' from child1.  
        Dim attr As XmlAttribute = doc.DocumentElement.ChildNodes(0).Attributes(0)  
  
        ' Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem(attr)  
  
        ''attr1' will be removed from 'child1' and added to 'child2'.  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Create a new attribute and add to the collection.  
        Dim attr2 As XmlAttribute = doc.CreateAttribute("attr4")  
        attr2.Value = "val4"  
        ac.SetNamedItem(attr2)  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
    End Sub 'Main  
End Class 'test  
```  
  
```csharp  
using System;  
using System.Xml;  
class test {  
    public static void Main() {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml( "<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> " );  
  
        // Get the attributes of node "child2"  
        XmlAttributeCollection ac = doc.DocumentElement.ChildNodes[1].Attributes;  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );  
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
        // Get the 'attr1' from child1.  
        XmlAttribute attr = doc.DocumentElement.ChildNodes[0].Attributes[0];  
  
        // Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem( attr );  
  
        // 'attr1' will be removed from 'child1' and added to 'child2'.  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
        // Create a new attribute and add to the collection.  
        XmlAttribute attr2 = doc.CreateAttribute( "attr4" );  
        attr2.Value = "val4";  
        ac.SetNamedItem( attr2 );  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
    }  
}  
```  
  
 <span data-ttu-id="33d15-119">Дополнительный пример кода, в котором показано перемещение атрибута из коллекции **AttributeCollection**, см. в описании [XmlNamedNodeMap.RemoveNamedItem Method](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A).</span><span class="sxs-lookup"><span data-stu-id="33d15-119">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A).</span></span> <span data-ttu-id="33d15-120">Дополнительные сведения о доступных методах и свойствах см. в описании [XmlNamedNodeMap Members](xref:System.Xml.XmlNamedNodeMap).</span><span class="sxs-lookup"><span data-stu-id="33d15-120">For more information on the methods and properties, see [XmlNamedNodeMap Members](xref:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33d15-121">См. также</span><span class="sxs-lookup"><span data-stu-id="33d15-121">See also</span></span>

- [<span data-ttu-id="33d15-122">Модель объектов документов XML (DOM)</span><span class="sxs-lookup"><span data-stu-id="33d15-122">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
