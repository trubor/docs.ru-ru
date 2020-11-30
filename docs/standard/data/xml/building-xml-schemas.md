---
title: Построение XML-схем
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
ms.openlocfilehash: 177c52ea7217821735250b297974ac0ebaa1eb2e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725382"
---
# <a name="building-xml-schemas"></a><span data-ttu-id="afea0-102">Построение XML-схем</span><span class="sxs-lookup"><span data-stu-id="afea0-102">Building XML Schemas</span></span>

<span data-ttu-id="afea0-103">Классы в пространстве имен <xref:System.Xml.Schema?displayProperty=nameWithType> сопоставляются со структурами, определенными в рекомендациях по схемам XML консорциума W3C, и могут использоваться для сборки схем XML в памяти.</span><span class="sxs-lookup"><span data-stu-id="afea0-103">The classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation and can be used to build XML schemas in-memory.</span></span>  
  
## <a name="building-an-xml-schema"></a><span data-ttu-id="afea0-104">Построение схемы XML</span><span class="sxs-lookup"><span data-stu-id="afea0-104">Building an XML Schema</span></span>  

 <span data-ttu-id="afea0-105">В следующем примере кода для построения схемы XML в памяти используется API модели SOM.</span><span class="sxs-lookup"><span data-stu-id="afea0-105">In the code examples that follow, the SOM API is used to build a customer XML schema in-memory.</span></span>  
  
### <a name="creating-element-and-attributes"></a><span data-ttu-id="afea0-106">Создание элемента и атрибутов</span><span class="sxs-lookup"><span data-stu-id="afea0-106">Creating Element and Attributes</span></span>  

 <span data-ttu-id="afea0-107">Примеры кода собирают пользовательскую схему снизу вверх, вначале создавая дочерние элементы, атрибуты и их соответствующие типы, а затем элементы верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="afea0-107">The code examples build the customer schema from the bottom up, creating the child elements, attributes, and their corresponding types first, and then the top-level elements.</span></span>  
  
 <span data-ttu-id="afea0-108">В следующем примере кода элементы `FirstName` и `LastName`, а также атрибут пользовательской схемы `CustomerId` создаются с помощью классов <xref:System.Xml.Schema.XmlSchemaElement> и <xref:System.Xml.Schema.XmlSchemaAttribute> модели SOM.</span><span class="sxs-lookup"><span data-stu-id="afea0-108">In the following code example, the `FirstName` and `LastName` elements, as well as the `CustomerId` attribute of the customer schema are created using the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes of the SOM.</span></span> <span data-ttu-id="afea0-109">Помимо свойств <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> классов <xref:System.Xml.Schema.XmlSchemaElement> и <xref:System.Xml.Schema.XmlSchemaAttribute>, соответствующих атрибуту name элементов `<xs:element />` и `<xs:attribute />` схемы XML, все остальные атрибуты, разрешенные схемой (`defaultValue`, `fixedValue`, `form` и так далее), имеют соответствующие свойства в классах <xref:System.Xml.Schema.XmlSchemaElement> и <xref:System.Xml.Schema.XmlSchemaAttribute>.</span><span class="sxs-lookup"><span data-stu-id="afea0-109">Apart from the <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> properties of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes, which correspond to the "name" attribute of the `<xs:element />` and `<xs:attribute />` elements in an XML schema, all other attributes allowed by the schema (`defaultValue`, `fixedValue`, `form`, and so on) have corresponding properties in the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a><span data-ttu-id="afea0-110">Создание типов схемы</span><span class="sxs-lookup"><span data-stu-id="afea0-110">Creating Schema Types</span></span>  

 <span data-ttu-id="afea0-111">Содержимое элементов и атрибутов определяется их типом.</span><span class="sxs-lookup"><span data-stu-id="afea0-111">The content of elements and attributes is defined by their types.</span></span> <span data-ttu-id="afea0-112">Чтобы создать элементы и атрибуты со встроенными типами схемы, свойство <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> классов <xref:System.Xml.Schema.XmlSchemaElement> или <xref:System.Xml.Schema.XmlSchemaAttribute> принимает значение соответствующего полного имени встроенного типа с помощью класса <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="afea0-112">To create elements and attributes whose types are one of the built-in schema types, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes are set with the corresponding qualified name of the built-in type using the <xref:System.Xml.XmlQualifiedName> class.</span></span> <span data-ttu-id="afea0-113">Чтобы создать определяемый пользователем тип для элементов и атрибутов, формируется новый простой или сложный тип с помощью классов <xref:System.Xml.Schema.XmlSchemaSimpleType> или <xref:System.Xml.Schema.XmlSchemaComplexType>.</span><span class="sxs-lookup"><span data-stu-id="afea0-113">To create a user-defined type for elements and attributes, a new simple or complex type is created using the <xref:System.Xml.Schema.XmlSchemaSimpleType> or <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="afea0-114">Чтобы создать неименованные простые или сложные типы, являющиеся анонимными потомками элемента или атрибута (к атрибутам применяются только простые типы), присвойте свойству <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> класса <xref:System.Xml.Schema.XmlSchemaElement> или класса <xref:System.Xml.Schema.XmlSchemaAttribute> значение неименованного простого или сложного типа, а не свойства <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> классов <xref:System.Xml.Schema.XmlSchemaElement> или <xref:System.Xml.Schema.XmlSchemaAttribute>.</span><span class="sxs-lookup"><span data-stu-id="afea0-114">To create unnamed simple or complex types that are anonymous children of an element or attribute (only simple types apply for attributes), set the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes to the unnamed simple or complex type, instead of the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> or <xref:System.Xml.Schema.XmlSchemaAttribute> classes.</span></span>  
  
 <span data-ttu-id="afea0-115">Схемы XML допускают, чтобы анонимные и именованные простые типы выводились по ограничению из других простых типов (встроенных или пользовательских) либо конструировались в виде списка или объединения других простых типов.</span><span class="sxs-lookup"><span data-stu-id="afea0-115">XML schemas allow both anonymous and named simple types to be derived by restriction from other simple types (built-in or user-defined) or constructed as a list or union of other simple types.</span></span> <span data-ttu-id="afea0-116">Класс <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> используется для создания простого типа, ограничивая встроенный тип `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="afea0-116">The <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> class is used to create a simple type by restricting the built-in `xs:string` type.</span></span> <span data-ttu-id="afea0-117">Чтобы создать тип списка или объединения, можно также использовать класс <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> или <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion>.</span><span class="sxs-lookup"><span data-stu-id="afea0-117">You can also use the <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> or <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> classes to create list or union types.</span></span> <span data-ttu-id="afea0-118">Свойство <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> обозначает, является ли оно простым типом ограничения, типом списка или объединением.</span><span class="sxs-lookup"><span data-stu-id="afea0-118">The <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> property denotes whether it is a simple type restriction, list, or union.</span></span>  
  
 <span data-ttu-id="afea0-119">В следующем примере кода тип `FirstName` элемента является встроенным типом `xs:string`, тип `LastName` - именованным простым типом, представляющим собой ограничение встроенного типа `xs:string` со значением аспекта `MaxLength`, равным 20, а тип атрибута `CustomerId` является встроенным типом `xs:positiveInteger`.</span><span class="sxs-lookup"><span data-stu-id="afea0-119">In the following code example, the `FirstName` element's type is the built-in type `xs:string`, the `LastName` element's type is a named simple type that is a restriction of the built-in type `xs:string`, with a `MaxLength` facet value of 20, and the `CustomerId` attribute's type is the built-in type `xs:positiveInteger`.</span></span> <span data-ttu-id="afea0-120">Элемент `Customer` представляет собой анонимный сложный тип, примитив которого является последовательностью элементов `FirstName` и `LastName` и атрибут которого содержит атрибут `CustomerId`.</span><span class="sxs-lookup"><span data-stu-id="afea0-120">The `Customer` element is an anonymous complex type whose particle is the sequence of the `FirstName` and `LastName` elements and whose attributes contains the `CustomerId` attribute.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="afea0-121">Классы <xref:System.Xml.Schema.XmlSchemaChoice> и <xref:System.Xml.Schema.XmlSchemaAll> можно также использовать в качестве примитивов сложного типа для репликации семантики `<xs:choice />` или `<xs:all />`.</span><span class="sxs-lookup"><span data-stu-id="afea0-121">You can also use the <xref:System.Xml.Schema.XmlSchemaChoice> or <xref:System.Xml.Schema.XmlSchemaAll> classes as the particle of the complex type to replicate `<xs:choice />` or `<xs:all />` semantics.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a><span data-ttu-id="afea0-122">Создание и компиляция схем</span><span class="sxs-lookup"><span data-stu-id="afea0-122">Creating and Compiling Schemas</span></span>  

 <span data-ttu-id="afea0-123">В этой точке дочерние элементы и атрибуты, их соответствующие типы и элемент верхнего уровня `Customer` были созданы в памяти с помощью API модели SOM.</span><span class="sxs-lookup"><span data-stu-id="afea0-123">At this point, the child elements and attributes, their corresponding types, and the top-level `Customer` element have been created in-memory using the SOM API.</span></span> <span data-ttu-id="afea0-124">В следующем примере кода с помощью класса <xref:System.Xml.Schema.XmlSchema> создается элемент схемы, к нему добавляются элементы верхнего уровня и типы с помощью свойства <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> и полная схема компилируется с помощью класса <xref:System.Xml.Schema.XmlSchemaSet> и выводится на консоль.</span><span class="sxs-lookup"><span data-stu-id="afea0-124">In the following code example, the schema element is created using the <xref:System.Xml.Schema.XmlSchema> class, the top-level elements and types are added to it using the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> property and the complete schema is compiled using the <xref:System.Xml.Schema.XmlSchemaSet> class and written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <span data-ttu-id="afea0-125">Метод <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> проверяет пользовательскую схему по правилам схемы XML и делает доступными свойства результатов проверки компиляции схемы.</span><span class="sxs-lookup"><span data-stu-id="afea0-125">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> method validates the customer schema against the rules for an XML schema and makes post-schema-compilation properties available.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="afea0-126">Все свойства результатов проверки компиляции схемы в API модели SOM отличаются от информационного набора окончательной проверки схемы.</span><span class="sxs-lookup"><span data-stu-id="afea0-126">All post-schema-compilation properties in the SOM API differ from the Post-Schema-Validation-Infoset.</span></span>  
  
 <span data-ttu-id="afea0-127">Объект <xref:System.Xml.Schema.ValidationEventHandler>, добавленный к набору <xref:System.Xml.Schema.XmlSchemaSet>, является делегатом, вызывающим метод ответного вызова `ValidationCallback` для обработки ошибок и предупреждений проверки схемы.</span><span class="sxs-lookup"><span data-stu-id="afea0-127">The <xref:System.Xml.Schema.ValidationEventHandler> added to the <xref:System.Xml.Schema.XmlSchemaSet> is a delegate that calls the callback method `ValidationCallback` to handle schema validation warnings and errors.</span></span>  
  
 <span data-ttu-id="afea0-128">Ниже приводится полный пример кода, а пользовательская схема выводится на консоль.</span><span class="sxs-lookup"><span data-stu-id="afea0-128">The following is the complete code example, and the customer schema written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="Customer">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="FirstName" type="xs:string" />  
            <xs:element name="LastName" type="tns:LastNameType" />  
         </xs:sequence>  
         <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
      </xs:complexType>  
   </xs:element>  
   <xs:simpleType name="LastNameType">  
      <xs:restriction base="xs:string">  
         <xs:maxLength value="20" />  
      </xs:restriction>  
   </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="afea0-129">См. также</span><span class="sxs-lookup"><span data-stu-id="afea0-129">See also</span></span>

- [<span data-ttu-id="afea0-130">Общие сведения об модели объектов XML-схемы</span><span class="sxs-lookup"><span data-stu-id="afea0-130">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="afea0-131">Чтение и запись XML-схем</span><span class="sxs-lookup"><span data-stu-id="afea0-131">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="afea0-132">Обход XML-схем</span><span class="sxs-lookup"><span data-stu-id="afea0-132">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="afea0-133">Изменение XML-схем</span><span class="sxs-lookup"><span data-stu-id="afea0-133">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="afea0-134">Включение или импорт XML-схем</span><span class="sxs-lookup"><span data-stu-id="afea0-134">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="afea0-135">XmlSchemaSet для компиляции схемы</span><span class="sxs-lookup"><span data-stu-id="afea0-135">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="afea0-136">Набор сведений для постсхемной компиляции</span><span class="sxs-lookup"><span data-stu-id="afea0-136">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
