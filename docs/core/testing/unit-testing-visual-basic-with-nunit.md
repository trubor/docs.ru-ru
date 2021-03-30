---
title: Модульное тестирование Visual Basic в .NET Core с помощью dotnet test и NUnit
description: Сведения о концепциях модульного тестирования в .NET Core в рамках пошаговой процедуры по созданию примера Visual Basic решения с помощью NUnit.
author: rprouse
ms.date: 10/04/2018
ms.openlocfilehash: 11334951d41c5cca24fcfb4853569e503cff97c5
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874905"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="885f9-103">Модульное тестирование библиотек .NET Core в Visual Basic с использованием dotnet test и NUnit</span><span class="sxs-lookup"><span data-stu-id="885f9-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="885f9-104">Этот учебник описывает пошаговую процедуру по созданию примера решения для изучения концепций модульного тестирования.</span><span class="sxs-lookup"><span data-stu-id="885f9-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="885f9-105">Если при изучении учебника вы предпочитаете использовать готовое решение, [просмотрите или скачайте пример кода](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-vb-nunit/) перед началом работы.</span><span class="sxs-lookup"><span data-stu-id="885f9-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="885f9-106">Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="885f9-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a><span data-ttu-id="885f9-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="885f9-107">Prerequisites</span></span>

- <span data-ttu-id="885f9-108">[Пакет SDK для .NET Core 2.1](https://dotnet.microsoft.com/download) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="885f9-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="885f9-109">Текстовый редактор или редактор кода по вашему выбору.</span><span class="sxs-lookup"><span data-stu-id="885f9-109">A text editor or code editor of your choice.</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="885f9-110">Создание исходного проекта</span><span class="sxs-lookup"><span data-stu-id="885f9-110">Creating the source project</span></span>

<span data-ttu-id="885f9-111">Откройте окно оболочки.</span><span class="sxs-lookup"><span data-stu-id="885f9-111">Open a shell window.</span></span> <span data-ttu-id="885f9-112">Создайте каталог с именем *unit-testing-vb-nunit* для хранения решения.</span><span class="sxs-lookup"><span data-stu-id="885f9-112">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="885f9-113">В этом каталоге выполните следующую команду, чтобы создать файл решения для библиотеки классов и тестового проекта:</span><span class="sxs-lookup"><span data-stu-id="885f9-113">Inside this new directory, run the following command to create a new solution file for the class library and the test project:</span></span>

```dotnetcli
dotnet new sln
```

<span data-ttu-id="885f9-114">Затем создайте каталог *PrimeService*.</span><span class="sxs-lookup"><span data-stu-id="885f9-114">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="885f9-115">Ниже приведена актуальная структура файлов:</span><span class="sxs-lookup"><span data-stu-id="885f9-115">The following outline shows the file structure so far:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="885f9-116">Перейдите в каталог *PrimeService* и выполните следующую команду, чтобы создать исходный проект:</span><span class="sxs-lookup"><span data-stu-id="885f9-116">Make *PrimeService* the current directory and run the following command to create the source project:</span></span>

```dotnetcli
dotnet new classlib -lang VB
```

<span data-ttu-id="885f9-117">Переименуйте *Class1.VB* в *PrimeService.VB*.</span><span class="sxs-lookup"><span data-stu-id="885f9-117">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="885f9-118">Создайте сбойную реализацию класса `PrimeService`:</span><span class="sxs-lookup"><span data-stu-id="885f9-118">You create a failing implementation of the `PrimeService` class:</span></span>

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="885f9-119">Вернитесь в каталог *unit-testing-vb-using-mstest*.</span><span class="sxs-lookup"><span data-stu-id="885f9-119">Change the directory back to the *unit-testing-vb-using-mstest* directory.</span></span> <span data-ttu-id="885f9-120">Чтобы добавить проект библиотеки классов в решение, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="885f9-120">Run the following command to add the class library project to the solution:</span></span>

```dotnetcli
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a><span data-ttu-id="885f9-121">Создание тестового проекта</span><span class="sxs-lookup"><span data-stu-id="885f9-121">Creating the test project</span></span>

<span data-ttu-id="885f9-122">Затем создайте каталог *PrimeService.Tests*.</span><span class="sxs-lookup"><span data-stu-id="885f9-122">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="885f9-123">Ниже представлена структура каталогов:</span><span class="sxs-lookup"><span data-stu-id="885f9-123">The following outline shows the directory structure:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="885f9-124">Перейдите в каталог *PrimeService.Tests* и создайте проект, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="885f9-124">Make the *PrimeService.Tests* directory the current directory and create a new project using the following command:</span></span>

```dotnetcli
dotnet new nunit -lang VB
```

<span data-ttu-id="885f9-125">Команда [dotnet new](../tools/dotnet-new.md) создает тестовый проект, который использует NUnit в качестве библиотеки тестов.</span><span class="sxs-lookup"><span data-stu-id="885f9-125">The [dotnet new](../tools/dotnet-new.md) command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="885f9-126">Созданный шаблон позволяет настроить средство выполнения тестов в файле *PrimeServiceTests.vbproj*:</span><span class="sxs-lookup"><span data-stu-id="885f9-126">The generated template configures the test runner in the *PrimeServiceTests.vbproj* file:</span></span>

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

<span data-ttu-id="885f9-127">Тестовый проект требует других пакетов для создания и выполнения модульных тестов. Команда</span><span class="sxs-lookup"><span data-stu-id="885f9-127">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="885f9-128">`dotnet new` на предыдущем шаге добавляет NUnit и адаптер тестирования NUnit.</span><span class="sxs-lookup"><span data-stu-id="885f9-128">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="885f9-129">Теперь добавьте в проект библиотеку классов `PrimeService` в качестве еще одной зависимости.</span><span class="sxs-lookup"><span data-stu-id="885f9-129">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="885f9-130">Используйте команду [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="885f9-130">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="885f9-131">Все содержимое файла можно просмотреть в [репозитории образцов](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="885f9-131">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="885f9-132">Ниже показан окончательный макет решения:</span><span class="sxs-lookup"><span data-stu-id="885f9-132">You have the following final solution layout:</span></span>

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

<span data-ttu-id="885f9-133">Выполните следующую команду в каталоге *unit-testing-vb-nunit*:</span><span class="sxs-lookup"><span data-stu-id="885f9-133">Execute the following command in the *unit-testing-vb-nunit* directory:</span></span>

```dotnetcli
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="885f9-134">Создание первого теста</span><span class="sxs-lookup"><span data-stu-id="885f9-134">Creating the first test</span></span>

<span data-ttu-id="885f9-135">Напишите один тест сбоя теста, запустите его, а затем повторите этот процесс.</span><span class="sxs-lookup"><span data-stu-id="885f9-135">You write one failing test, make it pass, then repeat the process.</span></span> <span data-ttu-id="885f9-136">В каталоге *PrimeService.Tests* переименуйте файл *UnitTest1.vb* в *PrimeService_IsPrimeShould.VB* и замените его содержимое следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="885f9-136">In the *PrimeService.Tests* directory, rename the *UnitTest1.vb* file to *PrimeService_IsPrimeShould.VB* and replace its entire contents with the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="885f9-137">Атрибут `<TestFixture>` указывает класс, который содержит тесты.</span><span class="sxs-lookup"><span data-stu-id="885f9-137">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="885f9-138">Атрибут `<Test>` обозначает метод, который выполняется с помощью средства выполнения тестов.</span><span class="sxs-lookup"><span data-stu-id="885f9-138">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="885f9-139">Из каталога *unit-testing-vb-nunit* выполните команду [`dotnet test`](../tools/dotnet-test.md) для создания тестов и библиотеки классов, а затем выполните тесты.</span><span class="sxs-lookup"><span data-stu-id="885f9-139">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="885f9-140">Средство запуска тестов NUnit содержит точку входа в программу для выполнения тестов.</span><span class="sxs-lookup"><span data-stu-id="885f9-140">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="885f9-141">`dotnet test` запускает средство выполнения тестов с помощью проекта модульного теста, который вы создали.</span><span class="sxs-lookup"><span data-stu-id="885f9-141">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="885f9-142">Тест не будет пройден.</span><span class="sxs-lookup"><span data-stu-id="885f9-142">Your test fails.</span></span> <span data-ttu-id="885f9-143">Вы еще не создали реализацию.</span><span class="sxs-lookup"><span data-stu-id="885f9-143">You haven't created the implementation yet.</span></span> <span data-ttu-id="885f9-144">Чтобы тест был пройден, напишите простейший код в классе `PrimeService`, который работает:</span><span class="sxs-lookup"><span data-stu-id="885f9-144">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

<span data-ttu-id="885f9-145">Выполните команду `dotnet test` еще раз в каталоге *unit-testing-vb-nunit*.</span><span class="sxs-lookup"><span data-stu-id="885f9-145">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="885f9-146">Команда `dotnet test` запускает сборку для проекта `PrimeService` и затем для проекта `PrimeService.Tests`.</span><span class="sxs-lookup"><span data-stu-id="885f9-146">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="885f9-147">После сборки обоих проектов она запускает этот отдельный тест.</span><span class="sxs-lookup"><span data-stu-id="885f9-147">After building both projects, it runs this single test.</span></span> <span data-ttu-id="885f9-148">Он выполняется.</span><span class="sxs-lookup"><span data-stu-id="885f9-148">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="885f9-149">Добавление дополнительных возможностей</span><span class="sxs-lookup"><span data-stu-id="885f9-149">Adding more features</span></span>

<span data-ttu-id="885f9-150">Теперь, когда тест проходит успешно, пора создать дополнительные тесты.</span><span class="sxs-lookup"><span data-stu-id="885f9-150">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="885f9-151">Есть еще ряд элементарных случаев с простыми числами: 0, -1.</span><span class="sxs-lookup"><span data-stu-id="885f9-151">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="885f9-152">Можно добавить их в качестве тестов с помощью атрибута `<Test>`, но это скоро станет утомительным.</span><span class="sxs-lookup"><span data-stu-id="885f9-152">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="885f9-153">Есть другие атрибуты xUnit, которые позволяют создавать наборы похожих тестов.</span><span class="sxs-lookup"><span data-stu-id="885f9-153">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="885f9-154">Атрибут `<TestCase>` представляет набор тестов, которые выполняют один и тот же код, но имеют разные входные аргументы.</span><span class="sxs-lookup"><span data-stu-id="885f9-154">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="885f9-155">С помощью атрибута `<TestCase>` можно указать значения для этих входных аргументов.</span><span class="sxs-lookup"><span data-stu-id="885f9-155">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="885f9-156">Вместо создания тестов примените эти два атрибута, чтобы создать последовательность тестов, которая проверяет несколько значений меньше 2, то есть наименьшего простого числа.</span><span class="sxs-lookup"><span data-stu-id="885f9-156">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="885f9-157">Выполните команду `dotnet test`, и два из этих тестов завершаются ошибкой.</span><span class="sxs-lookup"><span data-stu-id="885f9-157">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="885f9-158">Для успешного выполнения всех тестов нужно изменить предложение `if` в начале метода `Main` в файле *PrimeServices.cs*:</span><span class="sxs-lookup"><span data-stu-id="885f9-158">To make all of the tests pass, change the `if` clause at the beginning of the `Main` method in the *PrimeServices.cs* file:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="885f9-159">Продолжайте итерации, добавляя тесты, алгоритмы и код в главной библиотеке.</span><span class="sxs-lookup"><span data-stu-id="885f9-159">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="885f9-160">В результате вы получите [готовую версию тестов](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) и [полную реализацию библиотеки](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span><span class="sxs-lookup"><span data-stu-id="885f9-160">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/main/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="885f9-161">Вы создали небольшую библиотеку и набор модульных тестов для нее.</span><span class="sxs-lookup"><span data-stu-id="885f9-161">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="885f9-162">Вы структурировали решение, чтобы сделать добавление новых пакетов и тестов частью обычного рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="885f9-162">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="885f9-163">и получить возможность сосредоточиться на задачах приложения.</span><span class="sxs-lookup"><span data-stu-id="885f9-163">You've concentrated most of your time and effort on solving the goals of the application.</span></span>
