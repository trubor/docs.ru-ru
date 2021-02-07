---
description: 'Дополнительные сведения: Method-Based примеры синтаксиса запросов: упорядочение'
title: Примеры синтаксиса запросов на основе методов. Упорядочение
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: 7b1c67ba66f549e82a57b5b34c645d36d1255a14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696702"
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="46e37-103">Примеры синтаксиса запросов на основе методов. Упорядочение</span><span class="sxs-lookup"><span data-stu-id="46e37-103">Method-Based Query Syntax Examples: Ordering</span></span>

<span data-ttu-id="46e37-104">В примерах этого раздела показано, как использовать <xref:System.Linq.Enumerable.ThenBy%2A> метод для запроса [модели AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) с помощью синтаксиса запросов на основе методов.</span><span class="sxs-lookup"><span data-stu-id="46e37-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="46e37-105">Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="46e37-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="46e37-106">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="46e37-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="46e37-107">ThenBy</span><span class="sxs-lookup"><span data-stu-id="46e37-107">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="46e37-108">Пример</span><span class="sxs-lookup"><span data-stu-id="46e37-108">Example</span></span>  

 <span data-ttu-id="46e37-109">В следующем примере, в синтаксисе запросов на основе методов, используются методы <xref:System.Linq.Queryable.OrderBy%2A> и <xref:System.Linq.Queryable.ThenBy%2A>, чтобы вернуть список контактов, отсортированный сначала по фамилии, а затем по имени.</span><span class="sxs-lookup"><span data-stu-id="46e37-109">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="46e37-110">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="46e37-110">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="46e37-111">Пример</span><span class="sxs-lookup"><span data-stu-id="46e37-111">Example</span></span>  

 <span data-ttu-id="46e37-112">В следующем примере используются методы <xref:System.Linq.Queryable.OrderBy%2A> и <xref:System.Linq.Queryable.ThenByDescending%2A>, чтобы вначале выполнить сортировку по стоимости, а затем сортировку по убыванию по названию продуктов.</span><span class="sxs-lookup"><span data-stu-id="46e37-112">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="46e37-113">См. также</span><span class="sxs-lookup"><span data-stu-id="46e37-113">See also</span></span>

- [<span data-ttu-id="46e37-114">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="46e37-114">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
