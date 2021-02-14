---
title: Ветви и циклы. Вводное руководство по C#
description: В рамках этого руководства, посвященного ветвям и циклам, вы создадите пример кода на C#, который демонстрирует возможности языка для организации условного ветвления и циклического выполнения операторов.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 1c93c96217abf041b14b94aafcdfe85bb7018528
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585709"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="d7354-103">Изучение условной логики с операторами ветви и цикла</span><span class="sxs-lookup"><span data-stu-id="d7354-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="d7354-104">В этом руководстве объясняется, как написать код, который позволяет проверить переменные и изменить путь выполнения на основе этих переменных.</span><span class="sxs-lookup"><span data-stu-id="d7354-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="d7354-105">Вы напишете код C# и сможете просмотреть результаты его компиляции и выполнения.</span><span class="sxs-lookup"><span data-stu-id="d7354-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="d7354-106">Это руководство содержит ряд уроков, в которых рассматриваются конструкции ветвления и циклов в C#.</span><span class="sxs-lookup"><span data-stu-id="d7354-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="d7354-107">В рамках этих занятий вы ознакомитесь с основами языка C#.</span><span class="sxs-lookup"><span data-stu-id="d7354-107">These lessons teach you the fundamentals of the C# language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d7354-108">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="d7354-108">Prerequisites</span></span>

<span data-ttu-id="d7354-109">Для работы с руководством вам потребуется компьютер, настроенный для разработки в локальной среде.</span><span class="sxs-lookup"><span data-stu-id="d7354-109">The tutorial expects that you have a machine set up for local development.</span></span> <span data-ttu-id="d7354-110">В Windows, Linux или macOS для создания, сборки и запуска приложений можно использовать .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="d7354-110">On Windows, Linux, or macOS, you can use the .NET CLI to create, build, and run applications.</span></span> <span data-ttu-id="d7354-111">В Windows можно использовать Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="d7354-111">On Windows, you can use Visual Studio 2019.</span></span> <span data-ttu-id="d7354-112">Инструкции по настройке см. в статье [Настройка локальной среды](local-environment.md).</span><span class="sxs-lookup"><span data-stu-id="d7354-112">For setup instructions, see [Set up your local environment](local-environment.md).</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="d7354-113">Принятие решений с помощью оператора `if`</span><span class="sxs-lookup"><span data-stu-id="d7354-113">Make decisions using the `if` statement</span></span>

<span data-ttu-id="d7354-114">Создайте каталог с именем *branches-tutorial*.</span><span class="sxs-lookup"><span data-stu-id="d7354-114">Create a directory named *branches-tutorial*.</span></span> <span data-ttu-id="d7354-115">Сделайте его текущим, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="d7354-115">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

<span data-ttu-id="d7354-116">Эта команда создает консольное приложение .NET в текущем каталоге.</span><span class="sxs-lookup"><span data-stu-id="d7354-116">This command creates a new .NET console application in the current directory.</span></span>

<span data-ttu-id="d7354-117">Откройте файл *Program.cs* в любом редакторе и замените строку `Console.WriteLine("Hello World!");` следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="d7354-117">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="d7354-118">Чтобы выполнить этот код, введите `dotnet run` в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="d7354-118">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="d7354-119">В консоли должно появиться сообщение The answer is greater than 10</span><span class="sxs-lookup"><span data-stu-id="d7354-119">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="d7354-120">(Ответ больше 10).</span><span class="sxs-lookup"><span data-stu-id="d7354-120">printed to your console.</span></span>

<span data-ttu-id="d7354-121">Измените объявление `b`, чтобы сумма была меньше 10:</span><span class="sxs-lookup"><span data-stu-id="d7354-121">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="d7354-122">Введите `dotnet run` еще раз.</span><span class="sxs-lookup"><span data-stu-id="d7354-122">Type `dotnet run` again.</span></span> <span data-ttu-id="d7354-123">Так как ответ меньше 10, никакие данные не выводятся.</span><span class="sxs-lookup"><span data-stu-id="d7354-123">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="d7354-124">Проверяемое **условие** имеет значение false.</span><span class="sxs-lookup"><span data-stu-id="d7354-124">The **condition** you're testing is false.</span></span> <span data-ttu-id="d7354-125">У вас еще нет кода для выполнения, так как вы написали только одну из возможных ветвей для оператора `if` — ветвь true.</span><span class="sxs-lookup"><span data-stu-id="d7354-125">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="d7354-126">Вероятнее всего, при изучении C# (как и любого другого языка программирования) вы будете допускать ошибки в коде.</span><span class="sxs-lookup"><span data-stu-id="d7354-126">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="d7354-127">Компилятор найдет ошибки и сообщит о них.</span><span class="sxs-lookup"><span data-stu-id="d7354-127">The compiler will find and report the errors.</span></span> <span data-ttu-id="d7354-128">Внимательно просмотрите выходные данные ошибки и код, вызвавший ошибку.</span><span class="sxs-lookup"><span data-stu-id="d7354-128">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="d7354-129">Как правило, сведения о причине ошибки можно найти в сообщении об ошибке компилятора.</span><span class="sxs-lookup"><span data-stu-id="d7354-129">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="d7354-130">В первом примере показаны возможности `if` и логические типы.</span><span class="sxs-lookup"><span data-stu-id="d7354-130">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="d7354-131">*Логическое значение* — это переменная, которая может иметь одно из двух значений: `true` или `false`.</span><span class="sxs-lookup"><span data-stu-id="d7354-131">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="d7354-132">Логические переменные в C# определяются особым типом — `bool`.</span><span class="sxs-lookup"><span data-stu-id="d7354-132">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="d7354-133">Оператор `if` проверяет значение `bool`.</span><span class="sxs-lookup"><span data-stu-id="d7354-133">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="d7354-134">Если значение `true`, выполняется оператор, следующий после `if`.</span><span class="sxs-lookup"><span data-stu-id="d7354-134">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="d7354-135">В противном случае он пропускается.</span><span class="sxs-lookup"><span data-stu-id="d7354-135">Otherwise, it's skipped.</span></span>

<span data-ttu-id="d7354-136">Этот процесс проверки условий и выполнения операторов на основе этих условий предоставляет широкие возможности.</span><span class="sxs-lookup"><span data-stu-id="d7354-136">This process of checking conditions and executing statements based on those conditions is powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="d7354-137">Объединение операторов if и else</span><span class="sxs-lookup"><span data-stu-id="d7354-137">Make if and else work together</span></span>

<span data-ttu-id="d7354-138">Чтобы выполнить разный код в ветвях true и false, создайте ветвь `else`, которая будет выполняться, если условие имеет значение false.</span><span class="sxs-lookup"><span data-stu-id="d7354-138">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="d7354-139">Попробуйте сделать следующее.</span><span class="sxs-lookup"><span data-stu-id="d7354-139">Try this.</span></span> <span data-ttu-id="d7354-140">Добавьте две последние строки из приведенного ниже кода в метод `Main` (первые четыре должны быть уже добавлены):</span><span class="sxs-lookup"><span data-stu-id="d7354-140">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="d7354-141">Оператор после ключевого слова `else` выполняется, только если проверяемое условие имеет значение `false`.</span><span class="sxs-lookup"><span data-stu-id="d7354-141">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="d7354-142">Объединив операторы `if` и `else` с логическими условиями, вы получите все необходимые возможности для обработки условий `true` и `false`.</span><span class="sxs-lookup"><span data-stu-id="d7354-142">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d7354-143">Отступы под операторами `if` и `else` предназначены только для удобства чтения.</span><span class="sxs-lookup"><span data-stu-id="d7354-143">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="d7354-144">В языке C# необязательно ставить отступы или пробелы.</span><span class="sxs-lookup"><span data-stu-id="d7354-144">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="d7354-145">Операторы после ключевого слова `if` или `else` будут выполняться на основе условия.</span><span class="sxs-lookup"><span data-stu-id="d7354-145">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="d7354-146">Во всех строках в примерах кода, представленных в этом руководстве, отступы традиционно соответствуют потоку управления операторов.</span><span class="sxs-lookup"><span data-stu-id="d7354-146">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="d7354-147">Так как отступ не обязателен, используйте скобки `{` и `}`, если нужно указать несколько операторов в блоке кода, который выполняется в зависимости от условий.</span><span class="sxs-lookup"><span data-stu-id="d7354-147">Because indentation isn't significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="d7354-148">Программисты C# обычно используют эти фигурные скобки во всех предложениях `if` и `else`.</span><span class="sxs-lookup"><span data-stu-id="d7354-148">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="d7354-149">Следующий пример аналогичен тому, который вы создали.</span><span class="sxs-lookup"><span data-stu-id="d7354-149">The following example is the same as the one you created.</span></span> <span data-ttu-id="d7354-150">Измените код выше, чтобы он соответствовал следующему коду:</span><span class="sxs-lookup"><span data-stu-id="d7354-150">Modify your code above to match the following code:</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> <span data-ttu-id="d7354-151">Все примеры кода в следующих разделах руководства содержат фигурные скобки в соответствии с принятой практикой.</span><span class="sxs-lookup"><span data-stu-id="d7354-151">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="d7354-152">Можно проверить более сложные условия.</span><span class="sxs-lookup"><span data-stu-id="d7354-152">You can test more complicated conditions.</span></span> <span data-ttu-id="d7354-153">Добавьте следующий код в метод `Main` после написанного кода:</span><span class="sxs-lookup"><span data-stu-id="d7354-153">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

<span data-ttu-id="d7354-154">Символ `==` позволяет проверить *равенство*.</span><span class="sxs-lookup"><span data-stu-id="d7354-154">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="d7354-155">С помощью `==` обозначается отличие проверки равенства от назначения, которое показано в `a = 5`.</span><span class="sxs-lookup"><span data-stu-id="d7354-155">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="d7354-156">`&&` представляет оператор and.</span><span class="sxs-lookup"><span data-stu-id="d7354-156">The `&&` represents "and".</span></span> <span data-ttu-id="d7354-157">То есть для выполнения оператора в ветви true оба условия должны иметь значение true.</span><span class="sxs-lookup"><span data-stu-id="d7354-157">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="d7354-158">В этих примерах также показано, что в каждой условной ветви можно задать несколько операторов. Нужно лишь заключить их в скобки `{` и `}`.</span><span class="sxs-lookup"><span data-stu-id="d7354-158">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="d7354-159">Вы также можете использовать оператор `||`, который представляет оператор or.</span><span class="sxs-lookup"><span data-stu-id="d7354-159">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="d7354-160">Добавьте следующий фрагмент после написанного кода:</span><span class="sxs-lookup"><span data-stu-id="d7354-160">Add the following code after what you've written so far:</span></span>

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

<span data-ttu-id="d7354-161">Измените значения `a`, `b` и `c`, а также переключитесь между `&&` и `||` для изучения.</span><span class="sxs-lookup"><span data-stu-id="d7354-161">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="d7354-162">Так вы лучше поймете, как работают операторы `&&` и `||`.</span><span class="sxs-lookup"><span data-stu-id="d7354-162">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="d7354-163">Вы завершили первый этап.</span><span class="sxs-lookup"><span data-stu-id="d7354-163">You've finished the first step.</span></span> <span data-ttu-id="d7354-164">Прежде чем перейти к следующему разделу, переместим текущий код в отдельный метод.</span><span class="sxs-lookup"><span data-stu-id="d7354-164">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="d7354-165">Это упростит начало работы с новым примером.</span><span class="sxs-lookup"><span data-stu-id="d7354-165">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="d7354-166">Переименуйте метод `Main` в `ExploreIf` и запишите новый метод `Main`, который вызывает `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="d7354-166">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="d7354-167">В результате ваш код должен выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="d7354-167">When you've finished, your code should look like this:</span></span>

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            int c = 4;
            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

<span data-ttu-id="d7354-168">Закомментируйте вызов `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="d7354-168">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="d7354-169">Это поможет упорядочить выходные данные в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="d7354-169">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="d7354-170">`//` запускает **комментарий** в C#.</span><span class="sxs-lookup"><span data-stu-id="d7354-170">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="d7354-171">Комментарии — это любой текст, который должен быть сохранен в исходном коде, но не должен выполняться как код.</span><span class="sxs-lookup"><span data-stu-id="d7354-171">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="d7354-172">Компилятор не создает исполняемый код из комментариев.</span><span class="sxs-lookup"><span data-stu-id="d7354-172">The compiler doesn't generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="d7354-173">Использование циклов для повторения операций</span><span class="sxs-lookup"><span data-stu-id="d7354-173">Use loops to repeat operations</span></span>

<span data-ttu-id="d7354-174">В этом разделе **циклы** используются для повторения операторов.</span><span class="sxs-lookup"><span data-stu-id="d7354-174">In this section, you use **loops** to repeat statements.</span></span> <span data-ttu-id="d7354-175">Выполните в методе `Main` следующий код:</span><span class="sxs-lookup"><span data-stu-id="d7354-175">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="d7354-176">Оператор `while` проверяет условие и выполняет инструкцию или блок инструкций, следующий после `while`.</span><span class="sxs-lookup"><span data-stu-id="d7354-176">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="d7354-177">Проверка условия и выполнение этих операторов будут повторяться, пока условие не примет значение false.</span><span class="sxs-lookup"><span data-stu-id="d7354-177">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="d7354-178">В этом примере представлен еще один новый оператор.</span><span class="sxs-lookup"><span data-stu-id="d7354-178">There's one other new operator in this example.</span></span> <span data-ttu-id="d7354-179">Объект `++` после переменной `counter` представляет собой оператор **инкремента**.</span><span class="sxs-lookup"><span data-stu-id="d7354-179">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="d7354-180">Он добавляет 1 к значению `counter` и сохраняет это значение в переменной `counter`.</span><span class="sxs-lookup"><span data-stu-id="d7354-180">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d7354-181">Напишите такой код, при выполнении которого значение условия цикла `while` изменится на false.</span><span class="sxs-lookup"><span data-stu-id="d7354-181">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="d7354-182">В противном случае будет создан **бесконечный цикл**, в котором выполнение программы никогда не закончится.</span><span class="sxs-lookup"><span data-stu-id="d7354-182">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="d7354-183">Это не показано в примере, так как нужно принудительно закрыть программу, нажав клавиши **CTRL+C**, или другим способом.</span><span class="sxs-lookup"><span data-stu-id="d7354-183">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="d7354-184">В цикле `while` условие проверяется, прежде чем выполнить код, который следует после `while`.</span><span class="sxs-lookup"><span data-stu-id="d7354-184">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="d7354-185">А в цикле `do` ... `while` сначала выполняется код, а потом проверяется условие.</span><span class="sxs-lookup"><span data-stu-id="d7354-185">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="d7354-186">Цикл *do while* показан в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="d7354-186">The *do while* loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="d7354-187">Этот цикл `do` и цикл `while`, приведенный выше, выводят одинаковый результат.</span><span class="sxs-lookup"><span data-stu-id="d7354-187">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="d7354-188">Работа с циклом for</span><span class="sxs-lookup"><span data-stu-id="d7354-188">Work with the for loop</span></span>

<span data-ttu-id="d7354-189">Цикл **for** широко используется в C#.</span><span class="sxs-lookup"><span data-stu-id="d7354-189">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="d7354-190">Выполните в методе Main() следующий код:</span><span class="sxs-lookup"><span data-stu-id="d7354-190">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="d7354-191">Этот цикл работает так же, как циклы `while` и `do`, которые вы использовали ранее.</span><span class="sxs-lookup"><span data-stu-id="d7354-191">The previous code does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="d7354-192">Оператор `for` состоит из трех частей, которые отвечают за его работу.</span><span class="sxs-lookup"><span data-stu-id="d7354-192">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="d7354-193">Первая часть — **для инициализатора**: `int index = 0;` объявляет `index` переменной цикла и задает для ее начальное значение `0`.</span><span class="sxs-lookup"><span data-stu-id="d7354-193">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="d7354-194">Средняя часть — **для условия**: `index < 10` объявляет, что этот цикл `for` продолжает выполняться, пока значение счетчика меньше 10.</span><span class="sxs-lookup"><span data-stu-id="d7354-194">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="d7354-195">Последняя часть — **для итератора**: `index++` определяет, как изменится переменная цикла после выполнения блока, следующего после оператора `for`.</span><span class="sxs-lookup"><span data-stu-id="d7354-195">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="d7354-196">В нашем случае определяется, что значение `index` должно увеличиваться на 1 каждый раз, когда выполняется блок.</span><span class="sxs-lookup"><span data-stu-id="d7354-196">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="d7354-197">Поэкспериментируйте.</span><span class="sxs-lookup"><span data-stu-id="d7354-197">Experiment yourself.</span></span> <span data-ttu-id="d7354-198">Попробуйте использовать следующие варианты.</span><span class="sxs-lookup"><span data-stu-id="d7354-198">Try each of the following variations:</span></span>

- <span data-ttu-id="d7354-199">Измените инициализатор, чтобы цикл начинался с другого значения.</span><span class="sxs-lookup"><span data-stu-id="d7354-199">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="d7354-200">Измените условие, чтобы цикл заканчивался другим значением.</span><span class="sxs-lookup"><span data-stu-id="d7354-200">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="d7354-201">По окончании попробуйте самостоятельно написать код, чтобы применить полученные знания.</span><span class="sxs-lookup"><span data-stu-id="d7354-201">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

<span data-ttu-id="d7354-202">Есть еще одна циклическая инструкция, которая не рассматривается в этом руководстве: оператор `foreach`.</span><span class="sxs-lookup"><span data-stu-id="d7354-202">There's one other looping statement that isn't covered in this tutorial: the `foreach` statement.</span></span> <span data-ttu-id="d7354-203">Оператор `foreach` повторяет выполнения для каждого элемента в последовательности элементов.</span><span class="sxs-lookup"><span data-stu-id="d7354-203">The `foreach` statement repeats its statement for every item in a sequence of items.</span></span> <span data-ttu-id="d7354-204">Чаще всего он используется с *коллекциями*, поэтому он рассматривается в следующем руководстве.</span><span class="sxs-lookup"><span data-stu-id="d7354-204">It's most often used with *collections*, so it's covered in the next tutorial.</span></span>

## <a name="created-nested-loops"></a><span data-ttu-id="d7354-205">Создание вложенных циклов</span><span class="sxs-lookup"><span data-stu-id="d7354-205">Created nested loops</span></span>

<span data-ttu-id="d7354-206">Цикл `while`, `do` или `for` можно вложить в другой цикл, чтобы создать матрицу, комбинируя каждый элемент во внешнем цикле с каждым элементом во внутреннем цикле.</span><span class="sxs-lookup"><span data-stu-id="d7354-206">A `while`, `do`, or `for` loop can be nested inside another loop to create a matrix using the combination of each item in the outer loop with each item in the inner loop.</span></span> <span data-ttu-id="d7354-207">Давайте сделаем это для получения набора из буквенно-цифровых пар, представляющих строки и столбцы.</span><span class="sxs-lookup"><span data-stu-id="d7354-207">Let's do that to build a set of alphanumeric pairs to represent rows and columns.</span></span>

<span data-ttu-id="d7354-208">Один цикл `for` может создавать строки:</span><span class="sxs-lookup"><span data-stu-id="d7354-208">One `for` loop can generate the rows:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

<span data-ttu-id="d7354-209">Другой цикл может создавать столбцы:</span><span class="sxs-lookup"><span data-stu-id="d7354-209">Another loop can generate the columns:</span></span>

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

<span data-ttu-id="d7354-210">Можно вложить один цикл внутрь другого для формирования пар:</span><span class="sxs-lookup"><span data-stu-id="d7354-210">You can nest one loop inside the other to form pairs:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

<span data-ttu-id="d7354-211">Как видите, внешний цикл увеличивается на единицу при каждом полном выполнении внутреннего цикла.</span><span class="sxs-lookup"><span data-stu-id="d7354-211">You can see that the outer loop increments once for each full run of the inner loop.</span></span> <span data-ttu-id="d7354-212">Измените порядок вложенности строк и столбцов и просмотрите изменения самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="d7354-212">Reverse the row and column nesting, and see the changes for yourself.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="d7354-213">Объединение ветвей и циклов</span><span class="sxs-lookup"><span data-stu-id="d7354-213">Combine branches and loops</span></span>

<span data-ttu-id="d7354-214">Теперь, когда вы ознакомились с оператором `if` и конструкциями цикла на языке C#, попытайтесь написать код C# для поиска суммы всех целых чисел от 1 до 20, которые делятся на 3.</span><span class="sxs-lookup"><span data-stu-id="d7354-214">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="d7354-215">Вот несколько подсказок:</span><span class="sxs-lookup"><span data-stu-id="d7354-215">Here are a few hints:</span></span>

- <span data-ttu-id="d7354-216">оператор `%` позволяет получить остаток от операции деления;</span><span class="sxs-lookup"><span data-stu-id="d7354-216">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="d7354-217">оператор `if` предоставляет условие, которое позволяет определить, будет ли число учитываться в сумме;</span><span class="sxs-lookup"><span data-stu-id="d7354-217">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="d7354-218">цикл `for` позволяет повторить последовательность шагов для всех чисел от 1 до 20.</span><span class="sxs-lookup"><span data-stu-id="d7354-218">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="d7354-219">Попробуйте самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="d7354-219">Try it yourself.</span></span> <span data-ttu-id="d7354-220">Затем проверьте результат.</span><span class="sxs-lookup"><span data-stu-id="d7354-220">Then check how you did.</span></span> <span data-ttu-id="d7354-221">Вы должны получить ответ "63".</span><span class="sxs-lookup"><span data-stu-id="d7354-221">You should get 63 for an answer.</span></span> <span data-ttu-id="d7354-222">Один из возможных ответов можно увидеть в [полном примере кода в GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="d7354-222">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="d7354-223">Вы ознакомились с руководством по ветвям и циклам.</span><span class="sxs-lookup"><span data-stu-id="d7354-223">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="d7354-224">Теперь вы можете перейти к ознакомлению с руководством [Массивы и коллекции](arrays-and-collections.md) в своей среде разработки.</span><span class="sxs-lookup"><span data-stu-id="d7354-224">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="d7354-225">Дополнительные сведения об этих понятиях см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="d7354-225">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="d7354-226">if-else (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="d7354-226">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="d7354-227">while (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="d7354-227">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="d7354-228">do (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="d7354-228">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="d7354-229">for (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="d7354-229">For statement</span></span>](../../language-reference/keywords/for.md)
