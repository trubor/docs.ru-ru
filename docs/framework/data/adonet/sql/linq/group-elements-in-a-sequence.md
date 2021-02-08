---
description: Дополнительные сведения о группировании элементов в последовательности
title: Группировка элементов последовательности
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
ms.openlocfilehash: bc9a4d042ed0edb090f0530ebb24d99a5390c882
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786073"
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="ae076-103">Группировка элементов последовательности</span><span class="sxs-lookup"><span data-stu-id="ae076-103">Group Elements in a Sequence</span></span>

<span data-ttu-id="ae076-104">Оператор <xref:System.Linq.Enumerable.GroupBy%2A> группирует элементы последовательности.</span><span class="sxs-lookup"><span data-stu-id="ae076-104">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="ae076-105">В следующем примере используется база данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="ae076-105">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae076-106">Иногда значения NULL в столбцах в запросах <xref:System.Linq.Enumerable.GroupBy%2A> могут вызывать исключение <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="ae076-106">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="ae076-107">Дополнительные сведения см. в разделе "GroupBy InvalidOperationException" раздела [Устранение неполадок](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="ae076-107">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae076-108">Пример</span><span class="sxs-lookup"><span data-stu-id="ae076-108">Example</span></span>  

 <span data-ttu-id="ae076-109">Следующий пример разделяет `Products` по `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="ae076-109">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="ae076-110">Пример</span><span class="sxs-lookup"><span data-stu-id="ae076-110">Example</span></span>  

 <span data-ttu-id="ae076-111">В следующем примере для нахождения максимальной цены за единицу для каждого <xref:System.Linq.Enumerable.Max%2A> используется `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="ae076-111">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="ae076-112">Пример</span><span class="sxs-lookup"><span data-stu-id="ae076-112">Example</span></span>  

 <span data-ttu-id="ae076-113">В следующем примере для нахождения среднего значения `UnitPrice` для каждого `CategoryID` используется функция Average.</span><span class="sxs-lookup"><span data-stu-id="ae076-113">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="ae076-114">Пример</span><span class="sxs-lookup"><span data-stu-id="ae076-114">Example</span></span>  

 <span data-ttu-id="ae076-115">В следующем примере для нахождения общего значения <xref:System.Linq.Queryable.Sum%2A> для каждого `UnitPrice` используется `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="ae076-115">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="ae076-116">Пример</span><span class="sxs-lookup"><span data-stu-id="ae076-116">Example</span></span>  

 <span data-ttu-id="ae076-117">В следующем примере для нахождения в каждом <xref:System.Linq.Queryable.Count%2A> числа `Products`, производство которых прекращено, используется `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="ae076-117">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="ae076-118">Пример</span><span class="sxs-lookup"><span data-stu-id="ae076-118">Example</span></span>  

 <span data-ttu-id="ae076-119">В следующем примере для нахождения всех категорий, включающих как минимум 10 продуктов, используется предложение `where`.</span><span class="sxs-lookup"><span data-stu-id="ae076-119">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="ae076-120">Пример</span><span class="sxs-lookup"><span data-stu-id="ae076-120">Example</span></span>  

 <span data-ttu-id="ae076-121">В следующем примере продукты сгруппированы по `CategoryID` и `SupplierID`.</span><span class="sxs-lookup"><span data-stu-id="ae076-121">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="ae076-122">Пример</span><span class="sxs-lookup"><span data-stu-id="ae076-122">Example</span></span>  

 <span data-ttu-id="ae076-123">В следующем примере возвращается две последовательности продуктов.</span><span class="sxs-lookup"><span data-stu-id="ae076-123">The following example returns two sequences of products.</span></span> <span data-ttu-id="ae076-124">В первой последовательности находятся продукты, цена за единицу которых меньше или равна 10.</span><span class="sxs-lookup"><span data-stu-id="ae076-124">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="ae076-125">Во второй последовательности содержатся продукты, цена за единицу которых больше 10.</span><span class="sxs-lookup"><span data-stu-id="ae076-125">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="ae076-126">Пример</span><span class="sxs-lookup"><span data-stu-id="ae076-126">Example</span></span>  

 <span data-ttu-id="ae076-127">Оператор <xref:System.Linq.Queryable.GroupBy%2A> может принимает только один основной аргумент.</span><span class="sxs-lookup"><span data-stu-id="ae076-127">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="ae076-128">Если требуется выполнить группировку по нескольким признакам, следует создать анонимный тип, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="ae076-128">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="ae076-129">См. также</span><span class="sxs-lookup"><span data-stu-id="ae076-129">See also</span></span>

- [<span data-ttu-id="ae076-130">Примеры запросов</span><span class="sxs-lookup"><span data-stu-id="ae076-130">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="ae076-131">Загрузка примеров баз данных</span><span class="sxs-lookup"><span data-stu-id="ae076-131">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
