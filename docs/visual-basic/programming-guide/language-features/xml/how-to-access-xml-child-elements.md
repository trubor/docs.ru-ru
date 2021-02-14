---
description: 'Дополнительные сведения: как получить доступ к дочерним элементам XML (Visual Basic)'
title: Практическое руководство. Доступ к дочерним XML-элементам
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: fad4d45853006762bc319b0ff8f9143ef13058da
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433243"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="7f7b7-103">Практическое руководство. Доступ к дочерним XML-элементам (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f7b7-103">How to: Access XML Child Elements (Visual Basic)</span></span>

<span data-ttu-id="7f7b7-104">В этом примере показано, как использовать свойство дочерней оси для доступа ко всем дочерним элементам XML с указанным именем в элементе XML.</span><span class="sxs-lookup"><span data-stu-id="7f7b7-104">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="7f7b7-105">В частности, он использует <xref:System.Xml.Linq.XElement.Value%2A> свойство для получения значения первого элемента в коллекции, `name` возвращаемого свойством дочерней оси.</span><span class="sxs-lookup"><span data-stu-id="7f7b7-105">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="7f7b7-106">`name`Свойство дочерней оси получает все дочерние элементы с именем `phone` в `contact` объекте.</span><span class="sxs-lookup"><span data-stu-id="7f7b7-106">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="7f7b7-107">В этом примере также используется `phone` свойство дочерней оси для доступа ко всем дочерним элементам с именем `phone` , содержащимся в `contact` объекте.</span><span class="sxs-lookup"><span data-stu-id="7f7b7-107">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f7b7-108">Пример</span><span class="sxs-lookup"><span data-stu-id="7f7b7-108">Example</span></span>  

 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="7f7b7-109">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="7f7b7-109">Compile the code</span></span>  

 <span data-ttu-id="7f7b7-110">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="7f7b7-110">This example requires:</span></span>  
  
- <span data-ttu-id="7f7b7-111">ссылка на пространство имен <xref:System.Xml.Linq>.</span><span class="sxs-lookup"><span data-stu-id="7f7b7-111">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f7b7-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7f7b7-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7f7b7-113">XML Child Axis Property</span><span class="sxs-lookup"><span data-stu-id="7f7b7-113">XML Child Axis Property</span></span>](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="7f7b7-114">Свойство значения XML</span><span class="sxs-lookup"><span data-stu-id="7f7b7-114">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="7f7b7-115">Доступ к XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7f7b7-115">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="7f7b7-116">XML</span><span class="sxs-lookup"><span data-stu-id="7f7b7-116">XML</span></span>](index.md)
