---
description: 'Дополнительные сведения: Сортировка с помощью DataView (LINQ to DataSet)'
title: Сортировка с использованием объекта DataView (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: ac07e5bc2c74a5724a4497d630d7352694ac9a7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718685"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a><span data-ttu-id="da7df-103">Сортировка с использованием объекта DataView (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="da7df-103">Sorting with DataView (LINQ to DataSet)</span></span>

<span data-ttu-id="da7df-104">Возможность сортировки данных на основе заданных критериев и их предоставление клиенту с помощью элемента управления в пользовательском интерфейсе - это важный аспект привязки данных.</span><span class="sxs-lookup"><span data-stu-id="da7df-104">The ability to sort data based on specific criteria and then present the data to a client through a UI control is an important aspect of data binding.</span></span> <span data-ttu-id="da7df-105">Объект <xref:System.Data.DataView> предоставляет несколько способов сортировки и возврата строк данных, упорядоченных по определенным критериям.</span><span class="sxs-lookup"><span data-stu-id="da7df-105"><xref:System.Data.DataView> provides several ways to sort data and return data rows ordered by specific ordering criteria.</span></span> <span data-ttu-id="da7df-106">В дополнение к возможностям сортировки на основе строк <xref:System.Data.DataView> также позволяет использовать выражения Language-Integrated запросов (LINQ) для критериев сортировки.</span><span class="sxs-lookup"><span data-stu-id="da7df-106">In addition to its string-based sorting capabilities, <xref:System.Data.DataView> also enables you to use Language-Integrated Query (LINQ) expressions for the sorting criteria.</span></span> <span data-ttu-id="da7df-107">Выражения LINQ позволяют выполнять гораздо более сложные и эффективные операции сортировки, чем сортировка на основе строк.</span><span class="sxs-lookup"><span data-stu-id="da7df-107">LINQ expressions allow for much more complex and powerful sorting operations than string-based sorting.</span></span> <span data-ttu-id="da7df-108">В этом разделе описываются оба подхода к сортировке с помощью объекта <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="da7df-108">This topic describes both approaches to sorting using <xref:System.Data.DataView>.</span></span>  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a><span data-ttu-id="da7df-109">Создание объекта DataView на основе запроса с данными сортировки</span><span class="sxs-lookup"><span data-stu-id="da7df-109">Creating DataView from a Query with Sorting Information</span></span>  

 <span data-ttu-id="da7df-110"><xref:System.Data.DataView>Объект может быть создан из LINQ to DataSet запроса.</span><span class="sxs-lookup"><span data-stu-id="da7df-110">A <xref:System.Data.DataView> object can be created from a LINQ to DataSet query.</span></span> <span data-ttu-id="da7df-111">Если этот запрос содержит <xref:System.Linq.Enumerable.OrderBy%2A> предложение, <xref:System.Linq.Enumerable.OrderByDescending%2A> , <xref:System.Linq.Enumerable.ThenBy%2A> или, <xref:System.Linq.Enumerable.ThenByDescending%2A> то выражения в этих предложениях используются в качестве базиса для сортировки данных в <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="da7df-111">If that query contains an <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, or <xref:System.Linq.Enumerable.ThenByDescending%2A> clause the expressions in these clauses are used as the basis for sorting the data in the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="da7df-112">Например, если запрос содержит `Order By…` `Then By…` предложения and, результирующие <xref:System.Data.DataView> данные будут упорядочены по обоим столбцам.</span><span class="sxs-lookup"><span data-stu-id="da7df-112">For example, if the query contains the `Order By…`and `Then By…` clauses, the resulting <xref:System.Data.DataView> would order the data by both columns specified.</span></span>  
  
 <span data-ttu-id="da7df-113">Сортировка на основе выражений является более сложной и мощной операцией сортировки, чем более простая сортировка на основе строк.</span><span class="sxs-lookup"><span data-stu-id="da7df-113">Expression-based sorting offers more powerful and complex sorting than the simpler string-based sorting.</span></span> <span data-ttu-id="da7df-114">Следует иметь в виду, что сортировки на основе строк и выражений являются взаимоисключающими.</span><span class="sxs-lookup"><span data-stu-id="da7df-114">Note that string-based and expression-based sorting are mutually exclusive.</span></span> <span data-ttu-id="da7df-115">Если сортировка на основе строк <xref:System.Data.DataView.Sort%2A> задается после создания объекта <xref:System.Data.DataView> на основе запроса, то выводимый из запроса фильтр на основе выражений удаляется и не восстанавливается.</span><span class="sxs-lookup"><span data-stu-id="da7df-115">If the string-based <xref:System.Data.DataView.Sort%2A> is set after a <xref:System.Data.DataView> is created from a query, the expression-based filter inferred from the query is cleared and cannot be reset.</span></span>  
  
 <span data-ttu-id="da7df-116">Индекс для <xref:System.Data.DataView> формируется как при создании <xref:System.Data.DataView>, так и при изменении каких-либо сведений о сортировке или фильтрации.</span><span class="sxs-lookup"><span data-stu-id="da7df-116">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="da7df-117">Вы получаете максимальную производительность, предоставляя критерии сортировки в LINQ to DataSet запросе, который <xref:System.Data.DataView> создается из, и не изменяет сведения о сортировке позже.</span><span class="sxs-lookup"><span data-stu-id="da7df-117">You get the best performance by supplying sorting criteria in the LINQ to DataSet query that the <xref:System.Data.DataView> is created from and not modifying the sorting information, later.</span></span> <span data-ttu-id="da7df-118">Дополнительные сведения см. в разделе [производительность DataView](dataview-performance.md).</span><span class="sxs-lookup"><span data-stu-id="da7df-118">For more information, see [DataView Performance](dataview-performance.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da7df-119">В большинстве случаев выражение, используемое для сортировки, не должно иметь побочных эффектов и должно быть детерминированным.</span><span class="sxs-lookup"><span data-stu-id="da7df-119">In most cases, the expressions used for sorting should not have side effects and must be deterministic.</span></span> <span data-ttu-id="da7df-120">Также эти выражения не должны содержать логику, зависящую от заданного количества выполнений, так как операции сортировки могут выполняться любое количество раз.</span><span class="sxs-lookup"><span data-stu-id="da7df-120">Also, the expressions should not contain any logic that depends on a set number of executions, because the sorting operations might be executed any number of times.</span></span>  
  
### <a name="example"></a><span data-ttu-id="da7df-121">Пример</span><span class="sxs-lookup"><span data-stu-id="da7df-121">Example</span></span>  

 <span data-ttu-id="da7df-122">В следующем примере выполняется запрос к таблице SalesOrderHeader, а полученные строки упорядочиваются по дате заказа; на основе этого запроса создается объект <xref:System.Data.DataView> и привязывается к <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="da7df-122">The following example queries the SalesOrderHeader table and orders the returned rows by the order date; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a><span data-ttu-id="da7df-123">Пример</span><span class="sxs-lookup"><span data-stu-id="da7df-123">Example</span></span>  

 <span data-ttu-id="da7df-124">В следующем примере выполняется запрос к таблице SalesOrderHeader, а полученные строки упорядочиваются по общей стоимости; на основе этого запроса создается объект <xref:System.Data.DataView> и привязывается к <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="da7df-124">The following example queries the SalesOrderHeader table and orders the returned row by total amount due; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a><span data-ttu-id="da7df-125">Пример</span><span class="sxs-lookup"><span data-stu-id="da7df-125">Example</span></span>  

 <span data-ttu-id="da7df-126">В следующем примере выполняется запрос к таблице SalesOrderDetail, а полученные строки упорядочиваются по объему заказа, а затем по идентификатору заказа на продажу; на основе этого запроса создается объект <xref:System.Data.DataView> и привязывается к <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="da7df-126">The following example queries the SalesOrderDetail table and orders the returned rows by order quantity and then by sales order ID; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a><span data-ttu-id="da7df-127">Использование свойства сортировки на основе строк</span><span class="sxs-lookup"><span data-stu-id="da7df-127">Using the String-Based Sort Property</span></span>  

 <span data-ttu-id="da7df-128">Функции сортировки на основе строк <xref:System.Data.DataView> по-прежнему работают с LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="da7df-128">The string-based sorting functionality of <xref:System.Data.DataView> still works with LINQ to DataSet.</span></span> <span data-ttu-id="da7df-129">После <xref:System.Data.DataView> создания из LINQ to DataSet запроса можно использовать <xref:System.Data.DataView.Sort%2A> свойство, чтобы задать сортировку для <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="da7df-129">After a <xref:System.Data.DataView> has been created from a LINQ to DataSet query, you can use the <xref:System.Data.DataView.Sort%2A> property to set the sorting on the <xref:System.Data.DataView>.</span></span>  
  
 <span data-ttu-id="da7df-130">Возможности сортировки на основе строк и выражений являются взаимоисключающими.</span><span class="sxs-lookup"><span data-stu-id="da7df-130">The string-based and expression-based sorting functionality are mutually exclusive.</span></span> <span data-ttu-id="da7df-131">При задании свойства <xref:System.Data.DataView.Sort%2A> сортировка на основе выражений, унаследованная из запроса, на основе которого был создан объект <xref:System.Data.DataView>, удаляется.</span><span class="sxs-lookup"><span data-stu-id="da7df-131">Setting the <xref:System.Data.DataView.Sort%2A> property will clear the expression-based sort inherited from the query that the <xref:System.Data.DataView> was created from.</span></span>  
  
 <span data-ttu-id="da7df-132">Дополнительные сведения о фильтрации на основе строк <xref:System.Data.DataView.Sort%2A> см. в разделе [Сортировка и фильтрация данных](./dataset-datatable-dataview/sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="da7df-132">For more information about string-based <xref:System.Data.DataView.Sort%2A> filtering, see [Sorting and Filtering Data](./dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="da7df-133">Пример</span><span class="sxs-lookup"><span data-stu-id="da7df-133">Example</span></span>  

 <span data-ttu-id="da7df-134">В следующем примере объект <xref:System.Data.DataView> создается на основе таблицы Contact, затем выполняется сортировка по фамилиям в возрастающем порядке, а затем по именам в убывающем порядке:</span><span class="sxs-lookup"><span data-stu-id="da7df-134">The follow example creates a <xref:System.Data.DataView> from the Contact table and sorts the rows by last name in descending order, then first name in ascending order:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a><span data-ttu-id="da7df-135">Пример</span><span class="sxs-lookup"><span data-stu-id="da7df-135">Example</span></span>  

 <span data-ttu-id="da7df-136">В следующем примере выполняется запрос к таблице Contact, который должен вернуть фамилии, начинающиеся на букву «S».</span><span class="sxs-lookup"><span data-stu-id="da7df-136">The following example queries the Contact table for last names that start with the letter "S".</span></span>  <span data-ttu-id="da7df-137">На основе этого запроса создается объект <xref:System.Data.DataView> и привязывается к объекту <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="da7df-137">A <xref:System.Data.DataView> is created from that query and bound to a <xref:System.Windows.Forms.BindingSource> object.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a><span data-ttu-id="da7df-138">Очистка сортировки</span><span class="sxs-lookup"><span data-stu-id="da7df-138">Clearing the Sort</span></span>  

 <span data-ttu-id="da7df-139">Данные сортировки для объекта <xref:System.Data.DataView> можно очистить после их задания с помощью свойства <xref:System.Data.DataView.Sort%2A>.</span><span class="sxs-lookup"><span data-stu-id="da7df-139">The sorting information on a <xref:System.Data.DataView> can be cleared after it has been set using the <xref:System.Data.DataView.Sort%2A> property.</span></span> <span data-ttu-id="da7df-140">Существует два способа очистки данных сортировки <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="da7df-140">There are two ways to clear the sorting information in <xref:System.Data.DataView>:</span></span>  
  
- <span data-ttu-id="da7df-141">Задайте для свойства <xref:System.Data.DataView.Sort%2A> значение `null`.</span><span class="sxs-lookup"><span data-stu-id="da7df-141">Set the <xref:System.Data.DataView.Sort%2A> property to `null`.</span></span>  
  
- <span data-ttu-id="da7df-142">Установите свойство <xref:System.Data.DataView.Sort%2A> равным пустой строке.</span><span class="sxs-lookup"><span data-stu-id="da7df-142">Set the <xref:System.Data.DataView.Sort%2A> property to an empty string.</span></span>  
  
### <a name="example"></a><span data-ttu-id="da7df-143">Пример</span><span class="sxs-lookup"><span data-stu-id="da7df-143">Example</span></span>  

 <span data-ttu-id="da7df-144">В следующем примере объект <xref:System.Data.DataView> создается на основе запроса и данные сортировки очищаются путем установки для свойства <xref:System.Data.DataView.Sort%2A> значения, равного пустой строке:</span><span class="sxs-lookup"><span data-stu-id="da7df-144">The following example creates a <xref:System.Data.DataView> from a query and clears the sorting by setting the <xref:System.Data.DataView.Sort%2A> property to an empty string:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a><span data-ttu-id="da7df-145">Пример</span><span class="sxs-lookup"><span data-stu-id="da7df-145">Example</span></span>  

 <span data-ttu-id="da7df-146">В следующем примере объект <xref:System.Data.DataView> создается на основе таблицы Contact и в свойстве <xref:System.Data.DataView.Sort%2A> задается сортировка по фамилиям в убывающем порядке.</span><span class="sxs-lookup"><span data-stu-id="da7df-146">The following example creates a <xref:System.Data.DataView> from the Contact table and sets the <xref:System.Data.DataView.Sort%2A> property to sort by last name in descending order.</span></span> <span data-ttu-id="da7df-147">Затем данные сортировки очищаются путем установки для свойства <xref:System.Data.DataView.Sort%2A> значения `null`:</span><span class="sxs-lookup"><span data-stu-id="da7df-147">The sorting information is then cleared by setting the <xref:System.Data.DataView.Sort%2A> property to `null`:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a><span data-ttu-id="da7df-148">См. также</span><span class="sxs-lookup"><span data-stu-id="da7df-148">See also</span></span>

- [<span data-ttu-id="da7df-149">Привязка данных и LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="da7df-149">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
- [<span data-ttu-id="da7df-150">Фильтрация с использованием объекта DataView</span><span class="sxs-lookup"><span data-stu-id="da7df-150">Filtering with DataView</span></span>](filtering-with-dataview-linq-to-dataset.md)
- <span data-ttu-id="da7df-151">[Сортировка данных](/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="da7df-151">[Sorting Data](/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))</span></span>
