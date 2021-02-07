---
description: 'Дополнительные сведения: тип сущности'
title: тип сущности
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: fb801ca8565fce01466f30bddc8c14c39af568c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724366"
---
# <a name="entity-type"></a><span data-ttu-id="73893-103">тип сущности</span><span class="sxs-lookup"><span data-stu-id="73893-103">entity type</span></span>

<span data-ttu-id="73893-104">*Тип сущности* является фундаментальным стандартным блоком для описания структуры данных с помощью EDM (EDM).</span><span class="sxs-lookup"><span data-stu-id="73893-104">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="73893-105">В концептуальной модели тип сущности представляет структуру основных концептуальных элементов верхнего уровня, таких как клиенты или заказы.</span><span class="sxs-lookup"><span data-stu-id="73893-105">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="73893-106">Тип сущности - это шаблон для экземпляров типов сущностей.</span><span class="sxs-lookup"><span data-stu-id="73893-106">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="73893-107">Каждый шаблон содержит следующие сведения.</span><span class="sxs-lookup"><span data-stu-id="73893-107">Each template contains the following information:</span></span>  
  
- <span data-ttu-id="73893-108">Уникальное имя.</span><span class="sxs-lookup"><span data-stu-id="73893-108">A unique name.</span></span> <span data-ttu-id="73893-109">(Обязательно).</span><span class="sxs-lookup"><span data-stu-id="73893-109">(Required.)</span></span>  
  
- <span data-ttu-id="73893-110">[Ключ сущности](entity-key.md) , определенный одним или несколькими свойствами.</span><span class="sxs-lookup"><span data-stu-id="73893-110">An [entity key](entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="73893-111">(Обязательно).</span><span class="sxs-lookup"><span data-stu-id="73893-111">(Required.)</span></span>  
  
- <span data-ttu-id="73893-112">Данные в виде [свойств](property.md).</span><span class="sxs-lookup"><span data-stu-id="73893-112">Data in the form of [properties](property.md).</span></span> <span data-ttu-id="73893-113">(Необязательно.)</span><span class="sxs-lookup"><span data-stu-id="73893-113">(Optional.)</span></span>  
  
- <span data-ttu-id="73893-114">[Свойства навигации](navigation-property.md) , позволяющие переходить с одного [конца](association-end.md) [ассоциации](association-type.md) на другой конец.</span><span class="sxs-lookup"><span data-stu-id="73893-114">[Navigation properties](navigation-property.md) that allow for navigation from one [end](association-end.md) of an [association](association-type.md) to the other end.</span></span> <span data-ttu-id="73893-115">(необязательно)</span><span class="sxs-lookup"><span data-stu-id="73893-115">(Optional)</span></span>  
  
 <span data-ttu-id="73893-116">В приложении экземпляр типа сущности представляет определенный объект (например, определенного клиента или заказ).</span><span class="sxs-lookup"><span data-stu-id="73893-116">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="73893-117">Каждый экземпляр типа сущности должен иметь уникальный [ключ сущности](entity-key.md) в [наборе сущностей](entity-set.md).</span><span class="sxs-lookup"><span data-stu-id="73893-117">Each instance of an entity type must have a unique [entity key](entity-key.md) within an [entity set](entity-set.md).</span></span>  
  
 <span data-ttu-id="73893-118">Два экземпляра типа сущности считаются равными, только если они являются экземплярами одного типа и значения их ключей сущности равны.</span><span class="sxs-lookup"><span data-stu-id="73893-118">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73893-119">Пример</span><span class="sxs-lookup"><span data-stu-id="73893-119">Example</span></span>  

 <span data-ttu-id="73893-120">На приведенной ниже схеме показана концептуальная модель с тремя типами сущностей: `Book`, `Publisher` и `Author`.</span><span class="sxs-lookup"><span data-stu-id="73893-120">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 ![Пример модели с тремя типами сущностей](./media/entity-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="73893-122">Обратите внимание, что свойства каждого типа сущности, составляющего его ключ сущности, обозначаются знаком «(Ключ)».</span><span class="sxs-lookup"><span data-stu-id="73893-122">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="73893-123">[Entity Framework ADO.NET](./ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)), для определения концептуальных моделей.</span><span class="sxs-lookup"><span data-stu-id="73893-123">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="73893-124">Ниже на языке CSDL определяется тип сущности `Book`, который ранее приводился в схеме.</span><span class="sxs-lookup"><span data-stu-id="73893-124">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="73893-125">См. также</span><span class="sxs-lookup"><span data-stu-id="73893-125">See also</span></span>

- [<span data-ttu-id="73893-126">Основные понятия модели EDM</span><span class="sxs-lookup"><span data-stu-id="73893-126">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="73893-127">EDM (модель данных с использованием сущностей)</span><span class="sxs-lookup"><span data-stu-id="73893-127">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="73893-128">устанавливают</span><span class="sxs-lookup"><span data-stu-id="73893-128">facet</span></span>](facet.md)
