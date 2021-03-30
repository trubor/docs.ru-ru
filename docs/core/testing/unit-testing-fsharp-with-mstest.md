---
title: Модульное тестирование F# в .NET Core с помощью dotnet test и MSTest
description: Сведения о концепциях модульного тестирования для F# в .NET Core в рамках пошаговой процедуры по созданию примера решения c помощью команды dotnet test и MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: 2245efef9ab63303b3ae8b5d45ad8955b334e6e5
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873527"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a><span data-ttu-id="77b01-103">Модульное тестирование библиотек F# в .NET Core с использованием dotnet test и MSTest</span><span class="sxs-lookup"><span data-stu-id="77b01-103">Unit testing F# libraries in .NET Core using dotnet test and MSTest</span></span>

<span data-ttu-id="77b01-104">Этот учебник описывает пошаговую процедуру по созданию примера решения для изучения концепций модульного тестирования.</span><span class="sxs-lookup"><span data-stu-id="77b01-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="77b01-105">Если при изучении учебника вы предпочитаете использовать готовое решение, [просмотрите или скачайте пример кода](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-with-fsharp-mstest/) перед началом работы.</span><span class="sxs-lookup"><span data-stu-id="77b01-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-with-fsharp-mstest/) before you begin.</span></span> <span data-ttu-id="77b01-106">Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="77b01-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a><span data-ttu-id="77b01-107">Создание исходного проекта</span><span class="sxs-lookup"><span data-stu-id="77b01-107">Creating the source project</span></span>

<span data-ttu-id="77b01-108">Откройте окно оболочки.</span><span class="sxs-lookup"><span data-stu-id="77b01-108">Open a shell window.</span></span> <span data-ttu-id="77b01-109">Создайте каталог с именем *unit-testing-with-fsharp* для хранения решения.</span><span class="sxs-lookup"><span data-stu-id="77b01-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="77b01-110">В этом каталоге выполните команду `dotnet new sln`, чтобы создать решение.</span><span class="sxs-lookup"><span data-stu-id="77b01-110">Inside this new directory, run `dotnet new sln` to create a new solution.</span></span> <span data-ttu-id="77b01-111">Это упрощает управление библиотекой классов и проектом модульного теста.</span><span class="sxs-lookup"><span data-stu-id="77b01-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="77b01-112">В каталоге решения создайте каталог *MathService*.</span><span class="sxs-lookup"><span data-stu-id="77b01-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="77b01-113">Актуальная структура каталогов и файлов приведена ниже:</span><span class="sxs-lookup"><span data-stu-id="77b01-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="77b01-114">Чтобы создать исходный проект, перейдите в каталог *MathService* и выполните команду `dotnet new classlib -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="77b01-114">Make *MathService* the current directory and run `dotnet new classlib -lang "F#"` to create the source project.</span></span>  <span data-ttu-id="77b01-115">Создайте реализацию службы вычислений со сбоем:</span><span class="sxs-lookup"><span data-stu-id="77b01-115">You'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="77b01-116">Вернитесь в каталог *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="77b01-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="77b01-117">Чтобы добавить проект библиотеки классов в решение, выполните команду `dotnet sln add .\MathService\MathService.fsproj`.</span><span class="sxs-lookup"><span data-stu-id="77b01-117">Run `dotnet sln add .\MathService\MathService.fsproj` to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="77b01-118">Создание тестового проекта</span><span class="sxs-lookup"><span data-stu-id="77b01-118">Creating the test project</span></span>

<span data-ttu-id="77b01-119">Затем создайте каталог *MathService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="77b01-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="77b01-120">Ниже представлена структура каталогов:</span><span class="sxs-lookup"><span data-stu-id="77b01-120">The following outline shows the directory structure:</span></span>

```console
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="77b01-121">Перейдите в каталог *MathService.Tests* и создайте проект с помощью `dotnet new mstest -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="77b01-121">Make the *MathService.Tests* directory the current directory and create a new project using `dotnet new mstest -lang "F#"`.</span></span> <span data-ttu-id="77b01-122">При этом создается тестовый проект, который использует MSTest в качестве среды тестирования.</span><span class="sxs-lookup"><span data-stu-id="77b01-122">This creates a test project that uses MSTest as the test framework.</span></span> <span data-ttu-id="77b01-123">Созданный шаблон настраивает средство выполнения тестов в файле *MathServiceTests.fsproj*:</span><span class="sxs-lookup"><span data-stu-id="77b01-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="77b01-124">Тестовый проект требует других пакетов для создания и выполнения модульных тестов. Команда</span><span class="sxs-lookup"><span data-stu-id="77b01-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="77b01-125">`dotnet new` на предыдущем шаге добавила MSTest и средство выполнения тестов MSTest.</span><span class="sxs-lookup"><span data-stu-id="77b01-125">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="77b01-126">Теперь добавьте в проект библиотеку классов `MathService` в качестве еще одной зависимости.</span><span class="sxs-lookup"><span data-stu-id="77b01-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="77b01-127">Использование команды `dotnet add reference`:</span><span class="sxs-lookup"><span data-stu-id="77b01-127">Use the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="77b01-128">Все содержимое файла можно просмотреть в [репозитории образцов](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="77b01-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="77b01-129">Ниже показан окончательный макет решения:</span><span class="sxs-lookup"><span data-stu-id="77b01-129">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathServiceTests.fsproj
```

<span data-ttu-id="77b01-130">Выполните команду `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` в каталоге *unit-testing-with-fsharp*.</span><span class="sxs-lookup"><span data-stu-id="77b01-130">Execute `dotnet sln add .\MathService.Tests\MathService.Tests.fsproj` in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="77b01-131">Создание первого теста</span><span class="sxs-lookup"><span data-stu-id="77b01-131">Creating the first test</span></span>

<span data-ttu-id="77b01-132">Напишите один тест сбоя теста, запустите его, а затем повторите этот процесс.</span><span class="sxs-lookup"><span data-stu-id="77b01-132">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="77b01-133">Откройте файл *Tests.fs* и добавьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="77b01-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open Microsoft.VisualStudio.TestTools.UnitTesting
open MathService

[<TestClass>]
type TestClass () =

    [<TestMethod>]
    member this.TestMethodPassing() =
        Assert.IsTrue(true)

    [<TestMethod>]
     member this.FailEveryTime() = Assert.IsTrue(false)
```

<span data-ttu-id="77b01-134">Атрибут `[<TestClass>]` обозначает класс, который содержит тесты.</span><span class="sxs-lookup"><span data-stu-id="77b01-134">The `[<TestClass>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="77b01-135">Атрибут `[<TestMethod>]` обозначает метод теста, который выполняется с помощью средства выполнения тестов.</span><span class="sxs-lookup"><span data-stu-id="77b01-135">The `[<TestMethod>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="77b01-136">В каталоге *unit-testing-with-fsharp* выполните команду `dotnet test` для создания тестов и библиотеки классов, а затем выполните тесты.</span><span class="sxs-lookup"><span data-stu-id="77b01-136">From the *unit-testing-with-fsharp* directory, execute `dotnet test` to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="77b01-137">Средство запуска тестов MSTest содержит точку входа в программу для выполнения тестов.</span><span class="sxs-lookup"><span data-stu-id="77b01-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="77b01-138">`dotnet test` запускает средство выполнения тестов с помощью проекта модульного теста, который вы создали.</span><span class="sxs-lookup"><span data-stu-id="77b01-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="77b01-139">Эти два теста демонстрируют самые простые тесты, которые выполняются и завершаются сбоем.</span><span class="sxs-lookup"><span data-stu-id="77b01-139">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="77b01-140">`My test` выполняется успешно, а `Fail every time` завершается сбоем.</span><span class="sxs-lookup"><span data-stu-id="77b01-140">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="77b01-141">Сейчас создайте тест для метода `squaresOfOdds`.</span><span class="sxs-lookup"><span data-stu-id="77b01-141">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="77b01-142">Метод `squaresOfOdds` возвращает список квадратов всех нечетных целочисленных значений, которые являются частью входной последовательности.</span><span class="sxs-lookup"><span data-stu-id="77b01-142">The `squaresOfOdds` method returns a list of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="77b01-143">Вместо того чтобы писать все эти функции одновременно, можно постепенно создавать тесты, проверяющие функциональность.</span><span class="sxs-lookup"><span data-stu-id="77b01-143">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="77b01-144">Если тест выполняется успешно, создается необходимая функция метода.</span><span class="sxs-lookup"><span data-stu-id="77b01-144">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="77b01-145">Самый простой тест — вызов `squaresOfOdds` со всеми четными числами, где результатом должна быть пустая последовательность целых чисел.</span><span class="sxs-lookup"><span data-stu-id="77b01-145">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="77b01-146">Вот этот тест:</span><span class="sxs-lookup"><span data-stu-id="77b01-146">Here's that test:</span></span>

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="77b01-147">Обратите внимание, что последовательность `expected` преобразована в список.</span><span class="sxs-lookup"><span data-stu-id="77b01-147">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="77b01-148">Библиотека MSTest зависит от многих стандартных типов .NET.</span><span class="sxs-lookup"><span data-stu-id="77b01-148">The MSTest library relies on many standard .NET types.</span></span> <span data-ttu-id="77b01-149">Эта зависимость означает, что ваш открытый интерфейс и ожидаемые результаты поддерживают интерфейс <xref:System.Collections.ICollection>, а не <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="77b01-149">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="77b01-150">Когда вы запустите этот тест, он завершится сбоем.</span><span class="sxs-lookup"><span data-stu-id="77b01-150">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="77b01-151">Вы еще не создали реализацию.</span><span class="sxs-lookup"><span data-stu-id="77b01-151">You haven't created the implementation yet.</span></span> <span data-ttu-id="77b01-152">Чтобы тест был пройден, напишите простейший код в классе `Mathservice`, который работает:</span><span class="sxs-lookup"><span data-stu-id="77b01-152">Make this test pass by writing the simplest code in the `Mathservice` class that works:</span></span>

```fsharp
let squaresOfOdds xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="77b01-153">В каталоге *unit-testing-with-fsharp* снова выполните команду `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="77b01-153">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="77b01-154">Команда `dotnet test` запускает сборку для проекта `MathService` и затем для проекта `MathService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="77b01-154">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="77b01-155">После сборки обоих проектов она запускает этот отдельный тест.</span><span class="sxs-lookup"><span data-stu-id="77b01-155">After building both projects, it runs this single test.</span></span> <span data-ttu-id="77b01-156">Он выполняется.</span><span class="sxs-lookup"><span data-stu-id="77b01-156">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="77b01-157">Выполнение требований</span><span class="sxs-lookup"><span data-stu-id="77b01-157">Completing the requirements</span></span>

<span data-ttu-id="77b01-158">Теперь, когда тест проходит успешно, пора создать дополнительные тесты.</span><span class="sxs-lookup"><span data-stu-id="77b01-158">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="77b01-159">Следующий простой пример работает с последовательностью, единственным нечетным числом которой является `1`.</span><span class="sxs-lookup"><span data-stu-id="77b01-159">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="77b01-160">Число 1 использовать проще, потому что квадрат 1 равен 1.</span><span class="sxs-lookup"><span data-stu-id="77b01-160">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="77b01-161">Вот этот тест:</span><span class="sxs-lookup"><span data-stu-id="77b01-161">Here's that next test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="77b01-162">Когда вы запустите `dotnet test`, новый тест завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="77b01-162">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="77b01-163">Необходимо обновить метод `squaresOfOdds`, чтобы обработать этот новый тест.</span><span class="sxs-lookup"><span data-stu-id="77b01-163">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="77b01-164">Чтобы тест выполнялся успешно, необходимо отфильтровать все четные числа из последовательности.</span><span class="sxs-lookup"><span data-stu-id="77b01-164">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="77b01-165">Чтобы сделать это, напишите небольшую функцию фильтра и используйте `Seq.filter`:</span><span class="sxs-lookup"><span data-stu-id="77b01-165">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

<span data-ttu-id="77b01-166">Обратите внимание на вызов `Seq.toList`.</span><span class="sxs-lookup"><span data-stu-id="77b01-166">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="77b01-167">В результате создается список, который реализует интерфейс <xref:System.Collections.ICollection>.</span><span class="sxs-lookup"><span data-stu-id="77b01-167">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="77b01-168">Нужно выполнить еще один шаг: определить квадрат каждого из нечетных чисел.</span><span class="sxs-lookup"><span data-stu-id="77b01-168">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="77b01-169">Начнем с написания нового теста:</span><span class="sxs-lookup"><span data-stu-id="77b01-169">Start by writing a new test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="77b01-170">Чтобы вычислить квадрат каждого нечетного числа, можно исправить тест, пропустив фильтрованную последовательность через операцию сопоставления:</span><span class="sxs-lookup"><span data-stu-id="77b01-170">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="77b01-171">Вы создали небольшую библиотеку и набор модульных тестов для нее.</span><span class="sxs-lookup"><span data-stu-id="77b01-171">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="77b01-172">Вы структурировали решение, чтобы сделать добавление новых пакетов и тестов частью обычного рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="77b01-172">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="77b01-173">и получить возможность сосредоточиться на задачах приложения.</span><span class="sxs-lookup"><span data-stu-id="77b01-173">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="77b01-174">См. также</span><span class="sxs-lookup"><span data-stu-id="77b01-174">See also</span></span>

- [<span data-ttu-id="77b01-175">dotnet new</span><span class="sxs-lookup"><span data-stu-id="77b01-175">dotnet new</span></span>](../tools/dotnet-new.md)
- [<span data-ttu-id="77b01-176">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="77b01-176">dotnet sln</span></span>](../tools/dotnet-sln.md)
- [<span data-ttu-id="77b01-177">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="77b01-177">dotnet add reference</span></span>](../tools/dotnet-add-reference.md)
- [<span data-ttu-id="77b01-178">dotnet test</span><span class="sxs-lookup"><span data-stu-id="77b01-178">dotnet test</span></span>](../tools/dotnet-test.md)
