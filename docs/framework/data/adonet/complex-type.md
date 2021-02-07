---
description: 'Дополнительные сведения: сложный тип'
title: сложный тип
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 06bb6f54f488e4c6038382707a2ad3e85f000bc2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663902"
---
# <a name="complex-type"></a><span data-ttu-id="f1609-103">сложный тип</span><span class="sxs-lookup"><span data-stu-id="f1609-103">complex type</span></span>

<span data-ttu-id="f1609-104">*Сложный тип* — это шаблон для определения насыщенных структурированных свойств [типов сущностей](entity-type.md) или других сложных типов.</span><span class="sxs-lookup"><span data-stu-id="f1609-104">A *complex type* is a template for defining rich, structured properties on [entity types](entity-type.md) or on other complex types.</span></span> <span data-ttu-id="f1609-105">Каждый шаблон содержит следующие сведения.</span><span class="sxs-lookup"><span data-stu-id="f1609-105">Each template contains the following:</span></span>  
  
- <span data-ttu-id="f1609-106">Уникальное имя.</span><span class="sxs-lookup"><span data-stu-id="f1609-106">A unique name.</span></span> <span data-ttu-id="f1609-107">(обязательно)</span><span class="sxs-lookup"><span data-stu-id="f1609-107">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f1609-108">Имя сложного типа не может быть таким же, что и имя типа сущности внутри одного и того же пространства имени.</span><span class="sxs-lookup"><span data-stu-id="f1609-108">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
- <span data-ttu-id="f1609-109">Данные в форме одного или нескольких [свойств](property.md).</span><span class="sxs-lookup"><span data-stu-id="f1609-109">Data in the form of one or more [properties](property.md).</span></span> <span data-ttu-id="f1609-110">(Необязательно.)</span><span class="sxs-lookup"><span data-stu-id="f1609-110">(Optional.)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f1609-111">Свойство сложного типа может быть другим сложным типом.</span><span class="sxs-lookup"><span data-stu-id="f1609-111">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="f1609-112">Сложный тип похож на тип сущности тем, что сложный тип может содержать полезные данные в форме свойств примитивного типа или других сложных типов.</span><span class="sxs-lookup"><span data-stu-id="f1609-112">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="f1609-113">Однако между сложными типами и типами сущности существуют некоторые ключевые различия.</span><span class="sxs-lookup"><span data-stu-id="f1609-113">However, there are some key differences between complex types and entity types:</span></span>  
  
- <span data-ttu-id="f1609-114">Сложные типы не имеют идентификаторов и поэтому не могут существовать независимо.</span><span class="sxs-lookup"><span data-stu-id="f1609-114">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="f1609-115">Сложные типы могут существовать только как свойства типов сущностей или других сложных типов.</span><span class="sxs-lookup"><span data-stu-id="f1609-115">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
- <span data-ttu-id="f1609-116">Сложные типы не могут участвовать в [связях](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="f1609-116">Complex types cannot participate in [associations](association-type.md).</span></span> <span data-ttu-id="f1609-117">Ни один из окончаний ассоциации не может быть сложным типом, поэтому [Свойства навигации](navigation-property.md) не могут быть определены для сложных типов.</span><span class="sxs-lookup"><span data-stu-id="f1609-117">Neither end of an association can be a complex type, and therefore [navigation properties](navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1609-118">Пример</span><span class="sxs-lookup"><span data-stu-id="f1609-118">Example</span></span>  

 <span data-ttu-id="f1609-119">[Entity Framework ADO.NET](./ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)), для определения концептуальных моделей.</span><span class="sxs-lookup"><span data-stu-id="f1609-119">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="f1609-120">Далее на языке CSDL определяется сложный тип, адрес со свойствами примитивного типа `StreetAddress`, `City`, `StateOrProvince`, `Country` и `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="f1609-120">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="f1609-121">Чтобы определить сложный тип `Address` (показанный выше) как свойство типа сущности, необходимо объявить тип свойства в определении типа сущности.</span><span class="sxs-lookup"><span data-stu-id="f1609-121">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="f1609-122">Далее на языке CSDL объявляется свойство `Address` в виде сложного типа в типе сущности (издателе).</span><span class="sxs-lookup"><span data-stu-id="f1609-122">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="f1609-123">См. также</span><span class="sxs-lookup"><span data-stu-id="f1609-123">See also</span></span>

- [<span data-ttu-id="f1609-124">Основные понятия модели EDM</span><span class="sxs-lookup"><span data-stu-id="f1609-124">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="f1609-125">EDM (модель данных с использованием сущностей)</span><span class="sxs-lookup"><span data-stu-id="f1609-125">Entity Data Model</span></span>](entity-data-model.md)
