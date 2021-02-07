---
description: 'Дополнительные сведения о: EDM: пространства имен'
title: 'EDM (модель данных с использованием сущностей): Пространства имен'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: c18178672ebab0e323c9712af2668c3cb92e0300
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672768"
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="5d9a9-103">EDM (модель данных с использованием сущностей): Пространства имен</span><span class="sxs-lookup"><span data-stu-id="5d9a9-103">Entity Data Model: Namespaces</span></span>

<span data-ttu-id="5d9a9-104">Пространство имен в EDM (EDM) является абстрактным контейнером для [типов сущностей](entity-type.md), [сложных типов](complex-type.md)и [ассоциаций](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="5d9a9-104">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](entity-type.md), [complex types](complex-type.md), and [associations](association-type.md).</span></span> <span data-ttu-id="5d9a9-105">Пространства имен в модели EDM схожи с пространствами имен в языке программирования: они обеспечивают контекст для объектов, которые они содержат, а также являются способом устранения неопределенности в отношении объектов, которые имеют одно и то же имя (но содержатся в разных пространствах имен).</span><span class="sxs-lookup"><span data-stu-id="5d9a9-105">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d9a9-106">Пример</span><span class="sxs-lookup"><span data-stu-id="5d9a9-106">Example</span></span>  

 <span data-ttu-id="5d9a9-107">[Entity Framework ADO.NET](./ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)), для определения концептуальных моделей.</span><span class="sxs-lookup"><span data-stu-id="5d9a9-107">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="5d9a9-108">В следующем коде на языке CSDL используется пространство имен для идентификации типа, определенного в другой концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="5d9a9-108">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="5d9a9-109">В примере определяется тип сущности (`Publisher`), который имеет свойство сложного типа (`Address`), импортированного из пространства имен `ExtendedBooksModel`.</span><span class="sxs-lookup"><span data-stu-id="5d9a9-109">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="5d9a9-110">Обратите внимание, что элемент `Using` указывает на то, что пространство имен было импортировано.</span><span class="sxs-lookup"><span data-stu-id="5d9a9-110">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="5d9a9-111">Также обратите внимание, что тип свойства `Address` определен при помощи своего полного имени (`ExtendedBooksModel.Address`) с указанием на то, что этот тип определен в пространстве имен `ExtendedBooksModel`.</span><span class="sxs-lookup"><span data-stu-id="5d9a9-111">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="5d9a9-112">См. также</span><span class="sxs-lookup"><span data-stu-id="5d9a9-112">See also</span></span>

- [<span data-ttu-id="5d9a9-113">Основные понятия модели EDM</span><span class="sxs-lookup"><span data-stu-id="5d9a9-113">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="5d9a9-114">EDM (модель данных с использованием сущностей)</span><span class="sxs-lookup"><span data-stu-id="5d9a9-114">Entity Data Model</span></span>](entity-data-model.md)
