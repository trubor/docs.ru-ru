---
description: Дополнительные сведения о свойстве "ось атрибутов XML" (Visual Basic)
title: XML Attribute Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 2085ef2151e7aef7c5642e0ba9ac2e6fa90bfd4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795174"
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="32052-103">Свойство оси атрибута XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32052-103">XML Attribute Axis Property (Visual Basic)</span></span>

<span data-ttu-id="32052-104">Предоставляет доступ к значению атрибута для <xref:System.Xml.Linq.XElement> объекта или к первому элементу в коллекции <xref:System.Xml.Linq.XElement> объектов.</span><span class="sxs-lookup"><span data-stu-id="32052-104">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32052-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="32052-105">Syntax</span></span>  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="32052-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="32052-106">Parts</span></span>  

 `object`  
 <span data-ttu-id="32052-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="32052-107">Required.</span></span> <span data-ttu-id="32052-108"><xref:System.Xml.Linq.XElement>Объект или коллекция <xref:System.Xml.Linq.XElement> объектов.</span><span class="sxs-lookup"><span data-stu-id="32052-108">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="32052-109">.@</span><span class="sxs-lookup"><span data-stu-id="32052-109">.@</span></span>  
 <span data-ttu-id="32052-110">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="32052-110">Required.</span></span> <span data-ttu-id="32052-111">Обозначает начало свойства оси атрибута.</span><span class="sxs-lookup"><span data-stu-id="32052-111">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="32052-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="32052-112">Optional.</span></span> <span data-ttu-id="32052-113">Обозначает начало имени атрибута, если не является `attribute` допустимым идентификатором в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="32052-113">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
 `attribute`  
 <span data-ttu-id="32052-114">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="32052-114">Required.</span></span> <span data-ttu-id="32052-115">Имя атрибута для доступа в форме [ `prefix` :] `name` .</span><span class="sxs-lookup"><span data-stu-id="32052-115">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="32052-116">Отделение</span><span class="sxs-lookup"><span data-stu-id="32052-116">Part</span></span>|<span data-ttu-id="32052-117">Описание</span><span class="sxs-lookup"><span data-stu-id="32052-117">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="32052-118">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="32052-118">Optional.</span></span> <span data-ttu-id="32052-119">Префикс пространства имен XML для атрибута.</span><span class="sxs-lookup"><span data-stu-id="32052-119">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="32052-120">Должно быть глобальным пространством имен XML, определенным с помощью оператора `Imports`.</span><span class="sxs-lookup"><span data-stu-id="32052-120">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="32052-121">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="32052-121">Required.</span></span> <span data-ttu-id="32052-122">Имя локального атрибута.</span><span class="sxs-lookup"><span data-stu-id="32052-122">Local attribute name.</span></span> <span data-ttu-id="32052-123">См. [Имена объявленных XML-элементов и атрибутов](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="32052-123">See [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="32052-124">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="32052-124">Optional.</span></span> <span data-ttu-id="32052-125">Обозначает конец имени атрибута, если не является `attribute` допустимым идентификатором в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="32052-125">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32052-126">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="32052-126">Return Value</span></span>  

 <span data-ttu-id="32052-127">Строка, содержащая значение `attribute` .</span><span class="sxs-lookup"><span data-stu-id="32052-127">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="32052-128">Если имя атрибута не существует, `Nothing` возвращается значение.</span><span class="sxs-lookup"><span data-stu-id="32052-128">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32052-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="32052-129">Remarks</span></span>  

 <span data-ttu-id="32052-130">Свойство оси атрибутов XML можно использовать для доступа к значению атрибута по имени из <xref:System.Xml.Linq.XElement> объекта или из первого элемента в коллекции <xref:System.Xml.Linq.XElement> объектов.</span><span class="sxs-lookup"><span data-stu-id="32052-130">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="32052-131">Можно получить значение атрибута по имени или добавить новый атрибут к элементу, указав новое имя перед идентификатором @.</span><span class="sxs-lookup"><span data-stu-id="32052-131">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="32052-132">При ссылке на XML-атрибут, используя идентификатор @, значение атрибута возвращается в виде строки и не требуется явно указывать <xref:System.Xml.Linq.XAttribute.Value%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="32052-132">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="32052-133">Правила именования для XML-атрибутов отличаются от правил именования для Visual Basic идентификаторов.</span><span class="sxs-lookup"><span data-stu-id="32052-133">The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers.</span></span> <span data-ttu-id="32052-134">Чтобы получить доступ к XML-атрибуту, имя которого не является допустимым Visual Basic идентификатором, заключите имя в угловые скобки ( \< and > ).</span><span class="sxs-lookup"><span data-stu-id="32052-134">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="32052-135">Пространства имен XML</span><span class="sxs-lookup"><span data-stu-id="32052-135">XML Namespaces</span></span>  

 <span data-ttu-id="32052-136">Имя в свойстве оси атрибута может использовать только префиксы пространства имен XML, объявленные глобально с помощью `Imports` инструкции.</span><span class="sxs-lookup"><span data-stu-id="32052-136">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="32052-137">В нем нельзя использовать префиксы пространства имен XML, объявленные локально с помощью литералов XML-элемента.</span><span class="sxs-lookup"><span data-stu-id="32052-137">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="32052-138">Дополнительные сведения см. в разделе [оператор Imports (пространство имен XML)](../statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="32052-138">For more information, see [Imports Statement (XML Namespace)](../statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32052-139">Пример</span><span class="sxs-lookup"><span data-stu-id="32052-139">Example</span></span>  

 <span data-ttu-id="32052-140">В следующем примере показано, как получить значения XML-атрибутов с именем `type` из коллекции XML-элементов с именами `phone` .</span><span class="sxs-lookup"><span data-stu-id="32052-140">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 <span data-ttu-id="32052-141">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="32052-141">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="32052-142">Пример</span><span class="sxs-lookup"><span data-stu-id="32052-142">Example</span></span>  

 <span data-ttu-id="32052-143">В следующем примере показано, как создать атрибуты для XML-элемента декларативно, как часть XML, и динамически, добавив атрибут к экземпляру <xref:System.Xml.Linq.XElement> объекта.</span><span class="sxs-lookup"><span data-stu-id="32052-143">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="32052-144">`type`Атрибут создается декларативно, а `owner` атрибут создается динамически.</span><span class="sxs-lookup"><span data-stu-id="32052-144">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 <span data-ttu-id="32052-145">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="32052-145">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="32052-146">Пример</span><span class="sxs-lookup"><span data-stu-id="32052-146">Example</span></span>  

 <span data-ttu-id="32052-147">В следующем примере используется синтаксис угловой скобки для получения значения XML-атрибута с именем `number-type` , который не является допустимым идентификатором в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="32052-147">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.</span></span>  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 <span data-ttu-id="32052-148">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="32052-148">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="32052-149">Пример</span><span class="sxs-lookup"><span data-stu-id="32052-149">Example</span></span>  

 <span data-ttu-id="32052-150">В следующем примере `ns` объявляется как префикс пространства имен XML.</span><span class="sxs-lookup"><span data-stu-id="32052-150">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="32052-151">Затем он использует префикс пространства имен для создания XML-литерала и доступа к первому дочернему узлу с полным именем " `ns:name` ".</span><span class="sxs-lookup"><span data-stu-id="32052-151">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 <span data-ttu-id="32052-152">Этот пример кода отображает следующий текст:</span><span class="sxs-lookup"><span data-stu-id="32052-152">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="32052-153">См. также</span><span class="sxs-lookup"><span data-stu-id="32052-153">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="32052-154">Свойства оси XML</span><span class="sxs-lookup"><span data-stu-id="32052-154">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="32052-155">XML-литералы</span><span class="sxs-lookup"><span data-stu-id="32052-155">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="32052-156">Создание XML в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32052-156">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="32052-157">Имена объявленных элементов и атрибутов XML</span><span class="sxs-lookup"><span data-stu-id="32052-157">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
