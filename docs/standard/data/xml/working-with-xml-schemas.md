---
title: Работа с XML-схемами
ms.date: 03/30/2017
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
ms.openlocfilehash: 0290cd31d9477d2c5a30a6efa907263fed137258
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675494"
---
# <a name="working-with-xml-schemas"></a><span data-ttu-id="524de-102">Работа с XML-схемами</span><span class="sxs-lookup"><span data-stu-id="524de-102">Working with XML Schemas</span></span>

<span data-ttu-id="524de-103">Чтобы определить структуру XML-документа, связи его элементов, типы данных, ограничения на содержимое, используется определение типа документа (DTD) или схема XSD.</span><span class="sxs-lookup"><span data-stu-id="524de-103">To define the structure of an XML document, as well as its element relationships, data types, and content constraints, you use a document type definition (DTD) or XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="524de-104">XML-документ имеет правильный формат, если он соответствует всем синтаксическим требованиям Рекомендации консорциума W3C по языку XML 1.0. Однако документ считается допустимым только в том случае, если он одновременно имеет правильный формат и соответствует ограничениям, заданным определением DTD или схемой.</span><span class="sxs-lookup"><span data-stu-id="524de-104">Although an XML document is considered to be well-formed if it meets all the syntactical requirements defined by the World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0 Recommendation, it is not considered valid unless it is both well-formed and conforms to the constraints defined by its DTD or schema.</span></span> <span data-ttu-id="524de-105">Следовательно, хотя все допустимые XML-документы имеют правильный формат, не все XML-документы правильного формата, являются допустимыми.</span><span class="sxs-lookup"><span data-stu-id="524de-105">Therefore, although all valid XML documents are well-formed, not all well-formed XML documents are valid.</span></span>  
  
 <span data-ttu-id="524de-106">Дополнительные сведения о XML см. в [документации консорциума W3C по XML 1.0](https://www.w3.org/TR/REC-xml/).</span><span class="sxs-lookup"><span data-stu-id="524de-106">For more information about XML, see the [W3C XML 1.0 Recommendation](https://www.w3.org/TR/REC-xml/).</span></span> <span data-ttu-id="524de-107">Для получения дополнительных сведений о XML-схеме см. документы [W3C XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/) (XML-схема W3C. Часть 1. Рекомендации по структурам) и [W3C XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/) (XML-схема W3C. Часть 1. Рекомендации по типам данных).</span><span class="sxs-lookup"><span data-stu-id="524de-107">For more information about XML Schema, see the [W3C XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/) and the [W3C XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="524de-108">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="524de-108">In This Section</span></span>  

 [<span data-ttu-id="524de-109">Модель объектов схемы XML (SOM)</span><span class="sxs-lookup"><span data-stu-id="524de-109">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)  
 <span data-ttu-id="524de-110">Обсуждается модель SOM в пространстве имен <xref:System.Xml.Schema?displayProperty=nameWithType>, предоставляющем набор классов, который позволяет считывать схему XSD из файла или создавать ее в памяти программным образом.</span><span class="sxs-lookup"><span data-stu-id="524de-110">Discusses the Schema Object Model (SOM) in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that provides a set of classes that allows you to read a Schema definition language (XSD) schema from a file or programmatically create a schema in-memory.</span></span>  
  
 [<span data-ttu-id="524de-111">XmlSchemaSet для компиляции схемы</span><span class="sxs-lookup"><span data-stu-id="524de-111">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)  
 <span data-ttu-id="524de-112">Обсуждается класс <xref:System.Xml.Schema.XmlSchemaSet>, представляющий собой кэш, где могут храниться и проверяться схемы XSD.</span><span class="sxs-lookup"><span data-stu-id="524de-112">Discusses the <xref:System.Xml.Schema.XmlSchemaSet> class that is a cache where XSD schemas can be stored and validated.</span></span>  
  
 [<span data-ttu-id="524de-113">Принудительная проверка с помощью XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="524de-113">XmlSchemaValidator Push-Based Validation</span></span>](xmlschemavalidator-push-based-validation.md)  
 <span data-ttu-id="524de-114">Обсуждается класс <xref:System.Xml.Schema.XmlSchemaValidator>, предоставляющий эффективный, высокопроизводительный механизм проверки XML-данных по схемам XSD в принудительном порядке.</span><span class="sxs-lookup"><span data-stu-id="524de-114">Discusses the <xref:System.Xml.Schema.XmlSchemaValidator> class that provides an efficient, high-performance mechanism to validate XML data against XSD schemas in a push-based manner.</span></span>  
  
 [<span data-ttu-id="524de-115">Выведение XML-схемы</span><span class="sxs-lookup"><span data-stu-id="524de-115">Inferring an XML Schema</span></span>](inferring-an-xml-schema.md)  
 <span data-ttu-id="524de-116">Обсуждается применение класса <xref:System.Xml.Schema.XmlSchemaInference> для выведения схемы XSD из структуры XML-документа.</span><span class="sxs-lookup"><span data-stu-id="524de-116">Discusses how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XSD schema from the structure of an XML document.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="524de-117">Справочник</span><span class="sxs-lookup"><span data-stu-id="524de-117">Reference</span></span>  

 <span data-ttu-id="524de-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="524de-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="524de-119">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="524de-119">Related Sections</span></span>  

 [<span data-ttu-id="524de-120">Проверка XML-документа в модели DOM</span><span class="sxs-lookup"><span data-stu-id="524de-120">Validating an XML Document in the DOM</span></span>](validating-an-xml-document-in-the-dom.md)  
 <span data-ttu-id="524de-121">Обсуждается проверка XML в модели DOM.</span><span class="sxs-lookup"><span data-stu-id="524de-121">Discusses how to validate the XML in the Document Object Model (DOM).</span></span> <span data-ttu-id="524de-122">XML можно проверять по мере загрузки в DOM, или проверять ранее не проверенный XML-документ в модели DOM.</span><span class="sxs-lookup"><span data-stu-id="524de-122">You can validate the XML as it is loaded into the DOM, or validate a previously unvalidated XML document in the DOM.</span></span>  
  
 [<span data-ttu-id="524de-123">Проверка по схеме с помощью XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="524de-123">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="524de-124">Обсуждается проверка XML-документа, по которому производится перемещение и изменение с помощью класса <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="524de-124">Discusses how to validate XML being navigated and edited using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
