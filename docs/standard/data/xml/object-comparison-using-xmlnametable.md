---
title: Сравнение объектов с помощью XmlNameTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
ms.openlocfilehash: 5e0f5de6fd956bcaaf30b592e04c432a5f824c52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734105"
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="5722b-102">Сравнение объектов с помощью XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="5722b-102">Object Comparison Using XmlNameTable</span></span>

<span data-ttu-id="5722b-103">При создании **XmlDocuments** создается таблица имен специально для этого документа.</span><span class="sxs-lookup"><span data-stu-id="5722b-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="5722b-104">Когда XML загружается в документ или создаются новые элементы и атрибуты, все имена элементов и атрибутов помещаются в **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="5722b-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="5722b-105">Также объект **XmlDocument** можно создать с помощью существующего объекта **NameTable** из другого документа.</span><span class="sxs-lookup"><span data-stu-id="5722b-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="5722b-106">Если **XmlDocuments** создается с помощью конструктора, который принимает параметр **XmlNameTable**, этот документ получает доступ к именам узлов, пространствам имен и префиксам, хранящимся в объекте **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="5722b-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="5722b-107">Независимо от того, насколько таблица имен загружена именами, после сохранения их в таблице эти имена можно быстро сравнить, используя сравнение объектов вместо сравнения строк.</span><span class="sxs-lookup"><span data-stu-id="5722b-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="5722b-108">Еще вы можете добавлять строки в таблицу имен с помощью <xref:System.Xml.NameTable.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="5722b-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="5722b-109">Следующий пример кода демонстрирует создание таблицы имен и добавление к ней строки **MyString**.</span><span class="sxs-lookup"><span data-stu-id="5722b-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="5722b-110">После этого на основе этой таблицы создается объект **XmlDocument**, и к существующей таблице имен добавляются имена элементов и атрибутов из файла **Myfile.xml**.</span><span class="sxs-lookup"><span data-stu-id="5722b-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 <span data-ttu-id="5722b-111">В следующем примере кода показано создание документа, добавление к нему двух новых элементов, имена которых добавляются в таблицу имен, а также сравнение объектов по именам.</span><span class="sxs-lookup"><span data-stu-id="5722b-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 <span data-ttu-id="5722b-112">Приведенный выше сценарий передачи таблицы имен между двумя документами является типичным для многократной обработки документа некоторого типа, совместимого со схемой XSD или определением DTD, в котором многократно повторяются некоторые строки, например, при обработке заказов на веб-узле электронной торговли.</span><span class="sxs-lookup"><span data-stu-id="5722b-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="5722b-113">Применение таблицы имен повышает производительность, поскольку одинаковое имя элемента встречается в нескольких документах.</span><span class="sxs-lookup"><span data-stu-id="5722b-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5722b-114">См. также</span><span class="sxs-lookup"><span data-stu-id="5722b-114">See also</span></span>

- [<span data-ttu-id="5722b-115">Модель объектов документов XML (DOM)</span><span class="sxs-lookup"><span data-stu-id="5722b-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
