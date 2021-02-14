---
description: 'Дополнительные сведения: доступ к XML в Visual Basic'
title: Доступ к XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 2d77b2aa5f4136095ce5684976fe3ba03be7c28c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462663"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="c527d-103">Доступ к XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c527d-103">Accessing XML in Visual Basic</span></span>

<span data-ttu-id="c527d-104">Visual Basic предоставляет свойства осей XML для доступа к структурам и навигации по ним [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c527d-104">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="c527d-105">Эти свойства используют специальный синтаксис, позволяющий получить доступ к элементам и атрибутам, указав имена XML.</span><span class="sxs-lookup"><span data-stu-id="c527d-105">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="c527d-106">В следующей таблице перечислены функции языка, позволяющие получать доступ к XML-элементам и атрибутам в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c527d-106">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="c527d-107">Свойства оси XML</span><span class="sxs-lookup"><span data-stu-id="c527d-107">XML Axis Properties</span></span>  
  
|<span data-ttu-id="c527d-108">Описание свойства</span><span class="sxs-lookup"><span data-stu-id="c527d-108">Property description</span></span>|<span data-ttu-id="c527d-109">Пример</span><span class="sxs-lookup"><span data-stu-id="c527d-109">Example</span></span>|<span data-ttu-id="c527d-110">Описание</span><span class="sxs-lookup"><span data-stu-id="c527d-110">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="c527d-111">*дочерняя ось*</span><span class="sxs-lookup"><span data-stu-id="c527d-111">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="c527d-112">Возвращает все `phone` элементы, являющиеся дочерними элементами `contact` элемента.</span><span class="sxs-lookup"><span data-stu-id="c527d-112">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="c527d-113">*attribute, ось*</span><span class="sxs-lookup"><span data-stu-id="c527d-113">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="c527d-114">Возвращает все `type` атрибуты `phone` элемента.</span><span class="sxs-lookup"><span data-stu-id="c527d-114">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="c527d-115">*descendant, ось*</span><span class="sxs-lookup"><span data-stu-id="c527d-115">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="c527d-116">Возвращает все `name` элементы `contacts` элемента, независимо от того, насколько глубоко в иерархии они выполняются.</span><span class="sxs-lookup"><span data-stu-id="c527d-116">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="c527d-117">*индексатор расширения*</span><span class="sxs-lookup"><span data-stu-id="c527d-117">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="c527d-118">Возвращает первый `name` элемент из последовательности.</span><span class="sxs-lookup"><span data-stu-id="c527d-118">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="c527d-119">*value*</span><span class="sxs-lookup"><span data-stu-id="c527d-119">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="c527d-120">Возвращает строковое представление первого объекта в последовательности или `Nothing` значение, если последовательность пуста.</span><span class="sxs-lookup"><span data-stu-id="c527d-120">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="c527d-121">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="c527d-121">In This Section</span></span>  

 [<span data-ttu-id="c527d-122">Практическое руководство. Доступ к элементам-потомкам XML</span><span class="sxs-lookup"><span data-stu-id="c527d-122">How to: Access XML Descendant Elements</span></span>](how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="c527d-123">Показывает, как использовать свойство оси потомков для доступа ко всем XML-элементам с указанным именем и содержащимся в указанном XML-элементе.</span><span class="sxs-lookup"><span data-stu-id="c527d-123">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="c527d-124">Практическое руководство. Доступ к дочерним XML-элементам</span><span class="sxs-lookup"><span data-stu-id="c527d-124">How to: Access XML Child Elements</span></span>](how-to-access-xml-child-elements.md)  
 <span data-ttu-id="c527d-125">Показывает, как использовать свойство дочерней оси для доступа ко всем дочерним элементам XML с указанным именем в элементе XML.</span><span class="sxs-lookup"><span data-stu-id="c527d-125">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="c527d-126">Практическое руководство. Доступ к XML-атрибутам</span><span class="sxs-lookup"><span data-stu-id="c527d-126">How to: Access XML Attributes</span></span>](how-to-access-xml-attributes.md)  
 <span data-ttu-id="c527d-127">Показывает, как использовать свойство оси атрибута для доступа ко всем XML-атрибутам, имеющим указанное имя в элементе XML.</span><span class="sxs-lookup"><span data-stu-id="c527d-127">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="c527d-128">Практическое руководство. Объявление и использование префиксов пространств имен XML</span><span class="sxs-lookup"><span data-stu-id="c527d-128">How to: Declare and Use XML Namespace Prefixes</span></span>](how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="c527d-129">Показывает, как объявить префикс пространства имен XML и использовать его для создания и доступа к XML-элементам.</span><span class="sxs-lookup"><span data-stu-id="c527d-129">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c527d-130">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="c527d-130">Related Sections</span></span>  

 [<span data-ttu-id="c527d-131">Свойства оси XML</span><span class="sxs-lookup"><span data-stu-id="c527d-131">XML Axis Properties</span></span>](../../../language-reference/xml-axis/index.md)  
 <span data-ttu-id="c527d-132">Содержит ссылки на разделы, описывающие различные свойства доступа к XML.</span><span class="sxs-lookup"><span data-stu-id="c527d-132">Provides links to sections describing the various XML access properties.</span></span>  
  
 <span data-ttu-id="c527d-133">[Overview of LINQ to XML in Visual Basic](overview-of-linq-to-xml.md) (Общие сведения о LINQ to XML в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c527d-133">[Overview of LINQ to XML in Visual Basic](overview-of-linq-to-xml.md)</span></span>  
 <span data-ttu-id="c527d-134">Общие сведения об использовании [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c527d-134">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="c527d-135">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c527d-135">Creating XML in Visual Basic</span></span>](creating-xml.md)  
 <span data-ttu-id="c527d-136">Общие сведения об использовании литералов XML в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c527d-136">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="c527d-137">Обработка XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c527d-137">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)  
 <span data-ttu-id="c527d-138">Содержит ссылки на разделы, посвященные загрузке и изменению XML в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c527d-138">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="c527d-139">XML</span><span class="sxs-lookup"><span data-stu-id="c527d-139">XML</span></span>](index.md)  
 <span data-ttu-id="c527d-140">Содержит ссылки на разделы, описывающие использование [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c527d-140">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
