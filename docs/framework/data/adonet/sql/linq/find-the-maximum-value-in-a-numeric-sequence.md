---
description: Дополнительные сведения см. в статье Поиск максимального значения в числовой последовательности.
title: Нахождение максимального значения в числовой последовательности
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: ab311f29d776c1ef4647967d391c7e4122ae7d38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672105"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a><span data-ttu-id="f3851-103">Нахождение максимального значения в числовой последовательности</span><span class="sxs-lookup"><span data-stu-id="f3851-103">Find the Maximum Value in a Numeric Sequence</span></span>

<span data-ttu-id="f3851-104">Используйте оператор <xref:System.Linq.Enumerable.Max%2A> для нахождения максимального значения в числовой последовательности.</span><span class="sxs-lookup"><span data-stu-id="f3851-104">Use the <xref:System.Linq.Enumerable.Max%2A> operator to find the highest value in a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3851-105">Пример</span><span class="sxs-lookup"><span data-stu-id="f3851-105">Example</span></span>  

 <span data-ttu-id="f3851-106">В следующем примере выполняется поиск самой последней даты приема сотрудника на работу.</span><span class="sxs-lookup"><span data-stu-id="f3851-106">The following example finds the latest date of hire for any employee.</span></span>  
  
 <span data-ttu-id="f3851-107">Если этот запрос запустить в образце базы данных Northwind, то будут получены следующие выходные данные: `11/15/1994 12:00:00 AM`.</span><span class="sxs-lookup"><span data-stu-id="f3851-107">If you run this query against the sample Northwind database, the output is: `11/15/1994 12:00:00 AM`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="f3851-108">Пример</span><span class="sxs-lookup"><span data-stu-id="f3851-108">Example</span></span>  

 <span data-ttu-id="f3851-109">В следующем примере выполняется максимальное количество единиц продукта на складе.</span><span class="sxs-lookup"><span data-stu-id="f3851-109">The following example finds the most units in stock for any product.</span></span>  
  
 <span data-ttu-id="f3851-110">Если этот пример запустить в образце базы данных Northwind, то будут получены следующие выходные данные: `125`.</span><span class="sxs-lookup"><span data-stu-id="f3851-110">If you run this example against the sample Northwind database, the output is: `125`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="f3851-111">Пример</span><span class="sxs-lookup"><span data-stu-id="f3851-111">Example</span></span>  

 <span data-ttu-id="f3851-112">В следующем примере для поиска `Products`, имеющего максимальную цену за единицу в каждой категории используется функция Max.</span><span class="sxs-lookup"><span data-stu-id="f3851-112">The following example uses Max to find the `Products` that have the highest unit price in each category.</span></span> <span data-ttu-id="f3851-113">Результаты упорядочиваются по категории.</span><span class="sxs-lookup"><span data-stu-id="f3851-113">The output then lists the results by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 <span data-ttu-id="f3851-114">Если выполнить предыдущий запрос для учебной базы данных "Northwind", результаты будут выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="f3851-114">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3851-115">См. также</span><span class="sxs-lookup"><span data-stu-id="f3851-115">See also</span></span>

- [<span data-ttu-id="f3851-116">Статистические запросы</span><span class="sxs-lookup"><span data-stu-id="f3851-116">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="f3851-117">Загрузка примеров баз данных</span><span class="sxs-lookup"><span data-stu-id="f3851-117">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
