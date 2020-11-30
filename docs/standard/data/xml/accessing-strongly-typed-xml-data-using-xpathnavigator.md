---
title: Доступ к XML-данным со строгой типизацией с помощью XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
ms.openlocfilehash: 7051aeb8cdc25518f99fe093045e7e769ae7f6f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725421"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a><span data-ttu-id="07d9f-102">Доступ к XML-данным со строгой типизацией с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="07d9f-102">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>

<span data-ttu-id="07d9f-103">Класс <xref:System.Xml.XPath.XPathNavigator>, как экземпляр модели данных XPath 2.0, может содержать данные со строгой типизацией, которые сопоставляются с типами CLR.</span><span class="sxs-lookup"><span data-stu-id="07d9f-103">As an instance of the XPath 2.0 data model, the <xref:System.Xml.XPath.XPathNavigator> class can contain strongly typed data that maps to common language runtime (CLR) types.</span></span> <span data-ttu-id="07d9f-104">Согласно модели данных XPath 2.0, только элементы и атрибуты могут содержать данные со строгой типизацией.</span><span class="sxs-lookup"><span data-stu-id="07d9f-104">According to the XPath 2.0 data model, only elements and attributes can contain strongly typed data.</span></span> <span data-ttu-id="07d9f-105">Класс <xref:System.Xml.XPath.XPathNavigator> предоставляет механизмы для доступа к данным со строгой типизацией в объектах <xref:System.Xml.XPath.XPathDocument> и <xref:System.Xml.XmlDocument>, а также механизмы для преобразования данных из одного типа в другой.</span><span class="sxs-lookup"><span data-stu-id="07d9f-105">The <xref:System.Xml.XPath.XPathNavigator> class provides mechanisms for accessing data within an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object as strongly typed data as well as mechanisms for converting from one data type to another.</span></span>  
  
## <a name="type-information-exposed-by-xpathnavigator"></a><span data-ttu-id="07d9f-106">Информация о типах, предоставляемая XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="07d9f-106">Type Information Exposed by XPathNavigator</span></span>  

 <span data-ttu-id="07d9f-107">Данные XML 1.0 практически не имеют типа, если они не обработаны с помощью определения DTD, схемы XSD или другим средством.</span><span class="sxs-lookup"><span data-stu-id="07d9f-107">XML 1.0 data is technically without type, unless processed with a DTD, XML schema definition language (XSD) schema, or other mechanism.</span></span> <span data-ttu-id="07d9f-108">Существует несколько категорий сведений о типах, которые можно связать с XML-элементом или атрибутом.</span><span class="sxs-lookup"><span data-stu-id="07d9f-108">There are a number of categories of type information that can be associated with an XML element or attribute.</span></span>  
  
- <span data-ttu-id="07d9f-109">Простые типы CLR. Ни один из языков схемы XML не поддерживает типы CLR напрямую.</span><span class="sxs-lookup"><span data-stu-id="07d9f-109">Simple CLR Types: None of the XML Schema languages support Common Language Runtime (CLR) types directly.</span></span> <span data-ttu-id="07d9f-110">Поскольку удобно иметь возможность просматривать простое содержимое элементов и атрибутов в виде соответствующих типов CLR, все простое содержимое можно типизировать как <xref:System.String> в отсутствие данных схемы и любой добавленной информации о схеме, способной уточнить наиболее соответствующий тип этого содержимого.</span><span class="sxs-lookup"><span data-stu-id="07d9f-110">Because it is useful to be able to view simple element and attribute content as the most appropriate CLR type, all simple content can be typed as <xref:System.String> in the absence of schema information with any added schema information potentially refining this content to a more appropriate type.</span></span> <span data-ttu-id="07d9f-111">Наиболее совпадающий тип CLR для простого содержимого элемента или атрибута можно найти с помощью свойства <xref:System.Xml.XPath.XPathNavigator.ValueType%2A>.</span><span class="sxs-lookup"><span data-stu-id="07d9f-111">You can find the best matching CLR type of simple element and attribute content by using the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property.</span></span> <span data-ttu-id="07d9f-112">Дополнительные сведения о сопоставлении встроенных типов схемы с типами CLR см. в руководстве по [поддержке типов в классах System.Xml](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="07d9f-112">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="07d9f-113">Списки простых типов CLR. Элемент или атрибут с простым содержимым может включать список значений, разделенных пробелом.</span><span class="sxs-lookup"><span data-stu-id="07d9f-113">Lists of Simple (CLR) Types: An element or attribute with simple content can contain a list of values separated by white space.</span></span> <span data-ttu-id="07d9f-114">Тип значений определяется схемой XML как тип списка.</span><span class="sxs-lookup"><span data-stu-id="07d9f-114">The values are specified by an XML Schema to be a "list type."</span></span> <span data-ttu-id="07d9f-115">В отсутствие схемы XML содержимое такого простого типа считается одиночным текстовым узлом.</span><span class="sxs-lookup"><span data-stu-id="07d9f-115">In the absence of an XML Schema, such simple content would be treated as a single text node.</span></span> <span data-ttu-id="07d9f-116">При наличии схемы XML это простое содержимое может быть представлено как ряд атомарных значений, каждое из которых имеет простой тип, сопоставляемый с коллекцией объектов CLR.</span><span class="sxs-lookup"><span data-stu-id="07d9f-116">When an XML Schema is available, this simple content can be exposed as a series of atomic values each having a simple type that maps to a collection of CLR objects.</span></span> <span data-ttu-id="07d9f-117">Дополнительные сведения о сопоставлении встроенных типов схемы с типами CLR см. в руководстве по [поддержке типов в классах System.Xml](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="07d9f-117">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="07d9f-118">Типизированное значение. Проверенный на соответствие схеме атрибут или элемент с простым типом, имеющий типизированное значение.</span><span class="sxs-lookup"><span data-stu-id="07d9f-118">Typed Value: A schema-validated attribute or element with a simple type has a typed value.</span></span> <span data-ttu-id="07d9f-119">Это значение является типом-примитивом, например типом numeric, string или date.</span><span class="sxs-lookup"><span data-stu-id="07d9f-119">This value is a primitive type such as a numeric, string, or date type.</span></span> <span data-ttu-id="07d9f-120">Все встроенные простые типы в XSD могут сопоставляться с типами CLR, предоставляющими доступ к значению узла как наиболее соответствующему типу, а не просто типу <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="07d9f-120">All the built-in simple types in XSD can be mapped to CLR types that provide access to the value of a node as a more appropriate type instead of just as a <xref:System.String>.</span></span> <span data-ttu-id="07d9f-121">Элемент с атрибутами или дочерними элементами рассматривается как сложный тип.</span><span class="sxs-lookup"><span data-stu-id="07d9f-121">An element with attributes or element children is considered to be a complex type.</span></span> <span data-ttu-id="07d9f-122">Типизированное значение сложного типа с простым содержимым (только текстовые узлы в качестве дочерних элементов) - то же самое, что и значение простого типа.</span><span class="sxs-lookup"><span data-stu-id="07d9f-122">The typed value of a complex type with simple content (only text nodes as children) is the same as that of the simple type of its content.</span></span> <span data-ttu-id="07d9f-123">Типизированное значение сложного типа со сложным содержимым (один или несколько дочерних элементов) является строковым значением объединения всех его текстовых узлов, возвращенных как тип <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="07d9f-123">The typed value of a complex type with complex content (one or more child elements) is the string value of the concatenation of all its child text nodes returned as a <xref:System.String>.</span></span> <span data-ttu-id="07d9f-124">Дополнительные сведения о сопоставлении встроенных типов схемы с типами CLR см. в руководстве по [поддержке типов в классах System.Xml](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="07d9f-124">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="07d9f-125">Имя типа, зависящее от языка схемы. В большинстве случаев типы CLR, которые определяются в результате применения внешней схемы, используются для предоставления доступа к значению узла.</span><span class="sxs-lookup"><span data-stu-id="07d9f-125">Schema-Language Specific Type Name: In most cases, the CLR types, which are set as a side-effect of applying an external schema, are used to provide access to the value of a node.</span></span> <span data-ttu-id="07d9f-126">Однако в некоторых ситуациях нужно изучить тип, связанный с конкретной схемой, примененной к XML-документу.</span><span class="sxs-lookup"><span data-stu-id="07d9f-126">However, there may be situations where you may want to examine the type associated with a particular schema applied to an XML document.</span></span> <span data-ttu-id="07d9f-127">Например, требуется выполнить поиск в XML-документе и получить все элементы, имеющие тип содержимого «PurchaseOrder», согласно присоединенной схеме.</span><span class="sxs-lookup"><span data-stu-id="07d9f-127">For example, you may wish to search through an XML document, extracting all elements that are determined to have content of type "PurchaseOrder" according to an attached schema.</span></span> <span data-ttu-id="07d9f-128">Такие сведения о типе можно получить только в результате проверки схемы, а доступ к ним осуществляется с помощью свойств <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> и <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> класса <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="07d9f-128">Such type information can be set only as a result of schema validation and this information is accessed through the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> and <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="07d9f-129">Дополнительные сведения см. в разделе «Набор сведений для постсхемной проверки (PSVI)» ниже.</span><span class="sxs-lookup"><span data-stu-id="07d9f-129">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
- <span data-ttu-id="07d9f-130">Отражение типа, зависящее от языка схемы. В других случаях вы можете получить дополнительные сведения о типе, зависящем от схемы, примененной к XML-документу.</span><span class="sxs-lookup"><span data-stu-id="07d9f-130">Schema-Language Specific Type Reflection: In other cases, you may want to obtain further details of the schema-specific type applied to an XML document.</span></span> <span data-ttu-id="07d9f-131">Например, при чтении XML-файла нужно получить атрибут `maxOccurs` для каждого допустимого узла в XML-документе, чтобы выполнить собственные вычисления.</span><span class="sxs-lookup"><span data-stu-id="07d9f-131">For example, when reading an XML file, you may want to extract the `maxOccurs` attribute for each valid node in the XML document in order to perform some custom calculation.</span></span> <span data-ttu-id="07d9f-132">Поскольку эти сведения устанавливаются только через проверку схемы, доступ к ним осуществляется с помощью свойства <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> класса <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="07d9f-132">Because this information is set only through schema validation, it is accessed through the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="07d9f-133">Дополнительные сведения см. в разделе «Набор сведений для постсхемной проверки (PSVI)» ниже.</span><span class="sxs-lookup"><span data-stu-id="07d9f-133">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
## <a name="xpathnavigator-typed-accessors"></a><span data-ttu-id="07d9f-134">Типизированные методы доступа XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="07d9f-134">XPathNavigator Typed Accessors</span></span>  

 <span data-ttu-id="07d9f-135">В следующей таблице показаны свойства и методы класса <xref:System.Xml.XPath.XPathNavigator>, которые используются для доступа к данным о типе узла.</span><span class="sxs-lookup"><span data-stu-id="07d9f-135">The following table shows the various properties and methods of the <xref:System.Xml.XPath.XPathNavigator> class that can be used to access the type information about a node.</span></span>  
  
|<span data-ttu-id="07d9f-136">Свойство.</span><span class="sxs-lookup"><span data-stu-id="07d9f-136">Property</span></span>|<span data-ttu-id="07d9f-137">Описание</span><span class="sxs-lookup"><span data-stu-id="07d9f-137">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|<span data-ttu-id="07d9f-138">Содержит информацию о типе схемы XML для узла, если он допустим.</span><span class="sxs-lookup"><span data-stu-id="07d9f-138">This contains the XML schema type information for the node if it is valid.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|<span data-ttu-id="07d9f-139">Содержит информационный набор после проверки по схеме узла, который добавляется после проверки.</span><span class="sxs-lookup"><span data-stu-id="07d9f-139">This contains the Post Schema Validation Infoset of the node that is added after validation.</span></span> <span data-ttu-id="07d9f-140">Он включает сведения о типе схемы XML, а также сведения о достоверности.</span><span class="sxs-lookup"><span data-stu-id="07d9f-140">This includes the XML schema type information, as well as validity information.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|<span data-ttu-id="07d9f-141">Тип CLR типизированного значения узла.</span><span class="sxs-lookup"><span data-stu-id="07d9f-141">The CLR type of the typed value of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|<span data-ttu-id="07d9f-142">Содержимое узла в виде одного или нескольких значений CLR, тип которых больше всего соответствует типу схемы XML узла.</span><span class="sxs-lookup"><span data-stu-id="07d9f-142">The content of the node as one or more CLR values whose type is the closest match to the XML schema type of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<span data-ttu-id="07d9f-143">Значение <xref:System.String> текущего узла приводится к значению <xref:System.Boolean> в соответствии с правилами приведения типов XPath 2.0 для `xs:boolean`.</span><span class="sxs-lookup"><span data-stu-id="07d9f-143">The <xref:System.String> value of the current node cast to a <xref:System.Boolean> value, according to the XPath 2.0 casting rules for `xs:boolean`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<span data-ttu-id="07d9f-144">Значение <xref:System.String> текущего узла приводится к значению <xref:System.DateTime> в соответствии с правилами приведения типов XPath 2.0 для `xs:datetime`.</span><span class="sxs-lookup"><span data-stu-id="07d9f-144">The <xref:System.String> value of the current node cast to a <xref:System.DateTime> value, according to the XPath 2.0 casting rules for `xs:datetime`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<span data-ttu-id="07d9f-145">Значение <xref:System.String> текущего узла приводится к значению <xref:System.Double> в соответствии с правилами приведения типов XPath 2.0 для `xsd:double`.</span><span class="sxs-lookup"><span data-stu-id="07d9f-145">The <xref:System.String> value of the current node cast to a <xref:System.Double> value, according to the XPath 2.0 casting rules for `xsd:double`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<span data-ttu-id="07d9f-146">Значение <xref:System.String> текущего узла приводится к значению <xref:System.Int32> в соответствии с правилами приведения типов XPath 2.0 для `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="07d9f-146">The <xref:System.String> value of the current node cast to a <xref:System.Int32> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<span data-ttu-id="07d9f-147">Значение <xref:System.String> текущего узла приводится к значению <xref:System.Int64> в соответствии с правилами приведения типов XPath 2.0 для `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="07d9f-147">The <xref:System.String> value of the current node cast to a <xref:System.Int64> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|<span data-ttu-id="07d9f-148">Содержимое узла, приведенное к целевому типу согласно правилам приведения типов XPath 2.0.</span><span class="sxs-lookup"><span data-stu-id="07d9f-148">The contents of the node cast to the target type according to the XPath 2.0 casting rules.</span></span>|  
  
 <span data-ttu-id="07d9f-149">Дополнительные сведения о сопоставлении встроенных типов схемы с типами CLR см. в руководстве по [поддержке типов в классах System.Xml](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="07d9f-149">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="the-post-schema-validation-infoset-psvi"></a><span data-ttu-id="07d9f-150">Информационный набор после проверки по схеме</span><span class="sxs-lookup"><span data-stu-id="07d9f-150">The Post Schema Validation Infoset (PSVI)</span></span>  

 <span data-ttu-id="07d9f-151">Процессор схемы XML принимает в качестве входных данных информационный набор XML и преобразует его в информационный набор после проверки по схеме.</span><span class="sxs-lookup"><span data-stu-id="07d9f-151">An XML Schema processor accepts an XML Infoset as input and converts it into a Post Schema Validation Infoset (PSVI).</span></span> <span data-ttu-id="07d9f-152">Информационный набор после проверки по схеме является исходным информационным набором XML с новыми информационными элементами и новыми свойствами, добавленными к существующим информационным элементам.</span><span class="sxs-lookup"><span data-stu-id="07d9f-152">A PSVI is the original input XML infoset with new information items added and new properties added to existing information items.</span></span> <span data-ttu-id="07d9f-153">Существует три широких класса данных, которые добавляются в информационный набор XML в информационном наборе после проверки по схеме, предоставляемом классом <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="07d9f-153">There are three broad classes of information added to the XML Infoset in the PSVI that are exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
1. <span data-ttu-id="07d9f-154">Результаты проверки. Сведения об успешной или неуспешной проверке элемента или атрибута.</span><span class="sxs-lookup"><span data-stu-id="07d9f-154">Validation Outcomes: Information as to whether an element or attribute was successfully validated or not.</span></span> <span data-ttu-id="07d9f-155">Это представляется свойством <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> свойства <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> класса <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="07d9f-155">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
2. <span data-ttu-id="07d9f-156">Сведения по умолчанию. Данные о том, было ли получено значение элемента или атрибута из заданных в схеме значений по умолчанию или из других источников.</span><span class="sxs-lookup"><span data-stu-id="07d9f-156">Default Information: Indications as to whether the value of the element or attribute was obtained via default values specified in the schema or not.</span></span> <span data-ttu-id="07d9f-157">Это представляется свойством <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> свойства <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> класса <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="07d9f-157">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
3. <span data-ttu-id="07d9f-158">Заметки о типах. Ссылки на компоненты схемы, которые могут быть декларациями типов или декларациями элементов и атрибутов.</span><span class="sxs-lookup"><span data-stu-id="07d9f-158">Type Annotations: References to schema components that may be type definitions or element and attribute declarations.</span></span> <span data-ttu-id="07d9f-159">Свойство <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> объекта <xref:System.Xml.XPath.XPathNavigator> содержит конкретные сведения о типе узла, если он допустим.</span><span class="sxs-lookup"><span data-stu-id="07d9f-159">The <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property of the <xref:System.Xml.XPath.XPathNavigator> contains the specific type information of the node if it is valid.</span></span> <span data-ttu-id="07d9f-160">Если достоверность узла неизвестна, например если он после проверки подвергся изменению,</span><span class="sxs-lookup"><span data-stu-id="07d9f-160">If the validity of a node is unknown, such as when it was validated then subsequently edited.</span></span> <span data-ttu-id="07d9f-161">то свойство <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> имеет значение `null`, но информация о типе остается доступной через различные свойства <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> класса <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="07d9f-161">then the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property is set to `null` but type information is still available from the various properties of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="07d9f-162">В следующем примере демонстрируются сведения информационного набора после проверки по схеме, предоставленной объектом <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="07d9f-162">The following example illustrates using information in the Post Schema Validation Infoset exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("books.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("published", "http://www.contoso.com/books")  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name)  
Console.WriteLine(navigator.SchemaInfo.Validity)  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("books.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("published", "http://www.contoso.com/books");  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name);  
Console.WriteLine(navigator.SchemaInfo.Validity);  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs);  
```  
  
 <span data-ttu-id="07d9f-163">В примере в качестве входных данных используется файл `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="07d9f-163">The example takes the `books.xml` file as input.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="07d9f-164">В примере в качестве входных данных также используется схема `books.xsd`.</span><span class="sxs-lookup"><span data-stu-id="07d9f-164">The example also takes the `books.xsd` schema as input.</span></span>  
  
```xml  
<xs:schema xmlns="http://www.contoso.com/books"
attributeFormDefault="unqualified" elementFormDefault="qualified"
targetNamespace="http://www.contoso.com/books"
xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="publishedType">  
        <xs:restriction base="xs:date">  
            <xs:minInclusive value="2003-01-01" />  
            <xs:maxInclusive value="2003-12-31" />  
        </xs:restriction>  
    </xs:simpleType>  
    <xs:complexType name="bookType">  
        <xs:sequence>  
            <xs:element name="title" type="xs:string"/>  
            <xs:element name="price" type="xs:decimal"/>  
            <xs:element name="published" type="publishedType"/>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="booksType">  
        <xs:sequence>  
            <xs:element name="book" type="bookType" />  
        </xs:sequence>  
    </xs:complexType>  
    <xs:element name="books" type="booksType" />  
</xs:schema>  
```  
  
## <a name="obtain-typed-values-using-valueas-properties"></a><span data-ttu-id="07d9f-165">Получение типизированных значений с помощью свойств ValueAs</span><span class="sxs-lookup"><span data-stu-id="07d9f-165">Obtain Typed Values Using ValueAs Properties</span></span>  

 <span data-ttu-id="07d9f-166">Типизированное значение узла можно получить с помощью свойства <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> класса <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="07d9f-166">The typed value of a node can be retrieved by accessing the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="07d9f-167">В определенных случаях можно преобразовать типизированное значение узла в другое значение.</span><span class="sxs-lookup"><span data-stu-id="07d9f-167">In certain cases you may want to convert the typed value of a node to a different type.</span></span> <span data-ttu-id="07d9f-168">Распространенным примером является получение численного значения из XML-узла.</span><span class="sxs-lookup"><span data-stu-id="07d9f-168">A common example is to get a numeric value from an XML node.</span></span> <span data-ttu-id="07d9f-169">Например, рассмотрим следующий непроверенный и нетипизированный XML-документ.</span><span class="sxs-lookup"><span data-stu-id="07d9f-169">For example, consider the following unvalidated and untyped XML document.</span></span>  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="07d9f-170">Если объект <xref:System.Xml.XPath.XPathNavigator> расположен на элементе `price`, свойство <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> будет иметь значение `null`, свойство <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> - значение <xref:System.String>, а свойство <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> примет строковое значение `10.00`.</span><span class="sxs-lookup"><span data-stu-id="07d9f-170">If the <xref:System.Xml.XPath.XPathNavigator> is positioned on the `price` element the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property would be `null`, the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property would be <xref:System.String>, and the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property would be the string `10.00`.</span></span>  
  
 <span data-ttu-id="07d9f-171">Однако все же можно получить цифровое значение с помощью методов и свойств <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A> и <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>.</span><span class="sxs-lookup"><span data-stu-id="07d9f-171">However, it is still possible to extract the value as a numeric value using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, or <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> method and properties.</span></span> <span data-ttu-id="07d9f-172">В следующем примере показано такое приведение к типу с помощью метода <xref:System.Xml.XPath.XPathItem.ValueAs%2A>.</span><span class="sxs-lookup"><span data-stu-id="07d9f-172">The following example illustrates performing such a cast using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A> method.</span></span>  
  
```vb  
Dim document As New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "")  
navigator.MoveToChild("book", "")  
navigator.MoveToChild("price", "")  
  
Dim price = navigator.ValueAs(GetType(Decimal))  
Dim discount As Decimal = 0.2  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * discount))  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "");  
navigator.MoveToChild("book", "");  
navigator.MoveToChild("price", "");  
  
Decimal price = (decimal)navigator.ValueAs(typeof(decimal));  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * (decimal)0.20));  
```  
  
 <span data-ttu-id="07d9f-173">Дополнительные сведения о сопоставлении встроенных типов схемы с типами CLR см. в руководстве по [поддержке типов в классах System.Xml](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="07d9f-173">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d9f-174">См. также</span><span class="sxs-lookup"><span data-stu-id="07d9f-174">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="07d9f-175">Поддержка типов в классах System.Xml</span><span class="sxs-lookup"><span data-stu-id="07d9f-175">Type Support in the System.Xml Classes</span></span>](type-support-in-the-system-xml-classes.md)
- [<span data-ttu-id="07d9f-176">Обработка XML-данных с использованием модели данных XPath</span><span class="sxs-lookup"><span data-stu-id="07d9f-176">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="07d9f-177">Навигация в наборе узлов с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="07d9f-177">Node Set Navigation Using XPathNavigator</span></span>](node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="07d9f-178">Навигация по узлам атрибутов и пространств имен с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="07d9f-178">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="07d9f-179">Извлечение XML-данных с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="07d9f-179">Extract XML Data Using XPathNavigator</span></span>](extract-xml-data-using-xpathnavigator.md)
