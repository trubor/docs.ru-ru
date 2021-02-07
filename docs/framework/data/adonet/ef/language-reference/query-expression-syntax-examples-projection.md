---
description: 'Дополнительные сведения: примеры синтаксиса выражений запросов: проекция'
title: Примеры синтаксиса выражений запросов. Проекция
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
ms.openlocfilehash: e14a84272cef03dca24df5d0f889b8aaa77e94d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696013"
---
# <a name="query-expression-syntax-examples-projection"></a><span data-ttu-id="f964e-103">Примеры синтаксиса выражений запросов. Проекция</span><span class="sxs-lookup"><span data-stu-id="f964e-103">Query Expression Syntax Examples: Projection</span></span>

<span data-ttu-id="f964e-104">В примерах этого раздела показано, как использовать `Select` метод и `From … From …` Ключевые слова для запроса [модели AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) с помощью синтаксиса выражения запроса.</span><span class="sxs-lookup"><span data-stu-id="f964e-104">The examples in this topic demonstrate how to use the `Select` method and the `From … From …` keywords to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="f964e-105">`From … From …` - это основанный на запросе эквивалент метода `SelectMany`.</span><span class="sxs-lookup"><span data-stu-id="f964e-105">`From … From …` is the query based equivalent of the `SelectMany` method.</span></span> <span data-ttu-id="f964e-106">Модель AdventureWorks Sales, которая используется в этих примерах, состоит из таблиц Contact, Address, Product, SalesOrderHeader и SalesOrderDetail образца базы данных AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f964e-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f964e-107">В примерах этого раздела используются следующие `using` / `Imports` инструкции:</span><span class="sxs-lookup"><span data-stu-id="f964e-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="f964e-108">Выберите пункт</span><span class="sxs-lookup"><span data-stu-id="f964e-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="f964e-109">Пример</span><span class="sxs-lookup"><span data-stu-id="f964e-109">Example</span></span>  

 <span data-ttu-id="f964e-110">В следующем примере метод <xref:System.Linq.Enumerable.Select%2A> используется для возврата всех строк из таблицы `Product` и отображения названий продуктов.</span><span class="sxs-lookup"><span data-stu-id="f964e-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="f964e-111">Пример</span><span class="sxs-lookup"><span data-stu-id="f964e-111">Example</span></span>  

 <span data-ttu-id="f964e-112">В следующем примере используется метод <xref:System.Linq.Enumerable.Select%2A> для возврата последовательности, состоящей только из названий продуктов.</span><span class="sxs-lookup"><span data-stu-id="f964e-112">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a><span data-ttu-id="f964e-113">Пример</span><span class="sxs-lookup"><span data-stu-id="f964e-113">Example</span></span>  

 <span data-ttu-id="f964e-114">В следующем примере используется метод <xref:System.Linq.Queryable.Select%2A> для проецирования свойств `Product.Name` и `Product.ProductID` в последовательность анонимных типов.</span><span class="sxs-lookup"><span data-stu-id="f964e-114">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a><span data-ttu-id="f964e-115">От...</span><span class="sxs-lookup"><span data-stu-id="f964e-115">From …</span></span> <span data-ttu-id="f964e-116">От...</span><span class="sxs-lookup"><span data-stu-id="f964e-116">From …</span></span> <span data-ttu-id="f964e-117">SelectMany</span><span class="sxs-lookup"><span data-stu-id="f964e-117">(SelectMany)</span></span>  
  
### <a name="example"></a><span data-ttu-id="f964e-118">Пример</span><span class="sxs-lookup"><span data-stu-id="f964e-118">Example</span></span>  

 <span data-ttu-id="f964e-119">В следующем примере используется инструкция `From … From …` (эквивалент метода <xref:System.Linq.Enumerable.SelectMany%2A>) для выделения всех заказов, в которых значение `TotalDue` меньше 500,00.</span><span class="sxs-lookup"><span data-stu-id="f964e-119">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="f964e-120">Пример</span><span class="sxs-lookup"><span data-stu-id="f964e-120">Example</span></span>  

 <span data-ttu-id="f964e-121">В следующем примере используется инструкция `From … From …` (эквивалент метода <xref:System.Linq.Enumerable.SelectMany%2A>) для выборки всех заказов, сделанных 1 октября 2002 г. или позже.</span><span class="sxs-lookup"><span data-stu-id="f964e-121">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="f964e-122">Пример</span><span class="sxs-lookup"><span data-stu-id="f964e-122">Example</span></span>  

 <span data-ttu-id="f964e-123">В следующем примере используется инструкция `From … From …` (эквивалент метода <xref:System.Linq.Enumerable.SelectMany%2A>) для выборки всех тех заказов, в которых итоговая сумма превышает 10 000,00, и применяется присваивание `From` для предотвращения повторного запроса того же итога.</span><span class="sxs-lookup"><span data-stu-id="f964e-123">The following example uses a `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="f964e-124">См. также</span><span class="sxs-lookup"><span data-stu-id="f964e-124">See also</span></span>

- [<span data-ttu-id="f964e-125">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="f964e-125">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
