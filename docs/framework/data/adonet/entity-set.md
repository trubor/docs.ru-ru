---
description: 'Дополнительные сведения: набор сущностей'
title: набор сущностей
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 4881be280e1da2d53db6fc9f526289cdcd82ee07
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724431"
---
# <a name="entity-set"></a><span data-ttu-id="79aa3-103">набор сущностей</span><span class="sxs-lookup"><span data-stu-id="79aa3-103">entity set</span></span>

<span data-ttu-id="79aa3-104">*Набор сущностей* — это логический контейнер для экземпляров [типа сущности](entity-type.md) и экземпляров любого типа, производного от этого типа сущности.</span><span class="sxs-lookup"><span data-stu-id="79aa3-104">An *entity set* is a logical container for instances of an [entity type](entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="79aa3-105">(Дополнительные сведения о производных типах см. в разделе [EDM: наследование](entity-data-model-inheritance.md).) Связь между типом сущности и набором сущностей аналогична связи между строкой и таблицей в реляционной базе данных: как строка, тип сущности Описывает структуру данных, и, как и таблица, набор сущностей содержит экземпляры данной структуры.</span><span class="sxs-lookup"><span data-stu-id="79aa3-105">(For information about derived types, see [Entity Data Model: Inheritance](entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="79aa3-106">Набор сущностей не является конструктом моделирования данных; он не описывает структуру данных.</span><span class="sxs-lookup"><span data-stu-id="79aa3-106">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="79aa3-107">Вместо этого набор сущностей обеспечивает конструкт для среды размещения или хранения (например, для среды CLR или базы данных сервера SQL), позволяя группировать экземпляры типа сущности так, чтобы они были сопоставлены хранилищу данных.</span><span class="sxs-lookup"><span data-stu-id="79aa3-107">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="79aa3-108">Набор сущностей определяется в [контейнере сущностей](entity-container.md), который является логической группировкой наборов сущностей и [наборов ассоциаций](association-set.md).</span><span class="sxs-lookup"><span data-stu-id="79aa3-108">An entity set is defined within an [entity container](entity-container.md), which is a logical grouping of entity sets and [association sets](association-set.md).</span></span>  
  
 <span data-ttu-id="79aa3-109">Чтобы экземпляр типа сущности существовал в наборе сущности, должны быть выполнены следующие условия.</span><span class="sxs-lookup"><span data-stu-id="79aa3-109">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
- <span data-ttu-id="79aa3-110">Тип экземпляра является либо тем же, что и тип сущности, в котором находится набор сущностей, либо подтипом типа сущности.</span><span class="sxs-lookup"><span data-stu-id="79aa3-110">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
- <span data-ttu-id="79aa3-111">[Ключ сущности](entity-key.md) для экземпляра уникален в пределах набора сущностей.</span><span class="sxs-lookup"><span data-stu-id="79aa3-111">The [entity key](entity-key.md) for the instance is unique within the entity set.</span></span>  
  
- <span data-ttu-id="79aa3-112">Экземпляр не существует ни в каком другом наборе сущностей.</span><span class="sxs-lookup"><span data-stu-id="79aa3-112">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="79aa3-113">Несколько наборов сущностей могут быть определены при помощи одного и того же типа сущности, однако экземпляр одного типа сущности может существовать только в одном наборе сущностей.</span><span class="sxs-lookup"><span data-stu-id="79aa3-113">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="79aa3-114">Нет необходимости определять набор сущностей для каждого типа сущности в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="79aa3-114">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79aa3-115">Пример</span><span class="sxs-lookup"><span data-stu-id="79aa3-115">Example</span></span>  

 <span data-ttu-id="79aa3-116">На приведенной ниже схеме показана концептуальная модель с тремя типами сущностей: `Book`, `Publisher` и `Author`.</span><span class="sxs-lookup"><span data-stu-id="79aa3-116">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Пример модели с тремя типами сущностей](./media/entity-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="79aa3-118">На следующей схеме показаны два набора сущностей (`Books` и `Publishers`) и набор ассоциаций (`PublishedBy`), основанный на приведенной выше концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="79aa3-118">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="79aa3-119">Бизнес-аналитика в `Books` наборе сущностей представляет экземпляр `Book` типа сущности во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="79aa3-119">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="79aa3-120">Аналогичным образом PJ представляет `Publisher` экземпляр в `Publishers` наборе сущностей.</span><span class="sxs-lookup"><span data-stu-id="79aa3-120">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="79aa3-121">Бипж представляет экземпляр `PublishedBy` ассоциации в `PublishedBy` наборе ассоциаций.</span><span class="sxs-lookup"><span data-stu-id="79aa3-121">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Снимок экрана, на котором показан пример набора.](./media/entity-set/sets-example-association.gif)  
  
 <span data-ttu-id="79aa3-123">[Entity Framework ADO.NET](./ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)), для определения концептуальных моделей.</span><span class="sxs-lookup"><span data-stu-id="79aa3-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="79aa3-124">Далее язык CSDL определяет контейнер сущностей с одним набором сущностей для каждого типа сущностей в приведенной выше концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="79aa3-124">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="79aa3-125">Обратите внимание, что имя и тип сущности для каждого набора сущностей определены при помощи атрибутов XML.</span><span class="sxs-lookup"><span data-stu-id="79aa3-125">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="79aa3-126">Предусмотрена возможность определять несколько наборов сущностей на тип (модель MEST).</span><span class="sxs-lookup"><span data-stu-id="79aa3-126">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="79aa3-127">Далее язык CSDL определяет контейнер сущностей с двумя наборами сущностей для типа сущности `Book`.</span><span class="sxs-lookup"><span data-stu-id="79aa3-127">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="79aa3-128">См. также</span><span class="sxs-lookup"><span data-stu-id="79aa3-128">See also</span></span>

- [<span data-ttu-id="79aa3-129">Основные понятия модели EDM</span><span class="sxs-lookup"><span data-stu-id="79aa3-129">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="79aa3-130">EDM (модель данных с использованием сущностей)</span><span class="sxs-lookup"><span data-stu-id="79aa3-130">Entity Data Model</span></span>](entity-data-model.md)
