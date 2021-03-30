---
title: Работа с коллекциями. Вводное руководство по C#
description: Это руководство по C# предоставляет для изучения примере коллекции списков.
ms.date: 02/05/2021
ms.openlocfilehash: 0bc2b84964e8fc270fe7e9d635c4c18aa1abb390
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111144"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="5b1ee-103">Научитесь управлять коллекциями данных с использованием универсального типа списка</span><span class="sxs-lookup"><span data-stu-id="5b1ee-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="5b1ee-104">Это вводное руководство содержит общие сведения о языке C# и классе <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5b1ee-105">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="5b1ee-105">Prerequisites</span></span>

<span data-ttu-id="5b1ee-106">Для работы с руководством вам потребуется компьютер, настроенный для разработки в локальной среде.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-106">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="5b1ee-107">В Windows, Linux или macOS для создания, сборки и запуска приложений можно использовать .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-107">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="5b1ee-108">Для Mac и Windows можно использовать Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-108">On Mac and Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="5b1ee-109">Инструкции по настройке см. в статье [Настройка локальной среды](local-environment.md).</span><span class="sxs-lookup"><span data-stu-id="5b1ee-109">For setup instructions, see [Set up your local environment](local-environment.md).</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="5b1ee-110">Пример простого списка</span><span class="sxs-lookup"><span data-stu-id="5b1ee-110">A basic list example</span></span>

<span data-ttu-id="5b1ee-111">Создайте каталог с именем *list-tutorial*.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-111">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="5b1ee-112">Откройте этот каталог и выполните команду `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-112">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="5b1ee-113">Откройте *Program.cs* в любом редакторе и замените существующий код следующим:</span><span class="sxs-lookup"><span data-stu-id="5b1ee-113">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

var names = new List<string> { "<name>", "Ana", "Felipe" };
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="5b1ee-114">Замените `<name>` собственным именем.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-114">Replace `<name>` with your name.</span></span> <span data-ttu-id="5b1ee-115">Сохраните *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-115">Save *Program.cs*.</span></span> <span data-ttu-id="5b1ee-116">Введите в окне консоли команду `dotnet run` для тестирования.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-116">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="5b1ee-117">Вы создали список строк, добавили три имени в этот список и вывели имена прописными буквами.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-117">You've created a list of strings, added three names to that list, and printed the names in all CAPS.</span></span> <span data-ttu-id="5b1ee-118">Для циклического прохода по списку вы примените концепции, которые изучили в предыдущих руководствах.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-118">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="5b1ee-119">В коде для отображения имен используется функция [интерполяции строк](../../language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="5b1ee-119">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="5b1ee-120">Если перед `string` добавить символ `$`, код C# можно внедрять в объявление строки.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-120">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="5b1ee-121">Фактическая строка заменяет код C# генерируемым значением.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-121">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="5b1ee-122">В этом примере она заменяет `{name.ToUpper()}` именами, буквы каждого из которых преобразованы в прописные, так как вызван метод <xref:System.String.ToUpper%2A>.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-122">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="5b1ee-123">Продолжим изучение.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-123">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="5b1ee-124">Изменение содержимого списка</span><span class="sxs-lookup"><span data-stu-id="5b1ee-124">Modify list contents</span></span>

<span data-ttu-id="5b1ee-125">В созданной коллекции используется тип <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-125">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="5b1ee-126">При применении такого типа сохраняются последовательности элементов.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-126">This type stores sequences of elements.</span></span> <span data-ttu-id="5b1ee-127">Тип элементов указывается в угловых скобках.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-127">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="5b1ee-128">Важный аспект типа <xref:System.Collections.Generic.List%601> — возможность увеличения или уменьшения, что позволяет добавлять или удалять элементы.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-128">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="5b1ee-129">Добавьте этот код в конец программы:</span><span class="sxs-lookup"><span data-stu-id="5b1ee-129">Add this code at the end of your program:</span></span>

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="5b1ee-130">В конец списка добавлены еще два имени.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-130">You've added two more names to the end of the list.</span></span> <span data-ttu-id="5b1ee-131">При этом одно имя удалено.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-131">You've also removed one as well.</span></span> <span data-ttu-id="5b1ee-132">Сохраните файл и введите `dotnet run` для тестирования.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-132">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="5b1ee-133"><xref:System.Collections.Generic.List%601> позволяет добавлять ссылки на отдельные элементы по **индексу**.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-133">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="5b1ee-134">Поместите индекс между токенами `[` и `]` после имени списка.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-134">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="5b1ee-135">Для первого индекса в C# используется значение 0.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-135">C# uses 0 for the first index.</span></span> <span data-ttu-id="5b1ee-136">Добавьте следующий код сразу после добавленного фрагмента и протестируйте его:</span><span class="sxs-lookup"><span data-stu-id="5b1ee-136">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="5b1ee-137">Доступ к индексу за пределами списка получить невозможно.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-137">You can't access an index beyond the end of the list.</span></span> <span data-ttu-id="5b1ee-138">Помните, что индексы начинаются с 0, поэтому максимальный допустимый индекс меньше, чем число элементов в списке.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-138">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="5b1ee-139">Вы можете проверить, как долго в списке используется свойство <xref:System.Collections.Generic.List%601.Count%2A>.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-139">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="5b1ee-140">Добавьте следующий код в конец программы:</span><span class="sxs-lookup"><span data-stu-id="5b1ee-140">Add the following code at the end of your program:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="5b1ee-141">Сохраните файл и еще раз введите `dotnet run`, чтобы просмотреть результаты.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-141">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="5b1ee-142">Поиск по спискам и их сортировка</span><span class="sxs-lookup"><span data-stu-id="5b1ee-142">Search and sort lists</span></span>

<span data-ttu-id="5b1ee-143">В наших примерах используются сравнительно небольшие списки. Но приложения часто создают списки с гораздо большим количеством элементов, иногда они исчисляются в тысячах.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-143">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="5b1ee-144">Чтобы найти элементы в таких больших коллекциях, необходимо выполнить поиск различных элементов по списку.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-144">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="5b1ee-145">Метод <xref:System.Collections.Generic.List%601.IndexOf%2A> выполняет поиск элемента и возвращает его индекс.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-145">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="5b1ee-146">Если элемент отсутствует в списке, `IndexOf` возвращает `-1`.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-146">If the item isn't in the list, `IndexOf` returns `-1`.</span></span> <span data-ttu-id="5b1ee-147">Добавьте этот код в конец программы:</span><span class="sxs-lookup"><span data-stu-id="5b1ee-147">Add this code to the bottom of your program:</span></span>

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

<span data-ttu-id="5b1ee-148">Кроме того, можно сортировать элементы в списке.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-148">The items in your list can be sorted as well.</span></span> <span data-ttu-id="5b1ee-149">Метод <xref:System.Collections.Generic.List%601.Sort%2A> сортирует все элементы списка в обычном порядке (строки — в алфавитном).</span><span class="sxs-lookup"><span data-stu-id="5b1ee-149">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically for strings).</span></span> <span data-ttu-id="5b1ee-150">Добавьте этот код в конец программы:</span><span class="sxs-lookup"><span data-stu-id="5b1ee-150">Add this code to the bottom of your program:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="5b1ee-151">Сохраните файл и введите `dotnet run`, чтобы протестировать последнюю версию.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-151">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="5b1ee-152">Прежде чем перейти к следующему разделу, переместим текущий код в отдельный метод.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-152">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="5b1ee-153">Это упростит начало работы с новым примером.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-153">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="5b1ee-154">Поместите весь написанный код в новый метод с именем `WorkWithStrings()`.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-154">Place all the code you've written in a new method called `WorkWithStrings()`.</span></span> <span data-ttu-id="5b1ee-155">Вызовите этот метод в начале кода программы.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-155">Call that method at the top of your program.</span></span> <span data-ttu-id="5b1ee-156">В результате ваш код должен выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5b1ee-156">When you finish, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

WorkWithString();

void WorkWithString()
{
    var names = new List<string> { "<name>", "Ana", "Felipe" };
    foreach (var name in names)
    {
        Console.WriteLine($"Hello {name.ToUpper()}!");
    }

    Console.WriteLine();
    names.Add("Maria");
    names.Add("Bill");
    names.Remove("Ana");
    foreach (var name in names)
    {
        Console.WriteLine($"Hello {name.ToUpper()}!");
    }

    Console.WriteLine($"My name is {names[0]}");
    Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

    Console.WriteLine($"The list has {names.Count} people in it");

    var index = names.IndexOf("Felipe");
    if (index == -1)
    {
        Console.WriteLine($"When an item is not found, IndexOf returns {index}");
    }
    else
    {
        Console.WriteLine($"The name {names[index]} is at index {index}");
    }

    index = names.IndexOf("Not Found");
    if (index == -1)
    {
        Console.WriteLine($"When an item is not found, IndexOf returns {index}");
    }
    else
    {
        Console.WriteLine($"The name {names[index]} is at index {index}");

    }

    names.Sort();
    foreach (var name in names)
    {
        Console.WriteLine($"Hello {name.ToUpper()}!");
    }
}
```

## <a name="lists-of-other-types"></a><span data-ttu-id="5b1ee-157">Списки других типов</span><span class="sxs-lookup"><span data-stu-id="5b1ee-157">Lists of other types</span></span>

<span data-ttu-id="5b1ee-158">Вы уже использовали в списках тип `string`.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-158">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="5b1ee-159">Создадим <xref:System.Collections.Generic.List%601> с использованием другого типа.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-159">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="5b1ee-160">Сначала создадим набор чисел.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-160">Let's build a set of numbers.</span></span>

<span data-ttu-id="5b1ee-161">Добавьте следующий код в программу после вызова `WorkWithStrings()`:</span><span class="sxs-lookup"><span data-stu-id="5b1ee-161">Add the following to your program after you call `WorkWithStrings()`:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="5b1ee-162">Будет создан список целых чисел. Для первых двух целых чисел будет задано значение 1.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-162">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="5b1ee-163">Это два первых значения *последовательности Фибоначчи*.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-163">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="5b1ee-164">Каждое следующее число Фибоначчи — это сумма двух предыдущих чисел.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-164">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="5b1ee-165">Добавьте этот код:</span><span class="sxs-lookup"><span data-stu-id="5b1ee-165">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="5b1ee-166">Сохраните файл и введите `dotnet run`, чтобы просмотреть результаты.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-166">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="5b1ee-167">Для задач этого раздела вы можете закомментировать код, который вызывает `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-167">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="5b1ee-168">Просто поместите два символа `/` перед вызовом. Например: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-168">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="5b1ee-169">Задача</span><span class="sxs-lookup"><span data-stu-id="5b1ee-169">Challenge</span></span>

<span data-ttu-id="5b1ee-170">Попробуйте объединить некоторые идеи из этого и предыдущих занятий.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-170">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="5b1ee-171">Расширьте код с числами Фибоначчи, который вы создали.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-171">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="5b1ee-172">Попробуйте написать код для создания первых 20 чисел в последовательности.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-172">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="5b1ee-173">Подсказка: 20-е число Фибоначчи — 6765.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-173">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="5b1ee-174">Выполнение задачи</span><span class="sxs-lookup"><span data-stu-id="5b1ee-174">Complete challenge</span></span>

<span data-ttu-id="5b1ee-175">Пример решения можно [просмотреть в готовом примере кода на GitHub](https://github.com/dotnet/samples/tree/main/csharp/list-quickstart/Program.cs#L8-L16).</span><span class="sxs-lookup"><span data-stu-id="5b1ee-175">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/main/csharp/list-quickstart/Program.cs#L8-L16).</span></span>

<span data-ttu-id="5b1ee-176">При каждой итерации цикла суммируются два последних целых числа в списке. Полученное значение добавляется в список.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-176">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="5b1ee-177">Цикл повторяется, пока в список не будут добавлены 20 элементов.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-177">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="5b1ee-178">Поздравляем! Вы выполнили задачи в руководстве по спискам.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-178">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="5b1ee-179">Можете продолжить изучение [дополнительных](../../tutorials/intro-to-csharp/introduction-to-classes.md) руководств в своей среде разработки.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-179">You can continue with [additional](../../tutorials/intro-to-csharp/introduction-to-classes.md) tutorials in your own development environment.</span></span>

<span data-ttu-id="5b1ee-180">Дополнительные сведения о работе с типом `List` см. в статье [Коллекции и структуры данных](../../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="5b1ee-180">You can learn more about working with the `List` type in the .NET fundamentals article on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="5b1ee-181">Также в нем описаны многие другие типы коллекций.</span><span class="sxs-lookup"><span data-stu-id="5b1ee-181">You'll also learn about many other collection types.</span></span>
