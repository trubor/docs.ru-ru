---
description: Дополнительные сведения о итераторах (Visual Basic)
title: Iterators
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: 9d12bd436a976e3f84dbd063ca746fc7e3b17bfb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462156"
---
# <a name="iterators-visual-basic"></a><span data-ttu-id="4d72d-103">Итераторы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d72d-103">Iterators (Visual Basic)</span></span>

<span data-ttu-id="4d72d-104">*Итератор* можно использовать для прохода по коллекции, такой как список или массив.</span><span class="sxs-lookup"><span data-stu-id="4d72d-104">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="4d72d-105">Метод итератора или метод доступа `get` выполняет настраиваемую итерацию по коллекции.</span><span class="sxs-lookup"><span data-stu-id="4d72d-105">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="4d72d-106">Метод итератора использует оператор [yield](../../language-reference/statements/yield-statement.md) для возвращения каждого элемента по одному за раз.</span><span class="sxs-lookup"><span data-stu-id="4d72d-106">An iterator method uses the [Yield](../../language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="4d72d-107">При достижении инструкции `Yield` текущее расположение в коде запоминается.</span><span class="sxs-lookup"><span data-stu-id="4d72d-107">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="4d72d-108">При следующем вызове функции итератора выполнение возобновляется с этого места.</span><span class="sxs-lookup"><span data-stu-id="4d72d-108">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="4d72d-109">Вы используете итератор из клиентского кода, используя [для каждого... Оператор Next](../../language-reference/statements/for-each-next-statement.md) или с помощью запроса LINQ.</span><span class="sxs-lookup"><span data-stu-id="4d72d-109">You consume an iterator from client code by using a [For Each…Next](../../language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>

<span data-ttu-id="4d72d-110">В приведенном ниже примере первая итерация цикла `For Each` приводит к вызову метода итератора `SomeNumbers`, пока не будет достигнут первый оператор `Yield`.</span><span class="sxs-lookup"><span data-stu-id="4d72d-110">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="4d72d-111">Эта итерация возвращает значение 3. Текущее расположение в методе итератора сохраняется.</span><span class="sxs-lookup"><span data-stu-id="4d72d-111">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="4d72d-112">В следующей итерации цикла выполнение метода итератора возобновляется с того же места и снова приостанавливается при достижении оператора `Yield`.</span><span class="sxs-lookup"><span data-stu-id="4d72d-112">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="4d72d-113">Эта итерация возвращает значение 5. Текущее расположение в методе итератора снова сохраняется.</span><span class="sxs-lookup"><span data-stu-id="4d72d-113">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="4d72d-114">Цикл завершается при достижении конца метода итератора.</span><span class="sxs-lookup"><span data-stu-id="4d72d-114">The loop completes when the end of the iterator method is reached.</span></span>

```vb
Sub Main()
    For Each number As Integer In SomeNumbers()
        Console.Write(number & " ")
    Next
    ' Output: 3 5 8
    Console.ReadKey()
End Sub

Private Iterator Function SomeNumbers() As System.Collections.IEnumerable
    Yield 3
    Yield 5
    Yield 8
End Function
```

<span data-ttu-id="4d72d-115">Типом возвращаемого метода итератора или метода доступа `get` может быть <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> или <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="4d72d-115">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="4d72d-116">`Exit Function` `Return` Для завершения итерации можно использовать оператор или.</span><span class="sxs-lookup"><span data-stu-id="4d72d-116">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>

<span data-ttu-id="4d72d-117">Visual Basic функция итератора или `get` объявление метода доступа содержит модификатор [iterator](../../language-reference/modifiers/iterator.md) .</span><span class="sxs-lookup"><span data-stu-id="4d72d-117">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../language-reference/modifiers/iterator.md) modifier.</span></span>

<span data-ttu-id="4d72d-118">Итераторы появились в Visual Basic в Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="4d72d-118">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>

<span data-ttu-id="4d72d-119">**Содержание раздела**</span><span class="sxs-lookup"><span data-stu-id="4d72d-119">**In this topic**</span></span>

- [<span data-ttu-id="4d72d-120">Простой итератор</span><span class="sxs-lookup"><span data-stu-id="4d72d-120">Simple Iterator</span></span>](#BKMK_SimpleIterator)

- [<span data-ttu-id="4d72d-121">Создание класса коллекции</span><span class="sxs-lookup"><span data-stu-id="4d72d-121">Creating a Collection Class</span></span>](#BKMK_CollectionClass)

- [<span data-ttu-id="4d72d-122">Блоки try</span><span class="sxs-lookup"><span data-stu-id="4d72d-122">Try Blocks</span></span>](#BKMK_TryBlocks)

- [<span data-ttu-id="4d72d-123">Анонимные методы</span><span class="sxs-lookup"><span data-stu-id="4d72d-123">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)

- [<span data-ttu-id="4d72d-124">Использование итераторов с универсальным списком</span><span class="sxs-lookup"><span data-stu-id="4d72d-124">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)

- [<span data-ttu-id="4d72d-125">Сведения о синтаксисе</span><span class="sxs-lookup"><span data-stu-id="4d72d-125">Syntax Information</span></span>](#BKMK_SyntaxInformation)

- [<span data-ttu-id="4d72d-126">Техническая реализация</span><span class="sxs-lookup"><span data-stu-id="4d72d-126">Technical Implementation</span></span>](#BKMK_Technical)

- [<span data-ttu-id="4d72d-127">Использование итераторов</span><span class="sxs-lookup"><span data-stu-id="4d72d-127">Use of Iterators</span></span>](#BKMK_UseOfIterators)

> [!NOTE]
> <span data-ttu-id="4d72d-128">Для всех примеров в разделе, за исключением простого примера итератора, включите операторы [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) для `System.Collections` `System.Collections.Generic` пространств имен и.</span><span class="sxs-lookup"><span data-stu-id="4d72d-128">For all examples in the topic except the Simple Iterator example, include [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><a name="BKMK_SimpleIterator"></a> <span data-ttu-id="4d72d-129">Простой итератор</span><span class="sxs-lookup"><span data-stu-id="4d72d-129">Simple Iterator</span></span>

<span data-ttu-id="4d72d-130">В следующем примере имеется один `Yield` оператор, который находится внутри блока [for... Следующий](../../language-reference/statements/for-next-statement.md) цикл.</span><span class="sxs-lookup"><span data-stu-id="4d72d-130">The following example has a single `Yield` statement that is inside a [For…Next](../../language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="4d72d-131">В методе `Main` каждая итерация оператора `For Each` создает вызов функции итератора, которая выполняет следующий оператор `Yield`.</span><span class="sxs-lookup"><span data-stu-id="4d72d-131">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>

```vb
Sub Main()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    ' Output: 6 8 10 12 14 16 18
    Console.ReadKey()
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As System.Collections.Generic.IEnumerable(Of Integer)

    ' Yield even numbers in the range.
    For number As Integer = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="creating-a-collection-class"></a><a name="BKMK_CollectionClass"></a> <span data-ttu-id="4d72d-132">Создание класса коллекции</span><span class="sxs-lookup"><span data-stu-id="4d72d-132">Creating a Collection Class</span></span>

<span data-ttu-id="4d72d-133">В следующем примере класс `DaysOfTheWeek` реализует интерфейс <xref:System.Collections.IEnumerable>, которому требуется метод <xref:System.Collections.IEnumerable.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d72d-133">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="4d72d-134">Компилятор неявно вызывает метод `GetEnumerator`, который возвращает <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="4d72d-134">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="4d72d-135">`GetEnumerator`Метод возвращает каждую строку по одному с помощью `Yield` инструкции, а `Iterator` Модификатор — в объявлении функции.</span><span class="sxs-lookup"><span data-stu-id="4d72d-135">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>

```vb
Sub Main()
    Dim days As New DaysOfTheWeek()
    For Each day As String In days
        Console.Write(day & " ")
    Next
    ' Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey()
End Sub

Private Class DaysOfTheWeek
    Implements IEnumerable

    Public days =
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        ' Yield each day of the week.
        For i As Integer = 0 To days.Length - 1
            Yield days(i)
        Next
    End Function
End Class
```

<span data-ttu-id="4d72d-136">В приведенном ниже примере создается класс `Zoo`, содержащий коллекцию животных.</span><span class="sxs-lookup"><span data-stu-id="4d72d-136">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="4d72d-137">Оператор `For Each`, который обращается к экземпляру класса (`theZoo`), неявно вызывает метод `GetEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="4d72d-137">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="4d72d-138">Операторы `For Each`, которые обращаются к свойствам `Birds` и `Mammals`, используют метод итератора с именем `AnimalsForType`.</span><span class="sxs-lookup"><span data-stu-id="4d72d-138">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

```vb
Sub Main()
    Dim theZoo As New Zoo()

    theZoo.AddMammal("Whale")
    theZoo.AddMammal("Rhinoceros")
    theZoo.AddBird("Penguin")
    theZoo.AddBird("Warbler")

    For Each name As String In theZoo
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros Penguin Warbler

    For Each name As String In theZoo.Birds
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Penguin Warbler

    For Each name As String In theZoo.Mammals
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros

    Console.ReadKey()
End Sub

Public Class Zoo
    Implements IEnumerable

    ' Private members.
    Private animals As New List(Of Animal)

    ' Public methods.
    Public Sub AddMammal(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})
    End Sub

    Public Sub AddBird(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})
    End Sub

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        For Each theAnimal As Animal In animals
            Yield theAnimal.Name
        Next
    End Function

    ' Public members.
    Public ReadOnly Property Mammals As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Mammal)
        End Get
    End Property

    Public ReadOnly Property Birds As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Bird)
        End Get
    End Property

    ' Private methods.
    Private Iterator Function AnimalsForType( _
    ByVal type As Animal.TypeEnum) As IEnumerable
        For Each theAnimal As Animal In animals
            If (theAnimal.Type = type) Then
                Yield theAnimal.Name
            End If
        Next
    End Function

    ' Private class.
    Private Class Animal
        Public Enum TypeEnum
            Bird
            Mammal
        End Enum

        Public Property Name As String
        Public Property Type As TypeEnum
    End Class
End Class
```

## <a name="try-blocks"></a><a name="BKMK_TryBlocks"></a> <span data-ttu-id="4d72d-139">Блоки try</span><span class="sxs-lookup"><span data-stu-id="4d72d-139">Try Blocks</span></span>

<span data-ttu-id="4d72d-140">Visual Basic позволяет `Yield` оператору в `Try` блоке [конструкции try... Перехватить... Оператор finally](../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4d72d-140">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="4d72d-141">`Try`Блок, содержащий `Yield` оператор, может иметь `Catch` блоки и может иметь `Finally` блок.</span><span class="sxs-lookup"><span data-stu-id="4d72d-141">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>

<span data-ttu-id="4d72d-142">В следующем примере `Try` блоки, `Catch` и используются `Finally` в функции итератора.</span><span class="sxs-lookup"><span data-stu-id="4d72d-142">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="4d72d-143">`Finally`Блок в функции итератора выполняется до `For Each` завершения итерации.</span><span class="sxs-lookup"><span data-stu-id="4d72d-143">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>

```vb
Sub Main()
    For Each number As Integer In Test()
        Console.WriteLine(number)
    Next
    Console.WriteLine("For Each is done.")

    ' Output:
    '  3
    '  4
    '  Something happened. Yields are done.
    '  Finally is called.
    '  For Each is done.
    Console.ReadKey()
End Sub

Private Iterator Function Test() As IEnumerable(Of Integer)
    Try
        Yield 3
        Yield 4
        Throw New Exception("Something happened. Yields are done.")
        Yield 5
        Yield 6
    Catch ex As Exception
        Console.WriteLine(ex.Message)
    Finally
        Console.WriteLine("Finally is called.")
    End Try
End Function
```

<span data-ttu-id="4d72d-144">`Yield`Оператор не может находиться внутри `Catch` блока или блока `Finally` .</span><span class="sxs-lookup"><span data-stu-id="4d72d-144">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>

<span data-ttu-id="4d72d-145">Если `For Each` тело (вместо метода итератора) создает исключение, `Catch` блок в функции итератора не выполняется, но `Finally` выполняется блок в функции итератора.</span><span class="sxs-lookup"><span data-stu-id="4d72d-145">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="4d72d-146">`Catch`Блок внутри функции итератора перехватывает только исключения, происходящие внутри функции итератора.</span><span class="sxs-lookup"><span data-stu-id="4d72d-146">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>

## <a name="anonymous-methods"></a><a name="BKMK_AnonymousMethods"></a> <span data-ttu-id="4d72d-147">Анонимные методы</span><span class="sxs-lookup"><span data-stu-id="4d72d-147">Anonymous Methods</span></span>

<span data-ttu-id="4d72d-148">В Visual Basic анонимная функция может быть функцией итератора.</span><span class="sxs-lookup"><span data-stu-id="4d72d-148">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="4d72d-149">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="4d72d-149">The following example illustrates this.</span></span>

```vb
Dim iterateSequence = Iterator Function() _
                      As IEnumerable(Of Integer)
                          Yield 1
                          Yield 2
                      End Function

For Each number As Integer In iterateSequence()
    Console.Write(number & " ")
Next
' Output: 1 2
Console.ReadKey()
```

<span data-ttu-id="4d72d-150">В следующем примере имеется метод, не являющийся итератором, который проверяет аргументы.</span><span class="sxs-lookup"><span data-stu-id="4d72d-150">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="4d72d-151">Метод возвращает результат анонимного итератора, который описывает элементы коллекции.</span><span class="sxs-lookup"><span data-stu-id="4d72d-151">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>

```vb
Sub Main()
    For Each number As Integer In GetSequence(5, 10)
        Console.Write(number & " ")
    Next
    ' Output: 5 6 7 8 9 10
    Console.ReadKey()
End Sub

Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _
As IEnumerable
    ' Validate the arguments.
    If low < 1 Then
        Throw New ArgumentException("low is too low")
    End If
    If high > 140 Then
        Throw New ArgumentException("high is too high")
    End If

    ' Return an anonymous iterator function.
    Dim iterateSequence = Iterator Function() As IEnumerable
                              For index = low To high
                                  Yield index
                              Next
                          End Function
    Return iterateSequence()
End Function
```

<span data-ttu-id="4d72d-152">Если вместо этого в функции итератора выполняется проверка, то проверка не может быть выполнена до начала первой итерации `For Each` тела.</span><span class="sxs-lookup"><span data-stu-id="4d72d-152">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>

## <a name="using-iterators-with-a-generic-list"></a><a name="BKMK_GenericList"></a> <span data-ttu-id="4d72d-153">Использование итераторов с универсальным списком</span><span class="sxs-lookup"><span data-stu-id="4d72d-153">Using Iterators with a Generic List</span></span>

<span data-ttu-id="4d72d-154">В следующем примере универсальный класс `Stack(Of T)` также реализует универсальный интерфейс <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="4d72d-154">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="4d72d-155">Метод `Push` присваивает значения массиву типа `T`.</span><span class="sxs-lookup"><span data-stu-id="4d72d-155">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="4d72d-156">Метод <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> возвращает массив значений с помощью оператора `Yield`.</span><span class="sxs-lookup"><span data-stu-id="4d72d-156">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>

<span data-ttu-id="4d72d-157">Помимо универсального метода <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> должен быть реализован и неуниверсальный метод <xref:System.Collections.IEnumerable.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d72d-157">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="4d72d-158">Это связано с тем, что <xref:System.Collections.Generic.IEnumerable%601> наследуется от <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="4d72d-158">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="4d72d-159">Неуниверсальная реализация подчиняется универсальной реализации.</span><span class="sxs-lookup"><span data-stu-id="4d72d-159">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="4d72d-160">В этом примере используются именованные итераторы для поддержки различных способов итерации по одной и той же коллекции данных.</span><span class="sxs-lookup"><span data-stu-id="4d72d-160">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="4d72d-161">Эти именованные итераторы являются свойствами `TopToBottom` и `BottomToTop` и методом `TopN`.</span><span class="sxs-lookup"><span data-stu-id="4d72d-161">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="4d72d-162">`BottomToTop`Объявление свойства включает `Iterator` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="4d72d-162">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>

```vb
Sub Main()
    Dim theStack As New Stack(Of Integer)

    ' Add items to the stack.
    For number As Integer = 0 To 9
        theStack.Push(number)
    Next

    ' Retrieve items from the stack.
    ' For Each is allowed because theStack implements
    ' IEnumerable(Of Integer).
    For Each number As Integer In theStack
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    ' For Each is allowed, because theStack.TopToBottom
    ' returns IEnumerable(Of Integer).
    For Each number As Integer In theStack.TopToBottom
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    For Each number As Integer In theStack.BottomToTop
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 0 1 2 3 4 5 6 7 8 9

    For Each number As Integer In theStack.TopN(7)
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3

    Console.ReadKey()
End Sub

Public Class Stack(Of T)
    Implements IEnumerable(Of T)

    Private values As T() = New T(99) {}
    Private top As Integer = 0

    Public Sub Push(ByVal t As T)
        values(top) = t
        top = top + 1
    End Sub

    Public Function Pop() As T
        top = top - 1
        Return values(top)
    End Function

    ' This function implements the GetEnumerator method. It allows
    ' an instance of the class to be used in a For Each statement.
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _
        Implements IEnumerable(Of T).GetEnumerator

        For index As Integer = top - 1 To 0 Step -1
            Yield values(index)
        Next
    End Function

    Public Iterator Function GetEnumerator1() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        Yield GetEnumerator()
    End Function

    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)
        Get
            Return Me
        End Get
    End Property

    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)
        Get
            For index As Integer = 0 To top - 1
                Yield values(index)
            Next
        End Get
    End Property

    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _
        As IEnumerable(Of T)

        ' Return less than itemsFromTop if necessary.
        Dim startIndex As Integer =
            If(itemsFromTop >= top, 0, top - itemsFromTop)

        For index As Integer = top - 1 To startIndex Step -1
            Yield values(index)
        Next
    End Function
End Class
```

## <a name="syntax-information"></a><a name="BKMK_SyntaxInformation"></a> <span data-ttu-id="4d72d-163">Сведения о синтаксисе</span><span class="sxs-lookup"><span data-stu-id="4d72d-163">Syntax Information</span></span>

<span data-ttu-id="4d72d-164">Итератор может являться методом или методом доступа `get`.</span><span class="sxs-lookup"><span data-stu-id="4d72d-164">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="4d72d-165">Итератор не может использоваться в событии, конструкторе экземпляра, статическом конструкторе или статическом деструкторе.</span><span class="sxs-lookup"><span data-stu-id="4d72d-165">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>

<span data-ttu-id="4d72d-166">Должно существовать неявное преобразование выражения типа в операторе `Yield` в возвращаемый тип итератора.</span><span class="sxs-lookup"><span data-stu-id="4d72d-166">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>

<span data-ttu-id="4d72d-167">В Visual Basic метод итератора не может иметь никаких `ByRef` параметров.</span><span class="sxs-lookup"><span data-stu-id="4d72d-167">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>

<span data-ttu-id="4d72d-168">В Visual Basic «yield» не является зарезервированным словом и имеет специальное значение только при использовании в `Iterator` методе или методе `get` доступа.</span><span class="sxs-lookup"><span data-stu-id="4d72d-168">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>

## <a name="technical-implementation"></a><a name="BKMK_Technical"></a> <span data-ttu-id="4d72d-169">Техническая реализация</span><span class="sxs-lookup"><span data-stu-id="4d72d-169">Technical Implementation</span></span>

<span data-ttu-id="4d72d-170">Хотя итератор создается как метод, компилятор переводит его во вложенный класс, который фактически является конечным автоматом.</span><span class="sxs-lookup"><span data-stu-id="4d72d-170">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="4d72d-171">Этот класс отслеживает положение итератора, пока в клиентском коде выполняется цикл `For Each...Next`.</span><span class="sxs-lookup"><span data-stu-id="4d72d-171">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>

<span data-ttu-id="4d72d-172">Чтобы просмотреть операции компилятора, воспользуйтесь средством Ildasm.exe для отображения кода промежуточного языка Майкрософт, создаваемого для метода итератора.</span><span class="sxs-lookup"><span data-stu-id="4d72d-172">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>

<span data-ttu-id="4d72d-173">При создании итератора для [класса](../../language-reference/statements/class-statement.md) или [структуры](../../language-reference/statements/structure-statement.md)не нужно реализовывать весь <xref:System.Collections.IEnumerator> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="4d72d-173">When you create an iterator for a [class](../../language-reference/statements/class-statement.md) or [struct](../../language-reference/statements/structure-statement.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="4d72d-174">Когда компилятор обнаруживает итератор, он автоматически создает методы `Current`, `MoveNext` и `Dispose` интерфейса <xref:System.Collections.IEnumerator> или <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="4d72d-174">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="4d72d-175">В каждой последовательной итерации цикла `For Each…Next` (или непосредственном вызове метода `IEnumerator.MoveNext`) код тела следующего итератора возобновляет выполнение после предыдущего оператора `Yield`.</span><span class="sxs-lookup"><span data-stu-id="4d72d-175">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="4d72d-176">Затем он переходит к следующему `Yield` оператору до тех пор, пока не будет достигнут конец тела итератора или пока не `Exit Function` `Return` встретится оператор или.</span><span class="sxs-lookup"><span data-stu-id="4d72d-176">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>

<span data-ttu-id="4d72d-177">Итераторы не поддерживают <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> метод.</span><span class="sxs-lookup"><span data-stu-id="4d72d-177">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4d72d-178">Для повторной итерации сначала необходимо получить новый итератор.</span><span class="sxs-lookup"><span data-stu-id="4d72d-178">To re-iterate from the start, you must obtain a new iterator.</span></span>

<span data-ttu-id="4d72d-179">Дополнительные сведения см. в разделе [Спецификация языка Visual Basic](../../reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4d72d-179">For additional information, see the [Visual Basic Language Specification](../../reference/language-specification/index.md).</span></span>

## <a name="use-of-iterators"></a><a name="BKMK_UseOfIterators"></a> <span data-ttu-id="4d72d-180">Использование итераторов</span><span class="sxs-lookup"><span data-stu-id="4d72d-180">Use of Iterators</span></span>

<span data-ttu-id="4d72d-181">Итераторы позволяют поддерживать простоту цикла `For Each`, когда необходимо использовать сложный код для заполнения последовательности списков.</span><span class="sxs-lookup"><span data-stu-id="4d72d-181">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="4d72d-182">Это может оказаться полезным в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="4d72d-182">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="4d72d-183">Изменение последовательности списков после первой итерации цикла `For Each`.</span><span class="sxs-lookup"><span data-stu-id="4d72d-183">Modify the list sequence after the first `For Each` loop iteration.</span></span>

- <span data-ttu-id="4d72d-184">Если необходимо избежать полной загрузки большого списка перед первой итерацией цикла `For Each`.</span><span class="sxs-lookup"><span data-stu-id="4d72d-184">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="4d72d-185">Пример: при постраничной загрузке пакета строк таблицы.</span><span class="sxs-lookup"><span data-stu-id="4d72d-185">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="4d72d-186">Другой пример — метод <xref:System.IO.DirectoryInfo.EnumerateFiles%2A>, реализующий итераторы в .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4d72d-186">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="4d72d-187">Инкапсулирование построения списка в итераторе.</span><span class="sxs-lookup"><span data-stu-id="4d72d-187">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="4d72d-188">В методе итератора можно построить список, а затем выдавать каждый результат в цикле.</span><span class="sxs-lookup"><span data-stu-id="4d72d-188">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d72d-189">См. также</span><span class="sxs-lookup"><span data-stu-id="4d72d-189">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="4d72d-190">Оператор For Each…Next</span><span class="sxs-lookup"><span data-stu-id="4d72d-190">For Each...Next Statement</span></span>](../../language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="4d72d-191">Оператор Yield</span><span class="sxs-lookup"><span data-stu-id="4d72d-191">Yield Statement</span></span>](../../language-reference/statements/yield-statement.md)
- [<span data-ttu-id="4d72d-192">Итератор</span><span class="sxs-lookup"><span data-stu-id="4d72d-192">Iterator</span></span>](../../language-reference/modifiers/iterator.md)
