---
description: Дополнительные сведения см. в статье вариативность в универсальных интерфейсах (Visual Basic)
title: Вариативность в универсальных интерфейсах
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: 42257f80cb929756583b1e488cd315450b9db35e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100469842"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="6e175-103">Вариативность в универсальных интерфейсах (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e175-103">Variance in Generic Interfaces (Visual Basic)</span></span>

<span data-ttu-id="6e175-104">В платформе .NET Framework 4 появилась поддержка вариативности для нескольких существующих универсальных интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="6e175-104">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="6e175-105">Поддержка вариативности позволяет выполнять неявное преобразование классов, реализующих эти интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="6e175-105">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="6e175-106">Сейчас вариативными являются следующие интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="6e175-106">The following interfaces are now variant:</span></span>

- <span data-ttu-id="6e175-107"><xref:System.Collections.Generic.IEnumerable%601> (T является ковариантным)</span><span class="sxs-lookup"><span data-stu-id="6e175-107"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="6e175-108"><xref:System.Collections.Generic.IEnumerator%601> (T является ковариантным)</span><span class="sxs-lookup"><span data-stu-id="6e175-108"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="6e175-109"><xref:System.Linq.IQueryable%601> (T является ковариантным)</span><span class="sxs-lookup"><span data-stu-id="6e175-109"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="6e175-110"><xref:System.Linq.IGrouping%602> (`TKey` и `TElement` являются ковариантными)</span><span class="sxs-lookup"><span data-stu-id="6e175-110"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="6e175-111"><xref:System.Collections.Generic.IComparer%601> (T является контравариантным)</span><span class="sxs-lookup"><span data-stu-id="6e175-111"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="6e175-112"><xref:System.Collections.Generic.IEqualityComparer%601> (T является контравариантным)</span><span class="sxs-lookup"><span data-stu-id="6e175-112"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="6e175-113"><xref:System.IComparable%601> (T является контравариантным)</span><span class="sxs-lookup"><span data-stu-id="6e175-113"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="6e175-114">Ковариация позволяет методу иметь тип возвращаемого значения, степень наследования которого больше, чем указано в параметре универсального типа интерфейса.</span><span class="sxs-lookup"><span data-stu-id="6e175-114">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="6e175-115">Чтобы продемонстрировать функцию ковариации, рассмотрим следующие универсальные интерфейсы: `IEnumerable(Of Object)` и `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="6e175-115">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="6e175-116">Интерфейс `IEnumerable(Of String)` не наследует интерфейс `IEnumerable(Of Object)`.</span><span class="sxs-lookup"><span data-stu-id="6e175-116">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="6e175-117">При этом тип `String` наследует тип `Object`, и в некоторых случаях может потребоваться назначить объекты этих интерфейсов друг другу.</span><span class="sxs-lookup"><span data-stu-id="6e175-117">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="6e175-118">Это показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="6e175-118">This is shown in the following code example.</span></span>

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

<span data-ttu-id="6e175-119">В более ранних версиях платформа .NET Framework этот код вызывает ошибку компиляции в Visual Basic с `Option Strict On` .</span><span class="sxs-lookup"><span data-stu-id="6e175-119">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="6e175-120">Но теперь можно использовать `strings` вместо `objects`, как показано в предыдущем примере, поскольку интерфейс <xref:System.Collections.Generic.IEnumerable%601> является ковариантным.</span><span class="sxs-lookup"><span data-stu-id="6e175-120">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="6e175-121">Контравариантность позволяет методу иметь типы аргументов, степень наследования которых меньше, чем указано в параметре универсального типа интерфейса.</span><span class="sxs-lookup"><span data-stu-id="6e175-121">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="6e175-122">Чтобы продемонстрировать функцию контравариантности, предположим, что создан класса `BaseComparer` для сравнения экземпляров класса `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="6e175-122">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="6e175-123">Класс `BaseComparer` реализует интерфейс `IEqualityComparer(Of BaseClass)`.</span><span class="sxs-lookup"><span data-stu-id="6e175-123">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="6e175-124">Поскольку теперь интерфейс <xref:System.Collections.Generic.IEqualityComparer%601> является контравариантным, для сравнения экземпляров классов, наследующих класс `BaseClass`, можно использовать класс `BaseComparer`.</span><span class="sxs-lookup"><span data-stu-id="6e175-124">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="6e175-125">Это показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="6e175-125">This is shown in the following code example.</span></span>

```vb
' Simple hierarchy of classes.
Class BaseClass
End Class

Class DerivedClass
    Inherits BaseClass
End Class

' Comparer class.
Class BaseComparer
    Implements IEqualityComparer(Of BaseClass)

    Public Function Equals1(ByVal x As BaseClass,
                            ByVal y As BaseClass) As Boolean _
                            Implements IEqualityComparer(Of BaseClass).Equals
        Return (x.Equals(y))
    End Function

    Public Function GetHashCode1(ByVal obj As BaseClass) As Integer _
        Implements IEqualityComparer(Of BaseClass).GetHashCode
        Return obj.GetHashCode
    End Function
End Class
Sub Test()
    Dim baseComparer As IEqualityComparer(Of BaseClass) = New BaseComparer
    ' Implicit conversion of IEqualityComparer(Of BaseClass) to
    ' IEqualityComparer(Of DerivedClass).
    Dim childComparer As IEqualityComparer(Of DerivedClass) = baseComparer
End Sub
```

<span data-ttu-id="6e175-126">Дополнительные примеры см. [в разделе Использование вариативности в интерфейсах для универсальных коллекций (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="6e175-126">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="6e175-127">Вариативность в универсальных интерфейсах поддерживается только для ссылочных типов.</span><span class="sxs-lookup"><span data-stu-id="6e175-127">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="6e175-128">Типы значений не поддерживают вариативность.</span><span class="sxs-lookup"><span data-stu-id="6e175-128">Value types do not support variance.</span></span> <span data-ttu-id="6e175-129">Например, `IEnumerable(Of Integer)` нельзя неявно преобразовать в `IEnumerable(Of Object)`, так как типом значения является integer.</span><span class="sxs-lookup"><span data-stu-id="6e175-129">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>

```vb
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)
' The following statement generates a compiler error
' with Option Strict On, because Integer is a value type.
' Dim objects As IEnumerable(Of Object) = integers
```

<span data-ttu-id="6e175-130">Кроме того, важно помнить, что классы, которые реализуют вариативные интерфейсы, сами являются инвариантными.</span><span class="sxs-lookup"><span data-stu-id="6e175-130">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="6e175-131">Например, несмотря на то, что <xref:System.Collections.Generic.List%601> реализует ковариантный интерфейс <xref:System.Collections.Generic.IEnumerable%601>, неявно преобразовать `List(Of Object)` в `List(Of String)` нельзя.</span><span class="sxs-lookup"><span data-stu-id="6e175-131">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="6e175-132">Это показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="6e175-132">This is illustrated in the following code example.</span></span>

```vb
' The following statement generates a compiler error
' because classes are invariant.
' Dim list As List(Of Object) = New List(Of String)

' You can use the interface object instead.
Dim listObjects As IEnumerable(Of Object) = New List(Of String)
```

## <a name="see-also"></a><span data-ttu-id="6e175-133">См. также</span><span class="sxs-lookup"><span data-stu-id="6e175-133">See also</span></span>

- [<span data-ttu-id="6e175-134">Использование вариативности в интерфейсах для универсальных коллекций (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e175-134">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="6e175-135">Создание вариативных универсальных интерфейсов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e175-135">Creating Variant Generic Interfaces (Visual Basic)</span></span>](creating-variant-generic-interfaces.md)
- [<span data-ttu-id="6e175-136">Универсальные интерфейсы</span><span class="sxs-lookup"><span data-stu-id="6e175-136">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="6e175-137">Вариативность в делегатах (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e175-137">Variance in Delegates (Visual Basic)</span></span>](variance-in-delegates.md)
