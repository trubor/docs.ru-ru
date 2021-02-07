---
description: 'Дополнительные сведения: Method-Based примеры синтаксиса запросов: проекция'
title: Примеры синтаксиса запросов на основе методов. Проекция
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: ed4d53166f15f5a2b618ccae92b40fc07d370299
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696663"
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="4dfe2-103">Примеры синтаксиса запросов на основе методов. Проекция</span><span class="sxs-lookup"><span data-stu-id="4dfe2-103">Method-Based Query Syntax Examples: Projection</span></span>

<span data-ttu-id="4dfe2-104">В примерах этого раздела показано, как использовать <xref:System.Linq.Enumerable.Select%2A> методы и <xref:System.Linq.Enumerable.SelectMany%2A> для запроса [модели AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) с помощью синтаксиса запросов на основе методов.</span><span class="sxs-lookup"><span data-stu-id="4dfe2-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="4dfe2-105">Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4dfe2-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="4dfe2-106">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="4dfe2-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="4dfe2-107">Выберите пункт</span><span class="sxs-lookup"><span data-stu-id="4dfe2-107">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="4dfe2-108">Пример</span><span class="sxs-lookup"><span data-stu-id="4dfe2-108">Example</span></span>  

 <span data-ttu-id="4dfe2-109">В следующем примере используется метод <xref:System.Linq.Queryable.Select%2A> для проецирования свойств `Product.Name` и `Product.ProductID` в последовательность анонимных типов.</span><span class="sxs-lookup"><span data-stu-id="4dfe2-109">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="4dfe2-110">Пример</span><span class="sxs-lookup"><span data-stu-id="4dfe2-110">Example</span></span>  

 <span data-ttu-id="4dfe2-111">В следующем примере используется метод <xref:System.Linq.Enumerable.Select%2A> для возвращения последовательности только названий продуктов.</span><span class="sxs-lookup"><span data-stu-id="4dfe2-111">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="4dfe2-112">SelectMany</span><span class="sxs-lookup"><span data-stu-id="4dfe2-112">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="4dfe2-113">Пример</span><span class="sxs-lookup"><span data-stu-id="4dfe2-113">Example</span></span>  

 <span data-ttu-id="4dfe2-114">В следующем примере используется метод <xref:System.Linq.Enumerable.SelectMany%2A> для выборки всех заказов, в которых `TotalDue` меньше 500,00.</span><span class="sxs-lookup"><span data-stu-id="4dfe2-114">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="4dfe2-115">Пример</span><span class="sxs-lookup"><span data-stu-id="4dfe2-115">Example</span></span>  

 <span data-ttu-id="4dfe2-116">В следующем примере используется метод <xref:System.Linq.Enumerable.SelectMany%2A> для выборки всех заказов, сделанных 1 октября 2002 или позже.</span><span class="sxs-lookup"><span data-stu-id="4dfe2-116">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="4dfe2-117">См. также</span><span class="sxs-lookup"><span data-stu-id="4dfe2-117">See also</span></span>

- [<span data-ttu-id="4dfe2-118">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="4dfe2-118">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
