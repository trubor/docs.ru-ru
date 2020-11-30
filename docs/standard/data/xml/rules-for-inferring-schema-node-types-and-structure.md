---
title: Правила выведения структуры и типов узлов схемы
ms.date: 03/30/2017
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
ms.openlocfilehash: e49e50dc21951d739b12cdfa60c6a48f67576873
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697601"
---
# <a name="rules-for-inferring-schema-node-types-and-structure"></a><span data-ttu-id="8bf74-102">Правила выведения структуры и типов узлов схемы</span><span class="sxs-lookup"><span data-stu-id="8bf74-102">Rules for Inferring Schema Node Types and Structure</span></span>

<span data-ttu-id="8bf74-103">В данном разделе описывается, как в процессе вывода схемы различные типы узлов XML-документа преобразуются в структуру языка XSD.</span><span class="sxs-lookup"><span data-stu-id="8bf74-103">This topic describes how the schema inference process translates the node types in an XML document to an XML Schema definition language (XSD) structure.</span></span>  
  
## <a name="element-inference-rules"></a><span data-ttu-id="8bf74-104">Правила вывода элементов</span><span class="sxs-lookup"><span data-stu-id="8bf74-104">Element Inference Rules</span></span>  

 <span data-ttu-id="8bf74-105">В данном разделе описаны правила вывода для декларации элементов.</span><span class="sxs-lookup"><span data-stu-id="8bf74-105">This section describes the inference rules for element declarations.</span></span> <span data-ttu-id="8bf74-106">Могут быть выведены восемь структур деклараций элементов.</span><span class="sxs-lookup"><span data-stu-id="8bf74-106">There are eight structures of element declarations that will be inferred:</span></span>  
  
1. <span data-ttu-id="8bf74-107">Элемент простого типа</span><span class="sxs-lookup"><span data-stu-id="8bf74-107">Element of simple type</span></span>  
  
2. <span data-ttu-id="8bf74-108">Пустой элемент</span><span class="sxs-lookup"><span data-stu-id="8bf74-108">Empty element</span></span>  
  
3. <span data-ttu-id="8bf74-109">Пустой элемент с атрибутами</span><span class="sxs-lookup"><span data-stu-id="8bf74-109">Empty element with attributes</span></span>  
  
4. <span data-ttu-id="8bf74-110">Элемент с атрибутами и простым содержимым</span><span class="sxs-lookup"><span data-stu-id="8bf74-110">Element with attributes and simple content</span></span>  
  
5. <span data-ttu-id="8bf74-111">Элемент с последовательностью дочерних элементов</span><span class="sxs-lookup"><span data-stu-id="8bf74-111">Element with a sequence of child elements</span></span>  
  
6. <span data-ttu-id="8bf74-112">Элемент с последовательностью дочерних элементов и атрибутов</span><span class="sxs-lookup"><span data-stu-id="8bf74-112">Element with a sequence of child elements and attributes</span></span>  
  
7. <span data-ttu-id="8bf74-113">Элемент с последовательностью выборов дочерних элементов</span><span class="sxs-lookup"><span data-stu-id="8bf74-113">Element with a sequence of choices of child elements</span></span>  
  
8. <span data-ttu-id="8bf74-114">Элемент с последовательностью выборов дочерних элементов и атрибутов</span><span class="sxs-lookup"><span data-stu-id="8bf74-114">Element with a sequence of choices of child elements and attributes</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8bf74-115">Все декларации элементов `complexType` выводятся как анонимные типы.</span><span class="sxs-lookup"><span data-stu-id="8bf74-115">All `complexType` declarations are inferred as anonymous types.</span></span> <span data-ttu-id="8bf74-116">Единственный выводимый глобальный элемент - корневой элемент; все остальные элементы локальны.</span><span class="sxs-lookup"><span data-stu-id="8bf74-116">The only global element inferred is the root element; all other elements are local.</span></span>  
  
 <span data-ttu-id="8bf74-117">См. дополнительные сведения о [выведении схем из XML-документов](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="8bf74-117">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
### <a name="simple-typed-element"></a><span data-ttu-id="8bf74-118">Простой типизированный элемент</span><span class="sxs-lookup"><span data-stu-id="8bf74-118">Simple Typed Element</span></span>  

 <span data-ttu-id="8bf74-119">В следующей таблице показаны входные XML-данные для метода <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> и созданная XML-схема.</span><span class="sxs-lookup"><span data-stu-id="8bf74-119">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="8bf74-120">Элемент, выделенный полужирным шрифтом, показывает схему, выведенную для элемента простого типа.</span><span class="sxs-lookup"><span data-stu-id="8bf74-120">The bolded element shows the schema inferred for the simple type element.</span></span>  
  
 <span data-ttu-id="8bf74-121">См. дополнительные сведения о [выведении схем из XML-документов](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="8bf74-121">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="8bf74-122">XML</span><span class="sxs-lookup"><span data-stu-id="8bf74-122">XML</span></span>|<span data-ttu-id="8bf74-123">Схема</span><span class="sxs-lookup"><span data-stu-id="8bf74-123">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root" type="xs:string" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element"></a><span data-ttu-id="8bf74-124">Пустой элемент</span><span class="sxs-lookup"><span data-stu-id="8bf74-124">Empty Element</span></span>  

 <span data-ttu-id="8bf74-125">В следующей таблице показаны входные XML-данные для метода <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> и созданная XML-схема.</span><span class="sxs-lookup"><span data-stu-id="8bf74-125">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="8bf74-126">Элемент, выделенный полужирным шрифтом, показывает схему, выведенную для пустого элемента.</span><span class="sxs-lookup"><span data-stu-id="8bf74-126">The bolded element shows the schema inferred for the empty element.</span></span>  
  
 <span data-ttu-id="8bf74-127">См. дополнительные сведения о [выведении схем из XML-документов](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="8bf74-127">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="8bf74-128">XML</span><span class="sxs-lookup"><span data-stu-id="8bf74-128">XML</span></span>|<span data-ttu-id="8bf74-129">Схема</span><span class="sxs-lookup"><span data-stu-id="8bf74-129">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty" />`<br /><br /> `</xs:schema>`|  
  
### <a name="empty-element-with-attributes"></a><span data-ttu-id="8bf74-130">Пустой элемент с атрибутами</span><span class="sxs-lookup"><span data-stu-id="8bf74-130">Empty Element with Attributes</span></span>  

 <span data-ttu-id="8bf74-131">В следующей таблице показаны входные XML-данные для метода <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> и созданная XML-схема.</span><span class="sxs-lookup"><span data-stu-id="8bf74-131">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="8bf74-132">Элементы, выделенные полужирным шрифтом, показывают схему, выведенную для пустого элемента с атрибутами.</span><span class="sxs-lookup"><span data-stu-id="8bf74-132">The bolded elements show the schema inferred for the empty element with attributes.</span></span>  
  
 <span data-ttu-id="8bf74-133">См. дополнительные сведения о [выведении схем из XML-документов](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="8bf74-133">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="8bf74-134">XML</span><span class="sxs-lookup"><span data-stu-id="8bf74-134">XML</span></span>|<span data-ttu-id="8bf74-135">Схема</span><span class="sxs-lookup"><span data-stu-id="8bf74-135">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="empty">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-attributes-and-simple-content"></a><span data-ttu-id="8bf74-136">Элемент с атрибутами и простым содержимым</span><span class="sxs-lookup"><span data-stu-id="8bf74-136">Element with Attributes and Simple Content</span></span>  

 <span data-ttu-id="8bf74-137">В следующей таблице показаны входные XML-данные для метода <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> и созданная XML-схема.</span><span class="sxs-lookup"><span data-stu-id="8bf74-137">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="8bf74-138">Элементы, выделенные полужирным шрифтом, показывают схему, выведенную для элемента с атрибутами и простым содержимым.</span><span class="sxs-lookup"><span data-stu-id="8bf74-138">The bolded elements show the schema inferred for an element with attributes and simple content.</span></span>  
  
 <span data-ttu-id="8bf74-139">См. дополнительные сведения о [выведении схем из XML-документов](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="8bf74-139">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="8bf74-140">XML</span><span class="sxs-lookup"><span data-stu-id="8bf74-140">XML</span></span>|<span data-ttu-id="8bf74-141">Схема</span><span class="sxs-lookup"><span data-stu-id="8bf74-141">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:simpleContent>`<br /><br /> `<xs:extension base="xs:string">`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:extension>`<br /><br /> `</xs:simpleContent>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements"></a><span data-ttu-id="8bf74-142">Элемент с последовательностью дочерних элементов</span><span class="sxs-lookup"><span data-stu-id="8bf74-142">Element with a Sequence of Child Elements</span></span>  

 <span data-ttu-id="8bf74-143">В следующей таблице показаны входные XML-данные для метода <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> и созданная XML-схема.</span><span class="sxs-lookup"><span data-stu-id="8bf74-143">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="8bf74-144">Элементы, выделенные полужирным шрифтом, показывают схему, выведенную для элемента с последовательностью дочерних элементов.</span><span class="sxs-lookup"><span data-stu-id="8bf74-144">The bolded elements show the schema inferred for an element with a sequence of child elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8bf74-145">Даже если элемент содержит только один дочерний элемент, он все равно интерпретируется как последовательность.</span><span class="sxs-lookup"><span data-stu-id="8bf74-145">Even if an element has only one child element, it is still treated as a sequence.</span></span>  
  
 <span data-ttu-id="8bf74-146">См. дополнительные сведения о [выведении схем из XML-документов](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="8bf74-146">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="8bf74-147">XML</span><span class="sxs-lookup"><span data-stu-id="8bf74-147">XML</span></span>|<span data-ttu-id="8bf74-148">Схема</span><span class="sxs-lookup"><span data-stu-id="8bf74-148">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement" />`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-of-child-elements-and-attributes"></a><span data-ttu-id="8bf74-149">Элемент с последовательностью дочерних элементов и атрибутов</span><span class="sxs-lookup"><span data-stu-id="8bf74-149">Element with a Sequence of Child Elements and Attributes</span></span>  

 <span data-ttu-id="8bf74-150">В следующей таблице показаны входные XML-данные для метода <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> и созданная XML-схема.</span><span class="sxs-lookup"><span data-stu-id="8bf74-150">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="8bf74-151">Элементы, выделенные полужирным шрифтом, показывают схему, выведенную для элемента с последовательностью дочерних элементов и атрибутов.</span><span class="sxs-lookup"><span data-stu-id="8bf74-151">The bolded elements show the schema inferred for an element with a sequence of child elements and attributes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8bf74-152">Даже если элемент содержит только один дочерний элемент, он все равно интерпретируется как последовательность.</span><span class="sxs-lookup"><span data-stu-id="8bf74-152">Even if an element has only one child element, it is still treated as a sequence.</span></span>  
  
 <span data-ttu-id="8bf74-153">См. дополнительные сведения о [выведении схем из XML-документов](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="8bf74-153">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="8bf74-154">XML</span><span class="sxs-lookup"><span data-stu-id="8bf74-154">XML</span></span>|<span data-ttu-id="8bf74-155">Схема</span><span class="sxs-lookup"><span data-stu-id="8bf74-155">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choices-of-child-elements"></a><span data-ttu-id="8bf74-156">Элемент с последовательностью и выбором дочерних элементов</span><span class="sxs-lookup"><span data-stu-id="8bf74-156">Element with a Sequence and Choices of Child Elements</span></span>  

 <span data-ttu-id="8bf74-157">В следующей таблице показаны входные XML-данные для метода <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> и созданная XML-схема.</span><span class="sxs-lookup"><span data-stu-id="8bf74-157">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="8bf74-158">Элементы, выделенные полужирным шрифтом, показывают схему, выведенную для элемента с последовательностью и выбором дочерних элементов.</span><span class="sxs-lookup"><span data-stu-id="8bf74-158">The bolded elements show the schema inferred for an element with a sequence and choice of child elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8bf74-159">Для атрибута `maxOccurs` элемента `xs:choice` устанавливается в выводимой схеме значение `"unbounded"`.</span><span class="sxs-lookup"><span data-stu-id="8bf74-159">The `maxOccurs` attribute of the `xs:choice` element is set to `"unbounded"` in the inferred schema.</span></span>  
  
 <span data-ttu-id="8bf74-160">См. дополнительные сведения о [выведении схем из XML-документов](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="8bf74-160">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="8bf74-161">XML</span><span class="sxs-lookup"><span data-stu-id="8bf74-161">XML</span></span>|<span data-ttu-id="8bf74-162">Схема</span><span class="sxs-lookup"><span data-stu-id="8bf74-162">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="element-with-a-sequence-and-choice-of-child-elements-and-attributes"></a><span data-ttu-id="8bf74-163">Элемент с последовательностью и выбором дочерних элементов и атрибутов</span><span class="sxs-lookup"><span data-stu-id="8bf74-163">Element with a Sequence and Choice of Child Elements and Attributes</span></span>  

 <span data-ttu-id="8bf74-164">В следующей таблице показаны входные XML-данные для метода <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> и созданная XML-схема.</span><span class="sxs-lookup"><span data-stu-id="8bf74-164">The following table shows the XML input to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> method, and the XML schema generated.</span></span> <span data-ttu-id="8bf74-165">Элементы, выделенные полужирным шрифтом, показывают схему, выведенную для элемента с последовательностью и выбором дочерних элементов и атрибутов.</span><span class="sxs-lookup"><span data-stu-id="8bf74-165">The bolded elements show the schema inferred for an element with a sequence and choice of child elements and attributes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8bf74-166">Для атрибута `maxOccurs` элемента `xs:choice` устанавливается в выводимой схеме значение `"unbounded"`.</span><span class="sxs-lookup"><span data-stu-id="8bf74-166">The `maxOccurs` attribute of the `xs:choice` element is set to `"unbounded"` in the inferred schema.</span></span>  
  
 <span data-ttu-id="8bf74-167">См. дополнительные сведения о [выведении схем из XML-документов](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="8bf74-167">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
|<span data-ttu-id="8bf74-168">XML</span><span class="sxs-lookup"><span data-stu-id="8bf74-168">XML</span></span>|<span data-ttu-id="8bf74-169">Схема</span><span class="sxs-lookup"><span data-stu-id="8bf74-169">Schema</span></span>|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> `<xs:element name="root">`<br /><br /> `<xs:complexType>`<br /><br /> `<xs:sequence>`<br /><br /> `<xs:choice maxOccurs="unbounded">`<br /><br /> `<xs:element name="subElement1" />`<br /><br /> `<xs:element name="subElement2" />`<br /><br /> `</xs:choice>`<br /><br /> `</xs:sequence>`<br /><br /> `<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `</xs:complexType>`<br /><br /> `</xs:element>`<br /><br /> `</xs:schema>`|  
  
### <a name="attribute-processing"></a><span data-ttu-id="8bf74-170">Обработка атрибутов</span><span class="sxs-lookup"><span data-stu-id="8bf74-170">Attribute Processing</span></span>  

 <span data-ttu-id="8bf74-171">Каждый раз, когда в узле встречается новый атрибут, он добавляется к выведенному определению узла с помощью атрибута `use="required"`.</span><span class="sxs-lookup"><span data-stu-id="8bf74-171">Whenever a new attribute is encountered within a node, it is added to the inferred definition of the node with `use="required"`.</span></span> <span data-ttu-id="8bf74-172">В следующий раз, когда в экземпляре обнаружится этот узел, процесс вывода сравнит атрибуты текущего экземпляра с уже выведенными.</span><span class="sxs-lookup"><span data-stu-id="8bf74-172">The next time the same node is found in the instance, the inference process will compare attributes of the current instance with the ones already inferred.</span></span> <span data-ttu-id="8bf74-173">Если в данном экземпляре отсутствуют некоторые из уже выведенных атрибутов, к определению атрибута добавляется атрибут `use="optional"`.</span><span class="sxs-lookup"><span data-stu-id="8bf74-173">If some of the already inferred ones are missing in the instance, `use="optional"` is added to the attribute definition.</span></span> <span data-ttu-id="8bf74-174">Новые атрибуты добавляются к существующим декларациям с атрибутом `use="optional"`.</span><span class="sxs-lookup"><span data-stu-id="8bf74-174">New attributes are added to existing declarations with `use="optional"`.</span></span>  
  
### <a name="occurrence-constraints"></a><span data-ttu-id="8bf74-175">Ограничения вхождений</span><span class="sxs-lookup"><span data-stu-id="8bf74-175">Occurrence Constraints</span></span>  

 <span data-ttu-id="8bf74-176">При выводе схемы формируются атрибуты `minOccurs` и `maxOccurs` для выведенных компонентов схемы, имеющие значения `"0"` или `"1"` и `"1"` или `"unbounded"`.</span><span class="sxs-lookup"><span data-stu-id="8bf74-176">During the schema inference process, the `minOccurs` and `maxOccurs` attributes are generated, for inferred components of a schema, with the values `"0"` or `"1"` and `"1"` or `"unbounded"`.</span></span> <span data-ttu-id="8bf74-177">Значения `"1"` и `"unbounded"` используются только в случае, когда не удается выполнить проверку XML-документа со значениями `"0"` и `"1"` (например, если `MinOccurs="0"` не описывает действительное состояние элемента, используется значение `minOccurs="1"`).</span><span class="sxs-lookup"><span data-stu-id="8bf74-177">The values `"1"` and `"unbounded"` are used only when the values `"0"` and `"1"` cannot validate the XML document (for example, if `MinOccurs="0"` does not accurately describe an element, `minOccurs="1"` is used).</span></span>  
  
### <a name="mixed-content"></a><span data-ttu-id="8bf74-178">Смешанное содержимое</span><span class="sxs-lookup"><span data-stu-id="8bf74-178">Mixed Content</span></span>  

 <span data-ttu-id="8bf74-179">Для элемента, имеющего смешанное содержимое (например, текст, перемежающийся элементами), для выводимого определения сложного типа будет создан атрибут `mixed="true"`.</span><span class="sxs-lookup"><span data-stu-id="8bf74-179">If an element contains mixed content (for example text interspersed with elements), the `mixed="true"` attribute is generated for the inferred complex type definition.</span></span>  
  
## <a name="other-node-type-inference-rules"></a><span data-ttu-id="8bf74-180">Другие правила определения типов узлов</span><span class="sxs-lookup"><span data-stu-id="8bf74-180">Other Node Type Inference Rules</span></span>  

 <span data-ttu-id="8bf74-181">В следующей таблице описаны правила вывода для инструкций по обработке, комментариев, ссылок на сущности, данных типа CDATA, типа документа и узлов пространства имен.</span><span class="sxs-lookup"><span data-stu-id="8bf74-181">The following table describes the inference rules for processing instruction, comment, entity reference, CDATA, document type, and namespace nodes.</span></span>  
  
|<span data-ttu-id="8bf74-182">Тип узла</span><span class="sxs-lookup"><span data-stu-id="8bf74-182">Node Type</span></span>|<span data-ttu-id="8bf74-183">Перевод</span><span class="sxs-lookup"><span data-stu-id="8bf74-183">Translation</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8bf74-184">Инструкция по обработке</span><span class="sxs-lookup"><span data-stu-id="8bf74-184">Processing instruction</span></span>|<span data-ttu-id="8bf74-185">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="8bf74-185">Ignored.</span></span>|  
|<span data-ttu-id="8bf74-186">Добавление примечаний</span><span class="sxs-lookup"><span data-stu-id="8bf74-186">Comment</span></span>|<span data-ttu-id="8bf74-187">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="8bf74-187">Ignored.</span></span>|  
|<span data-ttu-id="8bf74-188">Ссылка на сущность</span><span class="sxs-lookup"><span data-stu-id="8bf74-188">Entity reference</span></span>|<span data-ttu-id="8bf74-189">Класс <xref:System.Xml.Schema.XmlSchemaInference> не обрабатывает ссылки на сущности.</span><span class="sxs-lookup"><span data-stu-id="8bf74-189">The <xref:System.Xml.Schema.XmlSchemaInference> class does not handle entity references.</span></span> <span data-ttu-id="8bf74-190">Если XML-документ содержит ссылки на сущности, нужно использовать модуль чтения данных, разворачивающий сущности.</span><span class="sxs-lookup"><span data-stu-id="8bf74-190">If an XML document contains entity references, you need to use a reader that expands the entities.</span></span> <span data-ttu-id="8bf74-191">Например, можно передать в качестве параметра объект <xref:System.Xml.XmlTextReader>, у которого свойство <xref:System.Xml.XmlTextReader.EntityHandling%2A> имеет значение <xref:System.Xml.EntityHandling.ExpandEntities>.</span><span class="sxs-lookup"><span data-stu-id="8bf74-191">For example, you can pass an <xref:System.Xml.XmlTextReader> with the <xref:System.Xml.XmlTextReader.EntityHandling%2A> property set to <xref:System.Xml.EntityHandling.ExpandEntities> as a parameter.</span></span> <span data-ttu-id="8bf74-192">Если обнаружены ссылки на сущности и модуль чтения данных не разворачивает сущности, будет вызвано исключение.</span><span class="sxs-lookup"><span data-stu-id="8bf74-192">If entity references are encountered and the reader does not expand entities, an exception is throw.</span></span>|  
|<span data-ttu-id="8bf74-193">CDATA</span><span class="sxs-lookup"><span data-stu-id="8bf74-193">CDATA</span></span>|<span data-ttu-id="8bf74-194">Все разделы `<![CDATA[ … ]]` в XML-документе будут выведены как `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="8bf74-194">Any `<![CDATA[ … ]]` sections in an XML document will be inferred as `xs:string`.</span></span>|  
|<span data-ttu-id="8bf74-195">Тип документа</span><span class="sxs-lookup"><span data-stu-id="8bf74-195">Document type</span></span>|<span data-ttu-id="8bf74-196">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="8bf74-196">Ignored.</span></span>|  
|<span data-ttu-id="8bf74-197">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="8bf74-197">Namespaces</span></span>|<span data-ttu-id="8bf74-198">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="8bf74-198">Ignored.</span></span>|  
  
 <span data-ttu-id="8bf74-199">См. дополнительные сведения о [выведении схем из XML-документов](inferring-schemas-from-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="8bf74-199">For more information about the schema inference process, see [Inferring Schemas from XML Documents](inferring-schemas-from-xml-documents.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf74-200">См. также</span><span class="sxs-lookup"><span data-stu-id="8bf74-200">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaInference>
- [<span data-ttu-id="8bf74-201">Модель объектов схемы XML (SOM)</span><span class="sxs-lookup"><span data-stu-id="8bf74-201">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)
- [<span data-ttu-id="8bf74-202">Выведение XML-схемы</span><span class="sxs-lookup"><span data-stu-id="8bf74-202">Inferring an XML Schema</span></span>](inferring-an-xml-schema.md)
- [<span data-ttu-id="8bf74-203">Выведение схем из XML-документов</span><span class="sxs-lookup"><span data-stu-id="8bf74-203">Inferring Schemas from XML Documents</span></span>](inferring-schemas-from-xml-documents.md)
- [<span data-ttu-id="8bf74-204">Правила выведения простых типов</span><span class="sxs-lookup"><span data-stu-id="8bf74-204">Rules for Inferring Simple Types</span></span>](rules-for-inferring-simple-types.md)
