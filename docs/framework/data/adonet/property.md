---
description: 'Дополнительные сведения: свойство'
title: свойство;
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 8b25c19b0673817945fa6cc786589346462f7e61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754330"
---
# <a name="property"></a><span data-ttu-id="2168d-103">свойство;</span><span class="sxs-lookup"><span data-stu-id="2168d-103">property</span></span>

<span data-ttu-id="2168d-104">*Свойства* являются фундаментальными строительными блоками [типов сущностей](entity-type.md) и [сложных типов](complex-type.md).</span><span class="sxs-lookup"><span data-stu-id="2168d-104">*Properties* are the fundamental building blocks of [entity types](entity-type.md) and [complex types](complex-type.md).</span></span> <span data-ttu-id="2168d-105">Свойства определяют форму и характеристики данных, которые экземпляр типа сущности или сложного типа будет содержать.</span><span class="sxs-lookup"><span data-stu-id="2168d-105">Properties define the shape and characteristics of data that an entity type instance or complex type instance will contain.</span></span> <span data-ttu-id="2168d-106">Свойства в концептуальной модели аналогичны свойствам, которые определены применительно к классу.</span><span class="sxs-lookup"><span data-stu-id="2168d-106">Properties in a conceptual model are analogous to properties defined on a class.</span></span> <span data-ttu-id="2168d-107">По такому же принципу, как свойства, относящиеся к классу, определяют форму класса и несут информацию об объектах, свойства в концептуальной модели определяют форму типа сущности и несут информацию об экземплярах типа сущности.</span><span class="sxs-lookup"><span data-stu-id="2168d-107">In the same way that properties on a class define the shape of the class and carry information about objects, properties in a conceptual model define the shape of an entity type and carry information about entity type instances.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2168d-108">Свойства, как они описаны в этом разделе, отличаются от свойств навигации.</span><span class="sxs-lookup"><span data-stu-id="2168d-108">Properties, as described in this topic, are different from navigation properties.</span></span> <span data-ttu-id="2168d-109">Дополнительные сведения см. в разделе [Свойства навигации](navigation-property.md).</span><span class="sxs-lookup"><span data-stu-id="2168d-109">For more information, see [navigation properties](navigation-property.md).</span></span>  
  
 <span data-ttu-id="2168d-110">Определение свойства содержит следующую информацию.</span><span class="sxs-lookup"><span data-stu-id="2168d-110">A property definition contains the following information:</span></span>  
  
- <span data-ttu-id="2168d-111">Имя свойства.</span><span class="sxs-lookup"><span data-stu-id="2168d-111">A property name.</span></span> <span data-ttu-id="2168d-112">(обязательно)</span><span class="sxs-lookup"><span data-stu-id="2168d-112">(Required)</span></span>  
  
- <span data-ttu-id="2168d-113">Тип свойства.</span><span class="sxs-lookup"><span data-stu-id="2168d-113">A property type.</span></span> <span data-ttu-id="2168d-114">(обязательно)</span><span class="sxs-lookup"><span data-stu-id="2168d-114">(Required)</span></span>  
  
- <span data-ttu-id="2168d-115">Набор [аспектов](facet.md).</span><span class="sxs-lookup"><span data-stu-id="2168d-115">A set of [facets](facet.md).</span></span> <span data-ttu-id="2168d-116">(необязательно)</span><span class="sxs-lookup"><span data-stu-id="2168d-116">(Optional)</span></span>  
  
 <span data-ttu-id="2168d-117">Свойство может содержать примитивные данные (такие как строка, целое число, логическое значение) или структурированные данные (такие как сложный тип).</span><span class="sxs-lookup"><span data-stu-id="2168d-117">A property can contain primitive data (such as a string, an integer, or a Boolean value), or structured data (such as a complex type).</span></span> <span data-ttu-id="2168d-118">Свойства примитивного типа также называются скалярными свойствами.</span><span class="sxs-lookup"><span data-stu-id="2168d-118">Properties that are of primitive type are also called scalar properties.</span></span> <span data-ttu-id="2168d-119">Дополнительные сведения см. в разделе [EDM: примитивные типы данных](entity-data-model-primitive-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="2168d-119">For more information, see [Entity Data Model: Primitive Data Types](entity-data-model-primitive-data-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2168d-120">Сложный тип может сам по себе иметь свойства, которые являются сложными типами.</span><span class="sxs-lookup"><span data-stu-id="2168d-120">A complex type can, itself, have properties that are complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2168d-121">Пример</span><span class="sxs-lookup"><span data-stu-id="2168d-121">Example</span></span>  

 <span data-ttu-id="2168d-122">На приведенной ниже схеме показана концептуальная модель с тремя типами сущностей: `Book`, `Publisher` и `Author`.</span><span class="sxs-lookup"><span data-stu-id="2168d-122">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="2168d-123">Каждый тип сущности имеет несколько свойств, однако сведений о типе для каждого свойства в схеме не содержится.</span><span class="sxs-lookup"><span data-stu-id="2168d-123">Each entity type has several properties, although type information for each property is not conveyed in the diagram.</span></span> <span data-ttu-id="2168d-124">Свойства, являющиеся [ключами сущности](entity-key.md) , обозначаются ключевыми знаками (Key).</span><span class="sxs-lookup"><span data-stu-id="2168d-124">Properties that are [entity keys](entity-key.md) are denoted with (Key).</span></span>  
  
 ![Пример модели с тремя типами сущностей](./media/property/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="2168d-126">[Entity Framework ADO.NET](./ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)), для определения концептуальных моделей.</span><span class="sxs-lookup"><span data-stu-id="2168d-126">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="2168d-127">Далее на языке CSDL определяется тип сущности `Book` (как показано на схеме выше), и при помощи атрибутов XML указываются тип и имя каждого свойства.</span><span class="sxs-lookup"><span data-stu-id="2168d-127">The following CSDL defines the `Book` entity type (as shown in the diagram above) and indicates the type and name of each property by using XML attributes.</span></span> <span data-ttu-id="2168d-128">Дополнительный аспект, `Nullable`, также определяется при помощи атрибута XML.</span><span class="sxs-lookup"><span data-stu-id="2168d-128">An optional facet, `Nullable`, is also defined by using an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="2168d-129">Ни одно из свойств на схеме не может быть свойством сложного типа.</span><span class="sxs-lookup"><span data-stu-id="2168d-129">It is possible that one of the properties shown in the diagram is a complex type property.</span></span> <span data-ttu-id="2168d-130">Например, свойство `Address` в типе сущности `Publisher` может быть свойством сложного типа, состоящего из нескольких скалярных свойств, таких как `StreetAddress`, `City`, `StateOrProvince`, `Country` и `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="2168d-130">For example, the `Address` property on the `Publisher` entity type could be a complex type property composed of several scalar properties, such as `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span> <span data-ttu-id="2168d-131">Представление такого сложного типа на языке CSDL может быть следующим.</span><span class="sxs-lookup"><span data-stu-id="2168d-131">The CSDL representation of such a complex type would be as follows:</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="2168d-132">См. также</span><span class="sxs-lookup"><span data-stu-id="2168d-132">See also</span></span>

- [<span data-ttu-id="2168d-133">Основные понятия модели EDM</span><span class="sxs-lookup"><span data-stu-id="2168d-133">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="2168d-134">EDM (модель данных с использованием сущностей)</span><span class="sxs-lookup"><span data-stu-id="2168d-134">Entity Data Model</span></span>](entity-data-model.md)
