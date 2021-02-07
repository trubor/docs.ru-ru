---
description: 'Дополнительные сведения: формулировка соединений и кросс-по продукту запросов'
title: Практическое руководство. Формулировка запросов-объединений и запросов векторного произведения
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: 1adee3576d7b30d6ec9a9c4e920befcd21dd9e85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739122"
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="28eea-103">Практическое руководство. Формулировка запросов-объединений и запросов векторного произведения</span><span class="sxs-lookup"><span data-stu-id="28eea-103">Formulate Joins and Cross-Product Queries</span></span>

<span data-ttu-id="28eea-104">В следующем примере показано, как объединить результаты из нескольких таблиц.</span><span class="sxs-lookup"><span data-stu-id="28eea-104">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28eea-105">Пример</span><span class="sxs-lookup"><span data-stu-id="28eea-105">Example</span></span>  

 <span data-ttu-id="28eea-106">В следующем примере Навигация по внешнему ключу используется в `From` предложении Visual Basic ( `from` предложение в C#) для выбора всех заказов для клиентов в Лондоне.</span><span class="sxs-lookup"><span data-stu-id="28eea-106">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="28eea-107">Пример</span><span class="sxs-lookup"><span data-stu-id="28eea-107">Example</span></span>  

 <span data-ttu-id="28eea-108">В следующем примере Навигация по внешнему ключу используется в `Where` предложении в Visual Basic ( `where` предложение в C#) для фильтрации находящихся в наличии данных `Products` , которые `Supplier` находятся в США.</span><span class="sxs-lookup"><span data-stu-id="28eea-108">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="28eea-109">Пример</span><span class="sxs-lookup"><span data-stu-id="28eea-109">Example</span></span>  

 <span data-ttu-id="28eea-110">В следующем примере Навигация по внешнему ключу используется в `From` предложении Visual Basic ( `from` предложение в C#) для фильтрации сотрудников в Сиэтле и для перечисления своих территорий.</span><span class="sxs-lookup"><span data-stu-id="28eea-110">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="28eea-111">Пример</span><span class="sxs-lookup"><span data-stu-id="28eea-111">Example</span></span>  

 <span data-ttu-id="28eea-112">В следующем примере Навигация по внешнему ключу используется в `Select` предложении в Visual Basic ( `select` предложение в C#) для фильтрации пар сотрудников, в которых один сотрудник отчитывается друг с другом и когда оба сотрудника находятся в одном `City` .</span><span class="sxs-lookup"><span data-stu-id="28eea-112">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="28eea-113">Пример</span><span class="sxs-lookup"><span data-stu-id="28eea-113">Example</span></span>  

 <span data-ttu-id="28eea-114">В следующем Visual Basic примере выполняется поиск всех клиентов и заказов, гарантируется соответствие заказов клиентам и гарантируется, что для каждого клиента в этом списке предоставляется имя контакта.</span><span class="sxs-lookup"><span data-stu-id="28eea-114">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="28eea-115">Пример</span><span class="sxs-lookup"><span data-stu-id="28eea-115">Example</span></span>  

 <span data-ttu-id="28eea-116">В следующем пример явно соединяются две таблицы и проецируются результаты из обеих таблиц.</span><span class="sxs-lookup"><span data-stu-id="28eea-116">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="28eea-117">Пример</span><span class="sxs-lookup"><span data-stu-id="28eea-117">Example</span></span>  

 <span data-ttu-id="28eea-118">В следующем пример явно соединяются три таблицы и проецируются результаты из каждой таблицы.</span><span class="sxs-lookup"><span data-stu-id="28eea-118">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="28eea-119">Пример</span><span class="sxs-lookup"><span data-stu-id="28eea-119">Example</span></span>  

 <span data-ttu-id="28eea-120">В следующем примере показано, как реализовать оператор `LEFT OUTER JOIN` с помощью метода `DefaultIfEmpty()`.</span><span class="sxs-lookup"><span data-stu-id="28eea-120">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="28eea-121">Если для сотрудника (`DefaultIfEmpty()`) не имеется заказов (`Order`), метод `Employee` возвращает значение NULL.</span><span class="sxs-lookup"><span data-stu-id="28eea-121">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="28eea-122">Пример</span><span class="sxs-lookup"><span data-stu-id="28eea-122">Example</span></span>  

 <span data-ttu-id="28eea-123">В следующем примере проецируется выражение `let`, полученное в результате соединения.</span><span class="sxs-lookup"><span data-stu-id="28eea-123">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="28eea-124">Пример</span><span class="sxs-lookup"><span data-stu-id="28eea-124">Example</span></span>  

 <span data-ttu-id="28eea-125">В следующем примере показан оператор `join` с композитным ключом.</span><span class="sxs-lookup"><span data-stu-id="28eea-125">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="28eea-126">Пример</span><span class="sxs-lookup"><span data-stu-id="28eea-126">Example</span></span>  

 <span data-ttu-id="28eea-127">В следующем примере показано, как создать оператор `join`, в котором одна сторона может принимать значение NULL, а другая сторона не может.</span><span class="sxs-lookup"><span data-stu-id="28eea-127">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="28eea-128">См. также</span><span class="sxs-lookup"><span data-stu-id="28eea-128">See also</span></span>

- [<span data-ttu-id="28eea-129">Примеры запросов</span><span class="sxs-lookup"><span data-stu-id="28eea-129">Query Examples</span></span>](query-examples.md)
