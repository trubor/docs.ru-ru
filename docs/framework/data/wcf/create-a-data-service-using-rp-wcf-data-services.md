---
description: Дополнительные сведения см. в статье как создать службу данных с помощью поставщика отражения (службы данных WCF).
title: Практическое руководство. Создание службы данных с использованием поставщика отражений (службы данных WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 1c4d131b21c69e11dd6d8b574e4c22a6af7c5a25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766238"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="17375-103">Практическое руководство. Создание службы данных с использованием поставщика отражений (службы данных WCF)</span><span class="sxs-lookup"><span data-stu-id="17375-103">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="17375-104">Службы данных WCF позволяет определить модель данных, основанную на произвольных классах, если эти классы предоставляются как объекты, реализующие <xref:System.Linq.IQueryable%601> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="17375-104">WCF Data Services enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="17375-105">Дополнительные сведения см. в разделе [поставщики служб данных](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="17375-105">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="17375-106">Пример</span><span class="sxs-lookup"><span data-stu-id="17375-106">Example</span></span>  

 <span data-ttu-id="17375-107">Следующий пример определяет модель данных, включающую сущности `Orders` и `Items`.</span><span class="sxs-lookup"><span data-stu-id="17375-107">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="17375-108">Класс контейнера сущностей `OrderItemData` имеет два публичных метода, которые возвращают интерфейсы <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="17375-108">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="17375-109">Эти интерфейсы являются наборами сущностей типа `Orders` и типами сущностей `Items`.</span><span class="sxs-lookup"><span data-stu-id="17375-109">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="17375-110">Сущность `Order` может включать несколько сущностей `Items`, поэтому тип сущности `Orders` имеет свойство навигации `Items`, возвращающее коллекцию объектов `Items`.</span><span class="sxs-lookup"><span data-stu-id="17375-110">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="17375-111">Класс контейнера сущностей `OrderItemData` является универсальным типом класса <xref:System.Data.Services.DataService%601>, производным которого является класс `OrderItems` службы данных.</span><span class="sxs-lookup"><span data-stu-id="17375-111">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17375-112">Поскольку пример демонстрирует поставщика данных в памяти и изменения не сохраняются за пределами текущих экземпляров объектов, реализация интерфейса <xref:System.Data.Services.IUpdatable> не приносит никаких выгод.</span><span class="sxs-lookup"><span data-stu-id="17375-112">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="17375-113">Пример, в котором реализуется <xref:System.Data.Services.IUpdatable> интерфейс, см. [в разделе инструкции. Создание службы данных с помощью LINQ to SQL источника данных](create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="17375-113">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="17375-114">См. также</span><span class="sxs-lookup"><span data-stu-id="17375-114">See also</span></span>

- [<span data-ttu-id="17375-115">Практическое руководство. Создание службы данных с использованием источника данных LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="17375-115">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="17375-116">Поставщики служб данных</span><span class="sxs-lookup"><span data-stu-id="17375-116">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="17375-117">Практическое руководство. Создание службы данных с использованием источника данных Entity Framework ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17375-117">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
