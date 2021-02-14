---
description: Дополнительные сведения см. в статье как получить доступ к элементам-потомкам XML (Visual Basic)
title: Практическое руководство. Доступ к элементам-потомкам XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: d8f3176a91c2f637f49d2754513f3253399ee8ed
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433178"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="aeaf7-103">Практическое руководство. Доступ к производным XML элементам (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aeaf7-103">How to: Access XML Descendant Elements (Visual Basic)</span></span>

<span data-ttu-id="aeaf7-104">В этом примере показано, как использовать свойство оси потомков для доступа ко всем XML-элементам с указанным именем и содержащимся в XML-элементе.</span><span class="sxs-lookup"><span data-stu-id="aeaf7-104">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="aeaf7-105">В частности, он использует `Value` свойство для получения значения первого элемента в коллекции, `name` возвращаемого свойством дочерней оси.</span><span class="sxs-lookup"><span data-stu-id="aeaf7-105">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="aeaf7-106">`name`Свойство дочерняя ось получает все элементы с именем `name` , содержащиеся в `contacts` объекте.</span><span class="sxs-lookup"><span data-stu-id="aeaf7-106">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="aeaf7-107">В этом примере также используется `phone` свойство оси потомков для доступа ко всем потомкам `phone` , имена которых содержатся в `contacts` объекте.</span><span class="sxs-lookup"><span data-stu-id="aeaf7-107">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeaf7-108">Пример</span><span class="sxs-lookup"><span data-stu-id="aeaf7-108">Example</span></span>  

 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="aeaf7-109">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="aeaf7-109">Compile the code</span></span>  

 <span data-ttu-id="aeaf7-110">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="aeaf7-110">This example requires:</span></span>  
  
- <span data-ttu-id="aeaf7-111">ссылка на пространство имен <xref:System.Xml.Linq>.</span><span class="sxs-lookup"><span data-stu-id="aeaf7-111">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeaf7-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="aeaf7-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="aeaf7-113">XML Descendant Axis Property</span><span class="sxs-lookup"><span data-stu-id="aeaf7-113">XML Descendant Axis Property</span></span>](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="aeaf7-114">Свойство значения XML</span><span class="sxs-lookup"><span data-stu-id="aeaf7-114">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="aeaf7-115">Доступ к XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aeaf7-115">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="aeaf7-116">XML</span><span class="sxs-lookup"><span data-stu-id="aeaf7-116">XML</span></span>](index.md)
