---
description: 'Дополнительные сведения: окончание набора ассоциаций'
title: конечная точка набора ассоциаций
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 12e01a3fb947f6fabd5e1a93ef475132418963df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697677"
---
# <a name="association-set-end"></a><span data-ttu-id="54811-103">конечная точка набора ассоциаций</span><span class="sxs-lookup"><span data-stu-id="54811-103">association set end</span></span>

<span data-ttu-id="54811-104">*Конец набора ассоциаций* определяет [тип сущности](entity-type.md) и [набор сущностей](entity-set.md) в конце [набора ассоциаций](association-set.md).</span><span class="sxs-lookup"><span data-stu-id="54811-104">An *association set end* identifies the [entity type](entity-type.md) and the [entity set](entity-set.md) at the end of an [association set](association-set.md).</span></span> <span data-ttu-id="54811-105">Конечные точки набора ассоциаций определяются как часть набора ассоциаций; набор ассоциаций должен иметь ровно две конечные точки.</span><span class="sxs-lookup"><span data-stu-id="54811-105">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="54811-106">Определение конечной точки набора ассоциаций содержит следующую информацию.</span><span class="sxs-lookup"><span data-stu-id="54811-106">An association set end definition contains the following information:</span></span>  
  
- <span data-ttu-id="54811-107">Один из типов сущностей, участвующих в наборе ассоциаций.</span><span class="sxs-lookup"><span data-stu-id="54811-107">One of the entity types involved in the association set.</span></span> <span data-ttu-id="54811-108">(обязательно)</span><span class="sxs-lookup"><span data-stu-id="54811-108">(Required)</span></span>  
  
- <span data-ttu-id="54811-109">Набор сущностей для типа сущностей, участвующих в наборе ассоциаций.</span><span class="sxs-lookup"><span data-stu-id="54811-109">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="54811-110">(обязательно)</span><span class="sxs-lookup"><span data-stu-id="54811-110">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="54811-111">Пример</span><span class="sxs-lookup"><span data-stu-id="54811-111">Example</span></span>  

 <span data-ttu-id="54811-112">На приведенной ниже схеме показана концептуальная модель с двумя ассоциациями: `WrittenBy` и `PublishedBy`.</span><span class="sxs-lookup"><span data-stu-id="54811-112">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![Пример модели с тремя типами сущностей](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="54811-114">На следующей схеме показаны один набор ассоциаций (`PublishedBy` и `Books`) и два набора сущностей (`Publishers`) на основе приведенной выше концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="54811-114">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="54811-115">Конечные точки набора ассоциаций - это наборы сущностей `Books` и `Publishers`.</span><span class="sxs-lookup"><span data-stu-id="54811-115">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="54811-116">Бизнес-аналитика в `Books` наборе сущностей представляет экземпляр `Book` типа сущности во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="54811-116">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="54811-117">Аналогичным образом PJ представляет `Publisher` экземпляр в `Publishers` наборе сущностей.</span><span class="sxs-lookup"><span data-stu-id="54811-117">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="54811-118">Бипж представляет экземпляр `PublishedBy` ассоциации в `PublishedBy` наборе ассоциаций.</span><span class="sxs-lookup"><span data-stu-id="54811-118">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![Снимок экрана, на котором показан пример набора.](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="54811-120">В [Entity Framework ADO.NET](./ef/index.md) для определения концептуальных моделей используется DSL, именуемое языком определения концептуальной схемы ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)).</span><span class="sxs-lookup"><span data-stu-id="54811-120">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="54811-121">Далее на языке CSDL определяется контейнер сущностей с одним набором ассоциаций для каждой ассоциации на приведенной выше схеме.</span><span class="sxs-lookup"><span data-stu-id="54811-121">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="54811-122">Обратите внимание, что конечные точки набора ассоциаций определяются как часть каждого определения набора ассоциаций.</span><span class="sxs-lookup"><span data-stu-id="54811-122">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="54811-123">См. также</span><span class="sxs-lookup"><span data-stu-id="54811-123">See also</span></span>

- [<span data-ttu-id="54811-124">Основные понятия модели EDM</span><span class="sxs-lookup"><span data-stu-id="54811-124">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="54811-125">EDM (модель данных с использованием сущностей)</span><span class="sxs-lookup"><span data-stu-id="54811-125">Entity Data Model</span></span>](entity-data-model.md)
