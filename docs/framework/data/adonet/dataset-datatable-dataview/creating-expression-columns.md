---
description: 'Дополнительные сведения: создание столбцов выражений'
title: Создание столбцов выражений
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 96b445734d645a957951a1d4cbd9d72ed254068f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724990"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="9b143-103">Создание столбцов выражений</span><span class="sxs-lookup"><span data-stu-id="9b143-103">Creating Expression Columns</span></span>

<span data-ttu-id="9b143-104">Можно определить выражение для столбца, позволяя тем самым хранить в нем значение, вычисляемое из значений других столбцов той же строки или из значений столбцов нескольких строк таблицы.</span><span class="sxs-lookup"><span data-stu-id="9b143-104">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="9b143-105">Для определения вычисляемого выражения используется свойство <xref:System.Data.DataColumn.Expression%2A> целевого столбца, свойство <xref:System.Data.DataColumn.ColumnName%2A> - для ссылки на другие столбцы в выражении.</span><span class="sxs-lookup"><span data-stu-id="9b143-105">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="9b143-106">Тип данных <xref:System.Data.DataColumn.DataType%2A> столбца выражения должен соответствовать типу данных значения, возвращаемого выражением.</span><span class="sxs-lookup"><span data-stu-id="9b143-106">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="9b143-107">В следующей таблице приведен список возможного использования столбцов выражений в таблице.</span><span class="sxs-lookup"><span data-stu-id="9b143-107">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="9b143-108">Тип выражения</span><span class="sxs-lookup"><span data-stu-id="9b143-108">Expression type</span></span>|<span data-ttu-id="9b143-109">Пример</span><span class="sxs-lookup"><span data-stu-id="9b143-109">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="9b143-110">Сравнение</span><span class="sxs-lookup"><span data-stu-id="9b143-110">Comparison</span></span>|<span data-ttu-id="9b143-111">"Всего >= 500"</span><span class="sxs-lookup"><span data-stu-id="9b143-111">"Total >= 500"</span></span>|  
|<span data-ttu-id="9b143-112">Вычисление</span><span class="sxs-lookup"><span data-stu-id="9b143-112">Computation</span></span>|<span data-ttu-id="9b143-113">"UnitPrice \* Quantity"</span><span class="sxs-lookup"><span data-stu-id="9b143-113">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="9b143-114">Агрегирование</span><span class="sxs-lookup"><span data-stu-id="9b143-114">Aggregation</span></span>|<span data-ttu-id="9b143-115">Sum(Price)</span><span class="sxs-lookup"><span data-stu-id="9b143-115">Sum(Price)</span></span>|  
  
 <span data-ttu-id="9b143-116">Можно задать свойство **Expression** для существующего объекта **DataColumn** или включить свойство в качестве третьего аргумента, передаваемого <xref:System.Data.DataColumn> конструктору, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="9b143-116">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="9b143-117">Выражение может содержать ссылки на другие столбцы выражений, но циклическая ссылка, при которой два выражения ссылаются друг на друга, вызовет исключение.</span><span class="sxs-lookup"><span data-stu-id="9b143-117">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="9b143-118">Правила написания выражений см. в описании <xref:System.Data.DataColumn.Expression%2A> Свойства класса **DataColumn** .</span><span class="sxs-lookup"><span data-stu-id="9b143-118">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b143-119">См. также</span><span class="sxs-lookup"><span data-stu-id="9b143-119">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="9b143-120">Определение схемы таблицы данных</span><span class="sxs-lookup"><span data-stu-id="9b143-120">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="9b143-121">DataTables</span><span class="sxs-lookup"><span data-stu-id="9b143-121">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="9b143-122">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9b143-122">ADO.NET Overview</span></span>](../ado-net-overview.md)
