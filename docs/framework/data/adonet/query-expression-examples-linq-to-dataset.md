---
description: Дополнительные сведения см. в статье примеры выражений запросов (LINQ to DataSet).
title: Примеры выражений запроса (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: f743fbc7-faff-45e5-af1e-61577d87f0cc
ms.openlocfilehash: 1d1571a851fae685942cbdbd557b275e86e8b0d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663694"
---
# <a name="query-expression-examples-linq-to-dataset"></a><span data-ttu-id="8b233-103">Примеры выражений запроса (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="8b233-103">Query Expression Examples (LINQ to DataSet)</span></span>

<span data-ttu-id="8b233-104">В этом разделе приводятся LINQ to DataSet примеры программирования в синтаксисе выражений запросов, в которых используются стандартные операторы запросов.</span><span class="sxs-lookup"><span data-stu-id="8b233-104">This section provides LINQ to DataSet programming examples in query expression syntax that use the standard query operators.</span></span> <span data-ttu-id="8b233-105">Объект, <xref:System.Data.DataSet> используемый в этих примерах, заполняется с помощью `FillDataSet` метода, который задается при [загрузке данных в набор данных](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="8b233-105">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="8b233-106">Дополнительные сведения см. в разделе Общие сведения [о стандартных операторах запросов (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) или [Общие сведения о стандартных операторах запросов (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8b233-106">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b233-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="8b233-107">In This Section</span></span>  

 [<span data-ttu-id="8b233-108">Проекция</span><span class="sxs-lookup"><span data-stu-id="8b233-108">Projection</span></span>](query-expression-syntax-examples-projection-linq-to-dataset.md)  
 <span data-ttu-id="8b233-109">Примеры в данном разделе демонстрируют, как использовать методы <xref:System.Linq.Enumerable.Select%2A> и <xref:System.Linq.Enumerable.SelectMany%2A> для запроса к <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8b233-109">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="8b233-110">Ограничение</span><span class="sxs-lookup"><span data-stu-id="8b233-110">Restriction</span></span>](query-expression-syntax-examples-restriction-linq-to-dataset.md)  
 <span data-ttu-id="8b233-111">В примерах этого раздела показано, как использовать метод <xref:System.Linq.Enumerable.Where%2A> в запросе к <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8b233-111">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="8b233-112">Секционирование</span><span class="sxs-lookup"><span data-stu-id="8b233-112">Partitioning</span></span>](query-expression-syntax-examples-partitioning.md)  
 <span data-ttu-id="8b233-113">Примеры в данном разделе демонстрируют, как использовать методы <xref:System.Linq.Enumerable.Skip%2A> и <xref:System.Linq.Enumerable.Take%2A> для запроса <xref:System.Data.DataSet> и секционирования результатов.</span><span class="sxs-lookup"><span data-stu-id="8b233-113">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="8b233-114">Упорядочение</span><span class="sxs-lookup"><span data-stu-id="8b233-114">Ordering</span></span>](query-expression-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="8b233-115">Примеры в данном разделе демонстрируют, как использовать методы <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A> и <xref:System.Linq.Enumerable.ThenByDescending%2A> для запроса к <xref:System.Data.DataSet> и упорядочения результатов.</span><span class="sxs-lookup"><span data-stu-id="8b233-115">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="8b233-116">Операторы элементов</span><span class="sxs-lookup"><span data-stu-id="8b233-116">Element Operators</span></span>](query-expression-syntax-examples-element-operators.md)  
 <span data-ttu-id="8b233-117">Примеры в данном разделе демонстрируют, как использовать методы <xref:System.Linq.Enumerable.First%2A> и <xref:System.Linq.Enumerable.ElementAt%2A> для получения элементов <xref:System.Data.DataRow> из <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8b233-117">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="8b233-118">Операторы статистических выражений</span><span class="sxs-lookup"><span data-stu-id="8b233-118">Aggregate Operators</span></span>](query-expression-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="8b233-119">Примеры в данном разделе демонстрируют, как использовать методы <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A> и <xref:System.Linq.Enumerable.Sum%2A> для запроса <xref:System.Data.DataSet> и статистической обработки данных.</span><span class="sxs-lookup"><span data-stu-id="8b233-119">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="8b233-120">Операторы соединения</span><span class="sxs-lookup"><span data-stu-id="8b233-120">Join Operators</span></span>](query-expression-syntax-examples-join-operators.md)  
 <span data-ttu-id="8b233-121">Примеры в данном разделе демонстрируют, как использовать методы <xref:System.Linq.Enumerable.GroupJoin%2A> и <xref:System.Linq.Enumerable.Join%2A> для запроса к <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8b233-121">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b233-122">См. также</span><span class="sxs-lookup"><span data-stu-id="8b233-122">See also</span></span>

- [<span data-ttu-id="8b233-123">Примеры запросов на основе методов</span><span class="sxs-lookup"><span data-stu-id="8b233-123">Method-Based Query Examples</span></span>](method-based-query-examples-linq-to-dataset.md)
- [<span data-ttu-id="8b233-124">Связанные с определенными наборами данных примеры операторов</span><span class="sxs-lookup"><span data-stu-id="8b233-124">DataSet-Specific Operator Examples</span></span>](dataset-specific-operator-examples-linq-to-dataset.md)
- [<span data-ttu-id="8b233-125">Примеры LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="8b233-125">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
