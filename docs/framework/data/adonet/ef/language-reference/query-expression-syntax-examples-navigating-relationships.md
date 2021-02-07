---
description: 'Дополнительные сведения: примеры синтаксиса выражений запросов: Навигация по связям'
title: Примеры синтаксиса выражений запросов. Навигация по связям
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: 0548cba8d1d3d834da6a8416cb444898981b4123
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696156"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="1dd96-103">Примеры синтаксиса выражений запросов. Навигация по связям</span><span class="sxs-lookup"><span data-stu-id="1dd96-103">Query Expression Syntax Examples: Navigating Relationships</span></span>

<span data-ttu-id="1dd96-104">Свойства навигации в Entity Framework являются свойствами ярлыков, используемыми для поиска сущностей на концах ассоциации.</span><span class="sxs-lookup"><span data-stu-id="1dd96-104">Navigation properties in the Entity Framework are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="1dd96-105">Свойства навигации позволяют пользователю переходить от одной сущности к другой или от сущности к связанным сущностям в наборе ассоциаций.</span><span class="sxs-lookup"><span data-stu-id="1dd96-105">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="1dd96-106">В этом разделе приведены примеры синтаксиса выражений запросов для навигации по связям с помощью свойств навигации в запросах LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="1dd96-106">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="1dd96-107">Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1dd96-107">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1dd96-108">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="1dd96-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="1dd96-109">Пример</span><span class="sxs-lookup"><span data-stu-id="1dd96-109">Example</span></span>  

 <span data-ttu-id="1dd96-110">В следующем примере используется метод <xref:System.Linq.Queryable.Select%2A> для возврата всех идентификаторов контактных лиц и итогового значения суммы заказов для каждого контактного лица с фамилией «Zhou».</span><span class="sxs-lookup"><span data-stu-id="1dd96-110">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="1dd96-111">Свойство навигации `Contact.SalesOrderHeader` используется для получения коллекции объектов `SalesOrderHeader` для каждого контактного лица.</span><span class="sxs-lookup"><span data-stu-id="1dd96-111">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="1dd96-112">Метод `Sum` использует свойство навигации `Contact.SalesOrderHeader` для получения суммы всех заказов для каждого контактного лица.</span><span class="sxs-lookup"><span data-stu-id="1dd96-112">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="1dd96-113">Пример</span><span class="sxs-lookup"><span data-stu-id="1dd96-113">Example</span></span>  

 <span data-ttu-id="1dd96-114">В следующем примере осуществляется возврат всех заказов контактных лиц с фамилией «Zhou».</span><span class="sxs-lookup"><span data-stu-id="1dd96-114">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="1dd96-115">Свойство навигации `Contact.SalesOrderHeader` используется для получения коллекции объектов `SalesOrderHeader` для каждого контактного лица.</span><span class="sxs-lookup"><span data-stu-id="1dd96-115">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="1dd96-116">Имя и заказы контактного лица возвращаются в анонимном типе.</span><span class="sxs-lookup"><span data-stu-id="1dd96-116">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="1dd96-117">Пример</span><span class="sxs-lookup"><span data-stu-id="1dd96-117">Example</span></span>  

 <span data-ttu-id="1dd96-118">В следующем примере используются свойства навигации объектов `SalesOrderHeader.Address` и `SalesOrderHeader.Contact` для возврата коллекции объектов `Address` и `Contact`, связанных с каждым заказом.</span><span class="sxs-lookup"><span data-stu-id="1dd96-118">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="1dd96-119">Фамилия контактного лица, адрес, номер заказа на продажу и сумма заказа по каждому заказу в Сиэттле возвращаются в анонимном типе.</span><span class="sxs-lookup"><span data-stu-id="1dd96-119">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="1dd96-120">Пример</span><span class="sxs-lookup"><span data-stu-id="1dd96-120">Example</span></span>  

 <span data-ttu-id="1dd96-121">В следующем примере используется метод `Where` для нахождения заказов, сделанных после 1 декабря 2003 г. После этого с помощью свойства навигации `order.SalesOrderDetail` определяются подробности каждого заказа.</span><span class="sxs-lookup"><span data-stu-id="1dd96-121">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="1dd96-122">См. также</span><span class="sxs-lookup"><span data-stu-id="1dd96-122">See also</span></span>

- [<span data-ttu-id="1dd96-123">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1dd96-123">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
