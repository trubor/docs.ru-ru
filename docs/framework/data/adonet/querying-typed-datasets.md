---
description: 'Дополнительные сведения: запрос типизированных наборов данных'
title: Запросы к типизированным наборам данных
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 5bcf8bb587a0ed0eaca1bbe9b3a7d7143757780e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723703"
---
# <a name="query-typed-datasets"></a><span data-ttu-id="3a0c9-103">Запрос типизированных наборов данных</span><span class="sxs-lookup"><span data-stu-id="3a0c9-103">Query typed DataSets</span></span>

<span data-ttu-id="3a0c9-104">Если схема объекта <xref:System.Data.DataSet> известна во время разработки приложения, рекомендуется использовать типизированный <xref:System.Data.DataSet> при использовании LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="3a0c9-104">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using LINQ to DataSet.</span></span> <span data-ttu-id="3a0c9-105">Типизированный <xref:System.Data.DataSet> — это класс, производный от класса <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="3a0c9-105">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="3a0c9-106">Поэтому он наследует все методы, события и свойства класса <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="3a0c9-106">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="3a0c9-107">Кроме того, типизированный объект <xref:System.Data.DataSet> предоставляет строго типизированные методы, события и свойства.</span><span class="sxs-lookup"><span data-stu-id="3a0c9-107">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="3a0c9-108">Это означает, что доступ к таблицам и столбцам можно получить по имени, не используя методы на основе коллекций.</span><span class="sxs-lookup"><span data-stu-id="3a0c9-108">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="3a0c9-109">Это упрощает запросы и повышает их читаемость.</span><span class="sxs-lookup"><span data-stu-id="3a0c9-109">This makes queries simpler and more readable.</span></span> <span data-ttu-id="3a0c9-110">Дополнительные сведения см. в разделе [типизированные наборы данных](./dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="3a0c9-110">For more information, see [Typed DataSets](./dataset-datatable-dataview/typed-datasets.md).</span></span>

<span data-ttu-id="3a0c9-111">LINQ to DataSet также поддерживает запросы к типизированным <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="3a0c9-111">LINQ to DataSet also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="3a0c9-112">В типизированном виде нет необходимости <xref:System.Data.DataSet> использовать универсальный <xref:System.Data.DataRowExtensions.Field%2A> метод или <xref:System.Data.DataRowExtensions.SetField%2A> метод для доступа к данным столбца.</span><span class="sxs-lookup"><span data-stu-id="3a0c9-112">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span> <span data-ttu-id="3a0c9-113">Имена свойств доступны во время компиляции, так как сведения о типе включены в <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="3a0c9-113">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="3a0c9-114">LINQ to DataSet предоставляет доступ к значениям столбцов в качестве правильного типа, поэтому ошибки несоответствия типов перехватываются при компиляции кода, а не во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="3a0c9-114">LINQ to DataSet provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>

<span data-ttu-id="3a0c9-115">Прежде чем начать запрос к типизированному типу <xref:System.Data.DataSet> , необходимо создать класс с помощью **конструктора наборов данных** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3a0c9-115">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the **DataSet Designer** in Visual Studio.</span></span> <span data-ttu-id="3a0c9-116">Дополнительные сведения см. в разделе [Создание и Настройка наборов данных](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="3a0c9-116">For more information, see [Create and configure DataSets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>

## <a name="example"></a><span data-ttu-id="3a0c9-117">Пример</span><span class="sxs-lookup"><span data-stu-id="3a0c9-117">Example</span></span>

<span data-ttu-id="3a0c9-118">В следующем примере показан запрос к типизированному объекту <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="3a0c9-118">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>

```csharp
var query = from o in orders
            where o.OnlineOrderFlag == true
            select new { o.SalesOrderID,
                         o.OrderDate,
                         o.SalesOrderNumber };

foreach(var order in query)
{
    Console.WriteLine("{0}\t{1:d}\t{2}",
      order.SalesOrderID,
      order.OrderDate,
      order.SalesOrderNumber);
}
```

```vb
Dim orders = ds.Tables("SalesOrderHeader")

Dim query = _
       From o In orders _
       Where o.OnlineOrderFlag = True _
       Select New {SalesOrderID := o.SalesOrderID, _
                   OrderDate := o.OrderDate, _
                   SalesOrderNumber := o.SalesOrderNumber}

For Each Dim onlineOrder In query
 Console.WriteLine("{0}\t{1:d}\t{2}", _
 onlineOrder.SalesOrderID, _
 onlineOrder.OrderDate, _
 onlineOrder.SalesOrderNumber)
Next
```

## <a name="see-also"></a><span data-ttu-id="3a0c9-119">См. также</span><span class="sxs-lookup"><span data-stu-id="3a0c9-119">See also</span></span>

- [<span data-ttu-id="3a0c9-120">Запросы к DataSet</span><span class="sxs-lookup"><span data-stu-id="3a0c9-120">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="3a0c9-121">Запросы между таблицами</span><span class="sxs-lookup"><span data-stu-id="3a0c9-121">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="3a0c9-122">Запросы к одной таблице</span><span class="sxs-lookup"><span data-stu-id="3a0c9-122">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)
