---
title: Работа с коллекциями. Вводное руководство по C#
description: Это руководство по C# предоставляет для изучения примере коллекции списков.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 4ecd2cfebddf460d3766d708d2f6740bd1c6e29a
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585667"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="70253-103">Научитесь управлять коллекциями данных с использованием универсального типа списка</span><span class="sxs-lookup"><span data-stu-id="70253-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="70253-104">Это вводное руководство содержит общие сведения о языке C# и классе <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="70253-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="70253-105">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="70253-105">Prerequisites</span></span>

<span data-ttu-id="70253-106">Для работы с руководством вам потребуется компьютер, настроенный для разработки в локальной среде.</span><span class="sxs-lookup"><span data-stu-id="70253-106">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="70253-107">В Windows, Linux или macOS для создания, сборки и запуска приложений можно использовать .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="70253-107">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="70253-108">В Windows можно использовать Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="70253-108">On Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="70253-109">Инструкции по настройке см. в статье [Настройка локальной среды](local-environment.md).</span><span class="sxs-lookup"><span data-stu-id="70253-109">For setup instructions, see [Set up your local environment](local-environment.md).</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="70253-110">Пример простого списка</span><span class="sxs-lookup"><span data-stu-id="70253-110">A basic list example</span></span>

<span data-ttu-id="70253-111">Создайте каталог с именем *list-tutorial*.</span><span class="sxs-lookup"><span data-stu-id="70253-111">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="70253-112">Откройте этот каталог и выполните команду `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="70253-112">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="70253-113">Откройте *Program.cs* в любом редакторе и замените существующий код следующим:</span><span class="sxs-lookup"><span data-stu-id="70253-113">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

<span data-ttu-id="70253-114">Замените `<name>` собственным именем.</span><span class="sxs-lookup"><span data-stu-id="70253-114">Replace `<name>` with your name.</span></span> <span data-ttu-id="70253-115">Сохраните *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="70253-115">Save *Program.cs*.</span></span> <span data-ttu-id="70253-116">Введите в окне консоли команду `dotnet run` для тестирования.</span><span class="sxs-lookup"><span data-stu-id="70253-116">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="70253-117">Вы создали список строк, добавили три имени в этот список и вывели имена прописными буквами.</span><span class="sxs-lookup"><span data-stu-id="70253-117">You've created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="70253-118">Для циклического прохода по списку вы примените концепции, которые изучили в предыдущих руководствах.</span><span class="sxs-lookup"><span data-stu-id="70253-118">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="70253-119">В коде для отображения имен используется функция [интерполяции строк](../../language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="70253-119">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="70253-120">Если перед `string` добавить символ `$`, код C# можно внедрять в объявление строки.</span><span class="sxs-lookup"><span data-stu-id="70253-120">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="70253-121">Фактическая строка заменяет код C# генерируемым значением.</span><span class="sxs-lookup"><span data-stu-id="70253-121">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="70253-122">В этом примере она заменяет `{name.ToUpper()}` именами, буквы каждого из которых преобразованы в прописные, так как вызван метод <xref:System.String.ToUpper%2A>.</span><span class="sxs-lookup"><span data-stu-id="70253-122">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="70253-123">Продолжим изучение.</span><span class="sxs-lookup"><span data-stu-id="70253-123">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="70253-124">Изменение содержимого списка</span><span class="sxs-lookup"><span data-stu-id="70253-124">Modify list contents</span></span>

<span data-ttu-id="70253-125">В созданной коллекции используется тип <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="70253-125">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="70253-126">При применении такого типа сохраняются последовательности элементов.</span><span class="sxs-lookup"><span data-stu-id="70253-126">This type stores sequences of elements.</span></span> <span data-ttu-id="70253-127">Тип элементов указывается в угловых скобках.</span><span class="sxs-lookup"><span data-stu-id="70253-127">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="70253-128">Важный аспект типа <xref:System.Collections.Generic.List%601> — возможность увеличения или уменьшения, что позволяет добавлять или удалять элементы.</span><span class="sxs-lookup"><span data-stu-id="70253-128">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="70253-129">Добавьте следующий код в метод `Main` перед закрывающей фигурной скобкой `}`:</span><span class="sxs-lookup"><span data-stu-id="70253-129">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="70253-130">В конец списка добавлены еще два имени.</span><span class="sxs-lookup"><span data-stu-id="70253-130">You've added two more names to the end of the list.</span></span> <span data-ttu-id="70253-131">При этом одно имя удалено.</span><span class="sxs-lookup"><span data-stu-id="70253-131">You've also removed one as well.</span></span> <span data-ttu-id="70253-132">Сохраните файл и введите `dotnet run` для тестирования.</span><span class="sxs-lookup"><span data-stu-id="70253-132">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="70253-133"><xref:System.Collections.Generic.List%601> позволяет добавлять ссылки на отдельные элементы по **индексу**.</span><span class="sxs-lookup"><span data-stu-id="70253-133">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="70253-134">Поместите индекс между токенами `[` и `]` после имени списка.</span><span class="sxs-lookup"><span data-stu-id="70253-134">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="70253-135">Для первого индекса в C# используется значение 0.</span><span class="sxs-lookup"><span data-stu-id="70253-135">C# uses 0 for the first index.</span></span> <span data-ttu-id="70253-136">Добавьте следующий код сразу после добавленного фрагмента и протестируйте его:</span><span class="sxs-lookup"><span data-stu-id="70253-136">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="70253-137">Доступ к индексу за пределами списка получить невозможно.</span><span class="sxs-lookup"><span data-stu-id="70253-137">You can't access an index beyond the end of the list.</span></span> <span data-ttu-id="70253-138">Помните, что индексы начинаются с 0, поэтому максимальный допустимый индекс меньше, чем число элементов в списке.</span><span class="sxs-lookup"><span data-stu-id="70253-138">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="70253-139">Вы можете проверить, как долго в списке используется свойство <xref:System.Collections.Generic.List%601.Count%2A>.</span><span class="sxs-lookup"><span data-stu-id="70253-139">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="70253-140">Добавьте следующий код в конец метода Main:</span><span class="sxs-lookup"><span data-stu-id="70253-140">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="70253-141">Сохраните файл и еще раз введите `dotnet run`, чтобы просмотреть результаты.</span><span class="sxs-lookup"><span data-stu-id="70253-141">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="70253-142">Поиск по спискам и их сортировка</span><span class="sxs-lookup"><span data-stu-id="70253-142">Search and sort lists</span></span>

<span data-ttu-id="70253-143">В наших примерах используются сравнительно небольшие списки. Но приложения часто создают списки с гораздо большим количеством элементов, иногда они исчисляются в тысячах.</span><span class="sxs-lookup"><span data-stu-id="70253-143">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="70253-144">Чтобы найти элементы в таких больших коллекциях, необходимо выполнить поиск различных элементов по списку.</span><span class="sxs-lookup"><span data-stu-id="70253-144">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="70253-145">Метод <xref:System.Collections.Generic.List%601.IndexOf%2A> выполняет поиск элемента и возвращает его индекс.</span><span class="sxs-lookup"><span data-stu-id="70253-145">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="70253-146">Если элемент отсутствует в списке, `IndexOf` возвращает `-1`.</span><span class="sxs-lookup"><span data-stu-id="70253-146">If the item isn't in the list, `IndexOf` returns `-1`.</span></span> <span data-ttu-id="70253-147">Добавьте следующий код в конец метода `Main`:</span><span class="sxs-lookup"><span data-stu-id="70253-147">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="70253-148">Кроме того, можно сортировать элементы в списке.</span><span class="sxs-lookup"><span data-stu-id="70253-148">The items in your list can be sorted as well.</span></span> <span data-ttu-id="70253-149">Метод <xref:System.Collections.Generic.List%601.Sort%2A> сортирует все элементы списка в обычном порядке (строки — в алфавитном).</span><span class="sxs-lookup"><span data-stu-id="70253-149">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically for strings).</span></span> <span data-ttu-id="70253-150">Добавьте следующий код в конец метода `Main`:</span><span class="sxs-lookup"><span data-stu-id="70253-150">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="70253-151">Сохраните файл и введите `dotnet run`, чтобы протестировать последнюю версию.</span><span class="sxs-lookup"><span data-stu-id="70253-151">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="70253-152">Прежде чем перейти к следующему разделу, переместим текущий код в отдельный метод.</span><span class="sxs-lookup"><span data-stu-id="70253-152">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="70253-153">Это упростит начало работы с новым примером.</span><span class="sxs-lookup"><span data-stu-id="70253-153">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="70253-154">Переименуйте метод `Main` в `WorkingWithStrings` и запишите новый метод `Main`, который вызывает `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="70253-154">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="70253-155">В результате ваш код должен выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="70253-155">When you've finished, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        static void WorkingWithStrings()
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
    }
}
```

## <a name="lists-of-other-types"></a><span data-ttu-id="70253-156">Списки других типов</span><span class="sxs-lookup"><span data-stu-id="70253-156">Lists of other types</span></span>

<span data-ttu-id="70253-157">Вы уже использовали в списках тип `string`.</span><span class="sxs-lookup"><span data-stu-id="70253-157">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="70253-158">Создадим <xref:System.Collections.Generic.List%601> с использованием другого типа.</span><span class="sxs-lookup"><span data-stu-id="70253-158">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="70253-159">Сначала создадим набор чисел.</span><span class="sxs-lookup"><span data-stu-id="70253-159">Let's build a set of numbers.</span></span>

<span data-ttu-id="70253-160">Добавьте следующий код в конец нового метода `Main`:</span><span class="sxs-lookup"><span data-stu-id="70253-160">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="70253-161">Будет создан список целых чисел. Для первых двух целых чисел будет задано значение 1.</span><span class="sxs-lookup"><span data-stu-id="70253-161">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="70253-162">Это два первых значения *последовательности Фибоначчи*.</span><span class="sxs-lookup"><span data-stu-id="70253-162">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="70253-163">Каждое следующее число Фибоначчи — это сумма двух предыдущих чисел.</span><span class="sxs-lookup"><span data-stu-id="70253-163">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="70253-164">Добавьте этот код:</span><span class="sxs-lookup"><span data-stu-id="70253-164">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="70253-165">Сохраните файл и введите `dotnet run`, чтобы просмотреть результаты.</span><span class="sxs-lookup"><span data-stu-id="70253-165">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="70253-166">Для задач этого раздела вы можете закомментировать код, который вызывает `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="70253-166">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="70253-167">Просто поместите два символа `/` перед вызовом. Например: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="70253-167">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="70253-168">Задача</span><span class="sxs-lookup"><span data-stu-id="70253-168">Challenge</span></span>

<span data-ttu-id="70253-169">Попробуйте объединить некоторые идеи из этого и предыдущих занятий.</span><span class="sxs-lookup"><span data-stu-id="70253-169">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="70253-170">Расширьте код с числами Фибоначчи, который вы создали.</span><span class="sxs-lookup"><span data-stu-id="70253-170">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="70253-171">Попробуйте написать код для создания первых 20 чисел в последовательности.</span><span class="sxs-lookup"><span data-stu-id="70253-171">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="70253-172">Подсказка: 20-е число Фибоначчи — 6765.</span><span class="sxs-lookup"><span data-stu-id="70253-172">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="70253-173">Выполнение задачи</span><span class="sxs-lookup"><span data-stu-id="70253-173">Complete challenge</span></span>

<span data-ttu-id="70253-174">Пример решения можно [просмотреть в готовом примере кода на GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span><span class="sxs-lookup"><span data-stu-id="70253-174">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span></span>

<span data-ttu-id="70253-175">При каждой итерации цикла суммируются два последних целых числа в списке. Полученное значение добавляется в список.</span><span class="sxs-lookup"><span data-stu-id="70253-175">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="70253-176">Цикл повторяется, пока в список не будут добавлены 20 элементов.</span><span class="sxs-lookup"><span data-stu-id="70253-176">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="70253-177">Поздравляем! Вы выполнили задачи в руководстве по спискам.</span><span class="sxs-lookup"><span data-stu-id="70253-177">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="70253-178">Теперь вы можете выполнить задачи [вводного руководства по классам](introduction-to-classes.md) в своей среде разработки.</span><span class="sxs-lookup"><span data-stu-id="70253-178">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="70253-179">Дополнительные сведения о работе с типом `List` см. в статье [Коллекции и структуры данных](../../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="70253-179">You can learn more about working with the `List` type in the .NET fundamentals article on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="70253-180">Также в нем описаны многие другие типы коллекций.</span><span class="sxs-lookup"><span data-stu-id="70253-180">You'll also learn about many other collection types.</span></span>
