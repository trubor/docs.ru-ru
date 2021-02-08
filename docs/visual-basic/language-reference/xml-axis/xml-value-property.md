---
description: Дополнительные сведения о свойстве "значение XML" (Visual Basic)
title: Свойство значения XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 49762c1fcc0059472a5be11726aa344a001807ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768770"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="8f613-103">Свойство значения XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f613-103">XML Value Property (Visual Basic)</span></span>

<span data-ttu-id="8f613-104">Предоставляет доступ к значению первого элемента коллекции <xref:System.Xml.Linq.XElement> объектов.</span><span class="sxs-lookup"><span data-stu-id="8f613-104">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>

## <a name="syntax"></a><span data-ttu-id="8f613-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8f613-105">Syntax</span></span>

```vb
object.Value
```

## <a name="parts"></a><span data-ttu-id="8f613-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="8f613-106">Parts</span></span>

|<span data-ttu-id="8f613-107">Термин</span><span class="sxs-lookup"><span data-stu-id="8f613-107">Term</span></span>|<span data-ttu-id="8f613-108">Определение</span><span class="sxs-lookup"><span data-stu-id="8f613-108">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="8f613-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="8f613-109">Required.</span></span> <span data-ttu-id="8f613-110">Коллекция объектов <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="8f613-110">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  

## <a name="return-value"></a><span data-ttu-id="8f613-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8f613-111">Return Value</span></span>

 <span data-ttu-id="8f613-112">Значение типа `String` , содержащее значение первого элемента коллекции или, `Nothing` Если коллекция пуста.</span><span class="sxs-lookup"><span data-stu-id="8f613-112">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f613-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="8f613-113">Remarks</span></span>

 <span data-ttu-id="8f613-114"><xref:System.Xml.Linq.XElement.Value%2A>Свойство позволяет легко получить доступ к значению первого элемента в коллекции <xref:System.Xml.Linq.XElement> объектов.</span><span class="sxs-lookup"><span data-stu-id="8f613-114">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="8f613-115">Это свойство сначала проверяет, содержит ли коллекция хотя бы один объект.</span><span class="sxs-lookup"><span data-stu-id="8f613-115">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="8f613-116">Если коллекция пуста, это свойство возвращает значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="8f613-116">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="8f613-117">В противном случае это свойство возвращает значение <xref:System.Xml.Linq.XElement.Value%2A> свойства первого элемента в коллекции.</span><span class="sxs-lookup"><span data-stu-id="8f613-117">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="8f613-118">При доступе к значению атрибута XML с помощью идентификатора " \@ " значение атрибута возвращается в виде, `String` и вам не нужно явно указывать <xref:System.Xml.Linq.XAttribute.Value%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="8f613-118">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>

 <span data-ttu-id="8f613-119">Для доступа к другим элементам в коллекции можно использовать свойство индексатора расширения XML.</span><span class="sxs-lookup"><span data-stu-id="8f613-119">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="8f613-120">Дополнительные сведения см. в разделе [свойство индексатора расширения](extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="8f613-120">For more information, see [Extension Indexer Property](extension-indexer-property.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="8f613-121">Наследование</span><span class="sxs-lookup"><span data-stu-id="8f613-121">Inheritance</span></span>

 <span data-ttu-id="8f613-122">Большинству пользователей не придется реализовывать <xref:System.Collections.Generic.IEnumerable%601> , и поэтому этот раздел можно игнорировать.</span><span class="sxs-lookup"><span data-stu-id="8f613-122">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>

 <span data-ttu-id="8f613-123"><xref:System.Xml.Linq.XElement.Value%2A>Свойство является свойством расширения для типов, реализующих `IEnumerable(Of XElement)` .</span><span class="sxs-lookup"><span data-stu-id="8f613-123">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="8f613-124">Привязка этого свойства расширения похожа на привязку методов расширения: Если тип реализует один из интерфейсов и определяет свойство с именем "value", это свойство имеет приоритет над свойством расширения.</span><span class="sxs-lookup"><span data-stu-id="8f613-124">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="8f613-125">Иными словами, это <xref:System.Xml.Linq.XElement.Value%2A> свойство можно переопределить, определив новое свойство в классе, реализующем интерфейс `IEnumerable(Of XElement)` .</span><span class="sxs-lookup"><span data-stu-id="8f613-125">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>

## <a name="example"></a><span data-ttu-id="8f613-126">Пример</span><span class="sxs-lookup"><span data-stu-id="8f613-126">Example</span></span>

 <span data-ttu-id="8f613-127">В следующем примере показано, как использовать <xref:System.Xml.Linq.XElement.Value%2A> свойство для доступа к первому узлу в коллекции <xref:System.Xml.Linq.XElement> объектов.</span><span class="sxs-lookup"><span data-stu-id="8f613-127">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="8f613-128">В примере свойство дочерней оси используется для получения коллекции всех дочерних узлов, наименованных `phone` в `contact` объекте.</span><span class="sxs-lookup"><span data-stu-id="8f613-128">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 <span data-ttu-id="8f613-129">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="8f613-129">This code displays the following text:</span></span>

 `Phone number: 206-555-0144`

## <a name="example"></a><span data-ttu-id="8f613-130">Пример</span><span class="sxs-lookup"><span data-stu-id="8f613-130">Example</span></span>

 <span data-ttu-id="8f613-131">В следующем примере показано, как получить значение атрибута XML из коллекции <xref:System.Xml.Linq.XAttribute> объектов.</span><span class="sxs-lookup"><span data-stu-id="8f613-131">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="8f613-132">В примере свойство оси атрибута используется для вывода значения `type` атрибута для всех `phone` элементов.</span><span class="sxs-lookup"><span data-stu-id="8f613-132">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>

 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]

 <span data-ttu-id="8f613-133">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="8f613-133">This code displays the following text:</span></span>

 ```console
 home
 work
```

## <a name="see-also"></a><span data-ttu-id="8f613-134">См. также</span><span class="sxs-lookup"><span data-stu-id="8f613-134">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="8f613-135">Свойства оси XML</span><span class="sxs-lookup"><span data-stu-id="8f613-135">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="8f613-136">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="8f613-136">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="8f613-137">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8f613-137">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="8f613-138">Методы расширения</span><span class="sxs-lookup"><span data-stu-id="8f613-138">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="8f613-139">Свойство индексатора расширения</span><span class="sxs-lookup"><span data-stu-id="8f613-139">Extension Indexer Property</span></span>](extension-indexer-property.md)
- [<span data-ttu-id="8f613-140">XML Child Axis Property</span><span class="sxs-lookup"><span data-stu-id="8f613-140">XML Child Axis Property</span></span>](xml-child-axis-property.md)
- [<span data-ttu-id="8f613-141">XML Attribute Axis Property</span><span class="sxs-lookup"><span data-stu-id="8f613-141">XML Attribute Axis Property</span></span>](xml-attribute-axis-property.md)
