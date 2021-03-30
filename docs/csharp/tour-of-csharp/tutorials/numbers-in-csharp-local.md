---
title: Числа в C#. Вводное руководство по C#
description: Изучите C# на примере числовых типов, их использования, свойств и методов.
ms.date: 02/05/2021
ms.openlocfilehash: d6546fc8ac2609066a4f9b829749a4091fce7ce6
ms.sourcegitcommit: 5ce37699c2a51ed173171813be68ef7577b1aba5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881111"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="8c46e-103">Управление целыми числами и числами с плавающей запятой в C\#</span><span class="sxs-lookup"><span data-stu-id="8c46e-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="8c46e-104">Это руководство поможет в интерактивном изучении числовых типов в C#.</span><span class="sxs-lookup"><span data-stu-id="8c46e-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="8c46e-105">Вы напишете небольшие фрагменты кода, затем скомпилируете и выполните этот код.</span><span class="sxs-lookup"><span data-stu-id="8c46e-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="8c46e-106">Руководство содержит ряд уроков, в которых рассматриваются числа и математические операции в C#.</span><span class="sxs-lookup"><span data-stu-id="8c46e-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="8c46e-107">В рамках этих занятий вы ознакомитесь с основами языка C#.</span><span class="sxs-lookup"><span data-stu-id="8c46e-107">These lessons teach you the fundamentals of the C# language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8c46e-108">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="8c46e-108">Prerequisites</span></span>

<span data-ttu-id="8c46e-109">Для работы с руководством вам потребуется компьютер, настроенный для разработки в локальной среде.</span><span class="sxs-lookup"><span data-stu-id="8c46e-109">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="8c46e-110">В Windows, Linux или macOS для создания, сборки и запуска приложений можно использовать .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="8c46e-110">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="8c46e-111">Для Mac или Windows можно использовать Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="8c46e-111">On Mac or Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="8c46e-112">Инструкции по настройке см. в статье [Настройка локальной среды](local-environment.md).</span><span class="sxs-lookup"><span data-stu-id="8c46e-112">For setup instructions, see [Set up your local environment](local-environment.md).</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="8c46e-113">Вычисления с целыми числами</span><span class="sxs-lookup"><span data-stu-id="8c46e-113">Explore integer math</span></span>

<span data-ttu-id="8c46e-114">Создайте каталог с именем *numbers-quickstart*.</span><span class="sxs-lookup"><span data-stu-id="8c46e-114">Create a directory named *numbers-quickstart*.</span></span> <span data-ttu-id="8c46e-115">Сделайте его текущим и выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="8c46e-115">Make it the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

<span data-ttu-id="8c46e-116">Откройте файл *Program.cs* в любом редакторе и замените содержимое файла следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="8c46e-116">Open *Program.cs* in your favorite editor, and replace the contents of the file with the following code:</span></span>

```csharp
using System;

int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="8c46e-117">Чтобы выполнить этот код, введите `dotnet run` в окно командной строки.</span><span class="sxs-lookup"><span data-stu-id="8c46e-117">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="8c46e-118">Вы увидели одну из основных математических операций с целыми числами.</span><span class="sxs-lookup"><span data-stu-id="8c46e-118">You've seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="8c46e-119">Тип `int` представляет **целое** положительное или отрицательное число или ноль.</span><span class="sxs-lookup"><span data-stu-id="8c46e-119">The `int` type represents an **integer**, a zero, positive, or negative whole number.</span></span> <span data-ttu-id="8c46e-120">Для сложения используйте символ `+`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-120">You use the `+` symbol for addition.</span></span> <span data-ttu-id="8c46e-121">Другие стандартные математические операции с целыми числами включают:</span><span class="sxs-lookup"><span data-stu-id="8c46e-121">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="8c46e-122">`-` — вычитание;</span><span class="sxs-lookup"><span data-stu-id="8c46e-122">`-` for subtraction</span></span>
- <span data-ttu-id="8c46e-123">`*` — умножение;</span><span class="sxs-lookup"><span data-stu-id="8c46e-123">`*` for multiplication</span></span>
- <span data-ttu-id="8c46e-124">`/` — деление.</span><span class="sxs-lookup"><span data-stu-id="8c46e-124">`/` for division</span></span>

<span data-ttu-id="8c46e-125">Начните с ознакомления с различными операциями.</span><span class="sxs-lookup"><span data-stu-id="8c46e-125">Start by exploring those different operations.</span></span> <span data-ttu-id="8c46e-126">Добавьте следующие строки после строки, с помощью которой записывается значение `c`:</span><span class="sxs-lookup"><span data-stu-id="8c46e-126">Add these lines after the line that writes the value of `c`:</span></span>

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

<span data-ttu-id="8c46e-127">Чтобы выполнить этот код, введите `dotnet run` в окно командной строки.</span><span class="sxs-lookup"><span data-stu-id="8c46e-127">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="8c46e-128">Можно также поэкспериментировать, написав несколько математических операций в одной строке.</span><span class="sxs-lookup"><span data-stu-id="8c46e-128">You can also experiment by writing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="8c46e-129">Например, выполните `c = a + b - 12 * 17;`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-129">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="8c46e-130">Допускается сочетание переменных и постоянных чисел.</span><span class="sxs-lookup"><span data-stu-id="8c46e-130">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="8c46e-131">Вероятнее всего, при изучении C# (как и любого другого языка программирования) вы будете допускать ошибки в коде.</span><span class="sxs-lookup"><span data-stu-id="8c46e-131">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="8c46e-132">**Компилятор** найдет эти ошибки и сообщит вам о них.</span><span class="sxs-lookup"><span data-stu-id="8c46e-132">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="8c46e-133">Если результат содержит сообщения об ошибках, внимательно просмотрите пример кода и код в окне, чтобы понять, что нужно исправить.</span><span class="sxs-lookup"><span data-stu-id="8c46e-133">When the contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span> <span data-ttu-id="8c46e-134">Это упражнение поможет вам изучить структуру кода C#.</span><span class="sxs-lookup"><span data-stu-id="8c46e-134">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="8c46e-135">Вы завершили первый этап.</span><span class="sxs-lookup"><span data-stu-id="8c46e-135">You've finished the first step.</span></span> <span data-ttu-id="8c46e-136">Прежде чем перейти к следующему разделу, переместим текущий код в отдельный *метод*.</span><span class="sxs-lookup"><span data-stu-id="8c46e-136">Before you start the next section, let's move the current code into a separate *method*.</span></span> <span data-ttu-id="8c46e-137">Метод — это последовательность инструкций, сгруппированных под одним именем.</span><span class="sxs-lookup"><span data-stu-id="8c46e-137">A method is a series of statements grouped together and given a name.</span></span> <span data-ttu-id="8c46e-138">Чтобы вызвать метод, нужно указать имя метода и `()` после него.</span><span class="sxs-lookup"><span data-stu-id="8c46e-138">You call a method by writing the method's name followed by `()`.</span></span> <span data-ttu-id="8c46e-139">Упорядочение кода в методы упростит работу с новым примером.</span><span class="sxs-lookup"><span data-stu-id="8c46e-139">Organizing your code into methods makes it easier to start working with a new example.</span></span> <span data-ttu-id="8c46e-140">В результате ваш код должен выглядеть примерно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8c46e-140">When you finish, your code should look like this:</span></span>

```csharp
using System;

WorkWithIntegers();

void WorkWithIntegers()
{
    int a = 18;
    int b = 6;
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
```

<span data-ttu-id="8c46e-141">Строка `WorkWithIntegers();` вызывает метод.</span><span class="sxs-lookup"><span data-stu-id="8c46e-141">The line `WorkWithIntegers();` invokes the method.</span></span> <span data-ttu-id="8c46e-142">Код после этой строки объявляет метод и определяет его.</span><span class="sxs-lookup"><span data-stu-id="8c46e-142">The following code declares the method and defines it.</span></span>

## <a name="explore-order-of-operations"></a><span data-ttu-id="8c46e-143">Изучение порядка операций</span><span class="sxs-lookup"><span data-stu-id="8c46e-143">Explore order of operations</span></span>

<span data-ttu-id="8c46e-144">Закомментируйте вызов `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-144">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="8c46e-145">Это поможет упорядочить выходные данные в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="8c46e-145">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkWithIntegers();
```

<span data-ttu-id="8c46e-146">`//` запускает **комментарий** в C#.</span><span class="sxs-lookup"><span data-stu-id="8c46e-146">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="8c46e-147">Комментарии — это любой текст, который должен быть сохранен в исходном коде, но не должен выполняться как код.</span><span class="sxs-lookup"><span data-stu-id="8c46e-147">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="8c46e-148">Компилятор не создает исполняемый код из комментариев.</span><span class="sxs-lookup"><span data-stu-id="8c46e-148">The compiler doesn't generate any executable code from comments.</span></span> <span data-ttu-id="8c46e-149">Так как `WorkWithIntegers()` является методом, необходимо закомментировать только одну строку.</span><span class="sxs-lookup"><span data-stu-id="8c46e-149">Because `WorkWithIntegers()` is a method, you need to only comment out one line.</span></span>

<span data-ttu-id="8c46e-150">Язык C# определяет приоритет математических операций в соответствии с правилами математики.</span><span class="sxs-lookup"><span data-stu-id="8c46e-150">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span> <span data-ttu-id="8c46e-151">Умножение и деление имеют приоритет над сложением и вычитанием.</span><span class="sxs-lookup"><span data-stu-id="8c46e-151">Multiplication and division take precedence over addition and subtraction.</span></span> <span data-ttu-id="8c46e-152">Убедитесь в этом, добавив следующий код после вызова `WorkWithIntegers()` и выполнив `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="8c46e-152">Explore that by adding the following code after the call to `WorkWithIntegers()`, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="8c46e-153">В выходных данных видно, что умножение выполняется раньше сложения.</span><span class="sxs-lookup"><span data-stu-id="8c46e-153">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="8c46e-154">Можно применить другую последовательность операций. Для этого операции, которые должны выполняться первыми, нужно заключить в скобки.</span><span class="sxs-lookup"><span data-stu-id="8c46e-154">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="8c46e-155">Добавьте приведенные ниже строки и выполните код еще раз.</span><span class="sxs-lookup"><span data-stu-id="8c46e-155">Add the following lines and run again:</span></span>

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="8c46e-156">Поэкспериментируйте, объединяя различные операции.</span><span class="sxs-lookup"><span data-stu-id="8c46e-156">Explore more by combining many different operations.</span></span> <span data-ttu-id="8c46e-157">Добавьте строки, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="8c46e-157">Add something like the following lines.</span></span> <span data-ttu-id="8c46e-158">Выполните `dotnet run` еще раз.</span><span class="sxs-lookup"><span data-stu-id="8c46e-158">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="8c46e-159">Возможно, вы заметили интересное поведение целых чисел.</span><span class="sxs-lookup"><span data-stu-id="8c46e-159">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="8c46e-160">Деление целых чисел всегда дает результат в виде целого числа, даже если ожидаемый результат содержит десятичную или дробную часть.</span><span class="sxs-lookup"><span data-stu-id="8c46e-160">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="8c46e-161">Если вы еще не видели пример такого поведения, выполните следующий код:</span><span class="sxs-lookup"><span data-stu-id="8c46e-161">If you haven't seen this behavior, try the following code:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="8c46e-162">Выполните `dotnet run` еще раз, чтобы просмотреть результаты.</span><span class="sxs-lookup"><span data-stu-id="8c46e-162">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="8c46e-163">Прежде чем продолжить, давайте поместив весь код, который вы написали в этом разделе, в новый метод.</span><span class="sxs-lookup"><span data-stu-id="8c46e-163">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="8c46e-164">Вызовите этот новый метод `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-164">Call that new method `OrderPrecedence`.</span></span> <span data-ttu-id="8c46e-165">Код должен выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8c46e-165">Your code should look something like this:</span></span>

```csharp
using System;

// WorkWithIntegers();
OrderPrecedence();

void WorkWithIntegers()
{
    int a = 18;
    int b = 6;
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

void OrderPrecedence()
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
    int h = (e + f) / g;
    Console.WriteLine(h);
}
```

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="8c46e-166">Изучение точности и ограничений для целых чисел</span><span class="sxs-lookup"><span data-stu-id="8c46e-166">Explore integer precision and limits</span></span>

<span data-ttu-id="8c46e-167">В последнем примере вы увидели, что при делении целых чисел результат усекается.</span><span class="sxs-lookup"><span data-stu-id="8c46e-167">That last sample showed you that integer division truncates the result.</span></span> <span data-ttu-id="8c46e-168">Вы можете получить **остаток** с помощью оператора **остатка от деления**, который обозначается символом `%`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-168">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="8c46e-169">Попробуйте выполнить следующий код после вызова метода `OrderPrecedence()`:</span><span class="sxs-lookup"><span data-stu-id="8c46e-169">Try the following code after the method call to `OrderPrecedence()`:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="8c46e-170">Тип целых чисел C# характеризуется еще одним отличием от математических целых: тип `int` имеет минимальные и максимальные ограничения.</span><span class="sxs-lookup"><span data-stu-id="8c46e-170">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="8c46e-171">Чтобы просмотреть эти ограничения, добавьте такой код:</span><span class="sxs-lookup"><span data-stu-id="8c46e-171">Add this code to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="8c46e-172">Если при вычислении выводится значение вне этих пределов, возникает условие **потери значимости** или **переполнения**.</span><span class="sxs-lookup"><span data-stu-id="8c46e-172">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="8c46e-173">Ответ должен находиться в диапазоне от минимального до максимального значения.</span><span class="sxs-lookup"><span data-stu-id="8c46e-173">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="8c46e-174">Добавьте следующие две строки, чтобы увидеть пример:</span><span class="sxs-lookup"><span data-stu-id="8c46e-174">Add these two lines to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="8c46e-175">Обратите внимание, что ответ очень близок к минимальному целому числу (отрицательное значение).</span><span class="sxs-lookup"><span data-stu-id="8c46e-175">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="8c46e-176">Он совпадает со значением `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-176">It's the same as `min + 2`.</span></span> <span data-ttu-id="8c46e-177">Оператор сложения **вызвал переполнение** допустимых значений для целых чисел.</span><span class="sxs-lookup"><span data-stu-id="8c46e-177">The addition operation **overflowed** the allowed values for integers.</span></span> <span data-ttu-id="8c46e-178">Ответ является очень большим отрицательным числом, так как переполнение покрывает диапазон от наибольшего целого числа до наименьшего.</span><span class="sxs-lookup"><span data-stu-id="8c46e-178">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="8c46e-179">Существуют другие числовые типы с различными ограничениями и точностью, которые можно использовать, если тип `int` не соответствует вашим требованиям.</span><span class="sxs-lookup"><span data-stu-id="8c46e-179">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="8c46e-180">Далее рассмотрим другие типы.</span><span class="sxs-lookup"><span data-stu-id="8c46e-180">Let's explore those other types next.</span></span> <span data-ttu-id="8c46e-181">Прежде чем перейти к следующему разделу, переместите код, написанный согласно инструкциям из этого раздела, в отдельный метод.</span><span class="sxs-lookup"><span data-stu-id="8c46e-181">Before you start the next section, move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="8c46e-182">Присвойте обработчику события имя `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-182">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="8c46e-183">Работа с типом double</span><span class="sxs-lookup"><span data-stu-id="8c46e-183">Work with the double type</span></span>

<span data-ttu-id="8c46e-184">Числовой тип `double` представляет число с плавающей запятой двойной точности.</span><span class="sxs-lookup"><span data-stu-id="8c46e-184">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="8c46e-185">Эти термины могут быть новыми для вас.</span><span class="sxs-lookup"><span data-stu-id="8c46e-185">Those terms may be new to you.</span></span> <span data-ttu-id="8c46e-186">Число **с плавающей запятой** можно использовать для представления нецелых чисел, которые могут быть очень большими или малыми.</span><span class="sxs-lookup"><span data-stu-id="8c46e-186">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="8c46e-187">**Число двойной точности** — это относительный термин, описывающий количество двоичных разрядов, используемых для хранения значения.</span><span class="sxs-lookup"><span data-stu-id="8c46e-187">**Double-precision** is a relative term that describes the number of binary digits used to store the value.</span></span> <span data-ttu-id="8c46e-188">**Числа двойной точности** имеют в два раза больше двоичных символов по сравнению с **числами одиночной точности**.</span><span class="sxs-lookup"><span data-stu-id="8c46e-188">**Double precision** numbers have twice the number of binary digits as **single-precision**.</span></span> <span data-ttu-id="8c46e-189">На современных компьютерах числа двойной точности используются чаще, чем одиночной.</span><span class="sxs-lookup"><span data-stu-id="8c46e-189">On modern computers, it's more common to use double precision than single precision numbers.</span></span> <span data-ttu-id="8c46e-190">**Числа одиночной точности** объявляются с помощью ключевого слова `float`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-190">**Single precision** numbers are declared using the `float` keyword.</span></span> <span data-ttu-id="8c46e-191">Рассмотрим их.</span><span class="sxs-lookup"><span data-stu-id="8c46e-191">Let's explore.</span></span> <span data-ttu-id="8c46e-192">Добавьте следующий код и просмотрите результат:</span><span class="sxs-lookup"><span data-stu-id="8c46e-192">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="8c46e-193">Обратите внимание, что ответ включает десятичную долю частного.</span><span class="sxs-lookup"><span data-stu-id="8c46e-193">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="8c46e-194">Попробуйте более сложное выражение с типом double:</span><span class="sxs-lookup"><span data-stu-id="8c46e-194">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="8c46e-195">Диапазон значений типа double гораздо больше, чем диапазон значений целых чисел.</span><span class="sxs-lookup"><span data-stu-id="8c46e-195">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="8c46e-196">Добавьте следующий фрагмент после написанного кода:</span><span class="sxs-lookup"><span data-stu-id="8c46e-196">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="8c46e-197">Значения выводятся в экспоненциальном представлении.</span><span class="sxs-lookup"><span data-stu-id="8c46e-197">These values are printed in scientific notation.</span></span> <span data-ttu-id="8c46e-198">Число слева от символа `E` является значащим.</span><span class="sxs-lookup"><span data-stu-id="8c46e-198">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="8c46e-199">Число справа — это показатель степени, который равен 10.</span><span class="sxs-lookup"><span data-stu-id="8c46e-199">The number to the right is the exponent, as a power of 10.</span></span> <span data-ttu-id="8c46e-200">Так же, как десятичные числа в математике, значения double в C# могут содержать ошибки округления.</span><span class="sxs-lookup"><span data-stu-id="8c46e-200">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="8c46e-201">Выполните этот код:</span><span class="sxs-lookup"><span data-stu-id="8c46e-201">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="8c46e-202">Вы знаете, что периодическая десятичная дробь `0.3` не равняется `1/3`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-202">You know that `0.3` repeating isn't exactly the same as `1/3`.</span></span>

<span data-ttu-id="8c46e-203">***Задача***</span><span class="sxs-lookup"><span data-stu-id="8c46e-203">***Challenge***</span></span>

<span data-ttu-id="8c46e-204">Выполните другие вычисления с большими числами, малыми числами, умножением и делением с помощью типа `double`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-204">Try other calculations with large numbers, small numbers, multiplication, and division using the `double` type.</span></span> <span data-ttu-id="8c46e-205">Попробуйте выполнить более сложные вычисления.</span><span class="sxs-lookup"><span data-stu-id="8c46e-205">Try more complicated calculations.</span></span> <span data-ttu-id="8c46e-206">После того как вы решите сложную задачу, поместите написанный код в новый метод.</span><span class="sxs-lookup"><span data-stu-id="8c46e-206">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="8c46e-207">Присвойте этому методу имя `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-207">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-decimal-types"></a><span data-ttu-id="8c46e-208">Работа с десятичными типами</span><span class="sxs-lookup"><span data-stu-id="8c46e-208">Work with decimal types</span></span>

<span data-ttu-id="8c46e-209">Вы уже ознакомились с базовыми числовыми типами в C# — целыми числами и числами типа double.</span><span class="sxs-lookup"><span data-stu-id="8c46e-209">You've seen the basic numeric types in C#: integers and doubles.</span></span> <span data-ttu-id="8c46e-210">Осталось изучить еще один тип: `decimal`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-210">There's one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="8c46e-211">Тип `decimal` имеет меньший диапазон, но большую точность, чем `double`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-211">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="8c46e-212">Например:</span><span class="sxs-lookup"><span data-stu-id="8c46e-212">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="8c46e-213">Обратите внимание, что диапазон меньше, чем для типа `double`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-213">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="8c46e-214">Вы можете убедиться в повышении точности при использовании типа decimal, выполнив следующий код:</span><span class="sxs-lookup"><span data-stu-id="8c46e-214">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="8c46e-215">Суффикс `M` возле чисел указывает, что для константы должен использоваться тип `decimal`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-215">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span> <span data-ttu-id="8c46e-216">В противном случае компилятор предполагает тип `double`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-216">Otherwise, the compiler assumes the `double` type.</span></span>

> [!NOTE]
> <span data-ttu-id="8c46e-217">Буква `M` была выбрана потому, что визуально показывает различия между ключевыми словами `double` и `decimal`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-217">The letter `M` was chosen as the most visually distinct letter between the `double` and `decimal` keywords.</span></span>

<span data-ttu-id="8c46e-218">Обратите внимание, что при вычислении с использованием типа decimal справа от запятой содержится больше цифр.</span><span class="sxs-lookup"><span data-stu-id="8c46e-218">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="8c46e-219">***Задача***</span><span class="sxs-lookup"><span data-stu-id="8c46e-219">***Challenge***</span></span>

<span data-ttu-id="8c46e-220">Теперь, когда вы ознакомились с разными числовыми типами, напишите код, который позволяет вычислить площадь круга с радиусом 2,50 см.</span><span class="sxs-lookup"><span data-stu-id="8c46e-220">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="8c46e-221">Помните, что площадь круга равна квадрату радиуса, умноженному на число пи.</span><span class="sxs-lookup"><span data-stu-id="8c46e-221">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="8c46e-222">Подсказка: в .NET есть константа пи <xref:System.Math.PI?displayProperty=nameWithType>, которую можно использовать.</span><span class="sxs-lookup"><span data-stu-id="8c46e-222">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> <span data-ttu-id="8c46e-223"><xref:System.Math.PI?displayProperty=nameWithType>, как и все константы, объявленные в пространстве имен `System.Math`, — это значение `double`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-223"><xref:System.Math.PI?displayProperty=nameWithType>, like all constants declared in the `System.Math` namespace, is a `double` value.</span></span> <span data-ttu-id="8c46e-224">По этой причине вместо значений `decimal` для этой задачи следует использовать `double`.</span><span class="sxs-lookup"><span data-stu-id="8c46e-224">For that reason, you should use `double` instead of `decimal` values for this challenge.</span></span>

<span data-ttu-id="8c46e-225">Вы должны получить ответ от 19 до 20.</span><span class="sxs-lookup"><span data-stu-id="8c46e-225">You should get an answer between 19 and 20.</span></span> <span data-ttu-id="8c46e-226">Ответ можно [просмотреть в готовом примере кода на GitHub](https://github.com/dotnet/samples/tree/main/csharp/numbers-quickstart/Program.cs#L9-L11).</span><span class="sxs-lookup"><span data-stu-id="8c46e-226">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/main/csharp/numbers-quickstart/Program.cs#L9-L11).</span></span>

<span data-ttu-id="8c46e-227">При желании поэкспериментируйте с другими формулами.</span><span class="sxs-lookup"><span data-stu-id="8c46e-227">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="8c46e-228">Вы выполнили все задачи краткого руководства по числам в C#.</span><span class="sxs-lookup"><span data-stu-id="8c46e-228">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="8c46e-229">Теперь вы можете выполнить руководство по [ветвям и циклам](branches-and-loops-local.md) в своей среде разработки.</span><span class="sxs-lookup"><span data-stu-id="8c46e-229">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="8c46e-230">Дополнительные сведения о числах в C# см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="8c46e-230">You can learn more about numbers in C# in the following articles:</span></span>

- [<span data-ttu-id="8c46e-231">Целочисленные типы</span><span class="sxs-lookup"><span data-stu-id="8c46e-231">Integral numeric types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="8c46e-232">Числовые типы с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="8c46e-232">Floating-point numeric types</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="8c46e-233">Встроенные числовые преобразования</span><span class="sxs-lookup"><span data-stu-id="8c46e-233">Built-in numeric conversions</span></span>](../../language-reference/builtin-types/numeric-conversions.md)
