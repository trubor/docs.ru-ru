---
description: 'Дополнительные сведения: тип ассоциации'
title: тип ассоциации
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 4df84d97c798e9f2d06e0f5dce442e05cb4c67b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697560"
---
# <a name="association-type"></a><span data-ttu-id="98c6e-103">тип ассоциации</span><span class="sxs-lookup"><span data-stu-id="98c6e-103">association type</span></span>

<span data-ttu-id="98c6e-104">*Тип ассоциации* (называемый также Ассоциацией) — это фундаментальный Стандартный блок для описания связей в EDM (EDM).</span><span class="sxs-lookup"><span data-stu-id="98c6e-104">An *association type* (also called an association) is the fundamental building block for describing relationships in the Entity Data Model (EDM).</span></span> <span data-ttu-id="98c6e-105">В концептуальной модели Ассоциация представляет связь между двумя [типами сущностей](entity-type.md) (например `Customer` , и `Order` ).</span><span class="sxs-lookup"><span data-stu-id="98c6e-105">In a conceptual model, an association represents a relationship between two [entity types](entity-type.md) (such as `Customer` and `Order`).</span></span> <span data-ttu-id="98c6e-106">В приложении экземпляр ассоциации представляет собой специфическую ассоциацию (такую как ассоциация между экземпляром `Customer` и экземпляром `Order`).</span><span class="sxs-lookup"><span data-stu-id="98c6e-106">In an application, an instance of an association represents a specific association (such as an association between an instance of `Customer` and an instance of `Order`).</span></span> <span data-ttu-id="98c6e-107">Экземпляры ассоциаций логически группируются в [набор ассоциаций](association-set.md).</span><span class="sxs-lookup"><span data-stu-id="98c6e-107">Association instances are logically grouped in an [association set](association-set.md).</span></span>  
  
 <span data-ttu-id="98c6e-108">Определение ассоциации содержит следующую информацию.</span><span class="sxs-lookup"><span data-stu-id="98c6e-108">An association definition contains the following information:</span></span>  
  
- <span data-ttu-id="98c6e-109">Уникальное имя.</span><span class="sxs-lookup"><span data-stu-id="98c6e-109">A unique name.</span></span> <span data-ttu-id="98c6e-110">(обязательно)</span><span class="sxs-lookup"><span data-stu-id="98c6e-110">(Required)</span></span>  
  
- <span data-ttu-id="98c6e-111">Две [ассоциации завершаются](association-end.md), по одной для каждого типа сущности в связи.</span><span class="sxs-lookup"><span data-stu-id="98c6e-111">Two [association ends](association-end.md), one for each entity type in the relationship.</span></span> <span data-ttu-id="98c6e-112">(обязательно)</span><span class="sxs-lookup"><span data-stu-id="98c6e-112">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="98c6e-113">Ассоциация не может представлять связь между более чем двумя типами сущностей.</span><span class="sxs-lookup"><span data-stu-id="98c6e-113">An association cannot represent a relationship among more than two entity types.</span></span> <span data-ttu-id="98c6e-114">Ассоциация может, тем не менее, определять связь с самим собой посредством указания одного и того же типа сущности для каждой из его конечных точек ассоциаций.</span><span class="sxs-lookup"><span data-stu-id="98c6e-114">An association can, however, define a self-relationship by specifying the same entity type for each of its association ends.</span></span>  
  
- <span data-ttu-id="98c6e-115">[Ограничение ссылочной целостности](referential-integrity-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="98c6e-115">A [referential integrity constraint](referential-integrity-constraint.md).</span></span> <span data-ttu-id="98c6e-116">(необязательно)</span><span class="sxs-lookup"><span data-stu-id="98c6e-116">(Optional)</span></span>  
  
 <span data-ttu-id="98c6e-117">Каждый элемент ассоциации должен указывать количество [элементов ассоциации](association-end-multiplicity.md) , которое указывает число экземпляров типа сущности, которые могут находиться на одном конце ассоциации.</span><span class="sxs-lookup"><span data-stu-id="98c6e-117">Each association end must specify an [association end multiplicity](association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="98c6e-118">Кратность окончания ассоциации может иметь значение один (1), ноль или один (0.. 1) или многие ( \* ).</span><span class="sxs-lookup"><span data-stu-id="98c6e-118">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span> <span data-ttu-id="98c6e-119">Доступ к экземплярам типа сущности на одном конце ассоциации возможен через [Свойства навигации](navigation-property.md) или внешние ключи, если они представлены в типе сущности.</span><span class="sxs-lookup"><span data-stu-id="98c6e-119">Entity type instances at one end of an association can be accessed through [navigation properties](navigation-property.md) or foreign keys if they are exposed on an entity type.</span></span> <span data-ttu-id="98c6e-120">Дополнительные сведения см. в разделе [EDM: внешние ключи](foreign-key-property.md).</span><span class="sxs-lookup"><span data-stu-id="98c6e-120">For more information, see [Entity Data Model: Foreign Keys](foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98c6e-121">Пример</span><span class="sxs-lookup"><span data-stu-id="98c6e-121">Example</span></span>  

 <span data-ttu-id="98c6e-122">На приведенной ниже схеме показана концептуальная модель с двумя ассоциациями: `PublishedBy` и `WrittenBy`.</span><span class="sxs-lookup"><span data-stu-id="98c6e-122">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="98c6e-123">Конечные точки ассоциации для ассоциации `PublishedBy` - это типы сущности `Book` и `Publisher`.</span><span class="sxs-lookup"><span data-stu-id="98c6e-123">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="98c6e-124">Кратность `Publisher` конца равна единице (1), а кратность `Book` End — many ( \* ), что означает, что издатель публикует много книг, а книга публикуется одним издателем.</span><span class="sxs-lookup"><span data-stu-id="98c6e-124">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![Пример модели с тремя типами сущностей](./media/association-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="98c6e-126">[Entity Framework ADO.NET](./ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)), для определения концептуальных моделей.</span><span class="sxs-lookup"><span data-stu-id="98c6e-126">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="98c6e-127">Далее язык CSDL определяет ассоциацию `PublishedBy`, которая ранее приводилась в схеме.</span><span class="sxs-lookup"><span data-stu-id="98c6e-127">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="98c6e-128">См. также</span><span class="sxs-lookup"><span data-stu-id="98c6e-128">See also</span></span>

- [<span data-ttu-id="98c6e-129">Основные понятия модели EDM</span><span class="sxs-lookup"><span data-stu-id="98c6e-129">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="98c6e-130">EDM (модель данных с использованием сущностей)</span><span class="sxs-lookup"><span data-stu-id="98c6e-130">Entity Data Model</span></span>](entity-data-model.md)
