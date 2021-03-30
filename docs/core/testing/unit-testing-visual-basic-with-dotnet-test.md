---
title: Модульное тестирование .NET Core в Visual Basic с помощью dotnet test и xUnit
description: Сведения о концепциях модульного тестирования в .NET Core в рамках пошаговой процедуры по созданию примера решения Visual Basic с использованием dotnet test и xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 05/18/2020
ms.openlocfilehash: 67a8ea0520a0e38ff1f62cbecf82fe0b40969414
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875009"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a><span data-ttu-id="9b93b-103">Модульное тестирование библиотек .NET Core в Visual Basic с использованием dotnet test и xUnit</span><span class="sxs-lookup"><span data-stu-id="9b93b-103">Unit testing Visual Basic .NET Core libraries using dotnet test and xUnit</span></span>

<span data-ttu-id="9b93b-104">В этом руководстве показано, как создать решение c проектом модульного теста и проектом библиотеки.</span><span class="sxs-lookup"><span data-stu-id="9b93b-104">This tutorial shows how to build a solution containing a unit test project and library project.</span></span> <span data-ttu-id="9b93b-105">Чтобы работать с руководством на примере готового решения, [просмотрите или скачайте этот пример кода](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-using-dotnet-test/).</span><span class="sxs-lookup"><span data-stu-id="9b93b-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="9b93b-106">Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="9b93b-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="9b93b-107">Создание решения</span><span class="sxs-lookup"><span data-stu-id="9b93b-107">Create the solution</span></span>

<span data-ttu-id="9b93b-108">В этом разделе описано, как создать решение, которое содержит проект исходного кода и тестовый проект.</span><span class="sxs-lookup"><span data-stu-id="9b93b-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="9b93b-109">Полное решение имеет следующую структуру каталогов:</span><span class="sxs-lookup"><span data-stu-id="9b93b-109">The completed solution has the following directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.vb
        PrimeService.vbproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.vb
        PrimeServiceTests.vbproj
```

<span data-ttu-id="9b93b-110">В инструкциях далее описано, как создать тестовое решение.</span><span class="sxs-lookup"><span data-stu-id="9b93b-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="9b93b-111">См. [команды для быстрого создания тестового решения и дополнительные инструкции](#create-test-cmd).</span><span class="sxs-lookup"><span data-stu-id="9b93b-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="9b93b-112">Откройте окно оболочки.</span><span class="sxs-lookup"><span data-stu-id="9b93b-112">Open a shell window.</span></span>
* <span data-ttu-id="9b93b-113">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="9b93b-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="9b93b-114">Команда [`dotnet new sln`](../tools/dotnet-new.md) создает новое решение в каталоге *unit-testing-using-dotnet-test*.</span><span class="sxs-lookup"><span data-stu-id="9b93b-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="9b93b-115">Теперь перейдите в папку *unit-testing-using-dotnet-test*.</span><span class="sxs-lookup"><span data-stu-id="9b93b-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="9b93b-116">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="9b93b-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService --lang VB
  ```

   <span data-ttu-id="9b93b-117">Команда [`dotnet new classlib`](../tools/dotnet-new.md) создает новый проект библиотеки классов в папке *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="9b93b-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="9b93b-118">Новая библиотека классов будет содержать код для тестирования.</span><span class="sxs-lookup"><span data-stu-id="9b93b-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="9b93b-119">Переименуйте *Class1.vb* в *PrimeService.vb*.</span><span class="sxs-lookup"><span data-stu-id="9b93b-119">Rename *Class1.vb* to *PrimeService.vb*.</span></span>
* <span data-ttu-id="9b93b-120">Замените код файла *PrimeService.vb* кодом, приведенным ниже.</span><span class="sxs-lookup"><span data-stu-id="9b93b-120">Replace the code in *PrimeService.vb* with the following code:</span></span>
  
  ```vb
  Imports System
  
  Namespace Prime.Services
      Public Class PrimeService
          Public Function IsPrime(candidate As Integer) As Boolean
              Throw New NotImplementedException("Not implemented.")
          End Function
      End Class
  End Namespace
  ```

* <span data-ttu-id="9b93b-121">Предыдущий код:</span><span class="sxs-lookup"><span data-stu-id="9b93b-121">The preceding code:</span></span>
  * <span data-ttu-id="9b93b-122">Создает исключение <xref:System.NotImplementedException> с сообщением о том, что код не реализован.</span><span class="sxs-lookup"><span data-stu-id="9b93b-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="9b93b-123">Мы обновим его позже.</span><span class="sxs-lookup"><span data-stu-id="9b93b-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="9b93b-124">Выполните приведенную ниже команду в каталоге *unit-testing-using-dotnet-test*, чтобы добавить в решение проект библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="9b93b-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.vbproj
  ```

* <span data-ttu-id="9b93b-125">Создайте проект *PrimeService.Tests*, выполнив следующую команду</span><span class="sxs-lookup"><span data-stu-id="9b93b-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="9b93b-126">Предыдущая команда позволяет:</span><span class="sxs-lookup"><span data-stu-id="9b93b-126">The preceding command:</span></span>
  * <span data-ttu-id="9b93b-127">Создает проект *PrimeService.Tests* в каталоге *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="9b93b-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="9b93b-128">В тестовом проекте используется библиотека тестов [xUnit](https://xunit.net/).</span><span class="sxs-lookup"><span data-stu-id="9b93b-128">The test project uses [xUnit](https://xunit.net/) as the test library.</span></span>
  * <span data-ttu-id="9b93b-129">Настраивает средство выполнения тестов, добавляя следующие элементы `<PackageReference />` в файл проекта:</span><span class="sxs-lookup"><span data-stu-id="9b93b-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="9b93b-130">Microsoft.NET.Test.Sdk</span><span class="sxs-lookup"><span data-stu-id="9b93b-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="9b93b-131">xunit</span><span class="sxs-lookup"><span data-stu-id="9b93b-131">"xunit"</span></span>
    * <span data-ttu-id="9b93b-132">xunit.runner.visualstudio</span><span class="sxs-lookup"><span data-stu-id="9b93b-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="9b93b-133">Добавьте тестовый проект в файл решения, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="9b93b-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
  ```

* <span data-ttu-id="9b93b-134">Добавьте в проект *PrimeService.Tests* библиотеку классов `PrimeService` в качестве зависимости:</span><span class="sxs-lookup"><span data-stu-id="9b93b-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="9b93b-135">Команды для создания решения</span><span class="sxs-lookup"><span data-stu-id="9b93b-135">Commands to create the solution</span></span>

<span data-ttu-id="9b93b-136">В этом разделе перечислены все команды, описанные в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="9b93b-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="9b93b-137">Пропустите этот раздел, если вы уже выполнили действия из предыдущего раздела.</span><span class="sxs-lookup"><span data-stu-id="9b93b-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="9b93b-138">Следующие команды создают тестовое решение на компьютере Windows.</span><span class="sxs-lookup"><span data-stu-id="9b93b-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="9b93b-139">В macOS и UNIX измените в команде `ren` версию ОС на значение `ren`, чтобы переименовать файл:</span><span class="sxs-lookup"><span data-stu-id="9b93b-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.vb PrimeService.vb
dotnet sln add ./PrimeService/PrimeService.vbproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
```

<span data-ttu-id="9b93b-140">Выполните инструкции по замене кода в файле *PrimeService.vb*, из предыдущего раздела.</span><span class="sxs-lookup"><span data-stu-id="9b93b-140">Follow the instructions for "Replace the code in *PrimeService.vb* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="9b93b-141">Создание теста</span><span class="sxs-lookup"><span data-stu-id="9b93b-141">Create a test</span></span>

<span data-ttu-id="9b93b-142">Разработка на основе тестирования (TDD) обычно подразумевает написание теста до реализации целевого кода.</span><span class="sxs-lookup"><span data-stu-id="9b93b-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="9b93b-143">В этом руководстве используется подход TDD.</span><span class="sxs-lookup"><span data-stu-id="9b93b-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="9b93b-144">Метод `IsPrime` является вызываемым, но он пока не реализован.</span><span class="sxs-lookup"><span data-stu-id="9b93b-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="9b93b-145">Тестовый вызов `IsPrime` завершается ошибкой.</span><span class="sxs-lookup"><span data-stu-id="9b93b-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="9b93b-146">При использовании TDD мы создаем тест, который ожидаемо завершается ошибкой.</span><span class="sxs-lookup"><span data-stu-id="9b93b-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="9b93b-147">Затем мы обновляем целевой код, чтобы пройти только созданный тест.</span><span class="sxs-lookup"><span data-stu-id="9b93b-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="9b93b-148">Этот подход повторяется циклически: сначала вы создаете тест, который не выполняется, а затем обновляете целевой код, чтобы выполнить тест.</span><span class="sxs-lookup"><span data-stu-id="9b93b-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="9b93b-149">Обновите проект *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="9b93b-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="9b93b-150">Удалите *PrimeService.Tests/UnitTest1.vb*.</span><span class="sxs-lookup"><span data-stu-id="9b93b-150">Delete *PrimeService.Tests/UnitTest1.vb*.</span></span>
* <span data-ttu-id="9b93b-151">Создайте файл *PrimeService.Tests/PrimeService_IsPrimeShould.vb*.</span><span class="sxs-lookup"><span data-stu-id="9b93b-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.vb*  file.</span></span>
* <span data-ttu-id="9b93b-152">Замените код файла *PrimeService_IsPrimeShould.vb* кодом, приведенным ниже.</span><span class="sxs-lookup"><span data-stu-id="9b93b-152">Replace the code in *PrimeService_IsPrimeShould.vb* with the following code:</span></span>

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private ReadOnly _primeService As Prime.Services.PrimeService

        Public Sub New()
            _primeService = New Prime.Services.PrimeService()
        End Sub


        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="9b93b-153">Атрибут `[Fact]` объявляет метод теста, который выполняется средством выполнения тестов.</span><span class="sxs-lookup"><span data-stu-id="9b93b-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="9b93b-154">В папке *PrimeService.Tests* выполните `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="9b93b-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="9b93b-155">Команда [dotnet test](../tools/dotnet-test.md) компилирует оба проекта и выполняет тесты.</span><span class="sxs-lookup"><span data-stu-id="9b93b-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="9b93b-156">Средство запуска тестов xUnit содержит точку входа в программу для выполнения тестов.</span><span class="sxs-lookup"><span data-stu-id="9b93b-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="9b93b-157">`dotnet test` запускает средство выполнения тестов, используя проект модульного тестирования.</span><span class="sxs-lookup"><span data-stu-id="9b93b-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="9b93b-158">Тест возвращает ошибку, так как мы еще не реализовали `IsPrime`.</span><span class="sxs-lookup"><span data-stu-id="9b93b-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="9b93b-159">Согласно концепции TDD, нужно создавать только такой код, который позволит пройти этот тест.</span><span class="sxs-lookup"><span data-stu-id="9b93b-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="9b93b-160">Обновите `IsPrime`, включив в него следующий код.</span><span class="sxs-lookup"><span data-stu-id="9b93b-160">Update `IsPrime` with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Not implemented.")
End Function
```

<span data-ttu-id="9b93b-161">Запустите `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="9b93b-161">Run `dotnet test`.</span></span> <span data-ttu-id="9b93b-162">Тест проходит.</span><span class="sxs-lookup"><span data-stu-id="9b93b-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="9b93b-163">Добавьте дополнительные тесты.</span><span class="sxs-lookup"><span data-stu-id="9b93b-163">Add more tests</span></span>

<span data-ttu-id="9b93b-164">Добавьте проверку простых чисел для 0 и -1.</span><span class="sxs-lookup"><span data-stu-id="9b93b-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="9b93b-165">Можно скопировать предыдущий тест и изменить в нем код, чтобы использовать 0 и -1:</span><span class="sxs-lookup"><span data-stu-id="9b93b-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```vb
Dim result As Boolean = _primeService.IsPrime(1)

Assert.False(result, "1 should not be prime")
```

<span data-ttu-id="9b93b-166">Копирование кода теста, в котором изменяется только один параметр, приводит к дублированию кода и раздуванию теста.</span><span class="sxs-lookup"><span data-stu-id="9b93b-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="9b93b-167">Следующие атрибуты xUnit позволяют создавать набор сходных тестов.</span><span class="sxs-lookup"><span data-stu-id="9b93b-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="9b93b-168">`[Theory]` представляет набор тестов, которые выполняют один и тот же код, но имеют разные входные аргументы.</span><span class="sxs-lookup"><span data-stu-id="9b93b-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>
- <span data-ttu-id="9b93b-169">Атрибут `[InlineData]` задает значения для этих входных данных.</span><span class="sxs-lookup"><span data-stu-id="9b93b-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="9b93b-170">Чтобы не создавать новые тесты, примените указанные выше атрибуты xUnit для создания единой теории.</span><span class="sxs-lookup"><span data-stu-id="9b93b-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="9b93b-171">Замените представленный ниже код.</span><span class="sxs-lookup"><span data-stu-id="9b93b-171">Replace the following code:</span></span>

```vb
<Fact>
Sub IsPrime_InputIs1_ReturnFalse()
    Dim result As Boolean = _primeService.IsPrime(1)

    Assert.False(result, "1 should not be prime")
End Sub
```

<span data-ttu-id="9b93b-172">следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="9b93b-172">with the following code:</span></span>

```vb
<Theory>
<InlineData(-1)>
<InlineData(0)>
<InlineData(1)>
Sub IsPrime_ValuesLessThan2_ReturnFalse(ByVal value As Integer)
    Dim result As Boolean = _primeService.IsPrime(value)

    Assert.False(result, $"{value} should not be prime")
End Sub
```

<span data-ttu-id="9b93b-173">В приведенном выше коде `[Theory]` и `[InlineData]` позволяют тестировать несколько значений, не превышающих 2.</span><span class="sxs-lookup"><span data-stu-id="9b93b-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="9b93b-174">Число 2 является наименьшим простым числом.</span><span class="sxs-lookup"><span data-stu-id="9b93b-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="9b93b-175">Выполните команду `dotnet test`, и два теста завершатся ошибкой.</span><span class="sxs-lookup"><span data-stu-id="9b93b-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="9b93b-176">Поместите следующие код в метод `IsPrime`, чтобы успешно пройти все тесты:</span><span class="sxs-lookup"><span data-stu-id="9b93b-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate < 2 Then
        Return False
    End If
    Throw New NotImplementedException("Not fully implemented.")
End Function
```

<span data-ttu-id="9b93b-177">Согласно концепции TDD, добавьте новые тесты, которые завершаются ошибкой, а затем обновите целевой код.</span><span class="sxs-lookup"><span data-stu-id="9b93b-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="9b93b-178">Вы также можете изучить [готовую версию тестов](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) и [полную реализацию библиотеки](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="9b93b-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="9b93b-179">Составленный нами метод `IsPrime` не является эффективным алгоритмом для тестирования простых чисел.</span><span class="sxs-lookup"><span data-stu-id="9b93b-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9b93b-180">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="9b93b-180">Additional resources</span></span>

- [<span data-ttu-id="9b93b-181">Официальный сайт xUnit.net</span><span class="sxs-lookup"><span data-stu-id="9b93b-181">xUnit.net official site</span></span>](https://xunit.net/)
- [<span data-ttu-id="9b93b-182">Тестирование логики контроллера в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9b93b-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
