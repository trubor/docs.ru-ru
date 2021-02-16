---
description: Дополнительные сведения см. в статье Создание XML-литералов (Visual Basic).
title: Практическое руководство. Создание XML-литералов
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 0e57b037d0567002fd570025e147771c4fab38f4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433295"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="1441f-103">Практическое руководство. Создание XML-литералов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1441f-103">How to: Create XML Literals (Visual Basic)</span></span>

<span data-ttu-id="1441f-104">XML-документ, фрагмент или элемент можно создать непосредственно в коде с помощью XML-литерала.</span><span class="sxs-lookup"><span data-stu-id="1441f-104">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="1441f-105">В примерах этого раздела показано, как создать XML-элемент с тремя дочерними элементами и как создать XML-документ.</span><span class="sxs-lookup"><span data-stu-id="1441f-105">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="1441f-106">Вы также можете использовать [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API для создания [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] объектов.</span><span class="sxs-lookup"><span data-stu-id="1441f-106">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="1441f-107">Для получения дополнительной информации см. <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="1441f-107">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="1441f-108">Создание XML-элемента</span><span class="sxs-lookup"><span data-stu-id="1441f-108">To create an XML element</span></span>  
  
- <span data-ttu-id="1441f-109">Создайте встроенный XML-файл с помощью синтаксиса XML-литерала, который совпадает с фактическим синтаксисом XML.</span><span class="sxs-lookup"><span data-stu-id="1441f-109">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     <span data-ttu-id="1441f-110">Выполните код.</span><span class="sxs-lookup"><span data-stu-id="1441f-110">Run the code.</span></span> <span data-ttu-id="1441f-111">Выходные данные этого кода:</span><span class="sxs-lookup"><span data-stu-id="1441f-111">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="1441f-112">Создание XML-документа</span><span class="sxs-lookup"><span data-stu-id="1441f-112">To create an XML document</span></span>  
  
- <span data-ttu-id="1441f-113">Создайте встроенный XML-документ.</span><span class="sxs-lookup"><span data-stu-id="1441f-113">Create the XML document inline.</span></span> <span data-ttu-id="1441f-114">Следующий код создает XML-документ с литеральным синтаксисом, объявлением XML, инструкцией по обработке, комментарием и элементом, содержащим другой элемент.</span><span class="sxs-lookup"><span data-stu-id="1441f-114">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     <span data-ttu-id="1441f-115">Выполните код.</span><span class="sxs-lookup"><span data-stu-id="1441f-115">Run the code.</span></span> <span data-ttu-id="1441f-116">Выходные данные этого кода:</span><span class="sxs-lookup"><span data-stu-id="1441f-116">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="1441f-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="1441f-117">See also</span></span>

- [<span data-ttu-id="1441f-118">XML</span><span class="sxs-lookup"><span data-stu-id="1441f-118">XML</span></span>](index.md)
- [<span data-ttu-id="1441f-119">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1441f-119">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="1441f-120">XML-литерал элемента</span><span class="sxs-lookup"><span data-stu-id="1441f-120">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="1441f-121">XML-литерал документа</span><span class="sxs-lookup"><span data-stu-id="1441f-121">XML Document Literal</span></span>](../../../language-reference/xml-literals/xml-document-literal.md)
