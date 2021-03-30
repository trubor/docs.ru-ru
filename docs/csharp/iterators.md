---
title: Iterators
description: Сведения о том, как использовать встроенные итераторы C# и создавать собственные настраиваемые методы итераторов.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 357f05f6ae1a4cec7566ddc821036354c932af90
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872643"
---
# <a name="iterators"></a><span data-ttu-id="6196d-103">Iterators</span><span class="sxs-lookup"><span data-stu-id="6196d-103">Iterators</span></span>

<span data-ttu-id="6196d-104">Почти каждой написанной вами программе придется выполнять итерацию определенной коллекции.</span><span class="sxs-lookup"><span data-stu-id="6196d-104">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="6196d-105">Для этого вы напишете код, проверяющий каждый элемент в коллекции.</span><span class="sxs-lookup"><span data-stu-id="6196d-105">You'll write code that examines every item in a collection.</span></span>

<span data-ttu-id="6196d-106">Кроме того, вы создадите методы итератора — методы, которые итератор (то есть объект, который проходит по контейнеру, в частности списки) создает для элементов соответствующего класса.</span><span class="sxs-lookup"><span data-stu-id="6196d-106">You'll also create iterator methods which are methods that produces an iterator (which is an object that traverses a container, particularly lists) for the elements of that class.</span></span> <span data-ttu-id="6196d-107">Их можно использовать в следующих целях:</span><span class="sxs-lookup"><span data-stu-id="6196d-107">These can be used for:</span></span>

+ <span data-ttu-id="6196d-108">Выполнение определенного действия с каждым элементом в коллекции.</span><span class="sxs-lookup"><span data-stu-id="6196d-108">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="6196d-109">Перечисление настраиваемой коллекции.</span><span class="sxs-lookup"><span data-stu-id="6196d-109">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="6196d-110">Расширение [LINQ](linq/index.md) или других библиотек.</span><span class="sxs-lookup"><span data-stu-id="6196d-110">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="6196d-111">Создание конвейера данных, обеспечивающего эффективный поток данных через методы итератора.</span><span class="sxs-lookup"><span data-stu-id="6196d-111">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="6196d-112">В языке C# предусмотрены функции, позволяющие использовать оба сценария.</span><span class="sxs-lookup"><span data-stu-id="6196d-112">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="6196d-113">В этой статье представлены общие сведения об этих функциях.</span><span class="sxs-lookup"><span data-stu-id="6196d-113">This article provides an overview of those features.</span></span>

<span data-ttu-id="6196d-114">Это руководство описывает несколько шагов.</span><span class="sxs-lookup"><span data-stu-id="6196d-114">This tutorial has multiple steps.</span></span> <span data-ttu-id="6196d-115">После каждого из них вы сможете запустить приложение и оценить результаты.</span><span class="sxs-lookup"><span data-stu-id="6196d-115">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="6196d-116">Вы также можете [просмотреть или загрузить готовый пример](https://github.com/dotnet/samples/blob/main/csharp/iterators) для этого раздела.</span><span class="sxs-lookup"><span data-stu-id="6196d-116">You can also [view or download the completed sample](https://github.com/dotnet/samples/blob/main/csharp/iterators) for this topic.</span></span> <span data-ttu-id="6196d-117">Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="6196d-117">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="6196d-118">Итерация для каждого</span><span class="sxs-lookup"><span data-stu-id="6196d-118">Iterating with foreach</span></span>

<span data-ttu-id="6196d-119">Вы полнить перечисление коллекции несложно. Ключевое слово `foreach` перечисляет коллекцию, выполняя внедренный оператор по одному разу для каждого элемента в коллекции:</span><span class="sxs-lookup"><span data-stu-id="6196d-119">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="6196d-120">Больше ничего не требуется.</span><span class="sxs-lookup"><span data-stu-id="6196d-120">That's all there is to it.</span></span> <span data-ttu-id="6196d-121">Для итерации содержимого той или иной коллекции нужен только это оператор `foreach`.</span><span class="sxs-lookup"><span data-stu-id="6196d-121">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="6196d-122">При этом в работе оператора `foreach` нет ничего сложного.</span><span class="sxs-lookup"><span data-stu-id="6196d-122">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="6196d-123">Он создает код, необходимый для итерации коллекции, опираясь на два универсальных интерфейса, определенных в библиотеке ядра .NET: `IEnumerable<T>` и `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="6196d-123">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="6196d-124">Более подробно этот механизм рассматривается ниже.</span><span class="sxs-lookup"><span data-stu-id="6196d-124">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="6196d-125">Оба этих интерфейса также имеют неуниверсальные аналоги: `IEnumerable` и `IEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="6196d-125">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="6196d-126">[Универсальные](programming-guide/generics/index.md) версии более предпочтительны для современного кода.</span><span class="sxs-lookup"><span data-stu-id="6196d-126">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="6196d-127">Источники перечисления с применением методов итератора</span><span class="sxs-lookup"><span data-stu-id="6196d-127">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="6196d-128">Еще одна полезная функция языка C# позволяет выполнять сборку методов, создающих источник для перечисления.</span><span class="sxs-lookup"><span data-stu-id="6196d-128">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="6196d-129">Это так называемые *методы итератора*.</span><span class="sxs-lookup"><span data-stu-id="6196d-129">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="6196d-130">Метод итератора определяет, какие образом будут создаваться объекты в последовательности по запросу.</span><span class="sxs-lookup"><span data-stu-id="6196d-130">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="6196d-131">Метод итератора определяется с помощью контекстных ключевых слов `yield return`.</span><span class="sxs-lookup"><span data-stu-id="6196d-131">You use the `yield return` contextual keywords to define an iterator method.</span></span>

<span data-ttu-id="6196d-132">Напишем метод итератора, выдающий последовательность целых чисел от 0 до 9:</span><span class="sxs-lookup"><span data-stu-id="6196d-132">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    yield return 0;
    yield return 1;
    yield return 2;
    yield return 3;
    yield return 4;
    yield return 5;
    yield return 6;
    yield return 7;
    yield return 8;
    yield return 9;
}
```

<span data-ttu-id="6196d-133">Отдельные операторы `yield return` в этом коде показывают, что в любом методе итератора можно использовать сразу несколько дискретных операторов `yield return`.</span><span class="sxs-lookup"><span data-stu-id="6196d-133">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="6196d-134">Другие языковые конструкции можно (и нужно) включать для того, чтобы код метода итератора стал более простым.</span><span class="sxs-lookup"><span data-stu-id="6196d-134">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="6196d-135">Точно такую же последовательность чисел выдает определение метода, приведенное ниже:</span><span class="sxs-lookup"><span data-stu-id="6196d-135">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

<span data-ttu-id="6196d-136">Выбирать какой-то один из этих вариантов необязательно.</span><span class="sxs-lookup"><span data-stu-id="6196d-136">You don't have to decide one or the other.</span></span> <span data-ttu-id="6196d-137">В код можно добавлять столько операторов `yield return`, сколько требуется для вашего метода:</span><span class="sxs-lookup"><span data-stu-id="6196d-137">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    index = 100;
    while (index < 110)
        yield return index++;
}
```

<span data-ttu-id="6196d-138">Это базовый синтаксис.</span><span class="sxs-lookup"><span data-stu-id="6196d-138">That's the basic syntax.</span></span> <span data-ttu-id="6196d-139">Рассмотрим практический пример применения метода итератора.</span><span class="sxs-lookup"><span data-stu-id="6196d-139">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="6196d-140">Допустим, вы занимаетесь проектом IoT и имеете дело с датчиками устройств, которые создают большой поток данных.</span><span class="sxs-lookup"><span data-stu-id="6196d-140">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="6196d-141">Чтобы получить представление об этих данных, можно написать метод, формирующий выборку из каждого N-го элемента данных.</span><span class="sxs-lookup"><span data-stu-id="6196d-141">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="6196d-142">С этой задачей справится вот такой небольшой метод итератора:</span><span class="sxs-lookup"><span data-stu-id="6196d-142">This small iterator method does the trick:</span></span>

```csharp
public static IEnumerable<T> Sample(this IEnumerable<T> sourceSequence, int interval)
{
    int index = 0;
    foreach (T item in sourceSequence)
    {
        if (index++ % interval == 0)
            yield return item;
    }
}
```

<span data-ttu-id="6196d-143">Методы итератора подчиняются одному важному ограничению: в одном и том же методе не могут одновременно присутствовать оператор `return` и оператор `yield return`.</span><span class="sxs-lookup"><span data-stu-id="6196d-143">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="6196d-144">Этот код компилироваться не будет:</span><span class="sxs-lookup"><span data-stu-id="6196d-144">The following will not compile:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    // generates a compile time error:
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;
}
```

<span data-ttu-id="6196d-145">Обычно это ограничение не вызывает проблем.</span><span class="sxs-lookup"><span data-stu-id="6196d-145">This restriction normally isn't a problem.</span></span> <span data-ttu-id="6196d-146">Вы можете либо использовать в методе операторы `yield return`, либо разделить исходный метод на несколько отдельных методов, одни из которых будут включать оператор `return`, а другие — `yield return`.</span><span class="sxs-lookup"><span data-stu-id="6196d-146">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="6196d-147">Немного изменим последний метод, вставив в каждом случае оператор `yield return`:</span><span class="sxs-lookup"><span data-stu-id="6196d-147">You can modify the last method slightly to use `yield return` everywhere:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```

<span data-ttu-id="6196d-148">В некоторых случаях метод итератора лучше разбить на два разных метода.</span><span class="sxs-lookup"><span data-stu-id="6196d-148">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="6196d-149">В одном будет использоваться оператор `return`, а в другом — `yield return`.</span><span class="sxs-lookup"><span data-stu-id="6196d-149">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="6196d-150">Допустим, вам нужно получить пустую коллекцию или первые пять нечетных чисел, используя логический аргумент.</span><span class="sxs-lookup"><span data-stu-id="6196d-150">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="6196d-151">Для этого можно написать следующие два метода:</span><span class="sxs-lookup"><span data-stu-id="6196d-151">You could write that as these two methods:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitOddNumbers(bool getCollection)
{
    if (getCollection == false)
        return new int[0];
    else
        return IteratorMethod();
}

private IEnumerable<int> IteratorMethod()
{
    int index = 0;
    while (index < 10)
    {
        if (index % 2 == 1)
            yield return index;
        index++;
    }
}
```

<span data-ttu-id="6196d-152">Посмотрите на приведенные выше методы.</span><span class="sxs-lookup"><span data-stu-id="6196d-152">Look at the methods above.</span></span> <span data-ttu-id="6196d-153">В первом используется стандартный оператор `return`, который возвращает либо пустую коллекцию, либо итератор, созданный вторым методом.</span><span class="sxs-lookup"><span data-stu-id="6196d-153">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="6196d-154">Второй метод включает оператор `yield return`, создающий запрошенную последовательность.</span><span class="sxs-lookup"><span data-stu-id="6196d-154">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="6196d-155">Подробнее об операторе `foreach`</span><span class="sxs-lookup"><span data-stu-id="6196d-155">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="6196d-156">Оператор `foreach` разворачивается в стандартную идиому, которая выполняет итерацию всех элементов в коллекции с помощью интерфейсов `IEnumerable<T>` и `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="6196d-156">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="6196d-157">Кроме того, он сводит к минимуму ошибки, допускаемые разработчиками в результате неправильного управления ресурсами.</span><span class="sxs-lookup"><span data-stu-id="6196d-157">It also  minimizes errors developers make by not properly managing resources.</span></span>

<span data-ttu-id="6196d-158">Компилятор преобразует цикл `foreach`, показанный в первом примере, в конструкцию следующего вида:</span><span class="sxs-lookup"><span data-stu-id="6196d-158">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="6196d-159">Эта конструкция представляет код, создаваемый компилятором C# версии 5 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="6196d-159">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="6196d-160">До выхода версии 5 переменная `item` имела другую область:</span><span class="sxs-lookup"><span data-stu-id="6196d-160">Prior to version 5, the `item` variable had a different scope:</span></span>

```csharp
// C# versions 1 through 4:
IEnumerator<int> enumerator = collection.GetEnumerator();
int item = default(int);
while (enumerator.MoveNext())
{
    item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="6196d-161">Изменения были обусловлены тем, что прежнее поведение этой переменной могло вызывать с трудом выявляемые и поддающиеся диагностике ошибки, связанные с лямбда-выражениями.</span><span class="sxs-lookup"><span data-stu-id="6196d-161">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="6196d-162">Дополнительные сведения о лямбда-выражениях см. в разделе [Лямбда-выражения](language-reference/operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="6196d-162">For more information about lambda expressions, see [Lambda expressions](language-reference/operators/lambda-expressions.md).</span></span>

<span data-ttu-id="6196d-163">На практике компилятор создает несколько более сложный код и устраняет ситуации, когда объект, возвращаемый методом `GetEnumerator()`, реализует интерфейс `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="6196d-163">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="6196d-164">Полная версия кода выглядит так:</span><span class="sxs-lookup"><span data-stu-id="6196d-164">The full expansion generates code more like this:</span></span>

```csharp
{
    var enumerator = collection.GetEnumerator();
    try
    {
        while (enumerator.MoveNext())
        {
            var item = enumerator.Current;
            Console.WriteLine(item.ToString());
        }
    } finally
    {
        // dispose of enumerator.
    }
}
```

<span data-ttu-id="6196d-165">Способ ликвидации перечислителя зависит от характеристик типа `enumerator`.</span><span class="sxs-lookup"><span data-stu-id="6196d-165">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="6196d-166">Как правило, предложение `finally` разворачивается следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6196d-166">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

<span data-ttu-id="6196d-167">Однако если тип `enumerator` является запечатанным, а тип `enumerator` не подвергается явному преобразованию в тип `IDisposable`, предложение `finally` разворачивается в пустой блок:</span><span class="sxs-lookup"><span data-stu-id="6196d-167">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>

```csharp
finally
{
}
```

<span data-ttu-id="6196d-168">Если же тип `enumerator` подвергается неявному преобразованию в тип `IDisposable`, а `enumerator` является типом значения, не допускающим значение NULL, предложение `finally` разворачивается следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6196d-168">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

<span data-ttu-id="6196d-169">К счастью, запоминать все это не нужно.</span><span class="sxs-lookup"><span data-stu-id="6196d-169">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="6196d-170">Оператор `foreach` обрабатывает все эти нюансы в фоновом режиме,</span><span class="sxs-lookup"><span data-stu-id="6196d-170">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="6196d-171">а компилятор создает правильный код для любой из этих конструкций.</span><span class="sxs-lookup"><span data-stu-id="6196d-171">The compiler will generate the correct code for any of these constructs.</span></span>
