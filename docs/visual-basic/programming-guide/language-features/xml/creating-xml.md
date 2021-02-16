---
description: 'Дополнительные сведения: создание XML в Visual Basic'
title: Создание XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: 9511253791720d1f45e00669b0abc41a45237f63
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100431650"
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="efd9d-103">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="efd9d-103">Creating XML in Visual Basic</span></span>

<span data-ttu-id="efd9d-104">Visual Basic позволяет использовать *XML-литералы* непосредственно в коде.</span><span class="sxs-lookup"><span data-stu-id="efd9d-104">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="efd9d-105">Синтаксис XML-литерала представляет [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] объекты и аналогичен синтаксису xml 1,0.</span><span class="sxs-lookup"><span data-stu-id="efd9d-105">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="efd9d-106">Это упрощает создание XML-элементов, документов и фрагментов программным способом, так как код имеет ту же структуру, что и окончательный XML.</span><span class="sxs-lookup"><span data-stu-id="efd9d-106">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="efd9d-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="efd9d-107">In This Section</span></span>  
  
|<span data-ttu-id="efd9d-108">Термин</span><span class="sxs-lookup"><span data-stu-id="efd9d-108">Term</span></span>|<span data-ttu-id="efd9d-109">Определение</span><span class="sxs-lookup"><span data-stu-id="efd9d-109">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="efd9d-110">Общие сведения об XML-литералах</span><span class="sxs-lookup"><span data-stu-id="efd9d-110">XML Literals Overview</span></span>](xml-literals-overview.md)|<span data-ttu-id="efd9d-111">Общие сведения о XML-литералах и их связи с [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="efd9d-111">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="efd9d-112">Встроенные выражения в XML</span><span class="sxs-lookup"><span data-stu-id="efd9d-112">Embedded Expressions in XML</span></span>](embedded-expressions-in-xml.md)|<span data-ttu-id="efd9d-113">Описывает использование внедренных выражений в XML-литералах.</span><span class="sxs-lookup"><span data-stu-id="efd9d-113">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="efd9d-114">Практическое руководство. Создание XML-литералов</span><span class="sxs-lookup"><span data-stu-id="efd9d-114">How to: Create XML Literals</span></span>](how-to-create-xml-literals.md)|<span data-ttu-id="efd9d-115">Описывает создание XML-элемента в коде с помощью XML-литерала.</span><span class="sxs-lookup"><span data-stu-id="efd9d-115">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="efd9d-116">Пробелы в XML-литералах</span><span class="sxs-lookup"><span data-stu-id="efd9d-116">White Space in XML Literals</span></span>](white-space-in-xml-literals.md)|<span data-ttu-id="efd9d-117">Описывает, как Visual Basic обрабатывает пробелы в XML-литералах.</span><span class="sxs-lookup"><span data-stu-id="efd9d-117">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="efd9d-118">XML-литералы и спецификация XML 1.0</span><span class="sxs-lookup"><span data-stu-id="efd9d-118">XML Literals and the XML 1.0 Specification</span></span>](xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="efd9d-119">Описывает, как синтаксис XML-литерала в Visual Basic относится к спецификации XML 1,0.</span><span class="sxs-lookup"><span data-stu-id="efd9d-119">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="efd9d-120">Практическое руководство. Внедрение выражений в XML-литералы</span><span class="sxs-lookup"><span data-stu-id="efd9d-120">How to: Embed Expressions in XML Literals</span></span>](how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="efd9d-121">Описывает использование внедренных выражений в XML-литералах для создания содержимого во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="efd9d-121">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="efd9d-122">Имена объявленных элементов и атрибутов XML</span><span class="sxs-lookup"><span data-stu-id="efd9d-122">Names of Declared XML Elements and Attributes</span></span>](names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="efd9d-123">Описывает правила именования XML-элементов и атрибутов.</span><span class="sxs-lookup"><span data-stu-id="efd9d-123">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efd9d-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="efd9d-124">See also</span></span>

- [<span data-ttu-id="efd9d-125">XML</span><span class="sxs-lookup"><span data-stu-id="efd9d-125">XML</span></span>](index.md)
