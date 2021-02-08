---
description: 'Дополнительные сведения: сортировка элементов в последовательности'
title: Сортировка элементов последовательности
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: 337afe79826e9a9584a5fc3ed3980341dda1b4d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803767"
---
# <a name="sort-elements-in-a-sequence"></a><span data-ttu-id="079e1-103">Сортировка элементов последовательности</span><span class="sxs-lookup"><span data-stu-id="079e1-103">Sort Elements in a Sequence</span></span>

<span data-ttu-id="079e1-104">Для сортировки последовательности по одному или нескольким ключам используется оператор <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="079e1-104">Use the <xref:System.Linq.Enumerable.OrderBy%2A> operator to sort a sequence according to one or more keys.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="079e1-105">предназначен для поддержки упорядочения простыми примитивными типами, такими как `string` , `int` и т. д.</span><span class="sxs-lookup"><span data-stu-id="079e1-105">is designed to support ordering by simple primitive types, such as `string`, `int`, and so on.</span></span> <span data-ttu-id="079e1-106">В этой технологии не поддерживается упорядочение для сложных многозначных классов, таких как анонимные типы.</span><span class="sxs-lookup"><span data-stu-id="079e1-106">It does not support ordering for complex multi-valued classes, such as anonymous types.</span></span> <span data-ttu-id="079e1-107">В ней также не поддерживаются типы данных `byte`.</span><span class="sxs-lookup"><span data-stu-id="079e1-107">It also does not support `byte` datatypes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="079e1-108">Пример</span><span class="sxs-lookup"><span data-stu-id="079e1-108">Example</span></span>  

 <span data-ttu-id="079e1-109">В следующем примере выполняется сортировка сотрудников (`Employees`) по дате приема на работу.</span><span class="sxs-lookup"><span data-stu-id="079e1-109">The following example sorts `Employees` by date of hire.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a><span data-ttu-id="079e1-110">Пример</span><span class="sxs-lookup"><span data-stu-id="079e1-110">Example</span></span>  

 <span data-ttu-id="079e1-111">В следующем примере для сортировки заказов (`where`), поставленных в Лондон (`Orders`), по типу перевозки используется предложение `London`.</span><span class="sxs-lookup"><span data-stu-id="079e1-111">The following example uses `where` to sort `Orders` shipped to `London` by freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a><span data-ttu-id="079e1-112">Пример</span><span class="sxs-lookup"><span data-stu-id="079e1-112">Example</span></span>  

 <span data-ttu-id="079e1-113">В следующем примере выполняется сортировка продуктов (`Products`) по цене единицы товара по убыванию.</span><span class="sxs-lookup"><span data-stu-id="079e1-113">The following example sorts `Products` by unit price from highest to lowest.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="079e1-114">Пример</span><span class="sxs-lookup"><span data-stu-id="079e1-114">Example</span></span>  

 <span data-ttu-id="079e1-115">В следующем примере для сортировки клиентов (`OrderBy`) по городу, а затем по контактному лицу используется составной оператор `Customers`.</span><span class="sxs-lookup"><span data-stu-id="079e1-115">The following example uses a compound `OrderBy` to sort `Customers` by city and then by contact name.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="079e1-116">Пример</span><span class="sxs-lookup"><span data-stu-id="079e1-116">Example</span></span>  

 <span data-ttu-id="079e1-117">В следующем примере сортируются заказы от `EmployeeID 1` по `ShipCountry` , а затем по убыванию.</span><span class="sxs-lookup"><span data-stu-id="079e1-117">The following example sorts Orders from `EmployeeID 1` by `ShipCountry`, and then by highest to lowest freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="079e1-118">Пример</span><span class="sxs-lookup"><span data-stu-id="079e1-118">Example</span></span>  

 <span data-ttu-id="079e1-119">В следующем примере объединяются операторы <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A> и <xref:System.Linq.Enumerable.GroupBy%2A>, чтобы найти продукты (`Products`) с максимальной ценой за единицу товара в каждой категории, а затем выполнить сортировку полученной группы по коду категории.</span><span class="sxs-lookup"><span data-stu-id="079e1-119">The following example combines <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, and <xref:System.Linq.Enumerable.GroupBy%2A> operators to find the `Products` that have the highest unit price in each category, and then sorts the group by category id.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 <span data-ttu-id="079e1-120">Если выполнить предыдущий запрос для учебной базы данных "Northwind", результаты должны выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="079e1-120">If you run the previous query against the Northwind sample database, the results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="079e1-121">См. также</span><span class="sxs-lookup"><span data-stu-id="079e1-121">See also</span></span>

- [<span data-ttu-id="079e1-122">Примеры запросов</span><span class="sxs-lookup"><span data-stu-id="079e1-122">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="079e1-123">Загрузка примеров баз данных</span><span class="sxs-lookup"><span data-stu-id="079e1-123">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
