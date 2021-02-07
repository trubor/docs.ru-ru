---
description: Дополнительные сведения о свойстве внешнего ключа
title: свойство внешнего ключа
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: 1666e4477c09dd5d0ed3d2c35a93ca21824e8a0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724132"
---
# <a name="foreign-key-property"></a><span data-ttu-id="f32d3-103">свойство внешнего ключа</span><span class="sxs-lookup"><span data-stu-id="f32d3-103">foreign key property</span></span>

<span data-ttu-id="f32d3-104">*Свойство внешнего ключа* в EDM (EDM) является [свойством](property.md) типа-примитива (или набором свойств типа-примитива) для [типа сущности](entity-type.md) , который содержит [ключ сущности](entity-key.md) другого типа сущности.</span><span class="sxs-lookup"><span data-stu-id="f32d3-104">A *foreign key property* in the Entity Data Model (EDM) is a primitive type [property](property.md) (or a set of primitive type properties) on an [entity type](entity-type.md) that contains the [entity key](entity-key.md) of another entity type.</span></span>  
  
 <span data-ttu-id="f32d3-105">Свойство внешнего ключа схоже со столбцом внешнего ключа в реляционной базе данных.</span><span class="sxs-lookup"><span data-stu-id="f32d3-105">A foreign key property is analogous to a foreign key column in a relational database.</span></span> <span data-ttu-id="f32d3-106">Так же, как внешние ключевые столбцы используются в реляционной базе данных для создания связей между строками в таблицах, свойства внешнего ключа в концептуальной модели используются для установления [связей](association-type.md) между типами сущностей.</span><span class="sxs-lookup"><span data-stu-id="f32d3-106">In the same way that foreign key columns are used in a relational database to create relationships between rows in tables, foreign key properties in a conceptual model are used to establish [associations](association-type.md) between entity types.</span></span> <span data-ttu-id="f32d3-107">[Ограничение ссылочной целостности](referential-integrity-constraint.md) используется для определения ассоциации между двумя типами сущностей, если один из типов имеет внешнее ключевое свойство.</span><span class="sxs-lookup"><span data-stu-id="f32d3-107">A [referential integrity constraint](referential-integrity-constraint.md) is used to define an association between two entity types when one of the types has a foreign key property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f32d3-108">Пример</span><span class="sxs-lookup"><span data-stu-id="f32d3-108">Example</span></span>  

 <span data-ttu-id="f32d3-109">На приведенной ниже схеме показана концептуальная модель с тремя типами сущностей: `Book`, `Publisher` и `Author`.</span><span class="sxs-lookup"><span data-stu-id="f32d3-109">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="f32d3-110">Тип сущности `Book` имеет свойство `PublisherId`, которое ссылается на ключ сущности типа сущности `Publisher` при определении ограничения ссылочной целостности ассоциации `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="f32d3-110">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="f32d3-111">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Пример модели ссылочного ограничения")</span><span class="sxs-lookup"><span data-stu-id="f32d3-111">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="f32d3-112">[Entity Framework ADO.NET](./ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)), для определения концептуальных моделей.</span><span class="sxs-lookup"><span data-stu-id="f32d3-112">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="f32d3-113">Следующий язык CSDL использует свойство внешнего ключа `PublisherId` для определения ограничения ссылочной целостности в ассоциации `PublishedBy`, приведенной ранее в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="f32d3-113">The following CSDL uses the foreign key property `PublisherId` to define a referential integrity constraint on the `PublishedBy` association shown in the conceptual model shown above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="f32d3-114">См. также</span><span class="sxs-lookup"><span data-stu-id="f32d3-114">See also</span></span>

- [<span data-ttu-id="f32d3-115">Основные понятия модели EDM</span><span class="sxs-lookup"><span data-stu-id="f32d3-115">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="f32d3-116">EDM (модель данных с использованием сущностей)</span><span class="sxs-lookup"><span data-stu-id="f32d3-116">Entity Data Model</span></span>](entity-data-model.md)
