---
description: 'Дополнительные сведения о коллекциях: коллекции (Visual Basic)'
title: Коллекции
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: 8189eb6d3b95ef81b47f5694092a20a18894103c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100435113"
---
# <a name="collections-visual-basic"></a><span data-ttu-id="f53ad-103">Коллекции (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f53ad-103">Collections (Visual Basic)</span></span>

<span data-ttu-id="f53ad-104">Во многих приложениях требуется создавать группы связанных объектов и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="f53ad-104">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="f53ad-105">Существует два способа группировки объектов: создать массив объектов и создать коллекцию.</span><span class="sxs-lookup"><span data-stu-id="f53ad-105">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="f53ad-106">Массивы удобнее всего использовать для создания фиксированного числа строго типизированных объектов и работы с ними.</span><span class="sxs-lookup"><span data-stu-id="f53ad-106">Arrays are most useful for creating and working with a fixed number of strongly typed objects.</span></span> <span data-ttu-id="f53ad-107">Информацию о массивах см. в разделе [Массивы](../language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f53ad-107">For information about arrays, see [Arrays](../language-features/arrays/index.md).</span></span>

<span data-ttu-id="f53ad-108">Коллекции предоставляют более гибкий способ работы с группами объектов.</span><span class="sxs-lookup"><span data-stu-id="f53ad-108">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="f53ad-109">В отличие от массивов, коллекция, с которой вы работаете, может расти или уменьшаться динамически при необходимости.</span><span class="sxs-lookup"><span data-stu-id="f53ad-109">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="f53ad-110">Некоторые коллекции допускают назначение ключа любому объекту, который добавляется в коллекцию, чтобы в дальнейшем можно было быстро извлечь связанный с ключом объект из коллекции.</span><span class="sxs-lookup"><span data-stu-id="f53ad-110">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="f53ad-111">Коллекция является классом, поэтому необходимо объявить экземпляр класса перед добавлением в коллекцию элементов.</span><span class="sxs-lookup"><span data-stu-id="f53ad-111">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="f53ad-112">Если коллекция содержит элементы только одного типа данных, можно использовать один из классов в пространстве имен <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f53ad-112">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f53ad-113">Универсальная коллекция обеспечивает строгую типизацию, так что в нее нельзя добавить другие типы данных.</span><span class="sxs-lookup"><span data-stu-id="f53ad-113">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="f53ad-114">При извлечении элемента из универсальной коллекции не нужно определять или преобразовывать его тип данных.</span><span class="sxs-lookup"><span data-stu-id="f53ad-114">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="f53ad-115">Для примеров в этом разделе включите операторы [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) для `System.Collections.Generic` `System.Linq` пространств имен и.</span><span class="sxs-lookup"><span data-stu-id="f53ad-115">For the examples in this topic, include [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="f53ad-116">Использование простой коллекции</span><span class="sxs-lookup"><span data-stu-id="f53ad-116">Using a Simple Collection</span></span>

<span data-ttu-id="f53ad-117">В примерах этого раздела используется универсальный класс <xref:System.Collections.Generic.List%601>, который позволяет работать со строго типизированными списками объектов.</span><span class="sxs-lookup"><span data-stu-id="f53ad-117">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="f53ad-118">В следующем примере создается список строк, а затем выполняется итерация по строкам с помощью цикла [For Each... Следующий](../../language-reference/statements/for-each-next-statement.md) оператор.</span><span class="sxs-lookup"><span data-stu-id="f53ad-118">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../language-reference/statements/for-each-next-statement.md) statement.</span></span>

```vb
' Create a list of strings.
Dim salmons As New List(Of String)
salmons.Add("chinook")
salmons.Add("coho")
salmons.Add("pink")
salmons.Add("sockeye")

' Iterate through the list.
For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="f53ad-119">Если содержимое коллекции известно заранее, для ее инициализации можно использовать *инициализатор коллекции*.</span><span class="sxs-lookup"><span data-stu-id="f53ad-119">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="f53ad-120">Дополнительные сведения см. в разделе [Инициализаторы коллекций](../language-features/collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f53ad-120">For more information, see [Collection Initializers](../language-features/collection-initializers/index.md).</span></span>

<span data-ttu-id="f53ad-121">Следующий пример аналогичен предыдущему за исключением того, что для добавления элементов в коллекцию используется инициализатор коллекции.</span><span class="sxs-lookup"><span data-stu-id="f53ad-121">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

```vb
' Create a list of strings by using a
' collection initializer.
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="f53ad-122">Можно использовать [для... Оператор Next](../../language-reference/statements/for-next-statement.md) , а не `For Each` оператор для прохода по коллекции.</span><span class="sxs-lookup"><span data-stu-id="f53ad-122">You can use a [For…Next](../../language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="f53ad-123">Для этого доступ к элементам коллекции осуществляется по позиции индекса.</span><span class="sxs-lookup"><span data-stu-id="f53ad-123">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="f53ad-124">Индекс элементов начинается с 0 и заканчивается числом, равным количеству элементов минус 1.</span><span class="sxs-lookup"><span data-stu-id="f53ad-124">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="f53ad-125">В приведенном ниже примере выполняется перебор элементов коллекции с помощью оператора `For…Next` вместо `For Each`.</span><span class="sxs-lookup"><span data-stu-id="f53ad-125">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>

```vb
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For index = 0 To salmons.Count - 1
    Console.Write(salmons(index) & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="f53ad-126">В приведенном ниже примере элемент удаляется из коллекции путем указания удаляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="f53ad-126">The following example removes an element from the collection by specifying the object to remove.</span></span>

```vb
' Create a list of strings by using a
' collection initializer.
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

' Remove an element in the list by specifying
' the object.
salmons.Remove("coho")

For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook pink sockeye
```

<span data-ttu-id="f53ad-127">В приведенном ниже примере удаляются элементы из универсального списка.</span><span class="sxs-lookup"><span data-stu-id="f53ad-127">The following example removes elements from a generic list.</span></span> <span data-ttu-id="f53ad-128">Вместо `For Each` оператора, a [для... ](../../language-reference/statements/for-next-statement.md) Используется оператор Next, который выполняет итерацию в убывающем порядке.</span><span class="sxs-lookup"><span data-stu-id="f53ad-128">Instead of a `For Each` statement, a [For…Next](../../language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="f53ad-129">Связано это с тем, что в результате работы метода <xref:System.Collections.Generic.List%601.RemoveAt%2A> элементы, следующие за удаленным элементом, получают меньшее значение индекса.</span><span class="sxs-lookup"><span data-stu-id="f53ad-129">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

```vb
Dim numbers As New List(Of Integer) From
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}

' Remove odd numbers.
For index As Integer = numbers.Count - 1 To 0 Step -1
    If numbers(index) Mod 2 = 1 Then
        ' Remove the element by specifying
        ' the zero-based index in the list.
        numbers.RemoveAt(index)
    End If
Next

' Iterate through the list.
' A lambda expression is placed in the ForEach method
' of the List(T) object.
numbers.ForEach(
    Sub(number) Console.Write(number & " "))
' Output: 0 2 4 6 8
```

<span data-ttu-id="f53ad-130">Для типа элементов в <xref:System.Collections.Generic.List%601> можно также определить собственный класс.</span><span class="sxs-lookup"><span data-stu-id="f53ad-130">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="f53ad-131">В приведенном ниже примере класс `Galaxy`, который используется объектом <xref:System.Collections.Generic.List%601>, определен в коде.</span><span class="sxs-lookup"><span data-stu-id="f53ad-131">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

```vb
Private Sub IterateThroughList()
    Dim theGalaxies As New List(Of Galaxy) From
        {
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}
        }

    For Each theGalaxy In theGalaxies
        With theGalaxy
            Console.WriteLine(.Name & "  " & .MegaLightYears)
        End With
    Next

    ' Output:
    '  Tadpole  400
    '  Pinwheel  25
    '  Milky Way  0
    '  Andromeda  3
End Sub

Public Class Galaxy
    Public Property Name As String
    Public Property MegaLightYears As Integer
End Class
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a><span data-ttu-id="f53ad-132">Виды коллекций</span><span class="sxs-lookup"><span data-stu-id="f53ad-132">Kinds of Collections</span></span>

<span data-ttu-id="f53ad-133">Многие типовые коллекции предоставляются платформой .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f53ad-133">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="f53ad-134">Каждый тип коллекции предназначен для определенной цели.</span><span class="sxs-lookup"><span data-stu-id="f53ad-134">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="f53ad-135">В этом разделе описываются следующие часто используемые классы коллекций:</span><span class="sxs-lookup"><span data-stu-id="f53ad-135">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="f53ad-136">Классы <xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="f53ad-136"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="f53ad-137">Классы <xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="f53ad-137"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="f53ad-138">Классы <xref:System.Collections></span><span class="sxs-lookup"><span data-stu-id="f53ad-138"><xref:System.Collections> classes</span></span>

- <span data-ttu-id="f53ad-139">класс `Collection` в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f53ad-139">Visual Basic `Collection` class</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="f53ad-140">Классы System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="f53ad-140">System.Collections.Generic Classes</span></span>

<span data-ttu-id="f53ad-141">Универсальную коллекцию можно создать, используя один из классов в пространстве имен <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="f53ad-141">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="f53ad-142">Универсальная коллекция применяется в том случае, если все элементы в коллекции имеют одинаковый тип данных.</span><span class="sxs-lookup"><span data-stu-id="f53ad-142">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="f53ad-143">Универсальная коллекция обеспечивает строгую типизацию, позволяя добавлять данные только необходимого типа.</span><span class="sxs-lookup"><span data-stu-id="f53ad-143">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="f53ad-144">В таблице ниже перечислены некоторые из часто используемых классов пространства имен <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f53ad-144">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="f53ad-145">Класс</span><span class="sxs-lookup"><span data-stu-id="f53ad-145">Class</span></span>|<span data-ttu-id="f53ad-146">Описание</span><span class="sxs-lookup"><span data-stu-id="f53ad-146">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="f53ad-147">Предоставляет коллекцию пар «ключ-значение», которые упорядочены по ключу.</span><span class="sxs-lookup"><span data-stu-id="f53ad-147">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="f53ad-148">Представляет список объектов, доступных по индексу.</span><span class="sxs-lookup"><span data-stu-id="f53ad-148">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="f53ad-149">Предоставляет методы для поиска по списку, его сортировки и изменения.</span><span class="sxs-lookup"><span data-stu-id="f53ad-149">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="f53ad-150">Представляет коллекцию объектов, которая обслуживается в порядке поступления (FIFO).</span><span class="sxs-lookup"><span data-stu-id="f53ad-150">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="f53ad-151">Представляет коллекцию пар "ключ-значение", упорядоченных по ключу на основе реализации <xref:System.Collections.Generic.IComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="f53ad-151">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="f53ad-152">Представляет коллекцию объектов, которая обслуживается в обратном порядке (LIFO).</span><span class="sxs-lookup"><span data-stu-id="f53ad-152">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="f53ad-153">Дополнительные сведения см. в разделе [Часто используемые типы коллекций](../../../standard/collections/commonly-used-collection-types.md), [Выбор класса коллекции](../../../standard/collections/selecting-a-collection-class.md) и <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f53ad-153">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="f53ad-154">Классы System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="f53ad-154">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="f53ad-155">В .NET Framework 4 или более поздней версии коллекции пространства имен <xref:System.Collections.Concurrent> предоставляют эффективные потокобезопасные операции для доступа к элементам коллекции из нескольких потоков.</span><span class="sxs-lookup"><span data-stu-id="f53ad-155">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="f53ad-156">Классы пространства имен <xref:System.Collections.Concurrent> следует использовать вместо соответствующих типов пространств имен <xref:System.Collections.Generic?displayProperty=nameWithType> и <xref:System.Collections?displayProperty=nameWithType>, если несколько потоков параллельно обращаются к такой коллекции.</span><span class="sxs-lookup"><span data-stu-id="f53ad-156">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="f53ad-157">Дополнительные сведения см. в статьях [Потокобезопасные коллекции](../../../standard/collections/thread-safe/index.md) и <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="f53ad-157">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="f53ad-158">Некоторые из классов, входящих в пространство имен <xref:System.Collections.Concurrent>, — это <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601> и <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="f53ad-158">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="f53ad-159">Классы System.Collections</span><span class="sxs-lookup"><span data-stu-id="f53ad-159">System.Collections Classes</span></span>

<span data-ttu-id="f53ad-160">Классы в пространстве имен <xref:System.Collections?displayProperty=nameWithType> хранят элементы не в виде конкретно типизированных объектов, а как объекты типа `Object`.</span><span class="sxs-lookup"><span data-stu-id="f53ad-160">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="f53ad-161">Везде, где это возможно, следует использовать универсальные коллекции пространства имен <xref:System.Collections.Generic?displayProperty=nameWithType> или пространства имен <xref:System.Collections.Concurrent> вместо устаревших типов пространства имен `System.Collections`.</span><span class="sxs-lookup"><span data-stu-id="f53ad-161">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="f53ad-162">В следующей таблице перечислены некоторые из часто используемых классов пространства имен `System.Collections`:</span><span class="sxs-lookup"><span data-stu-id="f53ad-162">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="f53ad-163">Класс</span><span class="sxs-lookup"><span data-stu-id="f53ad-163">Class</span></span>|<span data-ttu-id="f53ad-164">Описание</span><span class="sxs-lookup"><span data-stu-id="f53ad-164">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="f53ad-165">Представляет массив объектов, размер которого динамически увеличивается по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="f53ad-165">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="f53ad-166">Представляет коллекцию пар «ключ-значение», которые упорядочены по хэш-коду ключа.</span><span class="sxs-lookup"><span data-stu-id="f53ad-166">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="f53ad-167">Представляет коллекцию объектов, которая обслуживается в порядке поступления (FIFO).</span><span class="sxs-lookup"><span data-stu-id="f53ad-167">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="f53ad-168">Представляет коллекцию объектов, которая обслуживается в обратном порядке (LIFO).</span><span class="sxs-lookup"><span data-stu-id="f53ad-168">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="f53ad-169">Пространство имен <xref:System.Collections.Specialized> предоставляет специализированные и строго типизированные классы коллекций, такие как коллекции строк, связанные списки и гибридные словари.</span><span class="sxs-lookup"><span data-stu-id="f53ad-169">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_VisualBasic"></a>

### <a name="visual-basic-collection-class"></a><span data-ttu-id="f53ad-170">Класс Collection в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f53ad-170">Visual Basic Collection Class</span></span>

<span data-ttu-id="f53ad-171">Класс <xref:Microsoft.VisualBasic.Collection> в Visual Basic можно использовать для доступа к элементу коллекции по числовому индексу или ключу `String`.</span><span class="sxs-lookup"><span data-stu-id="f53ad-171">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="f53ad-172">Элементы можно добавлять в объект коллекции с указанием или без указания ключа.</span><span class="sxs-lookup"><span data-stu-id="f53ad-172">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="f53ad-173">Если добавить объект без ключа, необходимо использовать его числовой индекс для доступа к нему.</span><span class="sxs-lookup"><span data-stu-id="f53ad-173">If you add an item without a key, you must use its numeric index to access it.</span></span>

<span data-ttu-id="f53ad-174">Класс `Collection` в Visual Basic хранит все свои элементы как тип `Object`, поэтому можно добавить элемент любого типа данных.</span><span class="sxs-lookup"><span data-stu-id="f53ad-174">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="f53ad-175">Нет никакой защиты от добавления неподходящих типов данных.</span><span class="sxs-lookup"><span data-stu-id="f53ad-175">There is no safeguard against inappropriate data types being added.</span></span>

<span data-ttu-id="f53ad-176">При использовании класса `Collection` в Visual Basic первый элемент в коллекции имеет индекс 1.</span><span class="sxs-lookup"><span data-stu-id="f53ad-176">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="f53ad-177">Этим он отличается от классов коллекций платформы .NET Framework, для которых начальный индекс равен 0.</span><span class="sxs-lookup"><span data-stu-id="f53ad-177">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>

<span data-ttu-id="f53ad-178">Везде, где это возможно, следует использовать универсальные коллекции в пространстве имен <xref:System.Collections.Generic?displayProperty=nameWithType> или пространстве имен <xref:System.Collections.Concurrent> вместо класса `Collection` в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f53ad-178">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>

<span data-ttu-id="f53ad-179">Для получения дополнительной информации см. <xref:Microsoft.VisualBasic.Collection>.</span><span class="sxs-lookup"><span data-stu-id="f53ad-179">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="f53ad-180">Реализация коллекции пар «ключ-значение»</span><span class="sxs-lookup"><span data-stu-id="f53ad-180">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="f53ad-181">Универсальная коллекция <xref:System.Collections.Generic.Dictionary%602> позволяет получить доступ к элементам коллекции с помощью ключа каждого элемента.</span><span class="sxs-lookup"><span data-stu-id="f53ad-181">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="f53ad-182">Каждый элемент, добавляемый в словарь, состоит из значения и связанного с ним ключа.</span><span class="sxs-lookup"><span data-stu-id="f53ad-182">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="f53ad-183">Извлечение значения по его ключу происходит быстро, так как класс `Dictionary` реализован как хэш-таблица.</span><span class="sxs-lookup"><span data-stu-id="f53ad-183">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="f53ad-184">В приведенном ниже примере создается коллекция `Dictionary` и выполняется перебор словаря с помощью оператора `For Each`.</span><span class="sxs-lookup"><span data-stu-id="f53ad-184">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>

```vb
Private Sub IterateThroughDictionary()
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    For Each kvp As KeyValuePair(Of String, Element) In elements
        Dim theElement As Element = kvp.Value

        Console.WriteLine("key: " & kvp.Key)
        With theElement
            Console.WriteLine("values: " & .Symbol & " " &
                .Name & " " & .AtomicNumber)
        End With
    Next
End Sub

Private Function BuildDictionary() As Dictionary(Of String, Element)
    Dim elements As New Dictionary(Of String, Element)

    AddToDictionary(elements, "K", "Potassium", 19)
    AddToDictionary(elements, "Ca", "Calcium", 20)
    AddToDictionary(elements, "Sc", "Scandium", 21)
    AddToDictionary(elements, "Ti", "Titanium", 22)

    Return elements
End Function

Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)
    Dim theElement As New Element

    theElement.Symbol = symbol
    theElement.Name = name
    theElement.AtomicNumber = atomicNumber

    elements.Add(Key:=theElement.Symbol, value:=theElement)
End Sub

Public Class Element
    Public Property Symbol As String
    Public Property Name As String
    Public Property AtomicNumber As Integer
End Class
```

<span data-ttu-id="f53ad-185">Чтобы вместо этого использовать инициализатор коллекции для создания коллекции `Dictionary`, можно заменить методы `BuildDictionary` и `AddToDictionary` приведенным ниже методом.</span><span class="sxs-lookup"><span data-stu-id="f53ad-185">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

```vb
Private Function BuildDictionary2() As Dictionary(Of String, Element)
    Return New Dictionary(Of String, Element) From
        {
            {"K", New Element With
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},
            {"Ca", New Element With
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},
            {"Sc", New Element With
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},
            {"Ti", New Element With
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}
        }
End Function
```

<span data-ttu-id="f53ad-186">В приведенном ниже примере используется метод <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> и свойство <xref:System.Collections.Generic.Dictionary%602.Item%2A>`Dictionary` для быстрого поиска элемента по ключу.</span><span class="sxs-lookup"><span data-stu-id="f53ad-186">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="f53ad-187">`Item`Свойство позволяет получить доступ к элементу в коллекции с `elements` помощью `elements(symbol)` кода в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f53ad-187">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>

```vb
Private Sub FindInDictionary(ByVal symbol As String)
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    If elements.ContainsKey(symbol) = False Then
        Console.WriteLine(symbol & " not found")
    Else
        Dim theElement = elements(symbol)
        Console.WriteLine("found: " & theElement.Name)
    End If
End Sub
```

<span data-ttu-id="f53ad-188">В приведенном ниже примере вместо этого используется метод <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> для быстрого поиска элемента по ключу.</span><span class="sxs-lookup"><span data-stu-id="f53ad-188">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

```vb
Private Sub FindInDictionary2(ByVal symbol As String)
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    Dim theElement As Element = Nothing
    If elements.TryGetValue(symbol, theElement) = False Then
        Console.WriteLine(symbol & " not found")
    Else
        Console.WriteLine("found: " & theElement.Name)
    End If
End Sub
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="f53ad-189">Использование LINQ для доступа к коллекции</span><span class="sxs-lookup"><span data-stu-id="f53ad-189">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="f53ad-190">Для доступа к коллекции можно использовать язык LINQ.</span><span class="sxs-lookup"><span data-stu-id="f53ad-190">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="f53ad-191">Запросы LINQ обеспечивают возможности фильтрации, упорядочения и группировки.</span><span class="sxs-lookup"><span data-stu-id="f53ad-191">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="f53ad-192">Дополнительные сведения см. [в разделе Начало работы с LINQ в Visual Basic](linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="f53ad-192">For more information, see [Getting Started with LINQ in Visual Basic](linq/getting-started-with-linq.md).</span></span>

<span data-ttu-id="f53ad-193">В приведенном ниже примере выполняется запрос LINQ применительно к универсальной коллекции `List`.</span><span class="sxs-lookup"><span data-stu-id="f53ad-193">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="f53ad-194">Запрос LINQ возвращает другую коллекцию, содержащую результаты.</span><span class="sxs-lookup"><span data-stu-id="f53ad-194">The LINQ query returns a different collection that contains the results.</span></span>

```vb
Private Sub ShowLINQ()
    Dim elements As List(Of Element) = BuildList()

    ' LINQ Query.
    Dim subset = From theElement In elements
                  Where theElement.AtomicNumber < 22
                  Order By theElement.Name

    For Each theElement In subset
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)
    Next

    ' Output:
    '  Calcium 20
    '  Potassium 19
    '  Scandium 21
End Sub

Private Function BuildList() As List(Of Element)
    Return New List(Of Element) From
        {
            {New Element With
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},
            {New Element With
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},
            {New Element With
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},
            {New Element With
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}
        }
End Function

Public Class Element
    Public Property Symbol As String
    Public Property Name As String
    Public Property AtomicNumber As Integer
End Class
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a><span data-ttu-id="f53ad-195">Сортировка коллекции</span><span class="sxs-lookup"><span data-stu-id="f53ad-195">Sorting a Collection</span></span>

<span data-ttu-id="f53ad-196">Приведенный ниже пример демонстрирует процедуру сортировки коллекции.</span><span class="sxs-lookup"><span data-stu-id="f53ad-196">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="f53ad-197">В примере сортируются экземпляры класса `Car`, которые хранятся в <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="f53ad-197">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="f53ad-198">Класс `Car` реализует интерфейс <xref:System.IComparable%601>, который требует реализации метода <xref:System.IComparable%601.CompareTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="f53ad-198">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="f53ad-199">Каждый вызов метода <xref:System.IComparable%601.CompareTo%2A> выполняет одно сравнение, используемое для сортировки.</span><span class="sxs-lookup"><span data-stu-id="f53ad-199">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="f53ad-200">Написанный пользователем код в методе `CompareTo` возвращает значение для каждого сравнения текущего объекта с другим объектом.</span><span class="sxs-lookup"><span data-stu-id="f53ad-200">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="f53ad-201">Возвращаемое значение меньше нуля, если текущий объект меньше другого объекта, больше нуля, если текущий объект больше другого объекта, и равняется нулю, если объекты равны.</span><span class="sxs-lookup"><span data-stu-id="f53ad-201">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="f53ad-202">Это позволяет определить в коде условия для отношения «больше», «меньше» и «равно».</span><span class="sxs-lookup"><span data-stu-id="f53ad-202">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="f53ad-203">В методе `ListCars` оператор `cars.Sort()` сортирует список.</span><span class="sxs-lookup"><span data-stu-id="f53ad-203">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="f53ad-204">Этот вызов метода <xref:System.Collections.Generic.List%601.Sort%2A><xref:System.Collections.Generic.List%601> приводит к тому, что метод `CompareTo` вызывается автоматически для объектов `Car` в `List`.</span><span class="sxs-lookup"><span data-stu-id="f53ad-204">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

```vb
Public Sub ListCars()

    ' Create some new cars.
    Dim cars As New List(Of Car) From
    {
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}
    }

    ' Sort the cars by color alphabetically, and then by speed
    ' in descending order.
    cars.Sort()

    ' View all of the cars.
    For Each thisCar As Car In cars
        Console.Write(thisCar.Color.PadRight(5) & " ")
        Console.Write(thisCar.Speed.ToString & " ")
        Console.Write(thisCar.Name)
        Console.WriteLine()
    Next

    ' Output:
    '  blue  50 car4
    '  blue  30 car5
    '  blue  20 car1
    '  green 50 car7
    '  green 10 car3
    '  red   60 car6
    '  red   50 car2
End Sub

Public Class Car
    Implements IComparable(Of Car)

    Public Property Name As String
    Public Property Speed As Integer
    Public Property Color As String

    Public Function CompareTo(ByVal other As Car) As Integer _
        Implements System.IComparable(Of Car).CompareTo
        ' A call to this method makes a single comparison that is
        ' used for sorting.

        ' Determine the relative order of the objects being compared.
        ' Sort by color alphabetically, and then by speed in
        ' descending order.

        ' Compare the colors.
        Dim compare As Integer
        compare = String.Compare(Me.Color, other.Color, True)

        ' If the colors are the same, compare the speeds.
        If compare = 0 Then
            compare = Me.Speed.CompareTo(other.Speed)

            ' Use descending order for speed.
            compare = -compare
        End If

        Return compare
    End Function
End Class
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a><span data-ttu-id="f53ad-205">Определение настраиваемой коллекции</span><span class="sxs-lookup"><span data-stu-id="f53ad-205">Defining a Custom Collection</span></span>

<span data-ttu-id="f53ad-206">Вы можете определить коллекцию, реализовав интерфейс <xref:System.Collections.Generic.IEnumerable%601> или <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="f53ad-206">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="f53ad-207">Дополнительные сведения см. [в разделе Перечисление коллекции](/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f53ad-207">For additional information, see [Enumerating a Collection](/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).</span></span>

<span data-ttu-id="f53ad-208">Хотя можно определить настраиваемую коллекцию, обычно лучше использовать коллекции, входящие в .NET Framework, которые описаны в подразделе [Виды коллекций](#kinds-of-collections) ранее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="f53ad-208">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#kinds-of-collections) earlier in this topic.</span></span>

<span data-ttu-id="f53ad-209">В приведенном ниже примере определяется настраиваемый класс коллекции с именем `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="f53ad-209">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="f53ad-210">Этот класс реализует интерфейс <xref:System.Collections.IEnumerable>, который требует реализации метода <xref:System.Collections.IEnumerable.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="f53ad-210">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="f53ad-211">Метод `GetEnumerator` возвращает экземпляр класса `ColorEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="f53ad-211">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="f53ad-212">Класс `ColorEnumerator` реализует интерфейс <xref:System.Collections.IEnumerator>, который требует реализации свойства <xref:System.Collections.IEnumerator.Current%2A>, метода <xref:System.Collections.IEnumerator.MoveNext%2A> и метода <xref:System.Collections.IEnumerator.Reset%2A>.</span><span class="sxs-lookup"><span data-stu-id="f53ad-212">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

```vb
Public Sub ListColors()
    Dim colors As New AllColors()

    For Each theColor As Color In colors
        Console.Write(theColor.Name & " ")
    Next
    Console.WriteLine()
    ' Output: red blue green
End Sub

' Collection class.
Public Class AllColors
    Implements System.Collections.IEnumerable

    Private _colors() As Color =
    {
        New Color With {.Name = "red"},
        New Color With {.Name = "blue"},
        New Color With {.Name = "green"}
    }

    Public Function GetEnumerator() As System.Collections.IEnumerator _
        Implements System.Collections.IEnumerable.GetEnumerator

        Return New ColorEnumerator(_colors)

        ' Instead of creating a custom enumerator, you could
        ' use the GetEnumerator of the array.
        'Return _colors.GetEnumerator
    End Function

    ' Custom enumerator.
    Private Class ColorEnumerator
        Implements System.Collections.IEnumerator

        Private _colors() As Color
        Private _position As Integer = -1

        Public Sub New(ByVal colors() As Color)
            _colors = colors
        End Sub

        Public ReadOnly Property Current() As Object _
            Implements System.Collections.IEnumerator.Current
            Get
                Return _colors(_position)
            End Get
        End Property

        Public Function MoveNext() As Boolean _
            Implements System.Collections.IEnumerator.MoveNext
            _position += 1
            Return (_position < _colors.Length)
        End Function

        Public Sub Reset() Implements System.Collections.IEnumerator.Reset
            _position = -1
        End Sub
    End Class
End Class

' Element class.
Public Class Color
    Public Property Name As String
End Class
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a><span data-ttu-id="f53ad-213">Iterators</span><span class="sxs-lookup"><span data-stu-id="f53ad-213">Iterators</span></span>

<span data-ttu-id="f53ad-214">*Итератор* используется для выполнения настраиваемого перебора коллекции.</span><span class="sxs-lookup"><span data-stu-id="f53ad-214">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="f53ad-215">Итератор может быть методом или методом доступа `get`.</span><span class="sxs-lookup"><span data-stu-id="f53ad-215">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="f53ad-216">Итератор использует оператор [yield](../../language-reference/statements/yield-statement.md) для возвращения каждого элемента коллекции по одному за раз.</span><span class="sxs-lookup"><span data-stu-id="f53ad-216">An iterator uses a [Yield](../../language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="f53ad-217">Для вызова итератора используется оператор [For Each... Следующий](../../language-reference/statements/for-each-next-statement.md) оператор.</span><span class="sxs-lookup"><span data-stu-id="f53ad-217">You call an iterator by using a [For Each…Next](../../language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="f53ad-218">Каждая итерация цикла `For Each` вызывает итератор.</span><span class="sxs-lookup"><span data-stu-id="f53ad-218">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="f53ad-219">При достижении оператора `Yield` в итераторе возвращается выражение, и текущее расположение в коде сохраняется.</span><span class="sxs-lookup"><span data-stu-id="f53ad-219">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="f53ad-220">При следующем вызове итератора выполнение возобновляется с этого места.</span><span class="sxs-lookup"><span data-stu-id="f53ad-220">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="f53ad-221">Дополнительные сведения см. в разделе [итераторы (Visual Basic)](iterators.md).</span><span class="sxs-lookup"><span data-stu-id="f53ad-221">For more information, see [Iterators (Visual Basic)](iterators.md).</span></span>

<span data-ttu-id="f53ad-222">В приведенном ниже примере используется метод-итератор.</span><span class="sxs-lookup"><span data-stu-id="f53ad-222">The following example uses an iterator method.</span></span> <span data-ttu-id="f53ad-223">Метод итератора содержит `Yield` оператор, который находится внутри блока [for... Следующий](../../language-reference/statements/for-next-statement.md) цикл.</span><span class="sxs-lookup"><span data-stu-id="f53ad-223">The iterator method has a `Yield` statement that is inside a [For…Next](../../language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="f53ad-224">В методе `ListEvenNumbers` каждая итерация тела оператора `For Each` создает вызов метода-итератора, который переходит к следующему оператору `Yield`.</span><span class="sxs-lookup"><span data-stu-id="f53ad-224">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>

```vb
Public Sub ListEvenNumbers()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    Console.WriteLine()
    ' Output: 6 8 10 12 14 16 18
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As IEnumerable(Of Integer)

' Yield even numbers in the range.
    For number = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="see-also"></a><span data-ttu-id="f53ad-225">См. также</span><span class="sxs-lookup"><span data-stu-id="f53ad-225">See also</span></span>

- [<span data-ttu-id="f53ad-226">Инициализаторы коллекций</span><span class="sxs-lookup"><span data-stu-id="f53ad-226">Collection Initializers</span></span>](../language-features/collection-initializers/index.md)
- [<span data-ttu-id="f53ad-227">Основные понятия программирования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f53ad-227">Programming Concepts (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="f53ad-228">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="f53ad-228">Option Strict Statement</span></span>](../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="f53ad-229">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f53ad-229">LINQ to Objects (Visual Basic)</span></span>](linq/linq-to-objects.md)
- [<span data-ttu-id="f53ad-230">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f53ad-230">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/introduction-to-plinq.md)
- [<span data-ttu-id="f53ad-231">Коллекции и структуры данных</span><span class="sxs-lookup"><span data-stu-id="f53ad-231">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="f53ad-232">Выбор класса коллекции</span><span class="sxs-lookup"><span data-stu-id="f53ad-232">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="f53ad-233">Сравнение и сортировка в коллекциях</span><span class="sxs-lookup"><span data-stu-id="f53ad-233">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="f53ad-234">Когда следует использовать универсальные коллекции</span><span class="sxs-lookup"><span data-stu-id="f53ad-234">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
