---
description: 'Дополнительные сведения: статистические запросы'
title: Статистические запросы
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 2b9b71440c804740e2f04d5b2dc8c2cd111634b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712835"
---
# <a name="aggregate-queries"></a><span data-ttu-id="57531-103">Статистические запросы</span><span class="sxs-lookup"><span data-stu-id="57531-103">Aggregate Queries</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="57531-104">поддерживает агрегатные операторы `Average`, `Count`, `Max`, `Min` и `Sum`.</span><span class="sxs-lookup"><span data-stu-id="57531-104">supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="57531-105">Обратите внимание на следующие характеристики агрегатных операторов в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="57531-105">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="57531-106">Агрегатные запросы выполняются немедленно.</span><span class="sxs-lookup"><span data-stu-id="57531-106">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="57531-107">Дополнительные сведения см. в разделе [Введение в запросы LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="57531-107">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
- <span data-ttu-id="57531-108">Агрегатные запросы обычно возвращают число, а не коллекцию.</span><span class="sxs-lookup"><span data-stu-id="57531-108">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="57531-109">Дополнительные сведения см. в разделе [операции агрегирования](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="57531-109">For more information, see [Aggregation Operations](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span></span>  
  
- <span data-ttu-id="57531-110">В анонимном типе вызвать агрегаты нельзя.</span><span class="sxs-lookup"><span data-stu-id="57531-110">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="57531-111">В следующих разделах используются примеры из учебной базы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="57531-111">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="57531-112">Дополнительные сведения см. в статье [Загрузка образцов баз данных](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="57531-112">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57531-113">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="57531-113">In This Section</span></span>  

 [<span data-ttu-id="57531-114">Возврат среднего значения из числовой последовательности</span><span class="sxs-lookup"><span data-stu-id="57531-114">Return the Average Value From a Numeric Sequence</span></span>](return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="57531-115">Демонстрируется использование оператора <xref:System.Linq.Enumerable.Average%2A>.</span><span class="sxs-lookup"><span data-stu-id="57531-115">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="57531-116">Подсчет количества элементов в последовательности</span><span class="sxs-lookup"><span data-stu-id="57531-116">Count the Number of Elements in a Sequence</span></span>](count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="57531-117">Демонстрируется использование оператора <xref:System.Linq.Enumerable.Count%2A>.</span><span class="sxs-lookup"><span data-stu-id="57531-117">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="57531-118">Нахождение максимального значения в числовой последовательности</span><span class="sxs-lookup"><span data-stu-id="57531-118">Find the Maximum Value in a Numeric Sequence</span></span>](find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="57531-119">Демонстрируется использование оператора <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="57531-119">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="57531-120">Нахождение минимального значения в числовой последовательности</span><span class="sxs-lookup"><span data-stu-id="57531-120">Find the Minimum Value in a Numeric Sequence</span></span>](find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="57531-121">Демонстрируется использование оператора <xref:System.Linq.Enumerable.Min%2A>.</span><span class="sxs-lookup"><span data-stu-id="57531-121">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="57531-122">Вычисление суммы значений в числовой последовательности</span><span class="sxs-lookup"><span data-stu-id="57531-122">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="57531-123">Демонстрируется использование оператора <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="57531-123">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="57531-124">См. также</span><span class="sxs-lookup"><span data-stu-id="57531-124">Related Sections</span></span>  

 [<span data-ttu-id="57531-125">Примеры запросов</span><span class="sxs-lookup"><span data-stu-id="57531-125">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="57531-126">Содержит ссылки на запросы [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] в Visual Basic и C#.</span><span class="sxs-lookup"><span data-stu-id="57531-126">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="57531-127">Основные принципы запросов</span><span class="sxs-lookup"><span data-stu-id="57531-127">Query Concepts</span></span>](query-concepts.md)  
 <span data-ttu-id="57531-128">Содержит ссылки на разделы, в которых объясняются основные понятия для разработки запросов LINQ в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="57531-128">Provides links to topics that explain concepts for designing LINQ queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="57531-129">Введение в запросы LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="57531-129">Introduction to LINQ Queries (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="57531-130">Объясняет, как работают запросы в LINQ.</span><span class="sxs-lookup"><span data-stu-id="57531-130">Explains how queries work in LINQ.</span></span>
