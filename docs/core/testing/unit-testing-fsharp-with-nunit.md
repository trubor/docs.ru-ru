---
title: Модульное тестирование F# в .NET Core с помощью dotnet test и NUnit
description: Сведения о концепциях модульного тестирования для F# в .NET Core в рамках пошаговой процедуры по созданию примера решения с помощью команды dotnet-test и NUnit.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- fsharp
ms.openlocfilehash: 54513d3063ea0a3be8da73bcbd55962e839c6e2c
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875061"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="fdba9-103">Модульное тестирование библиотек F# в .NET Core с использованием dotnet-test и NUnit</span><span class="sxs-lookup"><span data-stu-id="fdba9-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="fdba9-104">Этот учебник описывает пошаговую процедуру по созданию примера решения для изучения концепций модульного тестирования.</span><span class="sxs-lookup"><span data-stu-id="fdba9-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="fdba9-105">Если при изучении учебника вы предпочитаете использовать готовое решение, [просмотрите или скачайте пример кода](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-with-fsharp-nunit/) перед началом работы.</span><span class="sxs-lookup"><span data-stu-id="fdba9-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="fdba9-106">Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="fdba9-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="fdba9-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="fdba9-107">Prerequisites</span></span>

- <span data-ttu-id="fdba9-108">[Пакет SDK для .NET Core 2.1](https://dotnet.microsoft.com/download) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="fdba9-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="fdba9-109">Текстовый редактор или редактор кода по вашему выбору.</span><span class="sxs-lookup"><span data-stu-id="fdba9-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="fdba9-110">Создание исходного проекта</span><span class="sxs-lookup"><span data-stu-id="fdba9-110">Creating the source project</span></span>

<span data-ttu-id="fdba9-111">Откройте окно оболочки.</span><span class="sxs-lookup"><span data-stu-id="fdba9-111">Open a shell window.</span></span> <span data-ttu-id="fdba9-112">Создайте каталог с именем *unit-testing-with-fsharp* для хранения решения.</span><span class="sxs-lookup"><span data-stu-id="fdba9-112">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="fdba9-113">В этом каталоге выполните следующую команду, чтобы создать файл решения для библиотеки классов и тестового проекта:</span><span class="sxs-lookup"><span data-stu-id="fdba9-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="fdba9-114">Затем создайте каталог *MathService*.</span><span class="sxs-lookup"><span data-stu-id="fdba9-114">Next, create a *MathService* directory.</span></span> <span data-ttu-id="fdba9-115">Ниже приведена актуальная структура каталогов и файлов:</span><span class="sxs-lookup"><span data-stu-id="fdba9-115">The following outline shows the directory and file structure so far:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="fdba9-116">Перейдите к каталогу *MathService* и выполните следующую команду, чтобы создать исходный проект:</span><span class="sxs-lookup"><span data-stu-id="fdba9-116">Make *MathService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang "F#"
```

<span data-ttu-id="fdba9-117">Создайте реализацию службы вычислений со сбоем:</span><span class="sxs-lookup"><span data-stu-id="fdba9-117">You create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="fdba9-118">Вернитесь в каталог *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="fdba9-118">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="fdba9-119">Чтобы добавить проект библиотеки классов в решение, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="fdba9-119">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\MathService\MathService.fsproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="fdba9-120">Создание тестового проекта</span><span class="sxs-lookup"><span data-stu-id="fdba9-120">Creating the test project</span></span>

<span data-ttu-id="fdba9-121">Затем создайте каталог *MathService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="fdba9-121">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="fdba9-122">Ниже представлена структура каталогов:</span><span class="sxs-lookup"><span data-stu-id="fdba9-122">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="fdba9-123">Перейдите к каталогу *MathService.Tests* и создайте проект, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="fdba9-123">Make the *MathService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang "F#"
```

<span data-ttu-id="fdba9-124">При этом создается тестовый проект, который использует NUnit в качестве среды тестирования.</span><span class="sxs-lookup"><span data-stu-id="fdba9-124">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="fdba9-125">Созданный шаблон настраивает средство выполнения тестов в файле *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="fdba9-125">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="fdba9-126">Тестовый проект требует других пакетов для создания и выполнения модульных тестов. Команда</span><span class="sxs-lookup"><span data-stu-id="fdba9-126">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="fdba9-127">`dotnet new` на предыдущем шаге добавляет NUnit и адаптер тестирования NUnit.</span><span class="sxs-lookup"><span data-stu-id="fdba9-127">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="fdba9-128">Теперь добавьте в проект библиотеку классов `MathService` в качестве еще одной зависимости.</span><span class="sxs-lookup"><span data-stu-id="fdba9-128">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="fdba9-129">Использование команды `dotnet add reference`:</span><span class="sxs-lookup"><span data-stu-id="fdba9-129">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="fdba9-130">Все содержимое файла можно просмотреть в [репозитории образцов](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="fdba9-130">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="fdba9-131">Ниже показан окончательный макет решения:</span><span class="sxs-lookup"><span data-stu-id="fdba9-131">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathService.Tests.fsproj
```

<span data-ttu-id="fdba9-132">Выполните следующую команду в каталоге *unit-testing-with-fsharp*:</span><span class="sxs-lookup"><span data-stu-id="fdba9-132">Execute the following command in the *unit-testing-with-fsharp* directory:</span></span>

```dotnetcli
dotnet sln add .\MathService.Tests\MathService.Tests.fsproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="fdba9-133">Создание первого теста</span><span class="sxs-lookup"><span data-stu-id="fdba9-133">Creating the first test</span></span>

<span data-ttu-id="fdba9-134">Напишите один тест сбоя теста, запустите его, а затем повторите этот процесс.</span><span class="sxs-lookup"><span data-stu-id="fdba9-134">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="fdba9-135">Откройте файл *UnitTest1.fs* и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="fdba9-135">Open *UnitTest1.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open NUnit.Framework
open MathService

[<TestFixture>]
type TestClass () =

    [<Test>]
    member this.TestMethodPassing() =
        Assert.True(true)

    [<Test>]
     member this.FailEveryTime() = Assert.True(false)
```

<span data-ttu-id="fdba9-136">Атрибут `[<TestFixture>]` обозначает класс, который содержит тесты.</span><span class="sxs-lookup"><span data-stu-id="fdba9-136">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="fdba9-137">Атрибут `[<Test>]` обозначает метод теста, который выполняется с помощью средства выполнения тестов.</span><span class="sxs-lookup"><span data-stu-id="fdba9-137">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="fdba9-138">В каталоге *unit-testing-with-fsharp* выполните команду `dotnet test` для создания тестов и библиотеки классов, а затем выполните тесты.</span><span class="sxs-lookup"><span data-stu-id="fdba9-138">From the *unit-testing-with-fsharp* directory, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="fdba9-139">Средство запуска тестов NUnit содержит точку входа в программу для выполнения тестов.</span><span class="sxs-lookup"><span data-stu-id="fdba9-139">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="fdba9-140">`dotnet test` запускает средство выполнения тестов с помощью проекта модульного теста, который вы создали.</span><span class="sxs-lookup"><span data-stu-id="fdba9-140">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="fdba9-141">Эти два теста демонстрируют самые простые тесты, которые выполняются и завершаются сбоем.</span><span class="sxs-lookup"><span data-stu-id="fdba9-141">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="fdba9-142">`My test` выполняется успешно, а `Fail every time` завершается сбоем.</span><span class="sxs-lookup"><span data-stu-id="fdba9-142">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="fdba9-143">Сейчас создайте тест для метода `squaresOfOdds`.</span><span class="sxs-lookup"><span data-stu-id="fdba9-143">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="fdba9-144">Метод `squaresOfOdds` возвращает последовательность квадратов всех нечетных целочисленных значений, которые являются частью входной последовательности.</span><span class="sxs-lookup"><span data-stu-id="fdba9-144">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="fdba9-145">Вместо того чтобы писать все эти функции одновременно, можно постепенно создавать тесты, проверяющие функциональность.</span><span class="sxs-lookup"><span data-stu-id="fdba9-145">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="fdba9-146">Если тест выполняется успешно, создается необходимая функция метода.</span><span class="sxs-lookup"><span data-stu-id="fdba9-146">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="fdba9-147">Самый простой тест — вызов `squaresOfOdds` со всеми четными числами, где результатом должна быть пустая последовательность целых чисел.</span><span class="sxs-lookup"><span data-stu-id="fdba9-147">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="fdba9-148">Вот этот тест:</span><span class="sxs-lookup"><span data-stu-id="fdba9-148">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="fdba9-149">Обратите внимание, что последовательность `expected` преобразована в список.</span><span class="sxs-lookup"><span data-stu-id="fdba9-149">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="fdba9-150">Платформа NUnit зависит от многих стандартных типов .NET.</span><span class="sxs-lookup"><span data-stu-id="fdba9-150">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="fdba9-151">Эта зависимость означает, что ваш открытый интерфейс и ожидаемые результаты поддерживают интерфейс <xref:System.Collections.ICollection>, а не <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="fdba9-151">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="fdba9-152">Когда вы запустите этот тест, он завершится сбоем.</span><span class="sxs-lookup"><span data-stu-id="fdba9-152">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="fdba9-153">Вы еще не создали реализацию.</span><span class="sxs-lookup"><span data-stu-id="fdba9-153">You haven't created the implementation yet.</span></span> <span data-ttu-id="fdba9-154">Чтобы этот тест прошел успешно, напишите простейший код в классе *Library.fs* в своем рабочем проекте MathService:</span><span class="sxs-lookup"><span data-stu-id="fdba9-154">Make this test pass by writing the simplest code in the *Library.fs* class in your MathService project that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="fdba9-155">В каталоге *unit-testing-with-fsharp* снова выполните команду `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="fdba9-155">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="fdba9-156">Команда `dotnet test` запускает сборку для проекта `MathService` и затем для проекта `MathService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="fdba9-156">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="fdba9-157">После сборки обоих проектов команда позволяет запустить ваши тесты.</span><span class="sxs-lookup"><span data-stu-id="fdba9-157">After building both projects, it runs your tests.</span></span> <span data-ttu-id="fdba9-158">Теперь два теста пройдены.</span><span class="sxs-lookup"><span data-stu-id="fdba9-158">Two tests pass now.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="fdba9-159">Выполнение требований</span><span class="sxs-lookup"><span data-stu-id="fdba9-159">Completing the requirements</span></span>

<span data-ttu-id="fdba9-160">Теперь, когда тест проходит успешно, пора создать дополнительные тесты.</span><span class="sxs-lookup"><span data-stu-id="fdba9-160">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="fdba9-161">Следующий простой пример работает с последовательностью, единственным нечетным числом которой является `1`.</span><span class="sxs-lookup"><span data-stu-id="fdba9-161">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="fdba9-162">Число 1 использовать проще, потому что квадрат 1 равен 1.</span><span class="sxs-lookup"><span data-stu-id="fdba9-162">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="fdba9-163">Вот этот тест:</span><span class="sxs-lookup"><span data-stu-id="fdba9-163">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="fdba9-164">Когда вы запустите `dotnet test`, новый тест завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="fdba9-164">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="fdba9-165">Необходимо обновить метод `squaresOfOdds`, чтобы обработать этот новый тест.</span><span class="sxs-lookup"><span data-stu-id="fdba9-165">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="fdba9-166">Чтобы тест выполнялся успешно, необходимо отфильтровать все четные числа из последовательности.</span><span class="sxs-lookup"><span data-stu-id="fdba9-166">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="fdba9-167">Чтобы сделать это, напишите небольшую функцию фильтра и используйте `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="fdba9-167">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="fdba9-168">Обратите внимание на вызов `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="fdba9-168">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="fdba9-169">В результате создается список, который реализует интерфейс <xref:System.Collections.ICollection>.</span><span class="sxs-lookup"><span data-stu-id="fdba9-169">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="fdba9-170">Нужно выполнить еще один шаг: определить квадрат каждого из нечетных чисел.</span><span class="sxs-lookup"><span data-stu-id="fdba9-170">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="fdba9-171">Начнем с написания нового теста:</span><span class="sxs-lookup"><span data-stu-id="fdba9-171">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="fdba9-172">Чтобы вычислить квадрат каждого нечетного числа, можно исправить тест, пропустив фильтрованную последовательность через операцию сопоставления:</span><span class="sxs-lookup"><span data-stu-id="fdba9-172">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="fdba9-173">Вы создали небольшую библиотеку и набор модульных тестов для нее.</span><span class="sxs-lookup"><span data-stu-id="fdba9-173">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="fdba9-174">Вы структурировали решение, чтобы сделать добавление новых пакетов и тестов частью обычного рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="fdba9-174">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="fdba9-175">и получить возможность сосредоточиться на задачах приложения.</span><span class="sxs-lookup"><span data-stu-id="fdba9-175">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="fdba9-176">См. также</span><span class="sxs-lookup"><span data-stu-id="fdba9-176">See also</span></span>

- [<span data-ttu-id="fdba9-177">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="fdba9-177">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="fdba9-178">dotnet test</span><span class="sxs-lookup"><span data-stu-id="fdba9-178">dotnet test</span></span>](../tools/dotnet-test.md)
