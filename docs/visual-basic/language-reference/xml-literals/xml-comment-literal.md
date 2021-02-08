---
description: 'Дополнительные сведения: XML-литерал комментария (Visual Basic)'
title: XML-литерал комментария
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: f44d2e132236d74d312910921fabb3a85afd82d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768744"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="b60c7-103">XML-литерал комментариев (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b60c7-103">XML Comment Literal (Visual Basic)</span></span>

<span data-ttu-id="b60c7-104">Литерал, представляющий <xref:System.Xml.Linq.XComment> объект.</span><span class="sxs-lookup"><span data-stu-id="b60c7-104">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b60c7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b60c7-105">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="b60c7-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="b60c7-106">Parts</span></span>  
  
|<span data-ttu-id="b60c7-107">Термин</span><span class="sxs-lookup"><span data-stu-id="b60c7-107">Term</span></span>|<span data-ttu-id="b60c7-108">Определение</span><span class="sxs-lookup"><span data-stu-id="b60c7-108">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="b60c7-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="b60c7-109">Required.</span></span> <span data-ttu-id="b60c7-110">Обозначает начало XML-комментария.</span><span class="sxs-lookup"><span data-stu-id="b60c7-110">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="b60c7-111">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="b60c7-111">Required.</span></span> <span data-ttu-id="b60c7-112">Текст, отображаемый в XML-комментарии.</span><span class="sxs-lookup"><span data-stu-id="b60c7-112">Text to appear in the XML comment.</span></span> <span data-ttu-id="b60c7-113">Не может содержать последовательность из двух дефисов (--) или заканчиваться дефисом, рядом с закрывающим тегом.</span><span class="sxs-lookup"><span data-stu-id="b60c7-113">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="b60c7-114">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="b60c7-114">Required.</span></span> <span data-ttu-id="b60c7-115">Обозначает конец XML-комментария.</span><span class="sxs-lookup"><span data-stu-id="b60c7-115">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="b60c7-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b60c7-116">Return Value</span></span>  

 <span data-ttu-id="b60c7-117">Объект <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="b60c7-117">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b60c7-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="b60c7-118">Remarks</span></span>  

 <span data-ttu-id="b60c7-119">Литералы XML-комментариев не содержат содержимого документа; они содержат сведения о документе.</span><span class="sxs-lookup"><span data-stu-id="b60c7-119">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="b60c7-120">Раздел комментария XML заканчивается последовательностью "-->".</span><span class="sxs-lookup"><span data-stu-id="b60c7-120">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="b60c7-121">Это подразумевает следующие моменты:</span><span class="sxs-lookup"><span data-stu-id="b60c7-121">This implies the following points:</span></span>  
  
- <span data-ttu-id="b60c7-122">Нельзя использовать внедренное выражение в литерале XML-комментария, так как разделители внедренных выражений являются допустимым содержимым XML-комментариев.</span><span class="sxs-lookup"><span data-stu-id="b60c7-122">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
- <span data-ttu-id="b60c7-123">Разделы комментариев XML не могут быть вложенными, поскольку `content` не могут содержать значение "-->".</span><span class="sxs-lookup"><span data-stu-id="b60c7-123">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="b60c7-124">Литерал комментария XML можно назначить переменной или включить в литерал XML-элемента.</span><span class="sxs-lookup"><span data-stu-id="b60c7-124">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b60c7-125">XML-литерал может охватывать несколько строк без использования символов продолжения строки.</span><span class="sxs-lookup"><span data-stu-id="b60c7-125">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="b60c7-126">Эта функция позволяет копировать содержимое из XML-документа и вставлять его непосредственно в Visual Basic программу.</span><span class="sxs-lookup"><span data-stu-id="b60c7-126">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="b60c7-127">Компилятор Visual Basic преобразует литерал XML-комментария в вызов <xref:System.Xml.Linq.XComment.%23ctor%2A> конструктора.</span><span class="sxs-lookup"><span data-stu-id="b60c7-127">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b60c7-128">Пример</span><span class="sxs-lookup"><span data-stu-id="b60c7-128">Example</span></span>  

 <span data-ttu-id="b60c7-129">В следующем примере создается XML-комментарий, содержащий текст "это комментарий".</span><span class="sxs-lookup"><span data-stu-id="b60c7-129">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="b60c7-130">См. также</span><span class="sxs-lookup"><span data-stu-id="b60c7-130">See also</span></span>

- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="b60c7-131">XML-литерал элемента</span><span class="sxs-lookup"><span data-stu-id="b60c7-131">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="b60c7-132">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="b60c7-132">XML Literals</span></span>](index.md)
- [<span data-ttu-id="b60c7-133">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b60c7-133">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
