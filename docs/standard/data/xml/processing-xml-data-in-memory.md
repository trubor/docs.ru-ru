---
title: Обработка XML-данных в памяти
ms.date: 03/30/2017
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 878e008f5c7c3a018389e8666263269162989812
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686921"
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="fc309-102">Обработка XML-данных в памяти</span><span class="sxs-lookup"><span data-stu-id="fc309-102">Processing XML Data In-Memory</span></span>

<span data-ttu-id="fc309-103">Платформа Microsoft .NET Framework включает три модели обработки XML-данных: классы <xref:System.Xml.XmlDocument>, класс <xref:System.Xml.XPath.XPathDocument>, а также [LINQ to XML (C#)](../../linq/linq-xml-overview.md) и [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fc309-103">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).</span></span>  
  
 <span data-ttu-id="fc309-104">Класс <xref:System.Xml.XmlDocument> реализует базовую модель DOM W3C 1-го уровня и базовые рекомендации объекта DOM 2-го уровня.</span><span class="sxs-lookup"><span data-stu-id="fc309-104">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="fc309-105">DOM - древовидное представление XML-документа в памяти (кэш).</span><span class="sxs-lookup"><span data-stu-id="fc309-105">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="fc309-106">С помощью <xref:System.Xml.XmlDocument> и связанных классов можно конструировать XML-документы, загружать данные и обращаться к ним, изменять данные и сохранять изменения.</span><span class="sxs-lookup"><span data-stu-id="fc309-106">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="fc309-107">Класс <xref:System.Xml.XPath.XPathDocument> - доступное только для чтения хранилище данных в памяти, на базе модели данных XPath.</span><span class="sxs-lookup"><span data-stu-id="fc309-107">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="fc309-108">В классе <xref:System.Xml.XPath.XPathNavigator> предусмотрено несколько вариантов редактирования и способов навигации с помощью модели курсора для XML-документов в доступном только для чтения классе <xref:System.Xml.XPath.XPathDocument>, а также в классе <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="fc309-108">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="fc309-109">[LINQ to XML](../../linq/linq-xml-overview.md) — это модель для обработки XML-данных, представленная на платформе .NET Framework версии 3.5.</span><span class="sxs-lookup"><span data-stu-id="fc309-109">[LINQ to XML](../../linq/linq-xml-overview.md) is a model introduced in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="fc309-110">Это размещаемая в памяти модель, которая использует синтаксис [LINQ](../../../csharp/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="fc309-110">It's an in-memory model that leverages [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).</span></span> <span data-ttu-id="fc309-111">LINQ расширяет синтаксис C# и Visual Basic, обеспечивая новые возможности запросов.</span><span class="sxs-lookup"><span data-stu-id="fc309-111">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc309-112">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="fc309-112">In This Section</span></span>  

 [<span data-ttu-id="fc309-113">Обработка XML-данных с использованием модели DOM</span><span class="sxs-lookup"><span data-stu-id="fc309-113">Process XML Data Using the DOM Model</span></span>](process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="fc309-114">Описывает использование класса <xref:System.Xml.XmlDocument> и связанных с ним классов для обработки XML-данных.</span><span class="sxs-lookup"><span data-stu-id="fc309-114">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="fc309-115">Обработка XML-данных с использованием модели данных XPath</span><span class="sxs-lookup"><span data-stu-id="fc309-115">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="fc309-116">Описывает использование классов <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument> и <xref:System.Xml.XPath.XPathNavigator> для обработки XML-данных.</span><span class="sxs-lookup"><span data-stu-id="fc309-116">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="fc309-117">Обработка XML-данных с помощью LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="fc309-117">Process XML Data Using LINQ to XML</span></span>](process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="fc309-118">Содержит краткие общие сведения о LINQ to XML и ссылки на документацию LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="fc309-118">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fc309-119">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="fc309-119">Related Sections</span></span>  

 [<span data-ttu-id="fc309-120">XML-документы и данные</span><span class="sxs-lookup"><span data-stu-id="fc309-120">XML Documents and Data</span></span>](index.md)
