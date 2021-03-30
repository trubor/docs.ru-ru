---
title: Операторы верхнего уровня — учебник по C#
description: В этом учебнике показано, как использовать инструкции верхнего уровня для проведения экспериментов и подтверждения концепций при анализе идей.
ms.date: 10/28/2020
ms.openlocfilehash: d3cd089c5681e6c06a0c63cbffcc3cf5935fbeef
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104878955"
---
# <a name="tutorial-explore-ideas-using-top-level-statements-to-build-code-as-you-learn"></a><span data-ttu-id="3a6a3-103">Учебник. Анализ идей с использованием операторов верхнего уровня для создания кода по мере обучения</span><span class="sxs-lookup"><span data-stu-id="3a6a3-103">Tutorial: Explore ideas using top-level statements to build code as you learn</span></span>

<span data-ttu-id="3a6a3-104">Из этого руководства вы узнаете, как выполнять следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="3a6a3-104">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="3a6a3-105">Ознакомитесь с правилами, касающимися использования операторов верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-105">Learn the rules governing your use of top-level statements.</span></span>
> - <span data-ttu-id="3a6a3-106">Используете операторы верхнего уровня для изучения алгоритмов.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-106">Use top-level statements to explore algorithms.</span></span>
> - <span data-ttu-id="3a6a3-107">Выполните рефакторинг результатов исследования в многократно используемые компоненты.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-107">Refactor explorations into reusable components.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3a6a3-108">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="3a6a3-108">Prerequisites</span></span>

<span data-ttu-id="3a6a3-109">Вам нужно настроить свой компьютер для выполнения .NET 5, включая компилятор C# 9.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-109">You'll need to set up your machine to run .NET 5, which includes the C# 9 compiler.</span></span> <span data-ttu-id="3a6a3-110">Компилятор C# 9 доступен, начиная с [Visual Studio 2019 версии 16.9 preview 1](https://visualstudio.microsoft.com/vs/preview/) или [в пакете SDK .NET 5.0](https://dot.net/get-dotnet5).</span><span class="sxs-lookup"><span data-stu-id="3a6a3-110">The C# 9 compiler is available starting with [Visual Studio 2019 version 16.9 preview 1](https://visualstudio.microsoft.com/vs/preview/) or [.NET 5.0 SDK](https://dot.net/get-dotnet5).</span></span>

<span data-ttu-id="3a6a3-111">В этом руководстве предполагается, что вы знакомы с C# и .NET, включая Visual Studio или .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-111">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="start-exploring"></a><span data-ttu-id="3a6a3-112">Начало знакомства</span><span class="sxs-lookup"><span data-stu-id="3a6a3-112">Start exploring</span></span>

<span data-ttu-id="3a6a3-113">Операторы верхнего уровня позволяют избежать лишних формальностей благодаря помещению точки входа программы в статический метод в классе.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-113">Top-level statements enable you to avoid the extra ceremony required by placing your program's entry point in a static method in a class.</span></span> <span data-ttu-id="3a6a3-114">Новое консольное приложение обычно начинается со следующего кода.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-114">The typical starting point for a new console application looks like the following code:</span></span>

```csharp
using System;

namespace Application
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="3a6a3-115">Приведенный выше код является результатом выполнения команды `dotnet new console` для создания консольного приложения.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-115">The preceding code is the result of running the `dotnet new console` command and creating a new console application.</span></span> <span data-ttu-id="3a6a3-116">Из этих одиннадцати строк кода только одна является исполняемой.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-116">Those 11 lines contain only one line of executable code.</span></span> <span data-ttu-id="3a6a3-117">Эту программу можно упростить с помощью новой функции, которая называется операторами верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-117">You can simplify that program with the new top-level statements feature.</span></span> <span data-ttu-id="3a6a3-118">Она позволяет удалить из этой программы все строки, кроме двух.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-118">That enables you to remove all but two of the lines in this program:</span></span>

```csharp
using System;

Console.WriteLine("Hello World!");
```

<span data-ttu-id="3a6a3-119">Эта функция упрощает изучение новых идей.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-119">This feature simplifies what's needed to begin exploring new ideas.</span></span> <span data-ttu-id="3a6a3-120">Операторы верхнего уровня можно использовать для скриптов или исследования возможностей.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-120">You can use top-level statements for scripting scenarios, or to explore.</span></span> <span data-ttu-id="3a6a3-121">Получив работающую базовую структуру, можно перейти к рефакторингу кода и создать методы, классы и другие сборки для многократно используемых компонентов.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-121">Once you've got the basics working, you can start refactoring the code and create methods, classes, or other assemblies for reusable components you've built.</span></span> <span data-ttu-id="3a6a3-122">Операторы верхнего уровня позволяют быстро проводить эксперименты и реализовывать упражнения для начинающих.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-122">Top-level statements do enable quick experimentation and beginner tutorials.</span></span> <span data-ttu-id="3a6a3-123">Они также позволяют легко переходить от экспериментов к полнофункциональным программам.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-123">They also provide a smooth path from experimentation to full programs.</span></span>

<span data-ttu-id="3a6a3-124">Операторы верхнего уровня выполняются в том порядке, в котором они следуют в файле.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-124">Top-level statements are executed in the order they appear in the file.</span></span> <span data-ttu-id="3a6a3-125">Их можно использовать только в одном исходном файле приложения.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-125">Top-level statements can only be used in one source file in your application.</span></span> <span data-ttu-id="3a6a3-126">Если они используются более чем в одном файле, компилятор выдает ошибку.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-126">The compiler generates an error if you use them in more than one file.</span></span>

## <a name="build-a-magic-net-answer-machine"></a><span data-ttu-id="3a6a3-127">Создание программы для ответа на вопросы на .NET</span><span class="sxs-lookup"><span data-stu-id="3a6a3-127">Build a magic .NET answer machine</span></span>

<span data-ttu-id="3a6a3-128">В этом учебнике мы создадим консольное приложение, которое отвечает на вопрос, требующий ответа "да" или "нет", случайным образом.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-128">For this tutorial, let's build a console application that answers a "yes" or "no" question with a random answer.</span></span> <span data-ttu-id="3a6a3-129">Его функциональность будет реализована постепенно.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-129">You'll build out the functionality step by step.</span></span> <span data-ttu-id="3a6a3-130">Вы можете сосредоточиться на задаче, а не на формальностях, необходимых для построения структуры обычной программы.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-130">You can focus on your task rather than ceremony needed for the structure of a typical program.</span></span> <span data-ttu-id="3a6a3-131">Когда нужная функциональность будет получена, вы можете выполнить рефакторинг приложения по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-131">Then, once you're happy with the functionality, you can refactor the application as you see fit.</span></span>

<span data-ttu-id="3a6a3-132">Начать можно с записи вопроса обратно в консоль.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-132">A good starting point is to write the question back to the console.</span></span> <span data-ttu-id="3a6a3-133">Для этого можно использовать следующий код.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-133">You can start by writing the following code:</span></span>

```csharp
using System;

Console.WriteLine(args);
```

<span data-ttu-id="3a6a3-134">Переменная `args` не объявляется.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-134">You don't declare an `args` variable.</span></span> <span data-ttu-id="3a6a3-135">В случае с одним исходным файлом, содержащим операторы верхнего уровня, компилятор распознает `args` как аргументы командной строки.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-135">For the single source file that contains your top-level statements, the compiler recognizes `args` to mean the command-line arguments.</span></span> <span data-ttu-id="3a6a3-136">args имеет тип `string[]`, как во всех программах на C#.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-136">The type of args is a `string[]`, as in all C# programs.</span></span>

<span data-ttu-id="3a6a3-137">Вы можете протестировать код, выполнив следующую команду `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-137">You can test your code by running the following `dotnet run` command:</span></span>

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?
```

<span data-ttu-id="3a6a3-138">Аргументы после `--` в командной строке передаются в программу.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-138">The arguments after the `--` on the command line are passed to the program.</span></span> <span data-ttu-id="3a6a3-139">Вы можете увидеть тип переменной `args`, так как в консоли выводится следующее.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-139">You can see the type of the `args` variable, because that's what's printed to the console:</span></span>

```console
System.String[]
```

<span data-ttu-id="3a6a3-140">Чтобы записать вопрос в консоль, необходимо перечислить аргументы через пробел.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-140">To write the question to the console, you'll need to enumerate the arguments and separate them with a space.</span></span> <span data-ttu-id="3a6a3-141">Замените вызов `WriteLine` следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-141">Replace the `WriteLine` call with the following code:</span></span>

:::code language="csharp" source="snippets/top-level-statements/ProgramSnippets.cs" ID="EchoInput":::

<span data-ttu-id="3a6a3-142">Теперь при запуске программы она будет правильно выводить вопрос в виде строки аргументов.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-142">Now, when you run the program, it will correctly display the question as a string of arguments.</span></span>

## <a name="respond-with-a-random-answer"></a><span data-ttu-id="3a6a3-143">Вывод случайного ответа</span><span class="sxs-lookup"><span data-stu-id="3a6a3-143">Respond with a random answer</span></span>

<span data-ttu-id="3a6a3-144">После вывода вопроса можно добавить код для выбора случайного ответа.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-144">After echoing the question, you can add the code to generate the random answer.</span></span> <span data-ttu-id="3a6a3-145">Сначала добавьте массив возможных ответов.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-145">Start by adding an array of possible answers:</span></span>

:::code language="csharp" source="snippets/top-level-statements/ProgramSnippets.cs" ID="Answers":::

<span data-ttu-id="3a6a3-146">Этот массив содержит двенадцать утвердительных ответов: шесть неопределенных и шесть отрицательных.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-146">This array has 12 answers that are affirmative, six that are non-committal, and six that are negative.</span></span> <span data-ttu-id="3a6a3-147">Далее добавьте следующий код для выбора случайного ответа из массива и его вывода.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-147">Next, add the following code to generate and display a random answer from the array:</span></span>

:::code language="csharp" source="snippets/top-level-statements/ProgramSnippets.cs" ID="GenerateAnswer":::

<span data-ttu-id="3a6a3-148">Вы можете снова запустить приложение, чтобы увидеть результаты.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-148">You can run the application again to see the results.</span></span> <span data-ttu-id="3a6a3-149">Выходные данные должны быть примерно следующими.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-149">You should see something like the following output:</span></span>

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?

Should I use top level statements in all my programs?
Better not tell you now.
```

<span data-ttu-id="3a6a3-150">Этот код отвечает на вопросы, но давайте добавим еще одну функцию.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-150">This code answers the questions, but let's add one more feature.</span></span> <span data-ttu-id="3a6a3-151">Вы хотите, чтобы ваше приложение делало вид, будто думает над ответом.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-151">You'd like your question app to simulate thinking about the answer.</span></span> <span data-ttu-id="3a6a3-152">Для этого можно добавить ASCII-анимацию и сделать небольшую паузу.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-152">You can do that by adding a bit of ASCII animation, and pausing while working.</span></span>  <span data-ttu-id="3a6a3-153">Добавьте следующий код после строки, которая выводит на экран вопрос.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-153">Add the following code after the line that echoes the question:</span></span>

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="AnimationFirstPass":::

<span data-ttu-id="3a6a3-154">Необходимо также добавить оператор `using` в начало исходного файла.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-154">You'll also need to add a `using` statement to the top of the source file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="3a6a3-155">Операторы `using` должны находиться перед всеми остальными операторами в файле.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-155">The `using` statements must be before any other statements in the file.</span></span> <span data-ttu-id="3a6a3-156">В противном случае возникает ошибка компилятора.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-156">Otherwise, it's a compiler error.</span></span> <span data-ttu-id="3a6a3-157">Вы можете снова запустить программу и посмотреть анимацию.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-157">You can run the program again and see the animation.</span></span> <span data-ttu-id="3a6a3-158">Так уже лучше.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-158">That makes a better experience.</span></span> <span data-ttu-id="3a6a3-159">Поэкспериментируйте с длительностью задержки и выберите понравившуюся.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-159">Experiment with the length of the delay to match your taste.</span></span>

<span data-ttu-id="3a6a3-160">Приведенный выше код создает несколько вращающихся линий, разделенных пробелами.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-160">The preceding code creates a set of spinning lines separated by a space.</span></span> <span data-ttu-id="3a6a3-161">Добавление ключевого слова `await` предписывает компилятору создать точку входа программы в виде метода с модификатором `async` и возвращает <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-161">Adding the `await` keyword instructs the compiler to generate the program entry point as a method that has the `async` modifier, and returns a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3a6a3-162">Эта программа не возвращает значения, поэтому ее точка входа возвращает `Task`.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-162">This program does not return a value, so the program entry point returns a `Task`.</span></span> <span data-ttu-id="3a6a3-163">Если программа возвращала бы целочисленное значение, необходимо было бы добавить оператор return в конце блока операторов верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-163">If your program returns an integer value, you would add a return statement to the end of your top-level statements.</span></span> <span data-ttu-id="3a6a3-164">Он указывал бы возвращаемое целочисленное значение.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-164">That return statement would specify the integer value to return.</span></span> <span data-ttu-id="3a6a3-165">Если операторы верхнего уровня включают в себя выражение `await`, возвращается тип <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-165">If your top-level statements include an `await` expression, the return type becomes <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>.</span></span>

## <a name="refactoring-for-the-future"></a><span data-ttu-id="3a6a3-166">Рефакторинг кода для дальнейшего использования</span><span class="sxs-lookup"><span data-stu-id="3a6a3-166">Refactoring for the future</span></span>

<span data-ttu-id="3a6a3-167">Код программы должен выглядеть так.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-167">Your program should look like the following code:</span></span>

```csharp
using System;
using System.Threading.Tasks;

Console.WriteLine();
foreach(var s in args)
{
    Console.Write(s);
    Console.Write(' ');
}
Console.WriteLine();

for (int i = 0; i < 20; i++)
{
    Console.Write("| -");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("/ \\");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("- |");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("\\ /");
    await Task.Delay(50);
    Console.Write("\b\b\b");
}
Console.WriteLine();

string[] answers =
{
    "It is certain.",       "Reply hazy, try again.",     "Don't count on it.",
    "It is decidedly so.",  "Ask again later.",           "My reply is no.",
    "Without a doubt.",     "Better not tell you now.",   "My sources say no.",
    "Yes – definitely.",    "Cannot predict now.",        "Outlook not so good.",
    "You may rely on it.",  "Concentrate and ask again.", "Very doubtful.",
    "As I see it, yes.",
    "Most likely.",
    "Outlook good.",
    "Yes.",
    "Signs point to yes.",
};

var index = new Random().Next(answers.Length - 1);
Console.WriteLine(answers[index]);
```

<span data-ttu-id="3a6a3-168">Приведенный выше код имеет смысл.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-168">The preceding code is reasonable.</span></span> <span data-ttu-id="3a6a3-169">Он работает.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-169">It works.</span></span> <span data-ttu-id="3a6a3-170">Но его нельзя использовать многократно.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-170">But it isn't reusable.</span></span> <span data-ttu-id="3a6a3-171">Теперь, когда вы получили работающее приложение, пора извлечь из него многократно используемые части.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-171">Now that you have the application working, it's time to pull out reusable parts.</span></span>

<span data-ttu-id="3a6a3-172">Одним из кандидатов является код, отображающий анимацию во время ожидания.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-172">One candidate is the code that displays the waiting animation.</span></span> <span data-ttu-id="3a6a3-173">Этот фрагмент кода может стать методом.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-173">That snippet can become a method:</span></span>

<span data-ttu-id="3a6a3-174">Можно начать с создания локальной функции в файле.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-174">You can start by creating a local function in your file.</span></span> <span data-ttu-id="3a6a3-175">Замените текущую анимацию следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-175">Replace the current animation with the following code:</span></span>

```csharp
await ShowConsoleAnimation();

static async Task ShowConsoleAnimation()
{
    for (int i = 0; i < 20; i++)
    {
        Console.Write("| -");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("/ \\");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("- |");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("\\ /");
        await Task.Delay(50);
        Console.Write("\b\b\b");
    }
    Console.WriteLine();
}
```

<span data-ttu-id="3a6a3-176">Приведенный выше код создает локальную функцию внутри метода main.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-176">The preceding code creates a local function inside your main method.</span></span> <span data-ttu-id="3a6a3-177">Его также нельзя использовать повторно.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-177">That's still not reusable.</span></span> <span data-ttu-id="3a6a3-178">Поэтому давайте извлечем этот код в класс.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-178">So, extract that code into a class.</span></span> <span data-ttu-id="3a6a3-179">Создайте файл с именем *utilities.cs* и добавьте следующий код.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-179">Create a new file named *utilities.cs* and add the following code:</span></span>

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="SnippetUtilities":::

<span data-ttu-id="3a6a3-180">Файл, содержащий инструкции верхнего уровня, также может содержать пространства имен и типы в конце файла (после инструкций верхнего уровня).</span><span class="sxs-lookup"><span data-stu-id="3a6a3-180">A file that has top-level statements can also contain namespaces and types at the end of the file, after the top-level statements.</span></span> <span data-ttu-id="3a6a3-181">Но при работе с этим учебником метод анимации нужно поместить в отдельный файл, чтобы упростить его повторное использование.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-181">But for this tutorial you put the animation method in a separate file to make it more readily reusable.</span></span>

<span data-ttu-id="3a6a3-182">Наконец, можно очистить код анимации, удалив повторяющиеся элементы.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-182">Finally, you can clean the animation code to remove some duplication:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Utilities.cs" ID="Animation":::

<span data-ttu-id="3a6a3-183">Теперь у вас есть законченное приложение и вы выполнили рефакторинг частей, пригодных для многократного использования.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-183">Now you have a complete application, and you've refactored the reusable parts for later use.</span></span> <span data-ttu-id="3a6a3-184">Вы можете вызвать новый служебный метод с помощью инструкций верхнего уровня, как показано ниже в готовой версии основной программы:</span><span class="sxs-lookup"><span data-stu-id="3a6a3-184">You can call the new utility method from your top-level statements, as shown below in the finished version of the main program:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Program.cs":::

<span data-ttu-id="3a6a3-185">Таким образом, будет добавлен вызов `Utilities.ShowConsoleAnimation` и дополнительная инструкция `using`.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-185">This adds the call to `Utilities.ShowConsoleAnimation`, and adds an additional `using` statement.</span></span>

## <a name="summary"></a><span data-ttu-id="3a6a3-186">Сводка</span><span class="sxs-lookup"><span data-stu-id="3a6a3-186">Summary</span></span>

<span data-ttu-id="3a6a3-187">Операторы верхнего уровня упрощают создание простых программ для изучения новых алгоритмов.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-187">Top-level statements make it easier to create simple programs for use to explore new algorithms.</span></span> <span data-ttu-id="3a6a3-188">Вы можете экспериментировать с алгоритмами, используя разные фрагменты кода.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-188">You can experiment with algorithms by trying different snippets of code.</span></span> <span data-ttu-id="3a6a3-189">Определив наиболее эффективный подход, можно выполнить рефакторинг кода, чтобы его было удобнее обслуживать.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-189">Once you've learned what works, you can refactor the code to be more maintainable.</span></span>

<span data-ttu-id="3a6a3-190">Операторы верхнего уровня упрощают программы, основанные на консоли.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-190">Top-level statements simplify programs that are based on console applications.</span></span> <span data-ttu-id="3a6a3-191">К ним относятся функции Azure, действия GitHub и другие небольшие служебные программы.</span><span class="sxs-lookup"><span data-stu-id="3a6a3-191">These include Azure functions, GitHub actions, and other small utilities.</span></span> <span data-ttu-id="3a6a3-192">Дополнительные сведения см. в статье [Инструкции верхнего уровня (руководство по программированию на C#)](../../programming-guide/main-and-command-args/top-level-statements.md).</span><span class="sxs-lookup"><span data-stu-id="3a6a3-192">For more information, see [Top-level statements (C# Programming Guide)](../../programming-guide/main-and-command-args/top-level-statements.md).</span></span>
