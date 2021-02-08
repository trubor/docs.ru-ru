---
description: Дополнительные сведения о свойстве "дочерняя ось XML" (Visual Basic)
title: XML Child Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: 54920ebd35635f215eb6cb58867be1e4a7acd847
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768796"
---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="f1540-103">Свойство дочерней оси XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1540-103">XML Child Axis Property (Visual Basic)</span></span>

<span data-ttu-id="f1540-104">Предоставляет доступ к дочерним элементам одного из следующих: объекта <xref:System.Xml.Linq.XElement>, объекта <xref:System.Xml.Linq.XDocument>, коллекции объектов <xref:System.Xml.Linq.XElement> или коллекции объектов <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="f1540-104">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1540-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f1540-105">Syntax</span></span>  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="f1540-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="f1540-106">Parts</span></span>  
  
|<span data-ttu-id="f1540-107">Термин</span><span class="sxs-lookup"><span data-stu-id="f1540-107">Term</span></span>|<span data-ttu-id="f1540-108">Определение</span><span class="sxs-lookup"><span data-stu-id="f1540-108">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="f1540-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="f1540-109">Required.</span></span> <span data-ttu-id="f1540-110">Объект <xref:System.Xml.Linq.XElement>, объект <xref:System.Xml.Linq.XDocument>, коллекция объектов <xref:System.Xml.Linq.XElement> или коллекция объектов <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="f1540-110">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="f1540-111">. <</span><span class="sxs-lookup"><span data-stu-id="f1540-111">.<</span></span>|<span data-ttu-id="f1540-112">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="f1540-112">Required.</span></span> <span data-ttu-id="f1540-113">Обозначает начало свойства дочерней оси.</span><span class="sxs-lookup"><span data-stu-id="f1540-113">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="f1540-114">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="f1540-114">Required.</span></span> <span data-ttu-id="f1540-115">Имя дочернего узла, к которому осуществляется доступ, в форме `[prefix:]name` .</span><span class="sxs-lookup"><span data-stu-id="f1540-115">Name of the child nodes to access, of the form `[prefix:]name`.</span></span><br /><br /> <span data-ttu-id="f1540-116">-   `Prefix` Используемых.</span><span class="sxs-lookup"><span data-stu-id="f1540-116">-   `Prefix` - Optional.</span></span> <span data-ttu-id="f1540-117">Префикс пространства имен XML для дочернего узла.</span><span class="sxs-lookup"><span data-stu-id="f1540-117">XML namespace prefix for the child node.</span></span> <span data-ttu-id="f1540-118">Должно быть глобальным пространством имен XML, определенным с помощью оператора `Imports`.</span><span class="sxs-lookup"><span data-stu-id="f1540-118">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="f1540-119">-   `Name` Необходимости.</span><span class="sxs-lookup"><span data-stu-id="f1540-119">-   `Name` - Required.</span></span> <span data-ttu-id="f1540-120">Имя локального дочернего узла.</span><span class="sxs-lookup"><span data-stu-id="f1540-120">Local child node name.</span></span> <span data-ttu-id="f1540-121">См. [Имена объявленных XML-элементов и атрибутов](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="f1540-121">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="f1540-122">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="f1540-122">Required.</span></span> <span data-ttu-id="f1540-123">Обозначает конец свойства дочерней оси.</span><span class="sxs-lookup"><span data-stu-id="f1540-123">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="f1540-124">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f1540-124">Return Value</span></span>  

 <span data-ttu-id="f1540-125">Коллекция объектов <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="f1540-125">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1540-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="f1540-126">Remarks</span></span>  

 <span data-ttu-id="f1540-127">Свойство дочерней оси XML можно использовать для доступа к дочерним узлам по имени из объекта <xref:System.Xml.Linq.XElement> или <xref:System.Xml.Linq.XDocument> или из коллекции объектов <xref:System.Xml.Linq.XElement> или <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="f1540-127">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="f1540-128">Используйте XML-свойство `Value` для доступа к значению первого дочернего узла в возвращаемой коллекции.</span><span class="sxs-lookup"><span data-stu-id="f1540-128">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="f1540-129">Дополнительные сведения см. в разделе [свойство значения XML](xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="f1540-129">For more information, see [XML Value Property](xml-value-property.md).</span></span>  
  
 <span data-ttu-id="f1540-130">Компилятор Visual Basic преобразует свойства дочерней оси в вызовы <xref:System.Xml.Linq.XContainer.Elements%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="f1540-130">The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="f1540-131">Пространства имен XML</span><span class="sxs-lookup"><span data-stu-id="f1540-131">XML Namespaces</span></span>  

 <span data-ttu-id="f1540-132">Имя в свойстве дочерней оси может использовать только префиксы пространства имен XML, объявленные глобально с помощью метода `Imports`.</span><span class="sxs-lookup"><span data-stu-id="f1540-132">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="f1540-133">В нем нельзя использовать префиксы пространства имен XML, объявленные локально с помощью литералов XML-элемента.</span><span class="sxs-lookup"><span data-stu-id="f1540-133">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="f1540-134">Дополнительные сведения см. в разделе [оператор Imports (пространство имен XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="f1540-134">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1540-135">Пример</span><span class="sxs-lookup"><span data-stu-id="f1540-135">Example</span></span>  

 <span data-ttu-id="f1540-136">В следующем примере показано, как получить доступ к дочерним узлам `phone` из объекта `contact`.</span><span class="sxs-lookup"><span data-stu-id="f1540-136">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 <span data-ttu-id="f1540-137">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="f1540-137">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="f1540-138">Пример</span><span class="sxs-lookup"><span data-stu-id="f1540-138">Example</span></span>  

 <span data-ttu-id="f1540-139">В следующем примере показано, как получить доступ к дочерним узлам с именем `phone` из коллекции, возвращенной свойством дочерней оси `contact` объекта `contacts`.</span><span class="sxs-lookup"><span data-stu-id="f1540-139">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 <span data-ttu-id="f1540-140">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="f1540-140">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="f1540-141">Пример</span><span class="sxs-lookup"><span data-stu-id="f1540-141">Example</span></span>  

 <span data-ttu-id="f1540-142">В следующем примере `ns` объявляется как префикс пространства имен XML.</span><span class="sxs-lookup"><span data-stu-id="f1540-142">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="f1540-143">Затем префикс пространства имен используется для создания литерала XML и доступа к первому дочернему узлу с полным именем `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="f1540-143">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="f1540-144">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="f1540-144">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="f1540-145">См. также</span><span class="sxs-lookup"><span data-stu-id="f1540-145">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="f1540-146">Свойства оси XML</span><span class="sxs-lookup"><span data-stu-id="f1540-146">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="f1540-147">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="f1540-147">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="f1540-148">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1540-148">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="f1540-149">Имена объявленных элементов и атрибутов XML</span><span class="sxs-lookup"><span data-stu-id="f1540-149">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
