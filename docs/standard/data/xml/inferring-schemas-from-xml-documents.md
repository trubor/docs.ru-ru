---
title: Выведение схем из XML-документов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
ms.openlocfilehash: 4540e1706cbd3dad9490f100d7e8fa58e80a9206
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733442"
---
# <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="a5a93-102">Выведение схем из XML-документов</span><span class="sxs-lookup"><span data-stu-id="a5a93-102">Inferring Schemas from XML Documents</span></span>

<span data-ttu-id="a5a93-103">В этом разделе описывается, как использовать класс <xref:System.Xml.Schema.XmlSchemaInference> для выведения схемы XSD из структуры XML-документа.</span><span class="sxs-lookup"><span data-stu-id="a5a93-103">This topic describes how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XML Schema definition language (XSD) schema from the structure of an XML document.</span></span>  
  
## <a name="the-schema-inference-process"></a><span data-ttu-id="a5a93-104">Процесс выведения схемы</span><span class="sxs-lookup"><span data-stu-id="a5a93-104">The Schema Inference Process</span></span>  

 <span data-ttu-id="a5a93-105">Класс <xref:System.Xml.Schema.XmlSchemaInference> из пространства имен <xref:System.Xml.Schema?displayProperty=nameWithType> используется для создания одной или нескольких схем XSD из структуры XML-документа.</span><span class="sxs-lookup"><span data-stu-id="a5a93-105">The <xref:System.Xml.Schema.XmlSchemaInference> class of the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace is used to generate one or more XML Schema definition language (XSD) schemas from the structure of an XML document.</span></span> <span data-ttu-id="a5a93-106">Полученные схемы можно использовать для проверки исходного XML-документа.</span><span class="sxs-lookup"><span data-stu-id="a5a93-106">The generated schemas may be used to validate the original XML document.</span></span>  
  
 <span data-ttu-id="a5a93-107">Во время обработки XML-документа <xref:System.Xml.Schema.XmlSchemaInference> класс <xref:System.Xml.Schema.XmlSchemaInference> строит предположения о компонентах схемы, описывающих элементы и атрибуты в XML-документе.</span><span class="sxs-lookup"><span data-stu-id="a5a93-107">As an XML document is processed by the <xref:System.Xml.Schema.XmlSchemaInference> class, the <xref:System.Xml.Schema.XmlSchemaInference> class makes assumptions about the schema components that describe the elements and attributes in the XML document.</span></span> <span data-ttu-id="a5a93-108">Класс <xref:System.Xml.Schema.XmlSchemaInference> также выводит компоненты схемы по принципу ограничения - выводится самый строгий тип для каждого элемента или атрибута.</span><span class="sxs-lookup"><span data-stu-id="a5a93-108">The <xref:System.Xml.Schema.XmlSchemaInference> class also infers schema components in a constrained way by inferring the most restrictive type for a particular element or attribute.</span></span> <span data-ttu-id="a5a93-109">По мере сбора дополнительных сведений о XML-документе эти ограничения ослабляются и выводятся менее строгие типы.</span><span class="sxs-lookup"><span data-stu-id="a5a93-109">As more information about the XML document is gathered, these constraints are loosened by inferring less restrictive types.</span></span> <span data-ttu-id="a5a93-110">Наименее строгим выводимым типом является `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="a5a93-110">The least restrictive type that can be inferred is `xs:string`.</span></span>  
  
 <span data-ttu-id="a5a93-111">Рассмотрим, например, следующий фрагмент XML-документа.</span><span class="sxs-lookup"><span data-stu-id="a5a93-111">Take, for example, the following piece of an XML document.</span></span>  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A" />
```  
  
 <span data-ttu-id="a5a93-112">В примере выше, когда в процессе `attribute1` обнаруживается атрибут `6` со значением <xref:System.Xml.Schema.XmlSchemaInference>, для него предполагается тип `xs:unsignedByte`.</span><span class="sxs-lookup"><span data-stu-id="a5a93-112">In the example above, when the `attribute1` attribute is encountered with a value of `6` by the <xref:System.Xml.Schema.XmlSchemaInference> process, it is assumed to be of type `xs:unsignedByte`.</span></span> <span data-ttu-id="a5a93-113">Когда в процессе `parent` обнаруживается второй элемент <xref:System.Xml.Schema.XmlSchemaInference>, ограничение ослабляется путем замены типа на `xs:string`, поскольку теперь атрибут `attribute1` имеет значение `A`.</span><span class="sxs-lookup"><span data-stu-id="a5a93-113">When the second `parent` element is encountered by the <xref:System.Xml.Schema.XmlSchemaInference> process, the constraint is loosened by modifying the type to `xs:string` because the value of the `attribute1` attribute is now `A`.</span></span> <span data-ttu-id="a5a93-114">Аналогично, атрибут `minOccurs` для всех элементов `child`, выведенных в схему, ослабляется до значения `minOccurs="0"`, поскольку второй родительский элемент не имеет дочерних.</span><span class="sxs-lookup"><span data-stu-id="a5a93-114">Similarly, the `minOccurs` attribute for all the `child` elements inferred in the schema are loosened to `minOccurs="0"` because the second parent element has no child elements.</span></span>  
  
## <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="a5a93-115">Выведение схем из XML-документов</span><span class="sxs-lookup"><span data-stu-id="a5a93-115">Inferring Schemas from XML Documents</span></span>  

 <span data-ttu-id="a5a93-116">Класс <xref:System.Xml.Schema.XmlSchemaInference> использует два перегруженных метода <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> для вывода схемы из XML-документа.</span><span class="sxs-lookup"><span data-stu-id="a5a93-116">The <xref:System.Xml.Schema.XmlSchemaInference> class uses two overloaded <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> methods to infer a schema from an XML document.</span></span>  
  
 <span data-ttu-id="a5a93-117">Первый метод <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> используется для создания схемы на основе XML-документа.</span><span class="sxs-lookup"><span data-stu-id="a5a93-117">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to create a schema based on an XML document.</span></span> <span data-ttu-id="a5a93-118">Второй метод <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> используется для вывода схемы, описывающей несколько XML-документов.</span><span class="sxs-lookup"><span data-stu-id="a5a93-118">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to infer a schema that describes multiple XML documents.</span></span> <span data-ttu-id="a5a93-119">Например, можно по очереди передать методу <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> несколько XML-документов, чтобы создать схему, описывающую весь набор XML-документов.</span><span class="sxs-lookup"><span data-stu-id="a5a93-119">For example, you can feed multiple XML documents to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method one at a time to produce a schema that describes the entire set of XML documents.</span></span>  
  
 <span data-ttu-id="a5a93-120">Первый метод <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> выводит схему из XML-документа, содержащегося в объекте <xref:System.Xml.XmlReader>, и возвращает объект <xref:System.Xml.Schema.XmlSchemaSet>, содержащий выведенную схему.</span><span class="sxs-lookup"><span data-stu-id="a5a93-120">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method infers a schema from an XML document contained in an <xref:System.Xml.XmlReader> object, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span> <span data-ttu-id="a5a93-121">Второй метод <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> ищет в объекте <xref:System.Xml.Schema.XmlSchemaSet> схему, целевое пространство имен которой совпадает с XML-документом, содержащимся в объекте <xref:System.Xml.XmlReader>, уточняет существующую схему и возвращает объект <xref:System.Xml.Schema.XmlSchemaSet>, содержащий выведенную схему.</span><span class="sxs-lookup"><span data-stu-id="a5a93-121">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method searches an <xref:System.Xml.Schema.XmlSchemaSet> object for a schema with the same target namespace as the XML document contained in the <xref:System.Xml.XmlReader> object, refines the existing schema, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span>  
  
 <span data-ttu-id="a5a93-122">Изменения, вносимые в уточняемую схему, основаны на новой структуре, обнаруженной в XML-документе.</span><span class="sxs-lookup"><span data-stu-id="a5a93-122">The changes made to the refined schema are based on new structure found in the XML document.</span></span> <span data-ttu-id="a5a93-123">Например, в процессе обзора XML-документа строятся предположения об обнаруженных типах данных, и схема создается на основе этих предположений.</span><span class="sxs-lookup"><span data-stu-id="a5a93-123">For example, as an XML document is traversed, assumptions are made about the data types found, and the schema is created based on those assumptions.</span></span> <span data-ttu-id="a5a93-124">Однако если во втором проходе выведения обнаруживаются данные, отличающиеся от исходных предположений, схема уточняется.</span><span class="sxs-lookup"><span data-stu-id="a5a93-124">However, if data is encountered on a second inference pass that differs from the original assumption, the schema is refined.</span></span> <span data-ttu-id="a5a93-125">В следующем примере показан процесс уточнения.</span><span class="sxs-lookup"><span data-stu-id="a5a93-125">The following example illustrates the refinement process.</span></span>  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 <span data-ttu-id="a5a93-126">В примере в качестве первого входного аргумента принимается файл `item1.xml`.</span><span class="sxs-lookup"><span data-stu-id="a5a93-126">The example takes the following file, `item1.xml`, as its first input.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 <span data-ttu-id="a5a93-127">Затем в качестве второго входного аргумента принимается файл `item2.xml`:</span><span class="sxs-lookup"><span data-stu-id="a5a93-127">The example then takes the `item2.xml` file as its second input:</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 <span data-ttu-id="a5a93-128">Когда в первом XML-документе обнаруживается атрибут `productID`, для значения `123456789` предполагается тип `xs:unsignedInt`.</span><span class="sxs-lookup"><span data-stu-id="a5a93-128">When the `productID` attribute is encountered in the first XML document, the value of `123456789` is assumed to be an `xs:unsignedInt` type.</span></span> <span data-ttu-id="a5a93-129">Однако, когда при чтении второго XML-документа обнаруживается значение `A53-246`, тип `xs:unsignedInt` больше не может предполагаться.</span><span class="sxs-lookup"><span data-stu-id="a5a93-129">However, when the second XML document is read and the value of `A53-246` is found, the `xs:unsignedInt` type can no longer be assumed.</span></span> <span data-ttu-id="a5a93-130">Схема уточняется, и тип `productID` заменяется типом `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="a5a93-130">The schema is refined and the type of `productID` is changed to `xs:string`.</span></span> <span data-ttu-id="a5a93-131">Кроме того, атрибут `minOccurs` для элемента `supplierID` получает значение `0`, поскольку во втором XML-документе отсутствует элемент `supplierID`.</span><span class="sxs-lookup"><span data-stu-id="a5a93-131">In addition, the `minOccurs` attribute for the `supplierID` element is set to `0`, because the second XML document contains no `supplierID` element.</span></span>  
  
 <span data-ttu-id="a5a93-132">Далее представлена схема, выведенная из первого XML-документа.</span><span class="sxs-lookup"><span data-stu-id="a5a93-132">The following is the schema inferred from the first XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 <span data-ttu-id="a5a93-133">Далее представлена схема, выведенная из первого XML-документа и уточненная с помощью второго XML-документа.</span><span class="sxs-lookup"><span data-stu-id="a5a93-133">The following is the schema inferred from the first XML document, refined by the second XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a><span data-ttu-id="a5a93-134">Встроенные схемы</span><span class="sxs-lookup"><span data-stu-id="a5a93-134">Inline Schemas</span></span>  

 <span data-ttu-id="a5a93-135">Если в процессе <xref:System.Xml.Schema.XmlSchemaInference> обнаруживается встроенная схема XSD, создается исключение <xref:System.Xml.Schema.XmlSchemaInferenceException>.</span><span class="sxs-lookup"><span data-stu-id="a5a93-135">If an inline XML Schema definition language (XSD) schema is encountered during the <xref:System.Xml.Schema.XmlSchemaInference> process, an <xref:System.Xml.Schema.XmlSchemaInferenceException> is thrown.</span></span> <span data-ttu-id="a5a93-136">Например, следующая встроенная схема вызывает исключение <xref:System.Xml.Schema.XmlSchemaInferenceException>.</span><span class="sxs-lookup"><span data-stu-id="a5a93-136">For example, the following inline schema throws an <xref:System.Xml.Schema.XmlSchemaInferenceException>.</span></span>  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a><span data-ttu-id="a5a93-137">Неуточняемые схемы</span><span class="sxs-lookup"><span data-stu-id="a5a93-137">Schemas that Cannot be Refined</span></span>  

 <span data-ttu-id="a5a93-138">В схемах W3C XML существуют такие конструкции, которые процесс <xref:System.Xml.Schema.XmlSchemaInference> для схемы XSD не может обработать, если задан тип для уточнения, и которые приводят к созданию исключения.</span><span class="sxs-lookup"><span data-stu-id="a5a93-138">There are W3C XML Schema constructs that the XML Schema definition language (XSD) schema <xref:System.Xml.Schema.XmlSchemaInference> process cannot handle if given a type to refine and cause an exception to be thrown.</span></span> <span data-ttu-id="a5a93-139">Например, сложный тип, на верхнем уровне которого находится компоновщик, отличный от sequence.</span><span class="sxs-lookup"><span data-stu-id="a5a93-139">Such as a complex type whose top-level compositor is anything other than a sequence.</span></span> <span data-ttu-id="a5a93-140">В модели SOM это соответствует типу <xref:System.Xml.Schema.XmlSchemaComplexType>, свойством <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> которого не является экземпляр <xref:System.Xml.Schema.XmlSchemaSequence>.</span><span class="sxs-lookup"><span data-stu-id="a5a93-140">In the Schema Object Model (SOM), this corresponds to an <xref:System.Xml.Schema.XmlSchemaComplexType> whose <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> property is not an instance of <xref:System.Xml.Schema.XmlSchemaSequence>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a93-141">См. также</span><span class="sxs-lookup"><span data-stu-id="a5a93-141">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaInference>
- [<span data-ttu-id="a5a93-142">Модель объектов схемы XML (SOM)</span><span class="sxs-lookup"><span data-stu-id="a5a93-142">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)
- [<span data-ttu-id="a5a93-143">Выведение XML-схемы</span><span class="sxs-lookup"><span data-stu-id="a5a93-143">Inferring an XML Schema</span></span>](inferring-an-xml-schema.md)
- [<span data-ttu-id="a5a93-144">Правила выведения структуры и типов узлов схемы</span><span class="sxs-lookup"><span data-stu-id="a5a93-144">Rules for Inferring Schema Node Types and Structure</span></span>](rules-for-inferring-schema-node-types-and-structure.md)
- [<span data-ttu-id="a5a93-145">Правила выведения простых типов</span><span class="sxs-lookup"><span data-stu-id="a5a93-145">Rules for Inferring Simple Types</span></span>](rules-for-inferring-simple-types.md)
