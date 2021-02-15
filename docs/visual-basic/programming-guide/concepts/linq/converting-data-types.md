---
description: 'Дополнительные сведения: преобразование типов данных (Visual Basic)'
title: Преобразование типов данных
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 7650f5d5d6f727b7815b9dd2de8a565e27fa18d9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428718"
---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="ca08c-103">Преобразование типов данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca08c-103">Converting Data Types (Visual Basic)</span></span>

<span data-ttu-id="ca08c-104">Методы преобразования изменяют тип входных объектов.</span><span class="sxs-lookup"><span data-stu-id="ca08c-104">Conversion methods change the type of input objects.</span></span>

 <span data-ttu-id="ca08c-105">Операции преобразования в запросах LINQ удобны в различных ситуациях.</span><span class="sxs-lookup"><span data-stu-id="ca08c-105">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="ca08c-106">Ниже приводятся некоторые примеры:</span><span class="sxs-lookup"><span data-stu-id="ca08c-106">The following are some examples:</span></span>

- <span data-ttu-id="ca08c-107">Метод <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> можно использовать, чтобы скрыть настраиваемую реализацию типа стандартного оператора запроса.</span><span class="sxs-lookup"><span data-stu-id="ca08c-107">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> method can be used to hide a type's custom implementation of a standard query operator.</span></span>

- <span data-ttu-id="ca08c-108">Метод <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> позволяет использовать непараметризованные коллекции для запросов LINQ.</span><span class="sxs-lookup"><span data-stu-id="ca08c-108">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> method can be used to enable non-parameterized collections for LINQ querying.</span></span>

- <span data-ttu-id="ca08c-109">Методы <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> и <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> можно использовать для принудительного немедленного выполнения запроса, не дожидаясь, пока этот запрос будет перечислен.</span><span class="sxs-lookup"><span data-stu-id="ca08c-109">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>

## <a name="methods"></a><span data-ttu-id="ca08c-110">Методы</span><span class="sxs-lookup"><span data-stu-id="ca08c-110">Methods</span></span>

<span data-ttu-id="ca08c-111">В следующей таблице перечислены методы стандартных операторов запросов, выполняющие преобразование типов данных.</span><span class="sxs-lookup"><span data-stu-id="ca08c-111">The following table lists the standard query operator methods that perform data-type conversions.</span></span>

<span data-ttu-id="ca08c-112">Методы преобразования в этой таблице, имена которых начинаются с "As", изменяют статический тип исходной коллекции, но не выполняют перечисление.</span><span class="sxs-lookup"><span data-stu-id="ca08c-112">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="ca08c-113">Методы, имена которых начинаются с "To", перечисляют исходную коллекцию и помещают элементы в соответствующий тип коллекции.</span><span class="sxs-lookup"><span data-stu-id="ca08c-113">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>

|<span data-ttu-id="ca08c-114">Имя метода</span><span class="sxs-lookup"><span data-stu-id="ca08c-114">Method Name</span></span>|<span data-ttu-id="ca08c-115">Описание</span><span class="sxs-lookup"><span data-stu-id="ca08c-115">Description</span></span>|<span data-ttu-id="ca08c-116">Синтаксис выражения запроса Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca08c-116">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="ca08c-117">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="ca08c-117">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="ca08c-118">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="ca08c-118">AsEnumerable</span></span>|<span data-ttu-id="ca08c-119">Возвращает входное значение, типизированное как <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="ca08c-119">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="ca08c-120">Не применяется</span><span class="sxs-lookup"><span data-stu-id="ca08c-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ca08c-121">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="ca08c-121">AsQueryable</span></span>|<span data-ttu-id="ca08c-122">Преобразует <xref:System.Collections.IEnumerable> (универсальный шаблон) в <xref:System.Linq.IQueryable> (универсальный шаблон).</span><span class="sxs-lookup"><span data-stu-id="ca08c-122">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="ca08c-123">Не применяется</span><span class="sxs-lookup"><span data-stu-id="ca08c-123">Not applicable.</span></span>|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ca08c-124">Cast</span><span class="sxs-lookup"><span data-stu-id="ca08c-124">Cast</span></span>|<span data-ttu-id="ca08c-125">Приводит элементы коллекции к указанному типу.</span><span class="sxs-lookup"><span data-stu-id="ca08c-125">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ca08c-126">OfType</span><span class="sxs-lookup"><span data-stu-id="ca08c-126">OfType</span></span>|<span data-ttu-id="ca08c-127">Фильтрует значения в зависимости от возможности их приведения к указанному типу.</span><span class="sxs-lookup"><span data-stu-id="ca08c-127">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="ca08c-128">Не применяется</span><span class="sxs-lookup"><span data-stu-id="ca08c-128">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ca08c-129">ToArray</span><span class="sxs-lookup"><span data-stu-id="ca08c-129">ToArray</span></span>|<span data-ttu-id="ca08c-130">Преобразует коллекцию в массив.</span><span class="sxs-lookup"><span data-stu-id="ca08c-130">Converts a collection to an array.</span></span> <span data-ttu-id="ca08c-131">Этот метод принудительно выполняет запрос.</span><span class="sxs-lookup"><span data-stu-id="ca08c-131">This method forces query execution.</span></span>|<span data-ttu-id="ca08c-132">Не применяется</span><span class="sxs-lookup"><span data-stu-id="ca08c-132">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ca08c-133">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="ca08c-133">ToDictionary</span></span>|<span data-ttu-id="ca08c-134">Помещает элементы в <xref:System.Collections.Generic.Dictionary%602> в зависимости от функции выбора ключа.</span><span class="sxs-lookup"><span data-stu-id="ca08c-134">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="ca08c-135">Этот метод принудительно выполняет запрос.</span><span class="sxs-lookup"><span data-stu-id="ca08c-135">This method forces query execution.</span></span>|<span data-ttu-id="ca08c-136">Не применяется</span><span class="sxs-lookup"><span data-stu-id="ca08c-136">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ca08c-137">ToList</span><span class="sxs-lookup"><span data-stu-id="ca08c-137">ToList</span></span>|<span data-ttu-id="ca08c-138">Преобразует коллекцию в <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="ca08c-138">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="ca08c-139">Этот метод принудительно выполняет запрос.</span><span class="sxs-lookup"><span data-stu-id="ca08c-139">This method forces query execution.</span></span>|<span data-ttu-id="ca08c-140">Не применяется</span><span class="sxs-lookup"><span data-stu-id="ca08c-140">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ca08c-141">ToLookup</span><span class="sxs-lookup"><span data-stu-id="ca08c-141">ToLookup</span></span>|<span data-ttu-id="ca08c-142">Помещает элементы в <xref:System.Linq.Lookup%602> (словарь "один ко многим") в зависимости от функции выбора ключа.</span><span class="sxs-lookup"><span data-stu-id="ca08c-142">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="ca08c-143">Этот метод принудительно выполняет запрос.</span><span class="sxs-lookup"><span data-stu-id="ca08c-143">This method forces query execution.</span></span>|<span data-ttu-id="ca08c-144">Не применяется</span><span class="sxs-lookup"><span data-stu-id="ca08c-144">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="ca08c-145">Пример синтаксиса выражения запроса</span><span class="sxs-lookup"><span data-stu-id="ca08c-145">Query Expression Syntax Example</span></span>

<span data-ttu-id="ca08c-146">В следующем примере кода предложение используется `From As` для приведения типа к подтипу перед доступом к элементу, доступному только для подтипа.</span><span class="sxs-lookup"><span data-stu-id="ca08c-146">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>

```vb
Class Plant
    Public Property Name As String
End Class

Class CarnivorousPlant
    Inherits Plant
    Public Property TrapType As String
End Class

Sub Cast()

    Dim plants() As Plant = {
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}

    Dim query = From plant As CarnivorousPlant In plants
                Where plant.TrapType = "Snap Trap"
                Select plant

    Dim sb As New System.Text.StringBuilder()
    For Each plant In query
        sb.AppendLine(plant.Name)
    Next

    ' Display the results.
    MsgBox(sb.ToString())

    ' This code produces the following output:

    ' Venus Fly Trap
    ' Waterwheel Plant

End Sub
```

## <a name="see-also"></a><span data-ttu-id="ca08c-147">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ca08c-147">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ca08c-148">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca08c-148">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="ca08c-149">Предложение From</span><span class="sxs-lookup"><span data-stu-id="ca08c-149">From Clause</span></span>](../../../language-reference/queries/from-clause.md)
- [<span data-ttu-id="ca08c-150">Как выполнить запрос к ArrayList с помощью LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca08c-150">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](how-to-query-an-arraylist-with-linq.md)
