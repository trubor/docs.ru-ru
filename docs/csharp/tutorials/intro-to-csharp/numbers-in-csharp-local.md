---
title: Числа в C#. Вводное руководство по C#
description: Изучите C# на примере числовых типов, их использования, свойств и методов.
ms.date: 02/02/2021
ms.custom: mvc
ms.openlocfilehash: 253ecbc089722961013d058aff900bdde23fd366
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585641"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="d2d16-103">Управление целыми числами и числами с плавающей запятой в C\#</span><span class="sxs-lookup"><span data-stu-id="d2d16-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="d2d16-104">Это руководство поможет в интерактивном изучении числовых типов в C#.</span><span class="sxs-lookup"><span data-stu-id="d2d16-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="d2d16-105">Вы напишете небольшие фрагменты кода, затем скомпилируете и выполните этот код.</span><span class="sxs-lookup"><span data-stu-id="d2d16-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="d2d16-106">Руководство содержит ряд уроков, в которых рассматриваются числа и математические операции в C#.</span><span class="sxs-lookup"><span data-stu-id="d2d16-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="d2d16-107">В рамках этих занятий вы ознакомитесь с основами языка C#.</span><span class="sxs-lookup"><span data-stu-id="d2d16-107">These lessons teach you the fundamentals of the C# language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d2d16-108">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="d2d16-108">Prerequisites</span></span>

<span data-ttu-id="d2d16-109">Для работы с руководством вам потребуется компьютер, настроенный для разработки в локальной среде.</span><span class="sxs-lookup"><span data-stu-id="d2d16-109">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="d2d16-110">В Windows, Linux или macOS для создания, сборки и запуска приложений можно использовать .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="d2d16-110">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="d2d16-111">В Windows можно использовать Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="d2d16-111">On Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="d2d16-112">Инструкции по настройке см. в статье [Настройка локальной среды](local-environment.md).</span><span class="sxs-lookup"><span data-stu-id="d2d16-112">For setup instructions, see [Set up your local environment](local-environment.md).</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="d2d16-113">Вычисления с целыми числами</span><span class="sxs-lookup"><span data-stu-id="d2d16-113">Explore integer math</span></span>

<span data-ttu-id="d2d16-114">Создайте каталог с именем *numbers-quickstart*.</span><span class="sxs-lookup"><span data-stu-id="d2d16-114">Create a directory named *numbers-quickstart*.</span></span> <span data-ttu-id="d2d16-115">Сделайте его текущим, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="d2d16-115">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

<span data-ttu-id="d2d16-116">Откройте файл *Program.cs* в любом редакторе и замените строку `Console.WriteLine("Hello World!");` следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="d2d16-116">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="d2d16-117">Чтобы выполнить этот код, введите `dotnet run` в окно командной строки.</span><span class="sxs-lookup"><span data-stu-id="d2d16-117">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="d2d16-118">Вы увидели одну из основных математических операций с целыми числами.</span><span class="sxs-lookup"><span data-stu-id="d2d16-118">You've seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="d2d16-119">Тип `int` представляет **целое** положительное или отрицательное число или ноль.</span><span class="sxs-lookup"><span data-stu-id="d2d16-119">The `int` type represents an **integer**, a zero, positive, or negative whole number.</span></span> <span data-ttu-id="d2d16-120">Для сложения используйте символ `+`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-120">You use the `+` symbol for addition.</span></span> <span data-ttu-id="d2d16-121">Другие стандартные математические операции с целыми числами включают:</span><span class="sxs-lookup"><span data-stu-id="d2d16-121">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="d2d16-122">`-` — вычитание;</span><span class="sxs-lookup"><span data-stu-id="d2d16-122">`-` for subtraction</span></span>
- <span data-ttu-id="d2d16-123">`*` — умножение;</span><span class="sxs-lookup"><span data-stu-id="d2d16-123">`*` for multiplication</span></span>
- <span data-ttu-id="d2d16-124">`/` — деление.</span><span class="sxs-lookup"><span data-stu-id="d2d16-124">`/` for division</span></span>

<span data-ttu-id="d2d16-125">Начните с ознакомления с различными операциями.</span><span class="sxs-lookup"><span data-stu-id="d2d16-125">Start by exploring those different operations.</span></span> <span data-ttu-id="d2d16-126">Добавьте следующие строки после строки, с помощью которой записывается значение `c`:</span><span class="sxs-lookup"><span data-stu-id="d2d16-126">Add these lines after the line that writes the value of `c`:</span></span>

```csharp

// subtraction
c = a - b;
Console.WriteLine(c);

// multiplication
c = a * b;
Console.WriteLine(c);

// division
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="d2d16-127">Чтобы выполнить этот код, введите `dotnet run` в окно командной строки.</span><span class="sxs-lookup"><span data-stu-id="d2d16-127">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="d2d16-128">Можно также поэкспериментировать, написав несколько математических операций в одной строке.</span><span class="sxs-lookup"><span data-stu-id="d2d16-128">You can also experiment by writing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="d2d16-129">Например, выполните `c = a + b - 12 * 17;`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-129">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="d2d16-130">Допускается сочетание переменных и постоянных чисел.</span><span class="sxs-lookup"><span data-stu-id="d2d16-130">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="d2d16-131">Вероятнее всего, при изучении C# (как и любого другого языка программирования) вы будете допускать ошибки в коде.</span><span class="sxs-lookup"><span data-stu-id="d2d16-131">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="d2d16-132">**Компилятор** найдет эти ошибки и сообщит вам о них.</span><span class="sxs-lookup"><span data-stu-id="d2d16-132">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="d2d16-133">Если результат содержит сообщения об ошибках, внимательно просмотрите пример кода и код в окне, чтобы понять, что нужно исправить.</span><span class="sxs-lookup"><span data-stu-id="d2d16-133">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="d2d16-134">Это упражнение поможет вам изучить структуру кода C#.</span><span class="sxs-lookup"><span data-stu-id="d2d16-134">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="d2d16-135">Вы завершили первый этап.</span><span class="sxs-lookup"><span data-stu-id="d2d16-135">You've finished the first step.</span></span> <span data-ttu-id="d2d16-136">Прежде чем перейти к следующему разделу, переместим текущий код в отдельный метод.</span><span class="sxs-lookup"><span data-stu-id="d2d16-136">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="d2d16-137">Это упростит начало работы с новым примером.</span><span class="sxs-lookup"><span data-stu-id="d2d16-137">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="d2d16-138">Переименуйте метод `Main` в `WorkingWithIntegers` и запишите новый метод `Main`, который вызывает `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-138">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="d2d16-139">В результате ваш код должен выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d2d16-139">When you finish, your code should look like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;

            // addition
            int c = a + b;
            Console.WriteLine(c);

            // subtraction
            c = a - b;
            Console.WriteLine(c);

            // multiplication
            c = a * b;
            Console.WriteLine(c);

            // division
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a><span data-ttu-id="d2d16-140">Изучение порядка операций</span><span class="sxs-lookup"><span data-stu-id="d2d16-140">Explore order of operations</span></span>

<span data-ttu-id="d2d16-141">Закомментируйте вызов `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-141">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="d2d16-142">Это поможет упорядочить выходные данные в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="d2d16-142">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="d2d16-143">`//` запускает **комментарий** в C#.</span><span class="sxs-lookup"><span data-stu-id="d2d16-143">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="d2d16-144">Комментарии — это любой текст, который должен быть сохранен в исходном коде, но не должен выполняться как код.</span><span class="sxs-lookup"><span data-stu-id="d2d16-144">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="d2d16-145">Компилятор не создает исполняемый код из комментариев.</span><span class="sxs-lookup"><span data-stu-id="d2d16-145">The compiler doesn't generate any executable code from comments.</span></span>

<span data-ttu-id="d2d16-146">Язык C# определяет приоритет математических операций в соответствии с правилами математики.</span><span class="sxs-lookup"><span data-stu-id="d2d16-146">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="d2d16-147">Умножение и деление имеют приоритет над сложением и вычитанием.</span><span class="sxs-lookup"><span data-stu-id="d2d16-147">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="d2d16-148">Чтобы удостовериться в этом, добавьте следующий код в метод `Main` и выполните команду `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="d2d16-148">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="d2d16-149">В выходных данных видно, что умножение выполняется раньше сложения.</span><span class="sxs-lookup"><span data-stu-id="d2d16-149">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="d2d16-150">Можно применить другую последовательность операций. Для этого операции, которые должны выполняться первыми, нужно заключить в скобки.</span><span class="sxs-lookup"><span data-stu-id="d2d16-150">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="d2d16-151">Добавьте приведенные ниже строки и выполните код еще раз.</span><span class="sxs-lookup"><span data-stu-id="d2d16-151">Add the following lines and run again:</span></span>

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="d2d16-152">Поэкспериментируйте, объединяя различные операции.</span><span class="sxs-lookup"><span data-stu-id="d2d16-152">Explore more by combining many different operations.</span></span> <span data-ttu-id="d2d16-153">Добавьте в конец метода `Main` строки, подобные приведенным ниже.</span><span class="sxs-lookup"><span data-stu-id="d2d16-153">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="d2d16-154">Выполните `dotnet run` еще раз.</span><span class="sxs-lookup"><span data-stu-id="d2d16-154">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="d2d16-155">Возможно, вы заметили интересное поведение целых чисел.</span><span class="sxs-lookup"><span data-stu-id="d2d16-155">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="d2d16-156">Деление целых чисел всегда дает результат в виде целого числа, даже если ожидаемый результат содержит десятичную или дробную часть.</span><span class="sxs-lookup"><span data-stu-id="d2d16-156">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="d2d16-157">Если вы еще не видели пример такого поведения, добавьте следующий код в конец метода `Main`:</span><span class="sxs-lookup"><span data-stu-id="d2d16-157">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="d2d16-158">Выполните `dotnet run` еще раз, чтобы просмотреть результаты.</span><span class="sxs-lookup"><span data-stu-id="d2d16-158">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="d2d16-159">Прежде чем продолжить, давайте поместив весь код, который вы написали в этом разделе, в новый метод.</span><span class="sxs-lookup"><span data-stu-id="d2d16-159">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="d2d16-160">Вызовите этот новый метод `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-160">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="d2d16-161">Результат должен быть примерно таким:</span><span class="sxs-lookup"><span data-stu-id="d2d16-161">You should write something like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;

            // addition
            int c = a + b;
            Console.WriteLine(c);

            // subtraction
            c = a - b;
            Console.WriteLine(c);

            // multiplication
            c = a * b;
            Console.WriteLine(c);

            // division
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="d2d16-162">Изучение точности и ограничений для целых чисел</span><span class="sxs-lookup"><span data-stu-id="d2d16-162">Explore integer precision and limits</span></span>

<span data-ttu-id="d2d16-163">В последнем примере вы увидели, что при делении целых чисел результат усекается.</span><span class="sxs-lookup"><span data-stu-id="d2d16-163">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="d2d16-164">Вы можете получить **остаток** с помощью оператора **остатка от деления**, который обозначается символом `%`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-164">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="d2d16-165">Попробуйте добавить приведенный ниже код в метод `Main`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-165">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="d2d16-166">Тип целых чисел C# характеризуется еще одним отличием от математических целых: тип `int` имеет минимальные и максимальные ограничения.</span><span class="sxs-lookup"><span data-stu-id="d2d16-166">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="d2d16-167">Добавьте следующий код в метод `Main`, чтобы просмотреть эти ограничения:</span><span class="sxs-lookup"><span data-stu-id="d2d16-167">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="d2d16-168">Если при вычислении выводится значение вне этих пределов, возникает условие **потери значимости** или **переполнения**.</span><span class="sxs-lookup"><span data-stu-id="d2d16-168">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="d2d16-169">Ответ должен находиться в диапазоне от минимального до максимального значения.</span><span class="sxs-lookup"><span data-stu-id="d2d16-169">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="d2d16-170">Добавьте следующие две строки в метод `Main`, чтобы увидеть пример:</span><span class="sxs-lookup"><span data-stu-id="d2d16-170">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="d2d16-171">Обратите внимание, что ответ очень близок к минимальному целому числу (отрицательное значение).</span><span class="sxs-lookup"><span data-stu-id="d2d16-171">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="d2d16-172">Он совпадает со значением `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-172">It's the same as `min + 2`.</span></span>
<span data-ttu-id="d2d16-173">Оператор сложения **вызвал переполнение** допустимых значений для целых чисел.</span><span class="sxs-lookup"><span data-stu-id="d2d16-173">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="d2d16-174">Ответ является очень большим отрицательным числом, так как переполнение покрывает диапазон от наибольшего целого числа до наименьшего.</span><span class="sxs-lookup"><span data-stu-id="d2d16-174">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="d2d16-175">Существуют другие числовые типы с различными ограничениями и точностью, которые можно использовать, если тип `int` не соответствует вашим требованиям.</span><span class="sxs-lookup"><span data-stu-id="d2d16-175">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="d2d16-176">Далее рассмотрим другие типы.</span><span class="sxs-lookup"><span data-stu-id="d2d16-176">Let's explore those other types next.</span></span>

<span data-ttu-id="d2d16-177">Давайте еще раз переместим код, написанный в этом разделе, в отдельный метод.</span><span class="sxs-lookup"><span data-stu-id="d2d16-177">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="d2d16-178">Присвойте обработчику события имя `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-178">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="d2d16-179">Работа с типом double</span><span class="sxs-lookup"><span data-stu-id="d2d16-179">Work with the double type</span></span>

<span data-ttu-id="d2d16-180">Числовой тип `double` представляет число с плавающей запятой двойной точности.</span><span class="sxs-lookup"><span data-stu-id="d2d16-180">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="d2d16-181">Эти термины могут быть новыми для вас.</span><span class="sxs-lookup"><span data-stu-id="d2d16-181">Those terms may be new to you.</span></span> <span data-ttu-id="d2d16-182">Число **с плавающей запятой** можно использовать для представления нецелых чисел, которые могут быть очень большими или малыми.</span><span class="sxs-lookup"><span data-stu-id="d2d16-182">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="d2d16-183">**Число двойной точности** — это относительный термин, описывающий количество двоичных разрядов, используемых для хранения значения.</span><span class="sxs-lookup"><span data-stu-id="d2d16-183">**Double-precision** is a relative term that describes the number of binary digits used to store the value.</span></span> <span data-ttu-id="d2d16-184">**Числа двойной точности** имеют в два раза больше двоичных символов по сравнению с **числами одиночной точности**.</span><span class="sxs-lookup"><span data-stu-id="d2d16-184">**Double precision** numbers have twice the number of binary digits as **single-precision**.</span></span> <span data-ttu-id="d2d16-185">На современных компьютерах числа двойной точности используются чаще, чем одиночной.</span><span class="sxs-lookup"><span data-stu-id="d2d16-185">On modern computers, it's more common to use double precision than single precision numbers.</span></span> <span data-ttu-id="d2d16-186">**Числа одиночной точности** объявляются с помощью ключевого слова `float`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-186">**Single precision** numbers are declared using the `float` keyword.</span></span>
<span data-ttu-id="d2d16-187">Рассмотрим их.</span><span class="sxs-lookup"><span data-stu-id="d2d16-187">Let's explore.</span></span> <span data-ttu-id="d2d16-188">Добавьте следующий код и просмотрите результат:</span><span class="sxs-lookup"><span data-stu-id="d2d16-188">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="d2d16-189">Обратите внимание, что ответ включает десятичную долю частного.</span><span class="sxs-lookup"><span data-stu-id="d2d16-189">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="d2d16-190">Попробуйте более сложное выражение с типом double:</span><span class="sxs-lookup"><span data-stu-id="d2d16-190">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="d2d16-191">Диапазон значений типа double гораздо больше, чем диапазон значений целых чисел.</span><span class="sxs-lookup"><span data-stu-id="d2d16-191">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="d2d16-192">Добавьте следующий фрагмент после написанного кода:</span><span class="sxs-lookup"><span data-stu-id="d2d16-192">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="d2d16-193">Значения выводятся в экспоненциальном представлении.</span><span class="sxs-lookup"><span data-stu-id="d2d16-193">These values are printed out in scientific notation.</span></span> <span data-ttu-id="d2d16-194">Число слева от символа `E` является значащим.</span><span class="sxs-lookup"><span data-stu-id="d2d16-194">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="d2d16-195">Число справа — это показатель степени, который равен 10.</span><span class="sxs-lookup"><span data-stu-id="d2d16-195">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="d2d16-196">Так же, как десятичные числа в математике, значения double в C# могут содержать ошибки округления.</span><span class="sxs-lookup"><span data-stu-id="d2d16-196">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="d2d16-197">Выполните этот код:</span><span class="sxs-lookup"><span data-stu-id="d2d16-197">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="d2d16-198">Вы знаете, что периодическая десятичная дробь `0.3` не равняется `1/3`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-198">You know that `0.3` repeating isn't exactly the same as `1/3`.</span></span>

<span data-ttu-id="d2d16-199">***Задача***</span><span class="sxs-lookup"><span data-stu-id="d2d16-199">***Challenge***</span></span>

<span data-ttu-id="d2d16-200">Выполните другие вычисления с большими числами, малыми числами, умножением и делением с помощью типа `double`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-200">Try other calculations with large numbers, small numbers, multiplication, and division using the `double` type.</span></span> <span data-ttu-id="d2d16-201">Попробуйте выполнить более сложные вычисления.</span><span class="sxs-lookup"><span data-stu-id="d2d16-201">Try more complicated calculations.</span></span>

<span data-ttu-id="d2d16-202">После того как вы решите сложную задачу, поместите написанный код в новый метод.</span><span class="sxs-lookup"><span data-stu-id="d2d16-202">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="d2d16-203">Присвойте этому методу имя `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-203">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-decimal-types"></a><span data-ttu-id="d2d16-204">Работа с десятичными типами</span><span class="sxs-lookup"><span data-stu-id="d2d16-204">Work with decimal types</span></span>

<span data-ttu-id="d2d16-205">Вы уже ознакомились с базовыми числовыми типами в C# — целыми числами и числами типа double.</span><span class="sxs-lookup"><span data-stu-id="d2d16-205">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="d2d16-206">Осталось изучить еще один тип: `decimal`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-206">There's one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="d2d16-207">Тип `decimal` имеет меньший диапазон, но большую точность, чем `double`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-207">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="d2d16-208">Например:</span><span class="sxs-lookup"><span data-stu-id="d2d16-208">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="d2d16-209">Обратите внимание, что диапазон меньше, чем для типа `double`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-209">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="d2d16-210">Вы можете убедиться в повышении точности при использовании типа decimal, выполнив следующий код:</span><span class="sxs-lookup"><span data-stu-id="d2d16-210">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="d2d16-211">Суффикс `M` возле чисел указывает, что для константы должен использоваться тип `decimal`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-211">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span> <span data-ttu-id="d2d16-212">В противном случае компилятор предполагает тип `double`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-212">Otherwise, the compiler assumes the `double` type.</span></span>

> [!NOTE]
> <span data-ttu-id="d2d16-213">Буква `M` была выбрана потому, что визуально показывает различия между ключевыми словами `double` и `decimal`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-213">The letter `M` was chosen as the most visually distinct letter between the `double` and `decimal` keywords.</span></span>

<span data-ttu-id="d2d16-214">Обратите внимание, что при вычислении с использованием типа decimal справа от запятой содержится больше цифр.</span><span class="sxs-lookup"><span data-stu-id="d2d16-214">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="d2d16-215">***Задача***</span><span class="sxs-lookup"><span data-stu-id="d2d16-215">***Challenge***</span></span>

<span data-ttu-id="d2d16-216">Теперь, когда вы ознакомились с разными числовыми типами, напишите код, который позволяет вычислить площадь круга с радиусом 2,50 см.</span><span class="sxs-lookup"><span data-stu-id="d2d16-216">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="d2d16-217">Помните, что площадь круга равна квадрату радиуса, умноженному на число пи.</span><span class="sxs-lookup"><span data-stu-id="d2d16-217">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="d2d16-218">Подсказка: в .NET есть константа пи <xref:System.Math.PI?displayProperty=nameWithType>, которую можно использовать.</span><span class="sxs-lookup"><span data-stu-id="d2d16-218">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> <span data-ttu-id="d2d16-219"><xref:System.Math.PI?displayProperty=nameWithType>, как и все константы, объявленные в пространстве имен `System.Math`, — это значение `double`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-219"><xref:System.Math.PI?displayProperty=nameWithType>, like all constants declared in the `System.Math` namespace, is a `double` value.</span></span> <span data-ttu-id="d2d16-220">По этой причине вместо значений `decimal` для этой задачи следует использовать `double`.</span><span class="sxs-lookup"><span data-stu-id="d2d16-220">For that reason, you should use `double` instead of `decimal` values for this challenge.</span></span>

<span data-ttu-id="d2d16-221">Вы должны получить ответ от 19 до 20.</span><span class="sxs-lookup"><span data-stu-id="d2d16-221">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="d2d16-222">Ответ можно [просмотреть в готовом примере кода на GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).</span><span class="sxs-lookup"><span data-stu-id="d2d16-222">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).</span></span>

<span data-ttu-id="d2d16-223">При желании поэкспериментируйте с другими формулами.</span><span class="sxs-lookup"><span data-stu-id="d2d16-223">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="d2d16-224">Вы выполнили все задачи краткого руководства по числам в C#.</span><span class="sxs-lookup"><span data-stu-id="d2d16-224">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="d2d16-225">Теперь вы можете выполнить руководство по [ветвям и циклам](branches-and-loops-local.md) в своей среде разработки.</span><span class="sxs-lookup"><span data-stu-id="d2d16-225">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="d2d16-226">Дополнительные сведения о числах в C# см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="d2d16-226">You can learn more about numbers in C# in the following articles:</span></span>

- [<span data-ttu-id="d2d16-227">Целочисленные типы</span><span class="sxs-lookup"><span data-stu-id="d2d16-227">Integral numeric types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="d2d16-228">Числовые типы с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="d2d16-228">Floating-point numeric types</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="d2d16-229">Встроенные числовые преобразования</span><span class="sxs-lookup"><span data-stu-id="d2d16-229">Built-in numeric conversions</span></span>](../../language-reference/builtin-types/numeric-conversions.md)
