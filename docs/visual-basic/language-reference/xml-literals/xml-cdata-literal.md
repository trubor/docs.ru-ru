---
description: Дополнительные сведения см. в XML-литерале CDATA (Visual Basic)
title: XML-литерал CDATA
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: d0b419954acb5a9e8ae824dbac8234e2116d09b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768757"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="0db16-103">Литеральное представление XML-раздела CDATA (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0db16-103">XML CDATA Literal (Visual Basic)</span></span>

<span data-ttu-id="0db16-104">Литерал, представляющий <xref:System.Xml.Linq.XCData> объект.</span><span class="sxs-lookup"><span data-stu-id="0db16-104">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0db16-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0db16-105">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="0db16-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="0db16-106">Parts</span></span>  

 `<![CDATA[`  
 <span data-ttu-id="0db16-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0db16-107">Required.</span></span> <span data-ttu-id="0db16-108">Обозначает начало раздела XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="0db16-108">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="0db16-109">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0db16-109">Required.</span></span> <span data-ttu-id="0db16-110">Текстовое содержимое, отображаемое в разделе CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="0db16-110">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="0db16-111">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0db16-111">Required.</span></span> <span data-ttu-id="0db16-112">Обозначает конец раздела.</span><span class="sxs-lookup"><span data-stu-id="0db16-112">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0db16-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0db16-113">Return Value</span></span>  

 <span data-ttu-id="0db16-114">Объект <xref:System.Xml.Linq.XCData>.</span><span class="sxs-lookup"><span data-stu-id="0db16-114">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0db16-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="0db16-115">Remarks</span></span>  

 <span data-ttu-id="0db16-116">Разделы XML CDATA содержат необработанный текст, который должен быть добавлен, но не проанализирован, с XML-кодом, содержащим его.</span><span class="sxs-lookup"><span data-stu-id="0db16-116">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="0db16-117">Раздел CDATA XML может содержать любой текст.</span><span class="sxs-lookup"><span data-stu-id="0db16-117">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="0db16-118">Сюда входят зарезервированные символы XML.</span><span class="sxs-lookup"><span data-stu-id="0db16-118">This includes reserved XML characters.</span></span> <span data-ttu-id="0db16-119">Раздел CDATA XML заканчивается последовательностью "]] >".</span><span class="sxs-lookup"><span data-stu-id="0db16-119">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="0db16-120">Это подразумевает следующие моменты:</span><span class="sxs-lookup"><span data-stu-id="0db16-120">This implies the following points:</span></span>  
  
- <span data-ttu-id="0db16-121">Нельзя использовать внедренное выражение в XML-литерале CDATA, так как разделители внедренных выражений являются допустимыми содержимым XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="0db16-121">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="0db16-122">Разделы CDATA XML не могут быть вложенными, поскольку `content` не могут содержать значение "]] >".</span><span class="sxs-lookup"><span data-stu-id="0db16-122">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="0db16-123">Можно назначить литерал XML CDATA переменной или включить его в литерал XML-элемента.</span><span class="sxs-lookup"><span data-stu-id="0db16-123">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0db16-124">XML-литерал может охватывать несколько строк, но не использует символы продолжения строки.</span><span class="sxs-lookup"><span data-stu-id="0db16-124">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="0db16-125">Это позволяет копировать содержимое из XML-документа и вставлять его непосредственно в Visual Basic программу.</span><span class="sxs-lookup"><span data-stu-id="0db16-125">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="0db16-126">Компилятор Visual Basic преобразует литерал CDATA XML в вызов <xref:System.Xml.Linq.XCData.%23ctor%2A> конструктора.</span><span class="sxs-lookup"><span data-stu-id="0db16-126">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0db16-127">Пример</span><span class="sxs-lookup"><span data-stu-id="0db16-127">Example</span></span>  

 <span data-ttu-id="0db16-128">В следующем примере создается раздел CDATA, содержащий текст "может содержать литеральные \<XML> теги".</span><span class="sxs-lookup"><span data-stu-id="0db16-128">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="0db16-129">См. также</span><span class="sxs-lookup"><span data-stu-id="0db16-129">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="0db16-130">XML-литерал элемента</span><span class="sxs-lookup"><span data-stu-id="0db16-130">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="0db16-131">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="0db16-131">XML Literals</span></span>](index.md)
- [<span data-ttu-id="0db16-132">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0db16-132">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
