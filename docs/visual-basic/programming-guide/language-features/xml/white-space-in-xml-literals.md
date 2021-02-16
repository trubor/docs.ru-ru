---
description: 'Подробнее: пробелы в XML-литералах (Visual Basic)'
title: Пробелы в XML-литералах
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 9b4134626c0ad1f7f4be2923573eb6058fa7687f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428120"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="cfed3-103">Пробелы в XML-литералах (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfed3-103">White Space in XML Literals (Visual Basic)</span></span>

<span data-ttu-id="cfed3-104">Компилятор Visual Basic включает только значащие символы пробела из XML-литерала при создании [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] объекта.</span><span class="sxs-lookup"><span data-stu-id="cfed3-104">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="cfed3-105">Незначащие символы пробела не включаются.</span><span class="sxs-lookup"><span data-stu-id="cfed3-105">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="cfed3-106">Значительные и незначащие пробелы</span><span class="sxs-lookup"><span data-stu-id="cfed3-106">Significant and Insignificant White Space</span></span>  

 <span data-ttu-id="cfed3-107">Символы пробелов в XML-литералах являются значимыми только в трех областях:</span><span class="sxs-lookup"><span data-stu-id="cfed3-107">White space characters in XML literals are significant in only three areas:</span></span>  
  
- <span data-ttu-id="cfed3-108">Если они находятся в значении атрибута.</span><span class="sxs-lookup"><span data-stu-id="cfed3-108">When they are in an attribute value.</span></span>  
  
- <span data-ttu-id="cfed3-109">Если они являются частью текстового содержимого элемента, а текст также содержит другие символы.</span><span class="sxs-lookup"><span data-stu-id="cfed3-109">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
- <span data-ttu-id="cfed3-110">Если они находятся в внедренном выражении для текстового содержимого элемента.</span><span class="sxs-lookup"><span data-stu-id="cfed3-110">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="cfed3-111">В противном случае компилятор рассматривает символы пробела как незначащие и не включает в [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] объект для литерала.</span><span class="sxs-lookup"><span data-stu-id="cfed3-111">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="cfed3-112">Чтобы включить незначащие пробелы в XML-литерал, используйте внедренное выражение, содержащее строковый литерал с пробелом.</span><span class="sxs-lookup"><span data-stu-id="cfed3-112">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cfed3-113">Если `xml:space` атрибут отображается в литерале XML-элемента, Visual Basic компилятор включает атрибут в <xref:System.Xml.Linq.XElement> объект, но добавление этого атрибута не влияет на то, как компилятор обрабатывает пробелы.</span><span class="sxs-lookup"><span data-stu-id="cfed3-113">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cfed3-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="cfed3-114">Examples</span></span>  

 <span data-ttu-id="cfed3-115">В следующем примере содержатся два XML-элемента: OUTER и Inner.</span><span class="sxs-lookup"><span data-stu-id="cfed3-115">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="cfed3-116">Оба элемента содержат пробелы в текстовом содержимом.</span><span class="sxs-lookup"><span data-stu-id="cfed3-116">Both elements contain white space in their text content.</span></span> <span data-ttu-id="cfed3-117">Пробелы во внешнем элементе являются незначащими, так как содержат только пробелы и XML-элементы.</span><span class="sxs-lookup"><span data-stu-id="cfed3-117">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="cfed3-118">Пробел во внутреннем элементе важен, так как он содержит пробелы и текст.</span><span class="sxs-lookup"><span data-stu-id="cfed3-118">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 <span data-ttu-id="cfed3-119">При запуске этот код отображает следующий текст.</span><span class="sxs-lookup"><span data-stu-id="cfed3-119">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cfed3-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="cfed3-120">See also</span></span>

- [<span data-ttu-id="cfed3-121">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cfed3-121">Creating XML in Visual Basic</span></span>](creating-xml.md)
