---
description: Дополнительные сведения см. в статье сравнение строк (LINQ to DataSet)
title: Сравнение объектов DataRow (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: df410432ab31d5ee284cb1d7cd15661db65ca503
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663941"
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="6a452-103">Сравнение объектов DataRow (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="6a452-103">Comparing DataRows (LINQ to DataSet)</span></span>

<span data-ttu-id="6a452-104">Language-Integrated query (LINQ) определяет различные операторы наборов для сравнения элементов источника, чтобы определить, равны ли они.</span><span class="sxs-lookup"><span data-stu-id="6a452-104">Language-Integrated Query (LINQ) defines various set operators to compare source elements to see if they are equal.</span></span> <span data-ttu-id="6a452-105">LINQ предоставляет следующие операторы SET:</span><span class="sxs-lookup"><span data-stu-id="6a452-105">LINQ provides the following set operators:</span></span>  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="6a452-106">Эти операторы сравнивают элементы путем вызова методов <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> и <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> для каждой коллекции элементов.</span><span class="sxs-lookup"><span data-stu-id="6a452-106">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="6a452-107">Для объектов <xref:System.Data.DataRow> эти операторы выполняют ссылочное сравнение, которое в общем случае не является идеальным для операторов наборов, выполняющихся над табличными данными.</span><span class="sxs-lookup"><span data-stu-id="6a452-107">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="6a452-108">Для операторов наборов обычно требуется определить, являются ли равными значения элементов, а не ссылки на элементы.</span><span class="sxs-lookup"><span data-stu-id="6a452-108">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="6a452-109">Таким образом, <xref:System.Data.DataRowComparer> класс добавлен в LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="6a452-109">Therefore, the <xref:System.Data.DataRowComparer> class has been added to LINQ to DataSet.</span></span> <span data-ttu-id="6a452-110">Этот класс можно использовать для сравнения значений в строках.</span><span class="sxs-lookup"><span data-stu-id="6a452-110">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="6a452-111">Класс <xref:System.Data.DataRowComparer> содержит реализацию сравнения значений для объектов <xref:System.Data.DataRow>, поэтому его можно использовать в операциях над наборами, таких как <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="6a452-111">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="6a452-112">Этот класс нельзя создать напрямую, вместо этого необходимо использовать свойство <xref:System.Data.DataRowComparer.Default%2A> для возврата экземпляра <xref:System.Data.DataRowComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="6a452-112">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="6a452-113">Затем вызывается метод <xref:System.Data.DataRowComparer%601.Equals%2A>, которому в качестве входных параметров передаются два сравниваемых объекта <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="6a452-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="6a452-114">Метод <xref:System.Data.DataRowComparer%601.Equals%2A> возвращает значение `true`, если упорядоченные наборы значений столбцов в обоих объектах <xref:System.Data.DataRow> равны, в противном случае значение `false`.</span><span class="sxs-lookup"><span data-stu-id="6a452-114">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a452-115">Пример</span><span class="sxs-lookup"><span data-stu-id="6a452-115">Example</span></span>  

 <span data-ttu-id="6a452-116">В этом примере инструкция `Intersect` используется для возврата контактов, находящихся в обеих таблицах.</span><span class="sxs-lookup"><span data-stu-id="6a452-116">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="6a452-117">Пример</span><span class="sxs-lookup"><span data-stu-id="6a452-117">Example</span></span>  

 <span data-ttu-id="6a452-118">В следующем примере сравниваются две строки и возвращаются их хэш-коды.</span><span class="sxs-lookup"><span data-stu-id="6a452-118">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="6a452-119">См. также</span><span class="sxs-lookup"><span data-stu-id="6a452-119">See also</span></span>

- <xref:System.Data.DataRowComparer>
- [<span data-ttu-id="6a452-120">Загрузка данных в набор данных</span><span class="sxs-lookup"><span data-stu-id="6a452-120">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="6a452-121">Примеры LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="6a452-121">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
