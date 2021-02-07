---
description: 'Дополнительные сведения: окончание ассоциации'
title: конечная точка ассоциации
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 4a166c0bdb61d1b5fad07a052518a78a74c54e23
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697664"
---
# <a name="association-end"></a><span data-ttu-id="15099-103">конечная точка ассоциации</span><span class="sxs-lookup"><span data-stu-id="15099-103">association end</span></span>

<span data-ttu-id="15099-104">Элемент *ассоциации* определяет [тип сущности](entity-type.md) на одном конце [ассоциации](association-type.md) и число экземпляров типа сущности, которые могут существовать в этом конце ассоциации.</span><span class="sxs-lookup"><span data-stu-id="15099-104">An *association end* identifies the [entity type](entity-type.md) on one end of an [association](association-type.md) and the number of entity type instances that can exist at that end of an association.</span></span> <span data-ttu-id="15099-105">Элементы ассоциации определяются при определении ассоциации; ассоциация должна иметь два элемента.</span><span class="sxs-lookup"><span data-stu-id="15099-105">Association ends are defined as part of an association; an association must have exactly two association ends.</span></span> <span data-ttu-id="15099-106">[Свойства навигации](navigation-property.md) позволяют переходить от одного элемента связи к другому.</span><span class="sxs-lookup"><span data-stu-id="15099-106">[Navigation properties](navigation-property.md) allow for navigation from one association end to the other.</span></span>  
  
 <span data-ttu-id="15099-107">Определение конечной точки ассоциации содержит следующую информацию.</span><span class="sxs-lookup"><span data-stu-id="15099-107">An association end definition contains the following information:</span></span>  
  
- <span data-ttu-id="15099-108">Один из типов сущности, участвующий в ассоциации.</span><span class="sxs-lookup"><span data-stu-id="15099-108">One of the entity types involved in the association.</span></span> <span data-ttu-id="15099-109">(обязательно)</span><span class="sxs-lookup"><span data-stu-id="15099-109">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="15099-110">Для одной ассоциации тип сущности, указанный для каждой конечной точки ассоциации, может быть одним и тем же.</span><span class="sxs-lookup"><span data-stu-id="15099-110">For a given association, the entity type specified for each association end can be the same.</span></span> <span data-ttu-id="15099-111">Так создается самоассоциация.</span><span class="sxs-lookup"><span data-stu-id="15099-111">This creates a self-association.</span></span>  
  
- <span data-ttu-id="15099-112">[Кратность окончания ассоциации](association-end-multiplicity.md) , указывающая количество экземпляров типа сущности, которые могут находиться на одном конце ассоциации.</span><span class="sxs-lookup"><span data-stu-id="15099-112">An [association end multiplicity](association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="15099-113">Кратность окончания ассоциации может иметь значение один (1), ноль или один (0.. 1) или многие ( \* ).</span><span class="sxs-lookup"><span data-stu-id="15099-113">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span>  
  
- <span data-ttu-id="15099-114">Имя для элемента ассоциации.</span><span class="sxs-lookup"><span data-stu-id="15099-114">A name for the association end.</span></span> <span data-ttu-id="15099-115">(необязательно)</span><span class="sxs-lookup"><span data-stu-id="15099-115">(Optional)</span></span>  
  
- <span data-ttu-id="15099-116">Сведения об операциях, которые выполняются на конечной точке ассоциации, например каскадная операция удаления.</span><span class="sxs-lookup"><span data-stu-id="15099-116">Information about operations that are performed on the association end, such as cascade on delete.</span></span> <span data-ttu-id="15099-117">(необязательно)</span><span class="sxs-lookup"><span data-stu-id="15099-117">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="15099-118">Пример</span><span class="sxs-lookup"><span data-stu-id="15099-118">Example</span></span>  

 <span data-ttu-id="15099-119">На приведенной ниже схеме показана концептуальная модель с двумя ассоциациями: `PublishedBy` и `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="15099-119">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="15099-120">Конечные точки ассоциации для ассоциации `PublishedBy` - это типы сущности `Book` и `Publisher`.</span><span class="sxs-lookup"><span data-stu-id="15099-120">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="15099-121">Кратность `Publisher` конца равна единице (1), а кратность `Book` End — many ( \* ), что означает, что издатель публикует много книг, а книга публикуется одним издателем.</span><span class="sxs-lookup"><span data-stu-id="15099-121">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![Пример модели с тремя типами сущностей](./media/association-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="15099-123">Entity Framework ADO.NET использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)), для определения концептуальных моделей.</span><span class="sxs-lookup"><span data-stu-id="15099-123">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="15099-124">Ниже язык определения концептуальной схемы определяет ассоциацию `PublishedBy`, которая ранее приводилась в схеме.</span><span class="sxs-lookup"><span data-stu-id="15099-124">The CSDL below defines the `PublishedBy` association shown in the diagram above.</span></span> <span data-ttu-id="15099-125">Обратите внимание, что тип, имя и кратность каждой конечной точки ассоциации указаны атрибутами XML (атрибуты `Type`, `Role` и `Multiplicity` соответственно).</span><span class="sxs-lookup"><span data-stu-id="15099-125">Note that the type, name, and multiplicity of each association end are specified by XML attributes (the `Type`, `Role`, and `Multiplicity` attributes, respectively).</span></span> <span data-ttu-id="15099-126">Дополнительные сведения об операциях, выполненных на конечной точке, указываются в элементе XML (элемент `OnDelete`).</span><span class="sxs-lookup"><span data-stu-id="15099-126">Optional information about operations performed on an end is specified in an XML element (the `OnDelete` element).</span></span> <span data-ttu-id="15099-127">В данном случае, если издатель удаляется, удаляются и все связанные книги.</span><span class="sxs-lookup"><span data-stu-id="15099-127">In this case, if a publisher is deleted, so are all associated books.</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a><span data-ttu-id="15099-128">См. также</span><span class="sxs-lookup"><span data-stu-id="15099-128">See also</span></span>

- [<span data-ttu-id="15099-129">Основные понятия модели EDM</span><span class="sxs-lookup"><span data-stu-id="15099-129">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="15099-130">EDM (модель данных с использованием сущностей)</span><span class="sxs-lookup"><span data-stu-id="15099-130">Entity Data Model</span></span>](entity-data-model.md)
