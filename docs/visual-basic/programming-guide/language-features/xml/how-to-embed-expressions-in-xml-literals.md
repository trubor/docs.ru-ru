---
description: 'Дополнительные сведения о: инструкции по внедрению выражений в XML-литералы (Visual Basic)'
title: Практическое руководство. Внедрение выражений в XML-литералы
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 18bc6164c4466532956f1a5df70c1ff2a8dbbfd5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480054"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="fa2ee-103">Практическое руководство. Внедрение выражений в XML-литералы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa2ee-103">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>

<span data-ttu-id="fa2ee-104">Литералы XML можно объединять с внедренными выражениями для создания XML-документа, фрагмента или элемента, содержащего содержимое, созданное во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-104">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="fa2ee-105">В следующих примерах показано, как использовать внедренные выражения для заполнения содержимого, атрибутов и имен элементов во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-105">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="fa2ee-106">Синтаксис для внедренного выражения — это тот `<%=` `exp` `%>` же синтаксис, который используется ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-106">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that ASP.NET uses.</span></span> <span data-ttu-id="fa2ee-107">Дополнительные сведения см. [в разделе внедренные выражения в XML](embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fa2ee-107">For more information, see [Embedded Expressions in XML](embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="fa2ee-108">Вы также можете использовать [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API для создания [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] объектов.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-108">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="fa2ee-109">Для получения дополнительной информации см. <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-109">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="fa2ee-110">Процедуры</span><span class="sxs-lookup"><span data-stu-id="fa2ee-110">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="fa2ee-111">Вставка текста в качестве содержимого элемента</span><span class="sxs-lookup"><span data-stu-id="fa2ee-111">To insert text as element content</span></span>  
  
- <span data-ttu-id="fa2ee-112">В следующем примере показано, как вставить текст, содержащийся в переменной, `contactName` между открывающим и закрывающим элементами Name.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-112">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     <span data-ttu-id="fa2ee-113">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="fa2ee-113">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="fa2ee-114">Вставка текста в качестве значения атрибута</span><span class="sxs-lookup"><span data-stu-id="fa2ee-114">To insert text as an attribute value</span></span>  
  
- <span data-ttu-id="fa2ee-115">В следующем примере показано, как вставить текст, содержащийся в переменной, в `phoneType` качестве значения `type` атрибута.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-115">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     <span data-ttu-id="fa2ee-116">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="fa2ee-116">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="fa2ee-117">Вставка текста для имени элемента</span><span class="sxs-lookup"><span data-stu-id="fa2ee-117">To insert text for an element name</span></span>  
  
- <span data-ttu-id="fa2ee-118">В следующем примере показано, как вставить текст, содержащийся в переменной, в `elementName` качестве имени элемента.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-118">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="fa2ee-119">При создании элементов с помощью этого метода их необходимо закрыть с помощью \</> тега.</span><span class="sxs-lookup"><span data-stu-id="fa2ee-119">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     <span data-ttu-id="fa2ee-120">В этом примере выводятся следующие данные:</span><span class="sxs-lookup"><span data-stu-id="fa2ee-120">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fa2ee-121">См. также</span><span class="sxs-lookup"><span data-stu-id="fa2ee-121">See also</span></span>

- [<span data-ttu-id="fa2ee-122">Практическое руководство. Создание XML-литералов</span><span class="sxs-lookup"><span data-stu-id="fa2ee-122">How to: Create XML Literals</span></span>](how-to-create-xml-literals.md)
- [<span data-ttu-id="fa2ee-123">Встроенные выражения в XML</span><span class="sxs-lookup"><span data-stu-id="fa2ee-123">Embedded Expressions in XML</span></span>](embedded-expressions-in-xml.md)
- [<span data-ttu-id="fa2ee-124">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fa2ee-124">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="fa2ee-125">XML</span><span class="sxs-lookup"><span data-stu-id="fa2ee-125">XML</span></span>](index.md)
