---
description: Дополнительные сведения см. в статье Поиск минимального значения в числовой последовательности.
title: Нахождение минимального значения в числовой последовательности
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: 6f265c6db3e143bdd5371aa9d30b4dd248e8fe3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803845"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="ac320-103">Нахождение минимального значения в числовой последовательности</span><span class="sxs-lookup"><span data-stu-id="ac320-103">Find the Minimum Value in a Numeric Sequence</span></span>

<span data-ttu-id="ac320-104">Для возвращения минимального значения из последовательности числовых значений используется оператор <xref:System.Linq.Enumerable.Min%2A>.</span><span class="sxs-lookup"><span data-stu-id="ac320-104">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac320-105">Пример</span><span class="sxs-lookup"><span data-stu-id="ac320-105">Example</span></span>  

 <span data-ttu-id="ac320-106">В следующем примере выполняется поиск минимальной цены продукта.</span><span class="sxs-lookup"><span data-stu-id="ac320-106">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="ac320-107">Если выполнить этот запрос в образце базы данных Northwind, то будут получены следующие выходные данные: `2.5000`.</span><span class="sxs-lookup"><span data-stu-id="ac320-107">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="ac320-108">Пример</span><span class="sxs-lookup"><span data-stu-id="ac320-108">Example</span></span>  

 <span data-ttu-id="ac320-109">В следующем примере выполняется поиск минимального объема доставки для заказа.</span><span class="sxs-lookup"><span data-stu-id="ac320-109">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="ac320-110">Если выполнить этот запрос в образце базы данных Northwind, то будут получены следующие выходные данные: `0.0200`.</span><span class="sxs-lookup"><span data-stu-id="ac320-110">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="ac320-111">Пример</span><span class="sxs-lookup"><span data-stu-id="ac320-111">Example</span></span>  

 <span data-ttu-id="ac320-112">В следующем примере для поиска `Products`, имеющего минимальную цену за единицу в каждой категории используется функция Min.</span><span class="sxs-lookup"><span data-stu-id="ac320-112">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="ac320-113">Результат упорядочивается по категории.</span><span class="sxs-lookup"><span data-stu-id="ac320-113">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="ac320-114">Если выполнить предыдущий запрос для учебной базы данных "Northwind", результаты будут выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ac320-114">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Guaraná Fantástica`  
  
 `2`  
  
 `Aniseed Syrup`  
  
 `3`  
  
 `Teatime Chocolate Biscuits`  
  
 `4`  
  
 `Geitost`  
  
 `5`  
  
 `Filo Mix`  
  
 `6`  
  
 `Tourtière`  
  
 `7`  
  
 `Longlife Tofu`  
  
 `8`  
  
 `Konbu`  
  
## <a name="see-also"></a><span data-ttu-id="ac320-115">См. также</span><span class="sxs-lookup"><span data-stu-id="ac320-115">See also</span></span>

- [<span data-ttu-id="ac320-116">Статистические запросы</span><span class="sxs-lookup"><span data-stu-id="ac320-116">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="ac320-117">Загрузка примеров баз данных</span><span class="sxs-lookup"><span data-stu-id="ac320-117">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
