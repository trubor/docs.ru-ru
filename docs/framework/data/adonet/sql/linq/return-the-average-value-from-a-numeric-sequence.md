---
description: 'Дополнительные сведения: Возврат среднего значения из числовой последовательности'
title: Возврат среднего значения из числовой последовательности
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
ms.openlocfilehash: 4e0415c9ef981364fc3d6481ed6455f132e84932
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663070"
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a><span data-ttu-id="c1839-103">Возврат среднего значения из числовой последовательности</span><span class="sxs-lookup"><span data-stu-id="c1839-103">Return the Average Value From a Numeric Sequence</span></span>

<span data-ttu-id="c1839-104">Оператор <xref:System.Linq.Enumerable.Average%2A> вычисляет среднее последовательности числовых значений.</span><span class="sxs-lookup"><span data-stu-id="c1839-104">The <xref:System.Linq.Enumerable.Average%2A> operator computes the average of a sequence of numeric values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1839-105">Преобразование [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] для оператора `Average`, вычисляющего среднее значение целых чисел, возвращает целое число, а не число двойной точности.</span><span class="sxs-lookup"><span data-stu-id="c1839-105">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Average` of integer values is computed as an integer, not as a double.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1839-106">Пример</span><span class="sxs-lookup"><span data-stu-id="c1839-106">Example</span></span>  

 <span data-ttu-id="c1839-107">В следующем примере вычисляется среднее для значений `Freight` из таблицы `Orders`.</span><span class="sxs-lookup"><span data-stu-id="c1839-107">The following example returns the average of `Freight` values in the `Orders` table.</span></span>  
  
 <span data-ttu-id="c1839-108">Для образца базы данных Northwind результатом будет `78.2442`.</span><span class="sxs-lookup"><span data-stu-id="c1839-108">Results from the sample Northwind database would be `78.2442`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="c1839-109">Пример</span><span class="sxs-lookup"><span data-stu-id="c1839-109">Example</span></span>  

 <span data-ttu-id="c1839-110">Следующий пример возвращает среднее значение цены единицы для всех `Products` в таблице `Products`.</span><span class="sxs-lookup"><span data-stu-id="c1839-110">The following example returns the average of the unit price of all `Products` in the `Products` table.</span></span>  
  
 <span data-ttu-id="c1839-111">Для образца базы данных Northwind результатом будет `28.8663`.</span><span class="sxs-lookup"><span data-stu-id="c1839-111">Results from the sample Northwind database would be `28.8663`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="c1839-112">Пример</span><span class="sxs-lookup"><span data-stu-id="c1839-112">Example</span></span>  

 <span data-ttu-id="c1839-113">В следующем примере используется оператор `Average` для поиска тех продуктов `Products`, цена единицы товара для которых выше среднего значения цены единицы товара для содержащей их категории.</span><span class="sxs-lookup"><span data-stu-id="c1839-113">The following example uses the `Average` operator to find those `Products` whose unit price is higher than the average unit price of the category it belongs to.</span></span> <span data-ttu-id="c1839-114">Затем выполняется отображение групп результатов.</span><span class="sxs-lookup"><span data-stu-id="c1839-114">The example then displays the results in groups.</span></span>  
  
 <span data-ttu-id="c1839-115">Обратите внимание, что в этом примере требуется использовать ключевое слово `var` языка C#, поскольку тип возвращаемого значения является анонимным.</span><span class="sxs-lookup"><span data-stu-id="c1839-115">Note that this example requires the use of the `var` keyword in C#, because the return type is anonymous.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 <span data-ttu-id="c1839-116">Если выполнить этот пример для учебной базы данных "Northwind, результаты должны выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c1839-116">If you run this query against the Northwind sample database, the results should resemble of the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `Ipoh Coffee`  
  
 `2`  
  
 `Grandma's Boysenberry Spread`  
  
 `Northwoods Cranberry Sauce`  
  
 `Sirop d'érable`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `Gumbär Gummibärchen`  
  
 `Schoggi Schokolade`  
  
 `Tarte au sucre`  
  
 `4`  
  
 `Queso Manchego La Pastora`  
  
 `Mascarpone Fabioli`  
  
 `Raclette Courdavault`  
  
 `Camembert Pierrot`  
  
 `Gudbrandsdalsost`  
  
 `Mozzarella di Giovanni`  
  
 `5`  
  
 `Gustaf's Knäckebröd`  
  
 `Gnocchi di nonna Alice`  
  
 `Wimmers gute Semmelknödel`  
  
 `6`  
  
 `Mishi Kobe Niku`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Rössle Sauerkraut`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Ikura`  
  
 `Carnarvon Tigers`  
  
 `Nord-Ost Matjeshering`  
  
 `Gravad lax`  
  
## <a name="see-also"></a><span data-ttu-id="c1839-117">См. также</span><span class="sxs-lookup"><span data-stu-id="c1839-117">See also</span></span>

- [<span data-ttu-id="c1839-118">Статистические запросы</span><span class="sxs-lookup"><span data-stu-id="c1839-118">Aggregate Queries</span></span>](aggregate-queries.md)
