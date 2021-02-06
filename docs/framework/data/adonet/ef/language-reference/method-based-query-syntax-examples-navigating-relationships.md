---
description: 'Дополнительные сведения: Method-Based примеры синтаксиса запросов: Навигация по связям'
title: Примеры синтаксиса запросов на основе методов. Навигация по связям
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: c209b97704fec86834375ad8c9eee4d717a61294
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650523"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a><span data-ttu-id="8b798-103">Примеры синтаксиса запросов на основе методов. Навигация по связям</span><span class="sxs-lookup"><span data-stu-id="8b798-103">Method-Based Query Syntax Examples: Navigating Relationships</span></span>

<span data-ttu-id="8b798-104">Свойства навигации в Entity Framework являются свойствами ярлыков, используемыми для поиска сущностей на концах ассоциации.</span><span class="sxs-lookup"><span data-stu-id="8b798-104">Navigation properties in the Entity Framework are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="8b798-105">Свойства навигации позволяют пользователю переходить от одной сущности к другой или от сущности к связанным сущностям в наборе ассоциаций.</span><span class="sxs-lookup"><span data-stu-id="8b798-105">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="8b798-106">В этом разделе приведены примеры синтаксиса запросов на основе методов, позволяющих перемещаться по связям с помощью свойств навигации в запросах LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="8b798-106">This topic provides examples in method-based query syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="8b798-107">Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8b798-107">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8b798-108">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="8b798-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="8b798-109">Пример</span><span class="sxs-lookup"><span data-stu-id="8b798-109">Example</span></span>  

 <span data-ttu-id="8b798-110">В следующем примере синтаксиса запроса на основе методов используется метод <xref:System.Linq.Queryable.SelectMany%2A>, чтобы получить все заказы контактных лиц с фамилией «Zhou».</span><span class="sxs-lookup"><span data-stu-id="8b798-110">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.SelectMany%2A> method to get all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="8b798-111">Свойство навигации `Contact.SalesOrderHeader` используется для получения коллекции объектов `SalesOrderHeader` для каждого контактного лица.</span><span class="sxs-lookup"><span data-stu-id="8b798-111">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a><span data-ttu-id="8b798-112">Пример</span><span class="sxs-lookup"><span data-stu-id="8b798-112">Example</span></span>  

 <span data-ttu-id="8b798-113">В следующем примере синтаксиса запроса на основе методов используется метод <xref:System.Linq.Queryable.Select%2A>, чтобы получить все идентификаторы контактов и сумму заказа для каждого контактного лица с фамилией «Zhou».</span><span class="sxs-lookup"><span data-stu-id="8b798-113">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="8b798-114">Свойство навигации `Contact.SalesOrderHeader` используется для получения коллекции объектов `SalesOrderHeader` для каждого контактного лица.</span><span class="sxs-lookup"><span data-stu-id="8b798-114">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="8b798-115">Метод `Sum` использует свойство навигации `Contact.SalesOrderHeader` для получения суммы всех заказов для каждого контактного лица.</span><span class="sxs-lookup"><span data-stu-id="8b798-115">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a><span data-ttu-id="8b798-116">Пример</span><span class="sxs-lookup"><span data-stu-id="8b798-116">Example</span></span>  

 <span data-ttu-id="8b798-117">В следующем примере синтаксиса запроса на основе методов получаются все заказы контактных лиц с фамилией «Zhou».</span><span class="sxs-lookup"><span data-stu-id="8b798-117">The following example in method-based query syntax gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="8b798-118">Свойство навигации `Contact.SalesOrderHeader` используется для получения коллекции объектов `SalesOrderHeader` для каждого контактного лица.</span><span class="sxs-lookup"><span data-stu-id="8b798-118">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="8b798-119">Имя и заказы контактного лица возвращаются в анонимном типе.</span><span class="sxs-lookup"><span data-stu-id="8b798-119">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a><span data-ttu-id="8b798-120">Пример</span><span class="sxs-lookup"><span data-stu-id="8b798-120">Example</span></span>  

 <span data-ttu-id="8b798-121">В следующем примере свойства навигации `SalesOrderHeader.Address` и `SalesOrderHeader.Contact` используются, чтобы получить коллекцию объектов `Address` и `Contact`, связанных с каждым заказом.</span><span class="sxs-lookup"><span data-stu-id="8b798-121">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties to get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="8b798-122">Фамилия контактного лица, адрес, номер заказа на продажу и сумма заказа по каждому заказу в Сиэттле возвращаются в анонимном типе.</span><span class="sxs-lookup"><span data-stu-id="8b798-122">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a><span data-ttu-id="8b798-123">Пример</span><span class="sxs-lookup"><span data-stu-id="8b798-123">Example</span></span>  

 <span data-ttu-id="8b798-124">В следующем примере используется метод `Where` для нахождения заказов, сделанных после 1 декабря 2003 г. После этого с помощью свойства навигации `order.SalesOrderDetail` определяются подробности каждого заказа.</span><span class="sxs-lookup"><span data-stu-id="8b798-124">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="8b798-125">См. также</span><span class="sxs-lookup"><span data-stu-id="8b798-125">See also</span></span>

- [<span data-ttu-id="8b798-126">Связи, свойства навигации и внешние ключи</span><span class="sxs-lookup"><span data-stu-id="8b798-126">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
- [<span data-ttu-id="8b798-127">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="8b798-127">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
