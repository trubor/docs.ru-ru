---
description: 'Дополнительные сведения: литерал XML-документа (Visual Basic)'
title: XML-литерал документа
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: d268f205c9357598a631216879b424dd8155268a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700316"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="dba80-103">XML-литерал документа (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dba80-103">XML Document Literal (Visual Basic)</span></span>

<span data-ttu-id="dba80-104">Литерал, представляющий <xref:System.Xml.Linq.XDocument> объект.</span><span class="sxs-lookup"><span data-stu-id="dba80-104">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba80-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dba80-105">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="dba80-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="dba80-106">Parts</span></span>  
  
|<span data-ttu-id="dba80-107">Термин</span><span class="sxs-lookup"><span data-stu-id="dba80-107">Term</span></span>|<span data-ttu-id="dba80-108">Определение</span><span class="sxs-lookup"><span data-stu-id="dba80-108">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="dba80-109">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="dba80-109">Optional.</span></span> <span data-ttu-id="dba80-110">Литеральный текст, объявляющий кодировку, используемую в документе.</span><span class="sxs-lookup"><span data-stu-id="dba80-110">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="dba80-111">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="dba80-111">Optional.</span></span> <span data-ttu-id="dba80-112">Текст литерала.</span><span class="sxs-lookup"><span data-stu-id="dba80-112">Literal text.</span></span> <span data-ttu-id="dba80-113">Значение должно быть "Yes" или "No".</span><span class="sxs-lookup"><span data-stu-id="dba80-113">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="dba80-114">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="dba80-114">Optional.</span></span> <span data-ttu-id="dba80-115">Список инструкций по обработке XML и XML-комментариев.</span><span class="sxs-lookup"><span data-stu-id="dba80-115">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="dba80-116">Принимает следующий формат:</span><span class="sxs-lookup"><span data-stu-id="dba80-116">Takes the following format:</span></span><br /><br /> <span data-ttu-id="dba80-117">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="dba80-117">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="dba80-118">Каждый `piComment` из них может быть одним из следующих:</span><span class="sxs-lookup"><span data-stu-id="dba80-118">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="dba80-119">-   [Литерал инструкции обработки XML](xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="dba80-119">-   [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="dba80-120">-   [XML-литерал комментария](xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="dba80-120">-   [XML Comment Literal](xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="dba80-121">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="dba80-121">Required.</span></span> <span data-ttu-id="dba80-122">Корневой элемент документа.</span><span class="sxs-lookup"><span data-stu-id="dba80-122">Root element of the document.</span></span> <span data-ttu-id="dba80-123">Формат может быть одним из следующих:</span><span class="sxs-lookup"><span data-stu-id="dba80-123">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="dba80-124">[Литерал XML-элемента](xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="dba80-124">[XML Element Literal](xml-element-literal.md).</span></span></li><li><span data-ttu-id="dba80-125">Внедренное выражение формы `<%=` `elementExp` `%>` .</span><span class="sxs-lookup"><span data-stu-id="dba80-125">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="dba80-126">Метод `elementExp` возвращает одно из следующих:</span><span class="sxs-lookup"><span data-stu-id="dba80-126">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="dba80-127">Объект <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="dba80-127">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="dba80-128">Коллекция, содержащая один <xref:System.Xml.Linq.XElement> объект и любое количество <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment> объектов и.</span><span class="sxs-lookup"><span data-stu-id="dba80-128">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="dba80-129">Дополнительные сведения см. [в разделе внедренные выражения в XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dba80-129">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="dba80-130">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dba80-130">Return Value</span></span>  

 <span data-ttu-id="dba80-131">Объект <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="dba80-131">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dba80-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="dba80-132">Remarks</span></span>  

 <span data-ttu-id="dba80-133">Литерал XML-документа определяется XML-объявлением в начале литерала.</span><span class="sxs-lookup"><span data-stu-id="dba80-133">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="dba80-134">Хотя каждый литерал XML-документа должен иметь ровно один корневой XML-элемент, он может иметь любое количество инструкций по обработке XML и XML-комментариев.</span><span class="sxs-lookup"><span data-stu-id="dba80-134">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="dba80-135">Литерал XML-документа не может присутствовать в элементе XML.</span><span class="sxs-lookup"><span data-stu-id="dba80-135">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dba80-136">XML-литерал может охватывать несколько строк без использования символов продолжения строки.</span><span class="sxs-lookup"><span data-stu-id="dba80-136">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="dba80-137">Это позволяет копировать содержимое из XML-документа и вставлять его непосредственно в Visual Basic программу.</span><span class="sxs-lookup"><span data-stu-id="dba80-137">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="dba80-138">Компилятор Visual Basic преобразует литерал XML-документа в вызовы <xref:System.Xml.Linq.XDocument.%23ctor%2A> <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> конструкторов и.</span><span class="sxs-lookup"><span data-stu-id="dba80-138">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dba80-139">Пример</span><span class="sxs-lookup"><span data-stu-id="dba80-139">Example</span></span>  

 <span data-ttu-id="dba80-140">В следующем примере создается XML-документ с XML-объявлением, инструкцией по обработке, комментарием и элементом, содержащим другой элемент.</span><span class="sxs-lookup"><span data-stu-id="dba80-140">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="dba80-141">См. также</span><span class="sxs-lookup"><span data-stu-id="dba80-141">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="dba80-142">XML-литерал инструкции обработки</span><span class="sxs-lookup"><span data-stu-id="dba80-142">XML Processing Instruction Literal</span></span>](xml-processing-instruction-literal.md)
- [<span data-ttu-id="dba80-143">XML-литерал комментария</span><span class="sxs-lookup"><span data-stu-id="dba80-143">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="dba80-144">XML-литерал элемента</span><span class="sxs-lookup"><span data-stu-id="dba80-144">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="dba80-145">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="dba80-145">XML Literals</span></span>](index.md)
- [<span data-ttu-id="dba80-146">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dba80-146">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="dba80-147">Встроенные выражения в XML</span><span class="sxs-lookup"><span data-stu-id="dba80-147">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
