---
title: Организация и тестирование проектов с помощью .NET CLI
description: В этом учебнике объясняется, как упорядочить и протестировать проекты .NET из командной строки.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: c668cff48a2418cc1bc34aef78ea26c863d9de6a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872682"
---
# <a name="organizing-and-testing-projects-with-the-net-cli"></a><span data-ttu-id="57d1f-103">Организация и тестирование проектов с помощью .NET CLI</span><span class="sxs-lookup"><span data-stu-id="57d1f-103">Organizing and testing projects with the .NET CLI</span></span>

<span data-ttu-id="57d1f-104">Это руководство служит продолжением документа [Учебник. Создание консольного приложения с помощью .NET в Visual Studio Code](with-visual-studio-code.md), и с его помощью мы переходим от создания простых консольных приложений к разработке более сложных и структурированных приложений.</span><span class="sxs-lookup"><span data-stu-id="57d1f-104">This tutorial follows [Tutorial: Create a console application with .NET using Visual Studio Code](with-visual-studio-code.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="57d1f-105">В этом руководстве будет описано, как упорядочить код с помощью папок и расширить консольное приложение с помощью платформы тестирования [xUnit](https://xunit.net/).</span><span class="sxs-lookup"><span data-stu-id="57d1f-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.net/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="57d1f-106">Упорядочение кода с помощью папок</span><span class="sxs-lookup"><span data-stu-id="57d1f-106">Using folders to organize code</span></span>

<span data-ttu-id="57d1f-107">Если вы хотите добавить новые типы в консольное приложение, это можно сделать, добавив в приложение файлы, содержащие эти типы.</span><span class="sxs-lookup"><span data-stu-id="57d1f-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="57d1f-108">Например, если добавить в проект файлы, содержащие типы `AccountInformation` и `MonthlyReportRecords`, это позволит получить плоскую и удобную для навигации структуру файлов проекта:</span><span class="sxs-lookup"><span data-stu-id="57d1f-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="57d1f-109">Однако этот подход можно применять только для относительно небольших проектов.</span><span class="sxs-lookup"><span data-stu-id="57d1f-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="57d1f-110">Можете представить, что произойдет, если добавить в проект 20 типов?</span><span class="sxs-lookup"><span data-stu-id="57d1f-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="57d1f-111">С таким количеством файлов в корневом каталоге проекта навигация по проекту и поддержка проекта будут представлять трудности.</span><span class="sxs-lookup"><span data-stu-id="57d1f-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="57d1f-112">Чтобы упорядочить проект, создайте новую папку для файлов типов и назовите ее *Models*.</span><span class="sxs-lookup"><span data-stu-id="57d1f-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="57d1f-113">Поместите файлы типов в папку *Models*:</span><span class="sxs-lookup"><span data-stu-id="57d1f-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="57d1f-114">Проекты, в которых файлы логически упорядочены в папки, легко поддерживать. Они также отличаются удобной навигацией.</span><span class="sxs-lookup"><span data-stu-id="57d1f-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="57d1f-115">В следующем разделе мы создадим более сложный пример проекта с папками и модульным тестированием.</span><span class="sxs-lookup"><span data-stu-id="57d1f-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="57d1f-116">Упорядочение и тестирование проекта на основе примера проекта с новыми типами для животных</span><span class="sxs-lookup"><span data-stu-id="57d1f-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="prerequisites"></a><span data-ttu-id="57d1f-117">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="57d1f-117">Prerequisites</span></span>

* <span data-ttu-id="57d1f-118">[Пакет SDK для .NET 5.0](https://dotnet.microsoft.com/download) или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="57d1f-118">[.NET 5.0 SDK](https://dotnet.microsoft.com/download) or a later version.</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="57d1f-119">Создание примера</span><span class="sxs-lookup"><span data-stu-id="57d1f-119">Building the sample</span></span>

<span data-ttu-id="57d1f-120">Для выполнения следующих действий можно воспользоваться [примером проекта с новыми типами для животных](https://github.com/dotnet/samples/tree/main/core/console-apps/NewTypesMsBuild) или создать собственные файлы и папки.</span><span class="sxs-lookup"><span data-stu-id="57d1f-120">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/main/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="57d1f-121">Типы логически организованы в структуру папок, которая позволяет добавлять дополнительные типы. Тесты также организованы в структуру папок, которая позволяет добавлять дополнительные тесты.</span><span class="sxs-lookup"><span data-stu-id="57d1f-121">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="57d1f-122">В этом примере используются два типа, `Dog` и `Cat`, которые реализуют общий интерфейс `IPet`.</span><span class="sxs-lookup"><span data-stu-id="57d1f-122">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="57d1f-123">Цель проекта `NewTypes` — упорядочить типы, связанные с животными, в папку *Pets*.</span><span class="sxs-lookup"><span data-stu-id="57d1f-123">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="57d1f-124">Если впоследствии добавляется другой набор типов *WildAnimals*, они помещаются в папку *NewTypes* вместе с папкой *Pets*.</span><span class="sxs-lookup"><span data-stu-id="57d1f-124">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="57d1f-125">Папка *WildAnimals* может содержать типы для животных, которые не являются домашними, например `Squirrel` и `Rabbit`.</span><span class="sxs-lookup"><span data-stu-id="57d1f-125">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="57d1f-126">При таком добавлении типов структура проекта всегда остается хорошо упорядоченной.</span><span class="sxs-lookup"><span data-stu-id="57d1f-126">In this way as types are added, the project remains well organized.</span></span>

<span data-ttu-id="57d1f-127">Создайте следующую структуру папок, которая включает следующие файлы с указанным содержимым:</span><span class="sxs-lookup"><span data-stu-id="57d1f-127">Create the following folder structure with file content indicated:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

<span data-ttu-id="57d1f-128">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="57d1f-128">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="57d1f-129">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="57d1f-129">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="57d1f-130">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="57d1f-130">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="57d1f-131">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="57d1f-131">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

<span data-ttu-id="57d1f-132">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="57d1f-132">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="57d1f-133">Выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="57d1f-133">Execute the following command:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="57d1f-134">Вы получите следующие выходные данные:</span><span class="sxs-lookup"><span data-stu-id="57d1f-134">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="57d1f-135">Необязательное упражнение: добавьте в проект новый тип животных, например `Bird`.</span><span class="sxs-lookup"><span data-stu-id="57d1f-135">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="57d1f-136">Сделайте так, чтобы метод `TalkToOwner` для птицы возвращал владельцу `Tweet!`.</span><span class="sxs-lookup"><span data-stu-id="57d1f-136">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="57d1f-137">Снова запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="57d1f-137">Run the app again.</span></span> <span data-ttu-id="57d1f-138">Выходные данные будут включать `Tweet!`</span><span class="sxs-lookup"><span data-stu-id="57d1f-138">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="57d1f-139">Тестирование примера</span><span class="sxs-lookup"><span data-stu-id="57d1f-139">Testing the sample</span></span>

<span data-ttu-id="57d1f-140">Проект `NewTypes` развернут, и вы упорядочили типы, связанные с животными, в отдельную папку.</span><span class="sxs-lookup"><span data-stu-id="57d1f-140">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="57d1f-141">Теперь давайте создадим тестовый проект и напишем тесты с помощью платформы тестирования [xUnit](https://xunit.net/).</span><span class="sxs-lookup"><span data-stu-id="57d1f-141">Next, create your test project and start writing tests with the [xUnit](https://xunit.net/) test framework.</span></span> <span data-ttu-id="57d1f-142">Модульное тестирование позволяет автоматически проверять правильную работу типов домашних животных.</span><span class="sxs-lookup"><span data-stu-id="57d1f-142">Unit testing allows you to automatically check the behavior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="57d1f-143">Вернитесь в папку *src*, создайте папку *test*, а внутри нее — папку *NewTypesTests*.</span><span class="sxs-lookup"><span data-stu-id="57d1f-143">Navigate back to the *src* folder and create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="57d1f-144">В командной строке перейдите в каталог *NewTypesTests* и выполните команду `dotnet new xunit`.</span><span class="sxs-lookup"><span data-stu-id="57d1f-144">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="57d1f-145">Эта команда создает два файла: *NewTypesTests.csproj* и *UnitTest1.cs*.</span><span class="sxs-lookup"><span data-stu-id="57d1f-145">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="57d1f-146">Сейчас в тестовом проекте нельзя проверять типы в `NewTypes`. Для этого необходимо добавить в проект `NewTypes` ссылку на проект.</span><span class="sxs-lookup"><span data-stu-id="57d1f-146">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="57d1f-147">Чтобы добавить ссылку на проект, выполните команду [`dotnet add reference`](../tools/dotnet-add-reference.md):</span><span class="sxs-lookup"><span data-stu-id="57d1f-147">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="57d1f-148">Также можно добавить ссылку на проект вручную. Для этого добавьте узел `<ItemGroup>` в файл *NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="57d1f-148">Or, you also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="57d1f-149">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="57d1f-149">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="57d1f-150">Файл *NewTypesTests.csproj* содержит следующие элементы:</span><span class="sxs-lookup"><span data-stu-id="57d1f-150">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="57d1f-151">Ссылка на пакет `Microsoft.NET.Test.Sdk`, инфраструктура тестирования .NET</span><span class="sxs-lookup"><span data-stu-id="57d1f-151">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="57d1f-152">Ссылка на пакет `xunit`, платформа тестирования xUnit</span><span class="sxs-lookup"><span data-stu-id="57d1f-152">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="57d1f-153">Ссылка на пакет `xunit.runner.visualstudio`, средство выполнения тестов</span><span class="sxs-lookup"><span data-stu-id="57d1f-153">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="57d1f-154">Ссылка на проект `NewTypes`, код для тестирования</span><span class="sxs-lookup"><span data-stu-id="57d1f-154">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="57d1f-155">Переименуйте файл *UnitTest1.cs* в *PetTests.cs* и замените код в файле на следующий:</span><span class="sxs-lookup"><span data-stu-id="57d1f-155">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }

    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }
}
```

<span data-ttu-id="57d1f-156">Необязательное упражнение: если ранее был добавлен тип `Bird`, который предоставляет владельцу `Tweet!`, добавьте метод теста в файл *PetTests.cs*, `BirdTalkToOwnerReturnsTweet`, который проверит правильность работы метода `TalkToOwner` для типа `Bird`.</span><span class="sxs-lookup"><span data-stu-id="57d1f-156">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="57d1f-157">Несмотря на то, что значения `expected` и `actual` должны быть равны, в начальных проверочных утверждениях с проверкой `Assert.NotEqual` указывается, что они *не равны*.</span><span class="sxs-lookup"><span data-stu-id="57d1f-157">Although you expect that the `expected` and `actual` values are equal, an initial assertion with the `Assert.NotEqual` check specifies that these values are *not equal*.</span></span> <span data-ttu-id="57d1f-158">Всегда создавайте тест таким образом, чтобы он завершался с ошибкой, чтобы проверить логику теста.</span><span class="sxs-lookup"><span data-stu-id="57d1f-158">Always initially create a test to fail in order to check the logic of the test.</span></span> <span data-ttu-id="57d1f-159">Убедившись, что тест не пройден, измените утверждение так, чтобы тест был пройден.</span><span class="sxs-lookup"><span data-stu-id="57d1f-159">After you confirm that the test fails, adjust the assertion to allow the test to pass.</span></span>

<span data-ttu-id="57d1f-160">Ниже показана полная структура проекта:</span><span class="sxs-lookup"><span data-stu-id="57d1f-160">The following shows the complete project structure:</span></span>

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

<span data-ttu-id="57d1f-161">Запустите тест в папке *test/NewTypesTests*.</span><span class="sxs-lookup"><span data-stu-id="57d1f-161">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="57d1f-162">Запустите тесты, выполнив команду [`dotnet test`](../tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="57d1f-162">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="57d1f-163">Эта команда запускает средство запуска тестов, указанное в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="57d1f-163">This command starts the test runner specified in the project file.</span></span>

<span data-ttu-id="57d1f-164">Как и ожидалось, тест завершается с ошибкой, и в консоли отображаются следующие выходные данные:</span><span class="sxs-lookup"><span data-stu-id="57d1f-164">As expected, testing fails, and the console displays the following output:</span></span>

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.
[xUnit.net 00:00:00.50]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
  Failed PetTests.DogTalkToOwnerReturnsWoof [6 ms]
  Error Message:
   Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
  Stack Trace:
     at PetTests.DogTalkToOwnerReturnsWoof() in C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\PetTests.cs:line 13

Failed!  - Failed:     1, Passed:     1, Skipped:     0, Total:     2, Duration: 8 ms - NewTypesTests.dll (net5.0)
```

<span data-ttu-id="57d1f-165">Измените проверочные утверждения в тестах с `Assert.NotEqual` на `Assert.Equal`:</span><span class="sxs-lookup"><span data-stu-id="57d1f-165">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="57d1f-166">Повторно запустите тесты, выполнив `dotnet test` команду, и получите следующие выходные данные:</span><span class="sxs-lookup"><span data-stu-id="57d1f-166">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

```output
Test run for C:\Source\dotnet\docs\samples\snippets\core\tutorials\testing-with-cli\csharp\test\NewTypesTests\bin\Debug\net5.0\NewTypesTests.dll (.NETCoreApp,Version=v5.0)
Microsoft (R) Test Execution Command Line Tool Version 16.8.1
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
A total of 1 test files matched the specified pattern.

Passed!  - Failed:     0, Passed:     2, Skipped:     0, Total:     2, Duration: 2 ms - NewTypesTests.dll (net5.0)
```

<span data-ttu-id="57d1f-167">Тесты завершены успешно.</span><span class="sxs-lookup"><span data-stu-id="57d1f-167">Testing passes.</span></span> <span data-ttu-id="57d1f-168">Методы типов животных возвращают правильные значения при взаимодействии с владельцем.</span><span class="sxs-lookup"><span data-stu-id="57d1f-168">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="57d1f-169">Вы познакомились с тем, как упорядочить и тестировать проекты с помощью xUnit.</span><span class="sxs-lookup"><span data-stu-id="57d1f-169">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="57d1f-170">Теперь вы можете приметь эти методы в собственных проектах.</span><span class="sxs-lookup"><span data-stu-id="57d1f-170">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="57d1f-171">*Удачного программирования!*</span><span class="sxs-lookup"><span data-stu-id="57d1f-171">*Happy coding!*</span></span>
